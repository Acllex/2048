<template>
  <div class="bodyer">
    <button type="text" v-on:keydown="active">
      <div class="big-box">
        <div
          class="box"
          v-for="(item, index) in boxs"
          :key="index"
          v-getclass="datas[index]"
        >{{datas[index]==0?'':datas[index]}}</div>
      </div>
    </button>
  </div>
</template>

<style scoped>
.bodyer {
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  margin: auto;
  background-color: #faf8ef;
}
.big-box {
  width: 500px;
  height: 500px;
  background-color: #bbada0;
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  margin: auto;
  padding: 14px;
  box-sizing: border-box;
  border-radius: 10px;
  display: flex;
  flex-wrap: wrap;
}
.box {
  width: 106px;
  height: 106px;
  background-color: rgba(238, 228, 218, 0.35);
  border-radius: 6px;
  margin: 4px 6px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 60px;
  font-weight: 700;
}
.box2 {
  background-color: #eee4da;

  color: white;
}
.box4 {
  background-color: #ede0c8;

  color: white;
}
.box8 {
  background-color: #f2b179;

  color: white;
}
.box16 {
  background-color: #f59563;
  color: white;
}
.box32 {
  background-color: #f67c5f;
  color: white;
}
.box64 {
  background-color: #f65e3b;
  color: white;
}
button {
  padding: 0;
  border-width: 0;
}
</style>

<script>
export default {
  data() {
    return {
      boxs: 16,
      datas: []
    };
  },
  directives: {
    getclass(el, b) {
      el.classList.remove(el.classList[1]);
      if (b.value != 0) {
        el.classList.add("box" + b.value);
      }
    }
  },
  methods: {
    setbox() {
      if(!this.datas.length){
        for (let index = 0; index < this.boxs; index++) {
          this.datas.push(0);
        }
      }
      let index = Math.floor(Math.random() * 16);
      while (this.datas[index] != 0) {
        index = Math.floor(Math.random() * 16);
      }
      let num = Math.floor(Math.random() * 3 + 2);
      while (num == 3) {
        num = Math.floor(Math.random() * 3 + 2);
      }
      this.$set(this.datas, index, num);
    },
    active() {
      this.data = [...this.datas];
      if (!this.datas) {
        return;
      }
      if (event.keyCode == 38) {
        this.datas.forEach((element, index) => {
          let x = index;
          while (x >= 4) {
            if (this.datas[x - 4] != 0 && this.datas[x - 4] != element) {
              break;
            }
            this.$set(this.datas, x, 0);
            if (element == this.datas[x - 4]) {
              this.$set(this.datas, x - 4, element + this.datas[x - 4]);
            } else {
              this.$set(this.datas, x - 4, element);
            }
            x = x - 4;
          }
        });
      }
      if (event.keyCode == 40) {
        for (let i = this.datas.length; i >= 0; i--) {
          let x = i;
          while (x <= 11) {
            if (this.datas[x + 4] != 0 && this.datas[x + 4] != this.datas[x]) {
              break;
            }
            if (this.datas[x] == this.datas[x + 4]) {
              this.$set(this.datas, x + 4, this.datas[x] + this.datas[x + 4]);
              this.$set(this.datas, x, 0);
              break;
            } else {
              this.$set(this.datas, x + 4, this.datas[x]);
              this.$set(this.datas, x, 0);
            }
            x = x + 4;
          }
        }
      }
      if (event.keyCode == 37) {
        this.datas.forEach((element, index) => {
          let x = index;
          if (x > 0 && x < 4) {
            while (x > 0) {
              if (this.datas[x - 1] != 0 && this.datas[x - 1] != element) {
                break;
              }
              this.$set(this.datas, x, 0);
              if (element == this.datas[x - 1]) {
                this.$set(this.datas, x - 1, element + this.datas[x - 1]);
              } else {
                this.$set(this.datas, x - 1, element);
              }
              x = x - 1;
            }
          }
          if (x > 4 && x < 8) {
            while (x > 4) {
              if (this.datas[x - 1] != 0 && this.datas[x - 1] != element) {
                break;
              }
              this.$set(this.datas, x, 0);
              if (element == this.datas[x - 1]) {
                this.$set(this.datas, x - 1, element + this.datas[x - 1]);
              } else {
                this.$set(this.datas, x - 1, element);
              }
              x = x - 1;
            }
          }
          if (x > 8 && x < 12) {
            while (x > 8) {
              if (this.datas[x - 1] != 0 && this.datas[x - 1] != element) {
                break;
              }
              this.$set(this.datas, x, 0);
              if (element == this.datas[x - 1]) {
                this.$set(this.datas, x - 1, element + this.datas[x - 1]);
              } else {
                this.$set(this.datas, x - 1, element);
              }
              x = x - 1;
            }
          }
          if (x > 12 && x < 16) {
            while (x > 12) {
              if (this.datas[x - 1] != 0 && this.datas[x - 1] != element) {
                break;
              }
              this.$set(this.datas, x, 0);
              if (element == this.datas[x - 1]) {
                this.$set(this.datas, x - 1, element + this.datas[x - 1]);
              } else {
                this.$set(this.datas, x - 1, element);
              }
              x = x - 1;
            }
          }
        });
      }
      if (event.keyCode == 39) {
        for (let i = this.datas.length; i >= 0; i--) {
          const element = this.datas[i];
          let x = i;
          if (x >= 0 && x < 4) {
            while (x < 3) {
              if (this.datas[x + 1] != 0 && this.datas[x + 1] != element) {
                break;
              }
              this.$set(this.datas, x, 0);
              if (element == this.datas[x + 1]) {
                this.$set(this.datas, x + 1, element + this.datas[x + 1]);
              } else {
                this.$set(this.datas, x + 1, element);
              }
              x = x + 1;
            }
          }
          if (x >= 4 && x < 8) {
            while (x < 7) {
              if (this.datas[x + 1] != 0 && this.datas[x + 1] != element) {
                break;
              }
              this.$set(this.datas, x, 0);
              if (element == this.datas[x + 1]) {
                this.$set(this.datas, x + 1, element + this.datas[x + 1]);
              } else {
                this.$set(this.datas, x + 1, element);
              }
              x = x + 1;
            }
          }
          if (x >= 8 && x < 11) {
            while (x < 11) {
              if (this.datas[x + 1] != 0 && this.datas[x + 1] != element) {
                break;
              }
              this.$set(this.datas, x, 0);
              if (element == this.datas[x + 1]) {
                this.$set(this.datas, x + 1, element + this.datas[x + 1]);
              } else {
                this.$set(this.datas, x + 1, element);
              }
              x = x + 1;
            }
          }
          if (x >= 12 && x < 16) {
            while (x < 15) {
              if (this.datas[x + 1] != 0 && this.datas[x + 1] != element) {
                break;
              }
              this.$set(this.datas, x, 0);
              if (element == this.datas[x + 1]) {
                this.$set(this.datas, x + 1, element + this.datas[x + 1]);
              } else {
                this.$set(this.datas, x + 1, element);
              }
              x = x + 1;
            }
          }
        }
      }
      let res = this.datas.every((ele, i) => ele == this.data[i]);
      if (res) {
        return;
      } else {
        this.setbox();
      }
    }
  },
  created() {
    this.setbox();
  }
};
</script>