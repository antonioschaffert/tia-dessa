<template>
  <base-section
    id="story-alt"
    class="grey lighten-4 pb-12"
    space="0"
  >
    <v-row
      align="center"
      justify="center"
      no-gutters
    >
      <v-col
        cols="12"
        md="6"
      >
        <v-img
          class="ma-1"
          min-height="500px"
          min-width="50%"
          :src="activeProject.src"
        />
      </v-col>
      <v-col
        cols="12"
        md="6"
        class="px-5 py-2"
      >
        <base-heading
          class="font-weight-bold"
          :title="activeProject.title"
          align="left"
        />
        <base-subheading
          :title="activeProject.subtitle"
        />
        <base-subtitle
          title="Description"
          weight="bold"
        />
        <base-body
          :text="activeProject.description"
          space="3"
        />
        <div />
      </v-col>
    </v-row>
  </base-section>
</template>

<script>
  export default {
    name: 'SectionProjectDetail',
    computed: {
      activeProject () {
        const id = this.$route.params.id
        return this.appData.projects.find(prj => +prj.id === +id)
      },
    },
  }
</script>

<style lang="scss" scoped>

</style>
