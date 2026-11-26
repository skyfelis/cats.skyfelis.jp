<template>
  <section id="fankit"
    class="bg-white py-24 px-6 relative z-40 border-t border-slate-100 transition-all duration-[1000ms] ease-out transform font-sans antialiased text-slate-800">
    <div class="max-w-6xl mx-auto">
      <div class="mb-16 flex flex-col items-start select-none">
        <div class="w-12 h-1 bg-gradient-to-r from-miori-red to-miori-blue rounded-full mb-4"></div>

        <h2 class="text-4xl md:text-5xl font-sans font-bold tracking-wider text-miori-navy leading-none">
          Fan Kit
        </h2>

        <p class="text-xs font-sans font-bold text-slate-500 tracking-widest pt-3">
          ファンネーム・ハッシュタグ・ファンマーク
        </p>
      </div>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        <!-- ファンネーム -->
        <div
          class="cat-ear-card bg-slate-50/60 border border-slate-100 p-8 rounded-2xl space-y-4">
          <div class="flex items-center gap-3 text-miori-navy">
            <i class="fa-solid fa-users text-miori-blue text-lg"></i>
            <h3 class="text-base font-bold font-sans">ファンネーム</h3>
          </div>

          <p class="text-2xl font-sans font-black text-miori-navy tracking-wide pt-1">
            観測者
            <span class="text-xs text-slate-500 font-medium font-mono block sm:inline sm:ml-1">
              (型推論: Observer)
            </span>
          </p>

          <p class="text-xs md:text-sm text-slate-500 leading-relaxed font-medium">
            いつもパケットを受信し、活動をあたたかく見守って（デバッグして）くれているみんなの総称です。
          </p>
        </div>

        <!-- ハッシュタグ -->
        <div
          class="cat-ear-card bg-slate-50/60 border border-slate-100 p-8 rounded-2xl space-y-4">
          <div class="flex items-center gap-3 text-miori-navy">
            <i class="fa-solid fa-hashtag text-miori-blue text-lg"></i>
            <h3 class="text-base font-bold font-sans">ハッシュタグ</h3>
          </div>

          <div class="space-y-1.5 pt-1 font-mono">
            <div class="flex items-center gap-2">
              <span class="text-xs font-bold bg-miori-navy text-white px-2 py-0.5 rounded-md text-[10px] select-none">
                LIVE
              </span>

              <a href="https://x.com/search?q=%23%E3%81%BF%E3%81%8A%E3%82%8A%E8%A6%B3%E6%B8%AC%E4%B8%AD" target="_blank" rel="noopener noreferrer"
                class="text-sm font-black text-miori-navy hover:text-miori-blue transition-colors cursor-pointer">
                #みおり観測中
              </a>
            </div>

            <div class="flex items-center gap-2">
              <span class="text-xs font-bold bg-miori-navy text-white px-2 py-0.5 rounded-md text-[10px] select-none">
                ART
              </span>

              <a href="https://x.com/search?q=%23%E6%B7%B1%E7%80%AC%E7%94%BB%E5%BB%8A" target="_blank" rel="noopener noreferrer"
                class="text-sm font-black text-miori-navy hover:text-miori-blue transition-colors cursor-pointer">
                #深瀬画廊
              </a>
            </div>

            <div class="flex items-center gap-2">
              <span class="text-xs font-bold bg-miori-navy text-white px-2 py-0.5 rounded-md text-[10px] select-none">
                AI
              </span>

              <a href="https://x.com/search?q=%23%E3%81%BF%E3%81%8A%E3%82%8AAI%E7%94%BB%E5%BB%8A" target="_blank" rel="noopener noreferrer"
                class="text-sm font-black text-miori-navy hover:text-miori-blue transition-colors cursor-pointer">
                #みおりAI画廊
              </a>
            </div>
          </div>

          <p class="text-xs md:text-sm text-slate-500 leading-relaxed font-medium">
            X（Twitter）等でのポストの際にお使いください。ハッシュタグ付きのログは定期的に巡回・集約しています。
          </p>
        </div>

        <!-- ファンマーク -->
        <div
          class="cat-ear-card bg-slate-50/60 border border-slate-100 p-8 rounded-2xl space-y-4 sm:col-span-2 lg:col-span-1">
          <div class="flex items-center gap-3 text-miori-navy">
            <i class="fa-solid fa-paw text-miori-blue text-lg"></i>
            <h3 class="text-base font-bold font-sans">ファンマーク</h3>
          </div>

          <p class="text-4xl font-sans font-black text-miori-navy pt-1">
            🟥🟦🐈️
          </p>

          <p class="text-xs md:text-sm text-slate-500 leading-relaxed font-medium">
            赤、青、猫の順に並べたファンマークです。SNSの名前の後ろやプロフィールにどうぞ。
          </p>
        </div>

      </div>
    </div>
  </section>
</template>
