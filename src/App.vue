<template>
  <div id="app"> 
      <ion-menu side="start" content-id="main-content">
      <ion-header>
        <ion-toolbar translucent>
          <ion-title>OpenOTD</ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-content>
        <ion-list>
            
          <ion-item @click="navigate('/')">
            <ion-icon name="mail" slot="start"></ion-icon>
            <ion-label>Übersicht</ion-label>
         </ion-item> 
            
          <ion-item @click="navigate('/accesses')">
            <ion-icon name="paper-plane" slot="start"></ion-icon>
            <ion-label>Zugriffe</ion-label>
          </ion-item>
          <ion-item @click="navigate('/settings')">
            <ion-icon name="settings" slot="start"></ion-icon>
            <ion-label>Einstellungen</ion-label>
          </ion-item>
          <ion-item @click="navigate('/logout')">
            <ion-icon name="warning" slot="start"></ion-icon>
            <ion-label>Ausloggen</ion-label>
          </ion-item>
        </ion-list>
      </ion-content>
    </ion-menu>

    <div class="ion-page" id="main-content">
      <ion-header>
        <ion-toolbar>
          <ion-buttons slot="start">
            <ion-menu-button></ion-menu-button>
          </ion-buttons>
          <ion-title>OpenOTD</ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-content class="ion-padding">
        
  <ion-router-outlet id="main"></ion-router-outlet>
      </ion-content>
    </div>

  </div>
</template>
<style>
.my-custom-menu {
  --width: 500px;
}
</style>

<script>
import { 
  IonContent, 
  IonHeader, 
  IonItem, 
  IonList, 
  IonMenu, 
  IonRouterOutlet,
  IonTitle, 
  IonToolbar,
  menuController
} from '@ionic/vue';
import { defineComponent } from 'vue';
import { useRouter } from "vue-router";
export default defineComponent({
  components: {
    IonContent, 
    IonHeader, 
    IonItem, 
    IonList, 
    IonMenu, 
    IonRouterOutlet,
    IonTitle, 
    IonToolbar
  },
  methods: {
      navigate(url) {
          this.router.push(url)
      },
    openFirst() {
      menuController.enable(true, 'first');
      menuController.open('first');
    },
    openEnd() {
      menuController.open('end');
    },
    openCustom() {
      menuController.enable(true, 'custom');
      menuController.open('custom');
    }
  },
   setup() {
    const router = useRouter();
    return { router };
  },
});
</script>
<style lang="scss">

:host {
    text-transform: unset !important;
}
</style>