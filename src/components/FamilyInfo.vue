<template>
    <div class="family-container">
      <h2>Family</h2>
      <table>
        <thead>
          <tr>
            <th>Name</th>
            <th>Relation</th>
            <th>SSN</th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="(member, index) in family"
            :key="index"
            @mouseenter="hoveredIndex = index"
            @mouseleave="hoveredIndex = null"
          >
            <td>{{ member.name }}</td>
            <td>{{ member.relation }}</td>
            <td>
              {{ hoveredIndex === index ? member.ssn : maskedSSN(member.ssn) }}
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    name: 'FamilyInfo',
    data() {
      return {
        family: [
          { name: '김아빠', relation: 'Father', ssn: '890101-1234567' },
          { name: '김엄마', relation: 'Mother', ssn: '890101-1234567' },
          { name: '김철수', relation: 'Son', ssn: '000101-1234567' },
          { name: '김영희', relation: 'Daughter', ssn: '000101-1234567' }
        ],
        hoveredIndex: null
      };
    },
    methods: {
      maskedSSN(ssn) {
        return ssn.replace(/^(\d{6})-(\d{1})\d{6}$/, '$1-$2******');
      }
    }
  };
  </script>
  
  <style scoped>

  .family-container {
    padding: 20px;
  }
  table {
    width: 100%;
    border-collapse: collapse;
  }
  tr:hover {
    background-color: #f8f8f8;
    cursor: pointer;
  }
  </style>

  
  