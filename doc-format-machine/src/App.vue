<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>KOMODO</span>
        <span class="font-weight-light">DOCS</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
	<v-btn
		color="blue"
		class="white--text"
	>
		RPC Doc Configuration
	</v-btn>
    </v-toolbar>
    <v-content>
	<tool/>
    </v-content>
  </v-app>
</template>

<script>

import Tool from './components/Tool'

export default {
  name: 'App',
  components: {
	Tool
  },
  data () {
    return {
      //
    }
  }
}
</script>
