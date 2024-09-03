
<script setup>
    import { defineEmits } from 'vue';
    const emit = defineEmits(['action']);

    const login = () => {
        let user_mail =  document.getElementById("mail").value;
        let user_pass =  document.getElementById("pass").value;

        if (1){
            emit('action','goto_mance');
        }else {
            alert("login data wrongs")
        }
    }

    const goto_sigin = () => { emit('action','goto_sigin');}
    const goto_recov = () => { emit('action','goto_recov');}
</script>

<template>
    <div class="viewport">
    <section class="login-page">
        <h1>Login</h1>
        <lable>Email: <input id="mail" type="email" placeholder="exeplo@email.com"></lable>
        <lable>Senha: <input id="pass" type="password"></lable>
        <span @click="goto_recov">Recuperar Senha</span>
        <button @click="login">Logar</button>
        <p>Ainda não possue uma conta?<span @click="goto_sigin">Criar</span></p>
        <footer>
            <img src="" alt="">
            <span>CraftNerd &copy; - All rights</span>
        </footer>
    </section>
    </div>
</template>

<style scoped>
    .viewport {
        width: 100%;
        height: 97vh;
        display: flex;
    }
    .login-page {
        width: min(500px,98%);
        outline: 1px solid red;
        margin: auto auto;
    }
    .login-page h1 {
        width: 100%;
        text-align: center;
        font-size: 2.3rem;
    }
    .login lable { 
        display: block;
    }
</style>