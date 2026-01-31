# ga
<!doctype doctype>
<html lang="vi" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Bio-Tech Survival World</title>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body {
      box-sizing: border-box;
    }
    
    @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800;900&family=Rajdhani:wght@300;400;500;600;700&display=swap');
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    
    html, body {
      height: 100%;
      width: 100%;
      overflow: hidden;
    }
    
    body {
      font-family: 'Rajdhani', sans-serif;
      background: linear-gradient(135deg, #0a0e27 0%, #1a1f3a 50%, #0f1420 100%);
      color: #e0e7ff;
      position: relative;
    }
    
    .app-container {
      width: 100%;
      height: 100%;
      overflow-y: auto;
      overflow-x: hidden;
      position: relative;
    }
    
    /* Animated Background */
    .bg-circuit {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-image: 
        linear-gradient(rgba(99, 102, 241, 0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(99, 102, 241, 0.03) 1px, transparent 1px);
      background-size: 50px 50px;
      animation: circuitFlow 20s linear infinite;
      pointer-events: none;
      z-index: 0;
    }
    
    @keyframes circuitFlow {
      0% { transform: translate(0, 0); }
      100% { transform: translate(50px, 50px); }
    }
    
    /* Glowing Particles */
    .particle {
      position: fixed;
      width: 3px;
      height: 3px;
      background: #6366f1;
      border-radius: 50%;
      pointer-events: none;
      animation: float 15s infinite;
      box-shadow: 0 0 10px #6366f1, 0 0 20px #6366f1;
      z-index: 1;
    }
    
    @keyframes float {
      0%, 100% { 
        transform: translate(0, 0) scale(1);
        opacity: 0;
      }
      10% { opacity: 1; }
      90% { opacity: 1; }
      50% { 
        transform: translate(100px, -100px) scale(1.5);
      }
    }
    
    .particle:nth-child(2) { animation-delay: 2s; left: 20%; top: 20%; }
    .particle:nth-child(3) { animation-delay: 4s; left: 40%; top: 60%; }
    .particle:nth-child(4) { animation-delay: 6s; left: 60%; top: 30%; }
    .particle:nth-child(5) { animation-delay: 8s; left: 80%; top: 70%; }
    .particle:nth-child(6) { animation-delay: 10s; left: 30%; top: 80%; }
    .particle:nth-child(7) { animation-delay: 12s; left: 70%; top: 50%; }
    
    /* Hero Section */
    .hero-section {
      position: relative;
      z-index: 10;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 60px 30px;
      text-align: center;
    }
    
    .glitch-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 72px;
      font-weight: 900;
      color: #fff;
      text-transform: uppercase;
      letter-spacing: 8px;
      margin-bottom: 20px;
      position: relative;
      text-shadow: 
        0 0 20px rgba(99, 102, 241, 0.8),
        0 0 40px rgba(99, 102, 241, 0.5),
        0 0 60px rgba(99, 102, 241, 0.3);
      animation: glowPulse 3s ease-in-out infinite;
    }
    
    @keyframes glowPulse {
      0%, 100% { 
        text-shadow: 
          0 0 20px rgba(99, 102, 241, 0.8),
          0 0 40px rgba(99, 102, 241, 0.5),
          0 0 60px rgba(99, 102, 241, 0.3);
      }
      50% { 
        text-shadow: 
          0 0 30px rgba(99, 102, 241, 1),
          0 0 60px rgba(99, 102, 241, 0.8),
          0 0 90px rgba(99, 102, 241, 0.5);
      }
    }
    
    .subtitle {
      font-size: 28px;
      font-weight: 500;
      color: #a5b4fc;
      margin-bottom: 50px;
      letter-spacing: 2px;
      opacity: 0;
      animation: fadeInUp 1s ease-out 0.5s forwards;
    }
    
    @keyframes fadeInUp {
      from {
        opacity: 0;
        transform: translateY(30px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    
    /* World Description Cards */
    .world-card {
      background: linear-gradient(135deg, rgba(30, 41, 59, 0.8) 0%, rgba(15, 23, 42, 0.9) 100%);
      border: 2px solid rgba(99, 102, 241, 0.3);
      border-radius: 20px;
      padding: 40px;
      margin: 30px auto;
      max-width: 1200px;
      backdrop-filter: blur(10px);
      box-shadow: 
        0 10px 40px rgba(0, 0, 0, 0.5),
        inset 0 1px 0 rgba(255, 255, 255, 0.1);
      transition: all 0.4s ease;
      position: relative;
      overflow: hidden;
      opacity: 0;
      animation: fadeInUp 1s ease-out forwards;
    }
    
    .world-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(99, 102, 241, 0.1), transparent);
      transition: left 0.5s ease;
    }
    
    .world-card:hover::before {
      left: 100%;
    }
    
    .world-card:hover {
      transform: translateY(-10px);
      border-color: rgba(99, 102, 241, 0.6);
      box-shadow: 
        0 20px 60px rgba(99, 102, 241, 0.4),
        inset 0 1px 0 rgba(255, 255, 255, 0.2);
    }
    
    .world-card:nth-child(1) { animation-delay: 0.8s; }
    .world-card:nth-child(2) { animation-delay: 1s; }
    .world-card:nth-child(3) { animation-delay: 1.2s; }
    
    .card-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 42px;
      font-weight: 700;
      color: #fff;
      margin-bottom: 25px;
      text-transform: uppercase;
      letter-spacing: 3px;
      text-shadow: 0 0 20px rgba(99, 102, 241, 0.5);
    }
    
    .card-content {
      font-size: 20px;
      line-height: 1.8;
      color: #cbd5e1;
      margin-bottom: 15px;
    }
    
    .feature-icon {
      display: inline-block;
      font-size: 32px;
      margin-right: 15px;
      animation: pulse 2s ease-in-out infinite;
    }
    
    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.1); }
    }
    
    /* Philosophy Section */
    .philosophy-section {
      position: relative;
      z-index: 10;
      padding: 80px 30px;
      background: linear-gradient(180deg, rgba(15, 23, 42, 0) 0%, rgba(15, 23, 42, 0.8) 50%, rgba(15, 23, 42, 0) 100%);
    }
    
    .philosophy-box {
      max-width: 900px;
      margin: 0 auto;
      padding: 50px;
      background: linear-gradient(135deg, rgba(99, 102, 241, 0.1) 0%, rgba(139, 92, 246, 0.1) 100%);
      border: 3px solid rgba(99, 102, 241, 0.4);
      border-radius: 25px;
      text-align: center;
      position: relative;
      overflow: hidden;
      box-shadow: 0 0 50px rgba(99, 102, 241, 0.3);
    }
    
    .philosophy-box::before {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: conic-gradient(from 0deg, transparent, rgba(99, 102, 241, 0.2), transparent 30%);
      animation: rotate 6s linear infinite;
    }
    
    @keyframes rotate {
      100% { transform: rotate(360deg); }
    }
    
    .philosophy-box::after {
      content: '';
      position: absolute;
      inset: 3px;
      background: linear-gradient(135deg, rgba(15, 23, 42, 0.95) 0%, rgba(30, 41, 59, 0.95) 100%);
      border-radius: 22px;
      z-index: -1;
    }
    
    .philosophy-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 36px;
      font-weight: 700;
      color: #fff;
      margin-bottom: 30px;
      text-transform: uppercase;
      letter-spacing: 4px;
      position: relative;
      z-index: 1;
    }
    
    .philosophy-text {
      font-size: 26px;
      line-height: 1.7;
      color: #e0e7ff;
      font-weight: 500;
      position: relative;
      z-index: 1;
      text-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
    }
    
    /* Gameplay Section */
    .gameplay-section {
      position: relative;
      z-index: 10;
      padding: 80px 30px;
      max-width: 1400px;
      margin: 0 auto;
    }
    
    .section-header {
      text-align: center;
      margin-bottom: 60px;
    }
    
    .section-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 56px;
      font-weight: 800;
      color: #fff;
      margin-bottom: 20px;
      text-transform: uppercase;
      letter-spacing: 5px;
      text-shadow: 0 0 30px rgba(99, 102, 241, 0.6);
    }
    
    .section-subtitle {
      font-size: 22px;
      color: #a5b4fc;
      font-weight: 500;
    }
    
    /* Pillar Cards */
    .pillars-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
      gap: 40px;
      margin-bottom: 60px;
    }
    
    .pillar-card {
      background: linear-gradient(135deg, rgba(30, 41, 59, 0.9) 0%, rgba(15, 23, 42, 0.95) 100%);
      border: 2px solid rgba(99, 102, 241, 0.3);
      border-radius: 25px;
      padding: 45px 35px;
      position: relative;
      overflow: hidden;
      transition: all 0.4s ease;
      cursor: pointer;
    }
    
    .pillar-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 5px;
      background: linear-gradient(90deg, #6366f1, #8b5cf6, #6366f1);
      background-size: 200% 100%;
      animation: shimmer 3s linear infinite;
    }
    
    @keyframes shimmer {
      0% { background-position: 200% 0; }
      100% { background-position: -200% 0; }
    }
    
    .pillar-card:hover {
      transform: translateY(-15px) scale(1.02);
      border-color: rgba(99, 102, 241, 0.7);
      box-shadow: 
        0 25px 70px rgba(99, 102, 241, 0.5),
        inset 0 1px 0 rgba(255, 255, 255, 0.2);
    }
    
    .pillar-icon {
      font-size: 64px;
      margin-bottom: 25px;
      display: inline-block;
      animation: bounce 3s ease-in-out infinite;
    }
    
    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-15px); }
    }
    
    .pillar-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 32px;
      font-weight: 700;
      color: #fff;
      margin-bottom: 20px;
      text-transform: uppercase;
      letter-spacing: 2px;
    }
    
    .pillar-description {
      font-size: 18px;
      line-height: 1.7;
      color: #cbd5e1;
      margin-bottom: 25px;
    }
    
    .feature-list {
      list-style: none;
      padding: 0;
    }
    
    .feature-item {
      font-size: 17px;
      color: #a5b4fc;
      margin-bottom: 12px;
      padding-left: 30px;
      position: relative;
      line-height: 1.6;
    }
    
    .feature-item::before {
      content: '▸';
      position: absolute;
      left: 0;
      color: #6366f1;
      font-size: 20px;
      animation: blink 2s ease-in-out infinite;
    }
    
    @keyframes blink {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.3; }
    }
    
    /* Evolution System Section */
    .evolution-system-section {
      margin-top: 80px;
      padding: 70px 40px;
      background: linear-gradient(135deg, rgba(168, 85, 247, 0.08) 0%, rgba(147, 51, 234, 0.12) 100%);
      border-radius: 35px;
      border: 3px solid rgba(168, 85, 247, 0.4);
      position: relative;
      overflow: hidden;
      box-shadow: 0 0 60px rgba(168, 85, 247, 0.3);
    }
    
    .evolution-system-section::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 200%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(168, 85, 247, 0.15), transparent);
      animation: warningSlide 5s linear infinite;
    }
    
    .evolution-header {
      text-align: center;
      margin-bottom: 60px;
      position: relative;
      z-index: 1;
    }
    
    .evolution-icon-large {
      font-size: 96px;
      display: inline-block;
      margin-bottom: 30px;
      animation: dnaRotate 4s ease-in-out infinite;
      filter: drop-shadow(0 0 30px rgba(168, 85, 247, 0.8));
    }
    
    @keyframes dnaRotate {
      0%, 100% { transform: rotate(0deg) scale(1); }
      25% { transform: rotate(-10deg) scale(1.1); }
      75% { transform: rotate(10deg) scale(1.1); }
    }
    
    .evolution-main-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 56px;
      font-weight: 900;
      color: #fff;
      text-transform: uppercase;
      letter-spacing: 5px;
      margin-bottom: 25px;
      text-shadow: 0 0 30px rgba(168, 85, 247, 0.8);
      position: relative;
      z-index: 1;
    }
    
    .evolution-tagline {
      font-size: 28px;
      color: #e9d5ff;
      font-weight: 600;
      line-height: 1.6;
      max-width: 900px;
      margin: 0 auto 20px;
      position: relative;
      z-index: 1;
    }
    
    .evolution-tagline .highlight-evolution {
      color: #fff;
      font-size: 32px;
      display: block;
      margin-top: 15px;
      text-shadow: 0 0 20px rgba(168, 85, 247, 0.7);
    }
    
    .mutation-paths-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
      gap: 40px;
      margin-bottom: 60px;
      position: relative;
      z-index: 1;
    }
    
    .mutation-card {
      background: linear-gradient(135deg, rgba(20, 30, 48, 0.95) 0%, rgba(10, 15, 30, 0.98) 100%);
      border: 3px solid rgba(168, 85, 247, 0.5);
      border-radius: 25px;
      padding: 45px 35px;
      text-align: center;
      transition: all 0.5s ease;
      cursor: pointer;
      position: relative;
      overflow: hidden;
    }
    
    .mutation-card::before {
      content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      width: 0;
      height: 0;
      background: radial-gradient(circle, rgba(168, 85, 247, 0.2) 0%, transparent 70%);
      transform: translate(-50%, -50%);
      transition: width 0.6s ease, height 0.6s ease;
      border-radius: 50%;
    }
    
    .mutation-card:hover::before {
      width: 500px;
      height: 500px;
    }
    
    .mutation-card:hover {
      transform: translateY(-15px) scale(1.05);
      border-color: rgba(168, 85, 247, 0.9);
      box-shadow: 0 25px 70px rgba(168, 85, 247, 0.6);
    }
    
    .mutation-icon {
      font-size: 72px;
      margin-bottom: 30px;
      display: inline-block;
      filter: drop-shadow(0 0 20px rgba(168, 85, 247, 0.7));
      animation: mutationPulse 3s ease-in-out infinite;
      position: relative;
      z-index: 1;
    }
    
    @keyframes mutationPulse {
      0%, 100% { 
        transform: scale(1);
        filter: drop-shadow(0 0 20px rgba(168, 85, 247, 0.7));
      }
      50% { 
        transform: scale(1.15);
        filter: drop-shadow(0 0 35px rgba(168, 85, 247, 1));
      }
    }
    
    .mutation-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 32px;
      font-weight: 800;
      color: #fff;
      margin-bottom: 20px;
      text-transform: uppercase;
      letter-spacing: 2px;
      text-shadow: 0 0 20px rgba(168, 85, 247, 0.7);
      position: relative;
      z-index: 1;
    }
    
    .mutation-description {
      font-size: 19px;
      color: #e9d5ff;
      line-height: 1.7;
      margin-bottom: 25px;
      position: relative;
      z-index: 1;
    }
    
    .mutation-examples {
      list-style: none;
      padding: 0;
      margin-top: 25px;
      position: relative;
      z-index: 1;
    }
    
    .mutation-examples li {
      font-size: 17px;
      color: #d8b4fe;
      margin-bottom: 12px;
      padding-left: 30px;
      position: relative;
      text-align: left;
      line-height: 1.6;
    }
    
    .mutation-examples li::before {
      content: '◆';
      position: absolute;
      left: 0;
      color: #a855f7;
      font-size: 18px;
      animation: blink 2.5s ease-in-out infinite;
    }
    
    .humanity-cost-box {
      background: linear-gradient(135deg, rgba(239, 68, 68, 0.2) 0%, rgba(220, 38, 38, 0.2) 100%);
      border: 3px solid rgba(239, 68, 68, 0.6);
      border-radius: 25px;
      padding: 60px 50px;
      text-align: center;
      position: relative;
      overflow: hidden;
      box-shadow: 0 0 50px rgba(239, 68, 68, 0.4);
      margin-top: 60px;
    }
    
    .humanity-cost-box::before {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: conic-gradient(from 0deg, transparent, rgba(239, 68, 68, 0.3), transparent 30%);
      animation: rotate 10s linear infinite;
    }
    
    .humanity-cost-box::after {
      content: '';
      position: absolute;
      inset: 3px;
      background: linear-gradient(135deg, rgba(15, 23, 42, 0.98) 0%, rgba(20, 30, 48, 0.98) 100%);
      border-radius: 22px;
      z-index: 0;
    }
    
    .humanity-icon {
      font-size: 96px;
      margin-bottom: 30px;
      display: inline-block;
      animation: humanityFade 4s ease-in-out infinite;
      filter: drop-shadow(0 0 25px rgba(239, 68, 68, 0.8));
      position: relative;
      z-index: 1;
    }
    
    @keyframes humanityFade {
      0%, 100% { 
        opacity: 1;
        transform: scale(1);
      }
      50% { 
        opacity: 0.6;
        transform: scale(0.95);
      }
    }
    
    .humanity-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 48px;
      font-weight: 900;
      color: #fff;
      text-transform: uppercase;
      letter-spacing: 4px;
      margin-bottom: 30px;
      text-shadow: 0 0 30px rgba(239, 68, 68, 0.8);
      position: relative;
      z-index: 1;
    }
    
    .humanity-progression {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 40px;
      margin-bottom: 40px;
      flex-wrap: wrap;
      position: relative;
      z-index: 1;
    }
    
    .humanity-stage {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 15px;
    }
    
    .humanity-stage-icon {
      font-size: 56px;
      filter: drop-shadow(0 0 15px rgba(239, 68, 68, 0.6));
    }
    
    .humanity-stage-label {
      font-family: 'Orbitron', sans-serif;
      font-size: 20px;
      font-weight: 700;
      color: #fca5a5;
      text-transform: uppercase;
      letter-spacing: 1px;
    }
    
    .humanity-arrow {
      font-size: 48px;
      color: #ef4444;
      animation: arrowPulse 2s ease-in-out infinite;
    }
    
    .humanity-warning {
      font-size: 26px;
      color: #fecaca;
      line-height: 1.8;
      font-weight: 600;
      margin-top: 30px;
      position: relative;
      z-index: 1;
    }
    
    .humanity-warning strong {
      display: block;
      font-size: 32px;
      color: #fff;
      margin-top: 20px;
      text-shadow: 0 0 25px rgba(239, 68, 68, 0.9);
    }

    /* Ecosystem Survival Section */
    .ecosystem-survival-section {
      margin-top: 100px;
      padding: 80px 40px;
      background: linear-gradient(135deg, rgba(34, 197, 94, 0.06) 0%, rgba(22, 163, 74, 0.1) 50%, rgba(16, 185, 129, 0.06) 100%);
      border-radius: 40px;
      border: 3px solid rgba(34, 197, 94, 0.4);
      position: relative;
      overflow: hidden;
      box-shadow: 0 0 80px rgba(34, 197, 94, 0.2);
    }
    
    .ecosystem-survival-section::before {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: conic-gradient(from 0deg, transparent, rgba(34, 197, 94, 0.08), transparent 40%);
      animation: rotate 15s linear infinite;
    }
    
    .ecosystem-header {
      text-align: center;
      margin-bottom: 70px;
      position: relative;
      z-index: 1;
    }
    
    .ecosystem-badge {
      display: inline-block;
      background: linear-gradient(135deg, rgba(34, 197, 94, 0.3) 0%, rgba(22, 163, 74, 0.3) 100%);
      border: 2px solid rgba(34, 197, 94, 0.6);
      border-radius: 50px;
      padding: 15px 40px;
      margin-bottom: 30px;
      font-family: 'Orbitron', sans-serif;
      font-size: 22px;
      font-weight: 700;
      color: #6ee7b7;
      text-transform: uppercase;
      letter-spacing: 3px;
      box-shadow: 0 0 30px rgba(34, 197, 94, 0.3);
    }
    
    .ecosystem-main-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 64px;
      font-weight: 900;
      color: #fff;
      text-transform: uppercase;
      letter-spacing: 6px;
      margin-bottom: 30px;
      text-shadow: 0 0 40px rgba(34, 197, 94, 0.8);
    }
    
    .ecosystem-subtitle {
      font-size: 30px;
      color: #a7f3d0;
      font-weight: 600;
      line-height: 1.6;
      max-width: 1000px;
      margin: 0 auto 25px;
    }
    
    .ecosystem-subtitle strong {
      color: #fff;
      font-size: 34px;
      display: block;
      margin-top: 20px;
      text-shadow: 0 0 25px rgba(34, 197, 94, 0.7);
    }
    
    .dynamic-eco-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
      gap: 45px;
      margin-bottom: 70px;
      position: relative;
      z-index: 1;
    }
    
    .eco-card {
      background: linear-gradient(135deg, rgba(20, 30, 48, 0.95) 0%, rgba(10, 20, 35, 0.98) 100%);
      border: 3px solid rgba(34, 197, 94, 0.5);
      border-radius: 30px;
      padding: 50px 40px;
      text-align: center;
      transition: all 0.5s ease;
      cursor: pointer;
      position: relative;
      overflow: hidden;
    }
    
    .eco-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle at center, rgba(34, 197, 94, 0.15) 0%, transparent 70%);
      opacity: 0;
      transition: opacity 0.5s ease;
    }
    
    .eco-card:hover::before {
      opacity: 1;
    }
    
    .eco-card:hover {
      transform: translateY(-18px) scale(1.03);
      border-color: rgba(34, 197, 94, 0.9);
      box-shadow: 0 30px 80px rgba(34, 197, 94, 0.5);
    }
    
    .eco-icon {
      font-size: 80px;
      margin-bottom: 35px;
      display: inline-block;
      filter: drop-shadow(0 0 25px rgba(34, 197, 94, 0.8));
      animation: ecoFloat 4s ease-in-out infinite;
      position: relative;
      z-index: 1;
    }
    
    @keyframes ecoFloat {
      0%, 100% { 
        transform: translateY(0) rotate(0deg);
      }
      25% { 
        transform: translateY(-10px) rotate(-3deg);
      }
      75% { 
        transform: translateY(-10px) rotate(3deg);
      }
    }
    
    .eco-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 34px;
      font-weight: 800;
      color: #fff;
      margin-bottom: 25px;
      text-transform: uppercase;
      letter-spacing: 2px;
      text-shadow: 0 0 20px rgba(34, 197, 94, 0.6);
      position: relative;
      z-index: 1;
    }
    
    .eco-description {
      font-size: 20px;
      color: #d1fae5;
      line-height: 1.8;
      margin-bottom: 30px;
      position: relative;
      z-index: 1;
    }
    
    .eco-examples {
      list-style: none;
      padding: 0;
      margin: 0;
      position: relative;
      z-index: 1;
    }
    
    .eco-examples li {
      font-size: 18px;
      color: #a7f3d0;
      margin-bottom: 15px;
      padding-left: 35px;
      position: relative;
      text-align: left;
      line-height: 1.7;
    }
    
    .eco-examples li::before {
      content: '🌿';
      position: absolute;
      left: 0;
      font-size: 20px;
      animation: pulse 2s ease-in-out infinite;
    }
    
    .chain-reaction-box {
      background: linear-gradient(135deg, rgba(239, 68, 68, 0.15) 0%, rgba(220, 38, 38, 0.2) 100%);
      border: 4px solid rgba(239, 68, 68, 0.6);
      border-radius: 35px;
      padding: 70px 60px;
      text-align: center;
      position: relative;
      overflow: hidden;
      box-shadow: 0 0 60px rgba(239, 68, 68, 0.4);
      margin-bottom: 70px;
    }
    
    .chain-reaction-box::before {
      content: '';
      position: absolute;
      top: -100%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: conic-gradient(from 0deg, transparent, rgba(239, 68, 68, 0.2), transparent 20%);
      animation: rotate 12s linear infinite;
    }
    
    .chain-reaction-box::after {
      content: '';
      position: absolute;
      inset: 4px;
      background: linear-gradient(135deg, rgba(15, 23, 42, 0.98) 0%, rgba(20, 30, 48, 0.98) 100%);
      border-radius: 31px;
      z-index: 0;
    }
    
    .chain-icon {
      font-size: 100px;
      margin-bottom: 35px;
      display: inline-block;
      animation: chainShake 3s ease-in-out infinite;
      filter: drop-shadow(0 0 30px rgba(239, 68, 68, 0.8));
      position: relative;
      z-index: 1;
    }
    
    @keyframes chainShake {
      0%, 100% { transform: rotate(0deg); }
      10%, 30% { transform: rotate(-8deg); }
      20%, 40% { transform: rotate(8deg); }
      50%, 100% { transform: rotate(0deg); }
    }
    
    .chain-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 52px;
      font-weight: 900;
      color: #fff;
      text-transform: uppercase;
      letter-spacing: 4px;
      margin-bottom: 35px;
      text-shadow: 0 0 35px rgba(239, 68, 68, 0.8);
      position: relative;
      z-index: 1;
    }
    
    .chain-description {
      font-size: 28px;
      color: #fecaca;
      line-height: 1.8;
      font-weight: 600;
      max-width: 1000px;
      margin: 0 auto;
      position: relative;
      z-index: 1;
    }
    
    .chain-description strong {
      display: block;
      font-size: 34px;
      color: #fff;
      margin-top: 30px;
      text-shadow: 0 0 30px rgba(239, 68, 68, 0.9);
    }
    
    .environmental-factors-section {
      background: linear-gradient(135deg, rgba(99, 102, 241, 0.08) 0%, rgba(79, 70, 229, 0.12) 100%);
      border: 3px solid rgba(99, 102, 241, 0.4);
      border-radius: 35px;
      padding: 70px 50px;
      position: relative;
      overflow: hidden;
    }
    
    .env-header {
      text-align: center;
      margin-bottom: 60px;
      position: relative;
      z-index: 1;
    }
    
    .env-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 56px;
      font-weight: 900;
      color: #fff;
      text-transform: uppercase;
      letter-spacing: 5px;
      margin-bottom: 25px;
      text-shadow: 0 0 35px rgba(99, 102, 241, 0.8);
    }
    
    .env-subtitle {
      font-size: 26px;
      color: #c7d2fe;
      font-weight: 600;
      line-height: 1.7;
    }
    
    .env-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 40px;
      position: relative;
      z-index: 1;
    }
    
    .env-factor-card {
      background: linear-gradient(135deg, rgba(30, 41, 59, 0.9) 0%, rgba(15, 23, 42, 0.95) 100%);
      border: 2px solid rgba(99, 102, 241, 0.4);
      border-radius: 25px;
      padding: 45px 35px;
      text-align: center;
      transition: all 0.4s ease;
      position: relative;
      overflow: hidden;
    }
    
    .env-factor-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(99, 102, 241, 0.15), transparent);
      transition: left 0.5s ease;
    }
    
    .env-factor-card:hover::before {
      left: 100%;
    }
    
    .env-factor-card:hover {
      transform: translateY(-12px);
      border-color: rgba(99, 102, 241, 0.7);
      box-shadow: 0 20px 60px rgba(99, 102, 241, 0.5);
    }
    
    .env-icon {
      font-size: 72px;
      margin-bottom: 30px;
      display: inline-block;
      filter: drop-shadow(0 0 20px rgba(99, 102, 241, 0.7));
      position: relative;
      z-index: 1;
    }
    
    .env-factor-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 30px;
      font-weight: 800;
      color: #fff;
      margin-bottom: 20px;
      text-transform: uppercase;
      letter-spacing: 2px;
      text-shadow: 0 0 15px rgba(99, 102, 241, 0.6);
      position: relative;
      z-index: 1;
    }
    
    .env-factor-effect {
      font-size: 19px;
      color: #c7d2fe;
      line-height: 1.8;
      position: relative;
      z-index: 1;
    }
    
    .final-message-box {
      margin-top: 70px;
      background: linear-gradient(135deg, rgba(168, 85, 247, 0.15) 0%, rgba(147, 51, 234, 0.2) 100%);
      border: 4px solid rgba(168, 85, 247, 0.6);
      border-radius: 35px;
      padding: 70px 60px;
      text-align: center;
      position: relative;
      overflow: hidden;
      box-shadow: 0 0 70px rgba(168, 85, 247, 0.4);
    }
    
    .final-message-box::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 200%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(168, 85, 247, 0.2), transparent);
      animation: warningSlide 6s linear infinite;
    }
    
    .final-icon {
      font-size: 96px;
      margin-bottom: 35px;
      display: inline-block;
      animation: pulse 3s ease-in-out infinite;
      filter: drop-shadow(0 0 30px rgba(168, 85, 247, 0.9));
      position: relative;
      z-index: 1;
    }
    
    .final-text {
      font-family: 'Orbitron', sans-serif;
      font-size: 42px;
      font-weight: 900;
      color: #fff;
      text-transform: uppercase;
      letter-spacing: 4px;
      line-height: 1.6;
      text-shadow: 0 0 40px rgba(168, 85, 247, 0.9);
      position: relative;
      z-index: 1;
    }

    /* Adaptive Combat Section */
    .adaptive-combat-section {
      margin-top: 80px;
      padding: 60px 40px;
      background: linear-gradient(135deg, rgba(239, 68, 68, 0.05) 0%, rgba(220, 38, 38, 0.08) 100%);
      border-radius: 30px;
      border: 2px solid rgba(239, 68, 68, 0.3);
      position: relative;
      overflow: hidden;
    }
    
    .adaptive-combat-section::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 200%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(239, 68, 68, 0.1), transparent);
      animation: warningSlide 4s linear infinite;
    }
    
    .adaptive-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 48px;
      font-weight: 800;
      color: #fff;
      text-align: center;
      margin-bottom: 25px;
      text-transform: uppercase;
      letter-spacing: 4px;
      text-shadow: 0 0 25px rgba(239, 68, 68, 0.6);
      position: relative;
      z-index: 1;
    }
    
    .adaptive-intro {
      text-align: center;
      font-size: 24px;
      color: #fca5a5;
      margin-bottom: 50px;
      font-weight: 500;
      position: relative;
      z-index: 1;
    }
    
    .adaptive-intro strong {
      color: #fff;
      text-shadow: 0 0 15px rgba(239, 68, 68, 0.5);
    }
    
    .evolution-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
      gap: 35px;
      margin-bottom: 50px;
      position: relative;
      z-index: 1;
    }
    
    .evolution-card {
      background: linear-gradient(135deg, rgba(20, 30, 48, 0.95) 0%, rgba(10, 15, 30, 0.98) 100%);
      border: 2px solid rgba(239, 68, 68, 0.4);
      border-radius: 20px;
      padding: 40px 30px;
      text-align: center;
      transition: all 0.4s ease;
      cursor: pointer;
      position: relative;
      overflow: hidden;
    }
    
    .evolution-card::before {
      content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      width: 0;
      height: 0;
      background: radial-gradient(circle, rgba(239, 68, 68, 0.15) 0%, transparent 70%);
      transform: translate(-50%, -50%);
      transition: width 0.5s ease, height 0.5s ease;
      border-radius: 50%;
    }
    
    .evolution-card:hover::before {
      width: 400px;
      height: 400px;
    }
    
    .evolution-card:hover {
      transform: translateY(-12px) scale(1.03);
      border-color: rgba(239, 68, 68, 0.8);
      box-shadow: 0 20px 60px rgba(239, 68, 68, 0.5);
    }
    
    .evolution-icon {
      font-size: 64px;
      margin-bottom: 25px;
      display: inline-block;
      filter: drop-shadow(0 0 15px rgba(239, 68, 68, 0.6));
      animation: pulse 3s ease-in-out infinite;
      position: relative;
      z-index: 1;
    }
    
    .evolution-trigger {
      font-family: 'Orbitron', sans-serif;
      font-size: 26px;
      font-weight: 700;
      color: #fca5a5;
      margin-bottom: 20px;
      text-transform: uppercase;
      letter-spacing: 1px;
      position: relative;
      z-index: 1;
    }
    
    .evolution-arrow {
      font-size: 48px;
      color: #ef4444;
      margin: 20px 0;
      animation: arrowPulse 2s ease-in-out infinite;
      position: relative;
      z-index: 1;
    }
    
    @keyframes arrowPulse {
      0%, 100% { 
        transform: scale(1);
        opacity: 0.7;
      }
      50% { 
        transform: scale(1.2);
        opacity: 1;
      }
    }
    
    .evolution-result {
      font-family: 'Orbitron', sans-serif;
      font-size: 28px;
      font-weight: 800;
      color: #fff;
      margin-bottom: 15px;
      text-transform: uppercase;
      letter-spacing: 2px;
      text-shadow: 0 0 20px rgba(239, 68, 68, 0.7);
      position: relative;
      z-index: 1;
    }
    
    .evolution-desc {
      font-size: 17px;
      color: #cbd5e1;
      line-height: 1.6;
      position: relative;
      z-index: 1;
    }
    
    .world-learns-box {
      background: linear-gradient(135deg, rgba(239, 68, 68, 0.15) 0%, rgba(220, 38, 38, 0.15) 100%);
      border: 3px solid rgba(239, 68, 68, 0.5);
      border-radius: 25px;
      padding: 50px 40px;
      text-align: center;
      position: relative;
      overflow: hidden;
      box-shadow: 0 0 40px rgba(239, 68, 68, 0.3);
    }
    
    .world-learns-box::before {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: conic-gradient(from 0deg, transparent, rgba(239, 68, 68, 0.2), transparent 30%);
      animation: rotate 8s linear infinite;
    }
    
    .world-learns-box::after {
      content: '';
      position: absolute;
      inset: 3px;
      background: linear-gradient(135deg, rgba(15, 23, 42, 0.97) 0%, rgba(20, 30, 48, 0.97) 100%);
      border-radius: 22px;
      z-index: 0;
    }
    
    .learns-icon {
      font-size: 80px;
      margin-bottom: 25px;
      display: inline-block;
      animation: brainPulse 3s ease-in-out infinite;
      filter: drop-shadow(0 0 20px rgba(239, 68, 68, 0.6));
      position: relative;
      z-index: 1;
    }
    
    @keyframes brainPulse {
      0%, 100% { 
        transform: scale(1) rotate(0deg);
      }
      25% { 
        transform: scale(1.1) rotate(-5deg);
      }
      75% { 
        transform: scale(1.1) rotate(5deg);
      }
    }
    
    .learns-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 42px;
      font-weight: 800;
      color: #fff;
      margin-bottom: 25px;
      text-transform: uppercase;
      letter-spacing: 3px;
      text-shadow: 0 0 25px rgba(239, 68, 68, 0.7);
      position: relative;
      z-index: 1;
    }
    
    .learns-text {
      font-size: 24px;
      color: #fca5a5;
      line-height: 1.8;
      font-weight: 500;
      position: relative;
      z-index: 1;
    }
    
    .learns-text .highlight-text {
      color: #fff;
      font-weight: 700;
      text-shadow: 0 0 15px rgba(239, 68, 68, 0.6);
    }
    
    .learns-text strong {
      display: block;
      margin-top: 20px;
      font-size: 28px;
      color: #fff;
      text-shadow: 0 0 20px rgba(239, 68, 68, 0.8);
    }
    
    /* Enemy Showcase */
    .enemy-showcase {
      margin-top: 80px;
      padding: 60px 40px;
      background: linear-gradient(135deg, rgba(99, 102, 241, 0.05) 0%, rgba(139, 92, 246, 0.05) 100%);
      border-radius: 30px;
      border: 2px solid rgba(99, 102, 241, 0.2);
    }
    
    .showcase-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 48px;
      font-weight: 800;
      color: #fff;
      text-align: center;
      margin-bottom: 50px;
      text-transform: uppercase;
      letter-spacing: 4px;
      text-shadow: 0 0 25px rgba(99, 102, 241, 0.5);
    }
    
    .enemy-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 30px;
    }
    
    .enemy-card {
      background: linear-gradient(135deg, rgba(20, 30, 48, 0.9) 0%, rgba(10, 15, 30, 0.95) 100%);
      border: 2px solid rgba(239, 68, 68, 0.4);
      border-radius: 20px;
      padding: 30px 25px;
      text-align: center;
      transition: all 0.3s ease;
      cursor: pointer;
      position: relative;
      overflow: hidden;
    }
    
    .enemy-card::before {
      content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      width: 0;
      height: 0;
      background: radial-gradient(circle, rgba(239, 68, 68, 0.2) 0%, transparent 70%);
      transform: translate(-50%, -50%);
      transition: width 0.4s ease, height 0.4s ease;
      border-radius: 50%;
    }
    
    .enemy-card:hover::before {
      width: 300px;
      height: 300px;
    }
    
    .enemy-card:hover {
      transform: translateY(-10px);
      border-color: rgba(239, 68, 68, 0.7);
      box-shadow: 0 15px 50px rgba(239, 68, 68, 0.4);
    }
    
    .enemy-icon {
      font-size: 56px;
      margin-bottom: 20px;
      display: inline-block;
      filter: drop-shadow(0 0 10px rgba(239, 68, 68, 0.5));
      position: relative;
      z-index: 1;
    }
    
    .enemy-name {
      font-family: 'Orbitron', sans-serif;
      font-size: 24px;
      font-weight: 700;
      color: #fff;
      margin-bottom: 15px;
      text-transform: uppercase;
      letter-spacing: 1px;
      position: relative;
      z-index: 1;
    }
    
    .enemy-desc {
      font-size: 16px;
      color: #cbd5e1;
      line-height: 1.6;
      position: relative;
      z-index: 1;
    }
    
    .threat-level {
      display: inline-block;
      margin-top: 15px;
      padding: 8px 20px;
      background: rgba(239, 68, 68, 0.2);
      border: 1px solid rgba(239, 68, 68, 0.5);
      border-radius: 20px;
      font-size: 14px;
      font-weight: 600;
      color: #fca5a5;
      text-transform: uppercase;
      letter-spacing: 1px;
      position: relative;
      z-index: 1;
    }
    
    /* Warning Message */
    .warning-section {
      margin-top: 80px;
      padding: 50px 40px;
      background: linear-gradient(135deg, rgba(239, 68, 68, 0.1) 0%, rgba(220, 38, 38, 0.1) 100%);
      border: 3px solid rgba(239, 68, 68, 0.4);
      border-radius: 25px;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    
    .warning-section::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 200%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(239, 68, 68, 0.1), transparent);
      animation: warningSlide 3s linear infinite;
    }
    
    @keyframes warningSlide {
      0% { left: -100%; }
      100% { left: 100%; }
    }
    
    .warning-icon {
      font-size: 72px;
      margin-bottom: 25px;
      display: inline-block;
      animation: warningPulse 2s ease-in-out infinite;
    }
    
    @keyframes warningPulse {
      0%, 100% { 
        transform: scale(1);
        filter: drop-shadow(0 0 10px rgba(239, 68, 68, 0.5));
      }
      50% { 
        transform: scale(1.15);
        filter: drop-shadow(0 0 25px rgba(239, 68, 68, 0.8));
      }
    }
    
    .warning-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 40px;
      font-weight: 800;
      color: #fca5a5;
      margin-bottom: 20px;
      text-transform: uppercase;
      letter-spacing: 3px;
      text-shadow: 0 0 20px rgba(239, 68, 68, 0.6);
      position: relative;
      z-index: 1;
    }
    
    .warning-text {
      font-size: 24px;
      color: #fecaca;
      line-height: 1.7;
      font-weight: 500;
      position: relative;
      z-index: 1;
    }
    
    /* Survival Tips */
    .tips-section {
      margin-top: 80px;
      padding: 60px 40px;
      background: linear-gradient(135deg, rgba(34, 197, 94, 0.05) 0%, rgba(22, 163, 74, 0.05) 100%);
      border-radius: 30px;
      border: 2px solid rgba(34, 197, 94, 0.3);
    }
    
    .tips-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 48px;
      font-weight: 800;
      color: #fff;
      text-align: center;
      margin-bottom: 50px;
      text-transform: uppercase;
      letter-spacing: 4px;
      text-shadow: 0 0 25px rgba(34, 197, 94, 0.5);
    }
    
    .tips-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 30px;
    }
    
    .tip-card {
      background: linear-gradient(135deg, rgba(20, 30, 48, 0.8) 0%, rgba(10, 15, 30, 0.9) 100%);
      border: 2px solid rgba(34, 197, 94, 0.3);
      border-radius: 20px;
      padding: 35px 30px;
      transition: all 0.3s ease;
      cursor: pointer;
      position: relative;
      overflow: hidden;
    }
    
    .tip-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(34, 197, 94, 0.1), transparent);
      transition: left 0.5s ease;
    }
    
    .tip-card:hover::before {
      left: 100%;
    }
    
    .tip-card:hover {
      transform: translateY(-8px);
      border-color: rgba(34, 197, 94, 0.6);
      box-shadow: 0 15px 50px rgba(34, 197, 94, 0.3);
    }
    
    .tip-number {
      font-family: 'Orbitron', sans-serif;
      font-size: 48px;
      font-weight: 900;
      color: rgba(34, 197, 94, 0.3);
      margin-bottom: 20px;
    }
    
    .tip-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 26px;
      font-weight: 700;
      color: #fff;
      margin-bottom: 15px;
      text-transform: uppercase;
      letter-spacing: 1px;
    }
    
    .tip-description {
      font-size: 17px;
      color: #cbd5e1;
      line-height: 1.7;
    }
    
    /* Stats Display */
    .stats-section {
      margin-top: 80px;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 30px;
    }
    
    .stat-box {
      background: linear-gradient(135deg, rgba(99, 102, 241, 0.1) 0%, rgba(139, 92, 246, 0.1) 100%);
      border: 2px solid rgba(99, 102, 241, 0.3);
      border-radius: 20px;
      padding: 35px 25px;
      text-align: center;
      position: relative;
      overflow: hidden;
      transition: all 0.3s ease;
    }
    
    .stat-box::before {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 0;
      background: linear-gradient(180deg, transparent, rgba(99, 102, 241, 0.2));
      transition: height 0.3s ease;
    }
    
    .stat-box:hover::before {
      height: 100%;
    }
    
    .stat-box:hover {
      transform: translateY(-8px);
      border-color: rgba(99, 102, 241, 0.6);
      box-shadow: 0 15px 40px rgba(99, 102, 241, 0.3);
    }
    
    .stat-icon {
      font-size: 48px;
      margin-bottom: 20px;
      display: inline-block;
      position: relative;
      z-index: 1;
    }
    
    .stat-value {
      font-family: 'Orbitron', sans-serif;
      font-size: 42px;
      font-weight: 900;
      color: #fff;
      margin-bottom: 10px;
      text-shadow: 0 0 15px rgba(99, 102, 241, 0.5);
      position: relative;
      z-index: 1;
    }
    
    .stat-label {
      font-size: 18px;
      color: #a5b4fc;
      text-transform: uppercase;
      letter-spacing: 1px;
      font-weight: 600;
      position: relative;
      z-index: 1;
    }
    
    /* Footer */
    .footer-section {
      margin-top: 100px;
      padding: 50px 30px;
      text-align: center;
      background: linear-gradient(180deg, transparent 0%, rgba(15, 23, 42, 0.5) 100%);
      border-top: 2px solid rgba(99, 102, 241, 0.2);
    }
    
    .footer-text {
      font-family: 'Orbitron', sans-serif;
      font-size: 20px;
      color: #64748b;
      letter-spacing: 2px;
      text-transform: uppercase;
    }
    
    .footer-highlight {
      color: #6366f1;
      font-weight: 700;
      text-shadow: 0 0 10px rgba(99, 102, 241, 0.5);
    }
    
    /* Responsive Design */
    @media (max-width: 768px) {
      .glitch-title {
        font-size: 42px;
        letter-spacing: 4px;
      }
      
      .subtitle {
        font-size: 20px;
      }
      
      .card-title {
        font-size: 32px;
      }
      
      .card-content {
        font-size: 18px;
      }
      
      .section-title {
        font-size: 40px;
      }
      
      .pillar-title {
        font-size: 26px;
      }
      
      .showcase-title {
        font-size: 36px;
      }
      
      .adaptive-title {
        font-size: 32px;
      }
      
      .adaptive-intro {
        font-size: 20px;
      }
      
      .evolution-trigger {
        font-size: 22px;
      }
      
      .evolution-result {
        font-size: 24px;
      }
      
      .learns-title {
        font-size: 32px;
      }
      
      .learns-text {
        font-size: 20px;
      }
      
      .learns-text strong {
        font-size: 24px;
      }
      
      .pillars-grid {
        grid-template-columns: 1fr;
      }
      
      .evolution-grid {
        grid-template-columns: 1fr;
      }
      
      .enemy-grid {
        grid-template-columns: 1fr;
      }
      
      .tips-grid {
        grid-template-columns: 1fr;
      }
      
      .stats-section {
        grid-template-columns: 1fr;
      }
    }
    
    /* Scrollbar Styling */
    .app-container::-webkit-scrollbar {
      width: 12px;
    }
    
    .app-container::-webkit-scrollbar-track {
      background: rgba(15, 23, 42, 0.5);
    }
    
    .app-container::-webkit-scrollbar-thumb {
      background: linear-gradient(180deg, #6366f1, #8b5cf6);
      border-radius: 6px;
      border: 2px solid rgba(15, 23, 42, 0.5);
    }
    
    .app-container::-webkit-scrollbar-thumb:hover {
      background: linear-gradient(180deg, #7c3aed, #a855f7);
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full"><!-- Animated Background -->
  <div class="bg-circuit"></div><!-- Floating Particles -->
  <div class="particle" style="left: 10%; top: 10%;"></div>
  <div class="particle"></div>
  <div class="particle"></div>
  <div class="particle"></div>
  <div class="particle"></div>
  <div class="particle"></div>
  <div class="particle"></div><!-- Main Container -->
  <div class="app-container"><!-- Hero Section -->
   <section class="hero-section">
    <h1 class="glitch-title" id="world-title">BIO-TECH SURVIVAL WORLD</h1>
    <p class="subtitle" id="world-subtitle">Nơi thiên nhiên và công nghệ hòa làm một</p><!-- World Description Cards -->
    <div style="width: 100%; max-width: 1200px;">
     <div class="world-card">
      <h2 class="card-title">🌲 Rừng Phát Sáng</h2>
      <p class="card-content">Những cánh rừng không còn là sinh vật đơn thuần — chúng là mạch điện sống, phát sáng như mạng lưới năng lượng khổng lồ. Mỗi cây cối là một nút kết nối trong hệ thống sinh học tiên tiến.</p>
     </div>
     <div class="world-card">
      <h2 class="card-title">⚡ Động Vật Lõi Năng Lượng</h2>
      <p class="card-content">Sinh vật trên hành tinh này không chỉ săn mồi để sinh tồn — chúng mang theo lõi năng lượng bio-tech, có khả năng thích nghi và tiến hóa trong thời gian thực. Mỗi cuộc chạm trán là một thử thách sinh tử.</p>
     </div>
     <div class="world-card">
      <h2 class="card-title">🌌 Bầu Trời Dữ Liệu</h2>
      <p class="card-content">Bầu trời không còn là khoảng không tĩnh lặng — nó là một mạng lưới dữ liệu sống, nơi thông tin chảy như dòng điện. Hành tinh đang tự cảm nhận, tự suy nghĩ, và tự quyết định số phận của mọi sinh vật.</p>
     </div>
    </div>
   </section><!-- Philosophy Section -->
   <section class="philosophy-section">
    <div class="philosophy-box">
     <h2 class="philosophy-title">Triết Lý Nền</h2>
     <p class="philosophy-text" id="philosophy-text">Sinh tồn không phải đánh bại thiên nhiên<br>
       mà là học cách không bị nó xóa bỏ<br><br><strong>Thế giới không ghét bạn.<br>
        Nó chỉ đang cố sửa lỗi… và bạn là lỗi đó.</strong></p>
    </div>
   </section><!-- Gameplay Section -->
   <section class="gameplay-section">
    <div class="section-header">
     <h2 class="section-title">GAMEPLAY CỐT LÕI</h2>
     <p class="section-subtitle">Sinh Tồn - Chiến Đấu - Chế Tạo</p>
    </div><!-- Three Pillars -->
    <div class="pillars-grid"><!-- Exploration Pillar -->
     <div class="pillar-card">
      <div class="pillar-icon">
       🧭
      </div>
      <h3 class="pillar-title" id="exploration-title">Khám Phá</h3>
      <p class="pillar-description">Bản đồ thay đổi theo chu kỳ sinh học của hành tinh. Không có gì cố định — mọi thứ đều sống và biến đổi.</p>
      <ul class="feature-list">
       <li class="feature-item">Rừng mọc lên trong vài phút</li>
       <li class="feature-item">Sông đổi hướng chảy</li>
       <li class="feature-item">Địa hình tự tái cấu trúc</li>
       <li class="feature-item">Thành phố bị nuốt chửng</li>
       <li class="feature-item">Học cách đọc chuyển động của thế giới</li>
      </ul>
     </div><!-- Combat Pillar -->
     <div class="pillar-card">
      <div class="pillar-icon">
       ⚔️
      </div>
      <h3 class="pillar-title" id="combat-title">Chiến Đấu</h3>
      <p class="pillar-description">Chiến đấu không chỉ là t���n công và phòng thủ. Đây là cuộc chiến giữa sinh học và ý chí sống.</p>
      <ul class="feature-list">
       <li class="feature-item">Sinh vật tiến hóa theo thời gian thực</li>
       <li class="feature-item">Mỗi lõi năng lượng có điểm yếu riêng</li>
       <li class="feature-item">Chiến thuật thích ứng là then chốt</li>
       <li class="feature-item">Môi trường là vũ khí và kẻ thù</li>
       <li class="feature-item">Sinh tồn qua trí tuệ, không phải sức mạnh</li>
      </ul>
     </div><!-- Crafting Pillar -->
     <div class="pillar-card">
      <div class="pillar-icon">
       🔧
      </div>
      <h3 class="pillar-title" id="crafting-title">Chế Tạo</h3>
      <p class="pillar-description">Thu thập tài nguyên từ môi trường sống và lõi năng lượng để chế t���o vũ khí, giáp, và công cụ sinh tồn.</p>
      <ul class="feature-list">
       <li class="feature-item">Khai thác năng lượng sinh học</li>
       <li class="feature-item">Chế tạo vũ khí hybrid bio-tech</li>
       <li class="feature-item">Nâng cấp thiết bị theo thời gian</li>
       <li class="feature-item">Tạo căn cứ di động</li>
       <li class="feature-item">Hợp nhất công nghệ và sinh học</li>
      </ul>
     </div>
    </div><!-- Evolution System Section -->
    <div class="evolution-system-section">
     <div class="evolution-header">
      <div class="evolution-icon-large">
       🧬
      </div>
      <h3 class="evolution-main-title">🧬 Thích Nghi</h3>
      <p class="evolution-tagline">Người chơi có thể tiến hóa <span class="highlight-evolution">Càng mạnh → càng ít giống người.</span></p>
     </div>
     <div class="mutation-paths-grid">
      <div class="mutation-card">
       <div class="mutation-icon">
        🧬
       </div>
       <h4 class="mutation-title">Cấy Gene Sinh Vật</h4>
       <p class="mutation-description">Hấp thụ DNA từ sinh vật bị tiêu diệt để có được khả năng đặc biệt của chúng.</p>
       <ul class="mutation-examples">
        <li>Thị giác của Circuit Fox - nhìn xuyên rừng</li>
        <li>Tốc độ của Data Hawk - chạy nhanh gấp đôi</li>
        <li>Sức mạnh của Titan Bear - đánh vỡ đá</li>
        <li>Độc tố của Cyber Scorpion - vũ khí sinh học</li>
       </ul>
      </div>
      <div class="mutation-card">
       <div class="mutation-icon">
        🦾
       </div>
       <h4 class="mutation-title">Thay Đổi Cơ Thể</h4>
       <p class="mutation-description">Cấy ghép các bộ phận sinh học-công nghệ để tăng cường khả năng chiến đấu.</p>
       <ul class="mutation-examples">
        <li>Tay bio-tech - tấn công cận chiến mạnh hơn</li>
        <li>Mắt mạch điện - phát hiện kẻ thù qua tường</li>
        <li>Chân bọc giáp - chạy nhanh, nhảy cao</li>
        <li>Lõi năng lượng phụ - tăng thể lực tối đa</li>
       </ul>
      </div>
      <div class="mutation-card">
       <div class="mutation-icon">
        ⚡
       </div>
       <h4 class="mutation-title">Nhận Kỹ Năng Dị Thường</h4>
       <p class="mutation-description">Mở khóa các khả năng siêu nhiên thông qua đột biến sinh học.</p>
       <ul class="mutation-examples">
        <li>Tái sinh nhanh - hồi máu tự động</li>
        <li>Cảm nhận sinh mạng - biết vị trí kẻ thù</li>
        <li>Hấp thụ năng lượng - biến sát thương thành HP</li>
        <li>Phản ứng thời gian - thế giới chậm lại</li>
       </ul>
      </div>
      <div class="mutation-card">
       <div class="mutation-icon">
        💀
       </div>
       <h4 class="mutation-title">Đánh Đổi Nhân Tính</h4>
       <p class="mutation-description">Mỗi đột biến khiến bạn mất đi một phần con người. Giá phải trả cho sức mạnh.</p>
       <ul class="mutation-examples">
        <li>Mất cảm xúc - không còn sợ hãi, nhưng cũng không còn đồng cảm</li>
        <li>Tâm trí biến đổi - suy nghĩ như máy móc</li>
        <li>Hình dạng thay đổi - càng lúc càng giống quái vật</li>
        <li>Bản năng thú tính - tấn công bất kể đối tượng</li>
       </ul>
      </div>
     </div>
     <div class="humanity-cost-box">
      <div class="humanity-icon">
       👤
      </div>
      <h4 class="humanity-title">Cái Giá Của Sức Mạnh</h4>
      <div class="humanity-progression">
       <div class="humanity-stage">
        <div class="humanity-stage-icon">
         🧑
        </div>
        <div class="humanity-stage-label">
         Con Người
        </div>
       </div>
       <div class="humanity-arrow">
        →
       </div>
       <div class="humanity-stage">
        <div class="humanity-stage-icon">
         🦾
        </div>
        <div class="humanity-stage-label">
         Hybrid
        </div>
       </div>
       <div class="humanity-arrow">
        →
       </div>
       <div class="humanity-stage">
        <div class="humanity-stage-icon">
         🦾
        </div>
        <div class="humanity-stage-label">
         Sinh Vật
        </div>
       </div>
       <div class="humanity-arrow">
        →
       </div>
       <div class="humanity-stage">
        <div class="humanity-stage-icon">
         👾
        </div>
        <div class="humanity-stage-label">
         Quái Vật
        </div>
       </div>
      </div>
      <p class="humanity-warning">Càng mạnh, càng ít giống người. <strong>Survival = đánh đổi bản thân.</strong></p>
     </div>
    </div><!-- Adaptive Combat Section -->
    <div class="adaptive-combat-section">
     <h3 class="adaptive-title">⚔️ ĐỐI KHÁNG ĐỘNG - THÍCH NGHI HOẶC CHẾT</h3>
     <p class="adaptive-intro">Sinh vật không chỉ tấn công — <strong>chúng tiến hóa theo cách bạn chơi</strong></p>
     <div class="evolution-grid">
      <div class="evolution-card">
       <div class="evolution-icon">
        🔫
       </div>
       <h4 class="evolution-trigger">Dùng súng nhiều</h4>
       <div class="evolution-arrow">
        ⟹
       </div>
       <p class="evolution-result">Quái kháng đạn</p>
       <p class="evolution-desc">Giáp sinh học dày lên, hấp thụ động năng</p>
      </div>
      <div class="evolution-card">
       <div class="evolution-icon">
        🔥
       </div>
       <h4 class="evolution-trigger">Dùng lửa</h4>
       <div class="evolution-arrow">
        ⟹
       </div>
       <p class="evolution-result">Quái miễn cháy</p>
       <p class="evolution-desc">Lớp da chống nhiệt, hấp thụ năng lượng lửa</p>
      </div>
      <div class="evolution-card">
       <div class="evolution-icon">
        🏃
       </div>
       <h4 class="evolution-trigger">Chạy trốn</h4>
       <div class="evolution-arrow">
        ⟹
       </div>
       <p class="evolution-result">Quái săn theo mùi</p>
       <p class="evolution-desc">Giác quan tăng cường, tốc độ cao hơn</p>
      </div>
     </div>
     <div class="world-learns-box">
      <div class="learns-icon">
       🧠
      </div>
      <h4 class="learns-title">Thế giới học từ bạn.</h4>
      <p class="learns-text">Bạn phải liên tục <span class="highlight-text">thay đổi chiến thuật</span>.<br>
        Không có công thức chiến thắng cố định.<br><strong>Thích nghi hoặc bị xóa bỏ.</strong></p>
     </div>
    </div><!-- Ecosystem Survival Section -->
    <div class="ecosystem-survival-section">
     <div class="ecosystem-header">
      <div class="ecosystem-badge">
       ③ HỆ THỐNG SINH TỒN ĐỘC QUYỀN
      </div>
      <h3 class="ecosystem-main-title">Quản Lý Cân Bằng Thế Giới</h3>
      <p class="ecosystem-subtitle">Không chỉ đói và máu. Game dùng hệ sinh thái động. <strong>Sinh tồn là quản lý cân bằng thế giới.</strong></p>
     </div>
     <div class="dynamic-eco-grid">
      <div class="eco-card">
       <div class="eco-icon">
        🦊
       </div>
       <h4 class="eco-title">Chuỗi Thức Ăn Động</h4>
       <p class="eco-description">Bạn săn quá nhiều → quái hiếm tuyệt chủng<br>
         Thiếu săn mồi → quái khác tràn lan</p>
       <ul class="eco-examples">
        <li>Giết hết Circuit Fox → Data Hawk thiếu thức ăn và chết dần</li>
        <li>Titan Bear tràn lan vì không còn kẻ thù tự nhiên</li>
        <li>Hệ sinh thái sụp đổ → bạn phải đối mặt với hỗn loạn</li>
       </ul>
      </div>
      <div class="eco-card">
       <div class="eco-icon">
        🌳
       </div>
       <h4 class="eco-title">Môi Trường Phản Ứng</h4>
       <p class="eco-description">Môi trường phản ứng với hành vi người chơi và thay đổi theo thời gian thực.</p>
       <ul class="eco-examples">
        <li>Chặt cây quá nhiều → rừng chết, sinh vật di cư</li>
        <li>Đốt rừng → phóng xạ tăng, đột biến gia tăng</li>
        <li>Ô nhiễm nước → sinh vật biển hung dữ hơn</li>
       </ul>
      </div>
      <div class="eco-card">
       <div class="eco-icon">
        ⚖️
       </div>
       <h4 class="eco-title">Cân Bằng Là Sống</h4>
       <p class="eco-description">Mỗi quyết định của bạn tạo ra hậu quả sinh thái dài hạn.</p>
       <ul class="eco-examples">
        <li>Săn vừa đủ → hệ sinh thái ổn định</li>
        <li>Bảo vệ loài yếu → chúng trở thành đồng minh</li>
        <li>Phá hủy bừa bãi → tự tạo ra địa ngục cho chính mình</li>
       </ul>
      </div>
     </div>
     <div class="chain-reaction-box">
      <div class="chain-icon">
       ⛓️‍💥
      </div>
      <h4 class="chain-title">Bạn Có Thể Phá Hủy Chuỗi Sinh Học</h4>
      <p class="chain-description">Và tự tạo ra địa ngục cho chính mình. <strong>Mọi hành động đều có hậu quả.</strong></p>
     </div>
     <div class="environmental-factors-section">
      <div class="env-header">
       <h4 class="env-title">Yếu Tố Môi Trường</h4>
       <p class="env-subtitle">Ngoài ra, môi trường ảnh hưởng trực tiếp đến gameplay</p>
      </div>
      <div class="env-grid">
       <div class="env-factor-card">
        <div class="env-icon">
         🌡️
        </div>
        <h5 class="env-factor-title">Nhiệt Độ</h5>
        <p class="env-factor-effect">Nhiệt độ ảnh hưởng tốc độ di chuyển và hao thể lực.<br><br>
          Lạnh quá → chậm hơn, mất HP liên tục<br>
          Nóng quá → tốc độ giảm, cần nước nhiều hơn</p>
       </div>
       <div class="env-factor-card">
        <div class="env-icon">
         ☢️
        </div>
        <h5 class="env-factor-title">Phóng Xạ</h5>
        <p class="env-factor-effect">Phóng xạ biến đổi cơ thể và cả sinh vật xung quanh.<br><br>
          Phóng xạ thấp → đột biến chậm<br>
          Phóng xạ cao → đột biến nhanh, nguy hiểm cao</p>
       </div>
       <div class="env-factor-card">
        <div class="env-icon">
         🦠
        </div>
        <h5 class="env-factor-title">Nhiễm Sinh Học</h5>
        <p class="env-factor-effect">Nhiễm sinh học gây hallucination và ảo giác.<br><br>
          Nhẹ → thấy bóng ma, âm thanh lạ<br>
          Nặng → không phân biệt được thực hư</p>
       </div>
       <div class="env-factor-card">
        <div class="env-icon">
         🌙
        </div>
        <h5 class="env-factor-title">Thiếu Ánh Sáng</h5>
        <p class="env-factor-effect">Thiếu ánh sáng làm AI sinh vật hung dữ và thông minh hơn.<br><br>
          Ban ngày → quái yếu hơn<br>
          Ban đêm → quái tấn công hung hãn, phục kích nhiều</p>
       </div>
      </div>
      <div class="final-message-box">
       <div class="final-icon">
        🌍
       </div>
       <p class="final-text">Mỗi Run Là Một Hệ Sinh Thái Khác</p>
      </div>
     </div>
    </div><!-- Enemy Showcase -->
    <div class="enemy-showcase">
     <h3 class="showcase-title">🦾 SINH VẬT ĐỐI ẦU</h3>
     <div class="enemy-grid">
      <div class="enemy-card">
       <div class="enemy-icon">
        ��
       </div>
       <h4 class="enemy-name">Circuit Fox</h4>
       <p class="enemy-desc">Sói mạch điện - nhanh nhẹn, săn mồi theo nhóm, có khả năng phát hiện sinh mạng từ xa.</p><span class="threat-level">⚠️ Mức Độ: Trung Bình</span>
      </div>
      <div class="enemy-card">
       <div class="enemy-icon">
        🦅
       </div>
       <h4 class="enemy-name">Data Hawk</h4>
       <p class="enemy-desc">Chim ưng dữ liệu - tấn công từ trên cao, quét vị trí và báo động cho các sinh vật khác.</p><span class="threat-level">⚠️ Mức Độ: Cao</span>
      </div>
      <div class="enemy-card">
       <div class="enemy-icon">
        🐻
       </div>
       <h4 class="enemy-name">Titan Bear</h4>
       <p class="enemy-desc">Gấu Titan - giáp sinh học dày, sức mạnh khủng khiếp, chỉ có thể đánh bại bằng chiến thuật.</p><span class="threat-level">🚨 Mức Độ: Cực Kỳ Nguy Hiểm</span>
      </div>
      <div class="enemy-card">
       <div class="enemy-icon">
        🌿
       </div>
       <h4 class="enemy-name">Forest Sentinel</h4>
       <p class="enemy-desc">Người gác rừng - sinh vật thực vật di động, kiểm soát cây cối và bẫy sinh học.</p><span class="threat-level">⚠️ Mức Độ: Cao</span>
      </div>
      <div class="enemy-card">
       <div class="enemy-icon">
        🦂
       </div>
       <h4 class="enemy-name">Cyber Scorpion</h4>
       <p class="enemy-desc">Bọ cạp điện tử - độc tố tê liệt h�� thần kinh, ẩn núp trong bóng tối.</p><span class="threat-level">⚠️ Mức Độ: Trung Bình</span>
      </div>
      <div class="enemy-card">
       <div class="enemy-icon">
        🐲
       </div>
       <h4 class="enemy-name">Core Dragon</h4>
       <p class="enemy-desc">Rồng Lõi - sinh vật huyền thoại mang lõi năng lượng nguyên thủy, có thể hủy diệt cả vùng rừng.</p><span class="threat-level">💀 Mức Độ: Boss</span>
      </div>
     </div>
    </div><!-- Warning Section -->
    <div class="warning-section">
     <div class="warning-icon">
      ⚠️
     </div>
     <h3 class="warning-title">CON NGƯỜI KHÔNG CÒN LÀ KẺ THỐNG TRỊ</h3>
     <p class="warning-text">Hành tinh này đang tự tái cấu trúc mỗi ngày<br>
       để loại bỏ loài người.<br><br><strong>Họ là kẻ sống sót, không phải kẻ chinh phục.</strong></p>
    </div><!-- Survival Tips -->
    <div class="tips-section">
     <h3 class="tips-title">💡 BÍ QUYẾT SINH TỒN</h3>
     <div class="tips-grid">
      <div class="tip-card">
       <div class="tip-number">
        01
       </div>
       <h4 class="tip-title">Quan Sát Môi Trường</h4>
       <p class="tip-description">Học cách đọc các dấu hiệu của hành tinh. Rừng phát sáng mạnh hơn có nghĩa nguy hiểm đang đến gần.</p>
      </div>
      <div class="tip-card">
       <div class="tip-number">
        02
       </div>
       <h4 class="tip-title">Thu Thập Lõi Năng Lượng</h4>
       <p class="tip-description">Mỗi sinh vật bị đánh bại để lại lõi năng lượng. Đây là nguồn tài nguyên quý giá nhất để chế tạo.</p>
      </div>
      <div class="tip-card">
       <div class="tip-number">
        03
       </div>
       <h4 class="tip-title">Thích Nghi Nhanh Chóng</h4>
       <p class="tip-description">Địa hình thay đổi liên tục. Đừng dựa vào bản đồ cũ. Luôn sẵn sàng di chuyển và thay đổi kế hoạch.</p>
      </div>
      <div class="tip-card">
       <div class="tip-number">
        04
       </div>
       <h4 class="tip-title">Tránh Chiến Đấu Không Cần Thiết</h4>
       <p class="tip-description">Không phải mọi sinh vật đều cần tiêu diệt. Đôi khi ẩn núp là lựa chọn khôn ngoan nhất.</p>
      </div>
      <div class="tip-card">
       <div class="tip-number">
        05
       </div>
       <h4 class="tip-title">Nâng Cấp Thiết Bị</h4>
       <p class="tip-description">Vũ khí và giáp cơ bản không đủ để đối mặt với các sinh vật mạnh. Luôn tìm cách nâng cấp.</p>
      </div>
      <div class="tip-card">
       <div class="tip-number">
        06
       </div>
       <h4 class="tip-title">Hiểu Kẻ Thù</h4>
       <p class="tip-description">Mỗi sinh vật có điểm yếu riêng. Quan sát, học hỏi, và khai thác điểm yếu của chúng.</p>
      </div>
     </div>
    </div><!-- Game Stats -->
    <div class="stats-section">
     <div class="stat-box">
      <div class="stat-icon">
       🌍
      </div>
      <div class="stat-value">
       1
      </div>
      <div class="stat-label">
       Hành Tinh Sống
      </div>
     </div>
     <div class="stat-box">
      <div class="stat-icon">
       ⚡
      </div>
      <div class="stat-value">
       50+
      </div>
      <div class="stat-label">
       Loại Sinh Vật
      </div>
     </div>
     <div class="stat-box">
      <div class="stat-icon">
       🗺️
      </div>
      <div class="stat-value">
       ∞
      </div>
      <div class="stat-label">
       Bản Đồ Động
      </div>
     </div>
     <div class="stat-box">
      <div class="stat-icon">
       🎯
      </div>
      <div class="stat-value">
       100%
      </div>
      <div class="stat-label">
       Tỷ Lệ Sống
      </div>
     </div>
    </div>
   </section><!-- Footer -->
   <footer class="footer-section">
    <p class="footer-text"><span class="footer-highlight">BIO-TECH SURVIVAL</span> | Nơi Sinh Tồn Là Nghệ Thuật</p>
   </footer>
  </div>
  <script>
    // Configuration object
    const defaultConfig = {
      world_title: "BIO-TECH SURVIVAL WORLD",
      world_subtitle: "Nơi thiên nhiên và công nghệ hòa làm một",
      philosophy_text: "Sinh tồn không phải đánh bại thiên nhiên\nmà là học cách không bị nó xóa bỏ\n\nThế giới không ghét bạn.\nNó chỉ đang cố sửa lỗi… và bạn là lỗi đó.",
      exploration_title: "🧭 Khám Phá",
      combat_title: "⚔️ Chiến Đấu",
      crafting_title: "🔧 Chế Tạo",
      background_color: "#0a0e27",
      surface_color: "#1e293b",
      text_color: "#e0e7ff",
      primary_action_color: "#6366f1",
      secondary_action_color: "#8b5cf6",
      font_family: "Rajdhani",
      font_size: 16
    };

    // Function to apply config changes to the DOM
    async function onConfigChange(config) {
      const currentConfig = { ...defaultConfig, ...config };
      
      // Update text content
      const worldTitle = document.getElementById('world-title');
      if (worldTitle) {
        worldTitle.textContent = currentConfig.world_title || defaultConfig.world_title;
      }
      
      const worldSubtitle = document.getElementById('world-subtitle');
      if (worldSubtitle) {
        worldSubtitle.textContent = currentConfig.world_subtitle || defaultConfig.world_subtitle;
      }
      
      const philosophyText = document.getElementById('philosophy-text');
      if (philosophyText) {
        const text = currentConfig.philosophy_text || defaultConfig.philosophy_text;
        philosophyText.innerHTML = text.split('\n').join('<br>');
      }
      
      const explorationTitle = document.getElementById('exploration-title');
      if (explorationTitle) {
        explorationTitle.textContent = currentConfig.exploration_title || defaultConfig.exploration_title;
      }
      
      const combatTitle = document.getElementById('combat-title');
      if (combatTitle) {
        combatTitle.textContent = currentConfig.combat_title || defaultConfig.combat_title;
      }
      
      const craftingTitle = document.getElementById('crafting-title');
      if (craftingTitle) {
        craftingTitle.textContent = currentConfig.crafting_title || defaultConfig.crafting_title;
      }
      
      // Apply colors
      const backgroundColor = currentConfig.background_color || defaultConfig.background_color;
      const surfaceColor = currentConfig.surface_color || defaultConfig.surface_color;
      const textColor = currentConfig.text_color || defaultConfig.text_color;
      const primaryActionColor = currentConfig.primary_action_color || defaultConfig.primary_action_color;
      const secondaryActionColor = currentConfig.secondary_action_color || defaultConfig.secondary_action_color;
      
      document.body.style.background = `linear-gradient(135deg, ${backgroundColor} 0%, ${surfaceColor} 50%, ${backgroundColor} 100%)`;
      document.body.style.color = textColor;
      
      // Apply font
      const customFont = currentConfig.font_family || defaultConfig.font_family;
      const baseFontStack = 'Arial, sans-serif';
      
      document.body.style.fontFamily = `${customFont}, ${baseFontStack}`;
      
      // Apply font sizing
      const baseSize = currentConfig.font_size || defaultConfig.font_size;
      
      const glitchTitle = document.querySelector('.glitch-title');
      if (glitchTitle) glitchTitle.style.fontSize = `${baseSize * 4.5}px`;
      
      const subtitle = document.querySelector('.subtitle');
      if (subtitle) subtitle.style.fontSize = `${baseSize * 1.75}px`;
      
      const cardTitles = document.querySelectorAll('.card-title');
      cardTitles.forEach(el => el.style.fontSize = `${baseSize * 2.625}px`);
      
      const cardContents = document.querySelectorAll('.card-content');
      cardContents.forEach(el => el.style.fontSize = `${baseSize * 1.25}px`);
      
      const sectionTitles = document.querySelectorAll('.section-title');
      sectionTitles.forEach(el => el.style.fontSize = `${baseSize * 3.5}px`);
      
      const pillarTitles = document.querySelectorAll('.pillar-title');
      pillarTitles.forEach(el => el.style.fontSize = `${baseSize * 2}px`);
      
      const pillarDescriptions = document.querySelectorAll('.pillar-description');
      pillarDescriptions.forEach(el => el.style.fontSize = `${baseSize * 1.125}px`);
    }

    // Initialize Element SDK
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities: (config) => ({
          recolorables: [
            {
              get: () => config.background_color || defaultConfig.background_color,
              set: (value) => {
                config.background_color = value;
                window.elementSdk.setConfig({ background_color: value });
              }
            },
            {
              get: () => config.surface_color || defaultConfig.surface_color,
              set: (value) => {
                config.surface_color = value;
                window.elementSdk.setConfig({ surface_color: value });
              }
            },
            {
              get: () => config.text_color || defaultConfig.text_color,
              set: (value) => {
                config.text_color = value;
                window.elementSdk.setConfig({ text_color: value });
              }
            },
            {
              get: () => config.primary_action_color || defaultConfig.primary_action_color,
              set: (value) => {
                config.primary_action_color = value;
                window.elementSdk.setConfig({ primary_action_color: value });
              }
            },
            {
              get: () => config.secondary_action_color || defaultConfig.secondary_action_color,
              set: (value) => {
                config.secondary_action_color = value;
                window.elementSdk.setConfig({ secondary_action_color: value });
              }
            }
          ],
          borderables: [],
          fontEditable: {
            get: () => config.font_family || defaultConfig.font_family,
            set: (value) => {
              config.font_family = value;
              window.elementSdk.setConfig({ font_family: value });
            }
          },
          fontSizeable: {
            get: () => config.font_size || defaultConfig.font_size,
            set: (value) => {
              config.font_size = value;
              window.elementSdk.setConfig({ font_size: value });
            }
          }
        }),
        mapToEditPanelValues: (config) => new Map([
          ["world_title", config.world_title || defaultConfig.world_title],
          ["world_subtitle", config.world_subtitle || defaultConfig.world_subtitle],
          ["philosophy_text", config.philosophy_text || defaultConfig.philosophy_text],
          ["exploration_title", config.exploration_title || defaultConfig.exploration_title],
          ["combat_title", config.combat_title || defaultConfig.combat_title],
          ["crafting_title", config.crafting_title || defaultConfig.crafting_title]
        ])
      });
    }

    // Add interactive particle animation on mouse move
    document.addEventListener('mousemove', (e) => {
      const particle = document.createElement('div');
      particle.className = 'particle';
      particle.style.left = e.clientX + 'px';
      particle.style.top = e.clientY + 'px';
      particle.style.position = 'fixed';
      document.body.appendChild(particle);
      
      setTimeout(() => {
        particle.remove();
      }, 1000);
    });

    // Add smooth scroll behavior for anchor links
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function (e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        if (target) {
          target.scrollIntoView({
            behavior: 'smooth',
            block: 'start'
          });
        }
      });
    });

    // Add parallax effect to cards on scroll
    const cards = document.querySelectorAll('.world-card, .pillar-card, .enemy-card, .tip-card');
    
    window.addEventListener('scroll', () => {
      const scrolled = window.pageYOffset;
      
      cards.forEach((card, index) => {
        const speed = 0.05 * (index + 1);
        const yPos = -(scrolled * speed);
        card.style.transform = `translateY(${yPos}px)`;
      });
    });
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c69aacd479acdec',t:'MTc2OTg2NzMxMi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
<!doctype doctype>
<html lang="vi">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sinh Tồn Sinh Thái</title>
  <script src="/_sdk/data_sdk.js"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&amp;family=Rajdhani:wght@300;500;700&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
    }
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    
    html, body {
      height: 100%;
      width: 100%;
    }
    
    @keyframes breathe {
      0%, 100% { opacity: 0.3; transform: scale(1); }
      50% { opacity: 0.7; transform: scale(1.05); }
    }
    
    @keyframes pulse {
      0%, 100% { box-shadow: 0 0 20px rgba(0, 245, 212, 0.3); }
      50% { box-shadow: 0 0 40px rgba(0, 245, 212, 0.8); }
    }
    
    @keyframes float {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-10px); }
    }
    
    @keyframes dataFlow {
      0% { transform: translateY(0) rotate(0deg); opacity: 0; }
      50% { opacity: 1; }
      100% { transform: translateY(-100%) rotate(360deg); opacity: 0; }
    }
    
    @keyframes glitch {
      0%, 100% { transform: translate(0); }
      20% { transform: translate(-2px, 2px); }
      40% { transform: translate(2px, -2px); }
      60% { transform: translate(-2px, -2px); }
      80% { transform: translate(2px, 2px); }
    }
    
    @keyframes neonGlow {
      0%, 100% { 
        text-shadow: 0 0 10px rgba(0, 245, 212, 0.5),
                     0 0 20px rgba(0, 245, 212, 0.3),
                     0 0 30px rgba(0, 187, 249, 0.2);
      }
      50% { 
        text-shadow: 0 0 20px rgba(0, 245, 212, 0.8),
                     0 0 40px rgba(0, 245, 212, 0.5),
                     0 0 60px rgba(0, 187, 249, 0.4);
      }
    }
    
    body {
      font-family: 'Rajdhani', sans-serif;
      background: linear-gradient(135deg, #0a0e27 0%, #1a1f3a 50%, #0f1419 100%);
      color: #e8f4f8;
      overflow-x: hidden;
      position: relative;
    }
    
    body::before {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: 
        radial-gradient(circle at 20% 30%, rgba(0, 245, 212, 0.1) 0%, transparent 50%),
        radial-gradient(circle at 80% 70%, rgba(123, 44, 191, 0.1) 0%, transparent 50%),
        radial-gradient(circle at 50% 50%, rgba(0, 187, 249, 0.05) 0%, transparent 70%);
      pointer-events: none;
      animation: breathe 8s ease-in-out infinite;
      z-index: 0;
    }
    
    .main-wrapper {
      width: 100%;
      height: 100%;
      overflow-y: auto;
      overflow-x: hidden;
      position: relative;
      z-index: 1;
    }
    
    .app-container {
      min-height: 100%;
      padding: 2.5% 4%;
      position: relative;
    }
    
    .data-particles {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 0;
      overflow: hidden;
    }
    
    .particle {
      position: absolute;
      width: 2px;
      height: 2px;
      background: rgba(0, 245, 212, 0.6);
      border-radius: 50%;
      animation: dataFlow 15s linear infinite;
      box-shadow: 0 0 10px rgba(0, 245, 212, 0.8);
    }
    
    .creature-glow {
      position: absolute;
      width: 150px;
      height: 150px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(157, 78, 221, 0.3) 0%, transparent 70%);
      pointer-events: none;
      animation: float 6s ease-in-out infinite;
      filter: blur(40px);
    }
    
    .header {
      text-align: center;
      margin-bottom: 3%;
      position: relative;
    }
    
    .game-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 3.5em;
      font-weight: 900;
      color: #00f5d4;
      margin-bottom: 0.5%;
      letter-spacing: 0.05em;
      animation: neonGlow 3s ease-in-out infinite;
      position: relative;
    }
    
    .game-title::after {
      content: attr(data-text);
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      color: #00bbf9;
      opacity: 0.3;
      animation: glitch 5s infinite;
      pointer-events: none;
    }
    
    .subtitle {
      font-size: 1.3em;
      color: #9d4edd;
      font-weight: 500;
      opacity: 0.9;
    }
    
    .stats-bar {
      display: flex;
      justify-content: space-around;
      background: rgba(15, 20, 35, 0.7);
      border: 2px solid #00f5d4;
      border-radius: 15px;
      padding: 2% 3%;
      margin-bottom: 3%;
      box-shadow: 0 0 25px rgba(0, 245, 212, 0.2);
    }
    
    .stat-item {
      text-align: center;
    }
    
    .stat-label {
      font-size: 0.9em;
      color: #7b2cbf;
      text-transform: uppercase;
      letter-spacing: 0.1em;
      margin-bottom: 0.5%;
    }
    
    .stat-value {
      font-family: 'Orbitron', sans-serif;
      font-size: 2em;
      color: #00f5d4;
      font-weight: 700;
    }
    
    .layers-container {
      display: grid;
      gap: 2.5%;
      margin-bottom: 3%;
    }
    
    .layer-card {
      background: linear-gradient(135deg, rgba(0, 187, 249, 0.1) 0%, rgba(123, 44, 191, 0.1) 100%);
      border: 2px solid;
      border-radius: 20px;
      padding: 3%;
      position: relative;
      overflow: hidden;
      transition: all 0.3s ease;
      cursor: pointer;
    }
    
    .layer-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, transparent 0%, rgba(0, 245, 212, 0.05) 100%);
      opacity: 0;
      transition: opacity 0.3s ease;
    }
    
    .layer-card:hover::before {
      opacity: 1;
    }
    
    .layer-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 40px rgba(0, 245, 212, 0.3);
    }
    
    .layer-card.locked {
      opacity: 0.5;
      cursor: not-allowed;
    }
    
    .layer-card.locked:hover {
      transform: none;
      box-shadow: none;
    }
    
    .layer-card.active {
      border-color: #00f5d4;
      box-shadow: 0 0 30px rgba(0, 245, 212, 0.4);
    }
    
    .layer-card.completed {
      border-color: #7b2cbf;
      background: linear-gradient(135deg, rgba(123, 44, 191, 0.2) 0%, rgba(0, 187, 249, 0.1) 100%);
    }
    
    .layer-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 2%;
    }
    
    .layer-number {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.2em;
      color: #00bbf9;
      font-weight: 700;
    }
    
    .layer-status {
      font-size: 0.9em;
      padding: 1% 3%;
      border-radius: 20px;
      font-weight: 500;
    }
    
    .layer-status.locked {
      background: rgba(157, 78, 221, 0.2);
      color: #9d4edd;
    }
    
    .layer-status.active {
      background: rgba(0, 245, 212, 0.2);
      color: #00f5d4;
    }
    
    .layer-status.completed {
      background: rgba(123, 44, 191, 0.3);
      color: #c77dff;
    }
    
    .layer-name {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.8em;
      color: #e8f4f8;
      margin-bottom: 1.5%;
      font-weight: 700;
    }
    
    .layer-description {
      font-size: 1.1em;
      color: #9d4edd;
      margin-bottom: 2%;
      line-height: 1.5;
    }
    
    .layer-challenges {
      display: flex;
      flex-wrap: wrap;
      gap: 1.5%;
      margin-bottom: 2.5%;
    }
    
    .challenge-tag {
      background: rgba(0, 187, 249, 0.2);
      color: #00bbf9;
      padding: 1.2% 2.5%;
      border-radius: 8px;
      font-size: 0.9em;
      border: 1px solid rgba(0, 187, 249, 0.3);
    }
    
    .progress-container {
      margin-top: 2.5%;
    }
    
    .progress-label {
      font-size: 0.9em;
      color: #7b2cbf;
      margin-bottom: 1%;
    }
    
    .progress-bar {
      width: 100%;
      height: 12px;
      background: rgba(15, 20, 35, 0.5);
      border-radius: 10px;
      overflow: hidden;
      border: 1px solid rgba(0, 245, 212, 0.3);
    }
    
    .progress-fill {
      height: 100%;
      background: linear-gradient(90deg, #00f5d4 0%, #00bbf9 100%);
      transition: width 0.5s ease;
      box-shadow: 0 0 10px rgba(0, 245, 212, 0.5);
    }
    
    .meta-progression {
      background: linear-gradient(135deg, rgba(123, 44, 191, 0.2) 0%, rgba(15, 20, 35, 0.8) 100%);
      border: 2px solid #7b2cbf;
      border-radius: 20px;
      padding: 3%;
      margin-bottom: 3%;
    }
    
    .meta-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.8em;
      color: #c77dff;
      margin-bottom: 2%;
      font-weight: 700;
    }
    
    .meta-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 2%;
    }
    
    .meta-item {
      background: rgba(0, 187, 249, 0.1);
      border: 1px solid rgba(0, 187, 249, 0.3);
      border-radius: 12px;
      padding: 3%;
      text-align: center;
    }
    
    .meta-icon {
      font-size: 2.5em;
      margin-bottom: 2%;
    }
    
    .meta-label {
      font-size: 1em;
      color: #00bbf9;
      margin-bottom: 1%;
      font-weight: 500;
    }
    
    .meta-count {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.8em;
      color: #00f5d4;
      font-weight: 700;
    }
    
    .memory-system {
      background: linear-gradient(135deg, rgba(157, 78, 221, 0.2) 0%, rgba(15, 20, 35, 0.8) 100%);
      border: 2px solid #9d4edd;
      border-radius: 20px;
      padding: 3%;
      margin-bottom: 3%;
    }
    
    .memory-title {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.6em;
      color: #9d4edd;
      margin-bottom: 2%;
      font-weight: 700;
    }
    
    .memory-warning {
      background: rgba(157, 78, 221, 0.2);
      border-left: 4px solid #9d4edd;
      padding: 2.5%;
      border-radius: 8px;
      font-size: 1.1em;
      color: #e8f4f8;
      line-height: 1.6;
    }
    
    .actions-container {
      display: flex;
      gap: 2%;
      flex-wrap: wrap;
    }
    
    .action-btn {
      flex: 1;
      min-width: 180px;
      padding: 3% 0;
      font-family: 'Orbitron', sans-serif;
      font-size: 1.1em;
      font-weight: 700;
      border: 2px solid;
      border-radius: 12px;
      cursor: pointer;
      transition: all 0.3s ease;
      text-transform: uppercase;
      letter-spacing: 0.1em;
    }
    
    .action-btn.primary {
      background: linear-gradient(135deg, #00f5d4 0%, #00bbf9 100%);
      border-color: #00f5d4;
      color: #0a0e27;
    }
    
    .action-btn.primary:hover {
      box-shadow: 0 0 25px rgba(0, 245, 212, 0.5);
      transform: translateY(-2px);
      animation: pulse 2s ease-in-out infinite;
    }
    
    .action-btn.primary:active {
      transform: translateY(0);
      box-shadow: 0 0 15px rgba(0, 245, 212, 0.3);
    }
    
    .action-btn.secondary {
      background: transparent;
      border-color: #7b2cbf;
      color: #c77dff;
    }
    
    .action-btn.secondary:hover {
      background: rgba(123, 44, 191, 0.2);
      box-shadow: 0 0 20px rgba(123, 44, 191, 0.3);
    }
    
    .action-btn:disabled {
      opacity: 0.4;
      cursor: not-allowed;
    }
    
    .history-list {
      margin-top: 2%;
      max-height: 200px;
      overflow-y: auto;
    }
    
    .history-item {
      background: rgba(0, 187, 249, 0.1);
      border-left: 3px solid #00bbf9;
      padding: 2%;
      margin-bottom: 1.5%;
      border-radius: 8px;
      font-size: 0.95em;
    }
    
    .history-time {
      color: #7b2cbf;
      font-size: 0.85em;
    }
    
    .loading-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(10, 14, 39, 0.9);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 1000;
    }
    
    .loading-spinner {
      width: 60px;
      height: 60px;
      border: 4px solid rgba(0, 245, 212, 0.2);
      border-top-color: #00f5d4;
      border-radius: 50%;
      animation: spin 1s linear infinite;
    }
    
    @keyframes spin {
      to { transform: rotate(360deg); }
    }
    
    .hidden {
      display: none;
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="https://cdn.tailwindcss.com" type="text/javascript"></script>
 </head>
 <body>
  <div class="data-particles" id="dataParticles"></div>
  <div class="main-wrapper">
   <div class="app-container">
    <div class="creature-glow" style="top: 10%; left: 15%; animation-delay: 0s;"></div>
    <div class="creature-glow" style="top: 60%; right: 10%; animation-delay: 2s;"></div>
    <div class="creature-glow" style="bottom: 20%; left: 40%; animation-delay: 4s;"></div>
    <div class="header">
     <h1 class="game-title" id="gameTitle" data-text="SINH TỒN SINH THÁI">SINH TỒN SINH THÁI</h1>
     <p class="subtitle" id="subtitle">Hệ sinh thái nhớ mọi sai lầm của bạn</p>
    </div>
    <div class="stats-bar">
     <div class="stat-item">
      <div class="stat-label">
       Run hiện tại
      </div>
      <div class="stat-value" id="currentRun">
       1
      </div>
     </div>
     <div class="stat-item">
      <div class="stat-label">
       Tầng
      </div>
      <div class="stat-value" id="currentLayer">
       1
      </div>
     </div>
     <div class="stat-item">
      <div class="stat-label">
       Tiến độ
      </div>
      <div class="stat-value" id="progressPercent">
       0%
      </div>
     </div>
    </div>
    <div class="layers-container" id="layersContainer"></div>
    <div class="meta-progression">
     <h2 class="meta-title">META PROGRESSION</h2>
     <div class="meta-grid">
      <div class="meta-item">
       <div class="meta-icon">
        🧬
       </div>
       <div class="meta-label">
        Gene Mở Khóa
       </div>
       <div class="meta-count" id="genesCount">
        0
       </div>
      </div>
      <div class="meta-item">
       <div class="meta-icon">
        🌍
       </div>
       <div class="meta-label">
        Biome Khám Phá
       </div>
       <div class="meta-count" id="biomesCount">
        0
       </div>
      </div>
      <div class="meta-item">
       <div class="meta-icon">
        💀
       </div>
       <div class="meta-label">
        Sai Lầm Ghi Nhận
       </div>
       <div class="meta-count" id="mistakesCount">
        0
       </div>
      </div>
      <div class="meta-item">
       <div class="meta-icon">
        🔄
       </div>
       <div class="meta-label">
        Tổng Run
       </div>
       <div class="meta-count" id="totalRuns">
        0
       </div>
      </div>
     </div>
    </div>
    <div class="memory-system">
     <h2 class="memory-title">⚠️ HỆ THỐNG KÝ ỨC</h2>
     <div class="memory-warning">
      Game nhớ mọi sai lầm bạn từng gây ra. Mỗi lần chết, sinh thái tiến hóa. Mỗi gen mở khóa, thế giới thay đổi. Ký ức từ run trước ảnh hưởng trực tiếp đến run sau. Bạn không chỉ đánh boss - bạn đánh một hệ sinh th��i nổi loạn đang học cách hủy diệt bạn.
     </div>
     <div class="history-list" id="historyList"></div>
    </div>
    <div class="actions-container"><button class="action-btn primary" id="startRunBtn">Bắt Đầu Run Mới</button> <button class="action-btn secondary" id="resetProgressBtn">Reset Tiến Trình</button>
    </div>
   </div>
  </div>
  <div class="loading-overlay hidden" id="loadingOverlay">
   <div class="loading-spinner"></div>
  </div>
  <script>
    const defaultConfig = {
      game_title: "SINH TỒN SINH THÁI",
      subtitle: "Hệ sinh thái nhớ mọi sai lầm của bạn",
      layer1_name: "Tầng hoang sơ",
      layer2_name: "Tầng săn mồi",
      layer3_name: "Tầng đột biến",
      layer4_name: "Tầng sụp đổ",
      layer5_name: "Tầng tuyệt chủng",
      background_color: "#0a0e27",
      surface_color: "#1a1f3a",
      text_color: "#e8f4f8",
      primary_action_color: "#00f5d4",
      secondary_action_color: "#7b2cbf"
    };

    const layerData = [
      {
        id: 1,
        description: "Học cách sinh tồn trong môi trường hoang sơ",
        challenges: ["Tìm th��c ăn", "Xây nơi trú ẩn", "Tránh nguy hiểm"]
      },
      {
        id: 2,
        description: "Bạn trở thành con mồi - hãy sống sót",
        challenges: ["Bị săn đuổi", "Ẩn náu", "Phản đòn"]
      },
      {
        id: 3,
        description: "Sinh vật phá vỡ mọi quy luật tự nhiên",
        challenges: ["Đột biến gen", "Thích nghi", "Tiến hóa ngược"]
      },
      {
        id: 4,
        description: "Môi trường tự hủy diệt - sống sót trong hỗn loạn",
        challenges: ["Thảm họa thiên nhiên", "Sụp đổ hệ sinh thái", "Tài nguyên cạn kiệt"]
      },
      {
        id: 5,
        description: "Đối đầu với boss sinh thái - hệ thống nổi loạn",
        challenges: ["Boss đa hình thái", "Hệ sinh thái vũ khí hóa", "Tuyệt chủng toàn diện"]
      }
    ];

    let currentRunData = {
      runNumber: 1,
      currentLayer: 1,
      genesUnlocked: 0,
      biomesUnlocked: 0,
      mistakesMade: 0,
      totalRuns: 0
    };

    let allRuns = [];
    let isLoading = false;

    const dataHandler = {
      onDataChanged(data) {
        allRuns = data.sort((a, b) => b.run_number - a.run_number);
        updateUIFromData();
      }
    };

    async function initSDK() {
      showLoading();
      const result = await window.dataSdk.init(dataHandler);
      hideLoading();
      
      if (!result.isOk) {
        showInlineMessage("Không thể khởi tạo hệ thống lưu trữ", "error");
      }
    }

    function updateUIFromData() {
      if (allRuns.length === 0) {
        renderInitialState();
        return;
      }

      const lastRun = allRuns[0];
      currentRunData = {
        runNumber: lastRun.run_number,
        currentLayer: lastRun.current_layer,
        genesUnlocked: lastRun.unlocked_genes ? lastRun.unlocked_genes.split(',').length : 0,
        biomesUnlocked: lastRun.unlocked_biomes ? lastRun.unlocked_biomes.split(',').length : 0,
        mistakesMade: lastRun.mistakes_made ? lastRun.mistakes_made.split(',').length : 0,
        totalRuns: allRuns.length
      };

      renderLayers();
      updateStats();
      renderHistory();
    }

    function renderInitialState() {
      currentRunData = {
        runNumber: 1,
        currentLayer: 1,
        genesUnlocked: 0,
        biomesUnlocked: 0,
        mistakesMade: 0,
        totalRuns: 0
      };
      
      renderLayers();
      updateStats();
      renderHistory();
    }

    function renderLayers() {
      const container = document.getElementById('layersContainer');
      container.innerHTML = '';

      layerData.forEach((layer) => {
        const isActive = layer.id === currentRunData.currentLayer;
        const isCompleted = layer.id < currentRunData.currentLayer;
        const isLocked = layer.id > currentRunData.currentLayer;

        const layerName = getLayerName(layer.id);
        
        const card = document.createElement('div');
        card.className = `layer-card ${isActive ? 'active' : ''} ${isCompleted ? 'completed' : ''} ${isLocked ? 'locked' : ''}`;
        card.style.borderColor = isActive ? defaultConfig.primary_action_color : (isCompleted ? defaultConfig.secondary_action_color : 'rgba(0, 187, 249, 0.3)');
        
        if (!isLocked) {
          card.addEventListener('click', () => selectLayer(layer.id));
        }

        const statusText = isCompleted ? 'Hoàn thành' : (isActive ? 'Đang chơi' : 'Khóa');
        const statusClass = isCompleted ? 'completed' : (isActive ? 'active' : 'locked');

        card.innerHTML = `
          <div class="layer-header">
            <span class="layer-number">TẦNG ${layer.id}</span>
            <span class="layer-status ${statusClass}">${statusText}</span>
          </div>
          <h3 class="layer-name">${layerName}</h3>
          <p class="layer-description">${layer.description}</p>
          <div class="layer-challenges">
            ${layer.challenges.map(challenge => `<span class="challenge-tag">${challenge}</span>`).join('')}
          </div>
          ${!isLocked ? `
            <div class="progress-container">
              <div class="progress-label">Tiến độ tầng</div>
              <div class="progress-bar">
                <div class="progress-fill" style="width: ${isCompleted ? '100' : (isActive ? '35' : '0')}%"></div>
              </div>
            </div>
          ` : ''}
        `;

        container.appendChild(card);
      });
    }

    function getLayerName(layerId) {
      const configKey = `layer${layerId}_name`;
      return window.elementSdk ? (window.elementSdk.config[configKey] || defaultConfig[configKey]) : defaultConfig[configKey];
    }

    function updateStats() {
      document.getElementById('currentRun').textContent = currentRunData.runNumber;
      document.getElementById('currentLayer').textContent = currentRunData.currentLayer;
      document.getElementById('progressPercent').textContent = Math.round((currentRunData.currentLayer / 5) * 100) + '%';
      document.getElementById('genesCount').textContent = currentRunData.genesUnlocked;
      document.getElementById('biomesCount').textContent = currentRunData.biomesUnlocked;
      document.getElementById('mistakesCount').textContent = currentRunData.mistakesMade;
      document.getElementById('totalRuns').textContent = currentRunData.totalRuns;
    }

    function renderHistory() {
      const historyList = document.getElementById('historyList');
      
      if (allRuns.length === 0) {
        historyList.innerHTML = '<div class="history-item">Ch���a có lịch sử chơi. Bắt đầu run đầu tiên!</div>';
        return;
      }

      historyList.innerHTML = allRuns.slice(0, 5).map(run => {
        const date = new Date(run.timestamp);
        return `
          <div class="history-item">
            <div>Run #${run.run_number} - Tầng ${run.current_layer}/5 ${run.completed ? '✅' : '⚠️'}</div>
            <div class="history-time">${date.toLocaleDateString('vi-VN')} ${date.toLocaleTimeString('vi-VN')}</div>
          </div>
        `;
      }).join('');
    }

    function selectLayer(layerId) {
      if (layerId > currentRunData.currentLayer) return;
      currentRunData.currentLayer = layerId;
      renderLayers();
      updateStats();
    }

    async function startNewRun() {
      if (isLoading) return;
      if (allRuns.length >= 999) {
        showInlineMessage("Đã đạt giới hạn 999 run. Vui lòng reset tiến trình trước.", "error");
        return;
      }

      showLoading();

      const newRun = {
        id: Date.now().toString() + Math.random().toString(36).substr(2, 9),
        run_number: currentRunData.totalRuns + 1,
        current_layer: 1,
        unlocked_genes: generateRandomGenes(),
        unlocked_biomes: generateRandomBiomes(),
        mistakes_made: generateRandomMistakes(),
        timestamp: new Date().toISOString(),
        completed: false
      };

      const result = await window.dataSdk.create(newRun);
      hideLoading();

      if (result.isOk) {
        showInlineMessage("Run mới đã bắt đầu! Chúc may mắn!", "success");
      } else {
        showInlineMessage("Không thể bắt đầu run mới", "error");
      }
    }

    function generateRandomGenes() {
      const genes = ['Alpha', 'Beta', 'Gamma', 'Delta', 'Epsilon', 'Zeta'];
      const count = Math.floor(Math.random() * 3) + 1;
      return genes.sort(() => 0.5 - Math.random()).slice(0, count).join(',');
    }

    function generateRandomBiomes() {
      const biomes = ['Rừng rậm', 'Sa mạc', 'Đại dương', 'Núi lửa', 'Băng nguyên'];
      const count = Math.floor(Math.random() * 2) + 1;
      return biomes.sort(() => 0.5 - Math.random()).slice(0, count).join(',');
    }

    function generateRandomMistakes() {
      const mistakes = ['Tấn công sai', 'Lãng phí tài nguyên', 'Bỏ lỡ cơ hội', 'Chọn sai chiến thuật'];
      const count = Math.floor(Math.random() * 3);
      return mistakes.sort(() => 0.5 - Math.random()).slice(0, count).join(',');
    }

    async function resetProgress() {
      if (isLoading) return;
      
      const confirmDiv = document.createElement('div');
      confirmDiv.style.cssText = 'position: fixed; top: 50%; left: 50%; transform: translate(-50%, -50%); background: #1a1f3a; padding: 30px; border: 2px solid #00f5d4; border-radius: 15px; z-index: 2000; text-align: center; box-shadow: 0 0 30px rgba(0, 245, 212, 0.3);';
      confirmDiv.innerHTML = `
        <div style="font-family: 'Orbitron', sans-serif; font-size: 1.4em; margin-bottom: 20px; color: #00f5d4;">Xác nhận reset?</div>
        <div style="margin-bottom: 25px; color: #e8f4f8;">Điều này sẽ xóa toàn bộ lịch sử run!</div>
        <button id="confirmReset" style="background: #00f5d4; color: #0a0e27; padding: 12px 30px; margin: 0 10px; border: none; border-radius: 8px; cursor: pointer; font-family: 'Orbitron', sans-serif; font-weight: 700;">Xác nhận</button>
        <button id="cancelReset" style="background: transparent; color: #c77dff; padding: 12px 30px; margin: 0 10px; border: 2px solid #7b2cbf; border-radius: 8px; cursor: pointer; font-family: 'Orbitron', sans-serif; font-weight: 700;">Hủy</button>
      `;
      document.body.appendChild(confirmDiv);

      document.getElementById('confirmReset').addEventListener('click', async () => {
        document.body.removeChild(confirmDiv);
        showLoading();
        
        for (const run of allRuns) {
          await window.dataSdk.delete(run);
        }
        
        hideLoading();
        showInlineMessage("Đã reset toàn bộ tiến trình", "success");
      });

      document.getElementById('cancelReset').addEventListener('click', () => {
        document.body.removeChild(confirmDiv);
      });
    }

    function showLoading() {
      isLoading = true;
      document.getElementById('loadingOverlay').classList.remove('hidden');
      document.getElementById('startRunBtn').disabled = true;
      document.getElementById('resetProgressBtn').disabled = true;
    }

    function hideLoading() {
      isLoading = false;
      document.getElementById('loadingOverlay').classList.add('hidden');
      document.getElementById('startRunBtn').disabled = false;
      document.getElementById('resetProgressBtn').disabled = false;
    }

    function showInlineMessage(message, type) {
      const messageDiv = document.createElement('div');
      messageDiv.style.cssText = `position: fixed; top: 20px; right: 20px; padding: 20px 30px; background: ${type === 'success' ? 'rgba(0, 245, 212, 0.2)' : 'rgba(157, 78, 221, 0.2)'}; border: 2px solid ${type === 'success' ? '#00f5d4' : '#9d4edd'}; border-radius: 12px; color: #e8f4f8; font-family: 'Rajdhani', sans-serif; font-size: 1.1em; z-index: 3000; box-shadow: 0 0 20px rgba(0, 245, 212, 0.3);`;
      messageDiv.textContent = message;
      document.body.appendChild(messageDiv);

      setTimeout(() => {
        document.body.removeChild(messageDiv);
      }, 3000);
    }

    document.getElementById('startRunBtn').addEventListener('click', startNewRun);
    document.getElementById('resetProgressBtn').addEventListener('click', resetProgress);

    async function onConfigChange(config) {
      const titleElement = document.getElementById('gameTitle');
      const newTitle = config.game_title || defaultConfig.game_title;
      titleElement.textContent = newTitle;
      titleElement.setAttribute('data-text', newTitle);
      
      document.getElementById('subtitle').textContent = config.subtitle || defaultConfig.subtitle;
      
      const backgroundColor = config.background_color || defaultConfig.background_color;
      const surfaceColor = config.surface_color || defaultConfig.surface_color;
      const textColor = config.text_color || defaultConfig.text_color;
      const primaryActionColor = config.primary_action_color || defaultConfig.primary_action_color;
      
      document.body.style.background = `linear-gradient(135deg, ${backgroundColor} 0%, ${surfaceColor} 50%, ${backgroundColor} 100%)`;
      document.documentElement.style.setProperty('--text-color', textColor);
      
      renderLayers();
    }

    function createDataParticles() {
      const container = document.getElementById('dataParticles');
      const particleCount = 50;
      
      for (let i = 0; i < particleCount; i++) {
        const particle = document.createElement('div');
        particle.className = 'particle';
        particle.style.left = Math.random() * 100 + '%';
        particle.style.animationDelay = Math.random() * 15 + 's';
        particle.style.animationDuration = (Math.random() * 10 + 10) + 's';
        
        const hue = Math.random() > 0.5 ? 174 : 268;
        particle.style.background = `hsl(${hue}, 100%, ${Math.random() * 30 + 50}%)`;
        particle.style.boxShadow = `0 0 10px hsl(${hue}, 100%, ${Math.random() * 30 + 50}%)`;
        
        container.appendChild(particle);
      }
    }

    function addHeartbeatEffect() {
      let lastTime = Date.now();
      let stress = 0;
      
      setInterval(() => {
        const now = Date.now();
        const delta = now - lastTime;
        
        if (delta < 100) {
          stress = Math.min(stress + 0.1, 1);
        } else {
          stress = Math.max(stress - 0.05, 0);
        }
        
        const scale = 1 + (stress * 0.02);
        document.body.style.transform = `scale(${scale})`;
        
        lastTime = now;
      }, 50);
    }

    createDataParticles();
    addHeartbeatEffect();

    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities: (config) => ({
          recolorables: [
            {
              get: () => config.background_color || defaultConfig.background_color,
              set: (value) => {
                if (window.elementSdk && window.elementSdk.config) {
                  window.elementSdk.config.background_color = value;
                  window.elementSdk.setConfig({ background_color: value });
                }
              }
            },
            {
              get: () => config.surface_color || defaultConfig.surface_color,
              set: (value) => {
                if (window.elementSdk && window.elementSdk.config) {
                  window.elementSdk.config.surface_color = value;
                  window.elementSdk.setConfig({ surface_color: value });
                }
              }
            },
            {
              get: () => config.text_color || defaultConfig.text_color,
              set: (value) => {
                if (window.elementSdk && window.elementSdk.config) {
                  window.elementSdk.config.text_color = value;
                  window.elementSdk.setConfig({ text_color: value });
                }
              }
            },
            {
              get: () => config.primary_action_color || defaultConfig.primary_action_color,
              set: (value) => {
                if (window.elementSdk && window.elementSdk.config) {
                  window.elementSdk.config.primary_action_color = value;
                  window.elementSdk.setConfig({ primary_action_color: value });
                }
              }
            },
            {
              get: () => config.secondary_action_color || defaultConfig.secondary_action_color,
              set: (value) => {
                if (window.elementSdk && window.elementSdk.config) {
                  window.elementSdk.config.secondary_action_color = value;
                  window.elementSdk.setConfig({ secondary_action_color: value });
                }
              }
            }
          ],
          borderables: [],
          fontEditable: undefined,
          fontSizeable: undefined
        }),
        mapToEditPanelValues: (config) => new Map([
          ["game_title", config.game_title || defaultConfig.game_title],
          ["subtitle", config.subtitle || defaultConfig.subtitle],
          ["layer1_name", config.layer1_name || defaultConfig.layer1_name],
          ["layer2_name", config.layer2_name || defaultConfig.layer2_name],
          ["layer3_name", config.layer3_name || defaultConfig.layer3_name],
          ["layer4_name", config.layer4_name || defaultConfig.layer4_name],
          ["layer5_name", config.layer5_name || defaultConfig.layer5_name]
        ])
      });
    }

    initSDK();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c69bee4c11dce6d',t:'MTc2OTg2ODEzNi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
