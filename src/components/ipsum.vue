<template>
    <form>
        <div class="container">
            <div class="item">
                <label>Lorem Ipsum Keywords: <br />
                    <textarea v-model="themeWords" placeholder="Enter keywords here."></textarea></label>
            </div>
            <div class="item">
                <div><label>Frequency of keywords: <br />Every <input id="themeWordFrequency" type="number" v-model="themeWordFrequency" /> words</label><br /><br /></div>
                <div><label>Paragraph size: <br /><input type="number" v-model="paragraphLength" /> words</label><br /><br /></div>
                <div><label>How many paragraphs: <br /><input type="number" v-model="howManyParagraphs" /> paragraphs</label></div>
            </div>
        </div>
        <br />
        <div>
            <button type="button"
                v-clipboard:copy="generatedValue"
                v-clipboard:success="onCopy"
                v-clipboard:error="onError">Copy!</button>
        </div>
        <div v-html="jabberOutput"></div>
    </form>
</template>

<script>
  import Jabber from 'jabber'
  const  lipsumator = require('lipsumator')
  export default {
    name: "ipsum",
    data: function () {
      return {
        howManyParagraphs: 5,
        paragraphLength: 50,
        themeWordFrequency: 2,
        themeWords: 'Torque-vectoring\n' +
          'NACA duct\n' +
          'Elon Musk\n' +
          'Brown wagon\n' +
          'Delta Integrale\n' +
          'Faszination\n' +
          'Torq Thrust\n' +
          'Pilot Sport\n' +
          'VTEC kicked in, yo\n' +
          'PDK\n' +
          'Does it have CarPlay?\n' +
          'Shooting brake\n' +
          'No reserve\n' +
          'Dynamism\n' +
          'Agnelli\n' +
          'Coffin-spoke\n' +
          'ZF 8-speed\n' +
          'Pop-up headlights\n' +
          'Borrani\n' +
          'Nürburgring\n' +
          'MR dampers\n' +
          'Nardi\n' +
          'Iskenderian\n' +
          'George Barris\n' +
          'Side louvers\n' +
          'Knock-offs\n' +
          'Bi-xenon\n' +
          'Super HICAS\n' +
          'iDrive\n' +
          'John Z. Delorean\n' +
          'KwH\n' +
          'Minilites\n' +
          'Dynaflow\n',
        generatedValue: ''
      }
    },
   computed: {
      jabberOutput: function() {
        this.generatedValue = this.generateValue()
        return `<p>${this.generatedValue.split('\n\n').join('</p><p>')}</p>`
      }
    },
    methods: {
      generateValue: function() {
        const jabber = new Jabber(this.themeWords.split('\n'), this.themeWordFrequency)
        let outputArray = []
        for (let i=0; i < Number(this.howManyParagraphs); i++) {
          outputArray.push(jabber.createParagraph(Number(this.paragraphLength)))
        }
        return outputArray.join('\n\n')
      },
      onCopy: function (e) {
        alert('Copied!')
      },
      onError: function (e) {
        alert('Failed to copy texts')
      }
    }
  }
</script>

<style scoped>
    textarea {
        width: calc(100% - 30px);
        height: 200px;
    }

    #themeWordFrequency {
        width: 2rem;
    }

    .container {
        display: flex;
        flex-direction: row;
    }
    .item {
        width: 50%;
    }
</style>
