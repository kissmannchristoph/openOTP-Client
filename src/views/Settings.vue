<template>
  <!-- Default Segment -->
  <ion-segment value="account" @ionChange="segmentChanged($event)">
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
    <Account v-if="checkSegment('account')" />
    <Security v-if="checkSegment('security')" />
    <data-managment v-if="checkSegment('data_management')" />
  </ion-content>
</template>

<script lang="ts">
import { IonSegment, IonSegmentButton, IonToolbar } from "@ionic/vue";
import { defineComponent, ref, computed } from "vue";
import Account from "./Settings/Account.vue";
import Security from "./Settings/Security.vue";
import DataManagment from "./Settings/DataManagment.vue";

export default defineComponent({
  components: {
    IonSegment,
    IonSegmentButton,
    IonToolbar,
    Account,
    Security,
    DataManagment,
  },
  methods: {
    checkSegment(data) {
      return data == this.currentSegment;
    },
    segmentChanged(ev: CustomEvent) {
      this.currentSegment = ev.detail.value;
      /*switch (ev.detail.value) {
        case "account":
          this.currentSegmentID = 0;
          break;
        case "security":
          this.currentSegmentID = 1;
          break;
        case "data_management":
          this.currentSegmentID = 2;
          break;
        default:
          break;
      }*/
    },
  },
  setup() {
    const val = ref("account");
    const currentSegment = computed({
      get: () => val.value,
      set: (_val) => {
        val.value = _val;
      },
    });

    return { currentSegment };
  },
});
</script>