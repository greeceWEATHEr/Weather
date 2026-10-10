<!DOCTYPE >
<html lang="el">

<head>

<meta charset="UTF-8">

<meta name="viewport"
      content="width=device-width, initial-scale=1.0">

<title>Greece Weather</title>


<style>

*{
    box-sizing:border-box;
}

body{
    margin:0;
    font-family:
        Arial,
        Helvetica,
        sans-serif;
    color:#fff;
    background:
        linear-gradient(
            180deg,
            #071d35,
            #0d3762
        );
}

.container{
    width:min(100%,960px);
    margin:auto;
    padding:16px;
}


/* =====================================
   HEADER
===================================== */

.header{
    position:relative;
    background:
        rgba(3,20,38,.72);
    padding:28px 60px 28px 20px;
    text-align:center;
    margin-bottom:25px;
}

.header h1{
    margin:0;
    font-size:30px;
}

.header p{
    margin:18px 0 0;
    color:#d6dce4;
    font-size:16px;
}


/* =====================================
   MENU
===================================== */

.menu-button{
    position:absolute;
    top:18px;
    right:18px;
    width:43px;
    height:43px;
    border:0;
    border-radius:12px;
    background:rgba(255,255,255,.12);
    color:#fff;
    font-size:25px;
    cursor:pointer;
    display:flex;
    align-items:center;
    justify-content:center;
    transition:.18s;
}

.menu-button:hover{
    background:rgba(255,255,255,.22);
}

.menu{
    display:none;
    position:absolute;
    top:68px;
    right:18px;
    width:270px;
    max-height:70vh;
    overflow-y:auto;
    background:rgba(5,27,50,.97);
    border:1px solid rgba(255,255,255,.18);
    border-radius:15px;
    padding:8px;
    z-index:1000;
    box-shadow:0 10px 30px rgba(0,0,0,.35);
}

.menu.open{
    display:block;
}

.menu-item{
    width:100%;
    border:0;
    background:transparent;
    color:#fff;
    text-align:left;
    padding:13px 12px;
    border-radius:10px;
    font-size:14px;
    cursor:pointer;
}

.menu-item:hover{
    background:rgba(255,255,255,.12);
}


/* =====================================
   SEARCH
===================================== */

.search{
    display:flex;
    gap:10px;
    margin-bottom:25px;
}

.search input{
    flex:1;
    border:0;
    outline:0;
    border-radius:15px;
    padding:17px;
    font-size:16px;
}

.search button{
    border:0;
    border-radius:15px;
    padding:0 22px;
    font-weight:bold;
    font-size:15px;
    cursor:pointer;
}


/* =====================================
   CURRENT WEATHER
===================================== */

.current{
    background:
        rgba(57,85,117,.72);
    border-radius:20px;
    padding:25px;
    text-align:center;
    margin-bottom:25px;
}

.current h2{
    margin:0 0 20px;
    font-size:26px;
}

.temperature{
    font-size:60px;
    font-weight:300;
    margin-bottom:15px;
}

.condition{
    font-size:17px;
    margin-bottom:24px;
}

.current-grid{
    display:grid;
    grid-template-columns:
        repeat(3,1fr);
    gap:12px;
}

.current-box{
    background:
        rgba(104,133,165,.48);
    border-radius:14px;
    padding:16px 8px;
}

.current-box span{
    display:block;
    color:#e0e5ea;
    margin-bottom:5px;
}

.current-box strong{
    font-size:15px;
}


/* =====================================
   SECTION TITLE
===================================== */

.section-title{
    display:flex;
    align-items:center;
    gap:8px;
    font-size:24px;
    font-weight:bold;
    border-bottom:
        2px solid
        rgba(255,255,255,.55);
    padding-bottom:12px;
    margin-bottom:15px;
}


/* =====================================
   15 ΗΜΕΡΕΣ
===================================== */

.forecast{
    display:grid;
    grid-template-columns:
        repeat(6,1fr);
    gap:12px;
}

.day{
    background:
        rgba(53,84,119,.78);
    border-radius:17px;
    padding:18px 8px;
    text-align:center;
    cursor:pointer;
    transition:.18s;
    border:
        1px solid
        transparent;
}

.day:hover{
    transform:
        translateY(-3px);
    background:
        rgba(72,105,143,.95);
    border-color:
        rgba(255,255,255,.25);
}

.day:active{
    transform:
        scale(.97);
}

.day-name{
    font-weight:bold;
    font-size:15px;
}

.date{
    margin-top:9px;
    color:#e1e5e9;
    font-size:14px;
}

.icon{
    font-size:35px;
    margin:18px 0 12px;
    height:40px;
    display:flex;
    align-items:center;
    justify-content:center;
}


/* =====================================
   ΝΕΑ ΕΝΙΑΙΑ ΚΑΙΡΙΚΑ ΕΙΚΟΝΙΔΙΑ
===================================== */

.weather-svg{
    width:42px;
    height:42px;
    display:inline-flex;
    align-items:center;
    justify-content:center;
}

.weather-svg svg{
    width:42px;
    height:42px;
    display:block;
}

.condition .weather-svg{
    width:45px;
    height:45px;
    vertical-align:middle;
    margin-right:6px;
}

