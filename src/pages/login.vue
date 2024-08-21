
<script setup>
    import { defineEmits } from 'vue';
    const emit = defineEmits(['action']);

    const login = () => {
        let user_mail =  document.getElementById("mail").value;
        let user_pass =  document.getElementById("pass").value;

        if ( user_mail ==  "test@test" && user_pass ==  "password" ){
            emit('action','goto_mance');
        }else {
            alert("login data wrongs")
        }
    }

    const goto_sigin = () => { emit('action','goto_sigin');}
    const goto_recov = () => { emit('action','goto_recov');}
</script>

<template>
    <div>
        <img class="logo-ic" alt="" src="./icons/ic_aber.png"/>
        <h1 class="page-title">Login</h1>
        <form @submit.prevent="login">
            <label class="input-form">
                <span>Email</span>
                <input type="email" placeholder="type your email" id="mail"/>
            </label>
            <label class="input-form">
                <span>Password</span>
                <input type="password" placeholder="type a password" id="pass"/>
            </label>
            <p class="recovery-link" @click="goto_recov">Recovery password</p>
            <button class="bnt-submit">Login</button>
            <p class="new-account-link">Dont have an accounter?, <p class="new-ac-link" @click="goto_sigin">sing up here</p></p>
        </form>
    </div>
    <footer>
        CraftNerd &copy; - 2023/2024
    </footer>
</template>

<style scoped>

    p {
        cursor: pointer;
    }
    .logo-ic {
        display: block;
        width: 20%;
        margin: 10% auto 4% auto;
    }
    .page-title {
        width: 100%;
        text-align: center;
        font: 600 1.9rem/1 sans-serif;
    }
    form {
        width: 80%;
        margin: 10% auto 14% auto;
    }
        .input-form {
            display: block;
            width: 100%;
            margin: 6% 0;
        }
            .input-form span {
                display: block;
                font: 600 1.3rem/1 sans-serif;
                padding-bottom: 1%;
            }
            .input-form input{
                display: block;
                border: 1px solid #312e2e;
                padding: 4% 2%;
                width: 100%;
                outline: none;
                font: 200 .9rem/1 sans-serif;
            }
            .input-form input[type='password'] { background: url('./icons/ic_pass.svg') 95% 50% / 5% no-repeat;}
            .input-form input[type='email']{ background: url('./icons/ic_emil.svg') 95% 50% / 5% no-repeat;}
</style>