
<script></script>

<template>
    <div>
        <img class="logo-ic" alt="" src="./icons/ic_aber.png"/>
        <h1 class="page-title">Login</h1>
        <form>
            <label class="input-form">
                <span>Email</span>
                <input type="email" placeholder="type your email"/>
            </label>
            <label class="input-form">
                <span>Password</span>
                <input type="password" placeholder="type a password"/>
            </label>
            <a hre="" class="recovery-link">Recovery password</a>
            <button class="bnt-submit">Login</button>
            <p class="new-account-link">Dont have an accounter?, <a href='' class="new-ac-link">sing up here</a></p>
        </form>
    </div>
    <footer>
        CraftNerd &copy; - 2023/2024
    </footer>
</template>

<style scoped>
    .logo-ic{
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