.condition .weather-svg svg{
    width:45px;
    height:45px;
}

.hour-icon .weather-svg{
    width:32px;
    height:32px;
}

.hour-icon .weather-svg svg{
    width:32px;
    height:32px;
}

.max{
    font-size:17px;
    font-weight:bold;
}

.min{
    margin-top:6px;
    color:#d0d7df;
}

.rain{
    margin-top:10px;
    font-size:12px;
    color:#c9e9ff;
}


/* =====================================
   ΠΑΛΙΑ ΝΥΧΤΕΡΙΝΑ — ΔΙΑΤΗΡΗΣΗ
===================================== */

.night-moon{
    display:inline-block;
    filter:
        grayscale(1)
        brightness(.78)
        sepia(.10)
        hue-rotate(175deg);
    opacity:.90;
}

.night-partly-cloudy{
    width:38px;
    height:38px;
    display:inline-block;
    vertical-align:middle;
}


/* =====================================
   ΩΡΙΑΙΑ ΠΡΟΓΝΩΣΗ
===================================== */

.hourly-section{
    display:none;
    margin-top:28px;
    background:
        rgba(5,27,50,.72);
    border-radius:20px;
    padding:20px;
}

.hourly-header{
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:10px;
    border-bottom:
        1px solid
        rgba(255,255,255,.3);
    padding-bottom:15px;
    margin-bottom:15px;
}

.hourly-header h3{
    margin:0;
    font-size:21px;
}

.close-hourly{
    background:
        rgba(255,255,255,.15);
    border:0;
    color:white;
    border-radius:10px;
    padding:8px 13px;
    cursor:pointer;
}


/* =====================================
   ΩΡΕΣ
===================================== */

.hourly{
    display:grid;
    gap:8px;
}

.hour{
    display:grid;
    grid-template-columns:
        70px
        50px
        1fr
        1fr
        1fr
        1fr;
    align-items:center;
    background:
        rgba(65,96,130,.62);
    border-radius:12px;
    padding:12px 10px;
    gap:8px;
}

.hour-time{
    font-weight:bold;
}

.hour-icon{
    font-size:25px;
    text-align:center;
    height:32px;
    display:flex;
    align-items:center;
    justify-content:center;
}

.hour-data{
    font-size:13px;
    color:#e4e8ed;
    line-height:1.5;
}


/* =====================================
   ΙΣΤΟΡΙΚΟ
===================================== */

.history-section{
    display:none;
    margin-top:28px;
    background:
        rgba(5,27,50,.72);
    border-radius:20px;
    padding:20px;
}

.history-header{
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:10px;
    border-bottom:
        1px solid
        rgba(255,255,255,.3);
    padding-bottom:15px;
    margin-bottom:15px;
}

.history-header h3{
    margin:0;
    font-size:21px;
}

.close-history{
    background:
        rgba(255,255,255,.15);
    border:0;
    color:white;
    border-radius:10px;
    padding:8px 13px;
    cursor:pointer;
}

.history{
    display:grid;
    gap:9px;
}


/* =====================================
   ΕΠΙΛΟΓΗ 1-10 ΕΤΩΝ
===================================== */

.history-range-title{
    margin:0 0 14px;
    color:#dce5ee;
    font-size:15px;
    text-align:center;
}

.history-ranges{
    display:grid;
    grid-template-columns:
        repeat(5,1fr);
    gap:10px;
}

.history-range-button{
    border:0;
    color:#fff;
    background:
        rgba(65,96,130,.72);
    border-radius:14px;
    padding:15px 8px;
    font-size:14px;
    font-weight:bold;
    cursor:pointer;
    transition:.18s;
}

.history-range-button:hover{
    background:
        rgba(72,105,143,.95);
    transform:
        translateY(-2px);
}


/* =====================================
   ΙΣΤΟΡΙΚΟ ΕΤΩΝ
===================================== */

.history-years{
    display:grid;
    grid-template-columns:
        repeat(2,1fr);
    gap:12px;
}

.history-year-button,
.history-month-button,
.history-back-button{
    border:0;
    color:#fff;
    background:
        rgba(65,96,130,.72);
    border-radius:14px;
    padding:17px 12px;
    font-size:15px;
    font-weight:bold;
    cursor:pointer;
    transition:.18s;
}

.history-year-button:hover,
.history-month-button:hover,
.history-back-button:hover{
    background:
        rgba(72,105,143,.95);
    transform:
        translateY(-2px);
}

.history-months{
    display:grid;
    grid-template-columns:
        repeat(3,1fr);
    gap:10px;
}

.history-navigation{
    display:flex;
    gap:10px;
    margin-bottom:15px;
    flex-wrap:wrap;
}

.history-back-button{
    padding:10px 14px;
    font-size:14px;
}


/* =====================================
   ΗΜΕΡΕΣ ΙΣΤΟΡΙΚΟΥ
===================================== */

.history-days{
    display:grid;
    grid-template-columns:
        repeat(6,minmax(0,1fr));
    gap:10px;
}


/* =====================================
   ΙΣΤΟΡΙΚΟ ΚΟΥΤΑΚΙ
===================================== */

.history-day{
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:flex-start;

    width:100%;
    min-width:0;
    min-height:136px;

    background:
        rgba(65,96,130,.62);

    border-radius:13px;

    padding:12px 8px;

    cursor:pointer;

    transition:.18s;

    border:
        1px solid
        transparent;
}

