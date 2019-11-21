<template>
  <v-container>
    <v-layout row wrap>
      <v-flex>
        {{message}}
        <ul>
          <li v-for="item in list" :key="item.name">
            {{ item.name }} - {{ item.amount }}
            <v-btn color="success" x-small @click="item.amount++">+</v-btn>
            <v-btn
              :disabled="item.amount <= 0"
              color="error"
              x-small
              @click="item.amount--"
              >-</v-btn
            >
          </li>
        </ul>
        Total: {{total}}
        <v-text-field label="Enter new item" v-model="newItem"></v-text-field>
        <v-btn color="success" @click="addNewItem">Add Item</v-btn>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  props: ["message"],
  data: () => ({
    newItem: "",
    list: [
      {
        name: "robot",
        amount: 5
      },
      {
        name: "drone",
        amount: 2
      }
    ]
  }),
  computed: {
    total() {
        return this.list.reduce((sum, item) => sum + item.amount, 0)
    }
  },
  methods: {
    addNewItem() {
      this.list.push({
        name: this.newItem,
        amount: 0
      });
    }
  }
};
</script>
