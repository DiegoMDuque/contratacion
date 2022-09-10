<template>
  <v-app>
    <v-main class="d-flex align-center">
      <v-container>
        <v-row class="d-flex justify-center">
          <v-col cols="12" sm="8" md="4" lg="4">
            <v-card elevation="5">
              <v-card-text>
                <div>
                  <a>
                    <v-img :src="require('@/assets/img/logo.png')"> </v-img>
                  </a>
                </div>
                <div>
                  <p
                    class="d-flex justify-center align-center black--text font-weight-bold mt-10 mb-10"
                  >
                    INICIO DE SESIÓN
                  </p>
                </div>
                <v-form ref="form" v-model="valid" lazy-validation>
                  <v-text-field
                    label="Ingrese su usuario"
                    type="text"
                    v-model="user"
                    :rules="userRules"
                    outlined
                    required
                  ></v-text-field>
                  <v-text-field
                    label="Ingrese su contraseña"
                    type="password"
                    v-model="password"
                    :rules="passwordRules"
                    outlined
                    required
                  ></v-text-field>
                  <v-btn color="#0195b1" x-large block dark @click="validate">
                    Ingresar
                  </v-btn>
                </v-form>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  layout: "login",
  data: () => ({
    valid: true,
    user: "",
    userRules: [(v) => !!v || "Debe ingresar su usuario"],
    password: "",
    passwordRules: [(v) => !!v || "Debe ingresar su contraseña"],
  }),
  methods: {
    validate() {
      this.$refs.form.validate();
    },
  },
};
</script>

<style lang="css" scoped></style>
