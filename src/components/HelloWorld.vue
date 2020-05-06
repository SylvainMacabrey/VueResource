<template>
  <div class="container hello">
    <h1>{{ msg }}</h1>
    <table class="table">
      <thead class="info-color-dark white-text">
        <tr>
          <th scope="col">Nom complet</th>
          <th scope="col">Email</th>
          <th scope="col">Adresse</th>
          <th scope="col"></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.id">
          <td><input class="form-control" type="text" v-model="user.name"/></td>
          <td>{{ user.email }}</td>
          <td>{{ user.address.city }} - {{ user.address.street }}</td>
          <td>
            <router-link type="button" class="btn btn-primary btn-tab" :to="{name: 'User', params: {id: user.id}}">En savoir plus</router-link>
            <button type="button" class="btn btn-warning btn-tab" @click="save(user)">Modifier</button>
            <button type="button" class="btn btn-danger btn-tab" @click="destroy(user)">Supprimer</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Utilisation de Vue Ressource',
      users: []
    }
  },
  methods: {
    save (user) {
      this.$user.update({id: user.id}, {name: user.name}).then(
        (response) => {

        },
        (error) => {
          console.log('erreur', error)
        }
      )
    },
    destroy (user) {
      this.$user.remove({id: user.id}).then(
        (response) => {
          this.users = this.users.filter(u => u !== user)
        },
        (error) => {
          console.log('erreur', error)
        }
      )
    }
  },
  mounted () {
    this.$user = this.$resource('https://jsonplaceholder.typicode.com/users{/id}')
    this.$user.query().then(
      (response) => {
        this.users = response.data
      },
      (error) => {
        console.log('erreur', error)
      }
    )
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn-tab {
  font-size: 10px;
  padding: 5px;
}
</style>
