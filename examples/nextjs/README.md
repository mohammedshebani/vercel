<!doctype html>
<html lang="ar">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>بطاقة رقمية — NFC Form</title>
<style>
  :root{--bg:#0b0b0c;--gold:#c79b2d;--muted:#bfbfbf}
  body{margin:0;font-family:system-ui,Segoe UI,Roboto,"Helvetica Neue",Arial;background:var(--bg);color:#eee;display:flex;min-height:100vh;align-items:center;justify-content:center;padding:20px}
  .card{width:100%;max-width:760px;background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent);border-radius:12px;box-shadow:0 8px 30px rgba(0,0,0,0.6);overflow:hidden;border:1px solid rgba(255,255,255,0.03)}
  header{padding:20px 24px;background:rgba(0,0,0,0.2);display:flex;align-items:center;gap:16px}
  .logo{width:56px;height:56px;border-radius:10px;background:linear-gradient(135deg,var(--gold),#f0d67a);display:flex;align-items:center;justify-content:center;color:#111;font-weight:700}
  h1{margin:0;font-size:18px}
  .sub{color:var(--muted);font-size:13px}
  main{padding:18px 24px;display:grid;grid-template-columns:1fr 1fr;gap:12px}
  label{display:block;font-size:13px;color:var(--muted);margin-bottom:6px}
  input,textarea,select{width:100%;padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.06);background:transparent;color:#fff;box-sizing:border-box}
  textarea{min-height:90px;resize:vertical}
  .full{grid-column:1/-1}
  .actions{padding:14px 24px;background:rgba(0,0,0,0.15);display:flex;gap:10px;align-items:center;justify-content:space-between}
  button{background:var(--gold);border:none;color:#111;padding:10px 14px;border-radius:8px;font-weight:700;cursor:pointer}
  .outline{background:transparent;border:1px solid rgba(255,255,255,0.06);color:var(--muted)}
  .note{font-size:13px;color:var(--muted)}
  .profileView{padding:18px 24px;border-top:1px dashed rgba(255,255,255,0.03)}
  .pv-row{display:flex;gap:12px;align-items:center;margin-bottom:10px}
  .pv-label{min-width:120px;color:var(--muted)}
  .pv-value{flex:1}
  .small{font-size:12px;color:var(--muted)}
  @media(max-width:720px){main{grid-template-columns:1fr} .logo{width:48px;height:48px}}
</style>
</head>
<body>
  <div class="card" role="main">
    <header>
      <div class="logo">BC</div>
      <div>
        <h1>بطاقة رقمية / Digital Card</h1>
        <div class="sub">املأ بياناتك — Fill your info</div>
      </div>
    </header>

    <main>
      <div class="full">
        <label>تعليمات • Instructions</label>
        <div class="note">املأ الحقول أو اترك الاختيارات الفارغة. بعد الحفظ يمكنك تنزيل vCard أو نسخ رابط صفحتك لحفظه أو مشاركته.</div>
      </div>

      <div>
        <label>الاسم • Name (مطلوب)</label>
        <input id="name" placeholder="مثال: محمد علي / Mohammed Ali" required>
      </div>

      <div>
        <label>المسمى الوظيفي • Title / Company</label>
        <input id="title" placeholder="مثال: مصمم جرافيك / Graphic Designer">
      </div>

      <div>
        <label>رقم الجوال • Phone (مطلوب)</label>
        <input id="phone" placeholder="مثال: 00966580016689" required>
      </div>

      <div>
        <label>واتساب • WhatsApp</label>
        <input id="whatsapp" placeholder="رابط wa.me أو رقم">
      </div>

      <div class="full">
        <label>البريد الإلكتروني • Email</label>
        <input id="email" placeholder="example@mail.com">
      </div>

      <div class="full">
        <label>الموقع الإلكتروني • Website</label>
        <input id="website" placeholder="https://your-site.com">
      </div>

      <div class="full">
        <label>لوكيشن • Location (Google Maps link)</label>
        <input id="location" placeholder="https://maps.app.goo.gl/....">
      </div>

      <div>
        <label>لينك بروفايل • Profile Link</label>
        <input id="profile" placeholder="رابط البروفايل أو صفحة عرض">
      </div>

      <div>
        <label>سناب • Snapchat</label>
        <input id="snap" placeholder="username">
      </div>

      <div>
        <label>انستغرام • Instagram</label>
        <input id="insta" placeholder="username">
      </div>

      <div>
        <label>فيسبوك • Facebook</label>
        <input id="fb" placeholder="profile/page link">
      </div>

      <div class="full">
        <label>ملاحظات • Notes / Short bio</label>
        <textarea id="notes" placeholder="نبذة قصيرة..."></textarea>
      </div>

      <div class="full">
        <label>رفع صورة شخصية / شعار • Upload image (اختياري)</label>
        <input id="imgfile" type="file" accept="image/*">
      </div>
    </main>

    <div class="actions">
      <div>
        <button id="saveBtn">حفظ • Save</button>
        <button id="downloadVcard" class="outline">تحميل vCard</button>
        <button id="copyLink" class="outline">نسخ رابط الملف • Copy Profile Link</button>
      </div>
      <div class="small">التصميم: أسود × ذهبي — Arabic / English</div>
    </div>

    <div id="profileView" class="profileView" style="display:none">
      <div class="pv-row"><div class="pv-label">الاسم • Name</div><div id="pv-name" class="pv-value"></div></div>
      <div class="pv-row"><div class="pv-label">الهاتف • Phone</div><div id="pv-phone" class="pv-value"></div></div>
      <div class="pv-row"><div class="pv-label">واتساب • WhatsApp</div><div id="pv-whatsapp" class="pv-value"></div></div>
      <div class="pv-row"><div class="pv-label">البريد • Email</div><div id="pv-email" class="pv-value"></div></div>
      <div class="pv-row"><div class="pv-label">الموقع • Website</div><div id="pv-website" class="pv-value"></div></div>
      <div class="pv-row"><div class="pv-label">اللوكيشن • Location</div><div id="pv-location" class="pv-value"></div></div>
      <div class="pv-row"><div class="pv-label">بروفايل • Profile</div><div id="pv-profile" class="pv-value"></div></div>
      <div class="pv-row"><div class="pv-label">سوشالز • Socials</div><div id="pv-socials" class="pv-value"></div></div>
      <div style="margin-top:8px" class="small">يمكنك نسخ الرابط أو تحميل vCard أو طباعتها.</div>
    </div>
  </div>

<script>
/* Helper: read/write base64 JSON in url hash for shareable profile */
function encodeData(obj){
  try{ return btoa(encodeURIComponent(JSON.stringify(obj))); }catch(e){ return ''; }
}
function decodeData(s){
  try{ return JSON.parse(decodeURIComponent(atob(s))); }catch(e){ return null; }
}

function getFormData(){
  return {
    name: document.getElementById('name').value.trim(),
    title: document.getElementById('title').value.trim(),
    phone: document.getElementById('phone').value.trim(),
    whatsapp: document.getElementById('whatsapp').value.trim(),
    email: document.getElementById('email').value.trim(),
    website: document.getElementById('website').value.trim(),
    location: document.getElementById('location').value.trim(),
    profile: document.getElementById('profile').value.trim(),
    snap: document.getElementById('snap').value.trim(),
    insta: document.getElementById('insta').value.trim(),
    fb: document.getElementById('fb').value.trim(),
    notes: document.getElementById('notes').value.trim(),
    img: window._uploadedImg || ''
  };
}

function showProfile(obj){
  if(!obj) return;
  document.getElementById('pv-name').textContent = obj.name || '-';
  document.getElementById('pv-phone').textContent = obj.phone || '-';
  document.getElementById('pv-whatsapp').innerHTML = obj.whatsapp ? `<a href="${obj.whatsapp}" target="_blank">${obj.whatsapp}</a>` : '-';
  document.getElementById('pv-email').textContent = obj.email || '-';
  document.getElementById('pv-website').innerHTML = obj.website ? `<a href="${obj.website}" target="_blank">${obj.website}</a>` : '-';
  document.getElementById('pv-location').innerHTML = obj.location ? `<a href="${obj.location}" target="_blank">View Map</a>` : '-';
  document.getElementById('pv-profile').innerHTML = obj.profile ? `<a href="${obj.profile}" target="_blank">Profile</a>` : '-';
  let socials = [];
  if(obj.snap) socials.push('Snap: '+obj.snap);
  if(obj.insta) socials.push('IG: '+obj.insta);
  if(obj.fb) socials.push('FB: '+obj.fb);
  document.getElementById('pv-socials').textContent = socials.length? socials.join(' • ') : '-';
  document.getElementById('profileView').style.display = 'block';
}

/* image upload as data URL */
document.getElementById('imgfile').addEventListener('change', function(e){
  const f = e.target.files[0];
  if(!f) return;
  const r = new FileReader();
  r.onload = function(){ window._uploadedImg = r.result; };
  r.readAsDataURL(f);
});

/* on page load - if URL hash contains data, show it */
window.addEventListener('load', function(){
  if(location.hash && location.hash.startsWith('#data=')){
    const s = location.hash.slice(6);
    const obj = decodeData(s);
    if(obj){
      // prefill fields (readonly view)
      Object.keys(obj).forEach(k=>{
        const el = document.getElementById(k);
        if(el) el.value = obj[k];
      });
      showProfile(obj);
      // hide form to avoid accidental edits when opening profile
      // you can still edit and save again
    }
  }
});

/* Save: generate link & show profile */
document.getElementById('saveBtn').addEventListener('click', function(){
  const data = getFormData();
  if(!data.name || !data.phone){ alert('الاسم ورقم الجوال مطلوبان • Name & Phone are required'); return; }
  const code = encodeData(data);
  const shareUrl = location.origin + location.pathname + '#data=' + code;
  // update location hash so page shows the profile
  location.hash = 'data=' + code;
  showProfile(data);
  alert('تم الحفظ مؤقتاً في الرابط — انسخ الرابط أو حمّل vCard.');
});

/* copy link */
document.getElementById('copyLink').addEventListener('click', function(){
  const h = location.hash || '';
  if(!h.startsWith('#data=')){ alert('اضغط حفظ أولاً ثم انسخ الرابط'); return; }
  const full = location.origin + location.pathname + h;
  navigator.clipboard.writeText(full).then(()=> alert('تم نسخ الرابط!'), ()=> alert('نسخ فشل — انسخ يدوياً: ' + full));
});

/* download vCard */
function makeVCard(obj){
  const lines = [];
  lines.push('BEGIN:VCARD');
  lines.push('VERSION:3.0');
  if(obj.name) lines.push('FN:'+obj.name);
  if(obj.title) lines.push('TITLE:'+obj.title);
  if(obj.phone) lines.push('TEL;TYPE=CELL:'+obj.phone);
  if(obj.email) lines.push('EMAIL;TYPE=INTERNET:'+obj.email);
  if(obj.website) lines.push('URL:'+obj.website);
  if(obj.notes) lines.push('NOTE:'+obj.notes.replace(/\n/g,' '));
  lines.push('END:VCARD');
  return lines.join('\r\n');
}

document.getElementById('downloadVcard').addEventListener('click', function(){
  const data = getFormData();
  if(!data.name || !data.phone){ alert('الاسم ورقم الجوال مطلوبان • Name & Phone are required'); return; }
  const v = makeVCard(data);
  const blob = new Blob([v], {type:'text/vcard'});
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url; a.download = (data.name.replace(/\s+/g,'_')||'contact') + '.vcf';
  document.body.appendChild(a); a.click(); a.remove(); URL.revokeObjectURL(url);
});

/* allow printing / save as PDF via browser print */
</script>
</body>
</html>
