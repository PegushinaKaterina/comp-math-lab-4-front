<template>
    <div class="plots">
        <div>
            Линейная функция:<br>
            <div ref="plotRef"></div>
            Функция:
            {{ fnString }}<br>
            Стандартное отклонение:
            {{std}}
            <br>
            {{ message }}
        </div>
        <div>

            Квадратичная функция:<br>
            <div ref="plotRef2"></div>
            Функция:
            {{ fnString2 }}<br>
            Стандартное отклонение:
            {{std2}}
            <br>
            {{ message2 }}
        </div>
        <div>

            Кубическая функция:<br>
            <div ref="plotRef3"></div>
            Функция:
            {{ fnString3 }}<br>
            Стандартное отклонение:
            {{std3}}
            <br>
            {{ message3 }}
        </div>
    </div>
    <br><br>
    <div class="plots">
        <div>

            Экспоненциальная функция:<br>
            <div ref="plotRef4"></div>
            Функция:
            {{ fnString4 }}
            <br>
            Стандартное отклонение:
            {{std4}}
            <br>
            {{ message4 }}
        </div>
        <div>

            Логарифмическая функция:<br>
            <div ref="plotRef5"></div>
            Функция:
            {{ fnString5 }}
            <br>
            Стандартное отклонение:
            {{std5}}
            <br>
            {{ message5 }}
        </div>
        <div>
            Степенная функция:<br>
            <div ref="plotRef6"></div>

            Функция:
            {{ fnString6 }}
            <br>
            Стандартное отклонение:
            {{std6}}
            <br>
            {{ message6 }}
        </div>
    </div>


</template>

<script>
import functionPlot from "function-plot";

export default {
    data() {
        return {
            message: "",
            message2: "",
            message3: "",
            message4: "",
            message5: "",
            message6: "",
            fnString: "",
            fnString2: "",
            fnString3: "",
            fnString4: "",
            fnString5: "",
            fnString6: "",
            std: "",
            std2: "",
            std3: "",
            std4: "",
            std5: "",
            std6: "",
        };
    },
  props: {
    fnProp: {
      type: Array,
    },
    pointsProp: {
        type: Array,
    },
    leftProp: {
      type: Number,
    },
    rightProp: {
      type: Number,
    },
    bottomProp: {
        type: Number,
    },
    topProp: {
        type: Number,
    }

  },
  watch: {
    fnProp: function () {
      this.updatePlot(this.fnProp, this.leftProp, this.rightProp, this.bottomProp, this.topProp, this.pointsProp)
        this.message = this.fnProp[0].message;
        this.message2 = this.fnProp[1].message;
        this.message3 = this.fnProp[2].message;
        this.message4 = this.fnProp[3].message;
        this.message5 = this.fnProp[4].message;
        this.message6 = this.fnProp[5].message;
        this.fnString = this.fnProp[0].fnText;
        this.fnString2 = this.fnProp[1].fnText;
        this.fnString3 = this.fnProp[2].fnText;
        this.fnString4 = this.fnProp[3].fnText;
        this.fnString5 = this.fnProp[4].fnText;
        this.fnString6 = this.fnProp[5].fnText;
        this.std = this.fnProp[0].standardDeviation;
        this.std2 = this.fnProp[1].standardDeviation;
        this.std3 = this.fnProp[2].standardDeviation;
        this.std4 = this.fnProp[3].standardDeviation;
        this.std5 = this.fnProp[4].standardDeviation;
        this.std6 = this.fnProp[5].standardDeviation;
    },
  },
  methods: {
    updatePlot(fn, left, right, bottom, top, pointsProp) {
      console.log(this.$refs.plotRef)
      functionPlot({
        target: this.$refs.plotRef,
        width: 350,
        height: 350,
        grid: true,
        xAxis: { domain: [left, right] },
        yAxis: { domain: [bottom, top] },
        data: [
          {
            fn: fn[0].fn,
          },
          {
            points: pointsProp,
            fnType: 'points',
            graphType: 'scatter'
          }
        ]

      });
      functionPlot({
        target: this.$refs.plotRef2,
        width: 350,
        height: 350,
        grid: true,
        xAxis: { domain: [left, right] },
        yAxis: { domain: [bottom, top] },
        data: [
            {
                fn: fn[1].fn,
            },
            {
                points: pointsProp,
                fnType: 'points',
                graphType: 'scatter'
            }
        ]
      });
      functionPlot({
          target: this.$refs.plotRef3,
          width: 350,
          height: 350,
          grid: true,
          xAxis: { domain: [left, right] },
          yAxis: { domain: [bottom, top] },
          data: [
              {
                  fn: fn[2].fn,
              },
              {
                  points: pointsProp,
                  fnType: 'points',
                  graphType: 'scatter'
              }
          ]
      });
      functionPlot({
          target: this.$refs.plotRef4,
          width: 350,
          height: 350,
          grid: true,
          xAxis: { domain: [left, right] },
          yAxis: { domain: [bottom, top] },
          data: [
              {
                  fn: fn[3].fn,
              },
              {
                  points: pointsProp,
                  fnType: 'points',
                  graphType: 'scatter'
              }
          ]
      });
      functionPlot({
          target: this.$refs.plotRef5,
          width: 350,
          height: 350,
          grid: true,
          xAxis: { domain: [left, right] },
          yAxis: { domain: [bottom, top] },
          data: [
              {
                  fn: fn[4].fn,
              },
              {
                  points: pointsProp,
                  fnType: 'points',
                  graphType: 'scatter'
              }
          ]
      });
      functionPlot({
          target: this.$refs.plotRef6,
          width: 350,
          height: 350,
          grid: true,
          xAxis: { domain: [left, right] },
          yAxis: { domain: [bottom, top] },
          data: [
              {
                  fn: fn[5].fn,
              },
              {
                  points: pointsProp,
                  fnType: 'points',
                  graphType: 'scatter'
              }
          ]
      });
    }
  }
}

</script>

<style scoped>
.plots {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
}
</style>