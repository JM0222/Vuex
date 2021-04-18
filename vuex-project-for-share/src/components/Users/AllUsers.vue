<template>
  <div>
    <h1>All Users</h1><br/>
    <h1>{{allUsersCount}}</h1>
    <h1>카운트오브서울{{$store.getters.countofSeoul}}</h1>
    <h1>레이트오브서울{{$store.getters.rateofSeoul}}</h1>




    <v-list two-line>
      <v-list-tile 
        v-for="(user, index) in allUsers"
        :key="index"
        avatar
      >
        <v-list-tile-avatar color="grey lighten-3">
          <img :src="user.src">
        </v-list-tile-avatar>

        <v-list-tile-content>
          <v-list-tile-title v-html="user.name"></v-list-tile-title>
          <v-list-tile-sub-title>id:#{{index}} / {{user.address}} 거주</v-list-tile-sub-title>
        </v-list-tile-content>
      </v-list-tile>
    </v-list>

  </div>
</template>

<script>
import { EventBus } from '@/main.js'
import { mapStatus, mapGetters } from 'vuex'
  export default {
    data() {
      return {
        // 중앙집중식 관리소 

       
      }
    },
    computed:{
      ...mapGetters(['allUsersCount','countofSeoul','rateofSeoul']),
      ...mapStatus(['allUsers'])

    },
    mounted() {
      EventBus.$on('signUp', users => {
        this.$store.state.allUsers.push(users)
      })
    }
  }
</script>
