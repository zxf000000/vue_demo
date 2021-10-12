<template>
  <v-container fluid class="fill-height d-flex flex-column justify-start align-start">
    <v-row style="width: 100%;">
      <v-col cols="12" >
        <h2 class="pa-3">Animations</h2>
        <v-row no-gutters>
          <v-col>
            <Loading ref="loading">
            </Loading>
            <v-btn @click="tapStart">Start</v-btn>
            <v-btn @click="tapComplete">Complete</v-btn>
            <v-btn @click="tapReset">Reset</v-btn>
          </v-col>
          <v-col>
            <TestSvg></TestSvg>
          </v-col>
          <v-col>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Loading from "@/components/Loading";
import TestSvg from "@/components/TestSvg";
export default {
  name: "AnimationPage",
  components: {TestSvg, Loading},
  methods: {
    tapStart() {
      this.$refs.loading.start();
    },
    tapComplete() {
      this.$refs.loading.complete();
    },
    tapReset() {
      this.$refs.loading.reset();
    }
  }
}
</script>

<style scoped>

</style>
