<template>
  <v-dialog max-width="600px">
    <v-btn flat slot="activator" class="success">Add new project</v-btn>
    <v-card>
      <v-card-title>
        <h2>Add new Project</h2>
      </v-card-title>
      <v-card-text>
        <v-form class="px-3" ref="form">
          <v-text-field v-model="title" label="Title" prepend-icon="folder" :rules="inputRules"></v-text-field>
          <v-textarea v-model="content" label="Information" prepend-icon="edit" :rules="inputRules"></v-textarea>
          <v-menu>
            <v-text-field
              :value="FormatDate"
              slot="activator"
              label="Due date"
              prepend-icon="date_range"
            ></v-text-field>
            <v-date-picker v-model="due"></v-date-picker>
          </v-menu>
          <v-spacer></v-spacer>
          <v-btn flat @click="submit" class="success mx-0 mt-3">Add Project</v-btn>
        </v-form>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>
<script>
import format from "date-fns/format";
export default {
  data() {
    return {
      title: "",
      content: "",
      due: null,
      inputRules: [v => v.length >= 3 || "Minimum length is 3 characters"]
    };
  },
  methods: {
    submit() {
      if (this.$refs.form.validate()) {
        alert(this.title, this.content);
      }
    }
  },
  computed: {
    FormatDate() {
      return this.due ? format(this.due, "Do MMM YYYY") : "";
    }
  }
};
</script>
