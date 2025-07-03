<template>
  <div id="mainCard" class="relative w-screen h-screen bg-white rounded-none overflow-hidden flex flex-row flex-wrap" style="box-sizing:border-box;">
    <!-- Sidebar -->
    <div class="hidden lg:flex bg-[#6b2323] w-full sm:w-[40%] md:w-[34%] min-w-[220px] md:min-w-[340px] flex flex-col justify-between p-0 pl-6 md:pl-12 lg:pl-16 relative z-10">
      <div class="flex flex-col justify-center h-full">
        <h1 id="headline" class="text-white font-serif font-bold leading-none select-none opacity-0 text-[3.5rem] sm:text-[5rem] md:text-[7rem] lg:text-[8.5rem]" style="line-height:1.05;transform: translateY(40px); transition: opacity 0.8s cubic-bezier(0.4,0,0.2,1), transform 0.8s cubic-bezier(0.4,0,0.2,1);">Explore</h1>
        <button id="detailsBtn" class="mt-8 md:mt-12 flex items-center text-white group" style="outline:none;">
          <span class="w-10 h-10 flex items-center justify-center rounded-full border border-white mr-3 md:mr-4" style="background:transparent;">
            <svg width="28" height="28" viewBox="0 0 43 43" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M21.5 13V30" stroke="#fff" stroke-width="2" stroke-linecap="round"/>
              <path d="M13 21.5H30" stroke="#fff" stroke-width="2" stroke-linecap="round"/>
            </svg>
          </span>
          <span class="text-lg md:text-xl font-medium">More Details</span>
        </button>
      </div>
    </div>
    <!-- Mobile Hero Header -->
    <div class="mobile-hero-header lg:hidden">
      <h1 class="mobile-hero-title">Explore</h1>
      <button class="mobile-hero-btn" id="mobileDetailsBtn">
        <span class="plus-circle">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect x="2" y="2" width="20" height="20" rx="4" stroke="#fff" stroke-width="2" fill="none"/>
            <path d="M12 7V17" stroke="#fff" stroke-width="2" stroke-linecap="round"/>
            <path d="M7 12H17" stroke="#fff" stroke-width="2" stroke-linecap="round"/>
          </svg>
        </span>
        <span class="mobile-hero-btn-label">More Details</span>
      </button>
    </div>
    <!-- Hero Image -->
    <div class="relative w-full sm:w-[60%] md:w-[66%] h-full">
      <img src="/assets/Coding-Challenge-Image.png" alt="Forest" class="object-cover w-full h-full" />
      <!-- Social Icons -->
      <div class="social-icons">
        <a class="social-icon" href="#" aria-label="Facebook">
          <svg viewBox="0 0 90 90" width="90" height="90" xmlns="http://www.w3.org/2000/svg">
            <defs>
              <mask id="fb-mask">
                <rect width="90" height="90" fill="white"/>
                <path d="M54 24h-7c-6 0-10 4-10 10v5h-5v9h5v22h9V48h6l1-9h-7v-4c0-2 1-3 3-3h4v-8z" fill="black"/>
              </mask>
            </defs>
            <rect width="90" height="90" fill="white" mask="url(#fb-mask)"/>
          </svg>
        </a>
        <a class="social-icon" href="#" aria-label="Instagram">
          <svg viewBox="0 0 90 90" width="90" height="90" xmlns="http://www.w3.org/2000/svg">
            <defs>
              <mask id="ig-mask" maskUnits="userSpaceOnUse">
                <rect width="90" height="90" fill="white"/>
                <rect x="22" y="22" width="46" height="46" rx="14" fill="black"/>
                <rect x="29" y="29" width="32" height="32" rx="10" fill="white"/>
                <circle cx="45" cy="45" r="9" fill="black"/>
                <circle cx="59" cy="31" r="3" fill="black"/>
              </mask>
            </defs>
            <rect width="90" height="90" fill="white" mask="url(#ig-mask)"/>
          </svg>
        </a>
      </div>
    </div>
    <!-- SVG Modal Overlay -->
    <div id="svgModalOverlay" class="svg-modal-overlay"></div>
    <svg id="svgModalBg" class="svg-modal-bg" width="520" height="600" viewBox="0 0 520 600" style="display:none;" xmlns="http://www.w3.org/2000/svg">
      <polygon id="svgMorphPoly" fill="#fff"/>
      <foreignObject x="0" y="0" width="520" height="600">
        <div id="svgModalContent" class="svg-modal-content no-scrollbar" xmlns="http://www.w3.org/1999/xhtml">
          <div class="modal-inner">
            <button id="closeSvgModal" class="modal-close">&times;</button>
            <h2 class="modal-title">Explore</h2>
            <p class="modal-body">Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur?</p>
            <button class="modal-btn">Read More</button>
          </div>
        </div>
      </foreignObject>
    </svg>
  </div>
