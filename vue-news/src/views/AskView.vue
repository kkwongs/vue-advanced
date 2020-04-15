<template>
  <div>
    <div v-for="item in ask">{{ item.title }} </div>
    <!-- #3
    <div v-for="item in askitems">{{ item.title }} </div> -->
  </div>
</template>

<script>
import { mapState, mapGetters } from 'vuex';

export default {
  computed: {
    // #4
    ...mapGetters([
      'ask'
    ]),

    // #3
    // ...mapGetters({
    //   askitems: 'ask'
    // }),

    // #2
    // ...mapState({
    //   ask: state => state.ask
    // }),

    // #1
    // ask() {
    //   return this.$store.state.ask
    // },
  },
  created() {
    this.$store.dispatch('FETCH_ASK');
  },
}
</script>

<style>

</style>