<template>
  <!-- Default Segment -->
  <ion-segment @ionChange="segmentChanged($event)">
    <ion-segment-button value="account">
      <ion-label>Account</ion-label>
    </ion-segment-button>
    <ion-segment-button value="security">
      <ion-label>Sicherheit</ion-label>
    </ion-segment-button>
        <ion-segment-button value="data_management">
      <ion-label>Datenverwaltung</ion-label>
    </ion-segment-button>
  </ion-segment>
  <ion-content>
    <Account v-if="currentSegmentID == 0"/>
    <Security v-if="currentSegmentID == 1"/>
    <data-managment  v-if="currentSegmentID == 2"/>
  </ion-content>
</template>

<script lang="ts">
import { IonSegment, IonSegmentButton, IonToolbar } from '@ionic/vue';
import { defineComponent, ref, computed } from 'vue';
import Account from './Settings/Account.vue';
import Security from './Settings/Security.vue';
import DataManagment from './Settings/DataManagment.vue';

export default defineComponent({
  components: { IonSegment, IonSegmentButton, IonToolbar , Account, Security, DataManagment},
  methods: {
    segmentChanged(ev: CustomEvent) {
      switch(ev.detail.value) {
        case "account": this.currentSegmentID = 0; break;
        case "security": this.currentSegmentID = 1; break;
        case "data_management": this.currentSegmentID = 2; break;
        default:break;
      }
    }
  },
setup() {
  const count = ref(1)
const currentSegmentID = computed({
  get: () => count.value,
  set: val => {
    count.value = val
  }
})

    return { currentSegmentID }
  }
});
</script>