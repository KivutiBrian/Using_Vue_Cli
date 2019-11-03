<template >
    <div>
        <div class="user_profile">
            <h3>User information</h3>
            <ul>
                <li><span>First Name:</span>{{ userName }}</li>
                <li><span>Last Name:</span>{{ lastName }}</li>
                <li><span>Age:</span>{{ userAge }}</li>
            </ul>
            <h3>Parents Details</h3>
            <ul>
                <!-- <li><span>Mother:</span>{{ userParents.mother }}</li>
                <li><span>Father:</span>{{ userParents.father }}</li> -->

                <!-- or -->
                <li v-for="(key,value,index) in userParents" :key="index">
                    <span>{{ value }}</span>: {{ key }}
                    
                </li>
            </ul>
        </div>

        <button @click="updateName">Update name</button>
        <button @click="updateLastName('Jonny')">Update Last Name</button>
        <br>
        <input type="text" v-model="newFriend" @keyup.enter="addFriend">
        <br>
    </div>
    
</template>

<script>

import { bus } from '../../main.js'

export default {
    props:{
        userName: String,
        lastName: String,
        userAge: Number,
        userParents: Object,
        updateLastName: Function
    },
    data(){
        return {
            newFriend: ''
        }
    },
    methods:{
        updateName(){
            this.$emit('changeName', 'Peter')
        }, 

        addFriend(){
            bus.$emit('addfriend', this.newFriend)
            this.newFriend = ''
        }
    }
}
</script>



<style>
    span {
        font-weight: 800
    }
    .user_profile {
        border: 1px solid thistle;
        padding: 10px 20px
    }
</style>