<!DOCTYPE html>
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


    <div class="model-info">

        Open-Meteo — Best Match forecast

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


    let html = `

        <div class="history-navigation">

            <button
                class="history-back-button"
                onclick="loadHistoryMonths(${year})">

                ← ${year}

            </button>

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
   OUTSIDE MENU
===================================== */

document.addEventListener(
    "click",
    function(event){

        const menu =
            document.getElementById("menu");

        const button =
            document.querySelector(".menu-button");


        if(
            menu.classList.contains("open") &&
            !menu.contains(event.target) &&
            !button.contains(event.target)
        ){

            menu.classList.remove("open");

        }

    }
);


/* =====================================
   COUNTRY FLAG
===================================== */

function countryFlag(countryCode){

    if(!countryCode){

        return "🌍";

    }


    const code =
        countryCode
        .toUpperCase()
        .trim();


    if(code.length !== 2){

        return "🌍";

    }


    return String
        .fromCodePoint(
            ...[...code].map(
                char =>
                    127397 +
                    char.charCodeAt(0)
            )
        );

}


/* =====================================
   DATE
===================================== */

const greekDays = [

    "Κυρ",
    "Δευ",
    "Τρί",
    "Τετ",
    "Πέμ",
    "Παρ",
    "Σάβ"

];


function formatDate(
    dateString,
    includeYear = false
){

    const parts =
        dateString.split("-");


    const year =
        Number(parts[0]);


    const month =
        Number(parts[1]);


    const day =
        Number(parts[2]);


    const d =
        new Date(
            Date.UTC(
                year,
                month - 1,
                day
            )
        );


    let formattedDate =

        String(day) +
        "/" +
        String(month);


    if(includeYear){

        formattedDate +=

            "/" +
            String(year);

    }


    return {

        day:
            greekDays[d.getUTCDay()],

        date:
            formattedDate

    };

}


/* =====================================
   ΕΝΙΑΙΑ WEATHER SVG
===================================== */

function svgWrap(content){

    return `

        <span class="weather-svg">

            <svg
                viewBox="0 0 64 64"
                xmlns="http://www.w3.org/2000/svg"
                aria-hidden="true">

                ${content}

            </svg>

        </span>

    `;

}


/* =====================================
   WEATHER ICON
   Κάθε κατάσταση = ΕΝΑ ενιαίο εικονίδιο
===================================== */

function weatherIcon(
    code,
    isDay = true,
    precipitationProbability = 0,
    snowfall = 0,
    windSpeed = 0,
    cloudCover = 0
){

    code =
        Number(code);

    precipitationProbability =
        Number(precipitationProbability || 0);

    snowfall =
        Number(snowfall || 0);

    windSpeed =
        Number(windSpeed || 0);

    cloudCover =
        Number(cloudCover || 0);


    const rainCodes = [

        51,53,55,
        61,63,65,
        80,81,82

    ];


    const sleetCodes = [

        56,57,
        66,67

    ];


    const snowCodes = [

        71,73,75,77,
        85,86

    ];


    const stormCodes = [

        95,96,99

    ];


    const hasPrecipitation =

        snowfall > 0 ||

        rainCodes.includes(code) ||

        sleetCodes.includes(code) ||

        snowCodes.includes(code) ||

        stormCodes.includes(code);


    const fullClouds =
        cloudCover >= 70;


    const strongWind =
        windSpeed >= 32;


    /*
       =================================
       ΙΣΧΥΡΟΣ ΑΝΕΜΟΣ + ΥΕΤΟΣ
       >=32 km/h
       =================================
    */

    if(
        strongWind &&
        hasPrecipitation
    ){

        /* ΚΑΤΑΙΓΙΔΑ */

        if(stormCodes.includes(code)){

            return svgWrap(`

                <path
                    d="M15 39
                       C8 39 8 29 16 26
                       C18 18 29 15 36 22
                       C45 20 53 27 50 35
                       C56 38 53 46 45 46
                       H15Z"
                    fill="#66798D"/>

                <path
                    d="M31 36
                       L24 50
                       L32 47
                       L28 61
                       L42 42
                       L34 45
                       L40 36Z"
                    fill="#FFD83D"/>

                <path
                    d="M10 49
                       C18 44 24 51 31 47"
                    fill="none"
                    stroke="#55BCEB"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M39 49
                       C46 45 51 49 56 46"
                    fill="none"
                    stroke="#55BCEB"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M9 55
                       C16 51 21 56 27 53"
                    fill="none"
                    stroke="#DCEAF4"
                    stroke-width="2.5"
                    stroke-linecap="round"/>

                <path
                    d="M40 56
                       C47 52 52 56 57 53"
                    fill="none"
                    stroke="#DCEAF4"
                    stroke-width="2.5"
                    stroke-linecap="round"/>

            `);

        }


        /* ΕΝΤΟΝΟ ΧΙΟΝΟΝΕΡΟ */

        if(sleetCodes.includes(code)){

            return svgWrap(`

                <path
                    d="M13 39
                       C7 39 7 30 15 27
                       C17 19 28 17 35 23
                       C44 21 52 28 49 36
                       C55 39 52 47 44 47
                       H13Z"
                    fill="#617487"/>

                <path
                    d="M18 49
                       L14 59"
                    stroke="#55BCEB"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M29 49
                       L25 59"
                    stroke="#55BCEB"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M41 49
                       L37 59"
                    stroke="#55BCEB"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M49 47
                       L49 57
                       M44 52
                       L54 52
                       M45.5 48.5
                       L52.5 55.5
                       M52.5 48.5
                       L45.5 55.5"
                    stroke="#FFFFFF"
                    stroke-width="2"
                    stroke-linecap="round"/>

                <path
                    d="M7 22
                       L20 17"
                    stroke="#E8F1F7"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M40 18
                       L56 14"
                    stroke="#E8F1F7"
                    stroke-width="3"
                    stroke-linecap="round"/>

            `);

        }


        /* ΕΝΤΟΝΗ ΧΙΟΝΟΠΤΩΣΗ */

        if(
            snowCodes.includes(code) ||
            snowfall > 0
        ){

            return svgWrap(`

                <path
                    d="M13 39
                       C7 39 7 30 15 27
                       C17 19 28 17 35 23
                       C44 21 52 28 49 36
                       C55 39 52 47 44 47
                       H13Z"
                    fill="#5F7286"/>

                <path
                    d="M17 48
                       L17 59
                       M11.5 53.5
                       L22.5 53.5
                       M13 49.5
                       L21 57.5
                       M21 49.5
                       L13 57.5"
                    stroke="#FFFFFF"
                    stroke-width="2"
                    stroke-linecap="round"/>

                <path
                    d="M31 48
                       L31 60
                       M25 54
                       L37 54
                       M26.5 49.5
                       L35.5 58.5
                       M35.5 49.5
                       L26.5 58.5"
                    stroke="#F7FBFF"
                    stroke-width="2"
                    stroke-linecap="round"/>

                <path
                    d="M46 48
                       L46 58
                       M41 53
                       L51 53
                       M42.5 49.5
                       L49.5 56.5
                       M49.5 49.5
                       L42.5 56.5"
                    stroke="#FFFFFF"
                    stroke-width="2"
                    stroke-linecap="round"/>

                <path
                    d="M7 23
                       L20 18"
                    stroke="#E8F1F7"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M40 18
                       L56 14"
                    stroke="#E8F1F7"
                    stroke-width="3"
                    stroke-linecap="round"/>

            `);

        }


        /* ΕΝΤΟΝΗ ΒΡΟΧΗ */

        if(rainCodes.includes(code)){

            return svgWrap(`

                <path
                    d="M13 39
                       C7 39 7 30 15 27
                       C17 19 28 17 35 23
                       C44 21 52 28 49 36
                       C55 39 52 47 44 47
                       H13Z"
                    fill="#5E7387"/>

                <path
                    d="M17 48
                       L12 61"
                    stroke="#4AB9EB"
                    stroke-width="4"
                    stroke-linecap="round"/>

                <path
                    d="M29 48
                       L24 61"
                    stroke="#4AB9EB"
                    stroke-width="4"
                    stroke-linecap="round"/>

                <path
                    d="M41 48
                       L36 61"
                    stroke="#4AB9EB"
                    stroke-width="4"
                    stroke-linecap="round"/>

                <path
                    d="M7 22
                       L20 17"
                    stroke="#E8F1F7"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M40 18
                       L56 14"
                    stroke="#E8F1F7"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M9 53
                       L4 58"
                    stroke="#CFE4EF"
                    stroke-width="2.5"
                    stroke-linecap="round"/>

                <path
                    d="M51 51
                       L58 55"
                    stroke="#CFE4EF"
                    stroke-width="2.5"
                    stroke-linecap="round"/>

            `);

        }

    }


    /*
       =================================
       ΔΥΝΑΤΟΣ ΑΝΕΜΟΣ ΧΩΡΙΣ ΥΕΤΟ
       >=32 km/h
       =================================
    */

    if(
        strongWind &&
        !hasPrecipitation &&
        ![45,48].includes(code)
    ){

        if(isDay){

            return svgWrap(`

                <circle
                    cx="23"
                    cy="24"
                    r="10"
                    fill="#FFD34E"/>

                <path
                    d="M8 42
                       C20 34, 29 46, 39 38
                       C45 33, 51 36, 55 38"
                    fill="none"
                    stroke="#D8E4EF"
                    stroke-width="4"
                    stroke-linecap="round"/>

                <path
                    d="M17 51
                       C27 45, 34 53, 44 47"
                    fill="none"
                    stroke="#AFC5D9"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M40 17
                       L52 13"
                    stroke="#FFFFFF"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M7 29
                       L20 25"
                    stroke="#E7EFF5"
                    stroke-width="3"
                    stroke-linecap="round"/>

            `);

        }


        return svgWrap(`

            <path
                d="M23 10
                   A13 13 0 1 0 39 30
                   A11 11 0 1 1 23 10Z"
                fill="#B9C4D0"/>

            <path
                d="M9 42
                   C19 34, 28 44, 38 37
                   C44 33, 50 36, 55 39"
                fill="none"
                stroke="#D8E1EA"
                stroke-width="7"
                stroke-linecap="round"/>

            <path
                d="M10 51
                   C22 44, 31 53, 44 47"
                fill="none"
                stroke="#AABAC9"
                stroke-width="3"
                stroke-linecap="round"/>

            <path
                d="M7 29
                   L20 25"
                stroke="#E7EFF5"
                stroke-width="3"
                stroke-linecap="round"/>

        `);

    }


    /* =================================
       ΚΑΤΑΙΓΙΔΑ
    ================================= */

    if(
        stormCodes.includes(code)
    ){

        return svgWrap(`

            <path
                d="M18 39
                   C10 39 9 28 18 25
                   C20 17 31 14 37 21
                   C46 19 53 26 50 34
                   C56 37 53 45 46 45
                   H18Z"
                fill="#71849A"/>

            <path
                d="M31 38
                   L25 51
                   L32 49
                   L29 60
                   L41 44
                   L34 46
                   L39 38Z"
                fill="#FFD84A"/>

            <path
                d="M23 48
                   L20 54"
                stroke="#65BCEB"
                stroke-width="3"
                stroke-linecap="round"/>

            <path
                d="M44 48
                   L41 54"
                stroke="#65BCEB"
                stroke-width="3"
                stroke-linecap="round"/>

        `);

    }


    /* =================================
       ΠΛΗΡΗΣ ΣΥΝΝΕΦΙΑ + ΧΙΟΝΟΝΕΡΟ
       ΗΜΕΡΑ / ΝΥΧΤΑ
    ================================= */

    if(
        sleetCodes.includes(code) &&
        fullClouds
    ){

        return svgWrap(`

            <path
                d="M12 40
                   C7 40 7 31 15 27
                   C17 19 28 17 36 24
                   C45 22 53 29 50 37
                   C56 40 53 48 45 48
                   H12Z"
                fill="#667A8E"/>

            <path
                d="M18 49
                   L15 59"
                stroke="#59B8E8"
                stroke-width="3"
                stroke-linecap="round"/>

            <path
                d="M30 49
                   L27 59"
                stroke="#59B8E8"
                stroke-width="3"
                stroke-linecap="round"/>

            <path
                d="M43 50
                   L43 57
                   M39.5 53.5
                   L46.5 53.5
                   M40.5 51
                   L45.5 56
                   M45.5 51
                   L40.5 56"
                stroke="#FFFFFF"
                stroke-width="1.8"
                stroke-linecap="round"/>

        `);

    }


    /* =================================
       ΠΛΗΡΗΣ ΣΥΝΝΕΦΙΑ + ΧΙΟΝΙ
       ΗΜΕΡΑ / ΝΥΧΤΑ
       ΠΟΛΛΕΣ ΝΙΦΑΔΕΣ
    ================================= */

    if(
        snowCodes.includes(code) &&
        fullClouds
    ){

        return svgWrap(`

            <path
                d="M12 40
                   C7 40 7 31 15 27
                   C17 19 28 17 36 24
                   C45 22 53 29 50 37
                   C56 40 53 48 45 48
                   H12Z"
                fill="#667A8E"/>

            <path
                d="M17 48
                   L17 58
                   M12 53
                   L22 53
                   M13.5 49.5
                   L20.5 56.5
                   M20.5 49.5
                   L13.5 56.5"
                stroke="#FFFFFF"
                stroke-width="1.9"
                stroke-linecap="round"/>

            <path
                d="M31 48
                   L31 59
                   M25.5 53.5
                   L36.5 53.5
                   M27 49.5
                   L35 57.5
                   M35 49.5
                   L27 57.5"
                stroke="#F7FBFF"
                stroke-width="1.9"
                stroke-linecap="round"/>

            <path
                d="M45 49
                   L45 58
                   M40.5 53.5
                   L49.5 53.5
                   M41.5 50
                   L48.5 57
                   M48.5 50
                   L41.5 57"
                stroke="#FFFFFF"
                stroke-width="1.9"
                stroke-linecap="round"/>

        `);

    }


    /* =================================
       ΠΛΗΡΗΣ ΣΥΝΝΕΦΙΑ + ΒΡΟΧΗ
       ΗΜΕΡΑ / ΝΥΧΤΑ
    ================================= */

    if(
        rainCodes.includes(code) &&
        fullClouds
    ){

        return svgWrap(`

            <path
                d="M12 40
                   C7 40 7 31 15 27
                   C17 19 28 17 36 24
                   C45 22 53 29 50 37
                   C56 40 53 48 45 48
                   H12Z"
                fill="#667A8E"/>

            <path
                d="M18 49
                   L15 59"
                stroke="#56BCEB"
                stroke-width="3"
                stroke-linecap="round"/>

            <path
                d="M31 49
                   L28 59"
                stroke="#56BCEB"
                stroke-width="3"
                stroke-linecap="round"/>

            <path
                d="M44 49
                   L41 59"
                stroke="#56BCEB"
                stroke-width="3"
                stroke-linecap="round"/>

        `);

    }


    /* =================================
       ΧΙΟΝΟΝΕΡΟ
       ΗΛΙΟΣ/ΦΕΓΓΑΡΙ + ΣΥΝΝΕΦΟ
    ================================= */

    if(
        sleetCodes.includes(code)
    ){

        if(isDay){

            return svgWrap(`

                <circle
                    cx="22"
                    cy="20"
                    r="10"
                    fill="#FFD34E"/>

                <path
                    d="M17 41
                       C10 41 10 31 18 28
                       C20 21 30 20 36 26
                       C45 24 52 31 49 39
                       C54 41 52 47 45 47
                       H17Z"
                    fill="#8295A8"/>

                <path
                    d="M24 48
                       L21 57"
                    stroke="#59B8E8"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M36 49
                       L33 57"
                    stroke="#59B8E8"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M45 49
                       L45 56
                       M42 52.5
                       L48 52.5
                       M43 50.5
                       L47 54.5
                       M47 50.5
                       L43 54.5"
                    stroke="#FFFFFF"
                    stroke-width="1.6"
                    stroke-linecap="round"/>

            `);

        }


        return svgWrap(`

            <path
                d="M23 9
                   A13 13 0 1 0 39 29
                   A11 11 0 1 1 23 9Z"
                fill="#B9C4D0"/>

            <path
                d="M17 41
                   C10 41 10 31 18 28
                   C20 21 30 20 36 26
                   C45 24 52 31 49 39
                   C54 41 52 47 45 47
                   H17Z"
                fill="#7A8B9D"/>

            <path
                d="M24 48
                   L21 57"
                stroke="#59B8E8"
                stroke-width="3"
                stroke-linecap="round"/>

            <path
                d="M36 49
                   L33 57"
                stroke="#59B8E8"
                stroke-width="3"
                stroke-linecap="round"/>

            <path
                d="M45 49
                   L45 56
                   M42 52.5
                   L48 52.5
                   M43 50.5
                   L47 54.5
                   M47 50.5
                   L43 54.5"
                stroke="#FFFFFF"
                stroke-width="1.6"
                stroke-linecap="round"/>

        `);

    }


    /* =================================
       ΧΙΟΝΙ
       ΗΛΙΟΣ/ΦΕΓΓΑΡΙ + ΣΥΝΝΕΦΟ
       ΠΟΛΛΕΣ ΝΙΦΑΔΕΣ
    ================================= */

    if(
        snowCodes.includes(code) ||
        snowfall > 0
    ){

        if(isDay){

            return svgWrap(`

                <circle
                    cx="22"
                    cy="21"
                    r="10"
                    fill="#FFD34E"/>

                <path
                    d="M18 41
                   C11 41 10 31 18 28
                   C20 21 30 19 36 25
                   C45 23 52 30 49 38
                   C54 40 52 47 45 47
                   H18Z"
                    fill="#8799AA"/>

                <path
                    d="M18 48
                       L18 57
                       M13.5 52.5
                       L22.5 52.5
                       M14.5 49
                       L21.5 56
                       M21.5 49
                       L14.5 56"
                    stroke="#FFFFFF"
                    stroke-width="1.8"
                    stroke-linecap="round"/>

                <path
                    d="M31 48
                       L31 58
                       M26 53
                       L36 53
                       M27.5 49.5
                       L34.5 56.5
                       M34.5 49.5
                       L27.5 56.5"
                    stroke="#F4F8FC"
                    stroke-width="1.8"
                    stroke-linecap="round"/>

                <path
                    d="M44 49
                       L44 57
                       M40 53
                       L48 53
                       M41 50
                       L47 56
                       M47 50
                       L41 56"
                    stroke="#FFFFFF"
                    stroke-width="1.8"
                    stroke-linecap="round"/>

            `);

        }


        return svgWrap(`

            <path
                d="M23 9
                   A13 13 0 1 0 39 29
                   A11 11 0 1 1 23 9Z"
                fill="#B8C3CE"/>

            <path
                d="M18 42
                   C11 42 10 32 18 29
                   C20 22 30 20 36 26
                   C45 24 52 31 49 39
                   C54 41 52 48 45 48
                   H18Z"
                fill="#718397"/>

            <path
                d="M18 49
                   L18 58
                   M13.5 53.5
                   L22.5 53.5
                   M14.5 50
                   L21.5 57
                   M21.5 50
                   L14.5 57"
                stroke="#FFFFFF"
                stroke-width="1.8"
                stroke-linecap="round"/>

            <path
                d="M31 49
                   L31 59
                   M26 54
                   L36 54
                   M27.5 50.5
                   L34.5 57.5
                   M34.5 50.5
                   L27.5 57.5"
                stroke="#F4F8FC"
                stroke-width="1.8"
                stroke-linecap="round"/>

            <path
                d="M44 50
                   L44 58
                   M40 54
                   L48 54
                   M41 51
                   L47 57
                   M47 51
                   L41 57"
                stroke="#FFFFFF"
                stroke-width="1.8"
                stroke-linecap="round"/>

        `);

    }


    /* =================================
       ΒΡΟΧΗ
       ΗΛΙΟΣ/ΦΕΓΓΑΡΙ + ΣΥΝΝΕΦΟ
    ================================= */

    if(
        rainCodes.includes(code)
    ){

        if(isDay){

            return svgWrap(`

                <circle
                    cx="22"
                    cy="20"
                    r="10"
                    fill="#FFD34E"/>

                <path
                    d="M17 41
                       C10 41 10 31 18 28
                       C20 21 30 20 36 26
                       C45 24 52 31 49 39
                       C54 41 52 47 45 47
                       H17Z"
                    fill="#7D91A5"/>

                <path
                    d="M21 49
                       L18 58"
                    stroke="#56BCEB"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M32 49
                       L29 58"
                    stroke="#56BCEB"
                    stroke-width="3"
                    stroke-linecap="round"/>

                <path
                    d="M43 49
                       L40 58"
                    stroke="#56BCEB"
                    stroke-width="3"
                    stroke-linecap="round"/>

            `);

        }


        return svgWrap(`

            <path
                d="M23 9
                   A13 13 0 1 0 39 29
                   A11 11 0 1 1 23 9Z"
                fill="#B9C4D0"/>

            <path
                d="M17 41
                   C10 41 10 31 18 28
                   C20 21 30 20 36 26
                   C45 24 52 31 49 39
                   C54 41 52 47 45 47
                   H17Z"
                fill="#6F8194"/>

            <path
                d="M21 49
                   L18 58"
                stroke="#56BCEB"
                stroke-width="3"
                stroke-linecap="round"/>

            <path
                d="M32 49
                   L29 58"
                stroke="#56BCEB"
                stroke-width="3"
                stroke-linecap="round"/>

            <path
                d="M43 49
                   L40 58"
                stroke="#56BCEB"
                stroke-width="3"
                stroke-linecap="round"/>

        `);

    }


    /* =================================
       ΟΜΙΧΛΗ
    ================================= */

    if(
        [45,48].includes(code)
    ){

        return svgWrap(`

            <path
                d="M12 24 H52"
                stroke="#B8C5D2"
                stroke-width="5"
                stroke-linecap="round"/>

            <path
                d="M8 34 H47"
                stroke="#D0D9E1"
                stroke-width="5"
                stroke-linecap="round"/>

            <path
                d="M15 44 H55"
                stroke="#A9B8C7"
                stroke-width="5"
                stroke-linecap="round"/>

            <path
                d="M22 15 H42"
                stroke="#8FA1B3"
                stroke-width="4"
                stroke-linecap="round"/>

        `);

    }


    /* =================================
       ΠΟΛΛΑ ΣΥΝΝΕΦΑ
    ================================= */

    if(code === 3){

        return svgWrap(`

            <path
                d="M13 42
                   C7 42 7 32 15 29
                   C17 21 27 19 33 25
                   C42 23 50 30 47 38
                   C53 40 51 47 44 47
                   H13Z"
                fill="#77899B"/>

            <path
                d="M22 33
                   C17 33 16 26 22 24
                   C24 18 32 17 37 22
                   C44 21 49 26 47 32
                   H22Z"
                fill="#AAB7C3"/>

        `);

    }


    /* =================================
       ΛΙΓΑ ΣΥΝΝΕΦΑ — ΗΜΕΡΑ / ΝΥΧΤΑ
    ================================= */

    if(
        code === 1 ||
        code === 2
    ){

        if(isDay){

            return svgWrap(`

                <circle
                    cx="24"
                    cy="23"
                    r="12"
                    fill="#FFD34E"/>

                <path
                    d="M25 45
                       C17 45 16 35 24 32
                       C26 25 36 24 42 30
                       C49 29 54 34 52 40
                       C56 42 54 47 48 47
                       H25Z"
                    fill="#B7C3CF"/>

            `);

        }


        return svgWrap(`

            <path
                d="M22 10
                   A13 13 0 1 0 38 30
                   A11 11 0 1 1 22 10Z"
                fill="#B8C4D0"/>

            <path
                d="M22 45
                   C15 45 15 35 23 32
                   C25 25 35 24 41 30
                   C48 29 53 34 51 40
                   C55 42 53 47 47 47
                   H22Z"
                fill="#9BAAB8"/>

        `);

    }


    /* =================================
       ΚΑΘΑΡΟΣ ΟΥΡΑΝΟΣ
    ================================= */

    if(code === 0){

        if(isDay){

            return svgWrap(`

                <circle
                    cx="32"
                    cy="32"
                    r="17"
                    fill="#FFD34E"/>

                <circle
                    cx="32"
                    cy="32"
                    r="12"
                    fill="#FFE071"/>

            `);

        }


        return svgWrap(`

            <path
                d="M25 9
                   A18 18 0 1 0 47 36
                   A15 15 0 1 1 25 9Z"
                fill="#C4CED8"/>

            <circle
                cx="21"
                cy="20"
                r="2"
                fill="#EEF3F7"/>

            <circle
                cx="44"
                cy="17"
                r="1.7"
                fill="#EEF3F7"/>

            <circle
                cx="48"
                cy="28"
                r="1.5"
                fill="#EEF3F7"/>

        `);

    }


    return isDay

        ? svgWrap(`

            <circle
                cx="32"
                cy="32"
                r="15"
                fill="#FFD34E"/>

        `)

        : svgWrap(`

            <path
                d="M25 9
                   A18 18 0 1 0 47 36
                   A15 15 0 1 1 25 9Z"
                fill="#C4CED8"/>

        `);

}


/* =====================================
   WEATHER TEXT
===================================== */

function weatherText(code){

    code =
        Number(code);


    if(code === 0)
        return "Αίθριος";


    if(code === 1)
        return "Κυρίως αίθριος";


    if(code === 2)
        return "Λίγες νεφώσεις";


    if(code === 3)
        return "Συννεφιά";


    if(
        [45,48].includes(code)
    )
        return "Ομίχλη";


    if(
        [51,53,55].includes(code)
    )
        return "Ψιλόβροχο";


    if(
        [56,57,66,67].includes(code)
    )
        return "Χιονόνερο";


    if(
        [61,63,65].includes(code)
    )
        return "Βροχή";


    if(
        [71,73,75,77].includes(code)
    )
        return "Χιόνι";


    if(
        [80,81,82].includes(code)
    )
        return "Μπόρες";


    if(
        [85,86].includes(code)
    )
        return "Χιονομπόρες";


    if(
        [95,96,99].includes(code)
    )
        return "Καταιγίδα";


    return "Μεταβλητός καιρός";

}


/* =====================================
   WIND DIRECTION
===================================== */

function windDirection(degrees){

    if(
        degrees === null ||
        degrees === undefined ||
        isNaN(degrees)
    ){

        return "—";

    }


    const directions = [

        "Β",
        "ΒΒΑ",
        "ΒΑ",
        "ΑΒΑ",
        "Α",
        "ΑΝΑ",
        "ΝΑ",
        "ΝΝΑ",
        "Ν",
        "ΝΝΔ",
        "ΝΔ",
        "ΔΝΔ",
        "Δ",
        "ΔΒΔ",
        "ΒΔ",
        "ΒΒΔ"

    ];


    const index =
        Math.round(
            degrees / 22.5
        ) % 16;


    return directions[index];

}


/* =====================================
   SEARCH CITY
===================================== */

async function searchCity(){

    const city =
        document
        .getElementById("cityInput")
        .value
        .trim();


    if(!city)
        return;


    closeHistory();

    closeHourly();


    document
        .getElementById("current")
        .innerHTML = "";


    document
        .getElementById("forecast")
        .innerHTML =

        `<div class="loading">

            Αναζήτηση πόλης...

         </div>`;


    try{

        const url =

            OPEN_METEO_GEOCODING +

            "?name=" +
            encodeURIComponent(city) +

            "&count=1" +

            "&language=el" +

            "&format=json";


        const response =
            await fetch(url);


        if(!response.ok){

            throw new Error(
                "Δεν ήταν δυνατή η αναζήτηση."
            );

        }


        const geo =
            await response.json();


        if(
            !geo.results ||
            !geo.results.length
        ){

            throw new Error(
                "Δεν βρέθηκε η πόλη."
            );

        }


        const place =
            geo.results[0];


        locationData = {

            name:
                place.name ||
                city,

            latitude:
                place.latitude,

            longitude:
                place.longitude,

            country:
                place.country ||
                "",

            countryCode:
                place.country_code ||
                ""

        };


        await loadWeather();


    }catch(error){

        console.error(error);


        document
            .getElementById("current")
            .innerHTML = "";


        document
            .getElementById("forecast")
            .innerHTML =

            `<div class="loading">

                Σφάλμα φόρτωσης δεδομένων.

                <br><br>

                ${error.message || ""}

             </div>`;

    }

}


/* =====================================
   LOAD WEATHER
===================================== */

async function loadWeather(){

    if(!locationData){

        return;

    }


    document
        .getElementById("current")
        .innerHTML =

        `<div class="current">

            <div class="loading">

                Φόρτωση καιρού...

            </div>

        </div>`;


    document
        .getElementById("forecast")
        .innerHTML =

        `<div class="loading">

            Φόρτωση πρόγνωσης...

        </div>`;


    try{

        const url =

            OPEN_METEO_FORECAST +

            "?latitude=" +
            encodeURIComponent(
                locationData.latitude
            ) +

            "&longitude=" +
            encodeURIComponent(
                locationData.longitude
            ) +

            "&current=" +

            "temperature_2m," +
            "relative_humidity_2m," +
            "apparent_temperature," +
            "weather_code," +
            "wind_speed_10m," +
            "wind_direction_10m," +
            "is_day," +
            "cloud_cover" +

            "&hourly=" +

            "temperature_2m," +
            "apparent_temperature," +
            "precipitation_probability," +
            "snowfall," +
            "weather_code," +
            "cloud_cover," +
            "wind_speed_10m," +
            "wind_direction_10m," +
            "is_day" +

            "&daily=" +

            "weather_code," +
            "temperature_2m_max," +
            "temperature_2m_min," +
            "precipitation_probability_max," +
            "snowfall_sum," +
            "wind_speed_10m_max," +
            "cloud_cover_mean" +

            "&forecast_days=15" +

            "&models=best_match" +

            "&temperature_unit=celsius" +

            "&wind_speed_unit=kmh" +

            "&precipitation_unit=mm" +

            "&timezone=auto";


        const response =
            await fetch(url);


        if(!response.ok){

            throw new Error(
                "Open-Meteo request failed"
            );

        }


        const data =
            await response.json();


        weatherData =
            data;


        renderCurrent();

        renderForecast();


    }catch(error){

        console.error(error);


        document
            .getElementById("current")
            .innerHTML = "";


        document
            .getElementById("forecast")
            .innerHTML =

            `<div class="loading">

                Δεν ήταν δυνατή η φόρτωση
                των δεδομένων καιρού.

                <br><br>

                ${error.message || ""}

             </div>`;

    }

}


/* =====================================
   CURRENT WEATHER
===================================== */

function renderCurrent(){

    const d =
        weatherData.current;


    const temp =
        Number(
            d.temperature_2m
        );


    const humidity =
        Number(
            d.relative_humidity_2m
        );


    const wind =
        Number(
            d.wind_speed_10m
        );


    const windDir =
        windDirection(
            d.wind_direction_10m
        );


    const feels =
        Number(
            d.apparent_temperature
        );


    const code =
        Number(
            d.weather_code
        );


    const isDay =
        Number(d.is_day) === 1;


    const cloudCover =
        Number(
            d.cloud_cover || 0
        );


    document
        .getElementById("current")
        .innerHTML = `

        <div class="current">

            <h2>

                ${locationData.name}

                <div style="
                    font-size:16px;
                    font-weight:normal;
                    color:#dce5ee;
                    margin-top:7px;
                ">

                    ${countryFlag(
                        locationData.countryCode
                    )}

                    ${locationData.country}

                </div>

            </h2>


            <div class="temperature">

                ${Math.round(temp)}°C

            </div>


            <div class="condition">

                ${weatherIcon(
                    code,
                    isDay,
                    0,
                    0,
                    wind,
                    cloudCover
                )}

                ${weatherText(code)}

            </div>


            <div class="current-grid">


                <div class="current-box">

                    <span>
                        💧 Υγρασία
                    </span>

                    <strong>

                        ${Math.round(humidity)}%

                    </strong>

                </div>


                <div class="current-box">

                    <span>
                        🌬️ Άνεμος
                    </span>

                    <strong>

                        ${Math.round(wind)}
                        km/h
                        —
                        ${windDir}

                    </strong>

                </div>


                <div class="current-box">

                    <span>
                        🌡️ Αίσθηση
                    </span>

                    <strong>

                        ${Math.round(feels)}°C

                    </strong>

                </div>


            </div>

        </div>

    `;

}


/* =====================================
   15 DAYS
===================================== */

function renderForecast(){

    const d =
        weatherData.daily;


    let html = "";


    for(
        let i = 0;
        i < d.time.length;
        i++
    ){

        const date =
            formatDate(
                d.time[i]
            );


        const rain =
            Number(
                d.precipitation_probability_max[i]
                || 0
            );


        const snow =
            Number(
                d.snowfall_sum[i]
                || 0
            );


        const wind =
            Number(
                d.wind_speed_10m_max[i]
                || 0
            );


        const cloudCover =
            Number(
                d.cloud_cover_mean[i]
                || 0
            );


        /*
           ΥΕΤΟΣ:

           Το ποσοστό εμφανίζεται ΠΑΝΤΑ.

           31% και πάνω:
           εμφανίζεται και το αντίστοιχο emoji.

           0–30%:
           εμφανίζεται μόνο το ποσοστό,
           χωρίς emoji υετού.
        */

        let precipitationInfo = "";


        if(rain >= 31){

            if(
                [56,57,66,67].includes(
                    Number(d.weather_code[i])
                )
            ){

                precipitationInfo =
                    `🌨️ ${Math.round(rain)}%`;

            }else if(
                [71,73,75,77,85,86].includes(
                    Number(d.weather_code[i])
                ) ||
                snow > 0
            ){

                precipitationInfo =
                    `❄️ ${Math.round(rain)}%`;

            }else{

                precipitationInfo =
                    `💧 ${Math.round(rain)}%`;

            }

        }else{

            precipitationInfo =
                `${Math.round(rain)}%`;

        }


        html += `

        <div
            class="day"
            onclick="showHourly(${i})"
        >

            <div class="day-name">

                ${date.day}

            </div>


            <div class="date">

                ${date.date}

            </div>


            <div class="icon">

                ${weatherIcon(
                    d.weather_code[i],
                    true,
                    rain,
                    snow,
                    wind,
                    cloudCover
                )}

            </div>


            <div class="max">

                ${Math.round(
                    d.temperature_2m_max[i]
                )}°

            </div>


            <div class="min">

                ${Math.round(
                    d.temperature_2m_min[i]
                )}°

            </div>


            <div class="rain">

                ${precipitationInfo}

            </div>


        </div>

        `;

    }


    document
        .getElementById("forecast")
        .innerHTML =
        html;

}


/* =====================================
   HOURLY
===================================== */

function showHourly(dayIndex){

    const d =
        weatherData.hourly;


    const date =
        weatherData
        .daily
        .time[dayIndex];


    const rows = [];


    for(
        let i = 0;
        i < d.time.length;
        i++
    ){

        if(
            d.time[i].substring(
                0,
                10
            ) === date
        ){

            rows.push(i);

        }

    }


    const formatted =
        formatDate(date);


    document
        .getElementById("hourlyTitle")
        .innerText =

        "Πρόγνωση ανά ώρα — " +

        formatted.day +

        " " +

        formatted.date;


    let html = "";


    rows.forEach(i => {

        const hour =
            d.time[i]
            .substring(11,16);


        const temp =
            Math.round(
                Number(
                    d.temperature_2m[i]
                )
            );


        const feels =
            Math.round(
                Number(
                    d.apparent_temperature[i]
                )
            );


        const rain =
            Math.round(
                Number(
                    d.precipitation_probability[i]
                    || 0
                )
            );


        const snowfall =
            Number(
                d.snowfall[i]
                || 0
            );


        const wind =
            Math.round(
                Number(
                    d.wind_speed_10m[i]
                    || 0
                )
            );


        const windDir =
            windDirection(
                d.wind_direction_10m[i]
            );


        const clouds =
            Math.round(
                Number(
                    d.cloud_cover[i]
                    || 0
                )
            );


        const code =
            Number(
                d.weather_code[i]
            );


        const isDay =
            Number(
                d.is_day[i]
            ) === 1;


        const icon =
            weatherIcon(
                code,
                isDay,
                rain,
                snowfall,
                wind,
                clouds
            );


        /*
           ΥΕΤΟΣ:

           Το ποσοστό εμφανίζεται ΠΑΝΤΑ.

           31% και πάνω:
           εμφανίζεται και emoji.

           0–30%:
           κανένα emoji υετού.
        */

        let precipitationHTML = "";


        if(rain >= 31){

            if(
                [56,57,66,67].includes(code)
            ){

                precipitationHTML =
                    `🌨️ ${rain}%`;

            }else if(
                [71,73,75,77,85,86].includes(code) ||
                snowfall > 0
            ){

                precipitationHTML =
                    `❄️ ${rain}%`;

            }else{

                precipitationHTML =
                    `💧 ${rain}%`;

            }

        }else{

            precipitationHTML =
                `${rain}%`;

        }


        html += `

        <div class="hour">


            <div class="hour-time">

                ${hour}

            </div>


            <div class="hour-icon">

                ${icon}

            </div>


            <div class="hour-data">

                🌡️

                <b>
                    ${temp}°
                </b>

                <br>

                Αίσθηση
                ${feels}°

            </div>


            <div class="hour-data">

                ${precipitationHTML}

            </div>


            <div class="hour-data">

                ☁️
                ${clouds}%

            </div>


            <div class="hour-data">

                🌬️
                ${wind} km/h

                <br>

                Διεύθυνση:
                <b>
                    ${windDir}
                </b>

            </div>


        </div>

        `;

    });


    if(!html){

        html = `

            <div class="loading">

                Δεν υπάρχουν διαθέσιμα
                ωριαία δεδομένα.

            </div>

        `;

    }


    document
        .getElementById("hourly")
        .innerHTML =
        html;


    const section =
        document
        .getElementById(
            "hourlySection"
        );


    section.style.display =
        "block";


    section.scrollIntoView({

        behavior:"smooth",

        block:"start"

    });

}


function closeHourly(){

    document
        .getElementById(
            "hourlySection"
        )
        .style.display =
        "none";

}


/* =====================================
   ENTER SEARCH
===================================== */

document
    .getElementById("cityInput")
    .addEventListener(
        "keydown",
        function(e){

            if(e.key === "Enter"){

                searchCity();

            }

        }
    );


/* =====================================
   START
===================================== */

searchCity();


</script>


</body>

</html>
