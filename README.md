<html lang="el">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Greece Weather</title>
<style>
*{box-sizing:border-box}
body{margin:0;font-family:Arial,Helvetica,sans-serif;color:#fff;background:linear-gradient(180deg,#071d35,#0d3762)}
.container{width:min(100%,960px);margin:auto;padding:16px}
.header{position:relative;background:rgba(3,20,38,.72);padding:28px 60px 28px 20px;text-align:center;margin-bottom:25px}
.header h1{margin:0;font-size:30px}.header p{margin:18px 0 0;color:#d6dce4;font-size:16px}
.menu-button{position:absolute;top:18px;right:18px;width:43px;height:43px;border:0;border-radius:12px;background:rgba(255,255,255,.12);color:#fff;font-size:25px;cursor:pointer;display:flex;align-items:center;justify-content:center}
.menu-button:hover{background:rgba(255,255,255,.22)}
.menu{display:none;position:absolute;top:68px;right:18px;width:285px;max-height:70vh;overflow-y:auto;background:rgba(5,27,50,.97);border:1px solid rgba(255,255,255,.18);border-radius:15px;padding:8px;z-index:1000;box-shadow:0 10px 30px rgba(0,0,0,.35)}
.menu.open{display:block}.menu-item{width:100%;border:0;background:transparent;color:#fff;text-align:left;padding:13px 12px;border-radius:10px;font-size:14px;cursor:pointer}.menu-item:hover{background:rgba(255,255,255,.12)}
.search{display:flex;gap:10px;margin-bottom:25px}.search input{flex:1;min-width:0;border:0;outline:0;border-radius:15px;padding:17px;font-size:16px}.search button{border:0;border-radius:15px;padding:0 22px;font-weight:bold;font-size:15px;cursor:pointer}
.current{background:rgba(255,255,255,.1);border-radius:20px;padding:25px;text-align:center;margin-bottom:25px}.current h2{margin:0 0 20px;font-size:24px}.temperature{font-size:64px;font-weight:bold;margin-bottom:10px}.condition{font-size:17px;margin-bottom:25px;display:flex;align-items:center;justify-content:center;gap:10px;flex-wrap:wrap}.current-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}.current-box{background:rgba(255,255,255,.08);border-radius:14px;padding:15px 10px}.current-box span{display:block;color:#d6dce4;margin-bottom:8px;font-size:13px}.current-box strong{font-size:15px;line-height:1.5}
.section-title{display:flex;align-items:center;gap:8px;font-size:24px;font-weight:bold;border-bottom:2px solid rgba(255,255,255,.55);padding-bottom:12px;margin:26px 0 15px}
.forecast{display:grid;grid-template-columns:repeat(6,1fr);gap:12px}.day{background:rgba(53,84,119,.78);border-radius:17px;padding:18px 8px;text-align:center;cursor:pointer;transition:.18s;border:1px solid transparent}.day:hover{transform:translateY(-3px);background:rgba(72,105,143,.95);border-color:rgba(255,255,255,.25)}.day-name{font-weight:bold;font-size:15px}.date{margin-top:9px;color:#e1e5e9;font-size:14px}.icon{margin:18px 0 12px;height:44px;display:flex;align-items:center;justify-content:center;position:relative;overflow:visible}.weather-svg{width:42px;height:42px;display:inline-flex;align-items:center;justify-content:center}.weather-svg svg{width:42px;height:42px;display:block}.condition .weather-svg{width:45px;height:45px;vertical-align:middle;margin-right:6px}.condition .weather-svg svg{width:45px;height:45px}.rain .weather-svg,.hour-data .weather-svg{width:18px;height:18px;vertical-align:middle}.rain .weather-svg svg,.hour-data .weather-svg svg{width:18px;height:18px}.hour-icon .weather-svg{width:32px;height:32px}.hour-icon .weather-svg svg{width:32px;height:32px}.max{font-size:17px;font-weight:bold}.min{margin-top:6px;color:#d0d7df}.rain{margin-top:10px;font-size:12px;color:#c9e9ff}
.hourly-section,.history-section,.extra-section{display:none;margin-top:28px;background:rgba(5,27,50,.72);border-radius:20px;padding:20px}
.hourly-header,.history-header{display:flex;align-items:center;justify-content:space-between;gap:10px;border-bottom:1px solid rgba(255,255,255,.3);padding-bottom:15px;margin-bottom:15px}.hourly-header h3,.history-header h3{margin:0;font-size:21px}.close-hourly,.close-history{background:rgba(255,255,255,.15);border:0;color:white;border-radius:10px;padding:8px 13px;cursor:pointer}
.hourly{display:grid;gap:8px}.hour{display:grid;grid-template-columns:70px 50px 1fr 1fr 1fr 1fr;align-items:center;background:rgba(65,96,130,.62);border-radius:12px;padding:12px 10px;gap:12px}.hour-time{font-weight:bold}.hour-icon{font-size:25px;text-align:center;height:32px;display:flex;align-items:center;justify-content:center;position:relative;overflow:visible}.weather-icon-wrap{position:relative;display:inline-flex;align-items:center;justify-content:center;overflow:visible;vertical-align:middle}.hour-warning,.day-warning{position:absolute;top:-3px;left:63%;transform:translateX(-50%);width:17px;height:17px;display:flex;align-items:center;justify-content:center;z-index:2;pointer-events:none}.hour-warning svg,.day-warning svg{width:17px;height:17px;display:block}.cold-warning{position:absolute;top:-3px;left:91%;transform:translateX(-50%);width:17px;height:17px;display:flex;align-items:center;justify-content:center;z-index:3;pointer-events:none}.cold-warning svg{width:17px;height:17px;display:block}.weather-icon-wrap.has-two-warnings .hour-warning,.weather-icon-wrap.has-two-warnings .day-warning{left:48%}.weather-icon-wrap.has-two-warnings .cold-warning{left:88%}.rain .weather-icon-wrap .day-warning,.hour-data .weather-icon-wrap .hour-warning,.rain .weather-icon-wrap .cold-warning{width:17px;height:17px;top:-3px}.rain .weather-icon-wrap .day-warning svg,.hour-data .weather-icon-wrap .hour-warning svg,.rain .weather-icon-wrap .cold-warning svg{width:17px;height:17px}.hour-data{font-size:13px;color:#e4e8ed;line-height:1.5}.hour-precip-symbols{display:inline-flex;align-items:center;gap:4px;margin-right:3px}.hour-precip-symbols span{font-size:15px}
.history{display:grid;gap:9px}.history-range-title{margin:0 0 14px;color:#dce5ee;font-size:15px;text-align:center}.history-ranges{display:grid;grid-template-columns:repeat(5,1fr);gap:10px}.history-range-button,.history-year-button,.history-month-button,.history-back-button{border:0;color:#fff;background:rgba(65,96,130,.72);border-radius:14px;padding:15px 8px;font-size:14px;font-weight:bold;cursor:pointer;transition:.18s}.history-range-button:hover,.history-year-button:hover,.history-month-button:hover,.history-back-button:hover{background:rgba(72,105,143,.95);transform:translateY(-2px)}.history-years{display:grid;grid-template-columns:repeat(2,1fr);gap:12px}.history-months{display:grid;grid-template-columns:repeat(3,1fr);gap:10px}.history-navigation{display:flex;gap:10px;margin-bottom:15px;flex-wrap:wrap}.history-back-button{padding:10px 14px;font-size:14px}.history-days{display:grid;grid-template-columns:repeat(6,minmax(0,1fr));gap:10px}.history-day{display:flex;flex-direction:column;align-items:center;justify-content:flex-start;min-width:0;min-height:136px;background:rgba(65,96,130,.62);border-radius:13px;padding:12px 8px}.history-date{width:100%;font-weight:bold;font-size:14px;text-align:center;white-space:nowrap;line-height:1.1;min-height:20px;display:flex;align-items:center;justify-content:center;margin-bottom:10px}.history-day-content{display:grid;grid-template-columns:18px 64px;column-gap:10px;align-items:center;justify-content:center;width:max-content;flex:1;margin-left:auto;margin-right:auto}.history-temperature{width:64px;min-width:64px;display:flex;flex-direction:column;justify-content:center;align-items:center;gap:5px;font-size:13px;line-height:1.2;text-align:center}.history-temperature .day-temp{width:100%;font-weight:bold;color:#fff;white-space:nowrap;text-align:center}.history-temperature .night-temp{width:100%;color:#d0d7df;white-space:nowrap;text-align:center}.history-thermometer{position:relative;width:18px;height:54px;flex:0 0 18px;justify-self:center}.history-thermometer:before{content:"";position:absolute;left:6px;top:1px;width:6px;height:39px;border-radius:6px;background:#f1f4f7}.history-thermometer:after{content:"";position:absolute;left:1px;bottom:0;width:17px;height:17px;border-radius:50%;background:#f1f4f7}.history-thermometer-fill{position:absolute;left:8px;bottom:8px;width:3px;height:31px;border-radius:3px;background:#e53935;z-index:2}.history-thermometer-bulb{position:absolute;left:5px;bottom:3px;width:9px;height:9px;border-radius:50%;background:#e53935;z-index:2}
.extra-content{display:grid;gap:10px}.period-card{background:rgba(65,96,130,.62);border-radius:12px;padding:14px;display:flex;justify-content:space-between;gap:12px;align-items:center}.period-card strong{font-size:16px}.period-card span{color:#dce5ee}.model-info{margin-top:18px;color:#bdc9d6;font-size:12px;line-height:1.5}.loading{text-align:center;padding:30px;font-size:16px}
@media(max-width:750px){.forecast{grid-template-columns:repeat(3,1fr)}.current-grid{grid-template-columns:1fr}.hour{grid-template-columns:55px 40px 1fr 1fr 1fr;gap:8px}.hour-data:nth-child(6),.hour-data:nth-child(7){display:none}.history-ranges{grid-template-columns:repeat(3,1fr)}.history-years{grid-template-columns:1fr}.history-months{grid-template-columns:repeat(3,1fr)}.history-days{grid-template-columns:repeat(3,minmax(0,1fr));gap:8px}.history-day{min-height:132px;padding:11px 6px}.history-date{font-size:13px}.history-temperature{font-size:11px;width:58px;min-width:58px}.history-day-content{grid-template-columns:18px 58px;column-gap:8px}}
@media(max-width:430px){.container{padding:12px}.header h1{font-size:26px}.temperature{font-size:52px}.forecast{grid-template-columns:repeat(3,1fr);gap:9px}.day{padding:15px 5px}.icon{font-size:30px}.menu{right:10px;width:245px}.history-ranges{grid-template-columns:repeat(2,1fr)}.history-months{grid-template-columns:repeat(2,1fr)}.history-days{grid-template-columns:repeat(2,minmax(0,1fr));gap:7px}.history-day{min-height:125px;border-radius:10px;padding:9px 5px}.history-date{font-size:12px;margin-bottom:8px}.history-temperature{font-size:10px;width:52px;min-width:52px}.history-day-content{grid-template-columns:18px 52px;column-gap:7px}.history-thermometer{transform:scale(.9);transform-origin:center}}
</style>
</head>
<body>
<div class="container">
  <div class="header">
    <h1>🇬🇷 Greece Weather</h1>
    <p>Πρόγνωση καιρού για όλη την Ελλάδα</p>
    <button class="menu-button" onclick="toggleMenu()" aria-label="Μενού">☰</button>
    <div id="menu" class="menu">
      <button class="menu-item" onclick="openHistorySelector()">📜 Ιστορικό τελευταίων 1–10 ετών</button>
      <button class="menu-item" onclick="openExtra('long')">📆 Μακροπρόθεσμη πρόγνωση 46 ημερών</button>
    </div>
  </div>
  <div class="search"><input id="cityInput" placeholder="Γράψε πόλη..." value="Θεσσαλονίκη"><button onclick="searchCity()">Αναζήτηση</button></div>
  <div id="current"></div>
  <div class="section-title">📅 Πρόγνωση 15 ημερών</div>
  <div id="forecast" class="forecast"><div class="loading">Φόρτωση πρόγνωσης...</div></div>
  <div id="hourlySection" class="hourly-section">
    <div class="hourly-header"><h3 id="hourlyTitle"></h3><button class="close-hourly" onclick="closeHourly()">✕ Κλείσιμο</button></div>
    <div id="hourly" class="hourly"></div>
  </div>
  <div id="historySection" class="history-section">
    <div class="history-header"><h3 id="historyTitle">📜 Ιστορικό καιρού</h3><button class="close-history" onclick="closeHistory()">✕ Κλείσιμο</button></div>
    <div id="history" class="history"></div>
  </div>
  <div id="extraSection" class="extra-section">
    <div class="history-header"><h3 id="extraTitle">Πρόγνωση</h3><button class="close-history" onclick="closeExtra()">✕ Κλείσιμο</button></div>
    <div id="extraContent" class="extra-content"></div>
  </div>
  <div class="model-info"></div>
</div>
<script>
const OPEN_METEO_FORECAST="https://api.open-meteo.com/v1/forecast";
const OPEN_METEO_GEOCODING="https://geocoding-api.open-meteo.com/v1/search";
let weatherData=null,locationData=null,historyYears=1,extraRequestId=0;
const rainCodes=[51,53,55,61,63,65,80,81,82],sleetCodes=[56,57,66,67],snowCodes=[71,73,75,77,85,86],stormCodes=[95,96,99];
const precipCodes=[...rainCodes,...sleetCodes,...snowCodes,...stormCodes];
function toggleMenu(){document.getElementById("menu").classList.toggle("open")}
function closeMenu(){document.getElementById("menu").classList.remove("open")}
function closeHistory(){document.getElementById("historySection").style.display="none"}
function closeHourly(){document.getElementById("hourlySection").style.display="none"}
function closeExtra(){document.getElementById("extraSection").style.display="none"}
function countryFlag(code){if(!code||code.length!==2)return "🌍";return String.fromCodePoint(...[...code.toUpperCase()].map(c=>127397+c.charCodeAt(0)))}
const greekDays=["Κυρ","Δευ","Τρί","Τετ","Πέμ","Παρ","Σάβ"];
function formatDate(s,year=false){const [y,m,d]=s.split("-").map(Number);const dt=new Date(Date.UTC(y,m-1,d));return {day:greekDays[dt.getUTCDay()],date:`${d}/${m}${year?"/"+y:""}`}}
function weatherIcon(code,isDay=true,prob=0,snow=0,wind=0,cloud=0,temp=99){
 code=Number(code);prob=normalizePrecipProbability(prob);snow=Number(snow)||0;wind=Number(wind)||0;cloud=Number(cloud)||0;temp=Number(temp);
 const wet=prob>=31;

 let art="cloud",label=weatherText(code),sun='<circle cx="22" cy="20" r="8" fill="url(#sunFill)" stroke="#FFCA58" stroke-width="2.5"/><path d="M22 5v4M22 31v4M7 20h4M33 20h4M11 9l3 3M30 28l3 3M33 9l-3 3M14 28l-3 3" stroke="#FFCA58" stroke-width="2.5" stroke-linecap="round"/>';
 const centeredSun='<circle cx="32" cy="30" r="10" fill="url(#sunFill)" stroke="#FFCA58" stroke-width="2.5"/><path d="M32 12v5M32 43v5M14 30h5M45 30h5M19 17l4 4M41 39l4 4M45 17l-4 4M23 39l-4 4" stroke="#FFCA58" stroke-width="2.5" stroke-linecap="round"/>';
 let defs='<defs><linearGradient id="sunFill" x1="0" y1="0" x2="1" y2="1"><stop stop-color="#FFE58A"/><stop offset="1" stop-color="#FF9F43"/></linearGradient><linearGradient id="cloudFill" x1="0" y1="0" x2="0" y2="1"><stop stop-color="#F7FCFF"/><stop offset="1" stop-color="#A8D5F2"/></linearGradient><linearGradient id="rainFill" x1="0" y1="0" x2="0" y2="1"><stop stop-color="#78E2FF"/><stop offset="1" stop-color="#3A8DFF"/></linearGradient></defs>';
 const cloudArt='<path d="M17 43h29a10 10 0 0 0 0-20 15 15 0 0 0-28-3 12 12 0 0 0-1 23Z" fill="url(#cloudFill)" stroke="#DDF4FF" stroke-width="2.5" stroke-linejoin="round"/>';
 let extra='';
 if(wet){
  if((temp<=1&&precipCodes.includes(code))||(temp<=4&&(snowCodes.includes(code)||snow>0))){art='snow';extra='<g stroke="#BCEBFF" stroke-width="2.6" stroke-linecap="round"><path d="M20 48v10m-4-7 8 4m0-4-8 4M36 48v10m-4-7 8 4m0-4-8 4M49 46v9m-3-6 6 3m0-3-6 3"/></g>'}
  else if(stormCodes.includes(code)){art='storm';extra='<path d="m32 34-8 14h8l-4 12 15-18h-9l5-8Z" fill="#FFD45C" stroke="#FFB33E" stroke-width="1.5" stroke-linejoin="round"/>'}
  else if(wet&&temp<=4&&(snowCodes.includes(code)||snow>0)){art='snow';extra='<g stroke="#BCEBFF" stroke-width="2.6" stroke-linecap="round"><path d="M20 48v10m-4-7 8 4m0-4-8 4M36 48v10m-4-7 8 4m0-4-8 4M49 46v9m-3-6 6 3m0-3-6 3"/></g>'}
  else if(sleetCodes.includes(code)){art='sleet';extra='<g stroke="#70D8FF" stroke-width="2.8" stroke-linecap="round"><path d="m23 48-3 6m13-6-3 6m13-6-3 6"/></g><g fill="#EAF8FF"><circle cx="25" cy="57" r="2"/><circle cx="40" cy="57" r="2"/></g>'}
  else {art='rain';extra='<g stroke="url(#rainFill)" stroke-width="4" stroke-linecap="round"><path d="m23 48-4 8m15-8-4 8m15-8-4 8"/></g>'}
 }
 else if([45,48].includes(code)){art='fog';extra='<g fill="none" stroke="#B9D7EA" stroke-width="3.5" stroke-linecap="round"><path d="M12 48h39M8 55h34M17 61h30"/></g>'}
 else if(code===3||cloud>=70){art='cloudy'}
 else if(code===2||cloud>=35){art='partly';extra=sun}
 else if(code===1){art=isDay?'mostly':'night';extra=isDay?sun:'<path d="M38 8a18 18 0 1 0 17 27A20 20 0 0 1 38 8Z" fill="#C8E6FF" stroke="#E8F6FF" stroke-width="2"/>'}
 else if(code===0){art=isDay?'sunny':'night';extra=isDay?sun:'<path d="M35 8a18 18 0 1 0 17 27A20 20 0 0 1 35 8Z" fill="#C8E6FF" stroke="#E8F6FF" stroke-width="2"/>'}
 else {art='partly';extra=sun}
 let body='';
 if(['sunny'].includes(art))body=centeredSun;
 else if(art==='night')body=extra;
 else if(art==='mostly')body=extra+cloudArt;
 else if(art==='partly')body=extra+'<path d="M20 49h27a9 9 0 0 0 0-18 13 13 0 0 0-24-2 10 10 0 0 0-3 20Z" fill="url(#cloudFill)" stroke="#DDF4FF" stroke-width="2.5" stroke-linejoin="round"/>'; 
 else body=cloudArt+extra;
 return `<span class="weather-svg" role="img" aria-label="${label}"><svg viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">${defs}${body}</svg></span>`;
}
function windWarningMarkup(className){return `<span class="${className}" role="img" aria-label="Προειδοποίηση ισχυρής ριπής ανέμου"><svg viewBox="0 0 36 36" xmlns="http://www.w3.org/2000/svg" aria-hidden="true"><path d="M18 2.5 34 31H2Z" fill="#F5222D" stroke="#FF7777" stroke-width="1.5" stroke-linejoin="round"/><g fill="none" stroke="#FFFFFF" stroke-width="1.8" stroke-linecap="round"><path d="M12 15h10q2 0 2-1.5t-2-1.5h-2M11 18.5h13q2 0 2-1.5t-2-1.5M13 22h9q2 0 2-1.5t-2-1.5"/></g></svg></span>`}
function coldWarningMarkup(){return `<span class="cold-warning" role="img" aria-label="Προειδοποίηση πολύ χαμηλής θερμοκρασίας"><svg viewBox="0 0 36 36" xmlns="http://www.w3.org/2000/svg" aria-hidden="true"><path d="M18 2.5 34 31H2Z" fill="#1677FF" stroke="#79B8FF" stroke-width="1.5" stroke-linejoin="round"/><g fill="none" stroke="#FFFFFF" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M18 11v12M12.8 14l10.4 6M23.2 14l-10.4 6M18 11l-2-2m2 2 2-2M18 23l-2 2m2-2 2 2M12.8 14l.2-2.5m-.2 2.5 2.5-.2M23.2 14l-.2-2.5m.2 2.5-2.5-.2M12.8 20l.2 2.5m-.2-2.5 2.5.2M23.2 20l-.2 2.5m.2-2.5-2.5.2"/></g></svg></span>`}
function weatherIconWithWarning(icon,wind,className,temp){const windy=Number(wind)>=32,celsius=Number(temp),cold=Number.isFinite(celsius)&&celsius<=3;return `<span class="weather-icon-wrap${windy&&cold?" has-two-warnings":""}">${icon}${windy?windWarningMarkup(className||"day-warning"):""}${cold?coldWarningMarkup():""}</span>`}
function hourlyPrecipSymbols(code,snow,rain,temp){code=Number(code);snow=Number(snow)||0;rain=normalizePrecipProbability(rain);temp=Number(temp);if(rain<31||!precipCodes.includes(code))return "";let out="";const snowCodesForSymbol=[71,73,75,77,85,86];if((temp<=1)||(temp<=4&&(snow>0||snowCodesForSymbol.includes(code)))){out='<span aria-label="Χιόνι" title="Χιόνι">❄️</span>'}else{out='<span aria-label="Βροχή" title="Βροχή">💧</span>'}return `<span class="hour-precip-symbols">${out}</span>`}
function normalizePrecipProbability(value){const p=Math.round(Number(value)||0);if(p>=25&&p<=28)return 24;if(p>=29&&p<=30)return 31;return p}
function weatherText(code){code=Number(code);if(code===0)return "Αίθριος";if(code===1)return "Κυρίως αίθριος";if(code===2)return "Λίγες νεφώσεις";if(code===3)return "Συννεφιά";if([45,48].includes(code))return "Ομίχλη";if([51,53,55].includes(code))return "Ψιλόβροχο";if(sleetCodes.includes(code))return "Χιονόνερο";if([61,63,65].includes(code))return "Βροχή";if([71,73,75,77].includes(code))return "Χιόνι";if([80,81,82].includes(code))return "Μπόρες";if([85,86].includes(code))return "Χιονομπόρες";if(stormCodes.includes(code))return "Καταιγίδα";return "Μεταβλητός καιρός"}
function windDirection(degrees){if(degrees==null||isNaN(degrees))return "—";const a=["Β","ΒΒΑ","ΒΑ","ΑΒΑ","Α","ΑΝΑ","ΝΑ","ΝΝΑ","Ν","ΝΝΔ","ΝΔ","ΔΝΔ","Δ","ΔΒΔ","ΒΔ","ΒΒΔ"];return a[Math.round(degrees/22.5)%16]}
async function searchCity(){
 const city=document.getElementById("cityInput").value.trim();if(!city)return;closeHistory();closeHourly();closeExtra();
 document.getElementById("current").innerHTML="";document.getElementById("forecast").innerHTML='<div class="loading">Αναζήτηση πόλης...</div>';
 try{const r=await fetch(`${OPEN_METEO_GEOCODING}?name=${encodeURIComponent(city)}&count=1&language=el&format=json`);if(!r.ok)throw Error("Δεν ήταν δυνατή η αναζήτηση.");const geo=await r.json();if(!geo.results?.length)throw Error("Δεν βρέθηκε η πόλη.");const p=geo.results[0];locationData={name:p.name||city,latitude:p.latitude,longitude:p.longitude,country:p.country||"",countryCode:p.country_code||""};await loadWeather()}
 catch(e){document.getElementById("current").innerHTML="";document.getElementById("forecast").innerHTML=`<div class="loading">Σφάλμα φόρτωσης δεδομένων.<br><br>${e.message||""}</div>`}
}
const FUSION_MODELS=[
 {id:"ecmwf_ifs",weight:0.40,name:"ECMWF IFS"},
 {id:"ncep_gfs_seamless",weight:0.25,name:"NOAA GFS"},
 {id:"icon_seamless",weight:0.20,name:"DWD ICON"},
 {id:"meteofrance_seamless",weight:0.15,name:"Météo-France"}
];
function finiteValues(entries){return entries.filter(x=>x.value!==null&&x.value!==undefined&&Number.isFinite(Number(x.value)))}
function weightedMean(entries){const good=finiteValues(entries);if(!good.length)return null;const total=good.reduce((s,x)=>s+x.weight,0);return total?good.reduce((s,x)=>s+Number(x.value)*x.weight,0)/total:null}
function weightedWeatherCode(entries){const good=finiteValues(entries);if(!good.length)return null;const tally={};for(const x of good){const k=String(Math.round(Number(x.value)));tally[k]=(tally[k]||0)+x.weight}return Number(Object.keys(tally).sort((a,b)=>tally[b]-tally[a])[0])}
function weightedDirection(entries){const good=finiteValues(entries);if(!good.length)return null;let x=0,y=0;for(const e of good){const rad=Number(e.value)*Math.PI/180;x+=Math.cos(rad)*e.weight;y+=Math.sin(rad)*e.weight}return (Math.atan2(y,x)*180/Math.PI+360)%360}
function blendObject(models,section,fields){
 const first=models.find(m=>m.data[section]?.time?.length)?.data[section];if(!first)return null;
 const result={time:first.time.slice()};
 for(const field of fields){if(field==='time')continue;const maxLength=Math.max(...models.map(m=>m.data[section]?.[field]?.length||0));if(!maxLength)continue;result[field]=[];
  for(let i=0;i<maxLength;i++){const entries=models.map(m=>({value:m.data[section]?.[field]?.[i],weight:m.weight}));result[field].push(field==='weather_code'?weightedWeatherCode(entries):field==='wind_direction_10m'?weightedDirection(entries):weightedMean(entries))}
 }
 return result;
}
function blendForecasts(models){
 const currentFields=["temperature_2m","relative_humidity_2m","apparent_temperature","weather_code","wind_speed_10m","wind_direction_10m","is_day","cloud_cover"];
 const hourlyFields=["temperature_2m","apparent_temperature","precipitation_probability","snowfall","weather_code","cloud_cover","wind_speed_10m","wind_direction_10m","is_day"];
 const dailyFields=["weather_code","temperature_2m_max","temperature_2m_min","precipitation_probability_max","snowfall_sum","wind_speed_10m_max","cloud_cover_mean"];
 const first=models[0].data;const current={};for(const field of currentFields){const entries=models.map(m=>({value:m.data.current?.[field],weight:m.weight}));current[field]=field==='weather_code'||field==='is_day'?weightedWeatherCode(entries):field==='wind_direction_10m'?weightedDirection(entries):weightedMean(entries)}
 const hourly=blendObject(models,"hourly",hourlyFields),daily=blendObject(models,"daily",dailyFields);
 if(!hourly||!daily)throw Error("Δεν επέστρεψαν όλα τα μοντέλα επαρκή δεδομένα.");
 return {...first,current,hourly,daily,customModel:"AegeanBlend WX-1",modelsUsed:models.map(m=>m.name)};
}
async function loadWeather(){
 if(!locationData)return;document.getElementById("current").innerHTML='<div class="current"><div class="loading">Φόρτωση AegeanBlend WX-1...</div></div>';document.getElementById("forecast").innerHTML='<div class="loading">Συνδυασμός μοντέλων πρόγνωσης...</div>';
 try{
  const base={latitude:locationData.latitude,longitude:locationData.longitude,current:"temperature_2m,relative_humidity_2m,apparent_temperature,weather_code,wind_speed_10m,wind_direction_10m,is_day,cloud_cover",hourly:"temperature_2m,apparent_temperature,precipitation_probability,snowfall,weather_code,cloud_cover,wind_speed_10m,wind_direction_10m,is_day",daily:"weather_code,temperature_2m_max,temperature_2m_min,precipitation_probability_max,snowfall_sum,wind_speed_10m_max,cloud_cover_mean",forecast_days:"15",temperature_unit:"celsius",wind_speed_unit:"kmh",precipitation_unit:"mm",timezone:"auto"};
  const results=await Promise.all(FUSION_MODELS.map(async model=>{try{const q=new URLSearchParams({...base,models:model.id});const r=await fetch(`${OPEN_METEO_FORECAST}?${q}`);if(!r.ok)throw Error(model.id);const data=await r.json();if(!data.current||!data.daily?.time?.length||!data.hourly?.time?.length)throw Error(model.id);return {...model,data}}catch(e){return null}}));
  const available=results.filter(Boolean);
  if(available.length>=2){const total=available.reduce((sum,m)=>sum+m.weight,0);weatherData=blendForecasts(available.map(m=>({...m,weight:m.weight/total})));}
  else {const q=new URLSearchParams({...base,models:"best_match"});const r=await fetch(`${OPEN_METEO_FORECAST}?${q}`);if(!r.ok)throw Error("Δεν ήταν δυνατή η λήψη πρόγνωσης.");weatherData=await r.json();weatherData.customModel="AegeanBlend WX-1 (εφεδρική πηγή)";weatherData.modelsUsed=["Open-Meteo Best Match"]}
  renderCurrent();renderForecast();
 }catch(e){document.getElementById("current").innerHTML="";document.getElementById("forecast").innerHTML=`<div class="loading">Δεν ήταν δυνατή η φόρτωση των δεδομένων καιρού.<br><br>${e.message||""}</div>`}
}
function renderCurrent(){const d=weatherData.current,wind=Number(d.wind_speed_10m)||0,code=Number(d.weather_code),day=Number(d.is_day)===1,cloud=Number(d.cloud_cover)||0;const currentIcon=weatherIconWithWarning(weatherIcon(code,day,precipCodes.includes(code)?31:0,0,wind,cloud,Number(d.temperature_2m)),wind,"day-warning",Number(d.temperature_2m));document.getElementById("current").innerHTML=`<div class="current"><h2>${locationData.name}<div style="font-size:16px;font-weight:normal;color:#dce5ee;margin-top:7px">${countryFlag(locationData.countryCode)} ${locationData.country}</div></h2><div class="temperature">${Math.round(d.temperature_2m)}°C</div><div class="condition">${currentIcon} ${weatherText(code)}</div><div class="current-grid"><div class="current-box"><span>💧 Υγρασία</span><strong>${Math.round(d.relative_humidity_2m)}%</strong></div><div class="current-box"><span>Άνεμος</span><strong>${Math.round(wind)} km/h — ${windDirection(d.wind_direction_10m)}</strong></div><div class="current-box"><span>🌡️ Αίσθηση</span><strong>${Math.round(d.apparent_temperature)}°C</strong></div></div></div>`}
function getDailyDaylightWeatherCode(dayIndex){
 const daily=weatherData.daily,hourly=weatherData.hourly,date=daily.time[dayIndex],rows=[];
 // Ελέγχουμε και τις 24 ώρες της συγκεκριμένης ημερομηνίας, όχι μόνο το φως της ημέρας.
 for(let i=0;i<hourly.time.length;i++)if(hourly.time[i].slice(0,10)===date)rows.push(i);
 if(!rows.length)return Number(daily.weather_code[dayIndex]);
 const qualifying=rows.filter(i=>precipCodes.includes(Number(hourly.weather_code[i]))&&normalizePrecipProbability(hourly.precipitation_probability?.[i])>=31);
 if(qualifying.length){
  // Επιλέγουμε το είδος υετού από τις ώρες που περνούν το όριο 31%.
  const counts={};for(const i of qualifying){const c=Number(hourly.weather_code[i]);counts[c]=(counts[c]||0)+1}
  return Number(Object.keys(counts).sort((a,b)=>counts[b]-counts[a])[0]);
 }
 // Χωρίς qualifying υετό, επιλέγουμε τον συχνότερο μη υετικό κωδικό όλης της ημέρας.
 const dry=rows.filter(i=>!precipCodes.includes(Number(hourly.weather_code[i]))),use=dry.length?dry:rows,counts={};
 for(const i of use){const c=Number(hourly.weather_code[i]);counts[c]=(counts[c]||0)+1}
 return Number(Object.keys(counts).sort((a,b)=>counts[b]-counts[a])[0]);
}
function getDailyQualifyingPrecipProbability(dayIndex,code){
 const h=weatherData.hourly,date=weatherData.daily.time[dayIndex];let max=0;
 for(let i=0;i<h.time.length;i++){if(h.time[i].slice(0,10)!==date)continue;const c=Number(h.weather_code[i]),p=normalizePrecipProbability(h.precipitation_probability?.[i]);if(precipCodes.includes(c)&&p>=31){if(!code||c===Number(code))max=Math.max(max,p)}}
 return max;
}
function getDailyHourlyTemperatureRange(dayIndex){
 const d=weatherData.daily,h=weatherData.hourly,date=d.time[dayIndex];let values=[];
 for(let i=0;i<h.time.length;i++)if(h.time[i].slice(0,10)===date&&Number.isFinite(Number(h.temperature_2m[i])))values.push(Number(h.temperature_2m[i]));
 if(!values.length)return {min:Number(d.temperature_2m_min[dayIndex]),max:Number(d.temperature_2m_max[dayIndex])};
 return {min:Math.min(...values),max:Math.max(...values)};
}
function renderForecast(){
 const d=weatherData.daily;let html="";
 for(let i=0;i<d.time.length;i++){
  const date=formatDate(d.time[i]),rain=normalizePrecipProbability(d.precipitation_probability_max[i]),snow=Number(d.snowfall_sum[i])||0,wind=Number(d.wind_speed_10m_max[i])||0,cloud=Number(d.cloud_cover_mean[i])||0,temps=getDailyHourlyTemperatureRange(i),minTemp=temps.min,maxTemp=temps.max;
  const dailyCode=getDailyDaylightWeatherCode(i),qualifyingProb=getDailyQualifyingPrecipProbability(i,dailyCode);
  // Πάνω από 30% αρκεί η ίδια η πιθανότητα: το εικονίδιο υετού εμφανίζεται πάντα, ακόμη κι αν ο κωδικός καιρού δεν δηλώνει υετό.
  const iconProb=Math.max(rain,qualifyingProb)>=31?Math.max(rain,qualifyingProb):0;
  const dailyIcon=weatherIconWithWarning(weatherIcon(dailyCode,true,iconProb,snow,wind,cloud,(minTemp+maxTemp)/2),wind,"day-warning",minTemp);
  const precipIcon=rain>=31?`${weatherIcon(dailyCode,true,rain,snow,0,cloud,(minTemp+maxTemp)/2)}`:"";
  const precipitationInfo=`${precipIcon}${precipIcon?" ":""}${rain}%`;
  html+=`<div class="day" onclick="showHourly(${i})"><div class="day-name">${date.day}</div><div class="date">${date.date}</div><div class="icon">${dailyIcon}</div><div class="max">${Math.round(maxTemp)}°</div><div class="min">${Math.round(minTemp)}°</div><div class="rain">${precipitationInfo}</div></div>`;
 }
 document.getElementById("forecast").innerHTML=html;
}
function showHourly(dayIndex){
 const d=weatherData.hourly,date=weatherData.daily.time[dayIndex],rows=[];
 for(let i=0;i<d.time.length;i++)if(d.time[i].slice(0,10)===date)rows.push(i);
 const f=formatDate(date);document.getElementById("hourlyTitle").innerText=`Πρόγνωση ανά ώρα — ${f.day} ${f.date}`;let html="";
 rows.forEach(i=>{
  const hour=d.time[i].slice(11,16),temp=Math.round(d.temperature_2m[i]),feels=Math.round(d.apparent_temperature[i]),rain=normalizePrecipProbability(d.precipitation_probability[i]),snow=Number(d.snowfall[i])||0,wind=Math.round(Number(d.wind_speed_10m[i])||0),dir=windDirection(d.wind_direction_10m[i]),cloud=Math.round(Number(d.cloud_cover[i])||0),code=Number(d.weather_code[i]),day=Number(d.is_day[i])===1;
  const icon=weatherIconWithWarning(weatherIcon(code,day,rain,snow,wind,cloud,Number(d.temperature_2m[i])),wind,"hour-warning",Number(d.temperature_2m[i]));const phtml=`${hourlyPrecipSymbols(code,snow,rain,Number(d.temperature_2m[i]))}${rain}%`;
  html+=`<div class="hour"><div class="hour-time">${hour}</div><div class="hour-icon">${icon}</div><div class="hour-data">🌡️ <b>${temp}°</b><br>Αίσθηση ${feels}°</div><div class="hour-data">${phtml}</div><div class="hour-data">☁️ ${cloud}%</div><div class="hour-data">Άνεμος ${wind} km/h<br>Διεύθυνση: <b>${dir}</b></div></div>`;
 });
 document.getElementById("hourly").innerHTML=html||'<div class="loading">Δεν υπάρχουν διαθέσιμα ωριαία δεδομένα.</div>';const s=document.getElementById("hourlySection");s.style.display="block";s.scrollIntoView({behavior:"smooth",block:"start"});
}
function openHistorySelector(){closeMenu();closeHourly();closeExtra();if(!locationData){alert("Πρώτα αναζήτησε μία τοποθεσία.");return}const s=document.getElementById("historySection");s.style.display="block";renderHistoryRangeSelector();s.scrollIntoView({behavior:"smooth",block:"start"})}
function renderHistoryRangeSelector(){let h='<div class="history-navigation"><button class="history-back-button" onclick="closeHistory()">✕ Κλείσιμο</button></div><div class="history-range-title">Επίλεξε πόσα τελευταία έτη θέλεις να εμφανιστούν</div><div class="history-ranges">';for(let y=1;y<=10;y++)h+=`<button class="history-range-button" onclick="loadHistory(${y})">${y} ${y===1?"έτος":"έτη"}</button>`;h+='</div>';document.getElementById("history").innerHTML=h;document.getElementById("historyTitle").innerText=`📜 Ιστορικό καιρού — ${locationData.name}`}
function loadHistory(years){if(!locationData)return;historyYears=years;let h='<div class="history-navigation"><button class="history-back-button" onclick="renderHistoryRangeSelector()">← 1–10 έτη</button></div><div class="history-years">';const currentYear=new Date().getFullYear();for(let i=0;i<years;i++)h+=`<button class="history-year-button" onclick="loadHistoryMonths(${currentYear-i})">📅 ${currentYear-i}</button>`;h+='</div>';document.getElementById("history").innerHTML=h;document.getElementById("historyTitle").innerText=`📜 Ιστορικό καιρού — ${locationData.name} — επίλεξε έτος`}
function loadHistoryMonths(year){const months=["Ιανουάριος","Φεβρουάριος","Μάρτιος","Απρίλιος","Μάιος","Ιούνιος","Ιούλιος","Αύγουστος","Σεπτέμβριος","Οκτώβριος","Νοέμβριος","Δεκέμβριος"];let h=`<div class="history-navigation"><button class="history-back-button" onclick="renderHistoryYears(historyYears)">← Έτη</button></div><div class="history-months">`;for(let m=1;m<=12;m++)h+=`<button class="history-month-button" onclick="loadHistoryMonth(${year},${m})">📅 ${months[m-1]}</button>`;h+='</div>';document.getElementById("history").innerHTML=h;document.getElementById("historyTitle").innerText=`📜 Ιστορικό καιρού — ${locationData.name} — ${year}`}
function renderHistoryYears(years){loadHistory(years)}
async function loadHistoryMonth(year,month){
 if(!locationData)return;const history=document.getElementById("history");history.innerHTML=`<div class="loading">Φόρτωση ιστορικού ${month}/${year}...</div>`;
 const names=["Ιανουάριος","Φεβρουάριος","Μάρτιος","Απρίλιος","Μάιος","Ιούνιος","Ιούλιος","Αύγουστος","Σεπτέμβριος","Οκτώβριος","Νοέμβριος","Δεκέμβριος"];
 try{
  const start=`${year}-${String(month).padStart(2,"0")}-01`,last=new Date(Date.UTC(year,month,0)).getUTCDate(),end=`${year}-${String(month).padStart(2,"0")}-${String(last).padStart(2,"0")}`;
  const q=new URLSearchParams({latitude:locationData.latitude,longitude:locationData.longitude,start_date:start,end_date:end,daily:"weather_code,temperature_2m_max,temperature_2m_min",models:"era5",timezone:"auto"});
  const r=await fetch(`https://archive-api.open-meteo.com/v1/archive?${q}`);if(!r.ok)throw Error("History request failed");const data=await r.json();if(!data.daily?.time?.length)throw Error("No history data");renderHistoryMonth(data,year,month,names[month-1]);
 }catch(e){history.innerHTML=`<div class="loading">Δεν ήταν δυνατή η φόρτωση του ιστορικού.<br><br><button class="history-back-button" onclick="loadHistoryMonths(${year})">← Επιστροφή στους μήνες</button></div>`}
}
function renderHistoryMonth(data,year,month,monthName){const d=data.daily;let h=`<div class="history-navigation"><button class="history-back-button" onclick="loadHistoryMonths(${year})">← ${year}</button></div><div class="history-days">`;for(let i=0;i<d.time.length;i++){const [y,m,day]=d.time[i].split("-").map(Number),date=`${day}/${m}/${y}`,max=Math.round(Number(d.temperature_2m_max[i])),min=Math.round(Number(d.temperature_2m_min[i]));h+=`<div class="history-day" title="${date}"><div class="history-date">${date}</div><div class="history-day-content"><div class="history-thermometer" aria-label="Θερμοκρασία"><div class="history-thermometer-fill"></div><div class="history-thermometer-bulb"></div></div><div class="history-temperature"><div class="day-temp">${max}°</div><div class="night-temp">${min}°</div></div></div></div>`}h+='</div>';document.getElementById("history").innerHTML=h;document.getElementById("historyTitle").innerText=`📜 Ιστορικό καιρού — ${locationData.name} — ${monthName} ${year}`}
async function openExtra(type){
 closeMenu();closeHourly();closeHistory();if(!locationData){alert("Πρώτα αναζήτησε μία τοποθεσία.");return}
 const section=document.getElementById("extraSection"),content=document.getElementById("extraContent"),title=document.getElementById("extraTitle"),requestId=++extraRequestId;
 section.style.display="block";content.innerHTML='<div class="loading">Φόρτωση δεδομένων...</div>';title.innerText="📆 Μακροπρόθεσμη πρόγνωση — 46 ημέρες";section.scrollIntoView({behavior:"smooth",block:"start"});
 try{
  const forecastURL="https://seasonal-api.open-meteo.com/v1/seasonal";
  const q=new URLSearchParams({latitude:locationData.latitude,longitude:locationData.longitude,daily:"temperature_2m_max",temperature_unit:"celsius",timezone:"auto",models:"ecmwf_ec46",forecast_days:"46"});
  const r=await fetch(`${forecastURL}?${q}`);if(!r.ok)throw Error("Το συγκεκριμένο μοντέλο δεν επέστρεψε διαθέσιμα δεδομένα.");const data=await r.json();if(requestId!==extraRequestId)return;
  if(!data.daily?.time?.length||!data.daily?.temperature_2m_max?.length)throw Error("Δεν υπάρχουν διαθέσιμα δεδομένα θερμοκρασίας για αυτή την τοποθεσία/περίοδο.");
  renderLongRange(data);
 }catch(e){if(requestId!==extraRequestId)return;content.innerHTML=`<div class="loading">Δεν ήταν δυνατή η φόρτωση της τάσης.<br><br>${e.message||"Δοκίμασε ξανά αργότερα."}<br><br>Το EC46 ενδέχεται να μην παρέχει δεδομένα για κάθε ημερομηνία ή τοποθεσία.</div>`}
}
function renderLongRange(data){
 const d=data.daily;let h='<div class="history-range-title">Μέση μέγιστη θερμοκρασία ανά εβδομάδα (°C)</div>';
 for(let start=0;start<d.time.length;start+=7){const end=Math.min(start+7,d.time.length),vals=d.temperature_2m_max.slice(start,end).filter(v=>v!==null&&Number.isFinite(Number(v))).map(Number);if(!vals.length)continue;const avg=vals.reduce((a,b)=>a+b,0)/vals.length;const a=formatDate(d.time[start],true).date,b=formatDate(d.time[end-1],true).date;h+=`<div class="period-card"><div><strong>${a} – ${b}</strong><br><span>${vals.length} ημέρες</span></div><strong>${avg.toFixed(1)}°C</strong></div>`}
 document.getElementById("extraContent").innerHTML=h;
}
document.addEventListener("click",e=>{const menu=document.getElementById("menu"),button=document.querySelector(".menu-button");if(menu.classList.contains("open")&&!menu.contains(e.target)&&!button.contains(e.target))menu.classList.remove("open")});
document.getElementById("cityInput").addEventListener("keydown",e=>{if(e.key==="Enter")searchCity()});
searchCity();
</script>
</body>
</html>
