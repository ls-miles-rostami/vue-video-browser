<template>
  <div>
    <input v-model='search' :input='onInput()'/>
  </div>
</template>
<script>
export default {
  name: 'SearchBar',
  data(){
    return {
      search: ''
    }
  },
  methods: {
    onInput(){
      this.$emit('searchTermChange', this.search)
    }
  }
}
</script>
<style scoped>
  input{
    width: 75%;
  }
  div{
    text-align: center;
    margin: 20px;
  }
</style>
