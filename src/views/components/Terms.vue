<template>
  <v-container>
    <v-row class="text-center">
      <v-col>
        <v-form ref="form" v-model="valid" lazy-validation>
          <v-text-field
            v-model="name"
            :counter="20"
            :rules="nameRules"
            label="用語名"
            required
          ></v-text-field>

          <v-btn
            :disabled="!valid"
            color="success"
            class="mr-4"
            @click="addTask"
          >
            用語 追加
          </v-btn>
        </v-form>
      </v-col>
      <v-col class="mb-5" cols="12">
        <div v-for="(checkbox, i) in checkboxes" :key="i">
          <v-card-title v-text="checkbox.lavel"></v-card-title>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "Tasks",

  data: () => ({
    checkboxes: [
      {
        lavel: "お買い物",
      },
      {
        lavel: "ゴミ捨て",
      },
    ],
    valid: true,
    name: "",
    nameRules: [
      (v: string) => !!v || "Name is required",
      (v: string) =>
        (v && v.length <= 10) || "Name must be less than 10 characters",
    ],
  }),

  methods: {
    addTask() {
      this.checkboxes.push({lavel: this.name });
      (this.$refs as any).form.reset();
    },
  },
});
</script>
