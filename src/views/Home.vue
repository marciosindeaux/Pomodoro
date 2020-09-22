<template>
  <v-container fill-height>
    <Card>
      <Cronometro>
      </Cronometro>
    </Card>
  </v-container>    
</template>


<script>
import Cronometro from '../components/Cronometro';
import Card from '../components/Card';
export default {
  name: 'Home',
  components: {
    Cronometro,
    Card
  }
}
</script>
