<template>
  <div :class="selected">
    <slot></slot>
  </div>
</template>

<script>

function genParams(){
  let cols = ['xs', 'sm', 'md', 'lg'];
  let params = {};

  cols.map( col => {
    for(let size = 1; size <= 12; size++){
      params[col + size] = { type: Boolean, default: false }
    }
  });

  return params
}

function getAllCols(){
  let cols = ['xs', 'sm', 'md', 'lg'];
  let allCols = [];
  cols.map( col => {
    for(let size = 1; size <= 12; size++){
      allCols.push(col + size)
    }
  });
  return allCols
}

export default {
  name: 'b-col',
  props: {...genParams()},
  data(){
    return { 
      allCols: getAllCols(),
    }  
  },
  computed: {
    selected(){
      let re = /([a-z]+|\d+)/g

      return this.allCols
        .filter( col => this[col] == true )
        .map( col => {
          let result = col.split(re)
          return `col-${result[1]}-${result[3]}`
        });
    }
  }
}
</script>
