<template>
  <div class="bg-white min-h-screen pt-44 pb-32 px-6 text-slate-800 animate-fade-in font-sans antialiased">
    <div class="max-w-[1440px] mx-auto w-full flex flex-col items-center">
      <div class="w-full max-w-4xl">
        <div class="text-center mb-8 select-none">
          <span class="text-xs font-mono font-bold tracking-[0.2em] text-slate-400 block">// GUIDELINE_MODULE:
            loaded</span>
        </div>

        <h1 class="text-2xl md:text-3xl font-sans font-black text-miori-navy leading-relaxed pb-3 text-center">
          二次創作ガイドライン
        </h1>
        <p class="text-center text-sm font-bold text-slate-500 tracking-wider mb-4 select-none">
          深瀬みおりの創作活動を楽しく応援していただくための共通ルール
        </p>
        <p class="text-center text-xs text-slate-500 mb-16">
          制定日：{{ enactedAt }}　／　最終改定日：{{ revisedAt }}（{{ effectiveAt }}施行）
        </p>

        <div
          class="text-[15px] md:text-base text-slate-700 leading-loose space-y-16 border-t border-slate-100 pt-10">
          <!-- ざっくりまとめ・目次 -->
          <nav aria-labelledby="guide-index" class="rounded-2xl border border-slate-200 bg-white p-5 sm:p-8">
            <h2 id="guide-index" class="text-xl font-bold text-miori-navy">
              ざっくりまとめ
            </h2>
            <ul class="mt-3 list-disc pl-5 space-y-1">
              <li v-for="(line, i) in summary" :key="i">{{ line }}</li>
            </ul>
            <h3 class="mt-6 font-bold text-miori-navy">作りたいものから探す</h3>
            <ul class="mt-3 grid gap-2 sm:grid-cols-2">
              <li v-for="item in guideLinks" :key="item.id">
                <a :href="'#' + item.id" class="text-miori-blue underline underline-offset-4">{{ item.label }}</a>
              </li>
            </ul>
          </nav>

          <!-- 前文 -->
          <section class="space-y-4">
            <h2 class="text-lg font-black text-miori-navy flex items-center gap-3 pl-0">
              <span class="w-1.5 h-6 bg-miori-blue rounded-full block animate-pulse"></span>
              前文（目的）
            </h2>
            <div class="pl-5 space-y-4">
              <p>
                本ガイドラインは、深瀬みおり（以下「当方」といいます。）のVTuberコンテンツをより多くの方に知っていただき、本コンテンツを利用した二次創作活動が活発に行われ、多種多様な作品が生まれることを奨励し、もって文化及び本コンテンツの発展に寄与することを目的として定めるものです。
              </p>
              <p>
                当方は、利用者による本コンテンツの利用が本ガイドラインに従ったものであり、かつ、法令及び公序良俗に反しない内容及び方法である限り、著作権その他の権利を行使しません。
              </p>
            </div>
          </section>

          <!-- 各条 -->
          <section v-for="(article, ai) in articles" :id="article.id" :key="ai" class="space-y-5 scroll-mt-32">
            <h2 class="text-lg font-black text-miori-navy flex items-center gap-2 border-b border-slate-100 pb-3 pl-0">
              <span class="text-miori-blue font-mono text-sm">#</span>
              第{{ ai + 1 }}条（{{ article.title }}）
            </h2>

            <div class="space-y-4">
              <p v-if="article.lead" class="pl-5" v-html="article.lead" />

              <div v-for="(item, ii) in article.items" :key="ii" class="flex items-start gap-2 pl-5">
                <span class="shrink-0 w-5 font-mono font-bold text-miori-blue">{{ article.lead ? letters[ii] : ii + 1
                  }}.</span>
                <div class="flex-1 space-y-3">
                  <div v-html="item.text" />
                  <div v-if="item.sub" class="space-y-2 text-slate-600 pt-1">
                    <div v-for="(sub, si) in item.sub" :key="si" class="flex items-start gap-2 pl-6">
                      <span class="shrink-0 w-4 font-mono font-bold text-slate-500">{{ letters[si] }}.</span>
                      <div class="flex-1" v-html="sub" />
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <aside v-if="article.example" class="guide-example">
              <h3>{{ article.example.title }}</h3>
              <p>{{ article.example.body }}</p>
            </aside>
          </section>

          <!-- 附則 -->
          <section id="supplementary" class="space-y-4 scroll-mt-32">
            <h2 class="text-lg font-black text-miori-navy flex items-center gap-2 border-b border-slate-100 pb-3 pl-0">
              附則
            </h2>
            <div class="pl-5 space-y-2">
              <p>本ガイドラインは、{{ enactedAt }}から施行します。</p>
              <p>{{ revisedAt }}改定の本ガイドラインは、{{ effectiveAt }}から施行します。</p>
            </div>
          </section>

          <!-- お問い合わせ -->
          <section id="contact" class="space-y-4 scroll-mt-32">
            <h2 class="text-lg font-black text-miori-navy">お問い合わせ</h2>
            <p>
              法人・団体による利用、スポンサー広告、営利が関わる利用など、本文から利用条件を判断できない場合は、<NuxtLink to="/contact"
                class="text-miori-blue underline">お問い合わせフォーム</NuxtLink>からご相談ください。次の情報を添えていただくと確認がスムーズです。
            </p>
            <ul class="list-disc pl-5 space-y-1">
              <li>お名前またはハンドルネーム、返信先</li>
              <li>使いたい素材や配信のURL</li>
              <li>作品やチャンネルのURL、公開先</li>
              <li>想定している利用内容、販売・収益化の予定の有無</li>
            </ul>
          </section>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