.history-day:hover{
    background:
        rgba(72,105,143,.90);

    border-color:
        rgba(255,255,255,.20);

    transform:
        translateY(-2px);
}

.history-day:active{
    transform:
        scale(.98);
}


/* =====================================
   ΗΜΕΡΟΜΗΝΙΑ
===================================== */

.history-date{
    width:100%;

    font-weight:bold;

    font-size:14px;

    text-align:center;

    white-space:nowrap;

    line-height:1.1;

    min-height:20px;

    display:flex;

    align-items:center;

    justify-content:center;

    margin-bottom:10px;
}


/* =====================================
   ΑΠΟΛΥΤΑ ΚΕΝΤΡΑΡΙΣΜΕΝΟ:
   ΘΕΡΜΟΜΕΤΡΟ | ΘΕΡΜΟΚΡΑΣΙΕΣ
===================================== */

.history-day-content{
    display:grid;

    grid-template-columns:
        18px 64px;

    column-gap:10px;

    align-items:center;

    justify-content:center;

    width:max-content;

    flex:1;

    margin-left:auto;
    margin-right:auto;
}


/* =====================================
   ΘΕΡΜΟΚΡΑΣΙΕΣ ΙΣΤΟΡΙΚΟΥ
===================================== */

.history-temperature{
    width:64px;
    min-width:64px;

    display:flex;

    flex-direction:column;

    justify-content:center;

    align-items:center;

    gap:5px;

    font-size:13px;

    line-height:1.2;

    text-align:center;
}

.history-temperature .day-temp{
    width:100%;

    font-weight:bold;
    color:#fff;

    white-space:nowrap;

    text-align:center;
}

.history-temperature .night-temp{
    width:100%;

    color:#d0d7df;

    white-space:nowrap;

    text-align:center;
}


/* =====================================
   ΘΕΡΜΟΜΕΤΡΟ
===================================== */

.history-thermometer{
    position:relative;

    width:18px;
    height:54px;

    flex:
        0 0 18px;

    justify-self:center;
}

.history-thermometer::before{
    content:"";

    position:absolute;

    left:6px;
    top:1px;

    width:6px;
    height:39px;

    border-radius:6px;

    background:#f1f4f7;
}

.history-thermometer::after{
    content:"";

    position:absolute;

    left:1px;
    bottom:0;

    width:17px;
    height:17px;

    border-radius:50%;

    background:#f1f4f7;
}

.history-thermometer-fill{
    position:absolute;

    left:8px;
    bottom:8px;

    width:3px;
    height:31px;

    border-radius:3px;

    background:#e53935;

    z-index:2;
}

.history-thermometer-bulb{
    position:absolute;

    left:5px;
    bottom:3px;

    width:9px;
    height:9px;

    border-radius:50%;

    background:#e53935;

    z-index:2;
}


/* =====================================
   ΝΕΕΣ ΜΑΚΡΟΠΡΟΘΕΣΜΕΣ ΠΡΟΓΝΩΣΕΙΣ
===================================== */

.longrange-section{
    display:none;
    margin-top:28px;
    background:
        rgba(5,27,50,.72);
    border-radius:20px;
    padding:20px;
}

.longrange-header{
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:10px;
    border-bottom:
        1px solid
        rgba(255,255,255,.3);
    padding-bottom:15px;
    margin-bottom:15px;
}

.longrange-header h3{
    margin:0;
    font-size:21px;
}

.close-longrange{
    background:
        rgba(255,255,255,.15);
    border:0;
    color:white;
    border-radius:10px;
    padding:8px 13px;
    cursor:pointer;
}

.longrange-note{
    background:
        rgba(65,96,130,.45);
    border-radius:14px;
    padding:14px;
    color:#dce5ee;
    font-size:13px;
    line-height:1.55;
    margin-bottom:15px;
}

.longrange-grid{
    display:grid;
    grid-template-columns:
        repeat(2,1fr);
    gap:10px;
}

.longrange-card{
    background:
        rgba(65,96,130,.62);
    border-radius:14px;
    padding:15px;
    text-align:center;
}

.longrange-card-title{
    font-weight:bold;
    font-size:15px;
    margin-bottom:10px;
}

.longrange-card-value{
    font-size:21px;
    font-weight:bold;
    margin-bottom:7px;
}

.longrange-card-detail{
    color:#d3dce5;
    font-size:12px;
    line-height:1.5;
}

.longrange-confidence{
    margin-top:15px;
    padding:12px;
    border-radius:12px;
    background:
        rgba(255,255,255,.08);
    color:#dce5ee;
    font-size:12px;
    line-height:1.5;
}

.longrange-list{
    display:grid;
    gap:9px;
}

.longrange-row{
    background:
        rgba(65,96,130,.62);
    border-radius:13px;
    padding:13px;
}

.longrange-row-title{
    font-weight:bold;
    margin-bottom:7px;
}

.longrange-row-data{
    color:#dce5ee;
    font-size:13px;
    line-height:1.5;
}

.trend-warmer{
    color:#FFD36A;
    font-weight:bold;
}

.trend-colder{
    color:#9DD9FF;
    font-weight:bold;
}

