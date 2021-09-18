<template>
    
     <v-app-bar
      absolute
      color="#6A76AB"
      dark
      shrink-on-scroll
      prominent
      src="@/assets/fondo.jpg"
      fade-img-on-scroll
      scroll-target="#scrolling-techniques-3"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top left, rgba(210,46,226,.7), rgba(25,32,72,.7)"
        ></v-img>
      </template>

      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-app-bar-title>SACRIS</v-app-bar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>dots-vertical</v-icon>
      </v-btn>

      <template v-slot:extension>
        <v-tabs align-with-title>
          <v-tab>Usuario</v-tab>
          <v-tab>Tipo Usuario</v-tab>
          <v-tab>Tipo Documento</v-tab>
        </v-tabs>
      </template>
    </v-app-bar>
</template>