</template>

<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  // Animate headline on load
  setTimeout(function() {
    const headline = document.getElementById('headline');
    if (headline) headline.classList.add('headline-animate');
  }, 200);

  // Get all the DOM elements
  const detailsBtn = document.getElementById('detailsBtn');
  const mobileDetailsBtn = document.getElementById('mobileDetailsBtn');
  const svgModalOverlay = document.getElementById('svgModalOverlay');
  const svgModalBg = document.getElementById('svgModalBg');
  const svgMorphPoly = document.getElementById('svgMorphPoly');
  const svgModalContent = document.getElementById('svgModalContent');
  const closeSvgModal = document.getElementById('closeSvgModal');
  const headline = document.getElementById('headline');
  const card = document.getElementById('mainCard');

  // Helper functions
  function lerp(a, b, t) { return a + (b - a) * t; }
  function interpPoints(a, b, t) {
    return a.map((pt, i) => [lerp(pt[0], b[i][0], t), lerp(pt[1], b[i][1], t)]);
  }
  function pointsToString(pts) {
    return pts.map(pt => pt.join(",")).join(" ");
  }
  function cubicBezier(p0, p1, p2, p3, t) {
    const u = 1 - t;
    return 3 * u * u * t * p1 + 3 * u * t * t * p2 + t * t * t;
  }
  function polygonalFoldedPoints() {
    return [
      [18, 0], [42, 8], [60, 22], [58, 44],
      [40, 60], [16, 58], [0, 40], [2, 16]
    ];
  }
  function rectPolygon(w, h) {
    return [
      [0, 0], [w/2, 0], [w, 0], [w, h/2],
      [w, h], [w/2, h], [0, h], [0, h/2]
    ];
  }

  function animateModalToCard(from, to, duration = 1000, cb) {
    let start = null;
    function step(ts) {
      if (!start) start = ts;
      let t = Math.min((ts - start) / duration, 1);
      const ease = t < 1 ? cubicBezier(0.22, 0.61, 0.36, 1, t) : 1;

      const w = lerp(from.w, to.w, ease);
      const h = lerp(from.h, to.h, ease);
      svgModalBg.setAttribute('width', w);
      svgModalBg.setAttribute('height', h);
      svgModalBg.setAttribute('viewBox', `0 0 ${w} ${h}`);
      svgModalBg.style.width = w + 'px';
      svgModalBg.style.height = h + 'px';

      const left = lerp(from.left, to.left, ease);
      const top = lerp(from.top, to.top, ease);
      svgModalBg.style.left = left + 'px';
      svgModalBg.style.top = top + 'px';

      const pts = interpPoints(from.foldedPoints, to.rectPoints, ease);
      svgMorphPoly.setAttribute('points', pointsToString(pts));

      if (t < 1) {
        requestAnimationFrame(step);
      } else {
        svgModalBg.setAttribute('width', to.w);
        svgModalBg.setAttribute('height', to.h);
        svgModalBg.setAttribute('viewBox', `0 0 ${to.w} ${to.h}`);
        svgModalBg.style.width = to.w + 'px';
        svgModalBg.style.height = to.h + 'px';
        svgModalBg.style.left = to.left + 'px';
        svgModalBg.style.top = to.top + 'px';
        svgMorphPoly.setAttribute('points', pointsToString(to.rectPoints));
        setTimeout(() => svgModalContent.classList.add('visible'), 120);
        if (cb) cb();
      }
    }
    requestAnimationFrame(step);
  }

  function openModalFromButton(btn) {
    headline.classList.add('headline-hidden');
    svgModalOverlay.classList.add('visible');
    svgModalBg.style.display = '';
    svgModalContent.classList.remove('visible');
    
    const btnRect = btn.getBoundingClientRect();
    const cardRect = card.getBoundingClientRect();
    const btnCenterX = btnRect.left + btnRect.width / 2 - cardRect.left;
    const btnCenterY = btnRect.top + btnRect.height / 2 - cardRect.top;
    
    let rectW = 520, rectH = 600;
    if (window.innerWidth < 700) {
      rectW = Math.min(window.innerWidth * 0.94, 370);
      rectH = Math.min(window.innerHeight * 0.70, 420);
    }
    if (window.innerWidth < 500) {
      rectW = Math.min(window.innerWidth * 0.97, 320);
      rectH = Math.min(window.innerHeight * 0.78, 340);
    }
    
    const foldedW = 60, foldedH = 60;
    const foldedPoints = polygonalFoldedPoints();
    const rectPoints = rectPolygon(rectW, rectH);
    svgMorphPoly.setAttribute('points', pointsToString(foldedPoints));
    
    let sidebarWidth = card.offsetWidth * 0.34;
    if (window.innerWidth < 700) sidebarWidth = card.offsetWidth * 0.40;
    if (window.innerWidth < 500) sidebarWidth = card.offsetWidth * 0.0;
    
    let finalLeft = sidebarWidth;
    let finalTop = 120;
    let margin = 16;
    
    if (window.innerWidth < 700) {
      finalLeft = (window.innerWidth - rectW) / 2;
      finalTop = (window.innerHeight - rectH) / 2;
      if (finalTop < 12) finalTop = 12;
    } else {
      if (finalLeft + rectW > window.innerWidth - margin) {
        finalLeft = window.innerWidth - rectW - margin;
        if (finalLeft < margin) finalLeft = margin;
      }
      if (finalTop + rectH > window.innerHeight - 24) {
        finalTop = window.innerHeight - rectH - 24;
        if (finalTop < 24) finalTop = 24;
      }
    }
    
    const foldedLeft = btnCenterX - foldedW/2 - 80;
    const foldedTop = btnCenterY - foldedH/2 + 120;
    
    svgModalBg.setAttribute('width', foldedW);
    svgModalBg.setAttribute('height', foldedH);
    svgModalBg.setAttribute('viewBox', `0 0 ${foldedW} ${foldedH}`);
    svgModalBg.style.width = foldedW + 'px';
    svgModalBg.style.height = foldedH + 'px';
    svgModalBg.style.position = 'absolute';
    svgModalBg.style.left = foldedLeft + 'px';
    svgModalBg.style.top = foldedTop + 'px';
    svgModalBg.style.transform = '';
    
    setTimeout(() => {
      animateModalToCard(
        {
          left: foldedLeft,
          top: foldedTop,
          w: foldedW,
          h: foldedH,
          foldedPoints: foldedPoints,
          rectPoints: rectPoints
        },
        {
          left: finalLeft,
          top: finalTop,
          w: rectW,
          h: rectH,
          foldedPoints: foldedPoints,
          rectPoints: rectPoints
        },
        1000
      );
    }, 60);
  }
  
  // Event listeners
  if (detailsBtn) {
    detailsBtn.addEventListener('click', function() { openModalFromButton(detailsBtn); });
  }
  if (mobileDetailsBtn) {
    mobileDetailsBtn.addEventListener('click', function() { openModalFromButton(mobileDetailsBtn); });
  }

  if (svgModalOverlay) {
    svgModalOverlay.addEventListener('transitionend', function(e) {
      if (svgModalOverlay.classList.contains('visible')) {
        svgModalBg.style.pointerEvents = 'auto';
        svgModalContent.style.pointerEvents = 'auto';
      }
    });
  }

  function closeModal() {
    svgModalOverlay.classList.remove('visible');
    svgModalBg.style.display = 'none';
    svgModalContent.classList.remove('visible');
    headline.classList.remove('headline-hidden');
  }
  
  if (closeSvgModal) {
    closeSvgModal.addEventListener('click', closeModal);
  }
  if (svgModalOverlay) {
    svgModalOverlay.addEventListener('click', function(e) {
      if (e.target === svgModalOverlay) closeModal();
    });
  }
})
</script>

