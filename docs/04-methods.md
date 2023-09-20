**Option API kullanımı:**

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  data() {
    return {
      rate: '0',
      isReplied: false,
      isDisabled: false
    };
  },
  methods: {
    emojiChecked() {
      if (this.rate === '0') {
        this.isDisabled = true;
      } else {
        this.isDisabled = false;
      }
    },
  },
});
</script>

**Composition API kullanımı:**

<script setup lang="ts">
import { ref, computed } from 'vue'
const rate = ref('0')
const isReplied = ref(false)
const isDisabled = ref(false)
const emojiChecked = () => {
  if (rate.value.toString() == '0') {
    isDisabled.value = true
  } else {
    isDisabled.value = false
  }
}
</script>

**_Composition API, methods bölümüne ihtiyaç duymaz. Bunun yerine, işlevleri doğrudan setup içinde tanımlayabilirsiniz. setup içinde tanımlanan işlevler, bileşenin içinde kullanılabilir ve reaktif verilere ve diğer bileşen özelliklerine erişebilir._**