// 改定時はここを更新してください。
// 利用者に不利な変更を含む改定は、民法548条の4第3項により施行日（effectiveAt）より前に掲載・周知すること。
const enactedAt = "2026年5月27日";
const revisedAt = "2026年11月26日";
const effectiveAt = "2026年12月10日";

type Article = {
  id?: string;
  title: string;
  /** 柱書（号を列挙する条で使用。指定すると items は a. b. … で表示） */
  lead?: string;
  items: { text: string; sub?: string[] }[];
  example?: { title: string; body: string };
};

const letters = "abcdefghijklmnopqrstuvwxyz".split("");

// 条番号の参照。本文には ref("id") でトークンを埋め、配列確定後に「第N条」へ置換する
const ref = (id: string) => `[[${id}]]`;

// 強調用（本文は静的な定数なので v-html で描画）
const em = (s: string) => `<strong class="text-miori-navy font-black">${s}</strong>`;
const warn = (s: string) => `<strong class="text-red-500 font-black">${s}</strong>`;
const credit = (s: string) =>
  `<strong class="text-miori-navy underline decoration-miori-blue/50 font-black">${s}</strong>`;

const summary = [
  "本コンテンツを利用すると、このガイドライン（民法上の定型約款）に同意したものとみなされます。",
  "個人や同人サークルによる、趣味の範囲のファン活動は、事前連絡なしで楽しんでいただけます。",
  "作品には「原作：深瀬みおり」など、出所を明記してください。",
  "公式と誤解される表現、当方や第三者を傷つける表現、各サービスの規約違反はご遠慮ください。",
  "販売、切り抜きの収益化、応援広告、AI生成作品には、それぞれ個別の条件があります。",
  "本文から判断できないとき、特に営利が関わるときは、お問い合わせください。",
];

