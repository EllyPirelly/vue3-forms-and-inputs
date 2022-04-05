<template>
  <form @submit.prevent="handleSubmit">
    <label>Email:</label>
    <input type="email" v-model="email" required />

    <label>Password:</label>
    <input type="password" v-model="password" required />
    <div class="error" v-if="passwordError">{{ passwordError }}</div>

    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup="addSkill" />
    <div class="pill" v-for="skill in skills" :key="skill">
      <span @click="removeSkill(skill)">{{ skill }}</span>
    </div>

    <div class="terms">
      <input type="checkbox" v-model="terms" required />
      <label>Accept terms and conditions</label>
    </div>
  </form>

  <button class="submit">create an account</button>

  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms accepted: {{ terms }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      role: 'developer',
      terms: false,
      tempSkill: '',
      skills: [],
      passwordError: '',
    }
  },

  methods: {
    addSkill(event) {
      if (event.key === ',' && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill)
        }
        this.tempSkill = ''
      }
    },

    removeSkill(skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item
      })
    },

    handleSubmit() {
      // validate password
      this.passwordError =
        this.password.length > 5 ? '' : 'Password must be at least 6 chars long'
      if (!this.passwordError) {
        console.log('email: ', this.email)
        console.log('password: ', this.password)
        console.log('role: ', this.role)
        console.log('skills: ', this.skills)
        console.log('terms accepted: ', this.terms)
      }
    },
  },
}
</script>

<style lang="scss">
form {
  background-color: #fff;
  border-radius: 10px;
  margin: 30px auto;
  max-width: 420px;
  padding: 40px;
  text-align: left;
}

label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
}

input,
select {
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
  display: block;
  padding: 10px 6px;
  width: 100%;
}

input[type='checkbox'] {
  display: inline-block;
  height: 16px;
  margin-right: 10px;
  width: 16px;
}

.pill {
  background-color: #eee;
  border-radius: 20px;
  color: #777;
  cursor: pointer;
  display: inline-block;
  font-size: 12px;
  font-weight: bold;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
}

button {
  background-color: #0b6dff;
  border: 0;
  border-radius: 20px;
  color: #fff;
  margin-top: 20px;
  padding: 10px 20px;
}

.submit {
  text-align: center;
}

.error {
  color: #ff0062;
  font-weight: bold;
  margin-top: 10px;
}
</style>
