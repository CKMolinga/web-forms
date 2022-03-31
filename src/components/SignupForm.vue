<template>
  <form>
    <label>Email:</label>
    <input type="email" required v-model="email">

    <label>Password:</label>
    <input type="password" required v-model="password">

    <label>Role</label>
    <select v-model="role">
      <option value="developer">web developer</option>
      <option value="designer">web designer</option>
    </select>
    
    <label for="">Skills</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill">
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteKill(skill)">{{ skill }}</span>
    </div>

    <div class="terms">
      <input type="checkbox" required v-model="terms">
      <label for="">Accept terms and conditions</label>
    </div>

  </form>

  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms accepted: {{ terms }}</p>
  <p>Nmaes: {{ names }}</p>
</template>

<script>
export default {
  data () {
    return {
      email: '',
      password: '',
      role: 'developer',
      terms: false,
      tempSkill: '',
      skills: [],
    }
  },
  methods: {
    addSkill (e) {
      if(e.key === ',' && this.tempSkill) {
        if(!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill)
        }
        this.tempSkill = ''
      }
    },
    deleteKill (skill) {
      this.skills.splice(this.skills.indexOf(skill), 1)
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
    padding: 40px;
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
    top: 2px;
    width: auto;
    margin-right: 10px;
  }

  .pill {
    display: inline-block;
    padding: 5px 10px;
    margin: 5px;
    border-radius: 5px;
    background: #eee;
    color: #777;
    font-size: 0.8em;
    font-weight: bold;
    cursor: pointer;
  }
</style>