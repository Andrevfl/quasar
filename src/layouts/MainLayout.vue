<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />
      </q-toolbar>

      <div class="q-px-lg q-pt-xl q-mb-md">
        <div class="text-h3">Cidades</div>
        <div class="text-subtitle1"> {{ todaysDate }} </div>
      </div>
      <q-img src="../layouts/statics/mountains.jpg" class="header-image absolute-top" />
    </q-header>

    <q-drawer
        v-model="leftDrawerOpenNew"
        show-if-above
        :width="250"
        :breakpoint="600"
      >
        <q-scroll-area style="height: calc(100% - 192px); margin-top: 192px; border-right: 1px solid #ddd">
          <q-list padding>

            <q-item 
            to="/"
            exact
            clickable
            v-ripple
            >
              <q-item-section avatar>
                <q-icon name="list" />
              </q-item-section>

              <q-item-section>
                Tudo
              </q-item-section>
            </q-item>

            <q-item
            to="/help"
            exact
            clickable
            v-ripple
             
             >
              <q-item-section avatar>
                <q-icon name="help" />
              </q-item-section>

              <q-item-section>
                Help
              </q-item-section>
            </q-item>

          </q-list>
        </q-scroll-area>

     
          <q-img class="absolute-top" src="../layouts/statics/mountains.jpg" style="height: 192px">

   

          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="https://avatars.githubusercontent.com/u/43456910?s=400&u=764e0a031b6f3aedd5ac3dd060517e7d10f75461&v=4">
            </q-avatar>
            <div class="text-weight-bold">Andre Victor</div>
            <div>@andre.vfl</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <keep-alive>
      <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'
import { date } from 'quasar'


const leftDrawerOpenNew = false


export default defineComponent({
  name: 'MainLayout',


  computed: {
    
    enviarNome() {
      return 'andre'
    },
    todaysDate() {
      const timeStamp = Date.now()
      return date.formatDate(timeStamp, 'YYYY-MM-DD')
    }
  },

  components: {
    EssentialLink
  },

  setup() {
 

    const leftDrawerOpen = ref(false)


    return {
  
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
<style>
.header-image {
  height: 100%;
  z-index: -1;
  opacity: 0.2;
  filter: grayscale(100%);
}
</style>
