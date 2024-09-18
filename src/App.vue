<script setup lang="ts">
import IsometricImageFlow from './IsometricImageFlow.vue';
</script>
<template>
  <div class="content">
    <h1>Isometric Image Flow</h1>
    <IsometricImageFlow
      class="isometric-image-flow"
      :images="[
        'https://images.unsplash.com/photo-1472491235688-bdc81a63246e?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8Y2F0fGVufDB8fDB8fHww',
        'https://images.unsplash.com/photo-1514888286974-6c03e2ca1dba?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8N3x8Y2F0fGVufDB8fDB8fHww',
        'https://images.unsplash.com/photo-1571566882372-1598d88abd90?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTJ8fGNhdHxlbnwwfHwwfHx8MA%3D%3D',
        'https://images.unsplash.com/photo-1513360371669-4adf3dd7dff8?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTR8fGNhdHxlbnwwfHwwfHx8MA%3D%3D',
        'https://images.unsplash.com/photo-1533743983669-94fa5c4338ec?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MjR8fGNhdHxlbnwwfHwwfHx8MA%3D%3D',
        'https://images.unsplash.com/photo-1492370284958-c20b15c692d2?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MzR8fGNhdHxlbnwwfHwwfHx8MA%3D%3D',
        'https://images.unsplash.com/photo-1511275539165-cc46b1ee89bf?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NDB8fGNhdHxlbnwwfHwwfHx8MA%3D%3D',
        'https://images.unsplash.com/photo-1574158622682-e40e69881006?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NDR8fGNhdHxlbnwwfHwwfHx8MA%3D%3D',
        'https://images.unsplash.com/photo-1529933037705-0d537317ae7b?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NDh8fGNhdHxlbnwwfHwwfHx8MA%3D%3D',
        'https://images.unsplash.com/photo-1490481920145-fc78891bbb99?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NTB8fGNhdHxlbnwwfHwwfHx8MA%3D%3D',
        'https://images.unsplash.com/photo-1472053092455-ee16a8b358b9?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NTJ8fGNhdHxlbnwwfHwwfHx8MA%3D%3D',
        'https://images.unsplash.com/photo-1497473376897-16fbb7552478?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NTh8fGNhdHxlbnwwfHwwfHx8MA%3D%3D',
        'https://images.unsplash.com/photo-1561948955-570b270e7c36?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NTl8fGNhdHxlbnwwfHwwfHx8MA%3D%3D',
        'https://images.unsplash.com/photo-1504384558400-c1347a7bd18f?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NjZ8fGNhdHxlbnwwfHwwfHx8MA%3D%3D',
      ]"
    />
  </div>
</template>

<style scoped>
.content {
  display: flex;
  min-height: 100vh;
  line-height: 1.1;
  text-align: center;
  flex-direction: column;
  justify-content: center;
}

.content h1 {
  font-size: 3.6rem;
  font-weight: 700;
  margin: 2rem 0;
}
.isometric-image-flow {
  width: 80vw;
  height: 50vh;
  margin: 0 auto;
}
</style>
