<template>
    <NavBar />
    <h1>{{ title }}</h1>
    <input type="password" @input="validatePassword" v-model="password" />
    <p v-if="password.length > 0" :style="{ color: msgColor }">{{ message }}</p>
</template>

<script>
import NavBar from './components/NavBar.vue';
export default {
    data() {
        return {
            title: "Password Validate!",
            message: "",
            msgColor: "",
            password: ""
        };
    },
    methods: {
        validatePassword() {
            const password = this.password;
            const isValid = /[a-zA-z]/.test(password)
                && /\d/.test(password) && password.length >= 8;
            if (isValid) {
                this.message = "Password Valid";
                this.msgColor = "green";
            }
            else {
                this.message = "Password Invalid";
                this.msgColor = "red";
            }
        }
    },
    components: { NavBar }
}
</script>

<style scoped></style>