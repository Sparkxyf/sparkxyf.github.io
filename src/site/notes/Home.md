---
{"dg-publish":true,"dg-home":true,"permalink":"/","tags":["gardenEntry","garden","home"],"dg-note-properties":{"tags":["gardenEntry","garden","home"]}}
---

<div class="spark-home">
  <section class="spark-hero" aria-labelledby="spark-title">
    <div class="spark-hero-copy">
      <p class="spark-kicker">Digital Garden / Public Notes</p>
      <h1 id="spark-title">Spark</h1>
      <p class="spark-lede">一个慢慢长出来的知识入口：技术笔记、工程经验、交易与数据、阅读札记，以及还在发芽的想法。</p>
      <div class="spark-actions">
        <a href="/tech/Redis性能优化/">Redis 性能优化</a>
        <a href="#the-index">浏览索引</a>
        <a href="#paths">查看路径</a>
      </div>
    </div>
    <div class="spark-map" aria-label="Knowledge map">
      <svg viewBox="0 0 640 420" role="img" aria-labelledby="spark-map-title">
        <title id="spark-map-title">Spark 知识花园地图</title>
        <path d="M120 210 C190 110 290 92 384 132 C482 174 506 282 420 332 C318 392 182 342 120 210Z" />
        <path d="M154 118 C242 204 374 234 498 162" />
        <path d="M148 304 C252 240 352 214 486 292" />
        <line x1="320" y1="210" x2="154" y2="118" />
        <line x1="320" y1="210" x2="498" y2="162" />
        <line x1="320" y1="210" x2="148" y2="304" />
        <line x1="320" y1="210" x2="486" y2="292" />
        <circle class="spark-node" cx="320" cy="210" r="48" />
        <circle class="spark-node spark-node-tech" cx="154" cy="118" r="32" />
        <circle class="spark-node spark-node-data" cx="498" cy="162" r="35" />
        <circle class="spark-node spark-node-reading" cx="148" cy="304" r="34" />
        <circle class="spark-node spark-node-forge" cx="486" cy="292" r="30" />
        <text x="320" y="207" text-anchor="middle">Spark</text>
        <text x="320" y="226" text-anchor="middle" class="subtext">garden</text>
        <text x="154" y="116" text-anchor="middle">Tech</text>
        <text x="154" y="133" text-anchor="middle" class="subtext">systems</text>
        <text x="498" y="160" text-anchor="middle">Data</text>
        <text x="498" y="177" text-anchor="middle" class="subtext">trading</text>
        <text x="148" y="302" text-anchor="middle">Reading</text>
        <text x="148" y="319" text-anchor="middle" class="subtext">notes</text>
        <text x="486" y="291" text-anchor="middle">Forge</text>
        <text x="486" y="308" text-anchor="middle" class="subtext">tools</text>
      </svg>
    </div>
  </section>

  <section class="spark-section" id="the-index">
    <div class="spark-section-head">
      <h2>The Index</h2>
      <p>按主题进入，而不是按发布时间排队。已发布的文章可以直接阅读，种子条目会继续长成独立页面。</p>
    </div>
    <div class="spark-index-grid">
      <section class="spark-cluster">
        <h3>Technology <span></span></h3>
        <ul>
          <li><a href="/tech/Redis性能优化/">Redis 性能优化</a><em>published</em></li>
          <li><span>Java 数据结构与算法</span><em>seed</em></li>
          <li><span>系统设计与性能调优</span><em>seed</em></li>
          <li><span>后端工程实践</span><em>seed</em></li>
        </ul>
      </section>
      <section class="spark-cluster">
        <h3>Data <span></span></h3>
        <ul>
          <li><span>股票数据整理</span><em>seed</em></li>
          <li><span>Tushare 数据管线</span><em>seed</em></li>
          <li><span>交易复盘</span><em>seed</em></li>
          <li><span>指标与回测</span><em>seed</em></li>
        </ul>
      </section>
      <section class="spark-cluster">
        <h3>Reading <span></span></h3>
        <ul>
          <li><span>读书摘录</span><em>seed</em></li>
          <li><span>长文笔记</span><em>seed</em></li>
          <li><span>观点索引</span><em>seed</em></li>
          <li><span>主题书单</span><em>seed</em></li>
        </ul>
      </section>
      <section class="spark-cluster">
        <h3>Forge <span></span></h3>
        <ul>
          <li><span>博客与数字花园</span><em>growing</em></li>
          <li><span>自动化工具</span><em>seed</em></li>
          <li><span>小项目记录</span><em>seed</em></li>
          <li><span>写作系统</span><em>seed</em></li>
        </ul>
      </section>
    </div>
  </section>

  <section class="spark-section" id="paths">
    <div class="spark-section-head">
      <h2>Paths</h2>
      <p>首页先给出几条清晰路线，之后每条路线都可以扩展成专题地图。</p>
    </div>
    <div class="spark-paths">
      <article><strong>Now</strong><p>最近入口放在技术区，从 Redis 性能优化开始，把工程笔记整理成可回访的知识节点。</p></article>
      <article><strong>Next</strong><p>继续补 Java 算法、股票数据、博客发布流程，把零散主题接到稳定索引里。</p></article>
      <article><strong>Long Arc</strong><p>把笔记当作长期系统维护：主题相互连接，读完一篇能自然走到下一篇。</p></article>
    </div>
  </section>

  <section class="spark-section" id="cloud">
    <div class="spark-section-head">
      <h2>Cloud</h2>
      <p>像 Hermitage 的随机漫游区一样，给主题一个可以扫视、跳转、偶遇的位置。</p>
    </div>
    <div class="spark-cloud" aria-label="Tag cloud">
      <a class="xl" href="/tech/Redis性能优化/">Redis</a>
      <span class="lg">Java</span>
      <span class="md">Stock</span>
      <span>Obsidian</span>
      <span class="lg">Tushare</span>
      <span>GitHub Pages</span>
      <span class="md">Backend</span>
      <span>Reading</span>
      <span class="lg">Tools</span>
      <span>Markdown</span>
      <span class="md">Systems</span>
      <span>Writing</span>
    </div>
  </section>

  <section class="spark-section" id="state">
    <div class="spark-section-head">
      <h2>State</h2>
      <p>先把首页从简单入口变成真正的花园门面，再逐步让内容长满。</p>
    </div>
    <div class="spark-state-grid">
      <div><b>1</b><span>published note</span></div>
      <div><b>4</b><span>topic areas</span></div>
      <div><b>16</b><span>index entries</span></div>
      <div><b>12</b><span>cloud signals</span></div>
    </div>
  </section>
</div>
