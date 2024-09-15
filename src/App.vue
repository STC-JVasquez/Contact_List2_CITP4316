<script setup>
import {ref} from 'vue'

//variables
const name = ref('')
const phone = ref('')
</script>

<template>
  <main class="app">
    <section class="contact-form">
      <h2> Contact list</h2>
      <form @submit.prevent="addContact">
        <div>
          <label for="name">Name:</label>
          <input type="text" id="name" v-model="name" placeholder="Enter name" />
        </div>
        <div>
          <label for="phone">Phone:</label>
          <input type="text" id="phone" v-model="phone" placeholder="Enter phone" />
        </div>
      </form>

    </section>
  </main>

</template>
