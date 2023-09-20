`<script setup>` bloğu, Vue 3.0'da tanıtılan ve bileşen kodunu daha sade ve okunabilir hale getiren bir özelliktir. Bu özellik, Composition API'yi kullanırken bileşenlerin daha az kodla yazılmasını sağlar. İşte <script setup> bloğunun neden kullanıldığına dair bazı nedenler:

1-Daha Az Kod: <script setup> kullanarak, bir bileşenin verilerini, işlevlerini ve diğer özelliklerini daha kısa ve daha net bir şekilde tanımlayabilirsiniz. Bu, kodun daha az satırdan oluşmasını sağlar ve bileşenin işlevselliğini daha kolay anlamanıza yardımcı olur.

A. Veri tanımlama
**COMPOSITION API**

<script setup>
import { ref } from 'vue';

const count = ref(0);
</script>

**OPTION API**

<script>

export default {
  data() {
    return {
      count: 0,
    };
  },
};
</script>

B. Olay İşleme

**COMPOSITION API**

<script setup>
const incrementCount = () => {
  count.value++;
};
</script>

**OPTION API**

<script>
export default {
  methods: {
    incrementCount() {
      this.count++;
    }
  }
};
</script>

C. Tekrar İşlemler

**COMPOSITION API**

<template>
  <ul>
    <li v-for="item in items" :key="item.id">{{ item.name }}</li>
  </ul>
</template>

<script setup>
const items = [
  { id: 1, name: 'Öğe 1' },
  { id: 2, name: 'Öğe 2' },
  { id: 3, name: 'Öğe 3' },
];
</script>

**OPTION API**

<template>
  <ul>
    <li v-for="item in items" :key="item.id">{{ item.name }}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { id: 1, name: 'Öğe 1' },
        { id: 2, name: 'Öğe 2' },
        { id: 3, name: 'Öğe 3' },
      ],
    };
  },
};
</script>

2-Karmaşıklığı Azaltır: Bu yapı, bileşen içindeki verilerin ve işlevlerin daha az karmaşık hale gelmesini sağlar. Her şeyi aynı blokta tanımladığınız için, verilere daha kolay erişebilirsiniz.

**COMPOSITION API**

<template>
  <div>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        {{ item.name }} - {{ item.price }} TL
        <button @click="removeItem(index)">Ürünü Kaldır</button>
      </li>
    </ul>
    <p>Toplam: {{ total }} TL</p>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const items = ref([
  { name: "Ürün 1", price: 50 },
  { name: "Ürün 2", price: 30 },
  { name: "Ürün 3", price: 20 }
]);

const total = computed(() => {
  return items.value.reduce((sum, item) => sum + item.price, 0);
});

const removeItem = (index) => {
  items.value.splice(index, 1);
};
</script>

**OPTION API**

<template>
  <div>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        {{ item.name }} - {{ item.price }} TL
        <button @click="removeItem(index)">Ürünü Kaldır</button>
      </li>
    </ul>
    <p>Toplam: {{ total }} TL</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { name: "Ürün 1", price: 50 },
        { name: "Ürün 2", price: 30 },
        { name: "Ürün 3", price: 20 }
      ],
      total: 0
    };
  },
  methods: {
    removeItem(index) {
      this.items.splice(index, 1);
      this.calculateTotal();
    },
    calculateTotal() {
      this.total = this.items.reduce((sum, item) => sum + item.price, 0);
    }
  },
  created() {
    this.calculateTotal();
  }
};
</script>

3-Daha Okunabilir Kod: <script setup> kullanmak, bileşen kodunu daha okunabilir hale getirir. Veriler ve işlevler aynı blokta tanımlandığı için, bileşenin nasıl çalıştığını daha iyi anlamak daha kolaydır.

4-Hata Ayıklama Kolaylığı: <script setup> kullanmak, hata ayıklama işlemini kolaylaştırabilir. Veriler ve işlevler daha sade olduğu için hataları bulmak ve düzeltmek daha kolaydır.
