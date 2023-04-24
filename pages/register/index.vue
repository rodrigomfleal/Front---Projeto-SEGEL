<template>
  <div>
    <v-app style="background-color: white; color: white">
      <v-layout justify-center>
        <v-flex xs12 sm8 md4>
          <v-card
            class="d-flex flex-column justify-center text-center"
            color="grey lighten-5"
            max-width="344"
            title="User Registration"
          >
            <v-toolbar height="0" color="grey darken-1">
              <v-toolbar-title>Registro</v-toolbar-title>
            </v-toolbar>
            <v-container>
              <v-text-field
                v-model="register.name"
                color="black"
                label="Nome"
                light
                variant="underlined"
                class="v-text-field--outlined text-black"
                outlined
              ></v-text-field>

              <v-text-field
                v-model="register.cpf"
                color="black"
                light
                label="CPF"
                variant="underlined"
                class="v-text-field--outlined text-black"
                outlined
              ></v-text-field>

              <v-text-field
                v-model="register.email"
                color="black"
                light
                label="Email"
                variant="underlined"
                outlined
                :rules="[
                  (v) => !!v || 'E-mail obrigatório',
                  (v) => /.+@.+\..+/.test(v) || 'E-mail inválido',
                ]"
              ></v-text-field>

              <v-text-field
                v-model="register.phone"
                color="black"
                light
                label="Telefone"
                variant="underlined"
                class="v-text-field--outlined text-black"
                outlined
              ></v-text-field>

              <v-text-field
                v-model="register.password"
                color="black"
                label="Senha"
                light
                placeholder="Enter your password"
                variant="underlined"
                :rules="[(v) => !!v || 'Senha obrigatória']"
                :append-icon="show ? 'mdi-eye-outline' : 'mdi-eye-off-outline'"
                outlined
                :type="show ? 'text' : 'password'"
                @click:append="show = !show"
                @keypress.enter="login"
              >
              </v-text-field>            

              <v-checkbox
                v-model="terms"
                light
                color="black"
                label="Aceito os termos e condições"
              ></v-checkbox>
            </v-container>

            <v-divider></v-divider>

            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="grey darken-1" @click="create()">
                Registrar
                <v-icon icon="mdi-chevron-right" end></v-icon>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-flex>
      </v-layout>
    </v-app>
  </div>
</template>

<script>
export default {
  name: "Register",

  data() {
    return {
      terms: false,
      register: {
        name: "",
        cpf: "",
        email: "",
        phone: "",
        password: "",
      },
      show: false,
    };
  },
  methods: {

    create() {
      
      this.$axios
        .$post("/account/create", {
          id: "",
          name: this.register.name,
          cpf: this.register.cpf,
          email: this.register.email,
          phone_number: this.register.phone,
          user_type: "1",
          available: true,
          hashed_password: this.register.password,
        })
        .then((response) => {
          console.table(response),
            this.$toast.success("Conta cadastrada com sucesso!"),
            this.$router.push("/login");
        })
        .catch(() => {});
    },
  },
};
</script>

<style scoped>
</style>