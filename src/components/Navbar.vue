<template>
  <nav>
    <v-app-bar depressed app class="nullShadow">
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title class="text-uppercase ">
        <v-text-field dense solo-inverted flat prepend-inner-icon="mdi-magnify" class="mt-6 serchNavbar" outlined
          clearable label="Search" type="text"></v-text-field>
      </v-toolbar-title>
      <v-toolbar-title class="text-uppercase ">
        <v-btn rounded-xl class="ml-4 btnBiru" depressed color="primary ">Cari</v-btn>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn text>
        <v-avatar color="grey lighten-2" size="38">
          <span class=" text-h5">DC</span>
        </v-avatar>
      </v-btn>
      <v-menu offset-y>
        <template v-slot:activator="{ on }">
          <v-btn text v-on="on">
            <v-icon right>expand_more</v-icon>
          </v-btn>
          <v-list class="nullpadding">
            <v-list-item class="font-weight-bold">Dane Coper</v-list-item>
            <v-list-item class="caption nullMargin">Super Admin</v-list-item>
          </v-list>
        </template>
        <v-list flat>
          <v-list-item v-for="link in links" :key="link.text" router :to="link.route" active-class="border">
            <v-list-item-title>{{ link.text }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" app class="">
      <v-layout column align-center>
        <v-flex class="mt-3 ml-1">
          <v-img size="40" class="mt-3" :src="require('../assets/ahamart.png')" height="70%">
          </v-img>
          <p class="white--text subheading mt-1 text-center">Username</p>
        </v-flex>
      </v-layout>
      <v-list flat>
        <v-list-item  active-class="border">
          <v-list-item-action>
            <v-icon>dashboard</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Dashboard</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-list>
        <v-list-group>
          <template #prependIcon>
            <v-icon>
              dashboard
            </v-icon>
          </template>
          <template #activator>
            <v-list-item class="ml-n6 font-weight-bold">Product</v-list-item>
          </template>
          <v-list-item v-for="item in product" :key="item.text">
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              {{ item.text }}
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
      </v-list>
      <v-list>
        <v-list-group>
          <template #prependIcon>
            <v-icon>
              dashboard
            </v-icon>
          </template>
          <template #activator>
            <v-list-item class="ml-n6 font-weight-bold">Marketing</v-list-item>
          </template>
          <v-list-item v-for="item in marketing" :key="item.text">
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              {{ item.text }}
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
      </v-list>
      <v-list>
        <v-list-group>
          <template #prependIcon>
            <v-icon>
              dashboard
            </v-icon>
          </template>
          <template #activator>
            <v-list-item class="ml-n6 font-weight-bold">Toko</v-list-item>
          </template>
          <v-list-item v-for="item in toko" :key="item.text">
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              {{ item.text }}
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
      </v-list>
      <v-list>
        <v-list-group>
          <template #prependIcon>
            <v-icon>
              dashboard
            </v-icon>
          </template>
          <template #activator>
            <v-list-item class="ml-n6 font-weight-bold">Driver</v-list-item>
          </template>
          <v-list-item v-for="item in driver" :key="item.text">
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              {{ item.text }}
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
      </v-list>
      <v-list>
        <v-list-group>
          <template #prependIcon>
            <v-icon>
              dashboard
            </v-icon>
          </template>
          <template #activator>
            <v-list-item class="ml-n6 font-weight-bold">
              Pengguna
            </v-list-item>
          </template>
          <v-list-item v-for="item in pengguna" :key="item.text">
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              {{ item.text }}
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
      </v-list>
      <v-list>
        <v-list-group>
          <template #prependIcon>
            <v-icon>
              dashboard
            </v-icon>
          </template>
          <template #activator>
            <v-list-item class="ml-n6 font-weight-bold">
              Customer Service
            </v-list-item>
          </template>
          <v-list-item v-for="item in service" :key="item.text">
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              {{ item.text }}
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>
<script>

export default {
  data: () => ({
    drawer: true,
    links: [
      { icon: 'dashboard', text: 'Dashboard', route: '/' },
      { icon: 'folder', text: 'My Project', route: '/projects' },
      { icon: 'person', text: 'Team', route: '/team' }
    ],
    product: [
      { icon: 'dashboard', text: 'Harga' },
      { icon: 'dashboard', text: 'Kategori' },
      { icon: 'dashboard', text: 'Produk Listing' },
    ],
    marketing: [
      { icon: 'dashboard', text: 'Banner' },
      { icon: 'dashboard', text: 'Promo Produk' },
      { icon: 'dashboard', text: 'Voucher' },
    ],
    toko: [
      { icon: 'dashboard', text: 'Zona' },
      { icon: 'dashboard', text: 'Geopeching' },
      { icon: 'dashboard', text: 'Akun Toko' },
      { icon: 'dashboard', text: 'Membership Toko' },
      { icon: 'dashboard', text: 'Human Reource' },
    ],
    driver: [
      { icon: 'dashboard', text: 'Akun Driver' },
      { icon: 'dashboard', text: 'Aktifitas Order' },
    ],
    pengguna: [
      { icon: 'dashboard', text: 'Akun Pengguna' },
      { icon: 'dashboard', text: 'Membership Pengguna' },
    ],
    service: [
      { icon: 'dashboard', text: 'Komplain' },
      { icon: 'dashboard', text: 'Aktifitas Order' },
    ],

  }),
  components: {

  },


}
</script>
<style scoped>

.nullMargin{
  margin-top: -30px !important;
  
}

.nullpadding{
  padding: 0px !important;
}
.border {
  border-left: 4px solid #0ba518;
}

.serchNavbar {
  border-radius: 0.4rem;
}

.sideBar{
  width: 187px !important;
}
.nullShadow{
  box-shadow: none !important;
}
.compact-form {
  transform: scale(0.775);
  /* transform-Origin: left; */
}
.btnBiru{
  background-color: #0095E8 !important;
}

.font{
  font-family: Poppins;
}
</style>
