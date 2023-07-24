<template>
    <div>
        <form @submit.prevent="login" method="POST">
            <div>
                <input type="text" name="username" placeholder="Enter username" v-model="user.username">
            </div>
            <div>
                <input type="password" name="password" placeholder="Enter password" v-model="user.password">
            </div>
            <div>
                <button type="submit">Login</button>
            </div>
        </form>
    </div>
</template>

<script>
import { ref } from 'vue';
import axios from 'axios';
import { useRouter } from 'vue-router';
    export default{
        // Composition API
        setup(){

        const user = ref({
            username: '',
            password: ''
        })

        const navigate = useRouter();

        const login = async () => {
            try {
                await axios.post('http://127.0.0.1:8000/api/login', user.value);
                navigate.push('/')
            } catch (error) {
                console.log('Failed');
            }
        }

        return {user, login}
    }
    }
</script>

<style scoped>

</style>