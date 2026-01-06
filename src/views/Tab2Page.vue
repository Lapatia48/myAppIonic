<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Photo Gallery</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Photo Gallery</ion-title>
        </ion-toolbar>
      </ion-header>

      <!-- Gallery Grid -->
      <div class="gallery-container">
        <div v-if="photos.length === 0" class="empty-state">
          <p>Gallerie vide</p>
        </div>
        <div v-else class="gallery-grid">
          <div v-for="photo in photos" :key="photo.filepath" class="gallery-item">
            <img 
              :src="photo.webviewPath" 
              :alt="photo.filepath"
              class="gallery-image"
            />
          </div>
        </div>
      </div>

      <!-- Floating Action Button for Camera -->
      <ion-fab vertical="bottom" horizontal="center" slot="fixed">
        <ion-fab-button @click="addNewToGallery()">
          <ion-icon :icon="camera"></ion-icon>
        </ion-fab-button>
      </ion-fab>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { camera } from 'ionicons/icons';
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonFab,
  IonFabButton,
  IonIcon,
} from '@ionic/vue';
import { usePhotoGallery } from '@/composables/usePhotoGallery';

const { photos, addNewToGallery } = usePhotoGallery();
</script>

<style scoped>
.gallery-container {
  background: linear-gradient(135deg, #000000 0%, #000000 100%);
  min-height: 100vh;
  padding: 16px;
}

.empty-state {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  color: white;
  font-size: 18px;
  text-align: center;
  padding: 20px;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 12px;
}

.gallery-item {
  position: relative;
  overflow: hidden;
  border-radius: 12px;
  aspect-ratio: 1;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.gallery-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>