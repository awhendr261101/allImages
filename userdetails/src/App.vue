<template>
  <form action="" class="container">
    <div>
      <input entry type="text" v-model="firstName" @keyup="removeStars"><span stars>*</span>
    </div>

    <div>

      <input entry type="text" v-model="lastName" @keyup="removeStars"><span stars>*</span>
    </div>

    <div>
    <input entry type="text" v-model="gender" :class='{
      male: lowerCaseGender == "male",
      female: lowerCaseGender == "female"
      
      }' @keyup="removeStars"><span stars>*</span>

    </div>
    <textarea output readonly></textarea>
    <button @click="userInfo" type="button">DIsplay</button>
  </form> 
</template>

<script>

export default {
  name: 'App',
  components: {
    
  },
  data () {
    return {
      firstName : '',
      lastName : '',
      gender : '',
    }

  },

  computed:{
    lowerCaseGender(){
      return this.gender.toLowerCase()
    }
  }
  
  ,
  methods: {
    userInfo(){
      document.querySelector("[output]").textContent = `
        First Name: ${this.firstName}
        last Name: ${this.lastName}
        gender: ${this.gender}
      `
    },

    removeStars(){
      console.log("keyup");
      document.querySelectorAll("[entry]").forEach((element, index) => {
        if (element.value.length > 0) {
          document.querySelectorAll("[stars]").forEach((star, position) => {
            if (position == index) {
              star.textContent = ""
            }
          });
        } else {
          document.querySelectorAll("[stars]").forEach((star, position) => {
            if (position == index) {
              star.textContent = "*"
            }
          });
        }
          
      });
    }

   
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container{
  display: grid;
  gap: 0.2rem;
  width: 30rem;
  margin-inline: auto;
}

input{
  text-align: center;
}

.male{
  border: 2px solid #2c3e50;
}

.female{
  border: 2px solid pink;
}
</style>
