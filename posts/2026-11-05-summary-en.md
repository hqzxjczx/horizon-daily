---
layout: default
title: "Horizon Summary: 2026-11-05 (EN)"
date: 2026-11-05
lang: en
---

> From 42 items, 9 important content pieces were selected

---

**Technology News**
1. [Alpine Linux OpenSSH password auth bypass via musl crypt\(\) edge case](#item-tech-news-1) ⭐️ 8.0/10
2. [ULC codec fits N64: near-MP3 quality at 32kbps, 4KB RAM](#item-tech-news-2) ⭐️ 8.0/10
3. [DialFork: a benchmark for procedural hallucination in conversational agents \[R\]](#item-tech-news-3) ⭐️ 8.0/10
4. [Xiaomi Robot Agent trials in youth apartments](#item-tech-news-4) ⭐️ 8.0/10
5. [约 60 万颗英伟达 H200 积压香港待批](#item-tech-news-5) ⭐️ 8.0/10

**Financial News**
1. [中国叫停软银 54 亿美元收购 ABB 机器人业务](#item-finance-news-1) ⭐️ 8.0/10
2. [美光因劳资纠纷暂停桃园 45 亿美元建厂](#item-finance-news-2) ⭐️ 8.0/10
3. [芯片股抛售加剧，纳斯达克 100 指数跌 5%](#item-finance-news-3) ⭐️ 8.0/10
4. [2027 年放假安排出炉：调休天数近年最少](#item-finance-news-4) ⭐️ 7.0/10

---

## Technology News

<a id="item-tech-news-1"></a>
### [Alpine Linux OpenSSH password auth bypass via musl crypt\(\) edge case](https://alpinelinux.org/posts/2026-11-05-openssh-password-authentication-bypass/) ⭐️ 8.0/10

Alpine Linux OpenSSH server vulnerable to password authentication bypass when musl libc crypt\(\) returns &\#x27;\*&\#x27; for passwords longer than 256 bytes. The &\#x27;\*&\#x27; return value matches the empty-password hash sentinel in /etc/passwd, allowing login to accounts with no password set. OpenSSH 10.6p2 released Nov 5 fixes the issue. Alpine 3.16+ have updated packages; mitigation is setting PasswordAuthentication no. Vulnerability affects Alpine-based Docker images widely used in production.

hackernews · pantalaimon · Nov 5, 14:44 · [Discussion](https://news.ycombinator.com/item?id=50379704)

**「Background」** musl libc crypt\(\) returns &\#x27;\*&\#x27; for keys longer than 256 bytes as error indicator. This &\#x27;\*&\#x27; matches empty-password hash sentinel in /etc/passwd, allowing authentication bypass. Alpine Linux uses musl libc by default, making OpenSSH server vulnerable when password authentication enabled. OpenSSH 10.6p2 released November 5, 2026 fixes this by rejecting overly long passwords before calling crypt\(\).

**「Impact」** Alpine Linux official Docker image has 12.4 billion pulls and underpins 55,141 Docker Official Images, making this vulnerability high-impact for container deployments. Affected systems: any Alpine 3.16+ container with OpenSSH server and PasswordAuthentication yes \(default\). Attackers with network access and valid username can authenticate as no-password accounts using 257-1024 byte passwords. Immediate mitigation: upgrade openssh-server package or set PasswordAuthentication no in sshd\_config. No exploit reports yet but rapid rediscovery risk cited by OpenSSH developers.

**「Community Discussion」** Commenters note musl&\#x27;s crypt\(\) returns &\#x27;\*&\#x27; as error indicator for keys over 256 bytes, which coincidentally matches the no-password sentinel in /etc/passwd. Discussion questions why musl chose this behavior despite POSIX adherence goals. Some highlight Rust&\#x27;s Result type forcing explicit error handling as safer than C&\#x27;s sentinel values. Links to related HN threads and openssh-unix-dev mailing list provide additional technical details.

<details><summary>References</summary>
<ul>
<li><a href="https://gist.github.com/ncopa/b1515f99f5efbc82fcc8b15dcc5e1b4f">Alpine Linux Usage Stastitics.md · GitHub</a></li>

</ul>
</details>

**Tags**: `#security`, `#alpine-linux`, `#openssh`, `#musl-libc`, `#docker`

---

<a id="item-tech-news-2"></a>
### [ULC codec fits N64: near-MP3 quality at 32kbps, 4KB RAM](https://phoboslab.org/log/2026/11/n64-ulc-codec) ⭐️ 8.0/10

ULC audio codec runs on N64 hardware using only integer arithmetic and 4KB RAM. Achieves near-MP3 quality at 32kbps. Article details fixed-point implementation, memory layout, and patent history context.

hackernews · frostbyte7 · Nov 5, 12:51 · [Discussion](https://news.ycombinator.com/item?id=50378508)

**「Background」** N64 audio historically faced severe constraints: limited CPU, 4MB RAM \(8MB with Expansion Pak\), and a patent minefield around MP3. Developers used low-quality ADPCM, sequenced music, or licensed expensive decoders. The ULC codec avoids patents by using only integer math and fits in 4KB RAM, making it viable for homebrew and retro development today.

**「Community Discussion」** Commenters note patent minefield would have blocked adoption in 1999; N64 MP3 decoder licensed from RAD/Fraunhofer but code unused. Another user expresses interest in writing own codec inspired by article.

<details><summary>References</summary>
<ul>
<li><a href="https://phoboslab.org/log/2026/11/n64-ulc-codec">Why this Obscure Audio Codec is a Perfect Fit for the N64</a></li>

</ul>
</details>

**Tags**: `#audio-codec`, `#n64`, `#compression`, `#retro-computing`, `#embedded-systems`

---

<a id="item-tech-news-3"></a>
### [DialFork: a benchmark for procedural hallucination in conversational agents \[R\]](https://www.reddit.com/r/MachineLearning/comments/1xofjrn/dialfork_a_benchmark_for_procedural_hallucination/) ⭐️ 8.0/10

DialFork benchmark measures procedural hallucination where agents execute correct tool calls but fail to follow conversational procedure steps.

reddit · r/MachineLearning · /u/sergbur · Nov 5, 10:44

**Tags**: `#conversational-agents`, `#benchmark`, `#procedural-hallucination`, `#LLM-evaluation`, `#dialogue-systems`

---

<a id="item-tech-news-4"></a>
### [Xiaomi Robot Agent trials in youth apartments](https://weibo.com/1749127163/5361796274981767) ⭐️ 8.0/10

Xiaomi deploys Xiaomi-Robotics-1 embodied base model in youth apartments for trial operation. Closed-loop system covers data collection, inference, execution. Validates autonomous long-horizon tasks over 30 minutes continuous across 3 rooms with 50+ tasks including desktop organization, trash cleaning, item sorting, room inspection, whole-house re-inspection.

telegram · zaihuapd · Nov 5, 08:19

**「Background」** Xiaomi-Robotics-1 is Xiaomi&\#x27;s embodied foundation model for robotics, enabling perception, planning, and control in physical environments. The Agent closed-loop system integrates data collection, model inference, and task execution for autonomous household operations. This trial extends prior lab validation into a real-world residential setting.

**「Impact」** Xiaomi Robot Agent trial youth apartments proves closed-loop embodied system works real homes. Long-horizon &gt;30 min, 3 rooms, 50+ tasks autonomous. Validates Xiaomi-Robotics-1 beyond factory. Developers get residential deployment reference. Xiaomi also runs eight-hour humanoid parts-sorting factories \(tool-2-1\). Embodied AI ready production across domains.

<details><summary>References</summary>
<ul>
<li><a href="https://interestingengineering.com/ai-robotics/xiaomi-humanoids-sort-car-parts">Xiaomi &#x27;s humanoid robots take on eight-hour car parts sorting task</a></li>

</ul>
</details>

**Tags**: `#embodied-ai`, `#robotics`, `#agent-systems`, `#xiaomi`, `#real-world-deployment`

---

<a id="item-tech-news-5"></a>
### [约 60 万颗英伟达 H200 积压香港待批](https://www.reuters.com/world/china/nvidia-chips-pile-up-hong-kong-china-withholds-import-approval-2026-11-05/) ⭐️ 8.0/10

600k NVIDIA H200 GPUs pile up in Hong Kong as Beijing withholds import approval, tripling server prices and constraining China AI compute.

telegram · zaihuapd · Nov 5, 14:42

**Tags**: `#AI hardware`, `#supply chain`, `#China tech`, `#NVIDIA`, `#export controls`

---

## Financial News

<a id="item-finance-news-1"></a>
### [中国叫停软银 54 亿美元收购 ABB 机器人业务](https://www.bloomberg.com/news/articles/2026-11-05/china-blocks-softbank-s-acquisition-of-abb-industrial-robot-unit) ⭐️ 8.0/10

China blocks SoftBank&\#x27;s $5.4B acquisition of ABB robotics unit citing national security concerns over industrial data and AI technology transfer.

telegram · zaihuapd · Nov 5, 10:44

**Tags**: `#China`, `#M&amp;A`, `#robotics`, `#AI`, `#regulation`, `#SoftBank`, `#ABB`

---

<a id="item-finance-news-2"></a>
### [美光因劳资纠纷暂停桃园 45 亿美元建厂](https://www.bloomberg.com/news/articles/2026-11-05/micron-pauses-work-on-4-5-billion-taiwan-plant-after-labor-spat) ⭐️ 8.0/10

Micron halts $4.5B Taoyuan fab construction over labor dispute threatening 60% of its DRAM output.

telegram · zaihuapd · Nov 5, 11:26

**Tags**: `#semiconductors`, `#labor-dispute`, `#Taiwan`, `#Micron`, `#DRAM`, `#supply-chain`

---

<a id="item-finance-news-3"></a>
### [芯片股抛售加剧，纳斯达克 100 指数跌 5%](https://www.bloomberg.com/news/articles/2026-11-04/stock-market-today-dow-s-p-live-updates) ⭐️ 8.0/10

Chip stocks lead Nasdaq 100 down 5% as weak guidance and Democratic sweep fuel AI regulation fears.

telegram · zaihuapd · Nov 5, 15:39

**Tags**: `#semiconductors`, `#market-selloff`, `#nasdaq`, `#ai-regulation`, `#defensive-rotation`

---

<a id="item-finance-news-4"></a>
### [2027 年放假安排出炉：调休天数近年最少](https://content-static.cctvnews.cctv.com/snow-book/index.html?toc_style_id=feeds_default&amp;amp;t=1793869338515&amp;amp;item_id=2849318238559867656&amp;amp;channelId=1215) ⭐️ 7.0/10

China releases 2027 holiday calendar with fewest make-up work days in recent years, detailing 9-day Spring Festival, 7-day National Day, 5-day Labor Day.

telegram · zaihuapd · Nov 5, 10:08

**Tags**: `#China`, `#holiday policy`, `#labor schedule`, `#consumer spending`, `#economic planning`

---