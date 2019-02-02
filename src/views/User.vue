<template lang="pug">
  div
    h1 Página usuario
    button(@click="changeName('alexis')") Cambiar a Alexis
    button(@click="changeName('santi')") Cambiar a Santi
    router-link(:to="{name: 'about', query: {ref: 'link'}}") Ir a casa
    router-view
</template>

<script>
export default {
  data () {
    return {
      name: 'Santi'
    }
  },
  methods: {
    sayHi () {
      console.log('hola');
    },
    changeName (name) {
      this.name = name

      this.$router.push({
        name: 'user-profile',
        params: {
          user_id: name
        },
        query: {
          ref: 'button'
        }
      })
    },
    async getApiResponse () {
      try {
        let response = await this.$axios.get('https://yesno.wtf/api')
        console.log('response')
        console.log(response.data)
      } catch (e) {
        console.log(e);
      }
    }
  },
  computed: {
    reverseName () {
      return this.name.split('').join('.')
    }
  },
  watch: {
    name (val) {
      console.log(val);
    },
    '$route': to => {
      console.log('USER:')
      console.log(to)
    }
  },
  created () {
    console.log('created');
  },
  mounted () {
    console.log('mounted');
    this.getApiResponse()
  }
}
</script>

<style lang="css" scoped>
</style>
