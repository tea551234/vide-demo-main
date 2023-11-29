<template>
  <div>
    <input v-show="state.length < 2" type="file" @change="handleFileUpload" />
    <table v-show="state.length > 2">
      <tr>
        <th>DCS ID</th>
        <th>Lsc Type</th>
        <th>Lsc Tool</th>
        <th>Lsc Chamber</th>
        <th>Lsc Location</th>
        <th>Lsc Location ID</th>
        <th>Lsc IP</th>
        <th>Lsc Other</th>
        <th>Actions</th>
      </tr>
      <tr v-for="(item, index) in state" :key="index">
        <td>{{ item.DCS_ID }}</td>
        <td>{{ item.Lsc_Type }}</td>
        <td>{{ item.Lsc_Tool }}</td>
        <td>{{ item.Lsc_Chamber }}</td>
        <td>{{ item.Lsc_Location }}</td>
        <td>{{ item.Lsc_LocationID }}</td>
        <td>{{ item.Lsc_IP }}</td>
        <td>{{ item.Lsc_Other }}</td>
        <td>
          <button @click="editItem(index)">Edit</button>
          <button @click="deleteItem(index)">Delete</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue';
import * as XLSX from 'xlsx';

type Dcs = {
  DCS_ID: string;
  Lsc_Type: string;
  Lsc_Tool: string;
  Lsc_Chamber: string;
  Lsc_Location: string;
  Lsc_LocationID: string;
  Lsc_IP: string;
  Lsc_Other?: string;
};

const state: Dcs[] = reactive([

]);

const handleFileUpload = (e: any) => {
  const files = e.target.files;
  const fileReader = new FileReader();
  fileReader.readAsArrayBuffer(files[0]);
  fileReader.onload = (e) => {
    if (!e.target) {
      return;
    }
    const bufferArray = e.target.result;
    const wb = XLSX.read(bufferArray, { type: 'buffer' });
    const wsname = wb.SheetNames[0];
    const ws = wb.Sheets[wsname];
    const data: any = XLSX.utils.sheet_to_json(ws);
    console.log(data);
    for (let i = 1; i < data.length; i++) {
      if (data[i].__EMPTY_4 && data[i].__EMPTY_5) {
        state.push({
          DCS_ID: data[i].KT,
          Lsc_Type: data[i].__EMPTY_9,
          Lsc_Location: data[i].__EMPTY_3 + '/' + data[1].__EMPTY_2,
          Lsc_LocationID: data[i].__EMPTY_5,
          Lsc_IP: data[i].__EMPTY_7,
          Lsc_Tool: data[i].__EMPTY_4,
          Lsc_Chamber: (data[i].__EMPTY_6 + '').toUpperCase()
        });
      }
    }
  };
};

const editItem = (index: number) => {
  // Logic to open edit window and modify the item at the given index
  console.log(index);

};

const deleteItem = (index: number) => {
  state.splice(index, 1);

};

</script>

<style scoped></style>