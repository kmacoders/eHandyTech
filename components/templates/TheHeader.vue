<template>
  <b-navbar>
    <template #brand>
      <b-navbar-item tag="router-link" :to="{ path: '/' }">
        <img
          src="https://raw.githubusercontent.com/buefy/buefy/dev/static/img/buefy-logo.png"
          alt="Lightweight UI components for Vue.js based on Bulma"
        >
      </b-navbar-item>
    </template>
    <template #start>
      <template v-for="(nav, index) in navbarItems">
        <b-navbar-item
          v-if="nav.subMenu.length === 0"
          :key="index"
          :href="nav.link"
        >
          {{ nav.title }}
        </b-navbar-item>
        <b-navbar-dropdown
          v-else
          :key="index"
          :label="nav.title"
        >
          <b-navbar-item
            v-for="(sub, i) in nav.subMenu"
            :key="i"
            :href="sub.link"
          >
            {{ sub.title }}
          </b-navbar-item>
        </b-navbar-dropdown>
      </template>
    </template>

    <template #end>
      <b-navbar-item tag="div">
        <div class="buttons">
          <a class="button is-primary">
            <strong>Sign up</strong>
          </a>
          <a class="button is-light">
            Log in
          </a>
        </div>
      </b-navbar-item>
    </template>
  </b-navbar>
</template>

<script>
import { Vue, Component } from 'nuxt-property-decorator'

@Component
export default class TheHeader extends Vue {
  navbarItems = [
    {
      title: 'Trang chu',
      link: '/',
      subMenu: []
    },
    {
      title: 'Khoa hoc',
      link: '/',
      subMenu: []
    },
    {
      title: 'Ve chung toi',
      link: '/',
      subMenu: [
        {
          title: 'sub 1',
          link: '/'
        },
        {
          title: 'Sub 2',
          link: '/'
        }
      ]
    }
  ]
}
</script>
