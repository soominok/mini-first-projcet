<template id="mainPage">
  <v-main>
    <br><br>
      <v-card width="1500" justify="center" class="px-3">
        <v-img
          src="https://investorplace.com/wp-content/uploads/2019/05/stock-picks-1024x683.jpg"
          height="600"
          class="grey darken-4"
        ></v-img>
        <!-- <v-card-title class="title">height</v-card-title> -->
      </v-card>
  </v-main>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
/* eslint-disable no-unused-vars */
import store from '../store'
import Vue from 'vue'
import cookies from 'vue-cookies'
import { mapState, mapGetters, mapActions } from 'vuex'

Vue.use(cookies)

export default {
  name: 'Home',
  data: function () {
    return {
      items: [
        {
          src: 'https://investorplace.com/wp-content/uploads/2019/05/stock-picks-1024x683.jpg'
        }
      ]
    }
  },
  methods: {
    onClickLogout () {
      this.logout()
      alert('Success Logout')
      this.$router.push({ name: 'Home' })
    },
    clickBoards (boardNo) {
      console.log('clickBoards: ' + boardNo)
    },
    start (category) {
      this.$store.dispatch('boardFind', category)
    },
    ...mapActions(['logout'])
  },
  computed: {
    ...mapState(['myinfo']),
    ...mapGetters(['isAuthorized']),
    ...mapState({
      lists: state => state.lists
    })
  },
  components: {
  }
}
</script>

<style scoped>
#header {
  padding: 40px;
  margin-bottom: 15px;
  margin: 0px 0px;
}
img {
  width: auto;
  height: auto;
  max-width: 1000px;
  max-height: 350px;
  display: block;
  margin-left: auto;
  margin-right: auto;
}
#login {
  background-color: #77aadd;
  color: #ffffff;
  font-weigth: bold;
  float: right;
}
</style>
