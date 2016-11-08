<template lang="html">
  <div class="">
    <h1 class="title has-text-centered">{{ puppy.name }}
      <a class="button is-primary" @click="update" v-if="!puppy.adopted">
        <span class="icon is-small">
          <i class="fa fa-paw" aria-hidden="true">
        </span>
        <span>Adopt Me</span>
      </a>
      <a class="button is-success" v-if="puppy.adopted">
        <span class="icon is-small">
          <i class="fa fa-paw" aria-hidden="true">
        </span>
        <span>I'm adopted!</span>
      </a>
    </h1>
  <div class="columns">
      <div class="column is-half is-offset-one-quarter">
        <figure class="image">
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

    <div class="control is-grouped">
      <p class="control">
        <a class="button is-primary is-outlined" @click="removePuppy">
          <span class="icon is-small">
            <i class="fa fa-times"></i>
          </span>
            <span>Delete Puppy</span>
        </a>
      </p>
      <p class="control">
        <router-link class="button is-primary is-outlined" :to="{ name: 'update', params: { id: puppy.id }}">Edit Puppy</router-link>
      </p>
    </div>
  </div>

</template>

<script>
export default {
  props: ['findPuppy', 'puppies'],

  data() {
    return {
      puppy: {},
      id: this.$route.params.id,
    };
  },

  mounted() {
    this.getData();
  },

  watch: {
    '$route': 'getData',
    'puppies': 'getData',
  },

  methods: {
    getData() {
      this.findPuppy(this.$route.params.id)
      .then((puppy) => {
        this.puppy = puppy;
      });
    },

    update() {
      this.$emit('updatePuppy', this.puppy.id, { adopted: true});
    },

    removePuppy() {
      if (confirm('Are you sure you want to delete this puppy?')) {
        this.$emit('removePuppy', this.puppy);
      }
    },
},
};
</script>
