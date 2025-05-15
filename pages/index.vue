<template> 
  <v-app-bar fixed>
    <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
    <v-app-bar-title>Sample Application</v-app-bar-title>
  </v-app-bar>

  <v-navigation-drawer
    v-model="drawer"
    temporary
  >
    <v-sheet
      class="pa-4"
      color="grey-lighten-4"
    >
      <v-avatar
        class="mb-4"
        color="grey-darken-1"
        size="64"
      ></v-avatar>

      <div>test@example.com</div>
    </v-sheet>
    <v-list>
      <v-list-item
        v-for="[icon, text] in links"
        :key="icon"
        :prepend-icon="icon"
        :title="text"
        link
      ></v-list-item>
    </v-list>
  </v-navigation-drawer>

  <v-main class="bg-grey-lighten-2">
    <v-container
      class="py-8 px-6"
      fluid
    >
      <v-row>
        <v-col
          v-for="card in cards"
          :key="card"
          cols="12"
        >
          <v-card>
            <v-list lines="two">
              <v-list-subheader :title="card"></v-list-subheader>

              <template v-for="n in 6" :key="n">
                <v-list-item>
                  <template v-slot:prepend>
                    <v-avatar color="grey-darken-1"></v-avatar>
                  </template>

                  <v-list-item-title :title="`Message ${n}`"></v-list-item-title>

                  <v-list-item-subtitle title="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nihil repellendus distinctio similique"></v-list-item-subtitle>
                </v-list-item>

                <v-divider
                  v-if="n !== 6"
                  :key="`divider-${n}`"
                  inset
                ></v-divider>
              </template>
            </v-list>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>  
<script setup lang="ts">
  import { ref } from 'vue';

  const drawer = ref<boolean>(false);
  const cards = ['Today', 'Yesterday'];
  const links = [
    ['mdi-send', 'メール'],
    ['mdi-cog', '設定'],
    ['mdi-alert-octagon', 'ヘルプ'],
  ];
</script>