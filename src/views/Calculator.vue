<template>
  <div class="col-4 border border-primary p-2">

    <div class="border border-primary mb-2 fs-3" style="height:80px">
      {{this.formula}}
    </div>
    <b-container class="border border-primary">
      <b-row cols="3">
        <!-- left 3cols: nums,ac, backspace -->
        <b-col class="col-8">
          <b-row cols="3">

            <b-col class="col-8 p-1">
              <b-button squared variant="primary" class="col-12 fs-3"
                        @click = clear()>
                AC
              </b-button>
            </b-col>

            <b-col class="col-4 p-1">
              <b-button squared variant="outline-primary" class="col-12 fs-3"
                        @click = backspace()>
                ←
              </b-button>
            </b-col>

            <b-col class="col-4 p-1" v-for="item in nums">
              <b-button squared variant="outline-primary" class="col-12 fs-3"
                        @click = append(item)>
                {{item}}
              </b-button>
            </b-col>

            <b-col class="col-8 p-1">
              <b-button squared variant="outline-primary" class="col-12 fs-3"
                        @click = append(item)>
                0
              </b-button>
            </b-col>

          </b-row>
        </b-col>

        <!-- right col, operators -->
        <b-col class="col-4">
          <b-row cols="1">
            <b-col class="col-12 px-1 py-1" v-for="item in operators">
              <b-button squared variant="info" class="col-12 fs-3"
                        @click =evalOrAppend(item) >
                {{item}}
              </b-button>
            </b-col>
          </b-row>
        </b-col>

      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formula: ' ',
      nums: [7,8,9,4,5,6,1,2,3,"."],
      operators:["÷","x","+","-","="]
    }
  },  methods: {
    evalOrAppend(value){
      if (value == "=") this.evaluate();
      else this.append(value);
    },
    /*
     * FUNCTION: evaluate()
     * PARAMETERS: none
     * FUNCTIONALITY: evaluate() was already written by instructors.
     */
    evaluate() {
      this.enterPressed = true
      try {
        /* WARNING! Never use eval in production code. */
        // eslint-disable-next-line no-eval
        let result = eval(this.formula)
        this.formulaAlert = false
        this.formula = result
      } catch (exception) {
        this.formulaAlert = true
      }
    },

    /*
     * FUNCTION: append()
     * PARAMETERS: value: Value to be appended to end of string.
     * FUNCTIONALITY: append() first checks to see if this.formula has been set.
     * If not, then it just replaces the value. If it has been set, it adds the
     * user input string (the button pressed) to the end of this.formula.
     */
    append(value) {
      if(this.formula ==null) this.formula = value;
      this.formula+= value;
    },

    /*
     * FUNCTION: backspace()
     * PARAMETERS: none
     * FUNCTIONALITY: backspace() uses slice() to cut the last character off from
     * the string. It uses toString() to ensure that this.formula is a string
     * (otherwise this function would not work when deleting the last character
     * from a result).
     */
    backspace() {
      if(this.formula.length<1) return;
      this.formula=this.formula.slice(0,this.formula.length-1);
    },

    /*
     * FUNCTION: clear()
     * PARAMETERS: none
     * FUNCTIONALITY: clear() used to set the formula to initial state
     */
    clear(){
      this.formula="";
    }
  }
}
</script>
