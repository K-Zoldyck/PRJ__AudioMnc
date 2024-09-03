

<script setup>
import { onMounted } from 'vue';

    const audioList = [];

    onMounted(()=>{
        if (window.AudioContext || window.webkitAudioContext) {
            const AudioContext = window.AudioContext || window.webkitAudioContext;
            const audioCtx = new AudioContext();
            class AudioPlayer {
                constructor(url) {
                    this.url = url;
                    this.audioBuffer = null;
                    this.source = null;
                    this.isPlaying = false;
                    this.loop = false;
                    this.volume = 1;
                    this.gainNode = audioCtx.createGain();
                    this.loadAudio();
                }
                
                loadAudio() {
                    fetch(this.url)
                        .then(response => response.arrayBuffer())
                        .then(arrayBuffer => audioCtx.decodeAudioData(arrayBuffer))
                        .then(audioBuffer => {
                            this.audioBuffer = audioBuffer;
                        })
                    .catch(e => console.error('Erro ao carregar o áudio:', e));
                }

                play() {
                    if (!this.isPlaying) {
                        this.source = audioCtx.createBufferSource();
                        this.source.buffer = this.audioBuffer;
                        this.source.loop = this.loop;
                        this.source.connect(this.gainNode).connect(audioCtx.destination);
                        this.gainNode.gain.setValueAtTime(this.volume, audioCtx.currentTime);
                        this.source.start();
                        this.isPlaying = true;

                        this.source.onended = () => {
                            this.isPlaying = false;
                        };
                    }
                }

                pause() {
                    if (this.isPlaying) {
                        this.source.stop();
                        this.isPlaying = false;
                    }
                }

                setVolume(volume) {
                    this.volume = volume;
                    this.gainNode.gain.setValueAtTime(this.volume, audioCtx.currentTime);
                }

                setLoop(loop) {
                    this.loop = loop;
                    if (this.source) {
                        this.source.loop = loop;
                    }
                }
            }
            audioList.push(new AudioPlayer('./audios/campfire.mp3'))
            audioList.push(new AudioPlayer('./audios/demonic.mp3'))
            audioList.push(new AudioPlayer('./audios/goblin_growl.mp3'))
            audioList.push(new AudioPlayer('./audios/magic.mp3'))
            audioList.push(new AudioPlayer('./audios/rain.mp3'))
            audioList.push(new AudioPlayer('./audios/thunder.mp3'))
            audioList.push(new AudioPlayer('./audios/town.mp3'))
        }
       
    })
    
    const playAudio = (audioId) => { 
        var audio = audioList[audioId];
        
        if (audio.isPlaying ) {
            audio.pause()
        } else {
            audioList[audioId].play();
        }
    }

    const setRepeat = (audioId) => { 
        audioList[audioId].setLoop(!audioList[audioId].loop)
    } 

    const setVolume = (audioId,volume) => { audioList[audioId].setVolume((volume.value/100))} 
</script>

<template>
    <main class="mode-c">
        <div class="player-box">
            <div v-for="x in 10" class="audio-controls">
                <img src="./icons/ic_001.svg" alt="">
                <p class="play-audio-titulo">audio titulo</p>
                <input class="audio-vol" type="range" min="0" max="100" @change="setVolume(x,$event.target)"/>
                <img src="./icons/ic_003.svg" alt="" @click="setRepeat(x)">
                <img src="./icons/ic_002.svg" alt="" @click="playAudio(x)">
            </div>
            
        </div>
        <div class="text-voice">
            <label class="text-voice-label">
                Text to voice
                <select class="text-voice-option">
                    <option>opt1</option>
                    <option>opt2</option>
                    <option>opt3</option>
                    <option>opt4</option>
                </select>
            </label>
            <textarea class="text-voice-text"></textarea>
            <div class="text-voice-controls">
                <button>Speak</button>
                <input type="range" min="0" max="100"/>
            </div>
        </div>
    </main>
</template>

<style scoped>
    .mode-c {
        width: min(var(--min-w),var(--max-w));
        margin: 1% auto;
    }
    .player-box{
        overflow: auto;
        width: 100%;
        height: 240px;
    }
    .audio-controls {
        display: flex;
        justify-content: center;
        border: 1px solid #919191;
        width: 100%;
        margin: 10px 0;
        padding: 5px 0;
    }
        .audio-controls img {cursor: pointer;}

    .text-voice {
        width: 30%;
    }
        .text-voice-label {
            display: flex;
            align-items: center;
            width: 100%;
            margin-bottom: 10px;
        }
            .text-voice-option {
                width: 40%;
                padding: 4px;
                text-align: center;
                border: 1px solid #919191;
                background-color: transparent;
                margin-left: auto;
            }
        .text-voice-text {
            width: 100%;
            height: 150px;
            font-size: 1.2rem;
            text-align: justify;
            padding: 5px;
        }
        .text-voice-controls {
            display: flex;
            width: 100%;
            margin: 7px 0;
        }
            .text-voice-controls button{
                width: 30%;
                cursor: pointer;
                border: 1px solid rgb(64, 143, 64);
                background-color: rgb(64, 143, 64);
                padding: 5px;
                font-size: 1.2rem;
                color: #f4f4f4;
                font-weight: 600;
            }
            .text-voice-controls input {
                margin-left: auto;                
            }


</style>