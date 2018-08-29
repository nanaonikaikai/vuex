<template>
    <div>
        <h2>{{msg}}</h2>
        <hr/>
        <h3>{{$store.state.count}}-{{count}}-{{count}}}</h3>
        <div>
    <button @click="$store.commit('add',+10)">+</button>
    <button @click='reduce'>-</button>
    <br>
    <p>
  <button @click="addAction">+</button>
  <button @click="reduceAction">-</button>
</p>
</div>
    </div>
</template>
<script>
import store from "@/vuex/store";
import { mapState,mapMutations,mapGetters,mapActions } from "vuex";
export default {
  data() {
    return {
      msg: "Hello Vuex"
    };
  },
//   computed: {
//     count() {
//       return this.$store.state.count;
//     }
//   },
// computed:mapState({
//     count:state=>state.count
// }),

    computed:{
      ...mapState(["count"]),
      count(){
        return this.$store.getters.count;
        //return this.$store.state.a.count;
      }
    },
   methods:{
    ...mapMutations([  
        'add','reduce'
    ]),
    ...mapActions(['addAction','reduceAction'])
},
  store
};
</script>