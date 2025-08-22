<script lang="ts" setup>
import { VueCompareImage } from 'vue3-compare-image';

const inputImagePath = './image_inner/ours2.png';
const outputImagePath = './image_inner/gt2.png';
const cfarImagePath = './image_inner/cfar2.png';
const rpdnetImagePath = './image_inner/rpdnet2.png';

</script>

<template>
  <div>

    
    <el-divider />
    <h1>PCE Comparison</h1>
    <el-row justify="center">
      <h2 class="section-title">SDDiff</h2>
    </el-row>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <el-row style="margin-top: 20px;" >
                <VueCompareImage 
                    :left-image="inputImagePath" 
                    :right-image="outputImagePath"
                    :hover="true"
                />
            </el-row>
        </el-col>
    </el-row>

    <el-row justify="center">
      <h2 class="section-title">RPDNet</h2>
    </el-row>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <el-row style="margin-top: 20px;" >
                <VueCompareImage 
                    :left-image="rpdnetImagePath" 
                    :right-image="outputImagePath"
                    :hover="true"
                />
            </el-row>
        </el-col>
    </el-row>

    <el-row justify="center">
      <h2 class="section-title">CFAR</h2>
    </el-row>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <el-row style="margin-top: 20px;" >
                <VueCompareImage 
                    :left-image="cfarImagePath" 
                    :right-image="outputImagePath"
                    :hover="true"
                />
            </el-row>
        </el-col>
    </el-row>

  </div>
</template>

<style scoped>

</style>
