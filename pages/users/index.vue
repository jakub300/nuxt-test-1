<template>
  <div>
    <ul>
      <li
        v-for="user in users"
        :key="user._id"
      >
        <nuxt-link :to="{ name: 'users-id', params: { id: user._id } }">
          {{ user.name }}
        </nuxt-link>
    </li></ul>
  </div>
</template>

<script>
import gql from 'graphql-tag';

export default {
  apollo: {
    users: {
      query: gql`
        {
          userMany {
            _id
            name
          }
        }
      `,
      update: data => data.userMany,
    },
  },
};
</script>
