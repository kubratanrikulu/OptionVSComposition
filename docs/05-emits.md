`emit`, Vue.js bileşenlerinde olayları tetiklemek için kullanılan bir yöntemdir. Olaylar, bir bileşenin içinde veya dışında gerçekleşen eylemleri veya durum değişikliklerini temsil eder. Bir bileşen içinde bir olay tetiklendiğinde, bu olayı dinleyen diğer bileşenler veya dışarıdaki kod bu olayı algılayabilir ve buna tepki verebilir.

Emit değişimini iki açıdan inceleyebiliriz.

1-Readonly Props:

**Composition api birlikte propslar Readonly haline geldi. O yüzden fonksiyonlar içinde proplara değişim yapamadığımız zaman emit yoluyla bu sorunu çözebiliriz.**(Aşağıdaki örnek ESLint kurallarına göre yazılmıştır.)

**COMPOSITION API**

<script setup>
import { defineEmits } from 'vue'
type Emits = {
  (e: 'changeValueType'): void
}
const emit = defineEmits<Emits>()
const showForm = () => {
  emit('changeValueType')
}
</script>

**OPTION API**

<script>

export default {
methods: {
    showForm() {
      this.value.type = 'showForm'
    }
  }
};
</script>

2. Emit yazımı farklılıkları :

**COMPOSITION API**

<template>
<button @click="triggerEvent">Olayı Tetikle</button>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from 'vue';

const emit = defineEmits();

const triggerEvent = () => {
  emit('custom-event', 'veri');
};
</script>

**OPTION API**

<script>

export default {
  triggerEvent() {
    this.$emit('custom-event', 'veri');
  }
};
</script>