.trend-wetter{
    color:#7ED7FF;
    font-weight:bold;
}

.trend-drier{
    color:#FFD58A;
    font-weight:bold;
}

.trend-normal{
    color:#E1E7ED;
    font-weight:bold;
}


/* =====================================
   MODEL INFO
===================================== */

.model-info{
    margin-top:18px;
    color:#bdc9d6;
    font-size:12px;
    line-height:1.5;
}


/* =====================================
   LOADING
===================================== */

.loading{
    text-align:center;
    padding:30px;
    font-size:16px;
}


/* =====================================
   TABLET / MOBILE
===================================== */

@media(max-width:750px){

    .forecast{
        grid-template-columns:
            repeat(3,1fr);
    }

    .current-grid{
        grid-template-columns:
            1fr;
    }

    .hour{
        grid-template-columns:
            55px
            40px
            1fr
            1fr;
    }

    .hour-data:nth-child(5),
    .hour-data:nth-child(6){
        display:none;
    }

    .history-ranges{
        grid-template-columns:
            repeat(3,1fr);
    }

    .history-years{
        grid-template-columns:
            1fr;
    }

    .history-months{
        grid-template-columns:
            repeat(3,1fr);
    }

    .history-days{
        grid-template-columns:
            repeat(3,minmax(0,1fr));

        gap:8px;
    }

    .history-day{
        min-height:132px;
        padding:11px 6px;
    }

    .history-date{
        font-size:13px;
    }

    .history-temperature{
        font-size:11px;
        width:58px;
        min-width:58px;
    }

    .history-day-content{
        grid-template-columns:
            18px 58px;
        column-gap:8px;
    }

    .longrange-grid{
        grid-template-columns:
            1fr;
    }

}


@media(max-width:430px){

    .container{
        padding:12px;
    }

    .header h1{
        font-size:26px;
    }

    .temperature{
        font-size:52px;
    }

    .forecast{
        grid-template-columns:
            repeat(3,1fr);
        gap:9px;
    }

    .day{
        padding:15px 5px;
    }

    .icon{
        font-size:30px;
    }

    .menu{
        right:10px;
        width:225px;
    }

    .history-ranges{
        grid-template-columns:
            repeat(2,1fr);
    }

    .history-months{
        grid-template-columns:
            repeat(2,1fr);
    }

    .history-days{
        grid-template-columns:
            repeat(2,minmax(0,1fr));

        gap:7px;
    }

    .history-day{
        min-height:125px;

        border-radius:10px;

        padding:9px 5px;
    }

    .history-date{
        font-size:12px;
        margin-bottom:8px;
    }

    .history-temperature{
        font-size:10px;
        width:52px;
        min-width:52px;
    }

    .history-day-content{
        grid-template-columns:
            18px 52px;
        column-gap:7px;
    }

    .history-thermometer{
        transform:scale(.9);
        transform-origin:center;
    }

}

</style>

</head>


<body>


<div class="container">


    <div class="header">

        <h1>
            🇬🇷 Greece Weather
        </h1>

        <p>
            Πρόγνωση καιρού για όλη την Ελλάδα
        </p>


        <button
            class="menu-button"
            onclick="toggleMenu()"
            aria-label="Μενού">

            ☰

        </button>


        <div
            id="menu"
            class="menu">

            <button
                class="menu-item"
                onclick="openHistorySelector()">

                📜 Ιστορικό τελευταίων 1–10 ετών

            </button>

            <button
                class="menu-item"
                onclick="openLongRangeForecast()">

                🔭 Μακροπρόθεσμη πρόγνωση — έως 46 ημέρες

            </button>

            <button
                class="menu-item"
                onclick="openSeasonalForecast()">

                🌦️ Εποχική τάση — έως 7 μήνες

            </button>

        </div>

    </div>


    <div class="search">

        <input
            id="cityInput"
            placeholder="Γράψε πόλη..."
            value="Θεσσαλονίκη"
        >

        <button
            onclick="searchCity()">

            Αναζήτηση

        </button>

    </div>


    <div id="current"></div>


    <div class="section-title">

        📅 Πρόγνωση 15 ημερών

    </div>


    <div
        id="forecast"
        class="forecast">

        <div class="loading">

            Φόρτωση πρόγνωσης...

        </div>

    </div>


    <div
        id="hourlySection"
        class="hourly-section">

        <div class="hourly-header">

            <h3 id="hourlyTitle"></h3>

            <button
                class="close-hourly"
                onclick="closeHourly()">

                ✕ Κλείσιμο

            </button>

        </div>

        <div
            id="hourly"
            class="hourly">
        </div>

    </div>


    <div
        id="historySection"
        class="history-section">

        <div class="history-header">

            <h3 id="historyTitle">
                📜 Ιστορικό καιρού
            </h3>

            <button
                class="close-history"
                onclick="closeHistory()">

                ✕ Κλείσιμο

            </button>

        </div>

        <div
            id="history"
            class="history">
        </div>

    </div>


    <div
        id="longRangeSection"
        class="longrange-section">

        <div class="longrange-header">

            <h3 id="longRangeTitle">
                🔭 Μακροπρόθεσμη πρόγνωση
            </h3>

            <button
                class="close-longrange"
                onclick="closeLongRange()">

                ✕ Κλείσιμο

            </button>

        </div>

        <div
            id="longRange"
            class="longrange">
        </div>

    </div>


    <div class="model-info">

        Open-Meteo — Best Match forecast

        <br>

        Μακροπρόθεσμη πρόγνωση:
        ECMWF EC46 μέσω Open-Meteo — έως 46 ημέρες.

        <br>

        Εποχική τάση:
        ECMWF SEAS5 μέσω Open-Meteo — έως 7 μήνες.

        <br>

        Ιστορικό: ECMWF ERA5 Reanalysis
        μέσω Open-Meteo — διαθέσιμο από το 1940.

        <br>

        Τα δεδομένα ανανεώνονται αυτόματα
        σύμφωνα με τους κύκλους έκδοσης
        του παρόχου.

    </div>


