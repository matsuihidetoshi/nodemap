<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/logo.svg')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <v-btn @click="listNodes">test</v-btn>
        <p>nodes: {{ nodes }}</p>
      </v-col>

    </v-row>
  </v-container>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'HelloWorld',

    data() {
      return {
        token: localStorage.getItem('CognitoIdentityServiceProvider.2k3jgggf71h44kedn96l7tjn8k.a2dc5200-eaa6-40fa-a856-c8f65ab1ab88.idToken'),
        ecosystem: [
          {
            text: 'vuetify-loader',
            href: 'https://github.com/vuetifyjs/vuetify-loader',
          },
          {
            text: 'github',
            href: 'https://github.com/vuetifyjs/vuetify',
          },
          {
            text: 'awesome-vuetify',
            href: 'https://github.com/vuetifyjs/awesome-vuetify',
          },
        ],
        importantLinks: [
          {
            text: 'Documentation',
            href: 'https://vuetifyjs.com',
          },
          {
            text: 'Chat',
            href: 'https://community.vuetifyjs.com',
          },
          {
            text: 'Made with Vuetify',
            href: 'https://madewithvuejs.com/vuetify',
          },
          {
            text: 'Twitter',
            href: 'https://twitter.com/vuetifyjs',
          },
          {
            text: 'Articles',
            href: 'https://medium.com/vuetify',
          },
        ],
        whatsNext: [
          {
            text: 'Explore components',
            href: 'https://vuetifyjs.com/components/api-explorer',
          },
          {
            text: 'Select a layout',
            href: 'https://vuetifyjs.com/layout/pre-defined',
          },
          {
            text: 'Frequently Asked Questions',
            href: 'https://vuetifyjs.com/getting-started/frequently-asked-questions',
          },
        ],
        nodes: null
      }
    },
    methods: {
      listNodes: function() {
        axios.get('https://6big0ypl22.execute-api.ap-northeast-1.amazonaws.com/default/api/v1/nodes/',
        {
          headers: { "Authorization": this.token },
          data: {}
        }).then(response => (
          this.nodes = response
        )).catch(error => (
          this.nodes = error
        )).finally(
        )
      }
    }
  }
</script>
