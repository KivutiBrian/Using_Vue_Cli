<template>
    <div class="user_friends">
        <ul>
            <li v-for="(friend, index) in friends" :key="index">{{ friend }} </li>
        </ul>
    </div>
</template>

<script>

import { bus } from '../../main.js'

export default {
    data(){
        return {
            friends: ['Mary', 'Luke', 'Stacy']
        }
    },
    created(){

        bus.$on('addfriend', (value)=>{
            this.friends.push(value)
        })
    }
}
</script>

<style>
    .user_friends {
        border: 1px solid thistle;
        padding: 10px 20px
    }

</style>