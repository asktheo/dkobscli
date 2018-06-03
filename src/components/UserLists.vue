 <template>
    <div v-if="(vis)">
        <span><b>{{navn}}</b></span>
        <div id="lister" v-for="b in liste" v-bind:key="b.species_id">
        <span>{{b.bird_name}}</span>
        </div>
    </div>
</template>

<script>
export default {
  name: 'UserLists',
  props:  ['liste','navn','vis']
  }
</script>