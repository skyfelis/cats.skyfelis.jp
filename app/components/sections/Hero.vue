<template>
  <section class="brand-hero" aria-labelledby="hero-title">
    <div class="hero-inner">
      <div class="hero-copy">
        <h1 id="hero-title"><img src="/images/miori-logo.webp" width="1086" height="362" alt="深瀬みおり" /></h1>
        <p class="hero-tagline">情報学とゲームが好きな、<br />青い世界の猫VTuber。</p>
        <div class="hero-actions">
          <a class="brand-button" href="https://youtube.com/@skyfelis" target="_blank" rel="noopener noreferrer">YouTubeを見る <span aria-hidden="true">↗</span></a>
          <a class="hero-social" href="#profile">プロフィール <span aria-hidden="true">↓</span></a>
        </div>
      </div>
      <div class="hero-visual">
        <picture class="hero-character">
          <img src="/images/miori-front.webp" alt="猫耳と眼鏡に、紺色のジャージとヘッドホンを合わせた深瀬みおり" width="810" height="1440" fetchpriority="high" decoding="async" />
        </picture>
      </div>
    </div>
    <div class="hero-bottom"><a href="#activity">お知らせへ <span aria-hidden="true">↓</span></a></div>
  </section>
</template>

<style scoped>
.brand-hero {
  background: #eff8fc url("/images/banner.png") center / cover no-repeat;
}
.hero-bottom { justify-content: flex-end; }
.hero-bottom a, .hero-actions .hero-social {
  background-color: #fff;
}
.hero-bottom a {
  align-items: center;
  padding: 6px 12px;
  border-radius: 999px;
}
.hero-inner { column-gap: clamp(20px,4vw,70px); }
.hero-visual {
  overflow: hidden;
  align-self: center;
  height: clamp(440px,43vw,560px);
  border-radius: 48% 48% 16px 16px;
  background: radial-gradient(#fff9 1.3px, transparent 1.5px) 0 0 / 14px 14px,
    linear-gradient(148deg,#e0eafd 14%,#a7c4ed 68%,#789fce);
  border-bottom: 6px solid var(--red);
}
.hero-visual::before { inset: 12px; width: auto; height: auto; border-radius: inherit; border: 1px solid #ffffffa8; background: none; }
.hero-character { height: 100%; }
.hero-character img { width: 100%; height: 100%; object-fit: cover; object-position: center top; }
.hero-tagline { white-space: normal; }
.hero-actions a { border-radius: 999px; }
@media(max-width:640px) {
  .brand-hero {
    background-position: center top;
    background-size: auto clamp(255px, 73vw, 340px);
  }
  .hero-bottom a { width: auto; }
  .hero-inner { padding-top: 16px; }
  .hero-actions { flex-wrap: wrap; justify-content: center; }
  .hero-actions a { white-space: nowrap; padding-inline: 15px; gap: 8px; font-size: 13px; }
  .hero-visual { max-width: 380px; height: clamp(245px,70vw,320px); margin: 0 0 12px; }
  .hero-copy h1 { max-width: 280px; }
}
</style>
