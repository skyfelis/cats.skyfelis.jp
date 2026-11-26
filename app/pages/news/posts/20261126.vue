<template>
  <div class="space-y-6">
    <p>いつも配信や動画を見てくださって、ありがとうございます。汐猫みおは、活動名を「深瀬みおり（Fukase Miori）」に変更しました。</p>
    <p>改名に合わせて、公式サイトもリニューアルしました。目印は、天秤と本を抱えた猫のロゴです。<NuxtLink to="/#profile" class="text-miori-blue underline">プロフィール</NuxtLink>では新しいジャージ姿を、<NuxtLink to="/#model-spec" class="text-miori-blue underline">モデル紹介</NuxtLink>では髪の差し色やしっぽまで、三面図でご覧いただけます。</p>
    <p>観測者のみなさんへ。新しいファンマークは「🟥🟦🐈️」です。配信の実況や感想は <strong>#みおり観測中</strong>、ファンアートは <strong>#深瀬画廊</strong> で投稿してもらえたらうれしいです。どちらのタグも<NuxtLink to="/#fankit" class="text-miori-blue underline">ファンキット</NuxtLink>から探せます。</p>
    <p>これからも、情報学の話やゲームを一緒に楽しんでいけたらと思います。次の配信でお会いしましょう！</p>
    <p>深瀬みおり</p>
  </div>
</template>

<script setup lang="ts">
definePageMeta({
  layout: "news-detail",
  title: "「深瀬みおり」への改名と公式サイトリニューアルのお知らせ",
  year: "2026",
  date: "11.26",
  sortKey: "20261126",
  thumbnail: "/ogp-miori.jpg",
  category: "お知らせ",
});

const title = "「深瀬みおり」への改名と公式サイトリニューアルのお知らせ | 深瀬みおり Official Site";
const description = "汐猫みおは深瀬みおりに改名しました。新しいロゴと立ち絵、配信・ファンアートの公式ハッシュタグをご紹介します。";
useSeoMeta({ title, description, ogTitle: title, ogDescription: description, ogType: "article" });
</script>
