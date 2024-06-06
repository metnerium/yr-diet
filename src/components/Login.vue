<template>
  <v-app dark>
    <v-main>
      <v-responsive class="align-center text-center fill-height">
        <v-container class="w-lg-33 w-md-50 w-sm-75">
          <v-row align="center" justify="center">
            <v-card
              v-if="!sentCode"
              class="py-8 px-6 text-center mx-auto ma-4"
              elevation="0"
              width="100%"
            >

              <h3 class="mb-4">Введите номер телефона</h3>
              <v-text-field

                density="compact"
                v-model="phoneNumber"
                :rules="phoneRules"
                required
                variant="outlined"
              ></v-text-field>

              <v-btn
                class="my-4"
                color="purple"
                height="40"
                text="Получить код"
                variant="outlined"
                width="100%"
                :disabled="!isValidPhoneNumber"
                @click="sendCode"
              ></v-btn>
            </v-card>

            <v-card
              v-else
              class="py-8 px-6 text-center mx-auto ma-4"
              elevation="0"


            >
              <h3 class="text-h6 mb-4">Введите код из смс</h3>

              <div class="text-body-2">
                Код отправлен на номер <br />{{ phoneNumber }}
              </div>

              <v-sheet color="surface">
                <v-otp-input
                  length="5"
                  v-model="otpCode"
                ></v-otp-input>
              </v-sheet>

              <v-btn
                class="my-4"
                color="purple"
                height="40"
                text="Войти"
                variant="outlined"
                :disabled="otpCode.length !== 5"
                width="70%"
                @click="verifyCode"
              ></v-btn>

              <div class="text-caption">
                Не получили СМС? <br> <a href="#" @click.prevent="resendCode">Отправить повторно</a>
              </div>
            </v-card>
          </v-row>
        </v-container>
      </v-responsive>
    </v-main>
  </v-app>
</template>
<style>
h3 {
  font-size: 50px;
}
@media (max-width: 959px) {
  h3 {
    font-size: 36px;
  }
}

@media (max-width: 599px) {
  h3 {
    font-size: 24px;
  }
}
</style>

<script>
import axios from 'axios';

export default {
  data: () => ({
    phoneNumber: '+7',
    otpCode: '',
    sentCode: false,
    phoneRules: [
      v => !!v || 'Номер телефона обязателен',
      v => /^(\+7)\d{10}$/.test(v) || 'Некорректный номер телефона',
    ],
  }),
  computed: {
    isValidPhoneNumber() {
      return /^(\+7)\d{10}$/.test(this.phoneNumber);
    },
  },
  methods: {
    sendCode() {
      axios.post("/send_auth_code", { phone_number: this.phoneNumber})
      this.sentCode = true;
    },
    async verifyCode() {
      try {
        const response = await axios.post('/verify_code', { phone_number: this.phoneNumber }, { params: { code: this.otpCode } })
        // Save the JWT token to Vuex
        this.$store.commit('setJwtToken', response.data.jwt_token)
        this.$router.push('/profil')
      } catch (error) {
        console.error('Error verifying code:', error)
      }
    },
  },
};
</script>
