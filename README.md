# OSACA-V
Registro sesiones de asesoría 
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sesiones de seguimiento — OSACA V</title>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@latest/tabler-icons.min.css">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --bg: #ffffff; --bg2: #f5f5f3; --bg3: #efefec;
    --text: #1a1a18; --text2: #5f5e5a; --text3: #888780;
    --border: rgba(0,0,0,0.12); --border2: rgba(0,0,0,0.22);
    --blue: #185FA5; --blue-bg: #E6F1FB; --blue-text: #0C447C;
    --green-bg: #EAF3DE; --green-border: #97C459; --green-text: #3B6D11;
    --red-bg: #FCEBEB; --red-border: #F09595; --red-text: #A32D2D;
    --amber-bg: #FAEEDA; --amber-border: #EF9F27; --amber-text: #633806;
    --radius: 8px; --radius-lg: 12px;
    --font: system-ui, -apple-system, sans-serif;
  }
  @media (prefers-color-scheme: dark) {
    :root {
      --bg: #1e1e1c; --bg2: #2a2a27; --bg3: #333330;
      --text: #e8e6df; --text2: #a0a09a; --text3: #6a6a65;
      --border: rgba(255,255,255,0.1); --border2: rgba(255,255,255,0.2);
      --blue: #4A9BE8; --blue-bg: #0d2d4a; --blue-text: #85b7eb;
      --green-bg: #1a2e0f; --green-border: #3B6D11; --green-text: #97C459;
      --red-bg: #2e0f0f; --red-border: #A32D2D; --red-text: #F09595;
      --amber-bg: #2e1f05; --amber-border: #854F0B; --amber-text: #FAC775;
    }
  }
  body { font-family: var(--font); background: var(--bg3); color: var(--text); min-height: 100vh; padding: 2rem 1rem; }
  .container { max-width: 660px; margin: 0 auto; }
  .header { margin-bottom: 1.5rem; }
  .header h1 { font-size: 20px; font-weight: 500; color: var(--text); display: flex; align-items: center; gap: 8px; }
  .header p { font-size: 13px; color: var(--text2); margin-top: 5px; }
  .card { background: var(--bg); border: 0.5px solid var(--border); border-radius: var(--radius-lg); padding: 1.25rem; margin-bottom: 1rem; }
  .section-title { font-size: 12px; font-weight: 500; color: var(--text3); text-transform: uppercase; letter-spacing: 0.06em; margin-bottom: 0.75rem; }
  .field { margin-bottom: 0.9rem; }
  .field:last-child { margin-bottom: 0; }
  .field label { display: block; font-size: 13px; color: var(--text2); margin-bottom: 5px; }
  .field select, .field input { width: 100%; padding: 8px 10px; font-size: 14px; font-family: var(--font); background: var(--bg); color: var(--text); border: 0.5px solid var(--border2); border-radius: var(--radius); outline: none; transition: border-color 0.15s; }
  .field select:focus, .field input:focus { border-color: var(--blue); box-shadow: 0 0 0 3px rgba(24,95,165,0.12); }
  .field input[readonly] { background: var(--bg2); cursor: default; color: var(--text2); }
  .grid2 { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
  @media (max-width: 500px) { .grid2 { grid-template-columns: 1fr; } }
  .notice { background: var(--amber-bg); border: 0.5px solid var(--amber-border); border-radius: var(--radius); padding: 10px 14px; font-size: 13px; color: var(--amber-text); margin-bottom: 0.9rem; display: flex; gap: 8px; align-items: flex-start; line-height: 1.5; }
  .notice i { flex-shrink: 0; margin-top: 1px; }
  .hint { font-size: 12px; color: var(--text3); margin-top: 5px; line-height: 1.5; }
  .slot-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(110px, 1fr)); gap: 8px; }
  .slot-btn { padding: 10px 8px; border: 0.5px solid var(--border); border-radius: var(--radius); background: var(--bg); cursor: pointer; text-align: center; font-size: 13px; font-weight: 500; color: var(--text); transition: all 0.15s; user-select: none; }
  .slot-btn:hover:not(.taken):not(.selected) { border-color: var(--border2); background: var(--bg2); }
  .slot-btn.selected { border-color: var(--blue); background: var(--blue-bg); color: var(--blue-text); }
  .slot-btn.taken { background: var(--bg2); color: var(--text3); cursor: not-allowed; }
  .slot-names { font-size: 10px; font-weight: 400; color: var(--text3); margin-top: 3px; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
  .badge-taken { display: inline-block; font-size: 10px; background: var(--bg3); color: var(--text3); padding: 1px 7px; border-radius: 20px; margin-top: 3px; }
  .submit-btn { width: 100%; padding: 13px; background: var(--blue); color: #fff; border: none; border-radius: var(--radius); font-size: 14px; font-weight: 500; cursor: pointer; font-family: var(--font); transition: opacity 0.15s; margin-top: 0.25rem; }
  .submit-btn:hover { opacity: 0.88; }
  .msg { padding: 11px 14px; border-radius: var(--radius); font-size: 13px; margin-bottom: 1rem; display: none; line-height: 1.5; }
  .msg.success { background: var(--green-bg); color: var(--green-text); border: 0.5px solid var(--green-border); display: block; }
  .msg.error { background: var(--red-bg); color: var(--red-text); border: 0.5px solid var(--red-border); display: block; }
  .admin-section { margin-top: 2rem; padding-top: 1.5rem; border-top: 0.5px solid var(--border); }
  .admin-toggle { font-size: 13px; color: var(--text2); cursor: pointer; background: none; border: none; font-family: var(--font); padding: 0; text-decoration: underline; }
  .stat-row { display: flex; gap: 10px; margin-bottom: 1rem; }
  .stat-box { flex: 1; background: var(--bg2); border-radius: var(--radius); padding: 0.75rem 1rem; }
  .stat-box .n { font-size: 22px; font-weight: 500; }
  .stat-box .l { font-size: 12px; color: var(--text2); margin-top: 2px; }
  .reg-table { width: 100%; border-collapse: collapse; font-size: 12px; table-layout: fixed; }
  .reg-table th { text-align: left; padding: 6px 8px; border-bottom: 0.5px solid var(--border); color: var(--text2); font-weight: 500; }
  .reg-table td { padding: 7px 8px; border-bottom: 0.5px solid var(--border); vertical-align: top; word-break: break-word; }
  .reg-table tr:last-child td { border-bottom: none; }
  .refresh-btn, .copy-btn { font-size: 12px; color: var(--text2); background: none; border: 0.5px solid var(--border2); border-radius: var(--radius); padding: 4px 10px; cursor: pointer; font-family: var(--font); }
  .drive-link { color: var(--blue); text-decoration: none; font-size: 12px; }
  .drive-link:hover { text-decoration: underline; }
  .top-bar { display: flex; align-items: center; justify-content: space-between; margin-bottom: 0.75rem; }
</style>
</head>
<body>
<div class="container">
  <div class="header">
    <h1><i class="ti ti-calendar-event" style="font-size:20px;color:#185FA5" aria-hidden="true"></i> Sesiones de seguimiento — OSACA V</h1>
    <p>Programa de Derecho · Universidad Central · Reserva tu horario para la sesión vía Google Meet</p>
  </div>

  <div id="msg" class="msg"></div>

  <div class="card">
    <div class="section-title">Integrante 1</div>
    <div class="grid2">
      <div class="field"><label>Nombre completo</label><select id="s1"><option value="">— Seleccionar —</option></select></div>
      <div class="field"><label>Correo institucional</label><input type="email" id="e1" readonly placeholder="—"></div>
    </div>
  </div>

  <div class="card">
    <div class="section-title">Integrante 2 (si aplica)</div>
    <div class="grid2">
      <div class="field"><label>Nombre completo</label><select id="s2"><option value="">— Solo (no aplica) —</option></select></div>
      <div class="field"><label>Correo institucional</label><input type="email" id="e2" readonly placeholder="—"></div>
    </div>
  </div>

  <div class="card">
    <div class="section-title">Tema de investigación</div>
    <div class="field"><select id="tema"><option value="">— Seleccionar tema —</option></select></div>
  </div>

  <div class="card">
    <div class="section-title"><i class="ti ti-brand-google-drive" style="font-size:14px;vertical-align:-2px;margin-right:4px;color:#185FA5" aria-hidden="true"></i> Documento en Google Drive</div>
    <div class="notice">
      <i class="ti ti-alert-triangle" style="font-size:16px"></i>
      <span>Antes de pegar el enlace, configura el documento como <strong>«Cualquier persona con el enlace puede ver»</strong>. Sin este permiso el docente no podrá revisarlo.<br><br>
      Cómo hacerlo: <em>Archivo → Compartir → Cambiar a cualquier persona con el enlace → Copiar enlace.</em></span>
    </div>
    <div class="field">
      <label>Enlace de Google Drive</label>
      <input type="url" id="driveUrl" placeholder="https://docs.google.com/document/d/...">
    </div>
  </div>

  <div class="card">
    <div class="section-title">Horario disponible <span style="font-weight:400;font-size:11px;color:var(--text3)">&nbsp;·&nbsp;sesiones de 20 min</span></div>
    <div class="slot-grid" id="slots"></div>
  </div>

  <button class="submit-btn" onclick="submitForm()">Confirmar inscripción</button>

  <div class="admin-section">
    <button class="admin-toggle" onclick="toggleAdmin()">Ver inscripciones registradas ▾</button>
    <div id="adminPanel" style="display:none;margin-top:1rem;">
      <div class="top-bar">
        <span style="font-size:13px;font-weight:500">Panel del docente</span>
        <button class="refresh-btn" onclick="loadAdmin()"><i class="ti ti-refresh" style="font-size:13px;vertical-align:-1px"></i> Actualizar</button>
      </div>
      <div class="stat-row" id="stats"></div>
      <div class="card" style="overflow-x:auto;padding:0.75rem;">
        <table class="reg-table">
          <thead><tr><th style="width:52px">Hora</th><th style="width:23%">Integrante 1</th><th style="width:23%">Integrante 2</th><th>Tema</th><th style="width:56px">Doc.</th></tr></thead>
          <tbody id="regBody"></tbody>
        </table>
      </div>
      <button class="copy-btn" style="margin-top:8px" onclick="copyCSV()"><i class="ti ti-copy" style="font-size:12px;vertical-align:-1px"></i> Copiar CSV</button>
    </div>
  </div>
</div>

<script>
const STUDENTS=[{n:"Balaguera Argumedo, Mateo",e:"mbalagueraa2@ucentral.edu.co"},{n:"Castro Zapata, Maria Jose",e:"mcastroz2@ucentral.edu.co"},{n:"Florez Betancourt, Nicolas Samuel",e:"nflorezb@ucentral.edu.co"},{n:"Fonseca Chivata, Tomas Santiago",e:"tfonsecac@ucentral.edu.co"},{n:"Garzon Reina, Sara Daniela",e:"sgarzonr3@ucentral.edu.co"},{n:"Gualdron Tunjano, Valeria",e:"vguadront@ucentral.edu.co"},{n:"Hernández Rincón, Katherine Dayane",e:"khernandezr1@ucentral.edu.co"},{n:"Jiménez Ordoñez, Lucas Mateus",e:"ljimenezo1@ucentral.edu.co"},{n:"Mancipe Granada, Samuel Santiago",e:"smancipeg@ucentral.edu.co"},{n:"Martinez Berrio, Camilo Andres",e:"cmartinezb5@ucentral.edu.co"},{n:"Martinez Rojas, Fabian Lizandro",e:"fmartinezr@ucentral.edu.co"},{n:"Mesa Bautista, Juan David",e:"jmesab3@ucentral.edu.co"},{n:"Ortega Marin, Andres Felipe",e:"aortegam1@ucentral.edu.co"},{n:"Otalora Garzón, Stefanía",e:"sotalorag@ucentral.edu.co"},{n:"Pamplona Riveros, Laura Sofia",e:"lpamplonar@ucentral.edu.co"},{n:"Puentes Romero, Laura Daniela",e:"lpuentesr1@ucentral.edu.co"},{n:"Saenz Castiblanco, Sergio Alejandro",e:"ssaenzc1@ucentral.edu.co"},{n:"Sánchez Hernández, Eliana Haydee",e:"esanchezh@ucentral.edu.co"},{n:"Segura Alonso, Luisa Gabriela",e:"lseguraa1@ucentral.edu.co"},{n:"Sierra Charry, Brenda Katterine",e:"bsierrac@ucentral.edu.co"},{n:"Umaña Garcia, Duver Esteben",e:"dumanag@ucentral.edu.co"}];
const TEMAS=["Protección de la seguridad en plataformas digitales de transporte en Colombia","¿Se vende el futbolista o sus derechos deportivos?","Acciones afirmativas vs. discriminación positiva en Colombia: alcance y límites constitucionales","Entre la realidad y la ficción: regular imágenes creadas por IA para proteger la identidad personal","Prácticas abusivas en plataformas digitales de préstamos y vulneración de derechos del consumidor","Maternidad subrogada","Reasignación de sexo y problemas de acceso al sistema de salud","Transferencia mitocondrial en Colombia","Uso de animales en la fuerza pública y compatibilidad con el reconocimiento jurídico como seres sintientes","Vacíos en la protección laboral de las monjas en Colombia","Vacíos normativos frente al seguro de carga superior a 5 toneladas en plataformas digitales de transporte"];
const SLOTS=["20:00","20:20","20:40","21:00","21:20"];
const KEY="osaca_v_inscripciones_v2";
let sel=null,regs={};

function addMin(t,m){const[h,min]=t.split(':').map(Number);const tot=h*60+min+m;return String(Math.floor(tot/60)).padStart(2,'0')+':'+String(tot%60).padStart(2,'0');}

async function load(){try{const r=await window.storage.get(KEY,true);regs=r?JSON.parse(r.value):{};}catch(e){regs={};}}
async function save(){await window.storage.set(KEY,JSON.stringify(regs),true);}

function initSelects(){
  const s1=document.getElementById('s1'),s2=document.getElementById('s2'),tm=document.getElementById('tema');
  STUDENTS.forEach(s=>{s1.innerHTML+=`<option value="${s.n}">${s.n}</option>`;s2.innerHTML+=`<option value="${s.n}">${s.n}</option>`;});
  TEMAS.forEach(t=>{tm.innerHTML+=`<option value="${t}">${t}</option>`;});
  s1.addEventListener('change',()=>{const st=STUDENTS.find(x=>x.n===s1.value);document.getElementById('e1').value=st?st.e:'';});
  s2.addEventListener('change',()=>{const st=STUDENTS.find(x=>x.n===s2.value);document.getElementById('e2').value=st?st.e:'';});
}

function renderSlots(){
  const g=document.getElementById('slots');g.innerHTML='';
  SLOTS.forEach(sl=>{
    const r=regs[sl],taken=!!r,div=document.createElement('div');
    div.className='slot-btn'+(taken?' taken':'')+(sel===sl?' selected':'');
    let h=`<div>${sl} – ${addMin(sl,20)}</div>`;
    if(taken){h+=`<div class="slot-names">${r.s1.split(',')[0]}${r.s2&&r.s2!=='—'?' + '+r.s2.split(',')[0]:''}</div><div><span class="badge-taken">Reservado</span></div>`;}
    div.innerHTML=h;
    if(!taken)div.onclick=()=>{sel=sl;renderSlots();};
    g.appendChild(div);
  });
}

function showMsg(txt,type){const el=document.getElementById('msg');el.textContent=txt;el.className='msg '+type;setTimeout(()=>{el.className='msg';},6000);}

async function submitForm(){
  const s1=document.getElementById('s1').value.trim();
  const s2=document.getElementById('s2').value.trim();
  const tema=document.getElementById('tema').value.trim();
  const url=document.getElementById('driveUrl').value.trim();
  if(!s1){showMsg('Selecciona el nombre del integrante 1.','error');return;}
  if(!tema){showMsg('Selecciona el tema de investigación.','error');return;}
  if(!url){showMsg('Ingresa el enlace de Google Drive.','error');return;}
  if(!url.startsWith('https://')){showMsg('El enlace no es válido. Debe comenzar con https://','error');return;}
  if(!sel){showMsg('Selecciona un horario disponible.','error');return;}
  if(s1&&s2&&s1===s2){showMsg('Los dos integrantes no pueden ser la misma persona.','error');return;}
  await load();
  if(regs[sel]){showMsg('Ese horario ya fue tomado. Elige otro.','error');renderSlots();return;}
  regs[sel]={s1,s2:s2||'—',tema,driveUrl:url,ts:new Date().toLocaleString('es-CO',{timeZone:'America/Bogota'})};
  await save();
  showMsg('✓ Inscripción confirmada — '+sel+' · '+s1,'success');
  sel=null;document.getElementById('driveUrl').value='';
  renderSlots();
  if(document.getElementById('adminPanel').style.display!=='none')loadAdmin();
}

function toggleAdmin(){const p=document.getElementById('adminPanel');p.style.display=p.style.display==='none'?'block':'none';if(p.style.display==='block')loadAdmin();}

async function loadAdmin(){
  await load();
  const taken=Object.keys(regs).length;
  document.getElementById('stats').innerHTML=`<div class="stat-box"><div class="n">${taken}</div><div class="l">Inscripciones</div></div><div class="stat-box"><div class="n">${SLOTS.length-taken}</div><div class="l">Horarios libres</div></div><div class="stat-box"><div class="n">${SLOTS.length}</div><div class="l">Total horarios</div></div>`;
  const tb=document.getElementById('regBody');
  if(!taken){tb.innerHTML='<tr><td colspan="5" style="text-align:center;padding:1rem;color:var(--text2)">Sin inscripciones aún</td></tr>';return;}
  tb.innerHTML=SLOTS.map(sl=>{
    const r=regs[sl];
    if(!r)return`<tr><td style="color:var(--text3)">${sl}</td><td colspan="4" style="color:var(--text3)">Disponible</td></tr>`;
    const doc=r.driveUrl?`<a class="drive-link" href="${r.driveUrl}" target="_blank"><i class="ti ti-brand-google-drive" style="font-size:13px;vertical-align:-2px"></i> Abrir</a>`:'—';
    return`<tr><td style="font-weight:500">${sl}</td><td>${r.s1}</td><td>${r.s2}</td><td style="font-size:11px;color:var(--text2)">${r.tema}</td><td>${doc}</td></tr>`;
  }).join('');
}

function copyCSV(){
  const rows=[['Hora','Integrante 1','Integrante 2','Tema','Documento Drive','Registrado']];
  SLOTS.forEach(sl=>{const r=regs[sl];if(r)rows.push([sl,r.s1,r.s2,r.tema,r.driveUrl||'',r.ts]);});
  navigator.clipboard.writeText(rows.map(r=>r.map(c=>`"${c}"`).join(',')).join('\n')).then(()=>alert('CSV copiado al portapapeles'));
}

async function init(){await load();initSelects();renderSlots();setInterval(async()=>{await load();renderSlots();},15000);}
init();
</script>
</body>
</html>
