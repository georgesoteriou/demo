<template>
  <v-container>
    <v-layout row text-center wrap>
      <v-flex>
        <v-text-field
          label="Enter your name"
          v-model="name"
        ></v-text-field>
      </v-flex>
      <v-flex v-if="name != ''">
        Hello {{ name }}
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  name: "HelloWorld",

  data: () => ({
    name: ""
  })
};
</script>
