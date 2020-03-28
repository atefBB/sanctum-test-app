<template>
    <div>
        <a href="#" @click.prevent="login">Login</a> |
        <a href="#" @click.prevent="logout">Logout</a> |
        <a href="#" @click.prevent="getUserInfo">User info</a>
    </div>
</template>

<script>
import axios from "axios";
export default {
    methods: {
        async login() {
            await axios.get("http://fresh.test/sanctum/csrf-cookie");

            await axios.post("http://fresh.test/login", {
                email: "foulen@ymail.com",
                password: "foulenfoulen"
            });
        },
        async logout() {
            await axios.post("http://fresh.test/logout");
        },
        async getUserInfo() {
            let response = await axios.get("http://fresh.test/api/user");
            console.log(response);
        }
    }
};
</script>
