<script setup>
import { ref, onBeforeMount, onMounted } from 'vue'

const users = ref([])

onBeforeMount(async() => {
  // const host = 'lvm66115.sit.kmutt.ac.th'
  // const host = 'localhost:8080'
  // const res = await fetch(`http://${host}/api/users`)
  const res = await fetch(`/api/users`)
  const data = await res.json()
  users.value = data
})

onMounted(() => {
  console.log(users.value)
})

</script>

<template>
<h1>User</h1>
<table>
  <tr>
    <th>Id</th>
    <th>Name</th>
    <th>Email</th>
  </tr>
  <tr v-for="user in users" :key="user.id">
    <td>{{ user.id }}</td>
    <td>{{ user.name }}</td>
    <td>{{ user.email }}</td>
  </tr>
</table>
</template>