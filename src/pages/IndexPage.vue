<template>
  <q-page class="flex flex-center">

    <q-table
      title="Treats"
      :rows="rows"
      :columns="columns"
      row-key="name"
      v-model:pagination="pagination"
      hide-pagination
    />

  </q-page>
</template>

<script>
import { ref, computed } from 'vue'

const columns = [
  {
    name: 'desc',
    required: true,
    label: 'Dessert (100g serving)',
    align: 'left',
    field: row => row.name,
    format: val => `${val}`,
    sortable: true
  },
  { name: 'calories', align: 'center', label: 'Calories', field: 'calories', sortable: true },
  { name: 'fat', label: 'Fat (g)', field: 'fat', sortable: true },
  { name: 'carbs', label: 'Carbs (g)', field: 'carbs' },
  { name: 'protein', label: 'Protein (g)', field: 'protein' }
]

const rows = [
  {
    name: 'Frozen Yogurt',
    calories: 159,
    fat: 6.0,
    carbs: 24,
    protein: 4.0
  }

]

export default ({
  setup () {
    const pagination = ref({
      sortBy: 'desc',
      descending: false,
      page: 2,
      rowsPerPage: 3
    })

    return {
      pagination,
      columns,
      rows,

      pagesNumber: computed(() => Math.ceil(rows.length / pagination.value.rowsPerPage))
    }
  }
})

</script>
