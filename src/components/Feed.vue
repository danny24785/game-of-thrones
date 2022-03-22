<template>
    <ol>
      <li v-for="character in characters" v-bind:key="character.id" class="character-details">
        <ul>
          <li v-if="character.name">Name: {{ character.name }}</li>
          <li>Gender: {{ character.gender }}</li>
          <li v-if="!character.died">Is alive: Yes</li>
          <li v-else>Is alive: No ( died {{ character.died }} )</li>
        </ul>
      </li>  
    </ol>
</template>
<script>
export default {
    name: 'Feed',
    props: {
        characters: Array
    }
}

</script>
<style scoped>

</style>