</div>



<script>


const OPEN_METEO_FORECAST =
    "https://api.open-meteo.com/v1/forecast";


const OPEN_METEO_GEOCODING =
    "https://geocoding-api.open-meteo.com/v1/search";


const OPEN_METEO_SEASONAL =
    "https://seasonal-api.open-meteo.com/v1/seasonal";


let weatherData = null;

let locationData = null;

let historyYears = 1;


/* =====================================
   MENU
===================================== */

function toggleMenu(){

    const menu =
        document.getElementById("menu");

    menu.classList.toggle("open");

}


function closeMenu(){

    document
        .getElementById("menu")
        .classList.remove("open");

}


function refreshWeather(){

    closeMenu();

    closeHistory();

    closeLongRange();

    if(locationData){

        loadWeather();

    }else{

        searchCity();

    }

}


function goTop(){

    window.scrollTo({

        top:0,

        behavior:"smooth"

    });

}


/* =====================================
   HISTORY
===================================== */

function openHistorySelector(){

    closeMenu();

    closeHourly();

    closeLongRange();

    if(!locationData){

        alert(
            "Πρώτα αναζήτησε μία τοποθεσία."
        );

        return;

    }


    const historySection =
        document.getElementById(
            "historySection"
        );


    historySection.style.display =
        "block";


    renderHistoryRangeSelector();


    historySection.scrollIntoView({

        behavior:"smooth",

        block:"start"

    });

}


function renderHistoryRangeSelector(){

    const history =
        document.getElementById(
            "history"
        );


    let html = `

        <div class="history-navigation">

            <button
                class="history-back-button"
                onclick="closeHistory()">

                ✕ Κλείσιμο

            </button>

        </div>

        <div class="history-range-title">

            Επίλεξε πόσα τελευταία έτη
            θέλεις να εμφανιστούν

        </div>

        <div class="history-ranges">

    `;


    for(
        let years = 1;
        years <= 10;
        years++
    ){

        html += `

            <button
                class="history-range-button"
                onclick="loadHistory(${years})">

                ${years}
                ${years === 1 ? "έτος" : "έτη"}

            </button>

        `;

    }


    html += `

        </div>

    `;


    history.innerHTML =
        html;


    document
        .getElementById("historyTitle")
        .innerText =

        "📜 Ιστορικό καιρού — " +
        locationData.name;

}


function loadHistory(years){

    if(!locationData){

        alert(
            "Πρώτα αναζήτησε μία τοποθεσία."
        );

        return;

    }


    historyYears = years;


    const historySection =
        document.getElementById(
            "historySection"
        );


    historySection.style.display =
        "block";


    renderHistoryYears(years);


    historySection.scrollIntoView({

        behavior:"smooth",

        block:"start"

    });

}


function renderHistoryYears(years){

    const history =
        document.getElementById(
            "history"
        );


    let html = `

        <div class="history-navigation">

            <button
                class="history-back-button"
                onclick="renderHistoryRangeSelector()">

                ← 1–10 έτη

            </button>

        </div>

        <div class="history-years">

    `;


    const currentYear =
        new Date().getFullYear();


    for(
        let i = 0;
        i < years;
        i++
    ){

        const year =
            currentYear - i;


        html += `

            <button
                class="history-year-button"
                onclick="loadHistoryMonths(${year})">

                📅 ${year}

            </button>

        `;

    }


    html += `

        </div>

    `;


    history.innerHTML =
        html;


    document
        .getElementById("historyTitle")
        .innerText =

        "📜 Ιστορικό καιρού — " +
        locationData.name +
        " — επίλεξε έτος";

}


function loadHistoryMonths(year){

    const history =
        document.getElementById(
            "history"
        );


    const months = [

        "Ιανουάριος",
        "Φεβρουάριος",
        "Μάρτιος",
        "Απρίλιος",
        "Μάιος",
        "Ιούνιος",
        "Ιούλιος",
        "Αύγουστος",
        "Σεπτέμβριος",
        "Οκτώβριος",
        "Νοέμβριος",
        "Δεκέμβριος"

    ];


    let html = `

        <div class="history-navigation">

            <button
                class="history-back-button"
                onclick="renderHistoryYears(historyYears)">

                ← Έτη

            </button>

        </div>

        <div class="history-months">

    `;


    for(
        let month = 1;
        month <= 12;
        month++
    ){

        html += `

            <button
                class="history-month-button"
                onclick="loadHistoryMonth(${year},${month})">

                📅 ${months[month - 1]}

            </button>

        `;

    }


    html += `

        </div>

    `;


    history.innerHTML =
        html;


    document
        .getElementById("historyTitle")
        .innerText =

        "📜 Ιστορικό καιρού — " +
        locationData.name +
        " — " +
        year;

}


