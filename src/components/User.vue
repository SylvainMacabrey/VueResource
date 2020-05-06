<template>
  <div class="container">
    <h1>{{ user.name }}</h1>
    <ul class="nav nav-pills" id="pills-tab" role="tablist">
      <li class="nav-item">
        <a class="nav-link active" id="pills-home-tab" data-toggle="pill" href="#pills-adresse" role="tab"
          aria-controls="pills-home" aria-selected="true">Adresse</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" id="pills-company-tab" data-toggle="pill" href="#pills-company" role="tab"
          aria-controls="pills-company" aria-selected="false">Companie</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" id="pills-contact-tab" data-toggle="pill" href="#pills-contact" role="tab"
          aria-controls="pills-contact" aria-selected="false">Contact</a>
      </li>
    </ul>
    <div class="tab-content pt-2 pl-1" id="pills-tabContent">
      <div class="tab-pane fade show active" id="pills-adresse" role="tabpanel" aria-labelledby="pills-adresse-tab">
        <p>Ville : {{ user.address.city }}</p>
        <p>Rue : {{ user.address.street }}</p>
        <p>Zip code : {{ user.address.zipcode }}</p>
      </div>
      <div class="tab-pane fade" id="pills-company" role="tabpanel" aria-labelledby="pills-company-tab">
        <p>{{ user.company.name }} - " {{ user.company.catchPhrase }} "</p>
      </div>
      <div class="tab-pane fade" id="pills-contact" role="tabpanel" aria-labelledby="pills-contact-tab">
        <p>Adresse mail : {{ user.email }}</p>
        <p>Téléphone : {{ user.phone }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'User',
  data () {
    return {
      user: {}
    }
  },
  mounted () {
    this.id = this.$route.params.id
    this.$user = this.$resource('https://jsonplaceholder.typicode.com/users/' + this.id)
    this.$user.query().then(
      (response) => {
        this.user = response.data
      },
      (error) => {
        console.log('erreur', error)
      }
    )
  }
}
</script>
