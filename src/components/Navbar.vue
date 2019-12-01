<template>
  <nav class="navbar">
    <ul>
      <li><router-link to="/">Home</router-link></li>
      <li><router-link :to="{ name: 'About' }">About</router-link></li>
    </ul>
    <h2>User Profile</h2>
    <ul>
      <li v-for=" (id, index) in userIds" :key="index">
        <router-link :to="{ name: 'ViewProfile', params: {user_id: id }}">
          <span> Profile {{ id }} </span>
        </router-link>
      </li>
    </ul>
    <h2> Navigation Controls</h2>
    <ul>
      <li> <button @click="goBack">Go Back</button></li>
      <li> <button @click="goForward">Go Next</button></li>
      <li> <button @click="goHome">Redirect to home</button></li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  data() {
    return {
      userIds : [ '1', '2', '3', '4' ]
    }
  },
  methods: {
    goHome() {
     this.$router.push({ name: 'Home' })
    },
    goBack() {
      this.$router.go(-1)
    },
    goForward() {
      this.$router.go(+1)
    }
  }
}
</script>

<style>

ul {
   display :  inline-block;
   margin: 20px;
   padding: 0;
}

span {
  padding: 0;
}

li {
  list-style-type:none;
  display: inline;
  margin: 20px;
}

a {
  color: #42b983;
}

</style>