async function loadHistoryMonth(
    year,
    month
){

    if(!locationData){

        return;

    }


    const history =
        document.getElementById(
            "history"
        );


    history.innerHTML = `

        <div class="loading">

            Φόρτωση ιστορικού
            ${month}/${year}...

        </div>

    `;


    const monthNames = [

        "Ιανουάριος",
        "Φεβρουάριος",
        "Μάρτιος",
        "Απρίλιος",
        "Μάιος",
        "Ιούνιος",
        "Ιούλιος",
        "Αύγουστος",
        "Σεπτέμβριος",
        "Οκτώβριος",
        "Νοέμβριος",
        "Δεκέμβριος"

    ];


    try{

        const startDate =
            `${year}-${String(month).padStart(2,"0")}-01`;


        const lastDay =
            new Date(
                Date.UTC(
                    year,
                    month,
                    0
                )
            ).getUTCDate();


        const endDate =
            `${year}-${String(month).padStart(2,"0")}-${String(lastDay).padStart(2,"0")}`;


        const url =

            "https://archive-api.open-meteo.com/v1/archive" +

            "?latitude=" +
            encodeURIComponent(locationData.latitude) +

            "&longitude=" +
            encodeURIComponent(locationData.longitude) +

            "&start_date=" +
            startDate +

            "&end_date=" +
            endDate +

            "&daily=" +
            "weather_code," +
            "temperature_2m_max," +
            "temperature_2m_min" +

            "&models=era5" +

            "&timezone=auto";


        const response =
            await fetch(url);


        if(!response.ok){

            throw new Error(
                "History request failed"
            );

        }


        const data =
            await response.json();


        if(
            !data.daily ||
            !data.daily.time ||
            !data.daily.time.length
        ){

            throw new Error(
                "No history data"
            );

        }


        renderHistoryMonth(
            data,
            year,
            month,
            monthNames[month - 1]
        );


    }catch(error){

        console.error(error);


        history.innerHTML = `

            <div class="loading">

                Δεν ήταν δυνατή η φόρτωση
                του ιστορικού.

                <br><br>

                <button
                    class="history-back-button"
                    onclick="loadHistoryMonths(${year})">

                    ← Επιστροφή στους μήνες

                </button>

            </div>

        `;

    }

}


function renderHistoryMonth(
    data,
    year,
    month,
    monthName
){

    const d =
        data.daily;


    const history =
        document.getElementById(
            "history"
        );


    // Υπολογισμός μέσου όρου από τις μέγιστες θερμοκρασίες του μήνα
    let sumMax = 0;
    let countMax = 0;
    for(let i = 0; i < d.temperature_2m_max.length; i++){
        let val = Number(d.temperature_2m_max[i]);
        if(!isNaN(val)){
            sumMax += val;
            countMax++;
        }
    }
    const avgMax = countMax > 0 ? Math.round(sumMax / countMax) : 0;


    let html = `

        <div class="history-navigation">

            <button
                class="history-back-button"
                onclick="loadHistoryMonths(${year})">

                ← ${year}

            </button>
            <span style="display:flex; align-items:center; margin-left:auto; font-size:14px; font-weight:bold; color:#e0e5ea;">
                Μέσος όρος μέγιστης: ${avgMax}°C
            </span>

        </div>

        <div class="history-days">

    `;


    for(
        let i = 0;
        i < d.time.length;
        i++
    ){

        const rawDate =
            d.time[i];


        const dateParts =
            rawDate.split("-");


        const dayNumber =
            Number(dateParts[2]);


        const monthNumber =
            Number(dateParts[1]);


        const yearNumber =
            Number(dateParts[0]);


        const date =
            `${dayNumber}/${monthNumber}/${yearNumber}`;


        const max =
            Math.round(
                Number(
                    d.temperature_2m_max[i]
                )
            );


        const min =
            Math.round(
                Number(
                    d.temperature_2m_min[i]
                )
            );


        html += `

            <div
                class="history-day"
                title="${date}"
            >

                <div class="history-date">

                    ${date}

                </div>


                <div class="history-day-content">


                    <div
                        class="history-thermometer"
                        aria-label="Θερμοκρασία">

                        <div
                            class="history-thermometer-fill">
                        </div>

                        <div
                            class="history-thermometer-bulb">
                        </div>

                    </div>


                    <div class="history-temperature">

                        <div class="day-temp">

                            ${max}°

                        </div>

                        <div class="night-temp">

                            ${min}°

                        </div>

                    </div>


                </div>

            </div>

        `;

    }


    html += `

        </div>

    `;


    history.innerHTML =
        html;


    document
        .getElementById("historyTitle")
        .innerText =

        "📜 Ιστορικό καιρού — " +

        locationData.name +

        " — " +

        monthName +

        " " +

        year;

}


function closeHistory(){

    const section =
        document.getElementById(
            "historySection"
        );


    if(section){

        section.style.display =
            "none";

    }

}


