

<template>
    <div class="wrapper">
        <div class="wrapper__inner">
            <div class="wrapper__inner-content">
                <div class="header-logo">
    <div class="header-logo__container">
        <div class="header-logo__logo ibg">
            <img src="./assets/logo.svg" alt="logo">
        </div>
    </div>
</div>
                <main class="page">
                    <section class="authorization authorization-main">
                        <div class="authorization-main__container">
                            <div class="authorization-main__wrapper">
                                <div class="authorization-main__body">
                                    <div class="authorization__title">Welcome back!</div>
                                    <div class="authorization__subtitle">Enter your credentials to access your account</div>
                                    <div v-if="!user">
                                    <form action="#" name="#" class="authorization__form form-authorization">
                                        <label for="authorization-email">
                                            <div class="form-authorization__label">Email</div>
                                            <input v-model="email" type="email" class="form-authorization__input form-authorization__input_error" id="authorization-email" name="email" placeholder="name@company.com" autocomplete="off">
                                            <div class="form-authorization__error-text">Invalid email format</div>
                                        </label>
                                        <label for="authorization-password">
                                            <div class="form-authorization__label">Password</div>
                                            <input v-model="password" type="password" class="form-authorization__input" id="authorization-password" name="password" placeholder="Input your password" autocomplete="off">
                                            <!-- <div class="form-authorization__error-text">Password must be between 8 and 20 characters</div> -->
                                        </label>
                                        <a href="/forgot.html" class="form-authorization__link">Forgot password?</a>
                                        <button v-on:click="auth"  class="form-authorization__button">Sign in</button>
                                    </form>
                                    
                                  </div>
                                  <span v-else> вы зашли{{user?.email}} </span>
                                </div>
                                <div class="authorization__image">
                                    <img src="./assets/main-image.svg" alt="men">
                                </div>
                    
                                <div class="authorization__dots authorization__dots_1">
                                    <img src="./assets/dots.svg" alt="dots">
                                </div>
                                <div class="authorization__dots authorization__dots_2">
                                    <img src="./assets/dots.svg" alt="dots">
                                </div>
                            </div>
                        </div>
                    </section>
                </main>   
            </div>
        </div>
    </div>
   
</template>

<script >
import axios from 'axios'
export default {
  name: 'App',
  data(){
    return{
     /*  API_URL: 'https://api.corecruiter.org/api', */
      email: '',
      password: '',
      isLoading: false,
    }
  },
  methods:{
    async auth(){
      this.isLoading = true
      await axios.post(
        'https://api.corecruiter.org/api/user/auth',
        {email: this.email, password: this.password},
        
        {
          headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer '
          },
          
        }
        
      )
      .then(({data})=>{
        this.user = data.user
        this.isLoading = false
        console.log('ecgt[]')
      })
    }
  }
}

</script>


<style scoped>
  .wrapper {
    min-height: 100%;
    display: flex;
    flex-direction: column;
    background-color: #ffffff;
}

.wrapper__inner {
    display: flex;
    flex: 1;
}

.wrapper__inner-content {
    display: flex;
    flex-direction: column;
    flex: 1;
    transition: margin-left 0.3s ease 0s;
}

.header-logo {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    padding: 18px 0;
    background-color: #FFFFFF;
}

.authorization__title {
    text-align: center;
    font-size: 24px;
    color: #1F2937;
    font-weight: 700;
    line-height: 133%;
}

.authorization__title:not(:last-child) {
    margin-bottom: 8px;
}

.authorization__subtitle:not(:last-child) {
    margin-bottom: 32px;
}

.authorization__subtitle {
    text-align: center;
    font-size: 14px;
    color: #4B5563;
    line-height: 157%;
}

.form-authorization {
    position: relative;
    z-index: 5;
    min-width: 384px;
}

.form-authorization label {
    position: relative;
    display: block;
}

.authorization-main .authorization-main__body {
    max-width: unset;
}

.authorization__subtitle:not(:last-child) {
    margin-bottom: 32px;
}

.authorization__subtitle {
    text-align: center;
    font-size: 14px;
    color: #4B5563;
    line-height: 157%;
}

.form-authorization label {
    position: relative;
    display: block;
}

.form-authorization__input_error {
    background-color: #FDF2F2;
    border: 1px solid #DC2626;
}

.form-authorization__input {
    width: 100%;
    padding: 9px 12px;
    border: 1px solid #D1D5DB;
    border-radius: 4px;
    font-size: 14px;
    color: #1F2937;
    font-weight: 400;
    line-height: 157%;
}

.form-authorization__error-text {
    margin-top: 2.5px;
    font-weight: 400;
    font-size: 14px;
    line-height: 157%;
    color: #DC2626;
}

.form-authorization label {
    position: relative;
    display: block;
}

a:link, a:visited {
    text-decoration: none;
}

.form-authorization__link {
    display: block;
    font-weight: 500;
    font-size: 14px;
    line-height: 157%;
    color: #2A86FF;
    transition: opacity 0.3s ease 0s;
}

.form-authorization__button {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    width: 100%;
    padding: 9px 0;
    background-color: #2A86FF;
    border-radius: 4px;
    transition: all 0.3s ease 0s;
    font-weight: 500;
    font-size: 14px;
    line-height: 157%;
    color: #ffffff;
    transition: opacity 0.3s ease 0s;
}

.form-authorization > * {
    margin-bottom: 22px;
}

.header-logo__container {
    max-width: 1385px;
}

.ibg {
    position: relative;
}

.page {
    flex: 1 1 auto;
}

.authorization {
    position: relative;
    min-height: 100vh;
    overflow: hidden;
}

.authorization-main::before {
    content: "";
    position: absolute;
    top: 0;
    right: 0;
    width: 50.8%;
    height: 100%;
    display: block;
    background-color: #EDF2FB;
}

.wrapper > * {
    min-width: 0;
}



.authorization-main__container {
    position: relative;
    z-index: 2;
    display: flex;
    align-items: center;
    max-width: 1175px;
    min-height: 100vh;
}

.authorization-main__wrapper {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
}

.authorization-main .authorization-main__body {
    max-width: unset;
}

.authorization__image {
    position: relative;
    z-index: 2;
    padding-bottom: 42.533%;
    flex: 0 0 40.874%;
}

.authorization__image img {
    position: absolute;
    top: 0;
    left: 85px;
    z-index: 1;
    width: 100%;
    height: 100%;
    object-fit: cover;
}



img {
    vertical-align: top;
}

.authorization__dots {
    position: absolute;
    z-index: 1;
    animation: dots 2s ease-in-out infinite alternate-reverse;
}

/* .authorization__dots {
    position: absolute;
    z-index: 1;
    animation: dots 2s ease-in-out infinite alternate-reverse;
} */



.authorization__dots_1 {
    top: 4%;
    right:  400px;
}

.authorization__dots_2 {
    right: -13%;
    bottom: 4%;
}

.authorization__dots img {
    width: 100px;
    height: 110px;
}

@keyframes dots {
  from {
    top: 10px;
    bottom: 10px;
  }

  
}




</style>
