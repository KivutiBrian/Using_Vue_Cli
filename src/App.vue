<template>
  <div>


    <Header />
    
    <div class="container">

        <Profile
        :userName="uname" 
        :lastName="lname" 
        :userAge="uage"
        :userParents="parents"
        @changeName="uname = $event"
        :updateLastName="updateLast"
        />
        <Friends />
    </div>
    

    <Footer />
  </div>
</template>

<script>

import Header from './components/header_footer/Header.vue'
import Footer from './components/header_footer/Footer.vue'
import Profile from './components/user/Profile.vue'
import Friends from './components/user/Friends.vue'

export default {
  name: 'app',
  components: {
        Header,
        Footer,
        Profile,
        Friends
  },
  data(){
    return{

        uname:'Kivuti',
        lname: 'Brian',
        uage:25,
        parents: {
            mother: "Agnes Mary",
            father: "John Doe"
        }
    }
  },

  methods:{

    updateLast(value){

        this.lname = value
    }
  }

}
</script>

<style>
  body {
    padding: 0;
    margin: 0;
    font-family: 'Roboto', sans-serif
  }

  .container {
    min-height: 84vh;
    box-sizing: border-box;
    padding: 20px
  }

</style>
