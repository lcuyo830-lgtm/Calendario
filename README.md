

Progressup · HTML
<!DOCTYPE html>
<html lang="es"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>ProgressUp</title>
<link rel="preconnect" href="https://fonts.googleapis.com"><link href="https://fonts.googleapis.com/css2?family=Sora:wght@400;600;700&display=swap" rel="stylesheet">
<style>
:root{--bg:#0c0e1b;--s1:#151933;--s2:#1f2447;--tx:#f4f5ff;--mu:#9aa0c8;--b:#4f8cff;--p:#9b6bff;--ok:#34d399;--bad:#fb7185;--g:linear-gradient(135deg,var(--b),var(--p));box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px);color-scheme:dark}
:root[data-t=light]{--bg:#f3f4fb;--s1:#fff;--s2:#e8eafa;--tx:#171a33;--mu:#5b618c;color-scheme:light}
html{height:100%;scroll-padding-top:env(safe-area-inset-top,0px)}*{box-sizing:border-box}
body{margin:0;min-height:100%;background:var(--bg);color:var(--tx);font:15px/1.45 Sora,system-ui,sans-serif}
button,input,select,textarea{font:inherit;color:inherit}button{cursor:pointer;border:0;background:none}
.app{display:grid;grid-template-columns:200px 1fr;min-height:100vh}
nav{position:sticky;top:0;height:100vh;padding:20px 12px;background:var(--s1);display:flex;flex-direction:column;gap:4px}
.logo{font-weight:700;font-size:20px;padding:4px 12px 16px;background:var(--g);-webkit-background-clip:text;background-clip:text;color:transparent}
nav button{display:flex;gap:10px;align-items:center;padding:10px 12px;border-radius:12px;color:var(--mu);text-align:left;transition:.2s}
nav button.on{background:var(--s2);color:var(--tx)}nav button:focus-visible,.btn:focus-visible,.ck:focus-visible{outline:2px solid var(--b);outline-offset:2px}
main{padding:24px;max-width:980px;width:100%;margin:0 auto}
h1{font-size:26px;margin:0 0 4px}h2{font-size:17px;margin:0 0 12px}h3{margin:0 0 12px}
.mu{color:var(--mu)}small{color:var(--mu);font-size:12px}
.card{background:var(--s1);border-radius:18px;padding:18px;margin-bottom:14px}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:12px;margin-bottom:14px}
.kpi{background:var(--s1);border-radius:16px;padding:14px}.kpi b{display:block;font-size:24px}
.btn{padding:10px 16px;border-radius:12px;background:var(--s2);font-weight:600;transition:.2s}.btn:hover{filter:brightness(1.15)}
.pri{background:var(--g);color:#fff}.dg{color:var(--bad)}
.top{display:flex;justify-content:space-between;align-items:center;gap:10px;flex-wrap:wrap;margin-bottom:16px}
.bar{height:10px;border-radius:9px;background:var(--s2);overflow:hidden}.bar i{display:block;height:100%;background:var(--g);transition:width .6s}
.row{display:flex;align-items:center;gap:12px;padding:10px 4px;border-bottom:1px solid var(--s2)}.row:last-child{border:0}
.rb{flex:1;cursor:pointer;min-width:0}.rb b{display:block;font-weight:600}
.row.done .rb b{text-decoration:line-through;color:var(--mu)}.row.canc{opacity:.5}
.ck{width:28px;height:28px;border-radius:9px;border:2px solid var(--c,var(--b));color:#fff;font-weight:700;flex:none;transition:.2s}
.row.done .ck{background:var(--c)}.pop .ck{animation:pop .45s}
@keyframes pop{40%{transform:scale(1.35) rotate(-8deg);box-shadow:0 0 0 8px #9b6bff44}}
.tag{font-size:11px;padding:3px 9px;border-radius:99px;background:var(--s2)}.tag.done{color:var(--ok)}.tag.over{color:var(--bad)}.tag.pend{color:var(--b)}
.cal{display:grid;grid-template-columns:repeat(7,1fr);gap:6px}.cal .h{text-align:center;font-size:12px;color:var(--mu)}
.day{aspect-ratio:1;border-radius:12px;background:var(--s2);padding:6px;display:flex;flex-direction:column;justify-content:space-between;text-align:left;font-size:13px;min-height:44px}
.day.sel{outline:2px solid var(--p)}.day.today{background:var(--g);color:#fff}.day.x{background:none}
.dots{display:flex;gap:3px;flex-wrap:wrap}.dots i{width:7px;height:7px;border-radius:50%}
.g2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
label{display:block;font-size:12px;color:var(--mu);margin-bottom:10px}
input,select,textarea{width:100%;margin-top:4px;padding:10px;border-radius:10px;border:1px solid var(--s2);background:var(--bg)}
.wk{display:flex;gap:6px;margin-bottom:10px}.wk label{margin:0;flex:1}.wk input{width:auto;margin:0 4px 0 0}
dialog{border:0;border-radius:20px;background:var(--s1);color:var(--tx);width:min(460px,94vw);padding:20px;max-height:90vh;overflow:auto}
dialog::backdrop{background:#000a}.acts{display:flex;gap:8px;flex-wrap:wrap;margin-top:6px}
.ch{width:100%;height:110px;display:block}.hm{display:grid;grid-template-columns:repeat(7,1fr);gap:4px;max-width:380px}
.hm i{aspect-ratio:1;border-radius:7px;background:var(--s2);font:11px/1 Sora,sans-serif;display:flex;align-items:center;justify-content:center;font-style:normal;color:var(--tx)}.hm .hl{background:none;color:var(--mu)}
table{width:100%;border-collapse:collapse}td,th{padding:8px 6px;text-align:left;border-bottom:1px solid var(--s2);font-size:14px}
.banner{background:var(--g);color:#fff;border-radius:16px;padding:14px 18px;margin-bottom:14px;display:flex;justify-content:space-between;align-items:center;gap:10px;flex-wrap:wrap}.banner .btn{background:#fff3;color:#fff}
.fab{position:fixed;right:18px;bottom:calc(78px + env(safe-area-inset-bottom,0px));z-index:5;width:54px;height:54px;border-radius:50%;font-size:28px;color:#fff;background:var(--g);box-shadow:0 8px 24px #9b6bff66;display:none}
#toast{position:fixed;left:50%;bottom:90px;transform:translateX(-50%);background:var(--s2);padding:10px 16px;border-radius:12px;opacity:0;pointer-events:none;transition:.3s;z-index:20}#toast.on{opacity:1}
@media(max-width:800px){.app{display:block}nav{position:fixed;bottom:0;left:0;right:0;top:auto;height:auto;flex-direction:row;padding:6px 6px calc(6px + env(safe-area-inset-bottom,0px));z-index:6;justify-content:space-around}
nav .logo{display:none}nav button{flex-direction:column;gap:2px;font-size:10px;padding:6px 4px}main{padding:16px 14px 100px}.fab{display:block}}
@media(prefers-reduced-motion:reduce){*{animation:none!important;transition:none!important}}
@media print{nav,.fab,.noprint,#toast{display:none!important}.app{display:block}:root{--bg:#fff;--s1:#fff;--s2:#eee;--tx:#111;--mu:#555}body{background:#fff}}
</style></head><body>
<svg width="0" height="0" style="position:absolute"><defs><linearGradient id="g" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#4f8cff"/><stop offset="1" stop-color="#9b6bff"/></linearGradient></defs></svg>
<div class="app"><nav id="nav"></nav><main id="view"></main></div>
<button class="fab" data-a="new" aria-label="Nueva actividad">+</button>
<dialog id="md"></dialog><div id="toast"></div>
<script>
const $=s=>document.querySelector(s),fmt=d=>d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0')+'-'+String(d.getDate()).padStart(2,'0'),T=()=>fmt(new Date()),P=s=>new Date(s+'T00:00:00'),
add=(s,n)=>{const d=P(s);d.setDate(d.getDate()+n);return fmt(d)},uid=()=>Math.random().toString(36).slice(2,9),
esc=s=>String(s??'').replace(/[&<>"]/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c])),
pc=x=>x==null?'—':(Math.round(x*10)/10)+' %',
CATS={Estudio:'#4f8cff',Salud:'#34d399',Proyectos:'#9b6bff',Personal:'#f472b6',Trabajo:'#fbbf24'},PRI=['Baja','Media','Alta'],
MN=['enero','febrero','marzo','abril','mayo','junio','julio','agosto','septiembre','octubre','noviembre','diciembre'],DN=['dom','lun','mar','mié','jue','vie','sáb'],
SL={done:'Completada',pend:'Pendiente',over:'Vencida',canc:'Cancelada'},wk0=s=>{const d=P(s);d.setDate(d.getDate()-((d.getDay()+6)%7));return fmt(d)};
let S,V='home',N=new Date(),CM={y:N.getFullYear(),m:N.getMonth()},sel=T(),SM=null,H={a:'',b:''},E={},popK='',F={q:'',c:'',s:'',f:add(T(),-30),t:add(T(),30)};
try{S=JSON.parse(localStorage.getItem('pu1'))}catch(e){}
function save(){try{localStorage.setItem('pu1',JSON.stringify(S))}catch(e){}}
/* ---- modelo ---- */
function on(a,d){if(d<a.date)return false;if(a.rec==='none')return d===a.date;const w=P(d).getDay();if(a.rec==='daily')return true;if(a.rec==='weekly')return w===P(a.date).getDay();return(a.days||[]).includes(w)}
function st(a,d){return a.canc[d]?'canc':a.done[d]?'done':d<T()?'over':'pend'}
function dayOcc(d){return S.acts.filter(a=>on(a,d)).map(a=>({a,d,s:st(a,d)})).sort((x,y)=>(x.a.time||'99').localeCompare(y.a.time||'99'))}
function ds(d){const o=dayOcc(d),r={o,d:0,e:0,c:0,p:null};o.forEach(x=>{if(x.s==='canc')r.c++;else if(d<=T()){r.e++;if(x.s==='done')r.d++}});if(r.e)r.p=r.d/r.e*100;return r}
function mstats(y,m){const n=new Date(y,m+1,0).getDate(),c={done:0,pend:0,over:0,canc:0},cats={},miss={},days=[];
for(let i=1;i<=n;i++){const d=fmt(new Date(y,m,i));if(d>T()){days.push(null);continue}const x=ds(d);days.push(x);
x.o.forEach(o=>{c[o.s]++;if(o.s==='canc')return;const k=cats[o.a.cat]=cats[o.a.cat]||{d:0,e:0};k.e++;if(o.s==='done')k.d++;else miss[o.a.name]=(miss[o.a.name]||0)+1})}
const tot=c.done+c.pend+c.over;return{c,cats,miss,days,tot,pct:tot?c.done/tot*100:null}}
function streak(){const t=T();let n=0,min=S.acts.reduce((m,a)=>a.date<m?a.date:m,t);for(let d=t;d>=min;d=add(d,-1)){const x=ds(d);if(!x.e)continue;if(x.p===100)n++;else if(d!==t)break}return n}
function bestRun(days){let b=0,r=0;days.forEach(x=>{if(!x||!x.e)return;if(x.p===100){r++;b=Math.max(b,r)}else r=0});return b}
const gcount=(g,a,b)=>Object.keys(g.log).filter(k=>g.log[k]&&k>=a&&k<=b).length;
function gevo(g){const o=[];if(g.per==='semana'){for(let i=7;i>=0;i--){const a=add(wk0(T()),-7*i);o.push(Math.min(100,gcount(g,a,add(a,6))/g.n*100))}}else for(let i=5;i>=0;i--){const a=new Date(N.getFullYear(),N.getMonth()-i,1);o.push(Math.min(100,gcount(g,fmt(a),fmt(new Date(a.getFullYear(),a.getMonth()+1,0)))/g.n*100))}return o}
function seed(){const s0=fmt(new Date(N.getFullYear(),N.getMonth()-2,1)),mk=(n,cat,time,pri,rec,days)=>({id:uid(),name:n+' (ejemplo)',desc:'',date:s0,time,cat,pri,rec,days:days||[],done:{},canc:{},demo:1}),
acts=[mk('Estudiar 1 h','Estudio','19:00',2,'daily'),mk('Caminar 30 min','Salud','07:00',1,'daily'),mk('Leer 20 páginas','Personal','21:30',0,'daily'),mk('Practicar programación','Proyectos','18:00',2,'days',[1,3,5]),mk('Revisión semanal','Trabajo','10:00',1,'weekly')],
goals=[{id:uid(),name:'Hacer ejercicio (ejemplo)',desc:'Entrenar de forma saludable',n:4,per:'semana',log:{},demo:1}];
S={acts,goals,set:{name:'',theme:'dark',notif:0,rem:10},seen:{}};let r=7;const rnd=()=>(r=(r*9301+49297)%233280)/233280;
for(let d=s0;d<T();d=add(d,1)){const m=P(d).getMonth(),p=m===N.getMonth()?.82:m===(N.getMonth()+11)%12?.74:.6;dayOcc(d).forEach(o=>{if(rnd()<p)o.a.done[d]=1});if(rnd()<p-.15)goals[0].log[d]=1}return S}
if(!S||!S.acts)seed();
const commit=()=>{save();render()};
/* ---- gráficos ---- */
const bars=v=>`<svg viewBox="0 0 ${v.length*10} 100" preserveAspectRatio="none" class="ch">${v.map((x,i)=>x==null?'':`<rect x="${i*10+1}" y="${98-x*.9}" width="8" height="${x*.9+2}" rx="2" fill="url(#g)"><title>${Math.round(x)} %</title></rect>`).join('')}</svg>`;
function line(v,lab){const pts=v.map((x,i)=>x==null?null:[14+i*272/Math.max(v.length-1,1),90-x*.78,x,i]).filter(Boolean);return`<svg viewBox="0 0 300 118" class="ch" style="height:130px"><polyline points="${pts.map(p=>p[0]+','+p[1]).join(' ')}" fill="none" stroke="url(#g)" stroke-width="3" stroke-linejoin="round"/>${pts.map(p=>`<circle cx="${p[0]}" cy="${p[1]}" r="4" fill="#9b6bff"><title>${Math.round(p[2])} %</title></circle><text x="${p[0]}" y="112" font-size="9" text-anchor="middle" fill="#9aa0c8">${lab[p[3]]}</text>`).join('')}</svg>`}
function heat(y,m,days){const off=(new Date(y,m,1).getDay()+6)%7;return`<div class="hm">${['L','M','X','J','V','S','D'].map(x=>`<i class="hl">${x}</i>`).join('')}${'<i class="hl"></i>'.repeat(off)}${days.map((d,i)=>`<i title="${d&&d.p!=null?Math.round(d.p)+' %':'Sin datos'}" style="${d&&d.p!=null?`background:color-mix(in srgb,var(--p) ${Math.round(15+d.p*.85)}%,var(--s2))`:''}">${i+1}</i>`).join('')}</div><small>Más oscuro = menor cumplimiento. Más intenso = mayor cumplimiento.</small>`}
/* ---- componentes ---- */
function row(o){const a=o.a;return`<div class="row ${o.s} ${popK===a.id+o.d?'pop':''}"><button class="ck" data-a="tg" data-i="${a.id}" data-d="${o.d}" aria-label="Marcar como completada" style="--c:${CATS[a.cat]}">${o.s==='done'?'✓':''}</button><div class="rb" data-a="ed" data-i="${a.id}" data-d="${o.d}"><b>${esc(a.name)}</b><small>${a.time||'Sin hora'}, ${a.cat}, prioridad ${PRI[a.pri].toLowerCase()}${a.rec!=='none'?', se repite':''}${a.demo?', ejemplo':''}</small></div><span class="tag ${o.s}">${SL[o.s]}</span></div>`}
const list=(os,empty)=>os.length?os.map(row).join(''):`<p class="mu">${empty}</p>`;
const cmpTxt=(a,b)=>{if(a==null||b==null)return'Aún no hay datos del mes anterior para comparar.';const d=Math.round((a-b)*10)/10;if(!d)return'El progreso se mantuvo estable.';const rel=b>0?` (cambio relativo: ${d>0?'+':''}${Math.round((a-b)/b*1000)/10} %)`:'';return(d>0?'¡Mejoraste ':'Bajaste ')+Math.abs(d)+' puntos porcentuales'+(d>0?'!':'.')+rel};
function prevOf(y,m){return m?[y,m-1]:[y-1,11]}
function report(y,m){const s=mstats(y,m),[py,pm]=prevOf(y,m),p=mstats(py,pm),cur=y===N.getFullYear()&&m===N.getMonth();
if(!s.tot)return`<div class="card"><h2>${MN[m]} ${y}</h2><p class="mu">No hay actividades evaluables en este mes. Agrega actividades y márcalas para ver el informe.</p></div>`;
const cl=Object.entries(s.cats).map(([k,v])=>{const pp=p.cats[k]?p.cats[k].d/p.cats[k].e*100:null,me=v.d/v.e*100;return{k,me,df:pp==null?null:me-pp,n:v.e}}).sort((a,b)=>b.me-a.me);
const wkv=[],wkl=[];for(let i=0;i<s.days.length;i+=7){const sl=s.days.slice(i,i+7).filter(x=>x&&x.e),e=sl.reduce((a,x)=>a+x.e,0);wkv.push(e?sl.reduce((a,x)=>a+x.d,0)/e*100:null);wkl.push('S'+(i/7+1))}
const miss=Object.entries(s.miss).sort((a,b)=>b[1]-a[1]).slice(0,3),perf=s.days.filter(x=>x&&x.p===100).length,up=cl.filter(c=>c.df>0),down=cl.filter(c=>c.df<0);
return`<div class="card"><h2>Informe de ${MN[m]} ${y}${cur?' (mes en curso, parcial)':''}</h2><div class="grid"><div class="kpi"><small>Cumplimiento</small><b>${pc(s.pct)}</b></div><div class="kpi"><small>Realizadas</small><b>${s.c.done}</b></div><div class="kpi"><small>Pendientes</small><b>${s.c.pend}</b></div><div class="kpi"><small>Vencidas</small><b>${s.c.over}</b></div><div class="kpi"><small>Mejor racha</small><b>${bestRun(s.days)} d</b></div></div>
<p><b>${cmpTxt(s.pct,p.pct)}</b>${p.pct!=null?` <span class="mu">Mes anterior: ${pc(p.pct)}.</span>`:''}</p><small>${s.c.canc} canceladas excluidas del cálculo. Las fechas futuras no cuentan.</small></div>
<div class="card"><h2>Evolución diaria</h2>${bars(s.days.map(x=>x&&x.p))}<h2 style="margin-top:14px">Evolución semanal</h2>${line(wkv,wkl)}</div>
<div class="card"><h2>Calendario de calor</h2>${heat(y,m,s.days)}</div>
<div class="card"><h2>Categorías</h2><table><tr><th>Categoría</th><th>Cumplimiento</th><th>Vs. mes anterior</th></tr>${cl.map(c=>`<tr><td><span class="dots" style="display:inline-flex"><i style="background:${CATS[c.k]}"></i></span> ${c.k}</td><td>${pc(c.me)}</td><td style="color:${c.df==null?'var(--mu)':c.df>=0?'var(--ok)':'var(--bad)'}">${c.df==null?'—':(c.df>0?'+':'')+Math.round(c.df*10)/10+' pp'}</td></tr>`).join('')}</table></div>
<div class="card"><h2>Resumen</h2><p>Logros: ${perf} día${perf==1?'':'s'} con el 100 % completado y una racha máxima de ${bestRun(s.days)}. ${cl[0]?`Tu mejor categoría fue ${cl[0].k} (${pc(cl[0].me)}).`:''}</p><p>${up.length?'Mejoraste en: '+up.map(c=>c.k).join(', ')+'. ':''}${down.length?'Debes trabajar más en: '+down.map(c=>c.k).join(', ')+'. ':''}${!up.length&&!down.length&&cl.length?'Menor cumplimiento: '+cl[cl.length-1].k+'.':''}</p><p>${miss.length?'Lo que más dejas pendiente: '+miss.map(x=>`${esc(x[0])} (${x[1]})`).join(', ')+'.':'No quedaron actividades sin completar.'}</p></div>`}
/* ---- vistas ---- */
const views={
home(){const t=T(),x=ds(t),h=N.getHours(),g=h<12?'Buenos días':h<19?'Buenas tardes':'Buenas noches',nm=S.set.name?', '+esc(S.set.name):'',pend=x.o.filter(o=>o.s==='pend'),nowT=new Date().toTimeString().slice(0,5),up=[];
for(let i=0;i<8&&up.length<5;i++)dayOcc(add(t,i)).forEach(o=>{if(o.s==='pend'&&(i>0||!o.a.time||o.a.time>=nowT)&&up.length<5)up.push(o)});
const ws=wk0(t),wd=[0,1,2,3,4,5,6].map(i=>ds(add(ws,i))),we=wd.reduce((a,z)=>a+z.e,0),[py,pm]=prevOf(N.getFullYear(),N.getMonth()),pk=py+'-'+pm,pp=mstats(py,pm),hasPrev=pp.tot>0&&!S.seen[pk];
return`${S.demoOn!==0&&S.acts.some(a=>a.demo)?`<div class="banner"><span>Estás viendo datos de ejemplo.</span><button class="btn" data-a="deldemo">Borrar ejemplos y empezar</button></div>`:''}${hasPrev?`<div class="banner"><span>Tu informe de ${MN[pm]} está listo.</span><button class="btn" data-a="rep" data-y="${py}" data-m="${pm}">Ver informe</button></div>`:''}
<div class="top"><div><h1>${g}${nm}</h1><span class="mu">${DN[N.getDay()]}, ${N.getDate()} de ${MN[N.getMonth()]} de ${N.getFullYear()}</span></div><button class="btn pri noprint" data-a="new">+ Nueva actividad</button></div>
<div class="card"><div class="top" style="margin:0 0 8px"><h2 style="margin:0">Progreso de hoy</h2><b>${x.e?pc(x.p):'Sin actividades'}</b></div><div class="bar"><i style="width:${x.p||0}%"></i></div></div>
<div class="grid"><div class="kpi"><small>Completadas hoy</small><b>${x.d}</b></div><div class="kpi"><small>Pendientes hoy</small><b>${pend.length}</b></div><div class="kpi"><small>Racha actual</small><b>${streak()} d</b></div></div>
<div class="card"><h2>Pendientes de hoy</h2>${list(pend,'No tienes pendientes hoy.')}</div>
<div class="card"><h2>Próximas actividades</h2>${up.length?up.map(o=>`<div class="row"><div class="rb" data-a="ed" data-i="${o.a.id}" data-d="${o.d}"><b>${esc(o.a.name)}</b><small>${o.d===t?'Hoy':DN[P(o.d).getDay()]+' '+P(o.d).getDate()}, ${o.a.time||'Sin hora'}</small></div></div>`).join(''):'<p class="mu">Nada programado en los próximos días.</p>'}</div>
<div class="card"><h2>Semana actual</h2><div class="top" style="margin:0"><span>${we?pc(wd.reduce((a,z)=>a+z.d,0)/we*100):'—'}</span><small>${wd.reduce((a,z)=>a+z.d,0)} de ${we} completadas</small></div>${bars(wd.map(z=>z.p))}</div>`},
cal(){const{y,m}=CM,off=(new Date(y,m,1).getDay()+6)%7,n=new Date(y,m+1,0).getDate();let c=['L','M','X','J','V','S','D'].map(x=>`<div class="h">${x}</div>`).join('')+'<div class="day x"></div>'.repeat(off);
for(let i=1;i<=n;i++){const d=fmt(new Date(y,m,i)),o=dayOcc(d).filter(z=>z.s!=='canc');c+=`<button class="day ${d===sel?'sel':''} ${d===T()?'today':''}" data-a="sd" data-d="${d}">${i}<span class="dots">${[...new Set(o.map(z=>z.a.cat))].map(k=>`<i style="background:${CATS[k]}"></i>`).join('')}</span></button>`}
const dd=dayOcc(sel),x=ds(sel);return`<div class="top"><h1>${MN[CM.m]} ${CM.y}</h1><div class="acts noprint"><button class="btn" data-a="cm" data-n="-1" aria-label="Mes anterior">‹</button><button class="btn" data-a="ct">Hoy</button><button class="btn" data-a="cm" data-n="1" aria-label="Mes siguiente">›</button></div></div><div class="card"><div class="cal">${c}</div></div>
<div class="card"><div class="top" style="margin:0 0 8px"><h2 style="margin:0">${P(sel).getDate()} de ${MN[P(sel).getMonth()]}</h2><button class="btn pri" data-a="new" data-d="${sel}">+ Agregar</button></div><small>${x.d} completadas, ${dd.filter(o=>o.s==='pend').length} pendientes, ${dd.filter(o=>o.s==='over').length} vencidas</small>${list(dd,'No hay actividades este día. Agrega una con el botón.')}</div>`},
goals(){return`<div class="top"><h1>Objetivos y hábitos</h1><button class="btn pri" data-a="ng">+ Nuevo objetivo</button></div>${S.goals.length?S.goals.map(g=>{const t=T(),a=g.per==='semana'?wk0(t):t.slice(0,8)+'01',b=g.per==='semana'?add(a,6):t.slice(0,8)+'31',c=gcount(g,a,b),ev=gevo(g),last=Object.keys(g.log).filter(k=>g.log[k]).sort().reverse().slice(0,8);
return`<div class="card"><div class="top" style="margin:0"><div><h2 style="margin:0">${esc(g.name)}</h2><small>${esc(g.desc)||'Sin descripción'}. Meta: ${g.n} veces por ${g.per}.</small></div><button class="btn ${g.log[t]?'':'pri'}" data-a="gl" data-i="${g.id}" data-d="${t}">${g.log[t]?'Registrado hoy ✓':'Registrar hoy'}</button></div>
<p>Este${g.per==='semana'?'a semana':' mes'}: <b>${c} de ${g.n}</b></p><div class="bar"><i style="width:${Math.min(100,c/g.n*100)}%"></i></div><h2 style="margin-top:14px">Evolución (${g.per==='semana'?'últimas 8 semanas':'últimos 6 meses'})</h2>${bars(ev)}
<label style="margin-top:10px">Registrar otro día<input type="date" max="${t}" data-a="glp" data-i="${g.id}"></label><small>Historial reciente: ${last.map(k=>P(k).getDate()+'/'+(P(k).getMonth()+1)).join(', ')||'sin registros'}</small><div class="acts"><button class="btn dg" data-a="dg" data-i="${g.id}">Eliminar objetivo</button></div></div>`}).join(''):'<div class="card"><p class="mu">Crea tu primer objetivo, por ejemplo leer 3 veces por semana.</p></div>'}`},
stats(){const[y,m]=SM||[N.getFullYear(),N.getMonth()];return`<div class="top noprint"><h1>Estadísticas</h1><div class="acts"><select data-a="sm" style="width:auto;margin:0">${months().map(([a,b])=>`<option value="${a}-${b}" ${a==y&&b==m?'selected':''}>${MN[b]} ${a}</option>`).join('')}</select><button class="btn" data-a="pdf">Descargar PDF</button></div></div>${report(y,m)}<small class="noprint">Para el PDF, elige Guardar como PDF en la ventana de impresión.</small>`},
hist(){const ms=months().reverse(),a=H.a||(ms[1]||ms[0]).join('-'),b=H.b||ms[0].join('-'),ps=s=>s.split('-').map(Number),A=mstats(...ps(a)),B=mstats(...ps(b)),opt=v=>ms.map(([y,m])=>`<option value="${y}-${m}" ${v===y+'-'+m?'selected':''}>${MN[m]} ${y}</option>`).join('');
return`<h1>Historial</h1><div class="card"><h2>Meses guardados</h2>${ms.map(([y,m])=>{const s=mstats(y,m);return`<div class="row"><div class="rb" data-a="rep" data-y="${y}" data-m="${m}"><b>${MN[m]} ${y}</b><small>${s.tot} actividades evaluables, ${s.c.done} completadas</small></div><b>${pc(s.pct)}</b></div>`}).join('')}</div>
<div class="card"><h2>Comparar dos meses</h2><div class="g2"><label>Mes A<select data-a="ha">${opt(a)}</select></label><label>Mes B<select data-a="hb">${opt(b)}</select></label></div>
<table><tr><th></th><th>A</th><th>B</th></tr><tr><td>Cumplimiento</td><td>${pc(A.pct)}</td><td>${pc(B.pct)}</td></tr><tr><td>Realizadas</td><td>${A.c.done}</td><td>${B.c.done}</td></tr><tr><td>Pendientes</td><td>${A.c.pend}</td><td>${B.c.pend}</td></tr><tr><td>Vencidas</td><td>${A.c.over}</td><td>${B.c.over}</td></tr></table>
<p><b>${A.pct==null||B.pct==null?'Sin datos suficientes para comparar.':'De A a B: '+cmpTxt(B.pct,A.pct)}</b></p></div>`},
find(){return`<h1>Buscar</h1><div class="card"><label>Texto<input data-f="q" value="${esc(F.q)}" placeholder="Nombre o descripción"></label><div class="g2"><label>Categoría<select data-f="c"><option value="">Todas</option>${Object.keys(CATS).map(k=>`<option ${F.c===k?'selected':''}>${k}</option>`).join('')}</select></label><label>Estado<select data-f="s"><option value="">Todos</option>${Object.entries(SL).map(([k,v])=>`<option value="${k}" ${F.s===k?'selected':''}>${v}</option>`).join('')}</select></label></div><div class="g2"><label>Desde<input type="date" data-f="f" value="${F.f}"></label><label>Hasta<input type="date" data-f="t" value="${F.t}"></label></div></div><div class="card" id="res">${found()}</div>`}};
function found(){const q=F.q.toLowerCase();let r=[];for(let d=F.f,i=0;d<=F.t&&i<400;d=add(d,1),i++)dayOcc(d).forEach(o=>{if((!F.c||o.a.cat===F.c)&&(!F.s||o.s===F.s)&&(!q||(o.a.name+' '+o.a.desc).toLowerCase().includes(q)))r.push(o)});
return r.length?`<small>${r.length} resultados</small>`+r.slice(0,150).map(o=>`<small>${o.d}</small>`+row(o)).join(''):'<p class="mu">Sin resultados. Prueba con otro rango de fechas o filtro.</p>'}
function months(){const min=S.acts.reduce((m,a)=>a.date<m?a.date:m,T()),r=[];let y=+min.slice(0,4),m=+min.slice(5,7)-1;while(y<N.getFullYear()||(y===N.getFullYear()&&m<=N.getMonth())){r.push([y,m]);if(++m>11){m=0;y++}}return r}
const NAV=[['home','⌂','Inicio'],['cal','▦','Calendario'],['goals','◎','Objetivos'],['stats','◔','Estadísticas'],['hist','☰','Historial'],['find','⌕','Buscar']];
function render(){document.documentElement.dataset.t=S.set.theme;$('#nav').innerHTML=`<div class="logo">ProgressUp</div>`+NAV.map(([k,i,l])=>`<button data-a="nav" data-v="${k}" class="${V===k?'on':''}"><span>${i}</span>${l}</button>`).join('')+`<button data-a="set"><span>⚙</span>Ajustes</button>`;$('#view').innerHTML=views[V]();popK=''}
/* ---- formularios ---- */
const modal=h=>{$('#md').innerHTML=h;$('#md').showModal()},toast=t=>{const e=$('#toast');e.textContent=t;e.className='on';setTimeout(()=>e.className='',2600)};
function form(id,d){const a=id?S.acts.find(x=>x.id===id):{name:'',desc:'',date:d||T(),time:'',cat:'Estudio',pri:1,rec:'none',days:[]};E={id,d},rec=id&&a.rec!=='none';
modal(`<h3>${id?'Editar actividad':'Nueva actividad'}</h3><label>Nombre<input id="f_n" value="${esc(a.name)}"></label><label>Descripción (opcional)<textarea id="f_d" rows="2">${esc(a.desc)}</textarea></label>
<div class="g2"><label>${rec?'Inicia el':'Fecha'}<input type="date" id="f_f" value="${a.date}"></label><label>Hora<input type="time" id="f_t" value="${a.time}"></label></div>
<div class="g2"><label>Categoría<select id="f_c">${Object.keys(CATS).map(k=>`<option ${a.cat===k?'selected':''}>${k}</option>`).join('')}</select></label><label>Prioridad<select id="f_p">${PRI.map((p,i)=>`<option value="${i}" ${a.pri===i?'selected':''}>${p}</option>`).join('')}</select></label></div>
<label>Repetición<select id="f_r" data-a="rp">${[['none','No se repite'],['daily','Todos los días'],['weekly','Cada semana'],['days','Días específicos']].map(([v,l])=>`<option value="${v}" ${a.rec===v?'selected':''}>${l}</option>`).join('')}</select></label>
<div class="wk" id="f_w" style="display:${a.rec==='days'?'flex':'none'}">${[1,2,3,4,5,6,0].map(i=>`<label><input type="checkbox" value="${i}" ${a.days.includes(i)?'checked':''}>${DN[i]}</label>`).join('')}</div>
${rec&&d?`<label>Mover solo el ${d} a<input type="date" id="f_m" value="${d}"></label>`:''}
<div class="acts"><button class="btn pri" data-a="sv">Guardar</button>${rec&&d?'<button class="btn" data-a="mv">Mover este día</button>':''}${id&&d?`<button class="btn" data-a="cn">${a.canc[d]?'Restaurar este día':'Cancelar este día'}</button>`:''}${id?'<button class="btn dg" data-a="del">Eliminar</button>':''}<button class="btn" data-a="x">Cerrar</button></div>`)}
function goalForm(){modal(`<h3>Nuevo objetivo</h3><label>Nombre<input id="g_n"></label><label>Descripción<input id="g_d"></label><div class="g2"><label>Veces<input type="number" id="g_c" min="1" value="3"></label><label>Por<select id="g_p"><option>semana</option><option>mes</option></select></label></div><div class="acts"><button class="btn pri" data-a="sg">Crear objetivo</button><button class="btn" data-a="x">Cerrar</button></div>`)}
function settings(){const s=S.set;modal(`<h3>Ajustes</h3><label>Tu nombre<input id="s_n" value="${esc(s.name)}"></label><label>Tema<select id="s_t"><option value="dark" ${s.theme==='dark'?'selected':''}>Oscuro</option><option value="light" ${s.theme==='light'?'selected':''}>Claro</option></select></label>
<label>Recordatorios<select id="s_o"><option value="0" ${!s.notif?'selected':''}>Desactivados</option><option value="1" ${s.notif?'selected':''}>Activados</option></select></label><label>Avisar con anticipación (minutos)<input type="number" id="s_r" min="0" max="120" value="${s.rem}"></label>
<small>Tus datos se guardan solo en este navegador y no se envían a ningún servidor.</small><div class="acts" style="margin-top:12px"><button class="btn pri" data-a="ss">Guardar ajustes</button><button class="btn dg" data-a="rst">Borrar todos mis datos</button><button class="btn" data-a="x">Cerrar</button></div>`)}
/* ---- eventos ---- */
let armed='';
document.addEventListener('click',e=>{const t=e.target.closest('[data-a]');if(!t||/^(SELECT|INPUT)$/.test(t.tagName))return;const a=t.dataset.a,i=t.dataset.i,d=t.dataset.d,get=id=>S.acts.find(x=>x.id===id),close=()=>$('#md').close();
if(a==='nav'){V=t.dataset.v;render()}else if(a==='new')form(null,t.dataset.d||(V==='cal'?sel:T()));else if(a==='ed')form(i,d);
else if(a==='tg'){const x=get(i);if(x.canc[d])delete x.canc[d];if(x.done[d])delete x.done[d];else{x.done[d]=1;popK=i+d}commit();if(V==='find')$('#res').innerHTML=found()}
else if(a==='x')close();else if(a==='sd'){sel=d;render()}else if(a==='cm'){const n=new Date(CM.y,CM.m+ +t.dataset.n,1);CM={y:n.getFullYear(),m:n.getMonth()};render()}else if(a==='ct'){CM={y:N.getFullYear(),m:N.getMonth()};sel=T();render()}
else if(a==='sv'){const n=$('#f_n').value.trim();if(!n){$('#f_n').focus();return}const o={name:n,desc:$('#f_d').value.trim(),date:$('#f_f').value||T(),time:$('#f_t').value,cat:$('#f_c').value,pri:+$('#f_p').value,rec:$('#f_r').value,days:[...document.querySelectorAll('#f_w input:checked')].map(x=>+x.value),demo:0};
if(o.rec==='days'&&!o.days.length){toast('Elige al menos un día de la semana');return}if(E.id)Object.assign(get(E.id),o);else S.acts.push({id:uid(),done:{},canc:{},...o});close();commit();toast('Guardado')}
else if(a==='mv'){const x=get(E.id),nd=$('#f_m').value;if(!nd||nd===E.d)return;x.canc[E.d]=1;S.acts.push({...x,id:uid(),date:nd,rec:'none',days:[],done:{},canc:{}});close();commit();toast('Actividad reprogramada')}
else if(a==='cn'){const x=get(E.id);if(x.canc[E.d])delete x.canc[E.d];else x.canc[E.d]=1;close();commit()}
else if(a==='del'||a==='dg'||a==='rst'){const k=a+(i||'');if(armed!==k){armed=k;t.textContent='Toca de nuevo para confirmar';return}armed='';
if(a==='del')S.acts=S.acts.filter(x=>x.id!==E.id);else if(a==='dg')S.goals=S.goals.filter(x=>x.id!==i);else{const nm=S.set;S={acts:[],goals:[],set:nm,seen:{}}}close();commit()}
else if(a==='deldemo'){S.acts=S.acts.filter(x=>!x.demo);S.goals=S.goals.filter(x=>!x.demo);commit();toast('Ejemplos eliminados. Empieza con tus datos')}
else if(a==='ng')goalForm();else if(a==='sg'){const n=$('#g_n').value.trim();if(!n){$('#g_n').focus();return}S.goals.push({id:uid(),name:n,desc:$('#g_d').value.trim(),n:Math.max(1,+$('#g_c').value||1),per:$('#g_p').value,log:{}});close();commit()}
else if(a==='gl'){const g=S.goals.find(x=>x.id===i);g.log[d]=!g.log[d];commit()}
else if(a==='rep'){SM=[+t.dataset.y,+t.dataset.m];S.seen[SM[0]+'-'+SM[1]]=1;V='stats';commit()}else if(a==='pdf')window.print();
else if(a==='set')settings();else if(a==='ss'){S.set.name=$('#s_n').value.trim();S.set.theme=$('#s_t').value;S.set.notif=+$('#s_o').value;S.set.rem=+$('#s_r').value||0;if(S.set.notif&&window.Notification&&Notification.permission==='default')Notification.requestPermission();close();commit()}});
document.addEventListener('change',e=>{const t=e.target,a=t.dataset.a;if(a==='rp')$('#f_w').style.display=t.value==='days'?'flex':'none';else if(a==='sm'){SM=t.value.split('-').map(Number);S.seen[t.value]=1;commit()}else if(a==='ha'){H.a=t.value;render()}else if(a==='hb'){H.b=t.value;render()}
else if(a==='glp'&&t.value){const g=S.goals.find(x=>x.id===t.dataset.i);g.log[t.value]=!g.log[t.value];commit()}else if(t.dataset.f){F[t.dataset.f]=t.value;$('#res').innerHTML=found()}});
document.addEventListener('input',e=>{if(e.target.dataset.f==='q'){F.q=e.target.value;$('#res').innerHTML=found()}});
/* ---- recordatorios ---- */
const sent={};setInterval(()=>{if(!S.set.notif)return;const n=new Date(),now=n.getHours()*60+n.getMinutes();dayOcc(T()).forEach(o=>{if(o.s!=='pend'||!o.a.time)return;const[h,m]=o.a.time.split(':'),df=h*60+ +m-now,k=o.a.id+T();if(df>=0&&df<=S.set.rem&&!sent[k]){sent[k]=1;const msg=`${o.a.name} a las ${o.a.time}`;toast('Recordatorio: '+msg);try{if(Notification.permission==='granted')new Notification('ProgressUp',{body:msg})}catch(e){}}})},30000);
render();
</script></body></html>
 
Claude terminó la respuesta
