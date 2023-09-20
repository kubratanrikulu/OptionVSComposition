```vue
**Option API kullanımı:**

<script lang="ts">
import { computed } from 'vue'
export default Vue.extend({
  props: {
    message: {
      type: Object as () => Record<string, any>, 
      required: true
    }
  }
  computed: {
    submitButton() {
      return this.message.data.elements && this.message.data.elements[0]
    },
  }
});
</script>

**Composition API kullanımı:**

<script setup lang="ts">
import { computed } from 'vue'
const props = defineProps({
  message: {
    type: Object,
    required: true
  }
})
const submitButton = computed(() => {
  return props.message.data.elements && props.message.data.elements[0]
})
</script>

**_Vue.js'de "Composition API" ve "Options API" (veya "Opinion API" olarak da bilinir) arasındaki computed özelliklerinin kullanımında temel bir fark yoktur._**
