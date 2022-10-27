<template>

  <vue-select class="" v-if="users" v-model="user" label="first_name" :options="users">
    <template v-slot:option="option">
      <div class="d-flex align-items-center">
        <div>
          <div class="font-weight-bold">
            <img :src="option.avatar" class="rounded-circle" width="32" height="32"/>
            {{ option.first_name }} {{ option.last_name }}
          </div>
          <div class="text-muted">{{ option.email }}</div>
        </div>
      </div>
    </template>
    <template v-slot:selected-option="option">
      <div class="d-flex align-items-center">
        <div>
          <div class="font-weight-bold">
            <img :src="option.avatar" class="rounded-circle" width="32" height="32"/>
            {{ option.first_name }} {{ option.last_name }}
          </div>
        </div>
      </div>
    </template>
  </vue-select>
  <div>
    <pre style="text-align: left;"></pre>
    <div class="card">
      <div class="img-avatar" v-if="user">
        <img :src="user.avatar" class="rounded-circle" width="64" height="64"/>
      </div>
      <div class="card-text">
        <div class="portada">

        </div>
        <div class="title-total">
          <div class="title" v-if="user">{{ user.employment.title }}</div>
          <h2 v-if="user"> {{ user.first_name }} {{ user.last_name }}</h2>
          <div v-if="user">

          </div>

          <div class="desc" v-if="user">

          </div>
          <div class="actions">
            <button><i class="far fa-heart"></i></button>
            <button><i class="far fa-envelope"></i></button>
            <button><i class="fas fa-user-friends"></i></button>
          </div>
        </div>
      </div>
    </div>
  </div>
  <HelloWorld/>

</template>

<script>
import vueSelect from 'vue-select'
import 'vue-select/dist/vue-select.css';
import './assets/style.css';

export default {
  name: 'App',
  data() {
    return {
      users: [],
      user: null
    }
  },
  methods: {
    async fetchUsers() {
      let response = await fetch('https://random-data-api.com/api/v2/users?size=100&is_json=true', {
        "Content-Type": "application/json",
      })
      this.users = await response.json()
    }
  },
  components: {
    vueSelect,
  },
  mounted() {
    this.fetchUsers()
    console.log(require('vue'))
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
</style>
