<template>
  <v-row >
    <v-col cols="12" sm="6" md="6" v-for="p in project" :key="p.slug">
      <v-card >
        <v-card-title class="headline">
          {{p.title}}
        </v-card-title>
        <v-card-text>
          {{p.description}}
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            nuxt
            :to="{name:'project-id',params:{id:p.slug}}"
          >
            Show detail of {{p.title}}
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>
<script>
export default {
  async asyncData({$content}){
     const projectData = await $content('project').fetch();
     return {
       project:projectData
     }
  },
  mounted(){
    console.log(this.project)
  }
}
</script>