const articleDefs: Article[] = [
  {
    id: "scope",
    title: "適用範囲",
    items: [
      {
        text: "本ガイドラインの対象となるコンテンツ（以下「本コンテンツ」といいます。）は、次のとおりとします。",
        sub: [
          "深瀬みおりのキャラクター（名称、容姿、設定その他の要素を含みます。）",
          "当方が配信または投稿した動画、画像、音声、文章その他のコンテンツ",
          "その他、深瀬みおり名義で提供されるコンテンツ",
        ],
      },
      {
        text: "本ガイドラインに基づき利用できる本コンテンツは、当方が著作権その他の権利を有する範囲に限られます。第三者が権利を有する部分（ゲーム映像、BGM、ゲストやイラストレーターの作品等）については、当該権利者の定める条件に従ってください。",
      },
      {
        text: `本ガイドラインは、${em("個人および法人格を有しない同人サークル")}（以下「利用者」といいます。）に適用します。法人その他の団体が本コンテンツの利用を希望する場合は、別途当方までご連絡ください。`,
      },
    ],
  },
  {
    id: "agreement",
    title: "定型約款としての位置づけ及び合意",
    items: [
      {
        text: `本ガイドラインは、本コンテンツの利用に関する当方と利用者との間の契約（以下「本契約」といいます。）に適用される、${em("民法第548条の2第1項に定める定型約款")}です。`,
      },
      {
        text: "当方は、本ガイドラインを本契約の内容とすることを、本ページにおいてあらかじめ表示します。",
      },
      {
        text: `利用者は、本コンテンツを利用したときは、${em("本ガイドラインの各条項に合意したもの")}とみなされます。`,
      },
      {
        text: "当方は、本ガイドラインを本ページに常時掲載します。利用者は、いつでも本ページで本ガイドラインの内容を確認することができます。",
      },
    ],
  },
  {
    id: "definitions",
    title: "定義",
    lead: "本ガイドラインにおいて、次の各号に掲げる用語の意義は、当該各号に定めるところによります。",
    items: [
      { text: `${em("二次創作物")}：本コンテンツを基に利用者が創作したイラスト、漫画、小説、動画、音声作品、コスプレ、同人誌、グッズその他の作品` },
      { text: `${em("切り抜き動画")}：当方の配信または動画の一部を編集し、別の動画として投稿するもの` },
      { text: `${em("AI生成作品")}：画像生成AI、音声生成AIその他の生成AIを用いて作成した二次創作物` },
      { text: `${em("営利目的")}：趣味の範囲を超えて、継続的・反復的に利益を得ることを主たる目的とすること` },
    ],
  },
  {
    id: "fan-art",
    title: "基本原則",
    items: [
      {
        text: `利用者は、${em("個人的かつ非営利の目的で")}、二次創作物を作成し、SNS、個人サイト、同人イベント等で公開または頒布することができます。ただし、${ref("fan-goods")}から${ref("fan-events")}まで及び${ref("permissions")}に定める場合は、各条の条件に従って有償での頒布や収益化を行うことができます。`,
      },
      { text: "二次創作物の作成・公開について、当方への事前確認は不要です。" },
      {
        text: `二次創作物を公開する場合は、${credit("「©深瀬みおり」")}、${credit("「原作：深瀬みおり」")}等、本コンテンツに由来することを明記してください。`,
      },
      {
        text: "当方は、本ガイドラインの範囲内で公開された二次創作物を、当方の活動の中で紹介することがあります。その際は、可能な範囲で作者に事前に連絡し、作者名を明記します。",
      },
    ],
    example: {
      title: "投稿文・奥付の記載例",
      body: "自分で描いたイラストを投稿する場合は、投稿文に「原作：深瀬みおり／イラスト：ご自身の名前」と書くと、原作と作品の作者が伝わります。ファンアート用のタグは #深瀬画廊、AI生成作品は #みおりAI画廊、配信の感想は #みおり観測中 です。タグを使うかどうかは自由ですが、AI生成作品に #深瀬画廊 は使えません。",
    },
  },
  {
    id: "prohibited",
    title: "禁止事項",
    lead: "目的を問わず、次の各号のいずれかに該当し、またはそのおそれのある利用を禁止します。",
    items: [
      { text: `本コンテンツをそのまま利用するもの、または単なる改変の域を出ない等、創作性に欠けるもの（${ref("clips")}に定める切り抜き動画を除きます。）` },
      { text: `当方になりすますもの、または${warn("「公式」「公認」「コラボ」等の表示")}により、当方の公式・公認の作品やアカウントであると誤認させるもの` },
      { text: "本コンテンツのイメージを著しく損なうもの" },
      { text: "当方または第三者の名誉・信用を傷つけ、誹謗中傷し、または差別を助長するもの" },
      { text: "第三者の著作権、肖像権、プライバシーその他の権利を侵害するもの" },
      { text: "特定の思想・信条、宗教または政治活動の宣伝を目的とするもの" },
      { text: `事業目的のもの、または商品、サービス、店舗等の広告・宣伝を目的とするもの（${ref("fan-events")}に定める応援広告を除きます。）` },
      { text: "反社会的勢力への利益供与その他これに関与するもの" },
      { text: "法令、公序良俗または投稿先サービスの利用規約に違反するもの" },
      { text: "その他、前各号に準ずるものとして当方が合理的に不適切と判断したもの" },
    ],
  },
  {
    id: "age-rating",
    title: "成人向け表現",
    items: [
      {
        text: `性的、グロテスクその他${em("ゾーニングが必要な内容")}を含む二次創作物について、当方は原則として禁止しません。`,
      },
      {
        text: "前項の二次創作物を公開する場合は、利用者の責任において、投稿先の年齢制限機能を利用する等、未成年者の目に触れないよう配慮してください。",
      },
      {
        text: `第1項の二次創作物をSNS等に投稿する場合は、専用タグ ${em("#観測禁止区域")} を使用できます。`,
      },
      {
        text: "第1項の二次創作物については、次の行為を禁止します。",
        sub: [
          "公式の立ち絵、配信画面その他の公式素材の流用（トレースを含みます。）",
          "当方の公式アカウントへのタグ付け、リプライまたはメンション",
          "公式タグ（#深瀬画廊、#みおりAI画廊、#みおり観測中 等）の使用、および一般公開のサムネイル・告知文への該当場面の掲載",
          "タイトル、説明文その他検索結果に表示される箇所への「深瀬みおり」の名称、愛称その他当方を検索できる語句の記載",
        ],
      },
      {
        text: `${warn("当方に対するセクシャルハラスメントを意図した表現")}は、内容を問わず禁止します。`,
      },
    ],
    example: {
      title: "サムネイルや告知にも配慮を",
      body: "投稿先の年齢制限機能を使い、一般公開のサムネイルや告知文には該当する場面を載せないようにしてください。#深瀬画廊、#みおりAI画廊 は全年齢向けの作品のみとし、成人向けの作品には #観測禁止区域 をお使いください。",
    },
  },
  {
    id: "fan-goods",
    title: "同人活動および頒布",
    items: [
      { text: "趣味の範囲内に限り、同人誌、画集、グッズ等の二次創作物を有償で頒布することができます。" },
      { text: "本コンテンツをそのまま複製して製造した物品は、二次創作物とは認めません。" },
      { text: "当方は、頒布の規模や態様から営利性・事業性が高いと判断した場合、頒布の中止を求めることがあります。" },
    ],
    example: {
      title: "アクリルキーホルダーを作る場合",
      body: `ご自身で描いた深瀬みおりのイラストを使い、個人の趣味の範囲で頒布できます。公式の立ち絵を切り抜いて印刷したものや、公式ロゴの色だけを変えて製品にしたものは対象外です。AI生成作品には${ref("ai-art")}も適用されます。`,
    },
  },
  {
    id: "clips",
    title: "切り抜き動画",
    items: [
      { text: "利用者は、本コンテンツの切り抜き動画を作成し、動画共有サービスやSNSに投稿することができます。" },
      { text: `切り抜き動画の概要欄等には、${em("元動画のタイトルおよびURL")}を必ず記載してください。` },
      { text: `収益化機能は利用できます。ただし、${warn("Content ID等の権利管理システムへの登録は禁止します。")}` },
      {
        text: "次の切り抜き動画は禁止します。",
        sub: [
          "アーカイブ公開前の配信を元にしたもの",
          "メンバーシップ限定、有料または非公開の配信・動画を元にしたもの",
          "配信のほぼ全編を転載する等、元動画と誤認されるおそれのあるもの",
          "配信のサムネイル、公式ロゴその他の公式画像を、サムネイル等にそのまま流用したもの",
          "前後の文脈を切り離し、または字幕・タイトルにより、発言の意図を歪めるもの",
        ],
      },
      { text: "切り抜き動画に第三者のコンテンツ（ゲーム映像、BGM、ゲスト等）が含まれる場合は、当該権利者の定める条件にも従ってください。" },
    ],
    example: {
      title: "切り抜きを公開する前に",
      body: "概要欄には「元配信：配信タイトル」に続けて、その配信のURLを記載してください。字幕やタイトルを付けるときは、前後の文脈や発言の意図が伝わる範囲を選んでください。",
    },
  },
  {
    id: "fan-events",
    title: "応援広告および二次創作イベント",
    items: [
      { text: "利用者は、応援広告や二次創作イベントを企画・実施することができます。" },
      {
        text: "前項の企画を実施する場合は、次の事項を遵守してください。",
        sub: [
          "企画内容に、ファンによる非公式の企画であることを明記すること",
          "使用する素材は、必ず作者の許諾を得た二次創作物を用いること",
          "事前にお問い合わせフォームより、企画の詳細を連絡すること",
          "参加費等を徴収する場合は、実費相当とし、営利性を排したものとすること",
        ],
      },
    ],
    example: {
      title: "企画を相談するとき",
      body: "掲載場所・期間、使用予定のイラストと作者名、参加費の有無が分かると確認がスムーズです。",
    },
  },
  {
    id: "ai-art",
    title: "AI生成作品",
    items: [
      { text: `AI生成作品を公開または頒布する場合は、タグ、説明文、頒布物の奥付等により、${em("AIを用いて作成したことを明示")}してください。また、AI生成作品の投稿には #深瀬画廊 を使用せず、専用タグ ${em("#みおりAI画廊")} を使用してください（成人向けのAI生成作品は、${ref("age-rating")}に定める #観測禁止区域 を使用してください。）。` },
      { text: `AI生成作品は、${ref("fan-goods")}の定めに従い、${em("趣味の範囲内に限り")}、同人誌、グッズ等として有償で頒布することができます。` },
      {
        text: "次の利用を禁止します。",
        sub: [
          `AI生成作品を${warn("営利目的で利用すること")}（有料素材としての販売を含みます。）`,
          "本コンテンツ、他の利用者の二次創作物または第三者の作品を、追加学習（LoRA等）、img2img、inpainting等の素材とすること",
          "特定のイラストレーターの画風を模倣させること",
          "当方の声や話し方を模倣した音声を生成し、またはそのような学習済みモデルを配布・販売すること",
          "当方が関与し、または公認したと誤認させる表現をすること",
        ],
      },
      { text: "利用者が自ら描いたオリジナルの絵を下絵とするimg2img、inpainting等は、前項bにかかわらず利用できます。" },
    ],
    example: {
      title: "頒布を考えている方へ",
      body: `AI生成作品も、${ref("fan-goods")}の範囲で同人誌やグッズとして頒布できます。頒布物や告知にはAIを用いたことを明記してください。一方、AIで生成したイラストを有料素材として販売することや、趣味の範囲を超えて継続的に販売することは、営利目的の利用に当たります。`,
    },
  },
  {
    id: "permissions",
    title: "有償依頼",
    items: [
      { text: `利用者は、Skeb等のサービスを通じて、イラストレーター等に二次創作物の制作を有償で依頼することができます。この場合の依頼料の授受は、${ref("definitions")}に定める営利目的には当たらないものとします。` },
      { text: "依頼する際は、完成作品の用途（個人での鑑賞、SNSへの掲載、グッズへの使用等）を作者と共有してください。完成作品の利用範囲は、作者との取り決めおよび依頼サービスの規約にも従います。" },
    ],
  },
  {
    id: "remedies",
    title: "当方による対応",
    items: [
      { text: "当方は、利用者による本コンテンツの利用が本ガイドラインに違反し、またはそのおそれがあると合理的に判断した場合、当該利用者に対し、二次創作物の修正、削除、公開停止または今後の利用の中止を求めることがあります。" },
      { text: "利用者は、前項の求めがあった場合、速やかに対応するものとします。" },
    ],
  },
  {
    id: "disclaimer",
    title: "免責",
    items: [
      { text: "本ガイドラインは、個別の利用許諾ではありません。本ガイドラインの範囲外の利用について、当方は権利を行使しないことを保証するものではありません。" },
      { text: "当方は、利用者が本ガイドラインに基づいて本コンテンツを利用したことにより生じた損害について、当方の故意または重大な過失による場合を除き、責任を負いません。" },
      { text: "二次創作物に関して利用者と第三者との間で紛争が生じた場合は、利用者の費用と責任において解決するものとします。" },
    ],
  },
  {
    id: "changes",
    title: "ガイドラインの変更",
    items: [
      {
        text: "当方は、次の各号のいずれかに該当する場合、民法第548条の4の規定に基づき、利用者の個別の合意を得ることなく、本ガイドラインを変更することができます。",
        sub: [
          "変更が、利用者の一般の利益に適合するとき",
          "変更が、本契約の目的に反せず、かつ、変更の必要性、変更後の内容の相当性、変更の内容その他の変更に係る事情に照らして合理的なものであるとき",
        ],
      },
      { text: "当方は、前項の変更をするときは、その効力発生日を定め、効力発生日までに、本ガイドラインを変更する旨、変更後の内容および効力発生日を、本ページへの掲載その他の適切な方法により周知します。" },
      { text: "第1項bに該当する変更は、効力発生日の到来までに前項の周知をした場合に限り、その効力を生じます。" },
    ],
  },
  {
    id: "governing-law",
    title: "準拠法および合意管轄",
    items: [
      { text: "本ガイドラインは、日本法に準拠します。" },
      {
        text: `本ガイドラインに関する紛争については、訴額に応じて、${em("東京簡易裁判所")}または${em("東京地方裁判所")}を第一審の専属的合意管轄裁判所とします。`,
      },
    ],
  },
];