<style>
body, h1, h2, h3, h4, h5, h6 {
  font-family: 'Playfair Display', Georgia, serif;
}
:root {
  --maroon: #6d232c;
  --copper: #a85d5d;
}
.headline-animate {
  opacity: 1 !important;
  transform: none !important;
  transition: opacity 0.8s cubic-bezier(0.4,0,0.2,1), transform 0.8s cubic-bezier(0.4,0,0.2,1);
}
.headline-hidden {
  opacity: 0 !important;
  transition: opacity 0.4s cubic-bezier(0.4,0,0.2,1);
}
.modal-hidden {
  opacity: 0;
  transform: scale(0.85) translateY(40px);
  pointer-events: none;
  transition: opacity 0.4s, transform 0.4s;
}
.modal-visible {
  opacity: 1;
  transform: scale(1) translateY(0);
  pointer-events: auto;
  transition: opacity 0.4s, transform 0.4s;
}
.overlay-hidden {
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s;
}
.overlay-visible {
  opacity: 1;
  pointer-events: auto;
  transition: opacity 0.3s;
}
.svg-modal-bg {
  position: absolute;
  left: 50%;
  top: 50% !important;
  transform: translate(-50%, -50%);
  z-index: 50;
  pointer-events: none;
  filter: drop-shadow(0 8px 32px rgba(0,0,0,0.18));
  max-width: 98vw;
  max-height: 90vh;
  min-width: 0;
  min-height: 0;
  box-sizing: border-box;
}
.svg-modal-content {
  opacity: 0;
  transition: opacity 0.4s;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0;
}
.svg-modal-content.visible {
  opacity: 1;
  transition: opacity 0.4s 0.1s;
}
.svg-modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.4);
  opacity: 0;
  pointer-events: none;
  z-index: 40;
  transition: opacity 0.3s;
}
.svg-modal-overlay.visible {
  opacity: 1;
  pointer-events: auto;
}
.no-scrollbar::-webkit-scrollbar { display: none; }
.no-scrollbar { -ms-overflow-style: none; scrollbar-width: none; }
.modal-inner {
  position: relative;
  padding: 2.5rem 2.5rem 2.5rem 2.5rem;
  width: 100%;
  box-sizing: border-box;
  background: transparent;
  border-radius: 6px;
  box-shadow: 0 4px 24px rgba(0,0,0,0.10);
}
@media (min-width: 500px) {
  .modal-inner {
    padding: 2.8rem 2.5rem 2.8rem 2.5rem;
  }
}
.modal-close {
  position: absolute;
  top: 3rem;
  right: 1.5rem;
  font-size: 2rem;
  color: var(--maroon);
  font-weight: 400;
  background: none;
  border: none;
  cursor: pointer;
  font-family: 'Inter', Arial, sans-serif;
  padding: 0.1rem 0.7rem 0.1rem 0.2rem;
  line-height: 1;
  z-index: 2;
  margin: 0;
  transition: color 0.2s;
}
.modal-close:active {
  color: var(--copper);
}
.modal-title {
  font-family: 'Playfair Display', Georgia, serif;
  font-size: 2.7rem;
  font-weight: 700;
  color: var(--maroon);
  line-height: 1.05;
  letter-spacing: -0.01em;
  text-align: left;
  margin: 0 0 1.2rem 0;
  padding: 0;
}
.modal-body {
  color: #222;
  margin-bottom: 2.2rem;
  font-size: 1.08rem;
  line-height: 1.7;
  max-width: 100%;
  font-family: 'Inter', Arial, sans-serif;
  font-weight: 400;
  text-align: left;
  padding: 0;
}
.modal-btn {
  width: 200px;
  max-width: 90vw;
  background: linear-gradient(90deg, var(--maroon) 0%, var(--copper) 100%);
  color: #fff;
  padding: 0.95rem 0;
  font-size: 1.1rem;
  font-family: 'Inter', Arial, sans-serif;
  font-weight: 700;
  letter-spacing: 0.12em;
  border: none;
  border-radius: 0px;
  text-transform: uppercase;
  margin-top: 1.5rem;
  margin-bottom: 0.2rem;
  box-shadow: none;
  transition: background 0.2s;
  outline: none;
  text-align: center;
  display: block;
}
.modal-btn:active {
  background: linear-gradient(90deg, var(--copper) 0%, var(--maroon) 100%);
}
@media (min-width: 601px) and (max-width: 1023px) {
  .svg-modal-bg {
    width: 85vw !important;
    min-width: 0 !important;
    max-width: 90vw !important;
    left: 50% !important;
    top: 50% !important;
    transform: translate(-50%, -50%) !important;
    border-radius: 16px !important;
    box-shadow: none !important;
    max-height: 88vh !important;
  }
  .modal-inner {
    padding: 2rem 1.8rem 2rem 1.8rem;
    border-radius: 14px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    min-height: 50vh;
  }
  .modal-title {
    font-size: 2rem;
    margin-bottom: 1rem;
  }
  .modal-body {
    font-size: 1.05rem;
    line-height: 1.7;
    padding: 0;
  }
  .modal-btn {
    width: 180px;
    max-width: 100%;
    font-size: 1.05rem;
    margin-top: 1.3rem;
    margin-bottom: 0.2rem;
    padding: 0.9rem 0;
  }
  .modal-close {
    font-size: 1.8rem;
    top: 1.2rem;
    right: 1.2rem;
    padding: 0.3rem 0.8rem 0.3rem 0.3rem;
  }
  .social-icons {
    right: 14px;
    bottom: 50%;
    gap: 16px;
  }
  .social-icon {
    width: 60px;
    height: 60px;
  }
  .social-icon svg {
    width: 32px;
    height: 32px;
  }
  .hidden.lg\:flex {
    display: none !important;
  }
  .mobile-hero-header {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background: var(--maroon);
    width: 100vw;
    min-height: 50vh;
    padding: 3rem 2rem 2.5rem 2rem;
    box-sizing: border-box;
    text-align: center;
  }
  .mobile-hero-title {
    color: #fff;
    font-size: 3.5rem;
    font-family: 'Playfair Display', Georgia, serif;
    font-weight: 900;
    margin-bottom: 2rem;
    line-height: 1.08;
    letter-spacing: -0.01em;
  }
  .mobile-hero-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    background: rgba(255,255,255,0.08);
    border-radius: 9999px;
    color: #fff;
    font-size: 1.2rem;
    font-family: 'Inter', Arial, sans-serif;
    font-weight: 600;
    padding: 0.8rem 1.8rem;
    margin: 0 auto;
    box-shadow: 0 2px 8px rgba(0,0,0,0.07);
    transition: background 0.2s;
  }
  .mobile-hero-btn .plus-circle {
    width: 38px;
    height: 38px;
    margin-right: 12px;
    background: transparent;
    border: 2px solid #fff;
  }
  .mobile-hero-btn .plus-circle svg {
    width: 20px;
    height: 20px;
    stroke: #fff;
  }
  .mobile-hero-btn-label {
    color: #fff;
    font-size: 1.2rem;
    font-family: 'Inter', Arial, sans-serif;
    font-weight: 600;
    letter-spacing: 0.01em;
  }
  .relative.w-full.sm\:w-\[60\%\].md\:w-\[66\%\].h-full {
    width: 100% !important;
  }
}
@media (max-width: 600px) {
  .svg-modal-bg {
    width: 94vw !important;
    min-width: 0 !important;
    max-width: 98vw !important;
    left: 50% !important;
    top: 50% !important;
    transform: translate(-50%, -50%) !important;
    border-radius: 18px !important;
    box-shadow: 0 4px 24px rgba(0,0,0,0.13) !important;
    max-height: 92vh !important;
  }
  .modal-inner {
    padding: 1.5rem 1.1rem;
    border-radius: 16px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    min-height: 40vh;
    width: 80vw;
    max-width: 370px;
    margin: 0 auto;
    overflow-y: auto;
    position: relative;
    top: 0;
    left: 0;
  }
  .modal-title {
    font-size: 1.35rem;
    margin-bottom: 0.7rem;
  }
  .modal-body {
    font-size: 0.97rem;
    line-height: 1.7;
    padding: 0;
  }
  .modal-btn {
    width: 100%;
    max-width: 100%;
    font-size: 0.98rem;
    margin-top: 1.1rem;
    margin-bottom: 0.2rem;
    padding: 0.85rem 0;
  }
  .modal-close {
    font-size: 1.3rem;
    top: 0.7rem;
    right: 0.7rem;
    padding: 0.4rem 0.7rem 0.4rem 0.2rem;
  }
  .mobile-hero-btn .plus-circle {
    width: 34px;
    height: 34px;
    margin-right: 10px;
    background: transparent;
    border: 2px solid #fff;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .mobile-hero-btn .plus-circle svg {
    width: 18px;
    height: 18px;
    stroke: #fff;
  }
  .mobile-hero-btn-label {
    color: #fff;
    font-size: 1.1rem;
    font-family: 'Inter', Arial, sans-serif;
    font-weight: 600;
    letter-spacing: 0.01em;
  }
  .mobile-hero-header {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background: var(--maroon);
    width: 100vw;
    min-height: 56vw;
    min-height: 48vh;
    padding: 2.5rem 1.2rem 2.2rem 1.2rem;
    box-sizing: border-box;
    text-align: center;
  }
  .mobile-hero-title {
    color: #fff;
    font-size: 2.5rem;
    font-family: 'Playfair Display', Georgia, serif;
    font-weight: 900;
    margin-bottom: 1.5rem;
    line-height: 1.08;
    letter-spacing: -0.01em;
  }
  .mobile-hero-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    background: rgba(255,255,255,0.08);
    border-radius: 9999px;
    color: #fff;
    font-size: 1.1rem;
    font-family: 'Inter', Arial, sans-serif;
    font-weight: 600;
    padding: 0.7rem 1.6rem;
    margin: 0 auto;
    box-shadow: 0 2px 8px rgba(0,0,0,0.07);
    transition: background 0.2s;
  }
  .mobile-hero-btn .plus-circle {
    width: 34px;
    height: 34px;
    margin-right: 10px;
    background: transparent;
    border: 2px solid #fff;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .mobile-hero-btn .plus-circle svg {
    width: 18px;
    height: 18px;
    stroke: #fff;
  }
  .mobile-hero-btn-label {
    color: #fff;
    font-size: 1.1rem;
    font-family: 'Inter', Arial, sans-serif;
    font-weight: 600;
    letter-spacing: 0.01em;
  }
}
.social-icons {
  position: absolute;
  right: 18px;
  bottom: 18px;
  display: flex;
  flex-direction: column;
  z-index: 10;
  align-items: center;
}
.social-icon {
  width: 70px;
  height: 70px;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: none;
  border: none;
  margin-bottom: 10px;
  padding: 0;
}
.social-icon svg {
  display: block;
  width: 60px;
  height: 60px;
  margin: 0 auto;
  border-radius: 100%;
}
.social-icon img {
  display: none;
}
@media (max-width: 600px) {
  .social-icons {
    right: 8px;
    bottom: 50%;
    gap: 18px;
  }
  .social-icon {
    width: 64px;
    height: 64px;
  }
  .social-icon svg {
    width: 38px;
    height: 38px;
  }
}
</style>
