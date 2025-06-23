<script setup lang="ts">
import demo from './demo.json'
import {transliterate as tTransliterate} from "transliteration";
import transliterate from "@sindresorhus/transliterate";
import pinyin from "pinyin";
</script>

<template>
  <div>
    <template v-for="item in demo" :key="item.code">
      <div>
        <h2>{{ item.name }}</h2>
        <template v-for="name in item.names" :key="name">
          <div>
            {{ name }} to <b>`{{ tTransliterate(name) }}`</b>
            ~ sindresorhus: <b>`{{ transliterate(name) }}`</b>
            <template v-if="item.code === 'zh'">
              ~ pinyin: <b>{{ pinyin(name, {style: "PASSPORT"}).join(' ') }}</b>
            </template>
          </div>
        </template>
      </div>
    </template>
  </div>
</template>

<style></style>
