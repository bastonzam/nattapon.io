<template>
    <v-row>
        <v-col col="12" sm="6" >
             <v-card >
                <v-img
                class="white--text align-end"
                height="200px"
                :src="project.image"
                />
                <v-card-title class="headline">
                {{project.title}}
                </v-card-title>
                <v-card-text>
                {{project.description}}
                </v-card-text>

                <hr>
                <nuxt-content :document="project"></nuxt-content>
                
            </v-card>
        </v-col>
    </v-row>
</template>
<script>
export default {
    async asyncData({$content,params}){
        const projectData =  await $content('project',params.id).fetch();
        return {
            project : projectData
        }
    },
    mounted(){
        console.log(this.project);
    }
}
</script>