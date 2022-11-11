<template>
  <div class="">
    <!-- <h1 class="subheading grey--text">Dashboard</h1> -->
    <v-container>
      <v-layout row wrap>
        <v-flex sm12 xs12 md12 lg12>
          <v-btn class="ma-2 white--text btnHijau" small>Tambah Outlet</v-btn>
        </v-flex>
        <v-flex sm6 xs12 md6 lg6>
          <v-card class="ma-2 ">
            <v-card-title class="font-weight-bold caption">
              Jumlah Outlet
            </v-card-title>
            <v-divider></v-divider>
            <v-card-title class="font-weight-bold caption">
              <h1>73</h1>
              <v-btn small class="compact-form btnJumlahOutlet">+2 Toko</v-btn>
            </v-card-title>
            <div id="chart">
              <apexchart type="bar" height="350" :options="chartOptions" :series="series"></apexchart>
            </div>
          </v-card>
        </v-flex>
        <v-flex sm6 xs12 md6 lg3>
          <v-card class="ma-2">
            <v-card-title class="font-weight-bold caption">
              Outlet Terlaris
            </v-card-title>
            <v-divider></v-divider>
            <v-list>
              <v-list-item class="caption">
                <v-list-item-content>Nama Outlet</v-list-item-content>
                <v-list-item-content class="itemOutlet">Pendapatan</v-list-item-content>
              </v-list-item>
              <v-list-item v-for="items in outletlaris" :key="items.kota" class="">
                <v-list-item-content>
                  <span class="font-weight-bold caption">{{items.toko}}</span>
                  <v-list-item-subtitle class="caption">{{items.kota}}</v-list-item-subtitle>
                </v-list-item-content>
                <v-list-item-content>
                  <v-btn class="caption" small>{{items.pendapatan}}</v-btn>
                </v-list-item-content>
              </v-list-item>
            </v-list>
          </v-card>
        </v-flex>
        <v-flex sm6 xs12 md6 lg3>
          <v-card class="ma-2 ">
            <v-card-title class="font-weight-bold caption">
              Outlet Baru
            </v-card-title>
            <v-divider></v-divider>
            <v-list>
              <v-list-item class="caption">
                <v-list-item-content>Nama Outlet</v-list-item-content>
                <v-list-item-content class="itemOutlet">Tanggal Daftar</v-list-item-content>
              </v-list-item>
              <v-list-item v-for="items in outletbaru" :key="items.kota" class="">
                <v-list-item-content>
                  <span class="font-weight-bold caption">{{items.toko}}</span>
                  <v-list-item-subtitle class="caption">{{items.kota}}</v-list-item-subtitle>
                </v-list-item-content>
                <v-list-item-content>
                  <v-btn class="caption" small>{{items.tanggal}}</v-btn>
                </v-list-item-content>
              </v-list-item>
            </v-list>
          </v-card>
        </v-flex>
        <v-flex sm12 xs12 md12 lg12>
          <v-card class="ma-2">
            <v-card-title class="font-weight-bold caption">
              List Outlet
            </v-card-title>
            <v-divider></v-divider>
            <v-row>
              <v-col cols="12" sm="2" class="pa-0">
                <v-select label="Semua Lokasi" class="serchNavbar compact-form" dense outlined></v-select>
              </v-col>
              <v-col class="pa-0" cols="12" sm="7"></v-col>
              <v-col cols="12" sm="3" class="pa-0">
                <v-text-field dense solo-inverted flat prepend-inner-icon="mdi-magnify" class="compact-form serchNavbar"
                  outlined clearable label="Search" type="text"></v-text-field>
              </v-col>

            </v-row>
            <v-simple-table class="pa-0">
              <template v-slot:default>
                <thead>
                  <tr>
                    <th class="text-left">No</th>
                    <th class="text-left">Nama Outlet</th>
                    <th class="text-left">Nama Pemilik</th>
                    <th class="text-left">Jumlah Transaksi</th>
                    <th class="text-left">Lokasi</th>
                    <th class="text-left">Tanggal Daftar</th>
                    <th class="text-left">Pendapatan</th>
                    <th class="text-left">Action</th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="item in listOutlet" :key="item.no">
                    <td>{{ item.no }}</td>
                    <td>{{ item.nama }}</td>
                    <td>{{ item.pemilik }}</td>
                    <td>{{ item.transaksi }}</td>
                    <td>{{ item.lokasi }}</td>
                    <td>{{ item.tglDaftar }}</td>
                    <td>{{ item.pendapatan }}</td>
                    <td>
                      <v-btn small class="white--text primary btnBiru">Rincian</v-btn>
                    </td>
                  </tr>
                </tbody>
              </template>
            </v-simple-table>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
import VueApexCharts from 'vue-apexcharts';
// import ApexCharts from 'apexcharts';

