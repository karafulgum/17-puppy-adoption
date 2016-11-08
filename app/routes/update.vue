<template lang="html">
  <div class="">
    <h2 class="title">Update the puppy's info</h2>
    <form @submit.prevent="savePuppy">
      <label class="label" for="puppy-name">Name</label>
      <p class="control">
        <input class="input" type="text" v-model="formValues.name" id="puppy-name">
      </p>

      <label class="label" for="puppy-age">Age</label>
      <p class="control">
        <input class="input" type="text" v-model="formValues.age" id="puppy-age">
      </p>

      <label class="label" for="puppy-sex">Sex</label>
      <p class="control">
        <span class="select">
          <select v-model="formValues.sex" id="puppy-sex">
            <option>Please select an option</option>
            <option>Male</option>
            <option>Female</option>
          </select>
        </span>
      </p>

      <label class="label" for="puppy-breed">Color</label>
      <p class="control">
        <input class="input" type="text" v-model="formValues.color" id="puppy-color">
      </p>

      <label class="label" for="puppy-breed">Breed</label>
      <p class="control">
        <input class="input" type="text" v-model="formValues.breed" id="puppy-breed">
      </p>

      <label class="label" for="puppy-image">Image Url</label>
      <p class="control">
        <input class="input" type="text" v-model="formValues.image_url" id="puppy-image">
      </p>

      <label class="label" for="puppy-description">Description</label>
      <p class="control">
        <textarea class="textarea" type="text" v-model="formValues.description" id="puppy-description"></textarea>
      </p>

      <p class="control">
        <a href="/" class="button">Back</a>
        <button class="button is-primary">Submit</button>
      </p>
    </form>
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
        this.$emit('updatePuppy', this.puppy.id, {
            adopted: true
        });
    },

    savePuppy() {
      this.$emit(this.puppy.id, this.formValues);
      this.$router.push({ name: 'index '});
    },
  },
};
</script>
