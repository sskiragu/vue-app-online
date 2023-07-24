<template>
    <div class="signup-form">
        <form @submit.prevent="signup" method="POST">
            <div class="form-input">
                <input type="text" placeholder="Enter username" v-model="username">
            </div>
            <div class="form-input">
                <input type="email" placeholder="Enter email" v-model="email">
            </div>
            <div class="form-input">
                <input type="password" placeholder="Enter password" v-model="password">
            </div>
            <div class="form-input">
                <button type="submit">Signup</button>
            </div>
        </form>
        <h1>Username: {{ username }}</h1>
        <h1>Email: {{ email }}</h1>
        <h1>Password: {{ password }}</h1>
    </div>
</template>

<script>
import { ref } from 'vue';
import axios from 'axios';

export default {
    setup(){
        const username = ref('')
        const email = ref('')
        const password = ref('')

        const signup = async () => {
            // console.log(`Username: ${username.value} Password: ${password.value} Email: ${email.value}`);
            try {
                await axios.post('http://127.0.0.1:8000/api/signup', {
                        username: username.value,
                        email: email.value,
                        password: password.value
                    });
                    console.log('Successful');
            } catch (error) {
                console.log(error);
            }

        }

        return { username, email, password, signup}
    }
}
</script>

<style scoped>
.signup-form .form-input{
    padding: 5px;
}
</style>