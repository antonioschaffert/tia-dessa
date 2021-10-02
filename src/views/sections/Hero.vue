<template>
  <base-section
    id="hero"
    space="0"
  >
    <v-img
      :src="require('@/assets/background.png')"
      min-height="695px"
    >
      <v-theme-provider dark>
        <v-container class="fill-height px-5 py-12">
          <v-responsive
            class="d-flex align-center justify-center"
            height="100%"
            width="99%"
          >
            <v-row align="center">
              <v-col
                cols="12"
                md="6"
              >
                <base-heading
                  class="text-uppercase font-weight-bold"
                  :title="`Happy Birthday Denguinho`"
                />
                <base-subheading
                  title="We Love you so much!"
                />
                <base-body
                  text="33 anos :)"
                />

              </v-col>
              <v-col
                cols="12"
                md="6"
              >
                <v-img
                  :src="require('@/assets/projects/4.jpg')"
                  min-height="365px"
                  max-width="650px"
                />
              </v-col>
            </v-row>
          </v-responsive>
        </v-container>
      </v-theme-provider>
    </v-img>
  </base-section>
</template>

<script>
  export default {
    name: 'SectionHero',
  }
</script>

<style lang="scss" scoped>

</style>