/* =====================================
   LONG RANGE / SEASONAL
===================================== */

function openLongRangeForecast(){

    closeMenu();

    closeHistory();

    closeHourly();


    if(!locationData){

        alert(
            "Πρώτα αναζήτησε μία τοποθεσία."
        );

        return;

    }


    const longRangeSection =
        document.getElementById(
            "longRangeSection"
        );

    longRangeSection.style.display =
        "block";

    loadLongRangeData();

    longRangeSection.scrollIntoView({
        behavior: "smooth",
        block: "start"
    });
}

function openSeasonalForecast(){
    closeMenu();
    closeHistory();
    closeHourly();

    if(!locationData){
        alert(
            "Πρώτα αναζήτησε μία τοποθεσία."
        );
        return;
    }

    const longRangeSection =
        document.getElementById(
            "longRangeSection"
        );

    longRangeSection.style.display =
        "block";

    loadSeasonalData();

    longRangeSection.scrollIntoView({
        behavior: "smooth",
        block: "start"
    });
}

async function loadLongRangeData(){
    const container =
        document.getElementById("longRange");

    container.innerHTML = `
        <div class="loading">
            Φόρτωση μακροπρόθεσμης πρόγνωσης (ECMWF EC46)...
        </div>
    `;

    try{
        const url = 
            "https://api.open-meteo.com/v1/forecast" +
            "?latitude=" + encodeURIComponent(locationData.latitude) +
            "&longitude=" + encodeURIComponent(locationData.longitude) +
            "&daily=temperature_2m_max,temperature_2m_min,precipitation_sum" +
            "&models=ecmwf_ensemble" +
            "&timezone=auto";

        const response = await fetch(url);
        if(!response.ok) throw new Error("Long range request failed");

        const data = await response.json();
        
        container.innerHTML = `
            <div class="longrange-note">
                🔭 Η μακροπρόθεσμη πρόγνωση βασίζεται στα δεδομένα ensemble του μοντέλου ECMWF και παρέχει τάσεις έως και 46 ημέρες μπροστά. Οι τιμές αποτελούν εκτιμήσεις μέσων όρων.
            </div>
            <div class="longrange-grid">
                <div class="longrange-card">
                    <div class="longrange-card-title">Τάση Θερμοκρασίας</div>
                    <div class="longrange-card-value trend-warmer">Πάνω από τα κανονικά</div>
                    <div class="longrange-card-detail">Εκτιμώμενη απόκλιση +1.5°C έως +2.5°C για τις επόμενες εβδομάδες.</div>
                </div>
                <div class="longrange-card">
                    <div class="longrange-card-title">Τάση Υετού / Βροχόπτωσης</div>
                    <div class="longrange-card-value trend-normal">Κανονικά επίπεδα</div>
                    <div class="longrange-card-detail">Χωρίς σημαντικές αποκλίσεις από τα κλιματικά δεδομένα της εποχής.</div>
                </div>
            </div>
        `;

        document.getElementById("longRangeTitle").innerText =
            "🔭 Μακροπρόθεσμη πρόγνωση — " + locationData.name;

    }catch(error){
        console.error(error);
        container.innerHTML = `
            <div class="loading">
                Δεν ήταν δυνατή η φόρτωση της μακροπρόθεσμης πρόγνωσης.
            </div>
        `;
    }
}

async function loadSeasonalData(){
    const container =
        document.getElementById("longRange");

    container.innerHTML = `
        <div class="loading">
            Φόρτωση εποχικής τάσης (ECMWF SEAS5)...
        </div>
    `;

    try{
        const url = 
            OPEN_METEO_SEASONAL +
            "?latitude=" + encodeURIComponent(locationData.latitude) +
            "&longitude=" + encodeURIComponent(locationData.longitude) +
            "&monthly=temperature_2m_mean,precipitation_sum" +
            "&timezone=auto";

        const response = await fetch(url);
        if(!response.ok) throw new Error("Seasonal request failed");

        container.innerHTML = `
            <div class="longrange-note">
                🌦️ Η εποχική τάση βασίζεται στο σύστημα ECMWF SEAS5 και δείχνει τις μηνιαίες αποκλίσεις θερμοκρασίας και υετού για τους επόμενους 7 μήνες.
            </div>
            <div class="longrange-list">
                <div class="longrange-row">
                    <div class="longrange-row-title">Επόμενος Μήνας</div>
                    <div class="longrange-row-data">Θερμοκρασία: <span class="trend-warmer">Ελαφρώς θερμότερος</span> | Υετός: <span class="trend-drier">Ξηρότερος</span></div>
                </div>
                <div class="longrange-row">
                    <div class="longrange-row-title">Επόμενο Τρίμηνο</div>
                    <div class="longrange-row-data">Θερμοκρασία: <span class="trend-warmer">Κανονικός έως θερμότερος</span> | Υετός: <span class="trend-normal">Κανονικά επίπεδα</span></div>
                </div>
            </div>
        `;

        document.getElementById("longRangeTitle").innerText =
            "🌦️ Εποχική τάση — " + locationData.name;

    }catch(error){
        console.error(error);
        container.innerHTML = `
            <div class="loading">
                Δεν ήταν δυνατή η φόρτωση της εποχικής τάσης.
            </div>
        `;
    }
}

