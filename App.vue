<template>
  <div>
    <div class="table">
      <div class="row">
        <div 
          v-for="(value, name, index) in objectArray[0]" 
          :key="index"
        >
          <p>{{ name }}</p>
        </div>
      </div>
      <div
        class="row"
        v-for="object, index in objectArray"
        :key="index"
      > 
        <div
          v-for="(value, name, index) in object"
          :key="index"
        >
          <p>{{value}}</p>
        </div>            
      </div>  
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      objectArray: {},
    }
  },
  methods: {
    async getStuff() {
      await fetch(``)
      .then(results => {
      return results.json()
      })
      .then(data => {
      this.objectArray = data
      })
    }
  },
  created() {
    this.getStuff()
  }
}
</script>

<style>
.table {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: auto;
  min-width: 10%;
} 

.row {
  display: flex;
  flex-direction: row;
}

p {
  min-width: 100px;
  font-size: .8rem;
}
</style>