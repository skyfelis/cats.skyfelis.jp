<template>
  <div class="space-y-6">
    <p>いつも深瀬みおりを応援してくださって、ありがとうございます。改名に合わせて、<NuxtLink to="/guideline" class="text-miori-blue underline">二次創作ガイドライン</NuxtLink>を改定しました。</p>
    <p>改定後のガイドラインは、<strong>2026年12月10日</strong>から適用します。それまでは改定前のルールのままなので、いま公開している作品や準備中の作品は、適用日までに見直していただければ大丈夫です。</p>

    <h2 class="text-lg font-black text-miori-navy pt-2">新しいハッシュタグ</h2>
    <ul class="list-disc pl-5 space-y-1">
      <li><strong>#みおりAI画廊</strong>：AI生成作品用です。AI生成作品には #深瀬画廊 を使わず、こちらを使ってください。</li>
      <li><strong>#観測禁止区域</strong>：成人向け作品用です。成人向け作品には、公式タグや「深瀬みおり」の名前を付けず、こちらを使ってください。</li>
    </ul>
    <p>手描きのファンアートは #深瀬画廊、配信の感想は #みおり観測中 のままです。</p>

    <h2 class="text-lg font-black text-miori-navy pt-2">主な変更点</h2>
    <ul class="list-disc pl-5 space-y-1">
      <li><strong>AI生成作品：</strong>趣味の範囲であれば、同人誌やグッズとして頒布できるようになりました。頒布物にも、AIを使ったことを明記してください。</li>
      <li><strong>成人向け作品：</strong>タイトルや説明文など、検索結果に出る場所に「深瀬みおり」の名前や愛称を書かないでください。</li>
      <li><strong>切り抜き動画：</strong>配信のサムネイルや公式ロゴを、切り抜きのサムネイルにそのまま使うことはできません。</li>
      <li><strong>応援広告：</strong>使う作品は、作者の許可を得た二次創作物に限ります。</li>
      <li><strong>有償依頼：</strong>Skebなどで、イラストレーターさんにファンアートを有償で依頼できることを明記しました。</li>
      <li><strong>広告・宣伝での利用：</strong>ご自身のお店や商品などの宣伝に使うことはできません（応援広告を除きます）。</li>
      <li><strong>ガイドラインの位置づけ：</strong>民法上の定型約款として位置づけ、今後ガイドラインを変更するときの手続きを定めました。みなさんに不利になる変更は、適用日より前に、このサイトでお知らせします。</li>
    </ul>

    <p>このほかにも、条文の整理や表現の見直しをしています。詳しくは<NuxtLink to="/guideline" class="text-miori-blue underline">二次創作ガイドライン</NuxtLink>の本文をご確認ください。判断に迷うときは、<NuxtLink to="/contact" class="text-miori-blue underline">お問い合わせフォーム</NuxtLink>から気軽にご相談ください。</p>
    <p>これからも、みなさんの作品を楽しみにしています！</p>
    <p>深瀬みおり</p>
  </div>
</template>

<script setup lang="ts">
definePageMeta({
  layout: "news-detail",
  title: "二次創作ガイドライン改定のお知らせ（2026年12月10日適用）",
  year: "2026",
  date: "11.26",
  sortKey: "20261126_2",
  thumbnail: "/ogp-miori.jpg",
  category: "お知らせ",
});

const title = "二次創作ガイドライン改定のお知らせ | 深瀬みおり Official Site";
const description = "二次創作ガイドラインを改定し、2026年12月10日から適用します。AI生成作品用の #みおりAI画廊、成人向け作品用の #観測禁止区域 の新設など、主な変更点をお知らせします。";
useSeoMeta({ title, description, ogTitle: title, ogDescription: description, ogType: "article" });
</script>
