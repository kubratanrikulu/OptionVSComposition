**Option API kullanımı:**

<script lang="ts">
export default Vue.extend({
  props: {
    value: {
      type: Array as () => Array<any>, 
      required: true
    },
    message: {
      type: Object as () => Record<string, any>, 
      required: true
    }
  }
});
</script>

**Composition API kullanımı:**

<script setup lang="ts">
const props = defineProps({
  value: {
    type: Object,
    required: true
  },
  message: {
    type: Object,
    required: true
  }
})
</script>

<script setup lang="ts">
import { defineProps } from 'vue'

interface Props {
  value: Array<any>
  message: Object
}

const props = defineProps<Props>()
</script>

**_Vue3'te propslar Readonly haline getirilmiştir. Yani sadece okunabilir değeri değiştirilemez._**
