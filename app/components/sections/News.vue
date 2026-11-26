<template>
  <section id="activity" class="news-section" aria-labelledby="home-news-title">
    <div class="section-container">
      <header class="news-heading">
        <h2 id="home-news-title">News <small lang="ja">ニュース</small></h2>
        <NuxtLink to="/news" class="news-index">一覧を見る <span aria-hidden="true">→</span></NuxtLink>
      </header>
      <ul class="news-list">
        <li v-for="item in latestNews" :key="item.path">
          <NuxtLink :to="item.path" class="news-row">
            <time :datetime="item.year + '-' + item.date.replace('.', '-')">{{ item.year }}.{{ item.date }}</time>
            <div class="news-copy">
              <span class="news-category">{{ item.category }}</span>
              <h3>{{ item.title }}</h3>
            </div>
            <NuxtImg v-if="item.thumbnail" :src="item.thumbnail" width="560" height="315" fit="contain"
              format="webp" loading="lazy" alt="" class="news-thumbnail" />
          </NuxtLink>
        </li>
      </ul>
    </div>
  </section>
</template>

<script setup lang="ts">
const latestNews = useRouter().getRoutes()
  .filter(route => route.path.startsWith("/news/posts/") && route.meta.sortKey)
  .sort((a, b) => String(b.meta.sortKey).localeCompare(String(a.meta.sortKey)) || b.path.localeCompare(a.path))
  .slice(0, 4)
  .map(({ path, meta }) => ({
    path,
    year: String(meta.year),
    date: String(meta.date),
    title: String(meta.title).replace(/^【[^】]+】/, ""),
    category: meta.category === "Update" ? "モデル更新" : String(meta.category || "お知らせ"),
    thumbnail: typeof meta.thumbnail === "string" ? meta.thumbnail : undefined,
  }));
</script>

<style scoped>
#activity.news-section { background: white; padding-block: clamp(40px, 4.5vw, 64px); }
.news-heading { display: flex; align-items: center; justify-content: space-between; gap: 1rem; padding-bottom: 27px; }
#activity h2 { display: flex; align-items: baseline; gap: 12px; font-size: clamp(26px, 3vw, 32px); }
#activity h2::before { content: none; }
.news-heading small { font-size: 11px; letter-spacing: .1em; }
.news-index { display: inline-flex; align-items: center; gap: .75rem; padding: 12px 24px; border: 1px solid #d6d9df; border-radius: 99px; color: var(--navy); font-size: 13px; font-weight: 700; }
.news-index:hover { border-color: var(--red); color: var(--red); }
.news-list { border-top: 1px solid #d6d9df; }
.news-row { display: grid; grid-template-columns: clamp(96px, 10vw, 120px) minmax(0, 1fr) auto; align-items: center; gap: 20px; padding: 24px 0; border-bottom: 1px solid #d6d9df; color: var(--navy); }
.news-row time { font: 600 14px/1.5 "Source Code Pro", monospace; }
.news-category { display: inline-block; padding: 3px 12px; border-radius: 99px; background: #eef3fa; color: var(--blue); font-size: 11px; font-weight: 700; }
.news-copy h3 { margin-top: 9px; font-size: 18px; font-weight: 700; line-height: 1.55; }
.news-thumbnail { width: clamp(140px, 16vw, 200px); aspect-ratio: 16/9; height: auto; border-radius: 8px; background: #f4f6fa; object-fit: contain; }
li:first-child .news-row { padding-block: 28px; }
li:first-child .news-thumbnail { width: clamp(180px, 23vw, 280px); }
li:first-child h3 { font-size: clamp(20px, 2vw, 25px); }
.news-row:hover h3, .news-row:focus-visible h3 { color: var(--red); text-decoration: underline; text-underline-offset: .22em; }
@media(max-width: 640px) {
  .news-row { grid-template-columns: minmax(0, 1fr) auto; gap: 5px 12px; padding-block: 19px; }
  .news-row time { font-size: 12px; }
  .news-copy { grid-column: 1; }
  .news-thumbnail, li:first-child .news-thumbnail { grid-column: 2; grid-row: 1 / span 2; width: clamp(78px, 23vw, 130px); }
  .news-copy h3, li:first-child h3 { font-size: 15px; }
  .news-index { padding: 10px 15px; }
}
</style>
