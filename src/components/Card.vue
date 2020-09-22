<template>
    <v-card 
        class="mx-auto"
        color="blue-grey lighten-4"
        max-width="600">
        <v-card-text>
            <slot>
            </slot>
        </v-card-text>
    </v-card>
</template>
<style  scoped>
</style>
<script>
import Cronometro from './Cronometro'
export default {
    components:{
        Cronometro
    }
}
</script>