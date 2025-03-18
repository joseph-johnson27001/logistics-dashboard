<template>
  <div class="orders-by-countries">
    <div v-for="(country, index) in countries" :key="index" class="country-row">
      <div class="country-details">
        <img :src="country.flag" alt="Flag" class="flag" />
        <div class="financial-info">
          <div class="financial-value">{{ country.financialValue }}</div>
          <div class="country-name">{{ country.name }}</div>
        </div>
      </div>

      <div class="percentage-change">
        <div
          :class="[
            'change-value',
            { increase: country.change >= 0, decrease: country.change < 0 },
          ]"
        >
          <span class="chevron" :class="chevronClass(country.change)">
            <i :class="chevronIconClass(country.change)"></i>
          </span>
          {{ country.change }}%
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "OrdersByCountry",
  data() {
    return {
      countries: [
        {
          flag: "https://flagcdn.com/w320/us.png",
          financialValue: "$1,200,000",
          name: "United States",
          change: 5.4,
        },
        {
          flag: "https://flagcdn.com/w320/fr.png",
          financialValue: "$800,000",
          name: "France",
          change: -3.2,
        },
        {
          flag: "https://flagcdn.com/w320/gb.png",
          financialValue: "$1,000,000",
          name: "United Kingdom",
          change: 2.1,
        },
      ],
    };
  },
  computed: {
    chevronClass() {
      return (change) => {
        return change >= 0 ? "up" : "down";
      };
    },
    chevronIconClass() {
      return (change) => {
        return change >= 0 ? "fas fa-chevron-up" : "fas fa-chevron-down";
      };
    },
  },
};
</script>

<style scoped>
.country-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 5px;
  cursor: pointer;
}
.country-row:hover {
  background-color: #f5f5f5;
}

.country-details {
  display: flex;
  align-items: center;
}

.flag {
  width: 35px;
  height: 35px;
  border-radius: 50%;
  margin-right: 15px;
}

.financial-info {
  display: flex;
  flex-direction: column;
}

.financial-value {
  font-size: 16px;
  font-weight: 500;
  color: #333;
}

.country-name {
  margin-top: 2px;
  font-size: 13px;
  color: rgba(47, 43, 61, 0.55);
}

.percentage-change {
  display: flex;
  align-items: center;
}

.change-value {
  font-size: 15px;
  display: flex;
  align-items: center;
}

.change-value.increase {
  color: #10b981;
}

.change-value.decrease {
  color: #ef4444;
}

.chevron {
  margin-right: 8px;
}

.chevron.up {
  color: #10b981;
}

.chevron.down {
  color: #ef4444;
}
</style>
