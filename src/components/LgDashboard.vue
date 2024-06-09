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
            selectedFruits: ["Apple", "Banana", "Cherry", "Date"]
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
            // Load existing data from localStorage
            const existingData = JSON.parse(localStorage.getItem('data')) || [];

            // Merge existing data with selectedFruits
            const updatedData = [...existingData, ...this.selectedFruits];

            // Remove duplicates
            const uniqueData = [...new Set(updatedData)];

            // Save the updated list to localStorage
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

.el-dropdown+.el-dropdown {
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
