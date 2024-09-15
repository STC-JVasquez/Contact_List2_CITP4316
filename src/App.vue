<script setup>
import {ref} from 'vue'
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
      </form>

    </section>
  </main>

</template>
