<template>
  <section class="container">
    <h1 class="title">
      User
    </h1>
    <h2 class="info">
      {{ user.name }}
    </h2>
    <nuxt-link class="button" to="/users">
      Users
    </nuxt-link>
  </section>
</template>

<script>
import axios from '~/plugins/axios'

export default {
  name: 'id',
  async asyncData ({ params, error }) {
    let { data } = await axios.get('/users/' + params.id)
    var user = data.data
    return { user: user }

    // // Or using callbacks.
    // return axios.get('/users/' + params.id)
    //   .then((res) => {
    //     console.log(res.data.data)
    //     return { user: res.data.data }
    //   })
    //   .catch((e) => {
    //     error({ statusCode: 404, message: 'User not found' })
    //   })
  },
  head () {
    return {
      title: `User: ${this.user.name}`
    }
  }
}
</script>

<style scoped>
.title
{
  margin-top: 30px;
}
.info
{
  font-weight: 300;
  color: #9aabb1;
  margin: 0;
  margin-top: 10px;
}
.button
{
  margin-top: 30px;
}
</style>
