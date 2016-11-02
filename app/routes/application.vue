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
              <div class="panel-block">
                <div class="media">
                  <div class="media-left">
                    <p class="image is-64x64">
                      <img src="http://placehold.it/128x128">
                    </p>
                  </div>
                  <div class="media-right">
                    <h2>Pupper Name Here</h2>
                  </div>
                </div>
              </div>
            </nav>
          </div>
          <div class="column is-8">
            <router-view>

            </router-view>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    data() {
        return {

        };
    },

    methods: {

    },
};
</script>
