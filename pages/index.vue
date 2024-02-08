<script lang="ts" setup>
const toggleValue = ref(1)
const comboValue = ref("First")

const items = ref([
  "First",
  "Second",
  "Third"
])

useAsyncData('test', async () => {
  toggleValue.value = 1
  comboValue.value = "Second"
}, {
  lazy: true
})
</script>

<template>
  <v-container>
    <v-row>
      <v-col cols="6">
        <v-btn-toggle v-model="toggleValue" divided mandatory variant="outlined">
          <v-btn text="First"/>
          <v-btn text="Second"/>
        </v-btn-toggle>
        <p>v-btn-toggle gives hydration class mismatch when the model is set with useAsyncData</p>
      </v-col>
      <v-col>
        <v-combobox v-model="comboValue" :items="items"></v-combobox>
        <p>No mismatch for combobox</p>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>

</style>