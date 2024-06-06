<template>
  <v-app>

    <v-app-bar color="white" class="bar" elevation="1">
      <v-row class="align-center justify-center d-flex">
        <div class="font1 mt-1">Твой Рацион</div>
        <v-menu open-on-hover>
          <template v-slot:activator="{ props }">
            <v-btn class="hidden-sm-and-up" variant="plain" width="45px" v-bind="props" icon="mdi-menu"></v-btn>
          </template>
          <v-list>
            <v-list-item>
              <v-list-item-title><v-btn width="100%">Рецепты</v-btn></v-list-item-title>
            </v-list-item>
            <v-list-item>
              <v-list-item-title><v-btn width="100%">Поиск продуктов</v-btn></v-list-item-title>
            </v-list-item>
            <v-list-item>
              <v-list-item-title><v-btn width="100%">Планировщик</v-btn></v-list-item-title>
            </v-list-item>
            <v-list-item>
              <v-list-item-title><v-btn width="100%" variant="flat" @click="this.$router.push('/login')">Регистрация</v-btn>
              </v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
        <div class="but1 hidden-xs">
          <v-btn variant="plain"><div class="font-weight-bold">Рецепты</div></v-btn>
          <v-btn variant="plain"><div class="font-weight-bold">Поиск продуктов</div></v-btn>
          <v-btn variant="plain"><div class="font-weight-bold">Планировщик</div></v-btn>
        </div>
        <v-btn class="hidden-xs" variant="flat" @click="this.$router.push('/login')">Регистрация</v-btn>
      </v-row>
    </v-app-bar>

    <v-main class="main1 bg-white overflow-x-hidden" style="scroll-snap-type: y mandatory; overflow-y: auto; height: calc(100vh - 64px);">
      <v-container class="justify-center align-center d-flex flex-column con1 scroll-snap-align-start" style="min-height: 100vh;">
        <v-row align="center" justify="center">
          <v-col cols="12" md="6" order-xl="1" order-lg="1" order-md="1" class="text-center">
            <h1 class="display-3 font-weight-bold mb-2">Питайтесь по-новому</h1>
            <p class="subtitle-1 mx-auto">Встречайте сервис планирования приемов пищи, поиска продуктов, анализирования питания.</p>
            <v-btn class="" color="black" :size="buttonSize" rounded="lg">Зарегистрироваться</v-btn>
          </v-col>
          <v-col cols="12" md="6" order-xl="2" order-lg="2" order-md="2" class="justify-center d-flex">
            <div class="info-container">
              <v-row>
                <v-col cols="4">
                  <div class="info-item">
                    <div class="info-value">1K+</div>
                    <div class="info-label">Рецептов</div>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="info-item">
                    <div class="info-value">20+</div>
                    <div class="info-label">Категорий</div>
                  </div>
                </v-col>
                <v-col cols="4">
                  <div class="info-item">
                    <div class="info-value">5K+</div>
                    <div class="info-label">Пользователей</div>
                  </div>
                </v-col>
              </v-row>
            </div>
          </v-col>

        </v-row>
      </v-container>

      <v-container class="justify-center align-center d-flex flex-column con2 scroll-snap-align-start" style="min-height: 100vh;">
        <v-row align="center" justify="center">
          <v-col cols="12" md="6" order-xl="2" order-lg="2" order-md="2" class="justify-center d-flex">
            <video class="mx-auto col video" autoplay loop :width="videoWidth" >
              <source src="https://samsungfood.com/wp-content/uploads/2023/08/1_Save_Recipe_new.mp4">
            </video>
          </v-col>
          <v-col cols="12" md="6" order-xl="1" order-lg="1" order-md="1" class="text-center">
            <h1 class="display-1 font-weight-bold mb-4">Сохраняйте все рецепты в одном месте</h1>
            <p class="subtitle-1 mx-auto">Сохраняйте рецепты с любого сайта в цифровую коллекцию, что упрощает создание, организацию и обмен вдохновляющими рецептами.</p>
            <v-btn class="" variant="flat" :size="buttonSize" rounded="lg">Никогда не потеряйте рецепт</v-btn>
          </v-col>
        </v-row>
      </v-container>

      <v-container class="justify-center align-center d-flex flex-column con3 scroll-snap-align-start" style="min-height: 100vh;">
        <v-row align="center" justify="center">
          <v-col cols="12" md="6" order-xl="2" order-lg="2" order-md="2" class="justify-center d-flex">
            <video class="mx-auto col video" autoplay loop :width="videoWidth">
              <source src="https://samsungfood.com/wp-content/uploads/2023/08/2_Meal_Planner_new.mp4">
            </video>
          </v-col>
          <v-col cols="12" md="6" order-xl="1" order-lg="1" order-md="1" class="text-center">
            <h1 class="display-1 font-weight-bold mb-4">Создавайте планы приемов пищи, которым действительно хочется следовать</h1>
            <p class="subtitle-1 mx-auto">Перетаскивайте личную коллекцию рецептов в еженедельный план приемов пищи. Будь то экономия времени, уменьшение отходов или улучшение питания, планировщик ТВОЙ РАЦИОН поможет достичь ваших целей.</p>
            <v-btn class="" variant="flat" :size="buttonSize" rounded="lg">Наслаждайтесь вкусной неделей</v-btn>
          </v-col>
        </v-row>
      </v-container>
    </v-main>

  </v-app>
</template>

<style>
.main1 {
  width: 100%;
  padding-left: 15%;
}
.image-container {
  max-width: 450px;
}
.info-container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.info-item {
  text-align: center;
}

.info-value {
  font-size: 24px;
  font-weight: bold;
}

.info-label {
  font-size: 16px;
  color: #666;
}
.video {
  max-width: 450px;
}
.font1 {
  font-family: 'Docker';
  font-size: 24px;
}

.but1 {
  padding-right: 10%;
  padding-left: 10%;
}

p {
  font-size: 20px;
  font-family: "Fira Code Medium";
}

h1 {
  font-size: 24px;
  font-family: Docker;
}

@media (max-width: 960px) {
  .but1{
    padding:0%;
  }
  .main1 {
    padding-left: 0;
  }
}

@media (max-width: 600px) {
  .display-3 {
    font-size: 2rem;
  }
  .subtitle-1 {
    font-size: 1rem;
  }
  .v-btn.v-size--x-large {
    font-size: 1rem;
    padding: 8px 16px;
  }
  .video {
    max-width: 300px;
  }
}

</style>
<script>
export default {
  data() {
    return {
      videoWidth: '450px',
      imageWidth: '300px'
    }
  },
  created() {
    window.addEventListener('resize', this.updateVideoWidth)
    this.updateVideoWidth()
  },
  methods: {
    updateVideoWidth() {
      if (window.innerWidth <= 600) {
        this.videoWidth = '300px'
        this.imageWidth = '300px'
      } else {
        this.videoWidth = '450px'
        this.imageWidth = '450px'
      }
    }
  }
}
</script>
