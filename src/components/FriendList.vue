<template>
  <table class="w-64 my-5 p-1 flex flex-col h-auto border rounded-md">
    <tr class="flex flex-row justify-start py-3 px-8">
      <th>Hizb</th>
      <th class=" pl-8">Nome</th>
    </tr>
    <tr
      class="flex flex-row justify-between py-1 px-8 border-0 border-b border-gray-100"
      v-for="(item, index) in nomi"
      :key="item.id"
    >
      <td>{{ index + 1 }}</td>
      <td>
        <input class=" w-28 block" type="text" v-model="item.nome" />
      </td>
    </tr>
  </table>
</template>

<script>
export default {
  name: "FriendList",
  props: ["nomi"],
};
</script>

<style>
tr {
  font-family: Nunito;
}
</style>