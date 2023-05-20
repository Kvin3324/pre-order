<template>
  <section class="pre-order">
    <div>
      <v-container>
        <v-row>
          <v-col
            cols="12"
            md="12"
          >
            <h3 class="pre-order-title" v-text="title" />
            <form ref="form" @submit.prevent="sendEmail">
              <v-text-field
                label="Adresse mail"
                :rules="emailRules"
                hide-details="auto"
                required
              ></v-text-field>
            </form>
          </v-col>
        </v-row>
        <v-btn
          depressed
          color="primary"
          class="confirm-btn"
          :disabled="isBtnDisabled"
          @click="sendEmail"
        >
          Confirmer
        </v-btn>
      </v-container>
    </div>
  </section>
</template>

<script>
import emailjs from '@emailjs/browser';

export default {
  name: "PreOrder",
  props: {
    title: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      isBtnDisabled: null,
      email: '',
      emailRules: [
        value => {
          if (value) return true
          return 'Adresse mail requise.'
        },
        value => {
          if (/.+@.+\..+/.test(value)) {
            this.isBtnDisabled = false
            this.email = value
            return true
          }

          if (!(/.+@.+\..+/.test(value))) {
            this.isBtnDisabled = true
            return 'Le format du mail doit être valide.'
          }
        },
      ],
    }
  },
  methods: {
    sendEmail() {
      const templateParams = {
        email: this.email
      }

      emailjs.send( 'service_hl4d37f', 'template_z9fqvza', templateParams, 'pbjQPc_pRWu6hjfbw')
      .then((result) => {
        return result
      }, (error) => {
        console.log('FAILED...', error.text);
      });
    }
  }
}
</script>

<style>
.v-messages__message {
  color: red;
}

.confirm-btn {
  margin: 20px 0;
}

h3 {
  margin: 20px 0;
  text-align: left;
}
</style>