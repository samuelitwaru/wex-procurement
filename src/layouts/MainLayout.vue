<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />
        <q-toolbar-title> WEX Procurement </q-toolbar-title>
        <div class="text-orange-3 q-px-xs">
          <router-link to="/account">
            <q-chip
              class="glossy"
              icon="person"
              label="authStore.currentUser.username"
            />
          </router-link>
          <!-- {{ $getState("user")?.name }} -->
        </div>
        <user-logout />
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <side-menu />
    </q-drawer>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "MainLayout",

  components: {},

  setup(props, context) {
    const leftDrawerOpen = ref(false);

    console.dir(context.$route);

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>
