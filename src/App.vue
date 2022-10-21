<template>
  <div>
    <img :class="gender" :src="picture" alt="">
    <h1>{{firstName}} {{lastName}}</h1>
    <h3>Email: {{email}}</h3>
    <button :class="gender" @click="getUser">Get random user</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstName: 'John',
      lastName: 'Doe',
      email:'john@gmail.com',
      gender:'male',
      picture: 'https://randomuser.me/api/portraits/men/10.jpg'
    }
  },
  methods: {
    async getUser () {
      const res = await fetch(`https://randomuser.me/api`)
      const { results } = await res.json()
      console.log(results);

      this.firstName = results[0].name.first,
      this.lastName = results[0].name.last,
      this.email = results[0].email,
      this.gender = results[0].gender,
      this.picture = results[0].picture.large

    }
  }
}
</script>

<style>
  .male{
    border-radius: 50%;
    border: 5px solid dodgerblue;
  }

  .female{
    border-radius: 50%;
    border: 5px solid pink;
  }

  h1{
    font-size: 40px;
  }

  .male {
    background-color: dodgerblue;
  }

  .female {
    background-color: pink;
  }
</style>