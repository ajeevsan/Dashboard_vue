<template>
    <div class="buttonTest">
      <el-dropdown>
        <el-button type="primary">
          Dropdown List<i class="el-icon-arrow-down el-icon--right"></i>
        </el-button>
        <el-dropdown-menu slot="dropdown">
          <el-dropdown-item @click.native="clickButton('curr')">Current Page</el-dropdown-item>
          <el-dropdown-item @click.native="clickButton('all')">All Page</el-dropdown-item>
        </el-dropdown-menu>
      </el-dropdown>
  
      <div class="selectOption">
        <el-select v-model="selectedFruits" multiple filterable allow-create
                   placeholder="Choose tags for your article" @change="updateLocalStorage">
          <el-option v-for="fruit in fruits" :key="fruit" :label="fruit" :value="fruit">
          </el-option>
        </el-select>
      </div>
  
      <!-- Main Table with Border -->
      <el-table :data="projects" border style="margin-top: 20px;">
        <el-table-column prop="projectName" label="Project Name"></el-table-column>
        <el-table-column prop="projectType" label="Project Type"></el-table-column>
        <el-table-column prop="devType" label="Dev Type"></el-table-column>
        <el-table-column label="Trackers">
          <template slot-scope="scope">
            <el-table :data="scope.row.trackers" border style="width: 100%">
              <el-table-column prop="trackerName" label="Tracker Name"></el-table-column>
              <el-table-column prop="data" label="Data"></el-table-column>
            </el-table>
          </template>
        </el-table-column>
      </el-table>
    </div>
  </template>
  
  <script>
  export default {
    name: 'LgDashboard',
    data() {
      return {
        fruits: [
          "Apple",
          "Banana",
          "Cherry",
          "Date",
          "Elderberry",
          "Fig",
          "Grape",
          "Honeydew",
          "Kiwi",
          "Lemon"
        ],
        selectedFruits: ["Apple", "Banana", "Cherry", "Date"],
        projects: [
          {
            projectName: 'Project A',
            projectType: 'Type 1',
            devType: 'Frontend',
            trackers: [
              { trackerName: 'Tracker 1', data: 'Data 1' },
              { trackerName: 'Tracker 2', data: 'Data 2' },
              { trackerName: 'Tracker 3', data: 'Data 3' },
              { trackerName: 'Tracker 4', data: 'Data 4' },
              { trackerName: 'Tracker 5', data: 'Data 5' },
              { trackerName: 'Tracker 6', data: 'Data 6' },
              { trackerName: 'Tracker 7', data: 'Data 7' },
              { trackerName: 'Tracker 8', data: 'Data 8' },
              { trackerName: 'Tracker 9', data: 'Data 9' },
              { trackerName: 'Tracker 10', data: 'Data 10' }
            ]
          },
          {
            projectName: 'Project B',
            projectType: 'Type 2',
            devType: 'Backend',
            trackers: [
              { trackerName: 'Tracker 1', data: 'Data 1' },
              { trackerName: 'Tracker 2', data: 'Data 2' },
              { trackerName: 'Tracker 3', data: 'Data 3' },
              { trackerName: 'Tracker 4', data: 'Data 4' },
              { trackerName: 'Tracker 5', data: 'Data 5' },
              { trackerName: 'Tracker 6', data: 'Data 6' },
              { trackerName: 'Tracker 7', data: 'Data 7' },
              { trackerName: 'Tracker 8', data: 'Data 8' },
              { trackerName: 'Tracker 9', data: 'Data 9' },
              { trackerName: 'Tracker 10', data: 'Data 10' }
            ]
          }
        ]
      };
    },
    methods: {
      clickButton(value) {
        if (value === 'all') {
          console.log('All Page');
        } else {
          console.log('Current Page');
        }
      },
      updateLocalStorage() {
        const existingData = JSON.parse(localStorage.getItem('data')) || [];
        const updatedData = [...existingData, ...this.selectedFruits];
        const uniqueData = [...new Set(updatedData)];
        localStorage.setItem('data', JSON.stringify(uniqueData));
      },
      loadFromLocalStorage() {
        const data = localStorage.getItem('data');
        if (data) {
          this.selectedFruits = JSON.parse(data);
        } else {
          this.selectedFruits = ["Apple", "Banana", "Cherry", "Date"];
          this.updateLocalStorage();
        }
      }
    },
    mounted() {
      this.loadFromLocalStorage();
    }
  };
  </script>
  
  <style>
  .el-dropdown {
    vertical-align: top;
  }
  
  .el-dropdown + .el-dropdown {
    margin-left: 15px;
  }
  
  .el-icon-arrow-down {
    font-size: 12px;
  }
  
  .buttonTest {
    margin-top: 10%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .selectOption {
    margin-top: 20px;
    width: 300px;
  }
  </style>
  