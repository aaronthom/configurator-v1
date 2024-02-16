<template>
  <!-- Zylinder Reihe -->
  <div class="row" v-for="(row, index) in rows" :key="index">
    <!-- Zylinder Reihe Inhalte -->
    <div class="row">
      <div class="position">
        <h4>Pos.</h4>
        <div class="position-number">1</div>
      </div>
      <div class="door-designation">
        <h4>Türbeschreibung</h4>
        <input type="text" placeholder="z.B. Haupteingang" />
      </div>
      <div class="quantity">
        <h4>Anzahl</h4>
        <input type="number" />
      </div>
      <div class="cylinder-type">
        <h4>Zylinder-Typ</h4>
        <select class="select-cylinder">
          <option value="doppelzylinder">Doppelzylinder</option>
          <option value="knaufzylinder">Knaufzylinder</option>
          <option value="halbzylinder">Halbzylinder</option>
          <option value="vorhangschloss50">Vorhangschloss 50mm</option>
          <option value="vorhangschloss80">Vorhangschloss 80mm</option>
          <option value="briefkastenschloss">Briefkastenschloss</option>
        </select>
      </div>
      <div class="size-outside">
        <h4>Außen</h4>
        <select class="select-size-outside">
          <option value="30">30</option>
          <option value="35">35</option>
          <option value="40">40</option>
          <option value="45">45</option>
          <option value="50">50</option>
          <option value="55">55</option>
          <option value="60">60</option>
          <option value="N/A">N/A</option>
        </select>
      </div>
      <div class="size-inside">
        <h4>Innen</h4>
        <select class="select-size-inside">
          <option value="30">30</option>
          <option value="35">35</option>
          <option value="40">40</option>
          <option value="45">45</option>
          <option value="50">50</option>
          <option value="55">55</option>
          <option value="60">60</option>
          <option value="N/A">N/A</option>
        </select>
      </div>
      <div class="options">
        <h4>Optionen</h4>
        <select class="select-options">
          <option value="ngfunkion">Not- & Gefahrenfunktion</option>
          <option value="drehknauf">Drehknauf</option>
          <option value="fzg">FZG</option>
          <option value="abhkl1">ABH Kl. 1</option>
          <option value="abhkl2">ABH Kl. 2</option>
          <option value="psh">PSH</option>
          <option value="modular">Modular</option>
        </select>
      </div>
      <div class="buttons">
        <div class="space"></div>
        <button class="duplicate"><i class="fa-solid fa-copy"></i></button>
        <button class="delete"><i class="fa-solid fa-trash"></i></button>
      </div>
    </div>

    <!-- Checkbox Matrix für die Zylinder Reihe -->
    <CheckboxMatrix :numCheckboxes="maxCheckboxes" />
  </div>

  <!-- Button zum Hinzufügen einer neuen Zylinder Reihe -->
  <button @click="addRow">Neue Zylinder Reihe hinzufügen</button>
</template>

<script>
import CheckboxMatrix from './CheckboxMatrix.vue'

export default {
  components: {
    CheckboxMatrix
  },
  data() {
    return {
      rows: [], // Array, um Zylinderreihen zu speichern
      maxCheckboxes: 0 // Anzahl der maximalen Checkboxen für alle Reihen
    }
  },
  methods: {
    addRow() {
      // Hinzufügen einer neuen Zylinder Reihe
      this.rows.push({})

      // Aktualisierung der maximalen Anzahl von Checkboxen
      this.maxCheckboxes = Math.max(this.maxCheckboxes, this.rows.length)
    }
  }
}
</script>

<style scoped>
.row {
  display: flex;
  flex-direction: row;
  align-items: center;
}

input[type='number'] {
  width: 50px;
  height: 30px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 0 5px;
  margin: 0 5px;
  outline: none;
  text-align: center;
  font-size: 12px;
  font-weight: 500;
  color: #333;
  background-color: #fff;
  box-sizing: border-box;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}

input[type='text'] {
  width: 200px;
  height: 30px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 0 5px;
  margin: 0 5px;
  outline: none;
  font-size: 12px;
  color: #333;
  background-color: #fff;
  box-sizing: border-box;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}

.select-cylinder,
.select-options {
  width: 200px;
  height: 30px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 0 5px;
  margin: 0 5px;
  outline: none;
  font-size: 12px;
  color: #333;
  background-color: #fff;
  box-sizing: border-box;
}

.select-size-inside,
.select-size-outside {
  width: 50px;
  height: 30px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 0 5px;
  margin: 0 5px;
  outline: none;
  font-size: 12px;
  color: #333;
  background-color: #fff;
  box-sizing: border-box;
}

option {
  font-size: 14px;
  font-family: Arial, Helvetica, sans-serif;
}

.duplicate, .delete {
  width: 50px;
  height: 30px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 0 5px;
  margin: 0 5px;
  outline: none;
  font-size: 12px;
  color: #333;
  background-color: #fff;
  box-sizing: border-box;
  cursor: pointer;
}

i {
  font-size: large;
  color: #333;
}

.position-number {
  width: 40px;
  height: 30px;
  text-align: center;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 5px 5px;
  margin: 0 5px;
  outline: none;
  font-size: 14px;
  font-weight: 600;
  color: #333;
  box-sizing: border-box;
  background-color: #fff;
}

.space {
  height: 60px;
}
</style>
