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
                <div><label>How many paragraphs: <br /><input type="number" v-model="howManyParagraphs" /> paragraphs</label><br /><br /></div>
            </div>
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
          'Dynaflow\n'
      }
    },
   computed: {
      jabberOutput: function() {
        const jabber = new Jabber(this.themeWords.split('\n'), this.themeWordFrequency)
        let output = ''
        for (let i=0; i < Number(this.howManyParagraphs); i++) {
          output += `<p>${jabber.createParagraph(Number(this.paragraphLength))}</p>`
        }
        return output
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
