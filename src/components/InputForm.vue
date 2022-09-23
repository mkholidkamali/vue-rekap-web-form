<template>
    <form>
        <label>Email :</label>
        <input type="email" required v-model="email">

        <label>Password</label>
        <input type="password" required v-model="password">

        <label>Role</label>
        <select v-model="role">
            <option value="programmer">Web Programmer</option>
            <option value="designer">Web Designer</option>
        </select>

        <label>Skills</label>
        <input type="text" v-model="skills">

        <label>ACCEPT TERMS AND CONDITION</label>
    </form>

    <p>Email : {{ email }}</p>
    <p>Password : {{ password }}</p>
    <p>Role : {{ role }}</p>
    <p>Skills : {{ skills }}</p>
</template>

<script>
export default {
    data() {
        return {
            email: "",
            password: "",
            role: "",
            skills: []
        }
    }
}
</script>

<style>
form {
    background: #fff;
    margin: 30px auto;
    padding: 40px;
    max-width: 400px;
    border-radius: 10px;
    text-align: left;
}
label {
    display: block;
    color: #aaa;
    font-size: 0.6em;
    margin: 25px 0 15px;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input, select {
    display: block;
    padding: 10px 6px;
    border: 0;
    box-sizing: border-box;
    border-bottom: 1px solid black;
    color: #555;
    width: 100%;
}
</style>