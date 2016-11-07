<template lang="html">
  <div class="">
    <nav class="nav">
      <div class="nav-left">
        <router-link to="/"class="nav-item is-brand">Puppies</router-link>
      </div>
      <div class="nav-right">
       <router-link to="/" class="nav-item">All Puppies</router-link>
       <router-link to="/new" class="nav-item">Add Puppy</router-link>
      </div>
    </nav>

    <div class="section">
      <div class="container">
        <div class="columns">
          <div class="column is-4">
            <nav class="panel">
              <p class="panel-heading">
                Adopt A Pupper
              </p>
              <div class="panel-block" v-for="puppy in puppies">
                <div class="media">
                  <div class="media-left">
                    <p class="image is-64x64">
                      <img :src="puppy.image_url">
                    </p>
                  </div>
                  <div class="media-right">
                    <h2 class="subtitle">{{ puppy.name }}</h2>
                    <router-link :to="{ name: 'new', params: {id: puppy.id}}">Read More</router-link>
                  </div>
                </div>
              </div>
            </nav>
          </div>
          <div class="column is-8">
            <router-view
            :puppies="puppies"
            :api-url="apiUrl"
            @addPuppy="addPuppy"
            @updatePuppy="updatePuppy">
            </router-view>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const apiUrl = 'https://tiy-tn-class-api-fall-16.herokuapp.com/puppies/kara';

export default {
    data() {
        return {
          puppies: [''],
          apiUrl: apiUrl,
        };
    },

    mounted() {
      this.getData();
    },

    methods: {
      getData() {
        fetch(apiUrl)
        .then((r) => r.json())
        .then((puppies) => {
          this.puppies = puppies;
        });
      },

      addPuppy(input) {
        fetch(apiUrl, {
          method: 'POST',
          headers: { 'Content-Type': 'application/json'},
          body: JSON.stringify(input),
        })
        .then((r) => r.json())
        .then((newPup) => {
          this.puppies = [...this.puppies, newPup];

          this.$router.push({ name: 'index' });
        });

      },

      removePuppy() {

      },
      updatePuppy() {

      },
    },
};
</script>
