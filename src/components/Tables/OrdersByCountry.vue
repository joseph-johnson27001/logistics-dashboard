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
          <span
            class="chevron"
            :class="{ up: country.change >= 0, down: country.change < 0 }"
          >
            <i
              class="fas"
              :class="{
                'fa-chevron-up': country.change >= 0,
                'fa-chevron-down': country.change < 0,
              }"
            ></i>
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
};
</script>

<style scoped>
.country-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
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
  font-size: 16px; /* Same font size as the table */
  font-weight: 500; /* Same font weight as the table */
  display: flex;
  align-items: center;
}

.change-value.increase {
  color: #10b981; /* Green for increase */
}

.change-value.decrease {
  color: #ef4444; /* Red for decrease */
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
