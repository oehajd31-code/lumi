<!DOCTYPE html>
<html lang="ka">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LumiShop — პრემიუმ ონლაინ მაღაზია</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;}
:root{
  --cream:#F5F1EA;
  --cream2:#EDE8DF;
  --dark:#16140F;
  --dark2:#252318;
  --accent:#B8935A;
  --accent2:#D4B88A;
  --accent3:#7A9E7E;
  --pop:#C4515A;
  --muted:#7A7670;
  --border:rgba(22,20,15,0.1);
  --border2:rgba(22,20,15,0.06);
  --white:#FDFBF7;
  --success:#4A7A5A;
  --danger:#8A3A3A;
  --shadow:0 4px 24px rgba(22,20,15,0.08);
  --shadow-lg:0 16px 48px rgba(22,20,15,0.14);
}

html{scroll-behavior:smooth;}
body{font-family:'DM Sans',sans-serif;background:var(--cream);color:var(--dark);line-height:1.6;cursor:default;overflow-x:hidden;}

::-webkit-scrollbar{width:3px;}
::-webkit-scrollbar-track{background:var(--cream2);}
::-webkit-scrollbar-thumb{background:var(--accent2);border-radius:2px;}

/* ── ANIMATIONS ── */
@keyframes fadeUp{from{opacity:0;transform:translateY(24px);}to{opacity:1;transform:translateY(0);}}
@keyframes fadeIn{from{opacity:0;}to{opacity:1;}}
@keyframes slideUp{from{opacity:0;transform:translateY(20px);}to{opacity:1;transform:translateY(0);}}
@keyframes slideIn{from{transform:translateX(100%);}to{transform:translateX(0);}}
@keyframes scaleIn{from{opacity:0;transform:scale(0.96);}to{opacity:1;transform:scale(1);}}
@keyframes shimmer{0%{background-position:-200% center;}100%{background-position:200% center;}}
@keyframes pulse{0%,100%{opacity:1;}50%{opacity:0.6;}}
@keyframes float{0%,100%{transform:translateY(0);}50%{transform:translateY(-10px);}}
@keyframes spin{from{transform:rotate(0deg);}to{transform:rotate(360deg);}}
@keyframes badgePop{0%{transform:scale(0);}70%{transform:scale(1.15);}100%{transform:scale(1);}}

.animate-up{animation:fadeUp 0.55s cubic-bezier(0.22,1,0.36,1) both;}
.delay-1{animation-delay:0.08s;}
.delay-2{animation-delay:0.16s;}
.delay-3{animation-delay:0.24s;}
.delay-4{animation-delay:0.32s;}
.delay-5{animation-delay:0.40s;}

/* ── NAV ── */
nav{
  position:sticky;top:0;z-index:90;
  background:rgba(245,241,234,0.92);backdrop-filter:blur(16px);-webkit-backdrop-filter:blur(16px);
  border-bottom:0.5px solid var(--border);
  display:flex;align-items:center;justify-content:space-between;
  padding:0 48px;height:64px;
  transition:box-shadow 0.3s;
}
nav.scrolled{box-shadow:0 2px 20px rgba(22,20,15,0.06);}
.nav-logo{
  font-family:'Cormorant Garamond',serif;font-size:24px;font-weight:500;
  letter-spacing:0.05em;text-decoration:none;color:var(--dark);
  position:relative;
}
.nav-logo span{color:var(--accent);}
.nav-links{display:flex;gap:32px;align-items:center;list-style:none;}
.nav-links a{
  font-size:11px;font-weight:400;color:var(--muted);text-decoration:none;
  letter-spacing:0.12em;text-transform:uppercase;transition:color 0.2s;
  position:relative;padding-bottom:3px;
}
.nav-links a::after{
  content:'';position:absolute;bottom:0;left:50%;right:50%;
  height:1.5px;background:var(--accent);transition:all 0.3s cubic-bezier(0.22,1,0.36,1);
}
.nav-links a:hover{color:var(--dark);}
.nav-links a:hover::after,.nav-links a.active::after{left:0;right:0;}
.nav-links a.active{color:var(--dark);}
.nav-right{display:flex;align-items:center;gap:12px;}
.btn-login{
  font-size:11px;letter-spacing:0.1em;text-transform:uppercase;
  color:var(--muted);background:none;border:0.5px solid var(--border);
  padding:9px 18px;cursor:pointer;transition:all 0.25s;font-family:'DM Sans',sans-serif;
  border-radius:1px;
}
.btn-login:hover{color:var(--dark);border-color:var(--dark);background:rgba(22,20,15,0.03);}
.btn-cart{
  display:flex;align-items:center;gap:8px;
  background:var(--dark);color:var(--cream);border:none;
  padding:10px 20px;font-size:11px;letter-spacing:0.1em;text-transform:uppercase;
  cursor:pointer;transition:all 0.25s;font-family:'DM Sans',sans-serif;
  border-radius:1px;position:relative;overflow:hidden;
}
.btn-cart::before{
  content:'';position:absolute;inset:0;background:var(--accent);
  transform:translateX(-100%);transition:transform 0.3s cubic-bezier(0.22,1,0.36,1);
}
.btn-cart:hover::before{transform:translateX(0);}
.btn-cart span,.btn-cart svg{position:relative;z-index:1;}
.cart-badge{
  background:var(--accent);color:var(--dark);border-radius:50%;
  width:18px;height:18px;display:flex;align-items:center;justify-content:center;
  font-size:10px;font-weight:500;min-width:18px;position:relative;z-index:1;
  transition:transform 0.2s cubic-bezier(0.34,1.56,0.64,1);
}
.cart-badge.bump{animation:badgePop 0.3s cubic-bezier(0.34,1.56,0.64,1);}

/* ── HERO ── */
.hero{
  display:grid;grid-template-columns:1fr 1fr;
  min-height:calc(100vh - 64px);border-bottom:0.5px solid var(--border);
  position:relative;overflow:hidden;
}
.hero-left{
  padding:80px 64px;display:flex;flex-direction:column;
  justify-content:center;border-right:0.5px solid var(--border);
  position:relative;z-index:1;
}
.hero-bg-orb{
  position:absolute;top:-120px;left:-80px;
  width:480px;height:480px;border-radius:50%;
  background:radial-gradient(circle,rgba(184,147,90,0.1) 0%,transparent 70%);
  pointer-events:none;animation:float 8s ease-in-out infinite;
}
.hero-eyebrow{
  font-size:10px;letter-spacing:0.22em;text-transform:uppercase;
  color:var(--accent);margin-bottom:28px;
  display:flex;align-items:center;gap:12px;
}
.hero-eyebrow::before{content:'';width:28px;height:1px;background:var(--accent);}
.hero-title{
  font-family:'Cormorant Garamond',serif;font-size:74px;font-weight:300;
  line-height:0.98;margin-bottom:32px;letter-spacing:-0.02em;
}
.hero-title em{font-style:italic;color:var(--accent);}
.hero-desc{font-size:14px;color:var(--muted);line-height:1.9;margin-bottom:48px;max-width:360px;font-weight:300;}
.hero-actions{display:flex;gap:14px;align-items:center;}
.btn-primary{
  background:var(--dark);color:var(--cream);border:none;
  padding:15px 36px;font-size:11px;letter-spacing:0.14em;text-transform:uppercase;
  cursor:pointer;transition:all 0.3s;font-family:'DM Sans',sans-serif;
  position:relative;overflow:hidden;border-radius:1px;
}
.btn-primary::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,var(--accent),#8A6A3A);
  transform:translateY(100%);transition:transform 0.35s cubic-bezier(0.22,1,0.36,1);
}
.btn-primary:hover::before{transform:translateY(0);}
.btn-primary span{position:relative;z-index:1;}
.btn-secondary{
  font-size:11px;letter-spacing:0.12em;text-transform:uppercase;color:var(--muted);
  cursor:pointer;border:none;background:none;font-family:'DM Sans',sans-serif;
  position:relative;padding-bottom:2px;transition:color 0.2s;
}
.btn-secondary::after{
  content:'';position:absolute;bottom:0;left:0;right:0;
  height:1px;background:var(--muted);transition:background 0.2s;
}
.btn-secondary:hover{color:var(--dark);}
.btn-secondary:hover::after{background:var(--dark);}

.hero-stats{
  display:flex;gap:40px;margin-top:60px;
  padding-top:40px;border-top:0.5px solid var(--border);
}
.stat-num{
  font-family:'Cormorant Garamond',serif;font-size:38px;font-weight:400;color:var(--dark);
  line-height:1;margin-bottom:4px;
}
.stat-label{font-size:10px;color:var(--muted);letter-spacing:0.1em;text-transform:uppercase;}

.hero-right{
  background:var(--cream2);display:flex;flex-direction:column;
  align-items:center;justify-content:center;position:relative;padding:60px;gap:20px;
}
.hero-right::before{
  content:'';position:absolute;top:0;left:0;right:0;bottom:0;
  background:radial-gradient(ellipse at 80% 20%,rgba(184,147,90,0.07) 0%,transparent 60%);
  pointer-events:none;
}
.hero-featured-card{
  background:var(--white);width:100%;max-width:300px;
  border:0.5px solid var(--border);position:relative;overflow:hidden;
  box-shadow:var(--shadow);transition:transform 0.4s cubic-bezier(0.22,1,0.36,1),box-shadow 0.4s;
}
.hero-featured-card:hover{transform:translateY(-6px);box-shadow:var(--shadow-lg);}
.hero-card-img{height:280px;display:flex;align-items:center;justify-content:center;position:relative;overflow:hidden;}
.hero-card-circle{
  width:150px;height:150px;border-radius:50%;
  background:linear-gradient(145deg,#D4C5A0 0%,#B8A47A 50%,#9A8060 100%);
  position:relative;transition:transform 0.5s cubic-bezier(0.22,1,0.36,1);
  box-shadow:0 12px 32px rgba(184,147,90,0.3);
}
.hero-featured-card:hover .hero-card-circle{transform:scale(1.08) rotate(5deg);}
.hero-card-badge{
  position:absolute;top:18px;right:18px;
  background:var(--dark);color:var(--cream);
  font-size:9px;letter-spacing:0.14em;text-transform:uppercase;padding:5px 12px;
}
.hero-card-info{padding:22px;border-top:0.5px solid var(--border);}
.hero-card-name{font-size:13px;font-weight:500;margin-bottom:4px;letter-spacing:0.02em;}
.hero-card-price{font-family:'Cormorant Garamond',serif;font-size:28px;font-weight:400;color:var(--accent);}

.hero-mini-cards{display:flex;gap:12px;width:100%;max-width:300px;}
.mini-card{
  flex:1;background:var(--white);border:0.5px solid var(--border);
  padding:14px;cursor:pointer;transition:all 0.3s cubic-bezier(0.22,1,0.36,1);
  box-shadow:var(--shadow);
}
.mini-card:hover{border-color:var(--accent);transform:translateY(-3px);box-shadow:0 8px 24px rgba(22,20,15,0.1);}
.mini-card-dot{width:32px;height:32px;border-radius:50%;margin-bottom:10px;transition:transform 0.3s;}
.mini-card:hover .mini-card-dot{transform:scale(1.12);}
.mini-card-name{font-size:10px;font-weight:500;margin-bottom:2px;letter-spacing:0.04em;}
.mini-card-price{font-family:'Cormorant Garamond',serif;font-size:15px;color:var(--accent);}

/* ── CATEGORY BAR ── */
.cat-bar{
  display:flex;border-bottom:0.5px solid var(--border);
  overflow-x:auto;position:sticky;top:64px;z-index:80;
  background:rgba(245,241,234,0.96);backdrop-filter:blur(8px);
}
.cat-bar::-webkit-scrollbar{display:none;}
.cat-btn{
  font-size:10px;letter-spacing:0.14em;text-transform:uppercase;
  padding:15px 26px;cursor:pointer;border:none;background:none;
  color:var(--muted);white-space:nowrap;transition:all 0.25s;
  border-bottom:2px solid transparent;font-family:'DM Sans',sans-serif;
  border-right:0.5px solid var(--border);position:relative;overflow:hidden;
}
.cat-btn::before{
  content:'';position:absolute;inset:0;background:rgba(184,147,90,0.06);
  transform:scaleX(0);transition:transform 0.25s;transform-origin:left;
}
.cat-btn:hover::before{transform:scaleX(1);}
.cat-btn:hover{color:var(--dark);}
.cat-btn.active{color:var(--dark);border-bottom-color:var(--accent);}

/* ── PRODUCTS ── */
.section{padding:60px 48px;}
.section-header{display:flex;align-items:baseline;justify-content:space-between;margin-bottom:44px;}
.section-title{font-family:'Cormorant Garamond',serif;font-size:44px;font-weight:300;}
.section-title em{font-style:italic;color:var(--accent);}
.section-sub{font-size:11px;color:var(--muted);letter-spacing:0.1em;text-transform:uppercase;}

.products-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:0;}
.product-card{
  border:0.5px solid var(--border);margin-right:-0.5px;margin-bottom:-0.5px;
  cursor:pointer;transition:all 0.35s cubic-bezier(0.22,1,0.36,1);
  position:relative;overflow:hidden;background:var(--white);
}
.product-card::after{
  content:'';position:absolute;inset:0;border:1.5px solid transparent;
  transition:border-color 0.3s;pointer-events:none;
}
.product-card:hover{z-index:2;box-shadow:0 12px 48px rgba(22,20,15,0.12);}
.product-card:hover::after{border-color:var(--accent);}
.product-card:hover .product-img-inner{transform:scale(1.1) rotate(3deg);}
.product-card:hover .btn-add{background:var(--dark);color:var(--cream);border-color:var(--dark);}

