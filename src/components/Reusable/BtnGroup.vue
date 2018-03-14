<template>
  <div class="btn-group" role="group">
    <h5>{{ about.label }}:</h5>
    <button 
      type="button"  
      v-for="item in about.items"
      :key="item"
      :class="['btn', 'btn-default', { active: isActive(item) }]"
      @click="select(item)"
    >
      {{ item }}
    </button>
  </div>
</template>

<script>
export default {
  name: 'btn-group',
  props: { 
    active: { type:[Boolean, String], default: false },
    about: { 
      type: Object, 
      props: { 
        label: { type: String, required: true }, 
        items: { type: Array, required: true }
      } 
    },  
  },
  methods: {
    isActive(item){
      return this.active == item;
    },
    select(item){
      if(!this.isActive(item)){
        this.$emit('select', item);  
        return
      }
      this.$emit('select', false);
    }
  }
}
</script>