export default {
  name: 'team',
  components: {
    apexchart: VueApexCharts,
  },
  data: () => ({
    //chart 
    series: [{
      name: 'Net Profit',
      data: [44, 55, 57, 56, 61, 58, 63, 60, 66, 90, 34, 12]
    }, {
      name: 'Revenue',
      data: [76, 85, 101, 98, 87, 105, 91, 114, 94, 90, 34, 12]
    }],
    chartOptions: {
      chart: {
        type: 'bar',
        height: 350
      },
      plotOptions: {
        bar: {
          horizontal: false,
          columnWidth: '55%',
          endingShape: 'rounded'
        },
      },
      dataLabels: {
        enabled: false
      },
      stroke: {
        show: true,
        width: 2,
        colors: ['transparent']
      },
      xaxis: {
        categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Des'],
      },
      yaxis: {
        title: {
          text: '$ (thousands)'
        }
      },
      fill: {
        opacity: 1
      },
      tooltip: {
        y: {
          formatter: function (val) {
            return "$ " + val + " thousands"
          }
        }
      }
    },
    //endchart
    team: [
      { name: 'Iyad', role: 'web developer', avatar: '/img1.png' },
      { name: 'Reda', role: 'Graphic designer', avatar: '/img2.png' },
      { name: 'Zineb', role: 'web developer', avatar: '/img3.png' },
      { name: 'Hu TechGroup', role: 'Desktop developer', avatar: '/img4.png' },
    ],
    item: [
      {}
    ],
    listOutlet: [
      { no: 1, nama: 'Toko 1', pemilik: 'Floyd Milles', transaksi: 23, lokasi: 'Bandung', tglDaftar: '2 Juni 2022', pendapatan: 'Rp. 20.000.000' },
      { no: 2, nama: 'Toko 2', pemilik: 'Robet Fox', transaksi: 12, lokasi: 'Jakarta', tglDaftar: '2 Juni 2022', pendapatan: 'Rp. 20.000.000' },
      { no: 3, nama: 'Toko 3', pemilik: 'Courtney Henry', transaksi: 31, lokasi: 'Solo', tglDaftar: '2 Juni 2022', pendapatan: 'Rp. 20.000.000' },
      { no: 4, nama: 'Toko 4', pemilik: 'Arlene McCoy', transaksi: 24, lokasi: 'Semarang', tglDaftar: '2 Juni 2022', pendapatan: 'Rp. 20.000.000' },
      { no: 5, nama: 'Toko 5', pemilik: 'Annetle Black', transaksi: 12, lokasi: 'Bandung', tglDaftar: '2 Juni 2022', pendapatan: 'Rp. 20.000.000' },
    ],
    outletlaris : [
      {toko : 'Toko ABC', kota: 'Bandung', pendapatan: 'Rp. 20.000.000'},
      {toko : 'Toko ABC', kota: 'Jakarta', pendapatan: 'Rp. 20.000.000'},
      {toko : 'Toko ABC', kota: 'Solo', pendapatan: 'Rp. 20.000.000'},
      {toko : 'Toko ABC', kota: 'Semarang', pendapatan: 'Rp. 20.000.000'},
      {toko : 'Toko ABC', kota: 'Majalengka', pendapatan: 'Rp. 20.000.000'},
    ],
    outletbaru : [
    {toko : 'Toko ABC', kota: 'Bandung', tanggal: '2 juni 2022'},
    {toko : 'Toko ABC', kota: 'Jakarta', tanggal: '2 juni 2022'},
    {toko : 'Toko ABC', kota: 'Solo', tanggal: '2 juni 2022'},
    {toko : 'Toko ABC', kota: 'Semarang', tanggal: '2 juni 2022'},
    {toko : 'Toko ABC', kota: 'Majalengka', tanggal: '2 juni 2022'},
    ]
  }),
  methods: {

  },
}
</script>
<style scoped>
.jumlahOutlet {
  width: 560px;
  margin: 0px;
}

.compact-form {
  transform: scale(0.775);
  /* transform-Origin: left; */
}
.jenis-font{
  font-family: Poppins;
}
.outletLaris {
  width: 270px !important;
  margin: 0px;
}

.nullspacing {
  margin: 0rem;
  padding: 0rem;
}

.nullShadow {
  box-shadow: none !important;
}

.serchNavbar {
  border-radius: 0.4rem;
}

.textRight {
  text-align: right;
}

.btnColor {
  background-color: #0095E8;
  color: white;
}

.itemOutlet {
  margin-left: 3rem;
}

.btnBiru {
  background-color: #0095E8 !important;
  border-radius: 6px !important;
}

.btnHijau {
  background-color: #50CD89 !important;
  border-radius: 6px;
  padding: 6px 12px !important;
}

.btnJumlahOutlet {
  background-color: #E8FFF3 !important;
  color: #2BA579 !important;
  border-radius: 8px !important;

}
</style>
