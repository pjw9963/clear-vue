<template>
    <div id="background" >
        <h2>Cons</h2>
        <ul>      
          <li v-for="item in items" :key="item.id" >
            <Editable v-model="item.message" ></Editable>
          </li>              
        </ul>
    </div>
</template>

<script>
  import Editable from './Editable'


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
    components: {
      Editable
    },
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
            this.items.pop(); //I do not know why this if statement is nessesary, for somereason an extra linefeed is added
          }

          if(val.length - 2 >= 0 && val[val.length - 2].message.charCodeAt(0) === 10) {
            val[val.length - 2].message = '';
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
  li {
    font-size: 1.5rem;
    padding: 1% 5%;
  }  
</style>