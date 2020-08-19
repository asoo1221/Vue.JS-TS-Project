<template>
  <div class="categories">
    <div class="col-sm-10">
      <table
        id="MyTable"
        class="table table-striped table-bordered table-hover"
      >
        <tbody>
          <tr>
            <td>Text</td>
            <td>Type</td>
            <td>Upvotes</td>
            <td>ID</td>
          </tr>
          <tr>
            <td>{{ fact.text }}</td>
            <td>{{ fact.type }}</td>
            <td>{{ fact.upvotes }}</td>
            <td>{{ fact._id }}</td>
          </tr>
          <tr>
            <td>UserID</td>
            <td>FirstName</td>
            <td>LastName</td>
          </tr>
          <tr>
            <td>{{ fact.user._id }}</td>
            <td>{{ fact.user.name.first }}</td>
            <td>{{ fact.user.name.last }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "Categories",
  props: {
    fact: {}
  },
  data() {
    return {};
  }
};
</script>

<style scoped></style>
