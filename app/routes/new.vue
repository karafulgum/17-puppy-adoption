<template lang="html">
  <div class="">
    <div class="control">
      <h1 class="title">Found a Pupper? We can help!</h1>
    </div>
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
  data() {
    return {
      formValues: {
        name: '',
        age: '',
        sex: '',
        color: '',
        breed: '',
        image_url: '',
        description: '',
      }
    };
  },

  methods: {
    savePuppy() {
      this.$emit('addPuppy', this.formValues);
    },
  },
};
</script>
