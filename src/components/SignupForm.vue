<template>
    <form>
        <label>Email:</label>
        <input type="email" required v-model="email">

        <label>Password:</label>
        <input type="password" required v-model="password">

        <label>Role:</label>
        <select v-model="role">
            <option value="designer">Web Designer</option>
            <option value="developer">Web Developer</option>
        </select>

        <div>
            <input type="checkbox" value="permanent" v-model="jobType">
            <label>Permanent</label>
        </div>
        <div>
            <input type="checkbox" value="temporary" v-model="jobType">
            <label>Temporary</label>
        </div>

        <label>Skills:</label>
        <input type="text" v-model="tempSkill" @keypress="addSkill">
        <div v-for="skill in skills" :key="skill" class="pill">
            <span @click="deleteSkill(skill)">{{ skill }}</span>
        </div>

        <div>
            <input type="checkbox" required v-model="isTermAccepted">
            <label>Accept terms and conditions</label>
        </div>

    </form>

    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Roll: {{ role }}</p>
    <p>Terms: {{ isTermAccepted }}</p>
    <p>Job type: {{ jobType }}</p>

</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            role: '',
            isTermAccepted: '',
            jobType: [],
            tempSkill: '',
            skills: []
        }
    },
    methods: {
        addSkill(e){
            if(e.key === 'Enter' && this.tempSkill)
            {
                if (!this.skills.includes(this.tempSkill))
                {
                    this.skills.push(this.tempSkill)
                }
                this.tempSkill = '';
            }
        },
        deleteSkill(skill)
        {
            this.skills = this.skills.filter((item) => {
                return item !== skill
            })
        }
    }
}
</script>

<style>
form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40pt;
    border-radius: 10px;
}
label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input, select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}
input[type="checkbox"] {
    display: inline-block;
    position: relative;
    margin: 0 10px 0 0;
    top: 2px;
    width: 16px;
}
.pill
{
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}
</style>
