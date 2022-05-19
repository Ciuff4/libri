<template>
  <div>
      <h5>Titolo: {{titolo}}</h5>
      <p>Primo Anno di Pubblicazione{{annoPubblicazione}}</p>
      <h6>Editori:</h6>
      <ul>
          <li v-for="(editore ,index) in editori" :key="`editore${index}`">{{editore}}</li>
      </ul>
  </div>
</template>

<script>
export default {
nome:'BookComp',
props:{
   titolo:String,
   annoPubblicazione:Number,
   editori:Array,
}
}
</script>

<style lang="scss" scoped>
li{
    font-size: 0.7rem;
}
</style>