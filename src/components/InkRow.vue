<template>
  <tr>
    <td class="text-left">{{ ink.name | capitalize }}</td>
    <td>{{ ink.stockNo }}</td>
    <td>{{ ink.colors | arrayToString }}</td>
    <td>
      <i :class="ink.uvResistant | setCssClasses" :title="ink.uvResistant | capitalize | boolToString" data-toggle="tooltip"></i>
    </td>
    <td>
      <i :class="ink.archival | setCssClasses" :title="ink.archival | capitalize | boolToString"></i>
    </td>
    <td>
      <i :class="ink.forSecurityDocs | setCssClasses" :title="ink.forSecurityDocs | capitalize | boolToString"></i>
    </td>
    <td>
      <i :class="ink.waterProof | setCssClasses" :title="ink.waterProof | capitalize | boolToString"></i>
    </td>
    <td>
      <i :class="ink.uvGlow | setCssClasses" :title="ink.uvGlow | capitalize | boolToString"></i>
    </td>
    <td>
      <i :class="ink.lubricated | setCssClasses" :title="ink.lubricated | capitalize | boolToString"></i>
    </td>
    <td>
      <i :class="ink.freezeResistant | setCssClasses" :title="ink.freezeResistant | capitalize | boolToString"></i>
    </td>
    <td class="text-left">{{ ink.notes }}</td>
  </tr>
</template>


<script>
export default {
  name: 'ink-row',
  props: ['ink'],
  data () {
    return {}
  },

  filters: {
    arrayToString: (arr) => {
      return arr.map(word => {
        return this.default.filters.capitalize(word)
      }).join(', ')
    },
    boolToString: function (word) {
      if (word.toLowerCase() === 'true') {
        return 'Yes'
      } else if (word.toLowerCase() === 'false') {
        return 'No'
      } else {
        return word
      }
    },
    capitalize: function (word) {
      const wordStr = word.toString()
      return wordStr && wordStr.length > 0 ? `${wordStr.charAt(0).toUpperCase()}${wordStr.slice(1)}` : wordStr
    },
    setCssClasses: function (inkProp) {
      if (inkProp === 'partial') {
        return 'icon-contrast text-info'
      }

      return inkProp ? 'icon-checkmark text-success' : 'icon-cross text-danger'
    }
  }
}
</script>


<style scoped>
tr td { font-size: 0.8rem; }
</style>