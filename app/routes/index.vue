<template lang="html">
  <div class="">
    <div class="control is-grouped">
      <div class="nav-left">
        <h1 class="title">Puppies for Adoption</h1>
      </div>
      <div class="nav-right">
        <router-link class="button is-primary":to="{ name: 'new' }">Add A Pupper</router-link>
      </div>
    </div>
    <table class="table">
      <thead>
        <th>Name</th>
        <th>Age</th>
        <th></th>
      </thead>
      <tbody>
        <tr v-if="!puppy.adopted" v-for="puppy in puppies">
          <td>{{ puppy.name }}</td>
          <td>{{ puppy.age }}</td>
          <td>
            <router-link :to="{ name: 'detail', params: {id: puppy.id}}">read more</routerlink>
          </td>
        </tr>
      </tbody>
    </table>
    <div class="control">
      <h1 class="title">Adopted Puppers</h1>
    </div>
    <table class="table">
      <thead>
        <th>Name</th>
        <th>Age</th>
        <th></th>
      </thead>
      <tbody>
        <tr v-if="puppy.adopted" v-for="puppy in puppies">
          <td>{{ puppy.name }}</td>
          <td>{{ puppy.age }}</td>
          <td>
            <router-link :to="{ name: 'detail', params: {id: puppy.id}}">read more</routerlink>
          </td>
      </tr>
  </div>
</template>

<script>
export default {
    props: ['puppies'],

    data() {
        return {};
    },

    methods: {

    },
};
</script>