.product-img{height:200px;display:flex;align-items:center;justify-content:center;overflow:hidden;position:relative;}
.product-img-inner{width:96px;height:96px;border-radius:50%;transition:transform 0.45s cubic-bezier(0.22,1,0.36,1);box-shadow:0 8px 24px rgba(22,20,15,0.15);}
.product-badge{
  position:absolute;top:12px;left:12px;
  font-size:9px;letter-spacing:0.12em;text-transform:uppercase;padding:4px 9px;
}
.badge-new{background:var(--dark);color:var(--cream);}
.badge-sale{background:var(--pop);color:white;}
.product-info{padding:20px;border-top:0.5px solid var(--border);}
.product-cat{font-size:9px;color:var(--muted);letter-spacing:0.14em;text-transform:uppercase;margin-bottom:6px;}
.product-name{font-size:14px;font-weight:500;margin-bottom:4px;letter-spacing:0.01em;}
.product-desc{font-size:12px;color:var(--muted);margin-bottom:16px;line-height:1.6;font-weight:300;}
.product-footer{display:flex;align-items:center;justify-content:space-between;}
.product-price{font-family:'Cormorant Garamond',serif;font-size:22px;font-weight:400;}
.btn-add{
  font-size:9px;letter-spacing:0.12em;text-transform:uppercase;
  padding:8px 14px;border:0.5px solid var(--border);background:transparent;
  cursor:pointer;transition:all 0.25s;color:var(--dark);font-family:'DM Sans',sans-serif;
}

/* ── TRUST ── */
.trust-section{
  display:grid;grid-template-columns:repeat(4,1fr);
  border-top:0.5px solid var(--border);border-bottom:0.5px solid var(--border);
  background:var(--dark);
}
.trust-item{
  padding:40px 28px;border-right:0.5px solid rgba(253,251,247,0.06);
  text-align:center;transition:background 0.3s;
}
.trust-item:hover{background:rgba(184,147,90,0.06);}
.trust-item:last-child{border-right:none;}
.trust-icon{
  width:44px;height:44px;border-radius:50%;border:0.5px solid rgba(184,147,90,0.3);
  display:flex;align-items:center;justify-content:center;
  margin:0 auto 16px;font-size:18px;
  transition:border-color 0.3s,transform 0.3s;
}
.trust-item:hover .trust-icon{border-color:var(--accent);transform:scale(1.08);}
.trust-title{font-size:11px;font-weight:500;letter-spacing:0.12em;text-transform:uppercase;color:var(--cream);margin-bottom:8px;}
.trust-desc{font-size:12px;color:rgba(253,251,247,0.4);line-height:1.7;font-weight:300;}

