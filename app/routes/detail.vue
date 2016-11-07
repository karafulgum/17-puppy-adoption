<template lang="html">
  <div class="">
    <h1 class="title has-text-centered">{{ puppy.name }}</h1>
    <div class="columns">
      <div class="column is-half is-offset-one-quarter">
        <figure class="image is-square">
          <img :src="puppy.image_url">
        </figure>
      </div>
    </div>
    <nav class="level">
      <div class="level-item has-text-centered">
        <p class="heading">Age</p>
        <p class="title">{{ puppy.age }}</p>
      </div>
      <div class="level-item has-text-centered">
        <p class="heading">Breed</p>
        <p class="title">{{ puppy.breed }}</p>
      </div>
      <div class="level-item has-text-centered">
        <p class="heading">Color</p>
        <p class="title">{{ puppy.color }}</p>
      </div>
      <div class="level-item has-text-centered">
        <p class="heading">Sex</p>
        <p class="title">{{ puppy.sex }}</p>
      </div>
    </nav>

    <div class="content">
      <h3>About Me</h3>
      <p>{{ puppy. description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['apiUrl'],

  data() {
    return {
      puppy: {},
      id: this.$route.params.id,
    };
  },

  mounted() {
    this.getData();
  },

  methods: {
    getData() {
      fetch(`${this.apiUrl}/${this.$route.params.id}`)
      .then((r) => r.json())
      .then((puppy) => {
        this.puppy = puppy;
      });
    },
  },
};
</script>
