<script >
export default{
  data(){
    return{
      input : '',
      shoppingList: [],
    }
  },
  methods:{
    addItem(){
      if(!this.input)
      return;
    this.shoppingList.push(this.input)
    this.input = '';
    this.$refs.input.focus()
    },
    deleteItem(i){
      if(i < 0 || i > this.shoppingList.length)
      return;
    this.shoppingList = this.shoppingList.filter(
      (item, index ) => index !== i
    );
    },
    deleteAll(){
      this.shoppingList = []
    }
  }

}

</script>

<template>
  <div>
    <div class=" container">
      <h2>New Shopping Cart</h2>
      <div class='user-input'>
        <input
        placeholder = 'Press Enter to Add a new item'
        v-model="input"
        @keyup.enter="addItem"
        ref="input"/>
        <button @click="additem"> Add Item</button>
      </div>
      <ul v-if="shoppingList > 0">
        <li v-for='(item, i) in shoppingList' :key="i" class="item">
          <span>{{ item }}</span>
          <button class="remove-button" @click='deleteItem'> Remove</button>
        </li>
      </ul>
      <br/>
      <button class="button-delete" @click="deleteAll">Delete ALL</button>
    </div>
  </div>
  
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
  .container {
  max-width: 600px;
  margin: 80px auto;
}

.item {
  display: flex;
  justify-content: space-between;
}

// Type
.h2 {
  font-size: 21px;
}

.user-input {
  display: flex;
  align-items: center;
  padding-bottom: 20px;
  input {
    width: 100%;
    padding: 10px 6px;
    margin-right: 10px;
  }
}

.item {
  display: flex;
  align-items: center;
}

// Buttons
button {
  appearance: none;
  padding: 10px;

  font-weight: bold;
  border-radius: 10px;
  border: none;
  background: $color-grey;
  color: white;
  white-space: nowrap;

  + button {
    margin-left: 10px;
  }
}

.button--delete {
  display: block;
  margin: 0 auto;
  background: red;
}

.button--remove {
  background: none;
  color: red;
  text-transform: uppercase;
  font-size: 11px;
  align-self: flex-end;
}

ul {
  display: block;
  margin: 0 auto;
  padding: 30px;
  border: 1px solid rgba(0, 0, 0, 0.25);

  > li {
    color: $color-grey;
    margin-bottom: 4px;
  }
}
}
</style>
