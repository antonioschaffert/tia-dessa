<template>
  <v-app-bar
    app
    elevate-on-scroll
    style="right: 0"
    :color="color || '#dbffdc'"
    :height="$vuetify.breakpoint.mdAndUp ? '150px' : '60px'"
  >
    <v-toolbar-title class="headline">
      <router-link
        :to="{ name: 'Home' }"
        tag="h3"
        style="cursor: pointer; color: #458c47"
        v-text="appData.title"
      />
    </v-toolbar-title>
    <v-spacer />
    <div v-if="$vuetify.breakpoint.mdAndUp">
      <v-tabs
        hide-slider
        optional
        background-color="transparent"
        v-bind="tabAttrs"
      >
        <v-tab
          v-for="item in items"
          :key="item.name"
          :to="{ name: item.name }"
          :exact="item.name === 'Home'"
          :ripple="false"
          active-class="primary--text"
          class="font-weight-medium text-none"
          min-width="120px"
          text
        >
          <span v-text="item.name" />
          <v-icon
            v-if="item.icon && $vuetify.breakpoint.mdAndUp"
            small
            right
            v-text="item.icon"
          />
        </v-tab>
      </v-tabs>
    </div>
    <div v-else>
      <v-btn
        icon
        @click="drawer = true"
      >
        <v-icon>mdi-menu</v-icon>
      </v-btn>
      <blog-sidebar
        v-if="$route.name === 'Blog'"
        :value="drawer"
        @input="drawer = $event"
      />
      <base-sidebar
        v-else
        :items="items"
        :value="drawer"
        @input="drawer = $event"
      />
    </div>
  </v-app-bar>
</template>

<script>
  export default {
    name: 'BaseAppBar',

    components: {
      BlogSidebar: () => import('@/layouts/base/BlogSidebar'),
      BaseSidebar: () => import('@/layouts/base/BaseSidebar'),
    },

    props: {
      block: Boolean,
      search: Boolean,
      color: String,
    },

    data () {
      return {
        drawer: false,
        items: [
          { name: 'Home', icon: 'mdi-home' },
          { name: 'Portfolio', icon: 'mdi-book' },
        ],
      }
    },

    computed: {
      tabAttrs () {
        const attrs = {}
        if (this.block) attrs.height = '150px'
        return attrs
      },
    },

    watch: {
      '$route.name' (val) {
        this.drawer = false
      },
    },
  }
</script>
