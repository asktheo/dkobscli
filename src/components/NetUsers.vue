<template>
    <div style="width:30%; float:right">
        <div v-bind:key="u.id" v-for="u in netUsers">
            <input type="checkbox" v-model="u.valgt" true-value="yes" false-value="no"/>
            <span>{{u.navn}}</span>
        </div>
        <span v-if="2 === antalValgt"><button v-on:click="compare()">Sammenlign</button></span>
    </div>
</template>

<script>

export default {
  name: 'NetUsers',
  props: ['netUsers'],

  methods: {
        filterValgte : function(){
            return this.netUsers.filter( u => u.valgt == "yes");
        },
        compare : function() {this.$emit('user-compare',this.filterValgte())}
    },

    computed: {
        antalValgt : function(){
            return this.netUsers.filter( u => u.valgt == "yes").length;
        }
    },

    watch: {
        antalValgt: function(ant){
               if(ant == 2) this.$emit('user-load',this.filterValgte())}
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
