<script setup lang='ts'>
import {ref} from 'vue';

const username = ref<string>('');
const password = ref<string>('');

const login = () => {
    fetch('api/login', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            "username": username.value,
            "password": password.value
        })
    })
}
</script>


<template>
    <div class="login">
        <h1>Login Page</h1>
        <div>
            user:
            <input v-model="username" type="text" size="10" />
        </div>
        <div>
            password:
            <input v-model="password" type="password" size="10" />
        </div>
        <button @click="login">login</button>
    </div>
</template>