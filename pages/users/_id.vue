<template>
  <div>
    <pre>{{ JSON.stringify(user, null, 2) }}</pre>
  </div>
</template>

<script>
import gql from 'graphql-tag';

export default {
  apollo: {
    user: {
      query: gql`
        query($id: MongoID!) {
          userById(_id: $id) {
            name
            age
            # languages
            # contacts
            gender
            address {
              street
            }
            someMixed
          }
        }
      `,

      variables() {
        return { id: this.$route.params.id };
      },

      update: data => data.userById,
    },
  },

  mounted() {
    console.log(this.user);
  },
};
</script>
