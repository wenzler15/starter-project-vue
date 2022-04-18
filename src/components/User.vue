<template>
  <div class="container">
    <h3>Repositórios:</h3>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Id</th>
          <th scope="col">Name</th>
          <th scope="col">Linguagem</th>
          <th scope="col">Visibilidade</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="repo in repos" v-bind:key="repo.id">
          <th scope="row">{{ repo.id }}</th>
          <td>{{ repo.name }}</td>
          <td>{{ repo.language }}</td>
          <td>{{ repo.visibility }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "UserComp",
  data() {
    return {
      users: null,
      repos: null,
    };
  },
  created: function () {
    axios.get("https://api.github.com/users/wenzler15/repos").then((res) => {
      this.repos = res.data;
    });
  },
};
</script>
<style>
h3 {
  margin-bottom: 5%;
}
</style>