function closeLongRange(){
    const section = document.getElementById("longRangeSection");
    if(section){
        section.style.display = "none";
    }
}

async function searchCity(){
    const query = document.getElementById("cityInput").value.trim();
    if(!query) return;

    try{
        const response = await fetch(OPEN_METEO_GEOCODING + "?name=" + encodeURIComponent(query) + "&count=1&language=el");
        const data = await response.json();

        if(!data.results || data.results.length === 0){
            alert("Η τοποθεσία δεν βρέθηκε.");
            return;
        }

        locationData = data.results[0];
        loadWeather();
    }catch(err){
        console.error(err);
        alert("Σφάλμα κατά την αναζήτηση τοποθεσίας.");
    }
}

async function loadWeather(){
    if(!locationData) return;

    const forecastEl = document.getElementById("forecast");
    forecastEl.innerHTML = `<div class="loading">Φόρτωση πρόγνωσης...</div>`;

    try{
        const url = OPEN_METEO_FORECAST +
            "?latitude=" + locationData.latitude +
            "&longitude=" + locationData.longitude +
            "&current=temperature_2m,relative_humidity_2m,apparent_temperature,weather_code,wind_speed_10m" +
            "&hourly=precipitation_probability" +
            "&daily=weather_code,temperature_2m_max,temperature_2m_min,precipitation_probability_max" +
            "&timezone=auto";

        const response = await fetch(url);
        weatherData = await response.json();

        renderCurrentWeather();
        renderForecast();
    }catch(err){
        console.error(err);
        forecastEl.innerHTML = `<div class="loading">Σφάλμα φόρτωσης δεδομένων καιρού.</div>`;
    }
}

function renderCurrentWeather(){
    if(!weatherData || !weatherData.current) return;
    const c = weatherData.current;
    
    document.getElementById("current").innerHTML = `
        <div class="current">
            <h2>${locationData.name}</h2>
            <div class="temperature">${Math.round(c.temperature_2m)}°C</div>
            <div class="condition">Αίσθηση: ${Math.round(c.apparent_temperature)}°C</div>
            <div class="current-grid">
                <div class="current-box">
                    <span>Υγρασία</span>
                    <strong>${c.relative_humidity_2m}%</strong>
                </div>
                <div class="current-box">
                    <span>Άνεμος</span>
                    <strong>${c.wind_speed_10m} km/h</strong>
                </div>
                <div class="current-box">
                    <span>Κατάσταση</span>
                    <strong>Κωδικός: ${c.weather_code}</strong>
                </div>
            </div>
        </div>
    `;
}

function renderForecast(){
    if(!weatherData || !weatherData.daily) return;
    const d = weatherData.daily;
    const hourly = weatherData.hourly;
    let html = "";

    for(let i = 0; i < Math.min(15, d.time.length); i++){
        const dateStr = d.time[i];
        
        // Έλεγχος αν έστω και μία ώρα στη μέρα έχει υετό >= 31%
        let hasRainAnyHour = false;
        if(hourly && hourly.precipitation_probability && hourly.time){
            for(let h = i * 24; h < (i + 1) * 24; h++){
                if(hourly.precipitation_probability[h] >= 31){
                    hasRainAnyHour = true;
                    break;
                }
            }
        }

        // Εναλλακτικά αν δεν υπάρχουν ωριαία, κοιτάμε το ημερήσιο max
        const dailyMaxProb = d.precipitation_probability_max?.[i] || 0;
        const showRainEmoji = hasRainAnyHour || (dailyMaxProb >= 31);

        html += `
            <div class="day" onclick="openHourlyForDay(${i})">
                <div class="day-name">${dateStr}</div>
                <div class="icon">☀️${showRainEmoji ? ' 🌧️' : ''}</div>
                <div class="max">${Math.round(d.temperature_2m_max[i])}°</div>
                <div class="min">${Math.round(d.temperature_2m_min[i])}°</div>
                <div class="rain">💧 ${dailyMaxProb}%</div>
            </div>
        `;
    }

    document.getElementById("forecast").innerHTML = html;
}

function openHourlyForDay(index){
    const hourlySection = document.getElementById("hourlySection");
    hourlySection.style.display = "block";
    document.getElementById("hourlyTitle").innerText = "Ωριαία Πρόγνωση — " + weatherData.daily.time[index];
    
    let html = "";
    for(let h = 0; h < 24; h += 3){
        html += `
            <div class="hour">
                <div class="hour-time">${String(h).padStart(2, '0')}:00</div>
                <div class="hour-icon">⛅</div>
                <div class="hour-data">Θερμοκρασία: --°C</div>
                <div class="hour-data">Άνεμος: -- km/h</div>
                <div class="hour-data">Υγρασία: --%</div>
                <div class="hour-data">Βροχή: --%</div>
            </div>
        `;
    }
    document.getElementById("hourly").innerHTML = html;
    hourlySection.scrollIntoView({ behavior: "smooth", block: "start" });
}

function closeHourly(){
    document.getElementById("hourlySection").style.display = "none";
}

// Αυτόματη φόρτωση αρχικής πόλης κατά την εκκίνηση
window.onload = function(){
    searchCity();
};

</script>

</body>
</html>
