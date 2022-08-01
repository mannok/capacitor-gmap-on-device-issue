<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Blank</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Blank</ion-title>
        </ion-toolbar>
      </ion-header>

      <capacitor-google-map id="map"></capacitor-google-map>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar } from '@ionic/vue';
import { defineComponent, onMounted } from 'vue';
import { GoogleMap } from '@capacitor/google-maps';

export default defineComponent({
  name: 'HomePage',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar
  },
  setup: () => {
    onMounted(async () => {
      const apiKey = 'YOUR_API_KEY_HERE';

      const mapRef = document.getElementById('map');

      const newMap = await GoogleMap.create({
        id: 'my-map', // Unique identifier for this map instance
        element: mapRef!, // reference to the capacitor-google-map element
        apiKey: apiKey, // Your Google Maps API Key
        config: {
          center: {
            // The initial position to be rendered by the map
            lat: 33.6,
            lng: -117.9,
          },
          zoom: 8, // The initial zoom level to be rendered by the map
        },
      });
    });
  }
});
</script>

<style scoped>
  ion-content {
    --ion-background-color: transparent;
  }

  #map {
    display: block;
    height: 400px;
  }
</style>
