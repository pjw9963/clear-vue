<template>
    <div id="background" >
        <h2>Cons</h2>
        <ul>      
          <li v-for="item in items" :key="item.id" >
            <input type="text" v-model="item.message" />
          </li>              
        </ul>
    </div>
</template>

<script>
  let data = {
    items: [
      {
        message: '',
        id: 0
      }      
    ]
  }

  export default {
    name: 'ConList',
    data: function() {
      return data;
    },
    props: {

    },
    watch: {
      items: {
        handler: function (val) {
          if (val[val.length - 1].message.length > 0 ) {
            this.items.push({ message: '', id: val.length })
          } 
          if (val[val.length - 1].message.length === 0 && val.length - 2 >= 0 && val[val.length - 2].message.length === 0){
            this.items.pop();
          }
        },
        deep: true
      }
    }      
  }
</script>

<style scoped>
  #background {
    background-color: #d68c86;
    width: 50%;
    text-align: center;
    min-height: 100vh;
  }
  input {
    outline:none;
    border: none;
    background-color: transparent;
  }  
</style>