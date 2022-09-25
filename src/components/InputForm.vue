<template>
    <form @submit.prevent="submit">
        <label>Email :</label>
        <input type="email" required v-model="email">

        <label>Password</label>
        <input type="password" required v-model="password">
        <span v-if="passwordError" class="error">{{ passwordError }}</span>

        <label>Role</label>
        <select v-model="role">
            <option value="programmer">Web Programmer</option>
            <option value="designer">Web Designer</option>
        </select>

        <label>Skills</label>
        <input type="text" v-model="tempSkill" @keyup.ctrl="addSkill">
        <div v-for="skill in skills" :key="skill" class="pill">
            {{ skill }} <span @click="removeSkill(skill)">❌</span>
        </div>

        <div class="terms">
            <input type="checkbox" v-model="terms">
            <label>ACCEPT TERMS AND CONDITION</label>
        </div>

        <div class="submit">
            <button>Submit</button>
        </div>
    </form>

    <p>Email : {{ email }}</p>
    <p>Password : {{ password }}</p>
    <p>Role : {{ role }}</p>
    <p>Skills : {{ skills }}</p>
    <p>Terms : {{ terms }}</p>
</template>

<script>
export default {
    data() {
        return {
            email: "",
            password: "",
            role: "",
            tempSkill: '',
            skills: [],
            terms: false,
            passwordError: ""
        }
    },
    methods: {
        addSkill(e) {
            if(e.key === "Enter" && this.tempSkill) {
                this.skills.push(this.tempSkill)
                this.tempSkill = ''
            }
        },
        removeSkill(skill) {
            this.skills = this.skills.filter((item) => {
                return item !== skill
            })
        },
        submit() {
            this.passwordError = this.password.length > 5 ? '' : "Password must be min 5 characters"
            if (!this.passwordError) {
                console.log("Berhasil Menambah Data")
            }
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
    display: inline-block;
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
input[type="checkbox"] {
    display: inline-block;
    position: relative;
    width: 16px;
    margin: 16px;
    top: 2px;
}
.pill {
    display: inline-block;
    padding: 6px 12px;
    background: #eee;
    margin: 20px 10px 0 0;
    border-radius: 20px;
    font-weight: bold;
    letter-spacing: 1px;
    font-size: 12px;
    color: #477;
    cursor: pointer;
}
.error {
    color: red;
    font-weight: bold;
    display: block;
}
.submit {
    text-align: center;
}
button {
    border-radius: 30px;
    padding: 10px 30px;
    background:#477;
    border: 0px;
    color: white;
    margin-top: 20px;
}
</style>