<script setup>
import {ref , onMounted, watch} from 'vue'

//variables
const name = ref('')
const phone = ref('')
const contacts = ref([])

//add new contact function
const addContact = () => {
  if (name.value.trim() === '' || phone.value.trim() === '') {
    return
  }
  //combine name and number
  contacts.value.push(`${name.value}: ${phone.value}`)

  //clear fields after adding
  name.value = ''
  phone.value = ''
}

//remove a contact
const removeContact = (contact) => {
  contacts.value = contacts.value.filter(item => item !== contact)
}

//load data from storage when component is mounted
onMounted(() => {
  contacts.value = JSON.parse(localStorage.getItem('contacts')) || []
})

//save changed to storage
watch(contacts, (newVal) => {
  localStorage.setItem('contacts', JSON.stringify(newVal))
}, {deep: true})
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
        <button type="submit">Add Contact</button>
      </form>
    </section>

    <section class="contacts-list">
      <h3>Saved Contacts</h3>
      <div class="list">
        <div v-for="contact in contacts" :key = "contact" class="contact-item">
          <div class="contact-content">
            <span>{{ contact }}</span>
            <div class="actions">
              <button class="delet" @click="removeContact(contact)">Remove</button>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>

</template>
