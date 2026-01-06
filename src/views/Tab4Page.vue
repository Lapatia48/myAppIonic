<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button defaultHref="/tabs/tab3"></ion-back-button>
        </ion-buttons>
        <ion-title>La Puissance d'Ionic</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Découvrez Ionic</ion-title>
        </ion-toolbar>
      </ion-header>

      <!-- Hero Section -->
      <div class="ion-padding">
        <ion-card>
          <ion-card-header>
            <ion-card-title>Bienvenue sur Tab 4</ion-card-title>
            <ion-card-subtitle>Explorer les capacités d'Ionic Framework</ion-card-subtitle>
          </ion-card-header>
          <ion-card-content>
            <p>Ionic est un framework open-source puissant pour créer des applications mobiles et web avec un seul codebase.</p>
          </ion-card-content>
        </ion-card>
      </div>

      <!-- Composants Ionic -->
      <div class="ion-padding">
        <ion-segment v-model="selectedSegment" @ionChange="onSegmentChange">
          <ion-segment-button value="components">
            <ion-label>Composants</ion-label>
          </ion-segment-button>
          <ion-segment-button value="features">
            <ion-label>Fonctionnalités</ion-label>
          </ion-segment-button>
          <ion-segment-button value="tips">
            <ion-label>Conseils</ion-label>
          </ion-segment-button>
        </ion-segment>
      </div>

      <!-- Tab Contenu Composants -->
      <div v-if="selectedSegment === 'components'" class="ion-padding">
        <h2>Composants Ionic Essentiels</h2>

        <!-- Buttons -->
        <ion-card>
          <ion-card-header>
            <ion-card-title>Buttons</ion-card-title>
          </ion-card-header>
          <ion-card-content>
            <div class="button-group">
              <ion-button expand="block" color="primary">
                <ion-icon slot="start" :icon="heart"></ion-icon>
                Primary
              </ion-button>
              <ion-button expand="block" color="success">
                <ion-icon slot="start" :icon="checkmarkDone"></ion-icon>
                Success
              </ion-button>
              <ion-button expand="block" color="warning">
                <ion-icon slot="start" :icon="alertCircle"></ion-icon>
                Warning
              </ion-button>
              <ion-button expand="block" color="danger">
                <ion-icon slot="start" :icon="close"></ion-icon>
                Danger
              </ion-button>
            </div>
          </ion-card-content>
        </ion-card>

        <!-- Lists -->
        <ion-card>
          <ion-card-header>
            <ion-card-title>Listes</ion-card-title>
          </ion-card-header>
          <ion-card-content>
            <ion-list>
              <ion-item>
                <ion-icon slot="start" :icon="star" color="warning"></ion-icon>
                <ion-label>
                  <h2>Item 1</h2>
                  <p>Description détaillée</p>
                </ion-label>
              </ion-item>
              <ion-item>
                <ion-icon slot="start" :icon="flag" color="danger"></ion-icon>
                <ion-label>
                  <h2>Item 2</h2>
                  <p>Contenu dynamique</p>
                </ion-label>
              </ion-item>
              <ion-item>
                <ion-icon slot="start" :icon="sunny" color="warning"></ion-icon>
                <ion-label>
                  <h2>Item 3</h2>
                  <p>Interactif et réactif</p>
                </ion-label>
              </ion-item>
            </ion-list>
          </ion-card-content>
        </ion-card>

        <!-- Forms -->
        <ion-card>
          <ion-card-header>
            <ion-card-title>Formulaires</ion-card-title>
          </ion-card-header>
          <ion-card-content>
            <ion-item>
              <ion-label position="floating">Nom</ion-label>
              <ion-input v-model="formData.name" placeholder="Entrez votre nom"></ion-input>
            </ion-item>
            <ion-item>
              <ion-label position="floating">Email</ion-label>
              <ion-input v-model="formData.email" placeholder="email@example.com" type="email"></ion-input>
            </ion-item>
            <ion-item>
              <ion-label>Notification</ion-label>
              <ion-toggle v-model="formData.notification" slot="end"></ion-toggle>
            </ion-item>
          </ion-card-content>
        </ion-card>
      </div>

      <!-- Tab Contenu Fonctionnalités -->
      <div v-if="selectedSegment === 'features'" class="ion-padding">
        <h2>Fonctionnalités Puissantes d'Ionic</h2>

        <ion-card>
          <ion-card-header>
            <ion-card-title color="primary">
              <ion-icon :icon="flash"></ion-icon>
              Cross-Platform
            </ion-card-title>
          </ion-card-header>
          <ion-card-content>
            <p>Développez une seule application pour iOS, Android, Web et Desktop avec le même code.</p>
          </ion-card-content>
        </ion-card>

        <ion-card>
          <ion-card-header>
            <ion-card-title color="success">
              <ion-icon :icon="speedometer"></ion-icon>
              Performance
            </ion-card-title>
          </ion-card-header>
          <ion-card-content>
            <p>Optimisé pour des performances exceptionnelles et un rendu fluide sur tous les appareils.</p>
          </ion-card-content>
        </ion-card>

        <ion-card>
          <ion-card-header>
            <ion-card-title color="warning">
              <ion-icon :icon="build"></ion-icon>
              Composants Riches
            </ion-card-title>
          </ion-card-header>
          <ion-card-content>
            <p>Bibliothèque complète de composants prêts à l'emploi avec design Material et iOS.</p>
          </ion-card-content>
        </ion-card>

        <ion-card>
          <ion-card-header>
            <ion-card-title color="danger">
              <ion-icon :icon="call"></ion-icon>
              Accès Natif
            </ion-card-title>
          </ion-card-header>
          <ion-card-content>
            <p>Accédez aux APIs natives comme la caméra, le GPS, les contacts via Capacitor.</p>
          </ion-card-content>
        </ion-card>
      </div>

      <!-- Tab Contenu Conseils -->
      <div v-if="selectedSegment === 'tips'" class="ion-padding">
        <h2>Conseils et Bonnes Pratiques</h2>

        <ion-card>
          <ion-card-header>
            <ion-card-title>🎯 Organisation</ion-card-title>
          </ion-card-header>
          <ion-card-content>
            <ion-badge color="primary">Conseil</ion-badge>
            <p>Organisez vos composants en dossiers logiques pour faciliter la maintenance.</p>
          </ion-card-content>
        </ion-card>

        <ion-card>
          <ion-card-header>
            <ion-card-title>⚡ Performance</ion-card-title>
          </ion-card-header>
          <ion-card-content>
            <ion-badge color="success">Conseil</ion-badge>
            <p>Utilisez virtualScroll pour les listes longues et lazy loading pour les images.</p>
          </ion-card-content>
        </ion-card>

        <ion-card>
          <ion-card-header>
            <ion-card-title>🎨 Design</ion-card-title>
          </ion-card-header>
          <ion-card-content>
            <ion-badge color="warning">Conseil</ion-badge>
            <p>Respectez les guidelines Material Design et iOS pour une meilleure UX.</p>
          </ion-card-content>
        </ion-card>

        <ion-card>
          <ion-card-header>
            <ion-card-title>🔒 Sécurité</ion-card-title>
          </ion-card-header>
          <ion-card-content>
            <ion-badge color="danger">Conseil</ion-badge>
            <p>Validez toujours les données utilisateur et utilisez HTTPS pour les communications.</p>
          </ion-card-content>
        </ion-card>

        <!-- Progress Bar -->
        <ion-card>
          <ion-card-header>
            <ion-card-title>Progression</ion-card-title>
          </ion-card-header>
          <ion-card-content>
            <p>Progression d'apprentissage Ionic</p>
            <ion-progress-bar :value="0.7" color="primary"></ion-progress-bar>
            <p class="ion-text-center ion-margin-top"><small>70% Complété</small></p>
          </ion-card-content>
        </ion-card>
      </div>

      <!-- Bouton de Navigation -->
      <div class="ion-padding">
        <ion-button expand="block" color="secondary" href="/tabs/tab3">
          <ion-icon slot="start" :icon="chevronBack"></ion-icon>
          Retour à Tab 3
        </ion-button>
      </div>

      <!-- Toast Example -->
      <div class="ion-padding">
        <ion-button expand="block" @click="showToast">
          <ion-icon slot="start" :icon="informationCircle"></ion-icon>
          Afficher une notification
        </ion-button>
      </div>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { toastController } from '@ionic/vue';
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonButtons,
  IonBackButton,
  IonCard,
  IonCardHeader,
  IonCardTitle,
  IonCardSubtitle,
  IonCardContent,
  IonSegment,
  IonSegmentButton,
  IonLabel,
  IonIcon,
  IonList,
  IonItem,
  IonInput,
  IonToggle,
  IonButton,
  IonBadge,
  IonProgressBar,
} from '@ionic/vue';
import {
  heart,
  checkmarkDone,
  alertCircle,
  close,
  star,
  flag,
  sunny,
  flash,
  speedometer,
  build,
  call,
  chevronBack,
  informationCircle,
} from 'ionicons/icons';

const selectedSegment = ref('components');

const formData = ref({
  name: '',
  email: '',
  notification: false,
});

const onSegmentChange = () => {
  console.log('Segment changé:', selectedSegment.value);
};

const showToast = async () => {
  const toast = await toastController.create({
    message: 'Bienvenue sur Tab 4 - Découvrez la puissance d\'Ionic!',
    duration: 2000,
    position: 'bottom',
    color: 'success',
  });
  await toast.present();
};
</script>

<style scoped>
.button-group {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

ion-card {
  margin-bottom: 16px;
}

h2 {
  margin-top: 0;
  color: var(--ion-color-primary);
}

.ion-text-center {
  text-align: center;
}
</style>