const articleNo = new Map(articleDefs.map((a, i) => [a.id, i + 1]));
const resolveRefs = (s: string) =>
  s.replace(/\[\[([\w-]+)\]\]/g, (_, id: string) => {
    const n = articleNo.get(id);
    if (!n) throw new Error(`guideline: unknown article ref "${id}"`);
    return `第${n}条`;
  });

const articles: Article[] = articleDefs.map((a) => ({
  ...a,
  lead: a.lead && resolveRefs(a.lead),
  items: a.items.map((it) => ({
    text: resolveRefs(it.text),
    sub: it.sub?.map(resolveRefs),
  })),
  example: a.example && { title: a.example.title, body: resolveRefs(a.example.body) },
}));

const guideLinks = [
  { id: "fan-art", label: "ファンアート・クレジット" },
  { id: "prohibited", label: "禁止事項" },
  { id: "age-rating", label: "年齢制限のある作品" },
  { id: "fan-goods", label: "同人誌・グッズの頒布" },
  { id: "clips", label: "切り抜き・動画の収益化" },
  { id: "fan-events", label: "応援広告・イベント" },
  { id: "ai-art", label: "AI生成作品" },
  { id: "permissions", label: "有償依頼" },
  { id: "contact", label: "個別の相談・お問い合わせ" },
];

useSeoMeta({
  title: "二次創作ガイドライン | 深瀬みおり Official",
  description:
    "深瀬みおりの二次創作活動を楽しんでいただくための共通ルールとお願いです。",
});
</script>

<style scoped>
.guide-example {
  margin-inline-start: 1.25rem;
  padding: 1rem 1.25rem;
  border-inline-start: 3px solid var(--blue);
  background: #f3f6fb;
}

.guide-example h3 {
  font-weight: 700;
  color: var(--navy);
}

.guide-example p {
  margin-top: 0.4rem;
}

.animate-fade-in {
  animation: fadeIn 0.4s ease-out forwards;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(6px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
