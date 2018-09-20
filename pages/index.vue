<template>
  <section class="container">
    <span>There are {{ userTotal }} users, </span>
    <nuxt-link to="/users">browse them</nuxt-link>.
  </section>
</template>

<script>
import gql from 'graphql-tag';

export default {
  apollo: {
    userTotal: gql`
      {
        userTotal
      }
    `,
  },
};
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
