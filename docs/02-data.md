```vue
**Option API kullanımı:**

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  data() {
    return {
      carRate: "0",
      rate: "0",
      isReplied: false,
      isDisabled: true,
      comment: "",
    };
  },
});
</script>

**Composition API kullanımı:**

<script setup lang="ts">
import Vue from "vue";
const carRate = ref(0);
const rate = ref("0");
const isReplied = ref(false);
const isDisabled = ref(false);
const comment = ref("");
</script>

***Vue3 ile birlikte Data kullanımının yerini Ref almıştır. Peki neden Ref
kullanıyoruz? REF ile oluşturulan değişkenler, bileşen içinde kullanıldığında
otomatik olarak reaktif tepkilere neden olur. Bu, bileşenin otomatik olarak
güncellenmesini ve sayfanın dinamik olarak yenilenmesini sağlar.***
```