/* ── ABOUT ── */
.about-section{display:grid;grid-template-columns:1fr 1fr;border-bottom:0.5px solid var(--border);}
.about-left{padding:80px 64px;border-right:0.5px solid var(--border);display:flex;flex-direction:column;justify-content:center;}
.about-right{background:var(--cream2);display:flex;align-items:center;justify-content:center;padding:60px;position:relative;overflow:hidden;}
.about-visual{
  width:260px;height:260px;border-radius:50%;
  background:linear-gradient(145deg,var(--accent2),var(--accent),#8A6A3A);
  display:flex;align-items:center;justify-content:center;
  font-family:'Cormorant Garamond',serif;font-size:80px;font-weight:300;
  color:rgba(253,251,247,0.9);position:relative;
  box-shadow:0 24px 64px rgba(184,147,90,0.35);
  animation:float 7s ease-in-out infinite;
}
.about-visual::before{
  content:'';position:absolute;inset:-20px;border-radius:50%;
  border:1px solid rgba(184,147,90,0.2);
}
.about-label{font-size:10px;letter-spacing:0.22em;text-transform:uppercase;color:var(--accent);margin-bottom:20px;}
.about-title{font-family:'Cormorant Garamond',serif;font-size:48px;font-weight:300;line-height:1.08;margin-bottom:24px;}
.about-title em{font-style:italic;}
.about-text{font-size:14px;color:var(--muted);line-height:1.95;margin-bottom:28px;font-weight:300;}

/* ── CONTACT ── */
.contact-section{padding:80px 48px;border-bottom:0.5px solid var(--border);}
.contact-grid{display:grid;grid-template-columns:1fr 1fr;gap:80px;margin-top:48px;}
.contact-info-title{font-family:'Cormorant Garamond',serif;font-size:32px;font-weight:300;margin-bottom:28px;}
.contact-item{display:flex;gap:16px;align-items:flex-start;margin-bottom:24px;}
.contact-icon{
  width:38px;height:38px;border:0.5px solid var(--border);
  display:flex;align-items:center;justify-content:center;font-size:14px;flex-shrink:0;
  transition:border-color 0.2s;
}
.contact-item:hover .contact-icon{border-color:var(--accent);}
.contact-item-label{font-size:10px;color:var(--muted);letter-spacing:0.1em;text-transform:uppercase;margin-bottom:4px;}
.contact-item-val{font-size:14px;font-weight:400;}
.contact-form{display:flex;flex-direction:column;gap:14px;}
.form-label{font-size:10px;letter-spacing:0.12em;text-transform:uppercase;color:var(--muted);}
.form-input,.form-textarea{
  border:0.5px solid var(--border);background:var(--white);
  padding:12px 16px;font-size:14px;font-family:'DM Sans',sans-serif;
  color:var(--dark);outline:none;transition:border-color 0.25s,box-shadow 0.25s;resize:none;
  border-radius:1px;
}
.form-input:focus,.form-textarea:focus{border-color:var(--accent);box-shadow:0 0 0 3px rgba(184,147,90,0.08);}
.form-textarea{height:120px;}

/* ── COLLAB ── */
.collab-section{
  background:var(--dark);padding:80px 48px;
  display:grid;grid-template-columns:1fr 1fr;gap:80px;align-items:center;
}
.collab-label{font-size:10px;letter-spacing:0.22em;text-transform:uppercase;color:var(--accent);margin-bottom:20px;}
.collab-title{font-family:'Cormorant Garamond',serif;font-size:48px;font-weight:300;color:var(--cream);line-height:1.08;margin-bottom:24px;}
.collab-title em{font-style:italic;color:var(--accent);}
.collab-text{font-size:14px;color:rgba(253,251,247,0.5);line-height:1.95;margin-bottom:36px;font-weight:300;}
.btn-primary-light{
  background:transparent;color:var(--cream);border:0.5px solid rgba(253,251,247,0.25);
  padding:15px 36px;font-size:11px;letter-spacing:0.14em;text-transform:uppercase;
  cursor:pointer;transition:all 0.3s;font-family:'DM Sans',sans-serif;
  border-radius:1px;position:relative;overflow:hidden;
}
.btn-primary-light::before{
  content:'';position:absolute;inset:0;background:var(--accent);
  transform:translateX(-100%);transition:transform 0.35s cubic-bezier(0.22,1,0.36,1);
}
.btn-primary-light:hover::before{transform:translateX(0);}
.btn-primary-light:hover{border-color:var(--accent);color:var(--dark);}
.btn-primary-light span{position:relative;z-index:1;}

.collab-right{display:flex;flex-direction:column;gap:16px;}
.collab-benefit{
  border:0.5px solid rgba(253,251,247,0.08);padding:22px;
  display:flex;gap:20px;align-items:flex-start;
  transition:all 0.3s;cursor:default;
}
.collab-benefit:hover{border-color:rgba(184,147,90,0.35);background:rgba(184,147,90,0.04);}
.collab-benefit-num{font-family:'Cormorant Garamond',serif;font-size:30px;font-weight:300;color:var(--accent);line-height:1;flex-shrink:0;}
.collab-benefit-title{font-size:13px;font-weight:500;color:var(--cream);margin-bottom:5px;}
.collab-benefit-desc{font-size:12px;color:rgba(253,251,247,0.4);line-height:1.75;font-weight:300;}

/* ── FOOTER ── */
footer{background:var(--dark2);padding:60px 48px 32px;border-top:0.5px solid rgba(253,251,247,0.06);}
.footer-top{display:grid;grid-template-columns:2fr 1fr 1fr 1fr;gap:48px;margin-bottom:48px;}
.footer-logo{font-family:'Cormorant Garamond',serif;font-size:26px;font-weight:400;color:var(--cream);margin-bottom:14px;}
.footer-logo span{color:var(--accent);}
.footer-tagline{font-size:13px;color:rgba(253,251,247,0.35);line-height:1.85;max-width:220px;font-weight:300;}
.footer-col-title{font-size:10px;letter-spacing:0.14em;text-transform:uppercase;color:var(--accent);margin-bottom:20px;}
.footer-links{list-style:none;display:flex;flex-direction:column;gap:11px;}
.footer-links a{font-size:13px;color:rgba(253,251,247,0.45);text-decoration:none;transition:color 0.2s;cursor:pointer;font-weight:300;}
.footer-links a:hover{color:var(--cream);}
.footer-bottom{display:flex;justify-content:space-between;align-items:center;padding-top:28px;border-top:0.5px solid rgba(253,251,247,0.06);}
.footer-copy{font-size:12px;color:rgba(253,251,247,0.25);font-weight:300;}
.footer-social{display:flex;gap:10px;}
.social-btn{
  width:34px;height:34px;border:0.5px solid rgba(253,251,247,0.12);
  display:flex;align-items:center;justify-content:center;
  cursor:pointer;color:rgba(253,251,247,0.35);font-size:12px;
  transition:all 0.25s;text-decoration:none;font-style:normal;
}
.social-btn:hover{border-color:var(--accent);color:var(--accent);}

/* ── MODALS ── */
.overlay{
  display:none;position:fixed;inset:0;
  background:rgba(22,20,15,0.5);backdrop-filter:blur(6px);
  z-index:200;align-items:center;justify-content:center;
}
.overlay.open{display:flex;}
.modal{
  background:var(--cream);width:420px;max-width:95vw;
  border:0.5px solid var(--border);position:relative;
  animation:scaleIn 0.3s cubic-bezier(0.22,1,0.36,1);
  box-shadow:var(--shadow-lg);
}
.modal-close{
  position:absolute;top:20px;right:20px;font-size:22px;
  cursor:pointer;color:var(--muted);border:none;background:none;line-height:1;
  transition:color 0.2s,transform 0.2s;
}
.modal-close:hover{color:var(--dark);transform:rotate(90deg);}
.modal-body{padding:48px;}
.modal-eyebrow{font-size:10px;letter-spacing:0.18em;text-transform:uppercase;color:var(--accent);margin-bottom:10px;}
.modal-title{font-family:'Cormorant Garamond',serif;font-size:36px;font-weight:300;margin-bottom:6px;}
.modal-sub{font-size:13px;color:var(--muted);margin-bottom:28px;font-weight:300;}
.modal-input{
  width:100%;border:0.5px solid var(--border);background:var(--white);
  padding:13px 16px;font-size:14px;font-family:'DM Sans',sans-serif;
  color:var(--dark);outline:none;transition:border-color 0.25s,box-shadow 0.25s;
  margin-bottom:10px;border-radius:1px;
}
.modal-input:focus{border-color:var(--accent);box-shadow:0 0 0 3px rgba(184,147,90,0.08);}
.modal-btn{
  width:100%;background:var(--dark);color:var(--cream);border:none;
  padding:15px;font-size:11px;letter-spacing:0.12em;text-transform:uppercase;
  cursor:pointer;font-family:'DM Sans',sans-serif;transition:background 0.25s;
  margin-top:4px;position:relative;overflow:hidden;
}
.modal-btn::before{
  content:'';position:absolute;inset:0;background:var(--accent);
  transform:translateX(-100%);transition:transform 0.35s cubic-bezier(0.22,1,0.36,1);
}
.modal-btn:hover::before{transform:translateX(0);}
.modal-btn span{position:relative;z-index:1;}
.modal-switch{font-size:12px;color:var(--muted);text-align:center;margin-top:18px;font-weight:300;}
.modal-switch a{color:var(--dark);cursor:pointer;text-decoration:underline;text-underline-offset:3px;}
.modal-divider{display:flex;align-items:center;gap:16px;margin:18px 0;}
.modal-divider::before,.modal-divider::after{content:'';flex:1;height:0.5px;background:var(--border);}
.modal-divider span{font-size:10px;color:var(--muted);text-transform:uppercase;letter-spacing:0.1em;}

/* ── CART ── */
.cart-panel{
  display:none;position:fixed;right:0;top:0;bottom:0;width:400px;
  background:var(--cream);border-left:0.5px solid var(--border);
  z-index:300;flex-direction:column;
  animation:slideIn 0.35s cubic-bezier(0.22,1,0.36,1);
  box-shadow:-8px 0 48px rgba(22,20,15,0.1);
}
.cart-panel.open{display:flex;}
.cart-head{padding:24px 28px;border-bottom:0.5px solid var(--border);display:flex;justify-content:space-between;align-items:center;}
.cart-title{font-family:'Cormorant Garamond',serif;font-size:28px;font-weight:300;}
.cart-title span{font-size:14px;font-weight:400;color:var(--muted);font-family:'DM Sans',sans-serif;margin-left:8px;}
.cart-x{font-size:24px;cursor:pointer;border:none;background:none;color:var(--muted);transition:color 0.2s,transform 0.25s;}
.cart-x:hover{color:var(--dark);transform:rotate(90deg);}
.cart-body{flex:1;overflow-y:auto;padding:20px 28px;display:flex;flex-direction:column;gap:16px;}
.cart-empty{text-align:center;padding:60px 0;color:var(--muted);}
.cart-empty-icon{font-size:36px;margin-bottom:16px;opacity:0.25;}
.cart-empty-text{font-size:13px;letter-spacing:0.06em;font-weight:300;}
.cart-item{
  display:flex;gap:14px;padding-bottom:16px;border-bottom:0.5px solid var(--border);
  animation:fadeUp 0.3s cubic-bezier(0.22,1,0.36,1);
}
.cart-item-img{width:60px;height:60px;border-radius:50%;flex-shrink:0;box-shadow:0 4px 12px rgba(22,20,15,0.12);}
.cart-item-details{flex:1;}
.cart-item-name{font-size:13px;font-weight:500;margin-bottom:3px;}
.cart-item-cat{font-size:10px;color:var(--muted);text-transform:uppercase;letter-spacing:0.08em;margin-bottom:8px;}
.cart-item-row{display:flex;justify-content:space-between;align-items:center;}
.cart-item-price{font-family:'Cormorant Garamond',serif;font-size:20px;}
.cart-qty{display:flex;align-items:center;gap:6px;}
.qty-btn{
  width:24px;height:24px;border:0.5px solid var(--border);background:none;
  display:flex;align-items:center;justify-content:center;cursor:pointer;font-size:14px;
  transition:all 0.2s;line-height:1;
}
.qty-btn:hover{background:var(--dark);color:var(--cream);border-color:var(--dark);}
.qty-num{font-size:13px;min-width:20px;text-align:center;}
.cart-item-remove{
  font-size:10px;color:var(--muted);cursor:pointer;letter-spacing:0.08em;text-transform:uppercase;
  text-decoration:none;margin-top:6px;display:block;border:none;background:none;
  font-family:'DM Sans',sans-serif;transition:color 0.2s;
}
.cart-item-remove:hover{color:var(--pop);}

.cart-foot{padding:20px 28px;border-top:0.5px solid var(--border);}
.cart-ship-note{
  display:flex;align-items:center;gap:10px;font-size:12px;color:var(--muted);
  padding:11px 14px;background:rgba(184,147,90,0.07);border:0.5px solid rgba(184,147,90,0.2);
  margin-bottom:16px;font-weight:300;
}
.cart-totals{margin-bottom:16px;}
.cart-subtotal{display:flex;justify-content:space-between;font-size:13px;color:var(--muted);margin-bottom:7px;font-weight:300;}
.cart-total{display:flex;justify-content:space-between;align-items:baseline;border-top:0.5px solid var(--border);padding-top:12px;margin-top:10px;}
.cart-total-label{font-size:12px;letter-spacing:0.1em;text-transform:uppercase;}
.cart-total-val{font-family:'Cormorant Garamond',serif;font-size:28px;font-weight:400;}
.btn-checkout{
  width:100%;background:var(--dark);color:var(--cream);border:none;
  padding:16px;font-size:11px;letter-spacing:0.14em;text-transform:uppercase;
  cursor:pointer;font-family:'DM Sans',sans-serif;transition:background 0.25s;
  position:relative;overflow:hidden;
}
.btn-checkout::before{
  content:'';position:absolute;inset:0;background:var(--accent);
  transform:translateX(-100%);transition:transform 0.35s cubic-bezier(0.22,1,0.36,1);
}
.btn-checkout:hover::before{transform:translateX(0);}
.btn-checkout span{position:relative;z-index:1;}
.cart-payments{display:flex;justify-content:center;gap:10px;margin-top:12px;opacity:0.4;}
.pay-badge{font-size:10px;letter-spacing:0.06em;border:0.5px solid var(--border);padding:4px 10px;}

/* ── CHECKOUT ── */
.checkout-steps{display:flex;margin-bottom:28px;border-bottom:0.5px solid var(--border);}
.step-tab{
  flex:1;text-align:center;padding:12px;font-size:10px;
  letter-spacing:0.1em;text-transform:uppercase;color:var(--muted);
  border-bottom:2px solid transparent;cursor:pointer;transition:all 0.25s;
}
.step-tab.active{color:var(--dark);border-bottom-color:var(--accent);}
.checkout-section{display:none;}
.checkout-section.active{display:block;animation:fadeUp 0.3s cubic-bezier(0.22,1,0.36,1);}
.checkout-row{display:grid;grid-template-columns:1fr 1fr;gap:12px;}

/* ── BOG PAYMENT ── */
.bog-notice{
  background:rgba(122,158,126,0.08);border:0.5px solid rgba(122,158,126,0.25);
  padding:14px 16px;margin-bottom:16px;display:flex;align-items:flex-start;gap:12px;
}
.bog-notice-icon{font-size:16px;flex-shrink:0;margin-top:1px;}
.bog-notice-text{font-size:12px;color:var(--muted);line-height:1.7;font-weight:300;}
.bog-notice-text strong{color:var(--dark);font-weight:500;}
.payment-methods{display:flex;gap:10px;margin-bottom:16px;}
.pay-method{
  flex:1;border:0.5px solid var(--border);padding:14px 10px;text-align:center;
  cursor:pointer;transition:all 0.25s;font-size:12px;
}
.pay-method:hover,.pay-method.active{border-color:var(--accent);background:rgba(184,147,90,0.05);}
.pay-method-icon{font-size:20px;margin-bottom:6px;}
.pay-method-label{font-size:10px;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);}
.bog-redirect-btn{
  width:100%;background:linear-gradient(135deg,#1A5276,#1F618D);
  color:white;border:none;padding:15px;font-size:11px;letter-spacing:0.12em;
  text-transform:uppercase;cursor:pointer;font-family:'DM Sans',sans-serif;
  transition:all 0.3s;margin-top:16px;display:flex;align-items:center;justify-content:center;gap:8px;
}
.bog-redirect-btn:hover{background:linear-gradient(135deg,#154360,#1A5276);}
.bog-logo-text{font-weight:700;font-size:13px;letter-spacing:0.05em;}
.loading-spinner{
  width:16px;height:16px;border:2px solid rgba(255,255,255,0.3);
  border-top-color:white;border-radius:50%;animation:spin 0.8s linear infinite;
  display:none;
}

/* ── PAYMENT PROCESSING OVERLAY ── */
.processing-overlay{
  display:none;position:fixed;inset:0;
  background:rgba(22,20,15,0.7);backdrop-filter:blur(8px);
  z-index:999;align-items:center;justify-content:center;flex-direction:column;gap:24px;
}
.processing-overlay.show{display:flex;}
.processing-circle{
  width:72px;height:72px;border:2px solid rgba(184,147,90,0.2);
  border-top-color:var(--accent);border-radius:50%;animation:spin 1s linear infinite;
}
.processing-text{color:var(--cream);font-size:14px;letter-spacing:0.08em;text-transform:uppercase;font-weight:300;}

/* ── ADMIN ── */
.admin-panel{display:none;position:fixed;inset:0;background:var(--cream);z-index:500;flex-direction:column;overflow:hidden;}
.admin-panel.open{display:flex;}
.admin-top{
  display:flex;align-items:center;justify-content:space-between;
  padding:0 32px;height:56px;background:var(--dark);border-bottom:0.5px solid rgba(255,255,255,0.08);
}
.admin-logo{font-family:'Cormorant Garamond',serif;font-size:20px;color:var(--cream);}
.admin-logo span{color:var(--accent);}
.admin-user{font-size:12px;color:rgba(253,251,247,0.45);letter-spacing:0.06em;font-weight:300;}
.btn-admin-exit{
  font-size:10px;letter-spacing:0.12em;text-transform:uppercase;
  background:none;border:0.5px solid rgba(253,251,247,0.15);color:rgba(253,251,247,0.5);
  padding:7px 14px;cursor:pointer;font-family:'DM Sans',sans-serif;transition:all 0.25s;
}
.btn-admin-exit:hover{border-color:var(--accent);color:var(--accent);}
.admin-body{display:flex;flex:1;overflow:hidden;}
.admin-sidebar{width:220px;background:var(--dark2);flex-shrink:0;padding:20px 0;border-right:0.5px solid rgba(255,255,255,0.04);}
.admin-nav-item{
  display:flex;align-items:center;gap:12px;padding:13px 24px;
  font-size:12px;letter-spacing:0.06em;color:rgba(253,251,247,0.35);
  cursor:pointer;transition:all 0.2s;border-left:2px solid transparent;font-weight:300;
}
.admin-nav-item:hover,.admin-nav-item.active{color:var(--cream);background:rgba(184,147,90,0.07);border-left-color:var(--accent);}
.admin-nav-icon{font-size:13px;}
.admin-content{flex:1;overflow-y:auto;padding:32px;}
.admin-section{display:none;}
.admin-section.active{display:block;animation:fadeUp 0.3s cubic-bezier(0.22,1,0.36,1);}
.admin-section-title{font-family:'Cormorant Garamond',serif;font-size:32px;font-weight:300;margin-bottom:6px;}
.admin-section-sub{font-size:13px;color:var(--muted);margin-bottom:28px;font-weight:300;}
.admin-stats-row{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-bottom:28px;}
.admin-stat{
  background:var(--white);border:0.5px solid var(--border);padding:20px 22px;
  transition:box-shadow 0.2s;
}
.admin-stat:hover{box-shadow:var(--shadow);}
.admin-stat-val{font-family:'Cormorant Garamond',serif;font-size:32px;font-weight:300;margin-bottom:4px;}
.admin-stat-label{font-size:10px;color:var(--muted);text-transform:uppercase;letter-spacing:0.1em;}
.admin-table{width:100%;border-collapse:collapse;background:var(--white);border:0.5px solid var(--border);}
.admin-table th{
  font-size:9px;letter-spacing:0.12em;text-transform:uppercase;color:var(--muted);
  padding:13px 16px;border-bottom:0.5px solid var(--border);text-align:left;font-weight:400;
  background:var(--cream2);
}
.admin-table td{padding:13px 16px;font-size:13px;border-bottom:0.5px solid var(--border);font-weight:300;}
.admin-table tr:last-child td{border-bottom:none;}
.admin-table tr:hover td{background:rgba(184,147,90,0.03);}
.td-img{width:34px;height:34px;border-radius:50%;display:inline-block;}
.td-price{font-family:'Cormorant Garamond',serif;font-size:16px;}
.td-cat{font-size:9px;letter-spacing:0.1em;text-transform:uppercase;color:var(--muted);}
.btn-edit,.btn-delete{
  font-size:9px;letter-spacing:0.1em;text-transform:uppercase;padding:5px 11px;
  cursor:pointer;border:0.5px solid var(--border);background:transparent;
  font-family:'DM Sans',sans-serif;transition:all 0.2s;
}
.btn-edit:hover{background:var(--dark);color:var(--cream);border-color:var(--dark);}
.btn-delete:hover{background:var(--danger);color:var(--cream);border-color:var(--danger);}
.admin-actions{display:flex;gap:6px;}
.admin-form-card{background:var(--white);border:0.5px solid var(--border);padding:28px;max-width:580px;}
.admin-form-grid{display:grid;grid-template-columns:1fr 1fr;gap:14px;}
.admin-form-group{display:flex;flex-direction:column;gap:7px;}
.admin-form-group.full{grid-column:1/-1;}
.admin-form-label{font-size:10px;letter-spacing:0.12em;text-transform:uppercase;color:var(--muted);}
.admin-form-input,.admin-form-select{
  border:0.5px solid var(--border);background:var(--cream);
  padding:11px 14px;font-size:14px;font-family:'DM Sans',sans-serif;
  color:var(--dark);outline:none;transition:border-color 0.25s,box-shadow 0.25s;font-weight:300;
}
.admin-form-input:focus,.admin-form-select:focus{border-color:var(--accent);box-shadow:0 0 0 3px rgba(184,147,90,0.08);}
.btn-save{
  background:var(--dark);color:var(--cream);border:none;
  padding:13px 32px;font-size:11px;letter-spacing:0.12em;text-transform:uppercase;
  cursor:pointer;font-family:'DM Sans',sans-serif;transition:background 0.25s;margin-top:18px;
}
.btn-save:hover{background:var(--accent);}

/* ── BOG INTEGRATION INFO ── */
.bog-integration-card{
  background:linear-gradient(135deg,#1A5276 0%,#1F618D 100%);
  border:none;padding:28px;max-width:580px;margin-bottom:24px;
  color:white;position:relative;overflow:hidden;
}
.bog-integration-card::before{
  content:'BOG';position:absolute;right:20px;top:50%;transform:translateY(-50%);
  font-size:72px;font-weight:900;opacity:0.06;letter-spacing:-2px;
}
.bog-card-title{font-size:13px;font-weight:500;letter-spacing:0.06em;text-transform:uppercase;margin-bottom:8px;opacity:0.8;}
.bog-card-status{display:flex;align-items:center;gap:8px;margin-bottom:16px;}
.bog-status-dot{width:8px;height:8px;border-radius:50%;background:#5CDB95;animation:pulse 2s infinite;}
.bog-status-text{font-size:14px;font-weight:400;}
.bog-card-desc{font-size:12px;opacity:0.6;line-height:1.7;font-weight:300;}
.bog-config-row{display:flex;gap:8px;margin-top:16px;}
.bog-config-input{
  flex:1;background:rgba(255,255,255,0.1);border:0.5px solid rgba(255,255,255,0.2);
  color:white;padding:10px 14px;font-size:12px;font-family:'DM Sans',sans-serif;
  outline:none;transition:border-color 0.2s;
}
.bog-config-input::placeholder{color:rgba(255,255,255,0.4);}
.bog-config-input:focus{border-color:rgba(255,255,255,0.5);}
.bog-config-btn{
  background:rgba(255,255,255,0.15);border:0.5px solid rgba(255,255,255,0.2);
  color:white;padding:10px 16px;font-size:10px;letter-spacing:0.1em;text-transform:uppercase;
  cursor:pointer;font-family:'DM Sans',sans-serif;transition:all 0.2s;white-space:nowrap;
}
.bog-config-btn:hover{background:rgba(255,255,255,0.25);}

/* ── TOAST ── */
.toast{
  position:fixed;bottom:28px;left:50%;transform:translateX(-50%) translateY(16px);
  background:var(--dark);color:var(--cream);padding:12px 22px;font-size:12px;
  letter-spacing:0.06em;opacity:0;transition:all 0.35s cubic-bezier(0.22,1,0.36,1);
  z-index:999;pointer-events:none;white-space:nowrap;display:flex;align-items:center;gap:10px;
  box-shadow:0 8px 32px rgba(22,20,15,0.2);
}
.toast.show{opacity:1;transform:translateX(-50%) translateY(0);}
.toast-dot{width:5px;height:5px;border-radius:50%;background:var(--accent);flex-shrink:0;}

/* ── PAGES ── */
.page-section{display:none;}
.page-section.active{display:block;}
.page-hero{
  padding:80px 48px;border-bottom:0.5px solid var(--border);
  display:flex;align-items:flex-end;justify-content:space-between;
}
.page-hero-title{font-family:'Cormorant Garamond',serif;font-size:64px;font-weight:300;line-height:1.0;}
.page-hero-title em{font-style:italic;color:var(--accent);}
.page-hero-desc{font-size:14px;color:var(--muted);max-width:300px;line-height:1.85;font-weight:300;}

/* ── RESPONSIVE ── */
@media(max-width:1100px){
  .products-grid{grid-template-columns:repeat(3,1fr);}
  .footer-top{grid-template-columns:1fr 1fr;}
}
@media(max-width:900px){
  nav{padding:0 24px;}
  .nav-links{display:none;}
  .hero{grid-template-columns:1fr;}
  .hero-right{display:none;}
  .hero-title{font-size:52px;}
  .about-section,.collab-section{grid-template-columns:1fr;}
  .products-grid{grid-template-columns:repeat(2,1fr);}
  .trust-section{grid-template-columns:1fr 1fr;}
  .contact-grid{grid-template-columns:1fr;}
  .cart-panel{width:100%;}
  .admin-stats-row{grid-template-columns:1fr 1fr;}
}
</style>
</head>
<body>

<!-- NAV -->
<nav id="main-nav">
  <a class="nav-logo" href="#">LUMI<span>·</span>SHOP</a>
  <ul class="nav-links">
    <li><a href="#" class="active" data-page="home">მთავარი</a></li>
    <li><a href="#" data-page="products">პროდუქცია</a></li>
    <li><a href="#" data-page="about">ჩვენს შესახებ</a></li>
    <li><a href="#" data-page="collab">თანამშრომლობა</a></li>
    <li><a href="#" data-page="contact">კონტაქტი</a></li>
  </ul>
  <div class="nav-right">
    <button class="btn-login" onclick="openAuth('login')">შესვლა / რეგისტრაცია</button>
    <button class="btn-cart" onclick="openCart()">
      <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M6 2L3 6v14a2 2 0 002 2h14a2 2 0 002-2V6l-3-4z"/><line x1="3" y1="6" x2="21" y2="6"/><path d="M16 10a4 4 0 01-8 0"/></svg>
      <span>კალათა</span> <span class="cart-badge" id="cart-count">0</span>
    </button>
  </div>
</nav>

<!-- ══ HOME PAGE ══ -->
<div class="page-section active" id="page-home">
  <section class="hero">
    <div class="hero-left">
      <div class="hero-bg-orb"></div>
      <div class="hero-eyebrow animate-up">ახალი კოლექცია 2025</div>
      <h1 class="hero-title animate-up delay-1">გემოვნების<br><em>ხელოვნება</em><br>ყოველ დეტალში</h1>
      <p class="hero-desc animate-up delay-2">გამორჩეული პრემიუმ პროდუქტები, რომლებიც ასახავს სტილს და ხარისხს. პირდაპირ თქვენამდე — სწრაფი მიწოდებით.</p>
      <div class="hero-actions animate-up delay-3">
        <button class="btn-primary" onclick="navigateTo('products')"><span>კოლექციის ნახვა →</span></button>
        <button class="btn-secondary" onclick="navigateTo('about')">ჩვენს შესახებ</button>
      </div>
      <div class="hero-stats animate-up delay-4">
        <div class="stat-item"><div class="stat-num">500+</div><div class="stat-label">პროდუქტი</div></div>
        <div class="stat-item"><div class="stat-num">12k</div><div class="stat-label">მყიდველი</div></div>
        <div class="stat-item"><div class="stat-num">4.9★</div><div class="stat-label">შეფასება</div></div>
      </div>
    </div>
    <div class="hero-right">
      <div class="hero-featured-card animate-up delay-2">
        <div class="hero-card-img" style="background:#F0EBE0;">
          <div class="hero-card-circle"></div>
        </div>
        <div class="hero-card-badge">New In</div>
        <div class="hero-card-info">
          <div class="hero-card-name">Rose Gold Serum</div>
          <div class="hero-card-price">₾ 149</div>
        </div>
      </div>
      <div class="hero-mini-cards animate-up delay-3">
        <div class="mini-card" onclick="addToCartById(2)">
          <div class="mini-card-dot" style="background:#8A9E8A;"></div>
          <div class="mini-card-name">Linen Pillow</div>
          <div class="mini-card-price">₾ 64</div>
        </div>
        <div class="mini-card" onclick="addToCartById(3)">
          <div class="mini-card-dot" style="background:#6A80B4;"></div>
          <div class="mini-card-name">Silk Scarf</div>
          <div class="mini-card-price">₾ 149</div>
        </div>
        <div class="mini-card" onclick="addToCartById(5)">
          <div class="mini-card-dot" style="background:#C0A880;"></div>
          <div class="mini-card-name">Pearl Set</div>
          <div class="mini-card-price">₾ 199</div>
        </div>
      </div>
    </div>
  </section>

  <div class="cat-bar" id="home-cats">
    <button class="cat-btn active" onclick="filterProducts(this,'all','home')">ყველა</button>
    <button class="cat-btn" onclick="filterProducts(this,'სილამაზე','home')">სილამაზე</button>
    <button class="cat-btn" onclick="filterProducts(this,'სახლი','home')">სახლი</button>
    <button class="cat-btn" onclick="filterProducts(this,'მოდა','home')">მოდა</button>
    <button class="cat-btn" onclick="filterProducts(this,'ჯანმრთელობა','home')">ჯანმრთელობა</button>
    <button class="cat-btn" onclick="filterProducts(this,'ელექტრონიკა','home')">ელექტრონიკა</button>
  </div>
  <section class="section">
    <div class="section-header">
      <h2 class="section-title">არჩეული <em>პროდუქტები</em></h2>
      <span class="section-sub">ხარისხი · სტილი · ღირებულება</span>
    </div>
    <div class="products-grid" id="home-grid"></div>
  </section>

  <div class="trust-section">
    <div class="trust-item">
      <div class="trust-icon">🔒</div>
      <div class="trust-title">BOG გადახდა</div>
      <div class="trust-desc">256-bit SSL · BOG · TBC · ბარათი</div>
    </div>
    <div class="trust-item">
      <div class="trust-icon">🚀</div>
      <div class="trust-title">QuickShipper</div>
      <div class="trust-desc">1–3 სამუშაო დღე · Tbilisi 24h</div>
    </div>
    <div class="trust-item">
      <div class="trust-icon">↩</div>
      <div class="trust-title">30-დღიანი გარანტია</div>
      <div class="trust-desc">უპირობო დაბრუნება · სრული ანაზღაურება</div>
    </div>
    <div class="trust-item">
      <div class="trust-icon">💬</div>
      <div class="trust-title">24/7 მხარდაჭერა</div>
      <div class="trust-desc">ჩატი · ელ.ფოსტა · ტელეფონი</div>
    </div>
  </div>
</div>

<!-- ══ PRODUCTS PAGE ══ -->
<div class="page-section" id="page-products">
  <div class="page-hero">
    <div><h1 class="page-hero-title">ჩვენი<br><em>პროდუქცია</em></h1></div>
    <p class="page-hero-desc">500-ზე მეტი გამორჩეული პროდუქტი 6 კატეგორიაში. ყველა ნივთი გადამოწმებული და სერტიფიცირებული.</p>
  </div>
  <div class="cat-bar" id="prod-cats">
    <button class="cat-btn active" onclick="filterProducts(this,'all','prod')">ყველა</button>
    <button class="cat-btn" onclick="filterProducts(this,'სილამაზე','prod')">სილამაზე</button>
    <button class="cat-btn" onclick="filterProducts(this,'სახლი','prod')">სახლი</button>
    <button class="cat-btn" onclick="filterProducts(this,'მოდა','prod')">მოდა</button>
    <button class="cat-btn" onclick="filterProducts(this,'ჯანმრთელობა','prod')">ჯანმრთელობა</button>
    <button class="cat-btn" onclick="filterProducts(this,'ელექტრონიკა','prod')">ელექტრონიკა</button>
  </div>
  <section class="section"><div class="products-grid" id="prod-grid"></div></section>
</div>

<!-- ══ ABOUT PAGE ══ -->
<div class="page-section" id="page-about">
  <div class="page-hero">
    <div><h1 class="page-hero-title">ჩვენს<br><em>შესახებ</em></h1></div>
    <p class="page-hero-desc">ჩვენ ვართ გუნდი, რომელიც სჯერა, რომ ხარისხი ყველასთვის ხელმისაწვდომი უნდა იყოს.</p>
  </div>
  <div class="about-section">
    <div class="about-left">
      <div class="about-label">ჩვენი ისტორია</div>
      <h2 class="about-title">2019 წლიდან<br><em>სიყვარულით</em><br>გაკეთებული</h2>
      <p class="about-text">LumiShop დაიწყო პატარა სტარტაპად, რომლის მიზანი იყო პრემიუმ ევროპული პროდუქტების ხელმისაწვდომობა საქართველოში. დღეს ჩვენ ვართ ქვეყნის ერთ-ერთი ყველაზე სანდო ონლაინ მაღაზია.</p>
      <p class="about-text">ჩვენი ყოველი პროდუქტი გადის მკაცრ ხარისხის კონტროლს. ვმუშაობთ მხოლოდ სერტიფიცირებულ მომწოდებლებთან.</p>
      <button class="btn-primary" style="margin-top:8px;" onclick="navigateTo('collab')"><span>გახდი პარტნიორი →</span></button>
    </div>
    <div class="about-right"><div class="about-visual">✦</div></div>
  </div>
  <div class="trust-section">
    <div class="trust-item"><div class="trust-icon" style="font-family:'Cormorant Garamond',serif;font-size:18px;">2019</div><div class="trust-title">დაარსდა</div><div class="trust-desc">თბილისში, ქართული ოჯახის მიერ</div></div>
    <div class="trust-item"><div class="trust-icon" style="font-family:'Cormorant Garamond',serif;font-size:18px;">500+</div><div class="trust-title">პროდუქტი</div><div class="trust-desc">6 სხვადასხვა კატეგორიაში</div></div>
    <div class="trust-item"><div class="trust-icon" style="font-family:'Cormorant Garamond',serif;font-size:18px;">12k</div><div class="trust-title">მომხმარებელი</div><div class="trust-desc">საქართველოს მასშტაბით</div></div>
    <div class="trust-item"><div class="trust-icon" style="font-family:'Cormorant Garamond',serif;font-size:18px;">4.9</div><div class="trust-title">შეფასება</div><div class="trust-desc">12,000+ მიმოხილვიდან</div></div>
  </div>
</div>

<!-- ══ COLLAB PAGE ══ -->
<div class="page-section" id="page-collab">
  <div class="collab-section" style="min-height:60vh;">
    <div class="collab-left">
      <div class="collab-label">პარტნიორობა</div>
      <h2 class="collab-title">გახდი ჩვენი<br><em>პარტნიორი</em></h2>
      <p class="collab-text">LumiShop გთავაზობს გამარტივებულ სისტემას ბიზნეს-პარტნიორებისთვის. თქვენი პროდუქტები ათასობით მომხმარებელს მიაღწევს.</p>
      <button class="btn-primary-light" onclick="navigateTo('contact')"><span>დაგვიკავშირდი →</span></button>
    </div>
    <div class="collab-right">
      <div class="collab-benefit"><div class="collab-benefit-num">01</div><div><div class="collab-benefit-title">კომისია 0%-დან</div><div class="collab-benefit-desc">სპეციალური პირობები გრძელვადიანი პარტნიორებისთვის.</div></div></div>
      <div class="collab-benefit"><div class="collab-benefit-num">02</div><div><div class="collab-benefit-title">მარკეტინგული მხარდაჭერა</div><div class="collab-benefit-desc">ჩვენი გუნდი ეხმარება თქვენი პროდუქტის პოპულარიზაციაში.</div></div></div>
      <div class="collab-benefit"><div class="collab-benefit-num">03</div><div><div class="collab-benefit-title">BOG & QuickShipper</div><div class="collab-benefit-desc">ინტეგრირებული გადახდა და მიწოდება. ჩვენ ვზრუნავთ ყველაფერზე.</div></div></div>
      <div class="collab-benefit"><div class="collab-benefit-num">04</div><div><div class="collab-benefit-title">ანალიტიკა & ანგარიშები</div><div class="collab-benefit-desc">რეალური დროის მონაცემები გაყიდვებზე და ROI-ზე.</div></div></div>
    </div>
  </div>
</div>

<!-- ══ CONTACT PAGE ══ -->
<div class="page-section" id="page-contact">
  <div class="page-hero">
    <div><h1 class="page-hero-title">დაგვი<em>კავშირდი</em></h1></div>
    <p class="page-hero-desc">გვიყევი შენი კითხვები, წინადადებები ან პარტნიორობის სურვილი. ვპასუხობთ 24 საათში.</p>
  </div>
  <div class="contact-section">
    <div class="contact-grid">
      <div class="contact-info">
        <h3 class="contact-info-title">საკონტაქტო ინფორმაცია</h3>
        <div class="contact-item"><div class="contact-icon">📍</div><div><div class="contact-item-label">მისამართი</div><div class="contact-item-val">თბილისი, ვაკე, ჭავჭავაძის გამზ. 45</div></div></div>
        <div class="contact-item"><div class="contact-icon">📞</div><div><div class="contact-item-label">ტელეფონი</div><div class="contact-item-val">+995 555 00 11 22</div></div></div>
        <div class="contact-item"><div class="contact-icon">✉</div><div><div class="contact-item-label">ელ. ფოსტა</div><div class="contact-item-val">hello@lumishop.ge</div></div></div>
        <div class="contact-item"><div class="contact-icon">🕐</div><div><div class="contact-item-label">სამუშაო საათები</div><div class="contact-item-val">ორშ–შაბ: 10:00 – 20:00</div></div></div>
      </div>
      <div class="contact-form">
        <h3 style="font-family:'Cormorant Garamond',serif;font-size:32px;font-weight:300;margin-bottom:24px;">შეტყობინების გაგზავნა</h3>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;">
          <div><label class="form-label" style="display:block;margin-bottom:6px;">სახელი</label><input class="form-input" type="text" placeholder="გიორგი"></div>
          <div><label class="form-label" style="display:block;margin-bottom:6px;">გვარი</label><input class="form-input" type="text" placeholder="ბერიძე"></div>
        </div>
        <div><label class="form-label" style="display:block;margin-bottom:6px;">ელ. ფოსტა</label><input class="form-input" type="email" placeholder="giorgi@example.com"></div>
        <div>
          <label class="form-label" style="display:block;margin-bottom:6px;">თემა</label>
          <select class="form-input" style="cursor:pointer;">
            <option>შეკვეთასთან დაკავშირებით</option>
            <option>პარტნიორობა</option>
            <option>ტექნიკური დახმარება</option>
            <option>სხვა</option>
          </select>
        </div>
        <div><label class="form-label" style="display:block;margin-bottom:6px;">შეტყობინება</label><textarea class="form-textarea" placeholder="თქვენი შეტყობინება..."></textarea></div>
        <button class="btn-primary" onclick="showToast('შეტყობინება გაიგზავნა! ✓')"><span>გაგზავნა →</span></button>
      </div>
    </div>
  </div>
</div>

<!-- FOOTER -->
<footer id="main-footer">
  <div class="footer-top">
    <div>
      <div class="footer-logo">LUMI<span>·</span>SHOP</div>
      <p class="footer-tagline">პრემიუმ პროდუქტები, BOG-ის უსაფრთხო გადახდით. თქვენთვის, ყოველ დღე.</p>
    </div>
    <div>
      <div class="footer-col-title">ნავიგაცია</div>
      <ul class="footer-links">
        <li><a onclick="navigateTo('home')">მთავარი</a></li>
        <li><a onclick="navigateTo('products')">პროდუქცია</a></li>
        <li><a onclick="navigateTo('about')">ჩვენს შესახებ</a></li>
        <li><a onclick="navigateTo('collab')">თანამშრომლობა</a></li>
        <li><a onclick="navigateTo('contact')">კონტაქტი</a></li>
      </ul>
    </div>
    <div>
      <div class="footer-col-title">სერვისი</div>
      <ul class="footer-links">
        <li><a href="#">მიწოდება</a></li>
        <li><a href="#">დაბრუნება</a></li>
        <li><a href="#">გარანტია</a></li>
        <li><a href="#">FAQ</a></li>
        <li><a onclick="openAuth('login')">ჩემი ანგარიში</a></li>
      </ul>
    </div>
    <div>
      <div class="footer-col-title">ადმინი</div>
      <ul class="footer-links">
        <li><a onclick="openAuth('admin')">ადმინ პანელი</a></li>
        <li><a href="#">კონფიდენციალობა</a></li>
        <li><a href="#">წესები</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <div class="footer-copy">© 2025 LumiShop · BOG Merchant Partner · ყველა უფლება დაცულია</div>
    <div class="footer-social">
      <a class="social-btn" href="#">f</a>
      <a class="social-btn" href="#">in</a>
      <a class="social-btn" href="#">ig</a>
      <a class="social-btn" href="#">yt</a>
    </div>
  </div>
</footer>

<!-- AUTH MODAL -->
<div class="overlay" id="auth-overlay" onclick="closeOverlayClick(event,'auth-overlay')">
  <div class="modal">
    <button class="modal-close" onclick="closeOverlay('auth-overlay')">×</button>
    <div class="modal-body" id="auth-body"></div>
  </div>
</div>

<!-- CHECKOUT MODAL -->
<div class="overlay" id="checkout-overlay" onclick="closeOverlayClick(event,'checkout-overlay')">
  <div class="modal" style="width:520px;">
    <button class="modal-close" onclick="closeOverlay('checkout-overlay')">×</button>
    <div class="modal-body">
      <div class="modal-eyebrow">გადახდა</div>
      <div class="modal-title" style="margin-bottom:20px;">შეკვეთის დასრულება</div>
      <div class="checkout-steps">
        <div class="step-tab active" onclick="goStep(0)">1. მიწოდება</div>
        <div class="step-tab" onclick="goStep(1)">2. გადახდა</div>
        <div class="step-tab" onclick="goStep(2)">3. დადასტურება</div>
      </div>

      <!-- STEP 0: DELIVERY -->
      <div class="checkout-section active" id="step-0">
        <div class="checkout-row">
          <div><label class="form-label" style="display:block;margin-bottom:6px;">სახელი</label><input class="modal-input" type="text" placeholder="სახელი"></div>
          <div><label class="form-label" style="display:block;margin-bottom:6px;">გვარი</label><input class="modal-input" type="text" placeholder="გვარი"></div>
        </div>
        <label class="form-label" style="display:block;margin:10px 0 6px;">მისამართი</label>
        <input class="modal-input" type="text" placeholder="ქუჩა, №">
        <div class="checkout-row" style="margin-top:10px;">
          <div><label class="form-label" style="display:block;margin-bottom:6px;">ქალაქი</label><input class="modal-input" type="text" value="თბილისი"></div>
          <div><label class="form-label" style="display:block;margin-bottom:6px;">ტელეფონი</label><input class="modal-input" type="tel" placeholder="+995"></div>
        </div>
        <div style="margin-top:14px;padding:13px;background:rgba(184,147,90,0.07);border:0.5px solid rgba(184,147,90,0.2);font-size:12px;color:var(--muted);font-weight:300;">
          🚀 QuickShipper — სავარაუდო მიტანა: <strong style="color:var(--dark);">1–2 სამუშაო დღე</strong>
        </div>
        <button class="modal-btn" style="margin-top:16px;" onclick="goStep(1)"><span>გაგრძელება →</span></button>
      </div>

      <!-- STEP 1: PAYMENT (BOG) -->
      <div class="checkout-section" id="step-1">
        <div class="bog-notice">
          <div class="bog-notice-icon">🔒</div>
          <div class="bog-notice-text">
            <strong>BOG გადახდის სისტემა</strong><br>
            თქვენ გადამისამართდებით BOG-ის უსაფრთხო გვერდზე. ბარათის მონაცემები მხოლოდ ბანკს გადაეცემა — ჩვენი საიტი მათ ვერ ხედავს.
          </div>
        </div>

        <div class="payment-methods">
          <div class="pay-method active" onclick="selectPayMethod(this)">
            <div class="pay-method-icon">🏦</div>
            <div class="pay-method-label">BOG</div>
          </div>
          <div class="pay-method" onclick="selectPayMethod(this)">
            <div class="pay-method-icon">💳</div>
            <div class="pay-method-label">TBC Pay</div>
          </div>
          <div class="pay-method" onclick="selectPayMethod(this)">
            <div class="pay-method-icon">📱</div>
            <div class="pay-method-label">Apple Pay</div>
          </div>
        </div>

        <div id="checkout-summary"></div>

        <button class="bog-redirect-btn" onclick="startBOGPayment()">
          <div class="loading-spinner" id="pay-spinner"></div>
          <span id="pay-btn-text">გადახდა BOG-ით →</span>
        </button>

        <div style="margin-top:12px;text-align:center;font-size:11px;color:var(--muted);font-weight:300;letter-spacing:0.04em;">
          🔒 256-bit SSL · PCI DSS Certified · BOG Partner
        </div>
      </div>

      <!-- STEP 2: CONFIRMED -->
      <div class="checkout-section" id="step-2">
        <div style="text-align:center;padding:36px 0;">
          <div style="width:64px;height:64px;border-radius:50%;background:rgba(74,122,90,0.1);border:1px solid rgba(74,122,90,0.2);display:flex;align-items:center;justify-content:center;margin:0 auto 20px;font-size:26px;animation:scaleIn 0.4s cubic-bezier(0.34,1.56,0.64,1);">✓</div>
          <div style="font-family:'Cormorant Garamond',serif;font-size:28px;margin-bottom:12px;font-weight:300;">შეკვეთა დადასტურდა!</div>
          <div style="font-size:13px;color:var(--muted);line-height:1.9;font-weight:300;">
            თქვენი შეკვეთა <strong style="color:var(--dark);">#LM-<span id="order-num"></span></strong> მიღებულია.<br>
            BOG გადახდა წარმატებით დასრულდა. ✓<br>
            QuickShipper მოგაწვდის 1–2 სამუშაო დღეში.<br>
            დადასტურება გაიგზავნა თქვენს ელ.ფოსტაზე.
          </div>
          <button class="modal-btn" style="margin-top:28px;" onclick="closeOverlay('checkout-overlay');clearCart();"><span>სახლში დაბრუნება</span></button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- CART PANEL -->
<div class="cart-panel" id="cart-panel">
  <div class="cart-head">
    <div class="cart-title">კალათა <span id="cart-panel-count"></span></div>
    <button class="cart-x" onclick="closeCart()">×</button>
  </div>
  <div class="cart-body" id="cart-body"></div>
  <div class="cart-foot" id="cart-foot"></div>
</div>

<!-- ADMIN PANEL -->
<div class="admin-panel" id="admin-panel">
  <div class="admin-top">
    <div class="admin-logo">LUMI<span>·</span>SHOP <span style="font-size:11px;color:rgba(253,251,247,0.25);margin-left:8px;">ადმინ</span></div>
    <span class="admin-user">admin@lumishop.ge</span>
    <button class="btn-admin-exit" onclick="closeAdmin()">← საიტზე დაბრუნება</button>
  </div>
  <div class="admin-body">
    <div class="admin-sidebar">
      <div class="admin-nav-item active" onclick="adminNav(this,'dashboard')"><span class="admin-nav-icon">◈</span> Dashboard</div>
      <div class="admin-nav-item" onclick="adminNav(this,'products')"><span class="admin-nav-icon">◎</span> პროდუქტები</div>
      <div class="admin-nav-item" onclick="adminNav(this,'add')"><span class="admin-nav-icon">+</span> პროდუქტის დამატება</div>
      <div class="admin-nav-item" onclick="adminNav(this,'orders')"><span class="admin-nav-icon">◇</span> შეკვეთები</div>
      <div class="admin-nav-item" onclick="adminNav(this,'users')"><span class="admin-nav-icon">○</span> მომხმარებლები</div>
      <div class="admin-nav-item" onclick="adminNav(this,'bog')"><span class="admin-nav-icon">🏦</span> BOG გადახდა</div>
      <div class="admin-nav-item" onclick="adminNav(this,'shipping')"><span class="admin-nav-icon">→</span> QuickShipper</div>
    </div>
    <div class="admin-content">
      <!-- DASHBOARD -->
      <div class="admin-section active" id="admin-dashboard">
        <div class="admin-section-title">Dashboard</div>
        <div class="admin-section-sub">LumiShop-ის ოპერაციების მიმოხილვა</div>
        <div class="admin-stats-row">
          <div class="admin-stat"><div class="admin-stat-val">₾ 24,820</div><div class="admin-stat-label">ამ თვის შემოსავალი</div></div>
          <div class="admin-stat"><div class="admin-stat-val">142</div><div class="admin-stat-label">შეკვეთები</div></div>
          <div class="admin-stat"><div class="admin-stat-val" id="admin-prod-count">8</div><div class="admin-stat-label">პროდუქტი</div></div>
          <div class="admin-stat"><div class="admin-stat-val">98%</div><div class="admin-stat-label">კმაყოფილება</div></div>
        </div>
        <table class="admin-table">
          <thead><tr><th>სტატუსი</th><th>შეკვეთა</th><th>მომხმარებელი</th><th>თანხა</th><th>BOG / QS</th></tr></thead>
          <tbody>
            <tr><td><span style="color:var(--success);font-size:11px;">● მიტანილი</span></td><td>#LM-1041</td><td>ნინო ბ.</td><td class="td-price">₾ 312</td><td style="font-size:11px;color:var(--muted);">BOG-9821 · QS-4892</td></tr>
            <tr><td><span style="color:var(--accent);font-size:11px;">● გზაშია</span></td><td>#LM-1040</td><td>გიორგი კ.</td><td class="td-price">₾ 149</td><td style="font-size:11px;color:var(--muted);">BOG-9820 · QS-4891</td></tr>
            <tr><td><span style="color:var(--muted);font-size:11px;">● მუშავდება</span></td><td>#LM-1039</td><td>მარიამ ს.</td><td class="td-price">₾ 89</td><td style="font-size:11px;color:var(--muted);">BOG-9819 · —</td></tr>
            <tr><td><span style="color:var(--success);font-size:11px;">● მიტანილი</span></td><td>#LM-1038</td><td>დავით მ.</td><td class="td-price">₾ 520</td><td style="font-size:11px;color:var(--muted);">BOG-9818 · QS-4890</td></tr>
          </tbody>
        </table>
      </div>

      <!-- PRODUCTS -->
      <div class="admin-section" id="admin-products">
        <div class="admin-section-title">პროდუქტები</div>
        <div class="admin-section-sub">ყველა პროდუქტის მართვა</div>
        <table class="admin-table" id="admin-prod-table">
          <thead><tr><th>სურათი</th><th>დასახელება</th><th>კატეგორია</th><th>ფასი</th><th>მოქმედება</th></tr></thead>
          <tbody id="admin-prod-tbody"></tbody>
        </table>
      </div>

      <!-- ADD PRODUCT -->
      <div class="admin-section" id="admin-add">
        <div class="admin-section-title">პროდუქტის <span style="font-style:italic;color:var(--accent);">დამატება</span></div>
        <div class="admin-section-sub">ახალი პროდუქტი დაამატე კატალოგში</div>
        <div class="admin-form-card">
          <div class="admin-form-grid">
            <div class="admin-form-group"><label class="admin-form-label">პროდუქტის სახელი</label><input class="admin-form-input" type="text" id="new-name" placeholder="მაგ: Vitamin C Serum"></div>
            <div class="admin-form-group"><label class="admin-form-label">ფასი (₾)</label><input class="admin-form-input" type="number" id="new-price" placeholder="89"></div>
            <div class="admin-form-group"><label class="admin-form-label">კატეგორია</label>
              <select class="admin-form-select" id="new-cat">
                <option value="სილამაზე">სილამაზე</option>
                <option value="სახლი">სახლი</option>
                <option value="მოდა">მოდა</option>
                <option value="ჯანმრთელობა">ჯანმრთელობა</option>
                <option value="ელექტრონიკა">ელექტრონიკა</option>
              </select>
            </div>
            <div class="admin-form-group"><label class="admin-form-label">ბეჯი</label>
              <select class="admin-form-select" id="new-badge">
                <option value="">— არ არის —</option>
                <option value="new">New</option>
                <option value="sale">Sale</option>
              </select>
            </div>
            <div class="admin-form-group"><label class="admin-form-label">ფერი</label><input class="admin-form-input" type="color" id="new-color" value="#C5A96A" style="cursor:pointer;height:42px;"></div>
            <div class="admin-form-group"><label class="admin-form-label">ფონი</label><input class="admin-form-input" type="color" id="new-bg" value="#F7F4EF" style="cursor:pointer;height:42px;"></div>
            <div class="admin-form-group full"><label class="admin-form-label">აღწერა</label><input class="admin-form-input" type="text" id="new-desc" placeholder="მოკლე აღწერა..."></div>
          </div>
          <button class="btn-save" onclick="addProduct()">+ პროდუქტის შენახვა</button>
        </div>
      </div>

      <!-- ORDERS -->
      <div class="admin-section" id="admin-orders">
        <div class="admin-section-title">შეკვეთები</div>
        <div class="admin-section-sub">ყველა შეკვეთა და BOG გადახდის სტატუსი</div>
        <table class="admin-table">
          <thead><tr><th>შეკვეთა</th><th>მომხმარებელი</th><th>თარიღი</th><th>თანხა</th><th>BOG სტატუსი</th></tr></thead>
          <tbody>
            <tr><td>#LM-1041</td><td>ნინო ბ.</td><td>2025-04-30</td><td class="td-price">₾ 312</td><td><span style="font-size:11px;padding:4px 10px;background:rgba(74,122,90,0.1);color:var(--success);">✓ გადახდილი</span></td></tr>
            <tr><td>#LM-1040</td><td>გიორგი კ.</td><td>2025-04-29</td><td class="td-price">₾ 149</td><td><span style="font-size:11px;padding:4px 10px;background:rgba(184,147,90,0.1);color:var(--accent);">✓ გადახდილი</span></td></tr>
            <tr><td>#LM-1039</td><td>მარიამ ს.</td><td>2025-04-29</td><td class="td-price">₾ 89</td><td><span style="font-size:11px;padding:4px 10px;background:rgba(138,136,128,0.1);color:var(--muted);">⏳ პენდინგი</span></td></tr>
            <tr><td>#LM-1038</td><td>დავით მ.</td><td>2025-04-28</td><td class="td-price">₾ 520</td><td><span style="font-size:11px;padding:4px 10px;background:rgba(74,122,90,0.1);color:var(--success);">✓ გადახდილი</span></td></tr>
          </tbody>
        </table>
      </div>

      <!-- USERS -->
      <div class="admin-section" id="admin-users">
        <div class="admin-section-title">მომხმარებლები</div>
        <div class="admin-section-sub">რეგისტრირებული მომხმარებლები</div>
        <table class="admin-table">
          <thead><tr><th>ID</th><th>სახელი</th><th>ელ. ფოსტა</th><th>შეკვეთები</th><th>სტატუსი</th></tr></thead>
          <tbody>
            <tr><td>#U001</td><td>ნინო ბ.</td><td>nino@mail.ge</td><td>12</td><td><span style="font-size:11px;color:var(--success);">● აქტიური</span></td></tr>
            <tr><td>#U002</td><td>გიორგი კ.</td><td>giorgi@mail.ge</td><td>7</td><td><span style="font-size:11px;color:var(--success);">● აქტიური</span></td></tr>
            <tr><td>#U003</td><td>მარიამ ს.</td><td>mariam@mail.ge</td><td>3</td><td><span style="font-size:11px;color:var(--success);">● აქტიური</span></td></tr>
            <tr><td>#U004</td><td>დავით მ.</td><td>davit@mail.ge</td><td>19</td><td><span style="font-size:11px;color:var(--success);">● აქტიური</span></td></tr>
          </tbody>
        </table>
      </div>

      <!-- BOG PAYMENT ADMIN -->
      <div class="admin-section" id="admin-bog">
        <div class="admin-section-title">BOG <span style="font-style:italic;color:var(--accent);">გადახდა</span></div>
        <div class="admin-section-sub">Bank of Georgia - Merchant Integration Panel</div>

        <div class="bog-integration-card">
          <div class="bog-card-title">BOG Merchant სტატუსი</div>
          <div class="bog-card-status">
            <div class="bog-status-dot"></div>
            <div class="bog-status-text">კავშირი აქტიურია · ipay.ge</div>
          </div>
          <div class="bog-card-desc">
            გადახდები მუშავდება BOG-ის ipay.ge სერვისით. ფული ყოველ 24 საათში ჩაირიცხება თქვენს BOG Merchant ანგარიშზე.
          </div>
          <div class="bog-config-row">
            <input class="bog-config-input" type="text" placeholder="Client ID: bog_live_xxxxxxxx" id="bog-client-id">
            <input class="bog-config-input" type="password" placeholder="Client Secret" id="bog-secret">
            <button class="bog-config-btn" onclick="saveBOGConfig()">შენახვა</button>
          </div>
        </div>

        <div class="admin-stats-row" style="grid-template-columns:repeat(3,1fr);">
          <div class="admin-stat"><div class="admin-stat-val" style="color:var(--success);">₾ 24,820</div><div class="admin-stat-label">BOG-ით მიღებული</div></div>
          <div class="admin-stat"><div class="admin-stat-val">142</div><div class="admin-stat-label">წარმატებული ტრანზაქცია</div></div>
          <div class="admin-stat"><div class="admin-stat-val">2</div><div class="admin-stat-label">გაუქმებული / დაბრუნება</div></div>
        </div>

        <table class="admin-table">
          <thead><tr><th>BOG Transaction ID</th><th>შეკვეთა</th><th>თანხა</th><th>მეთოდი</th><th>სტატუსი</th><th>თარიღი</th></tr></thead>
          <tbody>
            <tr><td style="font-family:monospace;font-size:11px;">BOG-TXN-9821</td><td>#LM-1041</td><td class="td-price">₾ 312</td><td style="font-size:11px;">VISA ****4821</td><td><span style="font-size:11px;color:var(--success);">✓ SUCCESS</span></td><td style="font-size:11px;color:var(--muted);">2025-04-30 14:22</td></tr>
            <tr><td style="font-family:monospace;font-size:11px;">BOG-TXN-9820</td><td>#LM-1040</td><td class="td-price">₾ 149</td><td style="font-size:11px;">MC ****7734</td><td><span style="font-size:11px;color:var(--success);">✓ SUCCESS</span></td><td style="font-size:11px;color:var(--muted);">2025-04-29 11:05</td></tr>
            <tr><td style="font-family:monospace;font-size:11px;">BOG-TXN-9819</td><td>#LM-1039</td><td class="td-price">₾ 89</td><td style="font-size:11px;">BOG Pay</td><td><span style="font-size:11px;color:var(--accent);">⏳ PENDING</span></td><td style="font-size:11px;color:var(--muted);">2025-04-29 09:41</td></tr>
            <tr><td style="font-family:monospace;font-size:11px;">BOG-TXN-9818</td><td>#LM-1038</td><td class="td-price">₾ 520</td><td style="font-size:11px;">VISA ****2291</td><td><span style="font-size:11px;color:var(--success);">✓ SUCCESS</span></td><td style="font-size:11px;color:var(--muted);">2025-04-28 16:50</td></tr>
          </tbody>
        </table>
      </div>

      <!-- QUICKSHIPPER -->
      <div class="admin-section" id="admin-shipping">
        <div class="admin-section-title">QuickShipper</div>
        <div class="admin-section-sub">მიწოდების სისტემის ინტეგრაცია</div>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-bottom:24px;">
          <div class="admin-stat" style="background:rgba(74,122,90,0.04);border-color:rgba(74,122,90,0.15);"><div class="admin-stat-val" style="color:var(--success);">● სისტემა</div><div class="admin-stat-label">კავშირი აქტიურია</div></div>
          <div class="admin-stat"><div class="admin-stat-val">1.8 დღე</div><div class="admin-stat-label">საშუალო მიტანა</div></div>
          <div class="admin-stat"><div class="admin-stat-val">38</div><div class="admin-stat-label">გზაში (ეს კვირა)</div></div>
          <div class="admin-stat"><div class="admin-stat-val">99.2%</div><div class="admin-stat-label">წარმატებული მიტანა</div></div>
        </div>
        <table class="admin-table">
          <thead><tr><th>QS ტრეკინგი</th><th>შეკვეთა</th><th>BOG ტრანზ.</th><th>სტატუსი</th><th>ETA</th></tr></thead>
          <tbody>
            <tr><td style="font-family:monospace;font-size:11px;">QS-4892</td><td>#LM-1041</td><td style="font-size:11px;color:var(--muted);">BOG-TXN-9821</td><td><span style="font-size:11px;color:var(--success);">მიტანილი</span></td><td style="font-size:11px;color:var(--muted);">2025-04-30</td></tr>
            <tr><td style="font-family:monospace;font-size:11px;">QS-4891</td><td>#LM-1040</td><td style="font-size:11px;color:var(--muted);">BOG-TXN-9820</td><td><span style="font-size:11px;color:var(--accent);">გზაშია</span></td><td style="font-size:11px;color:var(--muted);">2025-05-02</td></tr>
            <tr><td style="font-family:monospace;font-size:11px;">QS-4890</td><td>#LM-1038</td><td style="font-size:11px;color:var(--muted);">BOG-TXN-9818</td><td><span style="font-size:11px;color:var(--success);">მიტანილი</span></td><td style="font-size:11px;color:var(--muted);">2025-04-28</td></tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</div>

<!-- PAYMENT PROCESSING OVERLAY -->
<div class="processing-overlay" id="processing-overlay">
  <div class="processing-circle"></div>
  <div class="processing-text">BOG-ზე გადამისამართება...</div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"><span class="toast-dot"></span><span id="toast-msg"></span></div>

<script>
// ── DATA ──
let products = [
  {id:1,name:"Rose Gold Serum",cat:"სილამაზე",price:149,bg:"#FFF0F0",col:"#C4747A",desc:"გამაახლებელი სეირუმი ვარდის ოქროთი",badge:"new"},
  {id:2,name:"Linen Pillow",cat:"სახლი",price:64,bg:"#F0EDE6",col:"#8A9E8A",desc:"ბუნებრივი სელის ბალიში",badge:""},
  {id:3,name:"Silk Scarf",cat:"მოდა",price:149,bg:"#E8EDF5",col:"#6A80B4",desc:"100% ბუნებრივი აბრეშუმი",badge:"new"},
  {id:4,name:"Herbal Drops",cat:"ჯანმრთელობა",price:45,bg:"#EAF0EA",col:"#6A9A6A",desc:"მცენარეული კომპლექსი",badge:""},
  {id:5,name:"Pearl Earrings",cat:"მოდა",price:199,bg:"#F5F0E8",col:"#C0A880",desc:"მარგალიტის ყურსაბამები",badge:"new"},
  {id:6,name:"Smart Desk Lamp",cat:"ელექტრონიკა",price:120,bg:"#EEEAF5",col:"#8A78C0",desc:"LED, USB-C დამტენი",badge:""},
  {id:7,name:"Clay Face Mask",cat:"სილამაზე",price:55,bg:"#FFF5EC",col:"#C09060",desc:"თიხის სახის ნიღაბი",badge:"sale"},
  {id:8,name:"Yoga Mat Premium",cat:"ჯანმრთელობა",price:89,bg:"#EAFAEA",col:"#5A9A6A",desc:"ანტი-სლიპ, 6mm",badge:""},
];
let nextId = 9;
let cart = [];

// ── NAV SCROLL ──
window.addEventListener('scroll',()=>{
  document.getElementById('main-nav').classList.toggle('scrolled',window.scrollY > 8);
});

// ── NAVIGATION ──
function navigateTo(page){
  document.querySelectorAll('.page-section').forEach(s=>s.classList.remove('active'));
  const el = document.getElementById('page-'+page);
  if(el) el.classList.add('active');
  document.querySelectorAll('.nav-links a').forEach(a=>a.classList.toggle('active',a.dataset.page===page));
  window.scrollTo({top:0,behavior:'smooth'});
  if(page==='products') renderGrid('prod-grid','all');
  if(page==='home') renderGrid('home-grid','all');
}
document.querySelectorAll('.nav-links a').forEach(a=>{
  a.addEventListener('click',function(e){
    e.preventDefault();
    if(this.dataset.page) navigateTo(this.dataset.page);
  });
});

// ── PRODUCTS ──
function renderGrid(gridId,cat){
  const grid = document.getElementById(gridId);
  if(!grid) return;
  const filtered = cat==='all'?products:products.filter(p=>p.cat===cat);
  grid.innerHTML = filtered.map((p,i)=>`
    <div class="product-card" style="animation:fadeUp 0.45s cubic-bezier(0.22,1,0.36,1) ${i*0.06}s both;">
      <div class="product-img" style="background:${p.bg};">
        <div class="product-img-inner" style="background:${p.col};"></div>
        ${p.badge==='new'?'<div class="product-badge badge-new">New</div>':''}
        ${p.badge==='sale'?'<div class="product-badge badge-sale">Sale</div>':''}
      </div>
      <div class="product-info">
        <div class="product-cat">${p.cat}</div>
        <div class="product-name">${p.name}</div>
        <div class="product-desc">${p.desc}</div>
        <div class="product-footer">
          <span class="product-price">₾ ${p.price}</span>
          <button class="btn-add" onclick="addToCartById(${p.id})">+ კალათა</button>
        </div>
      </div>
    </div>
  `).join('');
}

function filterProducts(btn,cat,ctx){
  const barId=ctx==='home'?'home-cats':'prod-cats';
  const gridId=ctx==='home'?'home-grid':'prod-grid';
  document.querySelectorAll('#'+barId+' .cat-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  renderGrid(gridId,cat);
}
renderGrid('home-grid','all');

// ── CART ──
function addToCartById(id){
  const p = products.find(x=>x.id===id);
  if(!p) return;
  const existing = cart.find(x=>x.id===id);
  if(existing) existing.qty++;
  else cart.push({...p,qty:1});
  updateCartBadge();
  showToast('"'+p.name+'" კალათაში დაემატა ✓');
}

function updateCartBadge(){
  const total = cart.reduce((a,b)=>a+b.qty,0);
  const badge = document.getElementById('cart-count');
  badge.textContent = total;
  badge.classList.remove('bump');
  void badge.offsetWidth;
  badge.classList.add('bump');
}

function openCart(){ renderCartPanel(); document.getElementById('cart-panel').classList.add('open'); }
function closeCart(){ document.getElementById('cart-panel').classList.remove('open'); }
function removeCartItem(id){ cart=cart.filter(x=>x.id!==id); updateCartBadge(); renderCartPanel(); }
function changeQty(id,delta){
  const item=cart.find(x=>x.id===id);
  if(!item) return;
  item.qty+=delta;
  if(item.qty<=0){ removeCartItem(id); return; }
  updateCartBadge(); renderCartPanel();
}

function renderCartPanel(){
  const body=document.getElementById('cart-body');
  const foot=document.getElementById('cart-foot');
  const countEl=document.getElementById('cart-panel-count');
  const total=cart.reduce((a,b)=>a+b.qty,0);
  countEl.textContent=total>0?'('+total+')':'';

  if(cart.length===0){
    body.innerHTML=`<div class="cart-empty"><div class="cart-empty-icon">◎</div><div class="cart-empty-text">კალათა ცარიელია</div></div>`;
    foot.innerHTML=''; return;
  }

  body.innerHTML=cart.map(item=>`
    <div class="cart-item">
      <div class="cart-item-img" style="background:${item.col};"></div>
      <div class="cart-item-details">
        <div class="cart-item-name">${item.name}</div>
        <div class="cart-item-cat">${item.cat}</div>
        <div class="cart-item-row">
          <div class="cart-item-price">₾ ${item.price*item.qty}</div>
          <div class="cart-qty">
            <button class="qty-btn" onclick="changeQty(${item.id},-1)">−</button>
            <span class="qty-num">${item.qty}</span>
            <button class="qty-btn" onclick="changeQty(${item.id},1)">+</button>
          </div>
        </div>
        <button class="cart-item-remove" onclick="removeCartItem(${item.id})">წაშლა</button>
      </div>
    </div>
  `).join('');

  const subtotal=cart.reduce((a,b)=>a+b.price*b.qty,0);
  const shipping=subtotal>=100?0:8;
  const totalVal=subtotal+shipping;

  foot.innerHTML=`
    <div class="cart-ship-note">🚀 ${subtotal>=100?'უფასო მიტანა QuickShipper-ით!':'კიდევ ₾'+Math.max(0,100-subtotal)+' — უფასო მიტანა'}</div>
    <div class="cart-totals">
      <div class="cart-subtotal"><span>ქვეჯამი</span><span>₾ ${subtotal}</span></div>
      <div class="cart-subtotal"><span>მიტანა (QuickShipper)</span><span>${shipping===0?'უფასო':'₾ '+shipping}</span></div>
      <div class="cart-total"><span class="cart-total-label">სულ</span><span class="cart-total-val">₾ ${totalVal}</span></div>
    </div>
    <button class="btn-checkout" onclick="openCheckout()"><span>BOG გადახდაზე გადასვლა →</span></button>
    <div class="cart-payments"><span class="pay-badge">BOG</span><span class="pay-badge">VISA</span><span class="pay-badge">MC</span><span class="pay-badge">Apple Pay</span></div>
  `;
}

function clearCart(){ cart=[]; updateCartBadge(); closeCart(); }

// ── PAYMENT METHOD ──
function selectPayMethod(el){
  document.querySelectorAll('.pay-method').forEach(m=>m.classList.remove('active'));
  el.classList.add('active');
}

// ── CHECKOUT ──
function openCheckout(){
  closeCart();
  const subtotal=cart.reduce((a,b)=>a+b.price*b.qty,0);
  const shipping=subtotal>=100?0:8;
  document.getElementById('checkout-summary').innerHTML=`
    <div style="display:flex;justify-content:space-between;font-size:13px;color:var(--muted);margin-bottom:5px;font-weight:300;"><span>ქვეჯამი</span><span>₾ ${subtotal}</span></div>
    <div style="display:flex;justify-content:space-between;font-size:13px;color:var(--muted);margin-bottom:12px;font-weight:300;"><span>მიტანა</span><span>${shipping===0?'უფასო':'₾ '+shipping}</span></div>
    <div style="display:flex;justify-content:space-between;font-size:15px;font-weight:500;border-top:0.5px solid var(--border);padding-top:11px;"><span>სულ</span><span>₾ ${subtotal+shipping}</span></div>
  `;
  goStep(0);
  openOverlay('checkout-overlay');
}

function goStep(i){
  document.querySelectorAll('.step-tab').forEach((t,idx)=>t.classList.toggle('active',idx===i));
  document.querySelectorAll('.checkout-section').forEach((s,idx)=>s.classList.toggle('active',idx===i));
}

// ── BOG PAYMENT SIMULATION ──
function startBOGPayment(){
  const spinner=document.getElementById('pay-spinner');
  const btnText=document.getElementById('pay-btn-text');
  spinner.style.display='block';
  btnText.textContent='BOG-თან კავშირი...';

  // Show processing overlay
  document.getElementById('processing-overlay').classList.add('show');

  // Simulate BOG redirect + callback (2.5 seconds)
  setTimeout(()=>{
    document.getElementById('processing-overlay').classList.remove('show');
    spinner.style.display='none';
    btnText.textContent='გადახდა BOG-ით →';

    // Simulate successful payment callback
    document.getElementById('order-num').textContent='LM-'+Math.floor(Math.random()*9000+1000);
    goStep(2);
    showToast('BOG გადახდა წარმატებელია! ✓');
  }, 2500);
}

// ── AUTH ──
function openAuth(type){
  const body=document.getElementById('auth-body');
  if(type==='login'){
    body.innerHTML=`
      <div class="modal-eyebrow">მოგესალმებით</div>
      <div class="modal-title">შესვლა</div>
      <div class="modal-sub">შედით LumiShop-ის ანგარიშში</div>
      <input class="modal-input" type="email" placeholder="ელ. ფოსტა">
      <input class="modal-input" type="password" placeholder="პაროლი">
      <button class="modal-btn" onclick="loginUser()"><span>შესვლა</span></button>
      <div class="modal-divider"><span>ან</span></div>
      <div class="modal-switch">არ გაქვთ ანგარიში? <a onclick="openAuth('register')">რეგისტრაცია</a></div>
    `;
  } else if(type==='register'){
    body.innerHTML=`
      <div class="modal-eyebrow">გამარჯობა!</div>
      <div class="modal-title">რეგისტრაცია</div>
      <div class="modal-sub">შექმენი LumiShop-ის ანგარიში</div>
      <input class="modal-input" type="text" placeholder="სახელი, გვარი">
      <input class="modal-input" type="email" placeholder="ელ. ფოსტა">
      <input class="modal-input" type="password" placeholder="პაროლი">
      <input class="modal-input" type="password" placeholder="პაროლის გამეორება">
      <button class="modal-btn" onclick="closeOverlay('auth-overlay');showToast('რეგისტრაცია წარმატებულია! ✓')"><span>ანგარიშის შექმნა</span></button>
      <div class="modal-switch">უკვე გაქვთ ანგარიში? <a onclick="openAuth('login')">შესვლა</a></div>
    `;
  } else if(type==='admin'){
    body.innerHTML=`
      <div class="modal-eyebrow">ადმინი</div>
      <div class="modal-title">ადმინ შესვლა</div>
      <div class="modal-sub">მხოლოდ ავტორიზებული პირებისთვის</div>
      <input class="modal-input" type="email" placeholder="admin@lumishop.ge" id="admin-email">
      <input class="modal-input" type="password" placeholder="პაროლი" id="admin-pw">
      <button class="modal-btn" onclick="tryAdminLogin()"><span>ადმინ პანელში შესვლა</span></button>
    `;
  }
  openOverlay('auth-overlay');
}

function loginUser(){ closeOverlay('auth-overlay'); showToast('წარმატებით შეხვედით! ✓'); }
function tryAdminLogin(){ closeOverlay('auth-overlay'); openAdmin(); }

// ── ADMIN ──
function openAdmin(){
  document.getElementById('admin-panel').classList.add('open');
  renderAdminProducts();
  document.getElementById('admin-prod-count').textContent=products.length;
}
function closeAdmin(){ document.getElementById('admin-panel').classList.remove('open'); }
function adminNav(el,section){
  document.querySelectorAll('.admin-nav-item').forEach(i=>i.classList.remove('active'));
  el.classList.add('active');
  document.querySelectorAll('.admin-section').forEach(s=>s.classList.remove('active'));
  document.getElementById('admin-'+section).classList.add('active');
}

function renderAdminProducts(){
  document.getElementById('admin-prod-tbody').innerHTML=products.map(p=>`
    <tr>
      <td><div class="td-img" style="background:${p.col};border-radius:50%;"></div></td>
      <td>${p.name}</td>
      <td class="td-cat">${p.cat}</td>
      <td class="td-price">₾ ${p.price}</td>
      <td><div class="admin-actions">
        <button class="btn-edit" onclick="editProduct(${p.id})">რედაქტირება</button>
        <button class="btn-delete" onclick="deleteProduct(${p.id})">წაშლა</button>
      </div></td>
    </tr>
  `).join('');
}

function deleteProduct(id){
  products=products.filter(p=>p.id!==id);
  renderAdminProducts(); renderGrid('home-grid','all'); renderGrid('prod-grid','all');
  document.getElementById('admin-prod-count').textContent=products.length;
  showToast('პროდუქტი წაიშალა');
}

function editProduct(id){
  const p=products.find(x=>x.id===id); if(!p) return;
  adminNav(document.querySelectorAll('.admin-nav-item')[2],'add');
  document.getElementById('new-name').value=p.name;
  document.getElementById('new-price').value=p.price;
  document.getElementById('new-cat').value=p.cat;
  document.getElementById('new-desc').value=p.desc;
  document.getElementById('new-color').value=p.col;
  document.getElementById('new-bg').value=p.bg;
  document.getElementById('new-badge').value=p.badge||'';
  showToast('"'+p.name+'" — ახლა შეასწორეთ და შეინახეთ');
}

function addProduct(){
  const name=document.getElementById('new-name').value.trim();
  const price=parseInt(document.getElementById('new-price').value);
  const cat=document.getElementById('new-cat').value;
  const desc=document.getElementById('new-desc').value.trim();
  const col=document.getElementById('new-color').value;
  const bg=document.getElementById('new-bg').value;
  const badge=document.getElementById('new-badge').value;
  if(!name||!price){ showToast('შეავსეთ სავალდებულო ველები'); return; }
  const existing=products.find(p=>p.name===name);
  if(existing){
    Object.assign(existing,{price,cat,desc,col,bg,badge});
    showToast('"'+name+'" განახლდა! ✓');
  } else {
    products.push({id:nextId++,name,cat,price,bg,col,desc,badge});
    showToast('"'+name+'" დაემატა! ✓');
  }
  renderAdminProducts(); renderGrid('home-grid','all'); renderGrid('prod-grid','all');
  document.getElementById('admin-prod-count').textContent=products.length;
  ['new-name','new-price','new-desc'].forEach(id=>document.getElementById(id).value='');
}

function saveBOGConfig(){
  const id=document.getElementById('bog-client-id').value;
  const sec=document.getElementById('bog-secret').value;
  if(!id||!sec){ showToast('Client ID და Secret ID-ი შეიყვანეთ'); return; }
  showToast('BOG კონფიგურაცია შენახულია ✓');
}

// ── HELPERS ──
function openOverlay(id){ document.getElementById(id).classList.add('open'); }
function closeOverlay(id){ document.getElementById(id).classList.remove('open'); }
function closeOverlayClick(e,id){ if(e.target.id===id) closeOverlay(id); }

let toastTimer;
function showToast(msg){
  clearTimeout(toastTimer);
  document.getElementById('toast-msg').textContent=msg;
  document.getElementById('toast').classList.add('show');
  toastTimer=setTimeout(()=>document.getElementById('toast').classList.remove('show'),2800);
}

// ── INIT ──
navigateTo('home');
</script>
</body>
</html>
