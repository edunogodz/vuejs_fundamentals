<template>
  <div>
    <div class="top-row">
      <div class="top part">
        <img v-bind:src="availableParts.heads[selectedHeadIndex].src" title="head" />
        <button v-on:click="selectPreviousHead()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextHead()" class="next-selector">&#9658;</button>
      </div>
    </div>
    <div class="middle-row">
      <div class="left part">
        <img v-bind:src="availableParts.arms[SelectedLeftArmIndex].src" title="left arm" />
        <button v-on:click="selectPreviousLeftArm()" class="prev-selector">&#9650;</button>
        <button v-on:click="selectNextLeftArm()" class="next-selector">&#9660;</button>
      </div>
      <div class="center part">
        <img v-bind:src="availableParts.torsos[SelectedTorsoIndex].src" title="left arm" />
        <button v-on:click="selectPreviousTorso()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextTorso()" class="next-selector">&#9658;</button>
      </div>
      <div class="right part">
        <img v-bind:src="availableParts.arms[SelectedRightArmIndex].src" title="left arm" />
        <button v-on:click="selectPreviousRightArm()" class="prev-selector">&#9650;</button>
        <button v-on:click="selectNextRightArm()" class="next-selector">&#9660;</button>
      </div>
    </div>
    <div class="bottom-row">
      <div class="bottom part">
        <img v-bind:src="availableParts.bases[SelectedBaseIndex].src" title="left arm" />
        <button v-on:click="selectPreviousBase()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextBase()" class="next-selector">&#9658;</button>
      </div>
    </div>
  </div>
</template>

<script>
import availableParts from '../data/parts';

function getPreviousValidIndex(index, length) {
  const deprecatedIndex = index - 1;
  return deprecatedIndex < 0 ? length - 1 : deprecatedIndex;
}

function getNextValidIndex(index, length) {
  const imcrementedIndex = index - 1;
  return imcrementedIndex < 0 ? length - 1 : imcrementedIndex;
}

export default {
  name: 'RobotBuilder',
  data() {
    return {
      availableParts,
      selectedHeadIndex: 0,
      SelectedLeftArmIndex: 0,
      SelectedTorsoIndex: 0,
      SelectedRightArmIndex: 0,
      SelectedBaseIndex: 0,
    };
  },
  methods: {
    selectNextHead() {
      this.selectedHeadIndex = getNextValidIndex(
        this.selectedHeadIndex, availableParts.heads.length,
      );
    },
    selectPreviousHead() {
      this.selectedHeadIndex = getPreviousValidIndex(
        this.selectedHeadIndex, availableParts.heads.length,
      );
    },
    selectNextLeftArm() {
      this.SelectedLeftArmIndex = getNextValidIndex(
        this.SelectedLeftArmIndex, availableParts.arms.length,
      );
    },
    selectPreviousLeftArm() {
      this.SelectedLeftArmIndex = getPreviousValidIndex(
        this.SelectedLeftArmIndex, availableParts.arms.length,
      );
    },
    selectNextTorso() {
      this.SelectedTorsoIndex = getNextValidIndex(
        this.SelectedTorsoIndex, availableParts.torsos.length,
      );
    },
    selectPreviousTorso() {
      this.SelectedTorsoIndex = getPreviousValidIndex(
        this.SelectedTorsoIndex, availableParts.torsos.length,
      );
    },
    selectNextRightArm() {
      this.SelectedRightArmIndex = getNextValidIndex(
        this.SelectedRightArmIndex, availableParts.arms.length,
      );
    },
    selectPreviousRightArm() {
      this.SelectedRightArmIndex = getPreviousValidIndex(
        this.SelectedRightArmIndex, availableParts.arms.length,
      );
    },
    selectNextBase() {
      this.SelectedBaseIndex = getNextValidIndex(
        this.SelectedBaseIndex, availableParts.bases.length,
      );
    },
    selectPreviousBase() {
      this.SelectedBaseIndex = getPreviousValidIndex(
        this.SelectedBaseIndex, availableParts.bases.length,
      );
    },
  },
};
</script>

<style>
.part {
  position: relative;
  width: 165px;
  height: 165px;
  border: 3px solid #aaa;
}
.part img {
  width: 165px;
}
.top-row {
  display: flex;
  justify-content: space-around;
}
.middle-row {
  display: flex;
  justify-content: center;
}
.bottom-row {
  display: flex;
  justify-content: space-around;
  border-top: none;
}
.head {
  border-bottom: none;
}
.left {
  border-right: none;
}
.right {
  border-left: none;
}
.left img {
  transform: rotate(-90deg);
}
.right img {
  transform: rotate(90deg);
}
.bottom {
  border-top: none;
}
.prev-selector {
  position: absolute;
  z-index: 1;
  top: -3px;
  left: -28px;
  width: 25px;
  height: 171px;
}
.next-selector {
  position: absolute;
  z-index: 1;
  top: -3px;
  right: -28px;
  width: 25px;
  height: 171px;
}
.center .prev-selector,
.center .next-selector {
  opacity: 0.8;
}
.left .prev-selector {
  top: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.left .next-selector {
  top: auto;
  bottom: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.right .prev-selector {
  top: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  top: auto;
  bottom: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  right: -3px;
}
</style>
