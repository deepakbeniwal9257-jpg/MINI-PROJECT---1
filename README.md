# MINI-PROJECT---1
```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>ResumeCraft | Smart Resume Builder</title>

<style>

/* =========================================================
   GLOBAL
========================================================= */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:"Segoe UI",Arial,sans-serif;
}

:root{
    --primary:#7c3aed;
    --secondary:#06b6d4;
    --bg:#f1f5f9;
    --card:#ffffff;
    --text:#172033;
    --muted:#64748b;
    --border:#e2e8f0;
    --input:#ffffff;
    --resume:#ffffff;
    --shadow:0 15px 40px rgba(15,23,42,.10);
}

body.dark{
    --bg:#080d1d;
    --card:#10172a;
    --text:#f8fafc;
    --muted:#94a3b8;
    --border:#24304a;
    --input:#151e34;
    --resume:#ffffff;
    --shadow:0 15px 40px rgba(0,0,0,.30);
}

html{
    scroll-behavior:smooth;
}

body{
    background:var(--bg);
    color:var(--text);
    transition:.3s;
}

/* =========================================================
   HEADER
========================================================= */

header{
    height:72px;
    background:var(--card);
    border-bottom:1px solid var(--border);
    display:flex;
    align-items:center;
    justify-content:space-between;
    padding:0 28px;
    position:sticky;
    top:0;
    z-index:1000;
}

.logo{
    display:flex;
    align-items:center;
    gap:11px;
}

.logo-icon{
    width:42px;
    height:42px;
    border-radius:12px;
    display:grid;
    place-items:center;
    color:white;
    font-size:21px;
    background:linear-gradient(135deg,var(--primary),#a855f7);
    box-shadow:0 8px 20px rgba(124,58,237,.3);
}

.logo h1{
    font-size:20px;
    line-height:1;
}

.logo p{
    color:var(--muted);
    font-size:11px;
    margin-top:4px;
}

.header-actions{
    display:flex;
    align-items:center;
    gap:9px;
}

.btn{
    border:none;
    border-radius:10px;
    padding:10px 15px;
    font-weight:700;
    cursor:pointer;
    transition:.2s;
}

.btn:hover{
    transform:translateY(-2px);
}

.btn-primary{
    color:white;
    background:linear-gradient(135deg,var(--primary),#9333ea);
    box-shadow:0 7px 18px rgba(124,58,237,.25);
}

.btn-soft{
    color:var(--primary);
    background:rgba(124,58,237,.10);
}

.btn-danger{
    color:#ef4444;
    background:#fee2e2;
}

.theme-toggle{
    width:44px;
    height:38px;
    border:none;
    border-radius:10px;
    cursor:pointer;
    background:var(--bg);
    color:var(--text);
    font-size:17px;
}

/* =========================================================
   LAYOUT
========================================================= */

.app{
    display:grid;
    grid-template-columns:210px 1fr 530px;
    min-height:calc(100vh - 72px);
}

/* =========================================================
   SIDEBAR
========================================================= */

.sidebar{
    background:var(--card);
    border-right:1px solid var(--border);
    padding:25px 13px;
    position:sticky;
    top:72px;
    height:calc(100vh - 72px);
}

.nav-title{
    color:var(--muted);
    text-transform:uppercase;
    letter-spacing:1px;
    font-size:10px;
    font-weight:800;
    padding:0 13px 10px;
}

.nav-item{
    display:flex;
    align-items:center;
    gap:12px;
    padding:12px 13px;
    margin-bottom:5px;
    border-radius:11px;
    cursor:pointer;
    color:var(--muted);
    font-size:13px;
    font-weight:600;
    transition:.2s;
}

.nav-item:hover{
    background:rgba(124,58,237,.08);
    color:var(--primary);
}

.nav-item.active{
    background:linear-gradient(
        135deg,
        rgba(124,58,237,.18),
        rgba(168,85,247,.08)
    );
    color:var(--primary);
}

.nav-icon{
    width:25px;
    text-align:center;
    font-size:17px;
}

.sidebar-card{
    margin:30px 5px 0;
    border-radius:15px;
    padding:17px;
    color:white;
    background:linear-gradient(
        145deg,
        #4c1d95,
        #7c3aed,
        #2563eb
    );
    overflow:hidden;
    position:relative;
}

.sidebar-card h3{
    font-size:14px;
    margin-bottom:7px;
}

.sidebar-card p{
    font-size:11px;
    line-height:1.5;
    opacity:.85;
}

.rocket{
    font-size:35px;
    text-align:right;
    margin-bottom:5px;
}

/* =========================================================
   EDITOR
========================================================= */

.editor{
    padding:30px;
    overflow-y:auto;
}

.editor-top{
    display:flex;
    justify-content:space-between;
    align-items:flex-start;
    margin-bottom:23px;
}

.editor-top h2{
    font-size:27px;
}

.editor-top p{
    color:var(--muted);
    margin-top:5px;
    font-size:13px;
}

.score-card{
    background:var(--card);
    border:1px solid var(--border);
    border-radius:17px;
    padding:18px;
    margin-bottom:20px;
    box-shadow:var(--shadow);
}

.score-row{
    display:flex;
    align-items:center;
    gap:18px;
}

.score-circle{
    width:72px;
    height:72px;
    border-radius:50%;
    display:grid;
    place-items:center;
    flex-shrink:0;
    background:
        conic-gradient(
            var(--secondary) var(--score,0%),
            var(--border) 0
        );
    position:relative;
}

.score-circle::after{
    content:"";
    position:absolute;
    width:58px;
    height:58px;
    border-radius:50%;
    background:var(--card);
}

.score-number{
    position:relative;
    z-index:2;
    font-size:16px;
    font-weight:800;
}

.score-info{
    flex:1;
}

.score-info strong{
    font-size:15px;
}

.score-info p{
    color:var(--muted);
    font-size:12px;
    margin-top:5px;
}

.progress{
    height:8px;
    background:var(--border);
    border-radius:20px;
    overflow:hidden;
    margin-top:12px;
}

.progress-bar{
    height:100%;
    width:0;
    border-radius:20px;
    background:linear-gradient(
        90deg,
        #06b6d4,
        #7c3aed,
        #ec4899
    );
    transition:width .5s ease;
}

/* =========================================================
   CARDS
========================================================= */

.form-card{
    background:var(--card);
    border:1px solid var(--border);
    border-radius:17px;
    padding:21px;
    margin-bottom:18px;
    box-shadow:var(--shadow);
}

.card-heading{
    display:flex;
    align-items:center;
    justify-content:space-between;
    margin-bottom:19px;
}

.card-title{
    display:flex;
    align-items:center;
    gap:10px;
}

.card-title-icon{
    width:34px;
    height:34px;
    border-radius:9px;
    display:grid;
    place-items:center;
    background:rgba(124,58,237,.12);
    color:var(--primary);
}

.card-title h3{
    font-size:16px;
}

.card-title p{
    font-size:11px;
    color:var(--muted);
    margin-top:2px;
}

.step{
    color:var(--primary);
    font-size:11px;
    font-weight:800;
}

/* =========================================================
   FORM
========================================================= */

.grid{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:14px;
}

.full{
    grid-column:1/-1;
}

.field{
    margin-bottom:3px;
}

label{
    display:block;
    color:var(--muted);
    font-size:11px;
    font-weight:800;
    margin-bottom:6px;
}

input,
textarea,
select{
    width:100%;
    border:1px solid var(--border);
    background:var(--input);
    color:var(--text);
    padding:11px 12px;
    border-radius:9px;
    outline:none;
    font-size:13px;
    transition:.2s;
}

input:focus,
textarea:focus,
select:focus{
    border-color:var(--primary);
    box-shadow:0 0 0 3px rgba(124,58,237,.10);
}

textarea{
    resize:vertical;
    min-height:90px;
}

.char-count{
    text-align:right;
    color:var(--muted);
    font-size:10px;
    margin-top:4px;
}

/* =========================================================
   DYNAMIC ITEMS
========================================================= */

.dynamic-item{
    border:1px dashed var(--border);
    border-radius:12px;
    padding:15px;
    margin-bottom:12px;
    position:relative;
    background:rgba(148,163,184,.025);
}

.remove{
    position:absolute;
    right:10px;
    top:10px;
    border:none;
    border-radius:7px;
    padding:5px 8px;
    font-size:10px;
    cursor:pointer;
    color:#ef4444;
    background:#fee2e2;
}

.add{
    width:100%;
    border:1px dashed var(--primary);
    background:rgba(124,58,237,.06);
    color:var(--primary);
    padding:10px;
    border-radius:9px;
    cursor:pointer;
    font-weight:800;
}

/* =========================================================
   SKILLS
========================================================= */

.skill-input{
    display:flex;
    gap:8px;
}

.skill-input input{
    flex:1;
}

.skill-add{
    background:var(--primary);
    color:white;
    border:none;
    border-radius:9px;
    width:44px;
    cursor:pointer;
    font-size:18px;
}

.skill-list{
    display:flex;
    flex-wrap:wrap;
    gap:7px;
    margin-top:12px;
}

.skill-tag{
    background:rgba(124,58,237,.11);
    color:var(--primary);
    padding:6px 10px;
    border-radius:20px;
    font-size:11px;
    font-weight:700;
    cursor:pointer;
}

.skill-tag span{
    margin-left:5px;
}

/* =========================================================
   FUN FEATURES
========================================================= */

.fun-box{
    border-radius:13px;
    padding:15px;
    background:linear-gradient(
        135deg,
        rgba(124,58,237,.10),
        rgba(6,182,212,.08)
    );
    border:1px solid rgba(124,58,237,.15);
}

.fun-box p{
    color:var(--muted);
    font-size:11px;
    margin-bottom:10px;
}

.quick-actions{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:8px;
}

.quick{
    border:none;
    padding:10px;
    border-radius:9px;
    cursor:pointer;
    font-size:11px;
    font-weight:800;
    color:var(--text);
    background:var(--bg);
}

.quick:hover{
    background:rgba(124,58,237,.13);
}

/* =========================================================
   PREVIEW
========================================================= */

.preview-panel{
    background:#dbe3ef;
    padding:22px;
    overflow:auto;
    position:sticky;
    top:72px;
    height:calc(100vh - 72px);
}

body.dark .preview-panel{
    background:#0b1120;
}

.preview-top{
    display:flex;
    justify-content:space-between;
    align-items:center;
    margin-bottom:15px;
}

.preview-top h3{
    font-size:14px;
}

.template-buttons{
    display:flex;
    gap:5px;
}

.template-btn{
    border:none;
    padding:7px 10px;
    border-radius:8px;
    cursor:pointer;
    font-size:10px;
    font-weight:700;
    background:white;
}

.template-btn.active{
    background:var(--primary);
    color:white;
}

.resume{
    width:100%;
    max-width:760px;
    min-height:1060px;
    margin:auto;
    background:white;
    color:#1e293b;
    padding:43px;
    box-shadow:0 15px 45px rgba(15,23,42,.22);
    transition:.3s;
}

/* =========================================================
   RESUME
========================================================= */

.resume-header{
    display:grid;
    grid-template-columns:1fr auto;
    gap:20px;
    padding-bottom:18px;
    border-bottom:2px solid var(--primary);
}

.resume-name{
    font-size:31px;
    font-weight:900;
    letter-spacing:-1px;
}

.resume-role{
    color:var(--primary);
    font-weight:700;
    font-size:14px;
    margin-top:3px;
}

.contact{
    display:flex;
    flex-wrap:wrap;
    gap:8px 15px;
    margin-top:12px;
    font-size:10px;
    color:#64748b;
}

.resume-section{
    margin-top:21px;
}

.resume-section h4{
    font-size:12px;
    text-transform:uppercase;
    letter-spacing:1.4px;
    color:var(--primary);
    border-bottom:1px solid #e2e8f0;
    padding-bottom:5px;
    margin-bottom:9px;
}

.resume-section p{
    font-size:10.8px;
    line-height:1.65;
    color:#334155;
}

.resume-item{
    margin-bottom:12px;
}

.resume-item-title{
    font-weight:800;
    font-size:12px;
}

.resume-item-sub{
    font-size:10px;
    color:#64748b;
    margin-top:2px;
}

.resume-item-desc{
    margin-top:4px;
}

.resume-skills{
    display:flex;
    flex-wrap:wrap;
    gap:5px;
}

.resume-skill{
    background:#eef2ff;
    color:#4f46e5;
    border-radius:15px;
    padding:4px 8px;
    font-size:9px;
    font-weight:700;
}

/* =========================================================
   RESUME THEMES
========================================================= */

.resume.classic .resume-header{
    border-bottom:3px solid #111827;
}

.resume.classic .resume-role,
.resume.classic .resume-section h4{
    color:#111827;
}

.resume.creative .resume-header{
    border-bottom:none;
    background:linear-gradient(135deg,#ede9fe,#cffafe);
    padding:20px;
    border-radius:12px;
}

.resume.creative .resume-name{
    color:#4c1d95;
}

.resume.creative .resume-section h4{
    background:#f5f3ff;
    padding:6px 8px;
    border:none;
    border-radius:5px;
}

/* =========================================================
   PREVIEW ACTIONS
========================================================= */

.preview-actions{
    max-width:760px;
    margin:14px auto 0;
    display:grid;
    grid-template-columns:1fr 1fr 1fr;
    gap:8px;
}

.preview-action{
    padding:11px;
    border:none;
    border-radius:9px;
    cursor:pointer;
    font-weight:800;
    background:white;
    color:#334155;
}

.preview-action.primary{
    background:var(--primary);
    color:white;
}

/* =========================================================
   TIPS
========================================================= */

.tip-list{
    display:grid;
    grid-template-columns:repeat(2,1fr);
    gap:8px;
    margin-top:10px;
}

.tip{
    padding:10px;
    border-radius:9px;
    background:var(--bg);
    font-size:10px;
}

.tip b{
    display:block;
    margin-bottom:3px;
}

/* =========================================================
   TOAST
========================================================= */

.toast{
    position:fixed;
    right:25px;
    bottom:25px;
    background:#111827;
    color:white;
    padding:13px 18px;
    border-radius:10px;
    font-size:12px;
    font-weight:700;
    opacity:0;
    transform:translateY(20px);
    pointer-events:none;
    transition:.3s;
    z-index:9999;
}

.toast.show{
    opacity:1;
    transform:translateY(0);
}

/* =========================================================
   CELEBRATION
========================================================= */

.celebrate{
    position:fixed;
    inset:0;
    display:none;
    place-items:center;
    background:rgba(15,23,42,.72);
    backdrop-filter:blur(8px);
    z-index:5000;
}

.celebrate.show{
    display:grid;
}

.celebrate-card{
    background:white;
    color:#172033;
    padding:35px;
    width:min(400px,90%);
    text-align:center;
    border-radius:20px;
    animation:pop .4s ease;
}

.celebrate-icon{
    font-size:55px;
}

.celebrate-card h2{
    margin:10px 0;
}

.celebrate-card p{
    color:#64748b;
    font-size:13px;
    margin-bottom:18px;
}

@keyframes pop{
    from{
        transform:scale(.7);
        opacity:0;
    }
    to{
        transform:scale(1);
        opacity:1;
    }
}

/* =========================================================
   RESPONSIVE
========================================================= */

@media(max-width:1250px){

    .app{
        grid-template-columns:180px 1fr;
    }

    .preview-panel{
        grid-column:1/-1;
        position:relative;
        height:auto;
    }

}

@media(max-width:850px){

    .app{
        display:block;
    }

    .sidebar{
        display:none;
    }

    .editor{
        padding:18px;
    }

    .preview-panel{
        padding:15px;
    }

    header{
        padding:0 15px;
    }

    .header-actions .btn-soft{
        display:none;
    }

}

@media(max-width:600px){

    .grid{
        grid-template-columns:1fr;
    }

    .full{
        grid-column:auto;
    }

    .editor-top{
        display:block;
    }

    .header-actions{
        gap:4px;
    }

    .header-actions .btn{
        padding:8px;
        font-size:10px;
    }

    .resume{
        padding:25px;
    }

    .resume-name{
        font-size:24px;
    }

    .quick-actions{
        grid-template-columns:1fr;
    }

}

/* =========================================================
   PRINT
========================================================= */

@media print{

    body{
        background:white !important;
    }

    header,
    .sidebar,
    .editor,
    .preview-top,
    .preview-actions{
        display:none !important;
    }

    .app{
        display:block;
    }

    .preview-panel{
        background:white !important;
        padding:0;
        height:auto;
    }

    .resume{
        box-shadow:none;
        max-width:none;
        width:100%;
        min-height:auto;
        margin:0;
    }

}

</style>
</head>


<body>

<!-- =====================================================
     HEADER
===================================================== -->

<header>

    <div class="logo">

        <div class="logo-icon">
            📄
        </div>

        <div>
            <h1>ResumeCraft</h1>
            <p>Build your future 🚀</p>
        </div>

    </div>


    <div class="header-actions">

        <button class="theme-toggle"
                onclick="toggleDark()"
                title="Dark Mode">
            🌙
        </button>

        <button class="btn btn-soft"
                onclick="fillSample()">
            ✨ Sample Data
        </button>

        <button class="btn btn-soft"
                onclick="saveResume()">
            💾 Save
        </button>

        <button class="btn btn-danger"
                onclick="resetResume()">
            ↻ Reset
        </button>

    </div>

</header>


<!-- =====================================================
     MAIN APP
===================================================== -->

<div class="app">


<!-- =====================================================
     SIDEBAR
===================================================== -->

<aside class="sidebar">

    <div class="nav-title">
        Resume Sections
    </div>


    <div class="nav-item active"
         onclick="scrollToSection('personal')">

        <span class="nav-icon">👤</span>
        Personal Info

    </div>


    <div class="nav-item"
         onclick="scrollToSection('education')">

        <span class="nav-icon">🎓</span>
        Education

    </div>


    <div class="nav-item"
         onclick="scrollToSection('experience')">

        <span class="nav-icon">💼</span>
        Experience

    </div>


    <div class="nav-item"
         onclick="scrollToSection('skills')">

        <span class="nav-icon">⚡</span>
        Skills

    </div>


    <div class="nav-item"
         onclick="scrollToSection('projects')">

        <span class="nav-icon">🚀</span>
        Projects

    </div>


    <div class="nav-item"
         onclick="scrollToSection('certifications')">

        <span class="nav-icon">🏆</span>
        Certifications

    </div>


    <div class="nav-item"
         onclick="scrollToSection('summary')">

        <span class="nav-icon">📝</span>
        Summary

    </div>


    <div class="nav-item"
         onclick="scrollToSection('theme')">

        <span class="nav-icon">🎨</span>
        Theme

    </div>


    <div class="sidebar-card">

        <div class="rocket">
            🚀
        </div>

        <h3>
            Small steps today,
            big dreams tomorrow!
        </h3>

        <p>
            Build a resume that shows
            what you're capable of.
        </p>

    </div>

</aside>


<!-- =====================================================
     EDITOR
===================================================== -->

<main class="editor">


    <div class="editor-top">

        <div>

            <h2>
                Build your resume
            </h2>

            <p>
                Tell your story. We'll make it look amazing.
            </p>

        </div>

    </div>


    <!-- SCORE -->

    <div class="score-card">

        <div class="score-row">

            <div class="score-circle"
                 id="scoreCircle">

                <span class="score-number"
                      id="scoreNumber">
                    0%
                </span>

            </div>


            <div class="score-info">

                <strong id="scoreTitle">
                    Let's get started!
                </strong>

                <p id="scoreMessage">
                    Complete your resume sections to increase your score.
                </p>

                <div class="progress">

                    <div class="progress-bar"
                         id="progressBar">
                    </div>

                </div>

            </div>

        </div>

    </div>


    <!-- =================================================
         PERSONAL INFORMATION
    ================================================= -->

    <section class="form-card"
             id="personal">

        <div class="card-heading">

            <div class="card-title">

                <div class="card-title-icon">
                    👤
                </div>

                <div>
                    <h3>Personal Information</h3>
                    <p>Let employers know who you are</p>
                </div>

            </div>

            <span class="step">01</span>

        </div>


        <div class="grid">

            <div class="field">

                <label>FULL NAME *</label>

                <input id="name"
                       placeholder="e.g. Harsh Sharma">

            </div>


            <div class="field">

                <label>PROFESSIONAL TITLE</label>

                <input id="role"
                       placeholder="e.g. B.Tech CSE Student">

            </div>


            <div class="field">

                <label>EMAIL *</label>

                <input id="email"
                       type="email"
                       placeholder="you@example.com">

            </div>


            <div class="field">

                <label>PHONE</label>

                <input id="phone"
                       placeholder="+91 98765 43210">

            </div>


            <div class="field">

                <label>LOCATION</label>

                <input id="location"
                       placeholder="Delhi, India">

            </div>


            <div class="field">

                <label>LINKEDIN</label>

                <input id="linkedin"
                       placeholder="linkedin.com/in/username">

            </div>


            <div class="field full">

                <label>GITHUB</label>

                <input id="github"
                       placeholder="github.com/username">

            </div>

        </div>

    </section>


    <!-- =================================================
         SUMMARY
    ================================================= -->

    <section class="form-card"
             id="summary">

        <div class="card-heading">

            <div class="card-title">

                <div class="card-title-icon">
                    📝
                </div>

                <div>
                    <h3>Professional Summary</h3>
                    <p>Make a great first impression</p>
                </div>

            </div>

            <button class="btn btn-primary"
                    onclick="surpriseMe()">
                ✨ Surprise Me
            </button>

        </div>


        <textarea id="summaryInput"
                  maxlength="300"
                  placeholder="Write a short and compelling summary about yourself..."></textarea>

        <div class="char-count">
            <span id="charCount">0</span>/300
        </div>

    </section>


    <!-- =================================================
         EDUCATION
    ================================================= -->

    <section class="form-card"
             id="education">

        <div class="card-heading">

            <div class="card-title">

                <div class="card-title-icon">
                    🎓
                </div>

                <div>
                    <h3>Education</h3>
                    <p>Your academic journey</p>
                </div>

            </div>

            <span class="step">02</span>

        </div>


        <div id="educationContainer">

            <div class="dynamic-item education-item">

                <button class="remove"
                        onclick="removeItem(this)">
                    Remove
                </button>

                <div class="grid">

                    <div class="field">

                        <label>DEGREE</label>

                        <input class="edu-degree"
                               placeholder="B.Tech Computer Science">

                    </div>


                    <div class="field">

                        <label>COLLEGE / UNIVERSITY</label>

                        <input class="edu-college"
                               placeholder="ABC Engineering College">

                    </div>


                    <div class="field">

                        <label>YEAR</label>

                        <input class="edu-year"
                               placeholder="2024 - 2028">

                    </div>


                    <div class="field">

                        <label>CGPA / PERCENTAGE</label>

                        <input class="edu-score"
                               placeholder="8.5 CGPA">

                    </div>

                </div>

            </div>

        </div>


        <button class="add"
                onclick="addEducation()">
            + Add Education
        </button>

    </section>


    <!-- =================================================
         EXPERIENCE
    ================================================= -->

    <section class="form-card"
             id="experience">

        <div class="card-heading">

            <div class="card-title">

                <div class="card-title-icon">
                    💼
                </div>

                <div>
                    <h3>Experience</h3>
                    <p>Internships and work experience</p>
                </div>

            </div>

            <span class="step">03</span>

        </div>


        <div id="experienceContainer">

            <div class="dynamic-item experience-item">

                <button class="remove"
                        onclick="removeItem(this)">
                    Remove
                </button>

                <div class="grid">

                    <div class="field">

                        <label>JOB TITLE</label>

                        <input class="exp-title"
                               placeholder="Web Development Intern">

                    </div>


                    <div class="field">

                        <label>COMPANY</label>

                        <input class="exp-company"
                               placeholder="XYZ Technologies">

                    </div>


                    <div class="field">

                        <label>DURATION</label>

                        <input class="exp-duration"
                               placeholder="May 2026 - July 2026">

                    </div>


                    <div class="field full">

                        <label>DESCRIPTION</label>

                        <textarea class="exp-desc"
                                  placeholder="Describe your responsibilities and achievements..."></textarea>

                    </div>

                </div>

            </div>

        </div>


        <button class="add"
                onclick="addExperience()">
            + Add Experience
        </button>

    </section>


    <!-- =================================================
         SKILLS
    ================================================= -->

    <section class="form-card"
             id="skills">

        <div class="card-heading">

            <div class="card-title">

                <div class="card-title-icon">
                    ⚡
                </div>

                <div>
                    <h3>Skills</h3>
                    <p>Showcase your strengths</p>
                </div>

            </div>

            <span class="step">04</span>

        </div>


        <div class="skill-input">

            <input id="skillInput"
                   placeholder="Type a skill and press +">

            <button class="skill-add"
                    onclick="addSkill()">
                +
            </button>

        </div>


        <div class="skill-list"
             id="skillList">
        </div>

    </section>


    <!-- =================================================
         PROJECTS
    ================================================= -->

    <section class="form-card"
             id="projects">

        <div class="card-heading">

            <div class="card-title">

                <div class="card-title-icon">
                    🚀
                </div>

                <div>
                    <h3>Projects</h3>
                    <p>Show what you can build</p>
                </div>

            </div>

            <span class="step">05</span>

        </div>


        <div id="projectContainer">

            <div class="dynamic-item project-item">

                <button class="remove"
                        onclick="removeItem(this)">
                    Remove
                </button>

                <div class="grid">

                    <div class="field">

                        <label>PROJECT NAME</label>

                        <input class="project-name"
                               placeholder="Campus Flow AI">

                    </div>


                    <div class="field">

                        <label>TECHNOLOGIES</label>

                        <input class="project-tech"
                               placeholder="Python, Flask, SQLite">

                    </div>


                    <div class="field full">

                        <label>DESCRIPTION</label>

                        <textarea class="project-desc"
                                  placeholder="Explain what the project does and what problem it solves..."></textarea>

                    </div>


                    <div class="field full">

                        <label>PROJECT LINK</label>

                        <input class="project-link"
                               placeholder="github.com/username/project">

                    </div>

                </div>

            </div>

        </div>


        <button class="add"
                onclick="addProject()">
            + Add Project
        </button>

    </section>


    <!-- =================================================
         CERTIFICATIONS
    ================================================= -->

    <section class="form-card"
             id="certifications">

        <div class="card-heading">

            <div class="card-title">

                <div class="card-title-icon">
                    🏆
                </div>

                <div>
                    <h3>Certifications & Achievements</h3>
                    <p>Highlight your accomplishments</p>
                </div>

            </div>

            <span class="step">06</span>

        </div>


        <textarea id="certificationsInput"
                  placeholder="Python Certification&#10;Hackathon Finalist&#10;Coding Contest Winner"></textarea>

    </section>


    <!-- =================================================
         THEME
    ================================================= -->

    <section class="form-card"
             id="theme">

        <div class="card-heading">

            <div class="card-title">

                <div class="card-title-icon">
                    🎨
                </div>

                <div>
                    <h3>Resume Style</h3>
                    <p>Make it yours</p>
                </div>

            </div>

            <span class="step">07</span>

        </div>


        <div class="templates">

            <button class="btn btn-primary"
                    onclick="setColor('#7c3aed')">
                Purple
            </button>

            <button class="btn btn-soft"
                    onclick="setColor('#0f766e')">
                Green
            </button>

            <button class="btn btn-soft"
                    onclick="setColor('#2563eb')">
                Blue
            </button>

            <button class="btn btn-soft"
                    onclick="setColor('#db2777')">
                Pink
            </button>

            <button class="btn btn-soft"
                    onclick="setColor('#ea580c')">
                Orange
            </button>

        </div>

    </section>


    <!-- =================================================
         FUN FEATURES
    ================================================= -->

    <section class="form-card">

        <div class="card-heading">

            <div class="card-title">

                <div class="card-title-icon">
                    ✨
                </div>

                <div>
                    <h3>Quick Actions</h3>
                    <p>Build faster</p>
                </div>

            </div>

        </div>


        <div class="fun-box">

            <p>
                Not sure what to write? Try one of these.
            </p>


            <div class="quick-actions">

                <button class="quick"
                        onclick="surpriseMe()">
                    ✨ Generate Summary
                </button>

                <button class="quick"
                        onclick="fillSample()">
                    🧪 Fill Sample Data
                </button>

                <button class="quick"
                        onclick="showTips()">
                    💡 Resume Tips
                </button>

            </div>

        </div>


        <div class="tip-list"
             id="tips"
             style="display:none;">

            <div class="tip">
                <b>🎯 Be Specific</b>
                Use numbers and measurable achievements.
            </div>

            <div class="tip">
                <b>💻 Add Projects</b>
                Projects are important for freshers.
            </div>

            <div class="tip">
                <b>⚡ Keep It Short</b>
                Try to keep your resume 1–2 pages.
            </div>

            <div class="tip">
                <b>🔑 Keywords</b>
                Match skills with the job description.
            </div>

        </div>

    </section>


</main>


<!-- =====================================================
     PREVIEW
===================================================== -->

<section class="preview-panel">


    <div class="preview-top">

        <h3>
            👁️ Live Preview
        </h3>


        <div class="template-buttons">

            <button class="template-btn active"
                    onclick="template('modern',this)">
                Modern
            </button>

            <button class="template-btn"
                    onclick="template('classic',this)">
                Classic
            </button>

            <button class="template-btn"
                    onclick="template('creative',this)">
                Creative
            </button>

        </div>

    </div>


    <!-- =================================================
         RESUME
    ================================================= -->

    <div class="resume"
         id="resume">


        <!-- HEADER -->

        <div class="resume-header">

            <div>

                <div class="resume-name"
                     id="previewName">
                    Your Name
                </div>

                <div class="resume-role"
                     id="previewRole">
                    B.Tech Computer Science Student
                </div>


                <div class="contact">

                    <span id="previewEmail">
                        📧 email@example.com
                    </span>

                    <span id="previewPhone">
                        📱 +91 XXXXX XXXXX
                    </span>

                    <span id="previewLocation">
                        📍 India
                    </span>

                    <span id="previewLinkedin">
                        🔗 LinkedIn
                    </span>

                    <span id="previewGithub">
                        💻 GitHub
                    </span>

                </div>

            </div>

        </div>


        <!-- SUMMARY -->

        <div class="resume-section">

            <h4>
                Professional Summary
            </h4>

            <p id="previewSummary">
                Your professional summary will appear here.
            </p>

        </div>


        <!-- EDUCATION -->

        <div class="resume-section">

            <h4>
                Education
            </h4>

            <div id="previewEducation">

                <div class="resume-item">

                    <div class="resume-item-title">
                        Your Degree
                    </div>

                    <div class="resume-item-sub">
                        Your College | Year
                    </div>

                </div>

            </div>

        </div>


        <!-- EXPERIENCE -->

        <div class="resume-section">

            <h4>
                Experience
            </h4>

            <div id="previewExperience">

                <div class="resume-item">

                    <div class="resume-item-title">
                        Your Experience
                    </div>

                    <div class="resume-item-sub">
                        Company | Duration
                    </div>

                    <p>
                        Your experience description.
                    </p>

                </div>

            </div>

        </div>


        <!-- SKILLS -->

        <div class="resume-section">

            <h4>
                Skills
            </h4>

            <div class="resume-skills"
                 id="previewSkills">

                <span class="resume-skill">
                    Your Skills
                </span>

            </div>

        </div>


        <!-- PROJECTS -->

        <div class="resume-section">

            <h4>
                Projects
            </h4>

            <div id="previewProjects">

                <div class="resume-item">

                    <div class="resume-item-title">
                        Your Project
                    </div>

                    <div class="resume-item-sub">
                        Technologies
                    </div>

                    <p class="resume-item-desc">
                        Your project description.
                    </p>

                </div>

            </div>

        </div>


        <!-- CERTIFICATIONS -->

        <div class="resume-section">

            <h4>
                Certifications & Achievements
            </h4>

            <p id="previewCertifications">
                Your certifications and achievements.
            </p>

        </div>


    </div>


    <!-- PREVIEW ACTIONS -->

    <div class="preview-actions">

        <button class="preview-action primary"
                onclick="downloadPDF()">
            📄 Download PDF
        </button>

        <button class="preview-action"
                onclick="window.print()">
            🖨️ Print
        </button>

        <button class="preview-action"
                onclick="shareResume()">
            🔗 Share
        </button>

    </div>

</section>

</div>


<!-- =====================================================
     TOAST
===================================================== -->

<div class="toast"
     id="toast">
    Saved successfully!
</div>


<!-- =====================================================
     CELEBRATION
===================================================== -->

<div class="celebrate"
     id="celebrate">

    <div class="celebrate-card">

        <div class="celebrate-icon">
            🏆
        </div>

        <h2>
            Resume Complete!
        </h2>

        <p>
            Amazing! Your resume is ready.
            You're one step closer to your dream opportunity 🚀
        </p>

        <button class="btn btn-primary"
                onclick="closeCelebration()">
            Let's Go! 🎉
        </button>

    </div>

</div>


<script>

/* =========================================================
   GLOBAL
========================================================= */

let skills = [];

let summaries = [

"Motivated and detail-oriented Computer Science student with a passion for building web applications and solving real-world problems. Eager to learn new technologies and contribute to innovative projects.",

"Enthusiastic B.Tech student with strong problem-solving skills and an interest in software development. Passionate about creating useful applications and continuously improving technical abilities.",

"Dedicated Computer Science student with experience in web development and programming. Interested in software engineering, emerging technologies, and building solutions that create real-world impact.",

"Creative and hardworking technology enthusiast with a strong foundation in programming and web development. Looking for opportunities to apply technical knowledge while learning from real-world projects."

];


/* =========================================================
   INPUT LISTENERS
========================================================= */

document
.querySelectorAll("input, textarea")
.forEach(element => {

    element.addEventListener(
        "input",
        updateResume
    );

});


/* =========================================================
   UPDATE RESUME
========================================================= */

function updateResume(){

    const get = id =>
        document.getElementById(id).value.trim();


    document.getElementById("previewName")
        .textContent =
        get("name") || "Your Name";


    document.getElementById("previewRole")
        .textContent =
        get("role") ||
        "B.Tech Computer Science Student";


    document.getElementById("previewEmail")
        .textContent =
        "📧 " +
        (get("email") || "email@example.com");


    document.getElementById("previewPhone")
        .textContent =
        "📱 " +
        (get("phone") || "+91 XXXXX XXXXX");


    document.getElementById("previewLocation")
        .textContent =
        "📍 " +
        (get("location") || "India");


    document.getElementById("previewLinkedin")
        .textContent =
        "🔗 " +
        (get("linkedin") || "LinkedIn");


    document.getElementById("previewGithub")
        .textContent =
        "💻 " +
        (get("github") || "GitHub");


    document.getElementById("previewSummary")
        .textContent =
        get("summaryInput") ||
        "Your professional summary will appear here.";


    document.getElementById("previewCertifications")
        .textContent =
        get("certificationsInput") ||
        "Your certifications and achievements.";


    updateEducation();

    updateExperience();

    updateProjects();

    updateSkillsPreview();

    updateScore();

    updateCharacterCount();

    autoSave();

}


/* =========================================================
   EDUCATION
========================================================= */

function updateEducation(){

    const items =
        document.querySelectorAll(
            ".education-item"
        );

    const preview =
        document.getElementById(
            "previewEducation"
        );

    preview.innerHTML = "";

    items.forEach(item => {

        const degree =
            item.querySelector(
                ".edu-degree"
            ).value.trim();

        const college =
            item.querySelector(
                ".edu-college"
            ).value.trim();

        const year =
            item.querySelector(
                ".edu-year"
            ).value.trim();

        const score =
            item.querySelector(
                ".edu-score"
            ).value.trim();


        if(degree || college){

            preview.innerHTML += `

                <div class="resume-item">

                    <div class="resume-item-title">
                        ${escapeHTML(degree || "Degree")}
                    </div>

                    <div class="resume-item-sub">
                        ${escapeHTML(college || "College")}
                        ${year ? " | " + escapeHTML(year) : ""}
                        ${score ? " | " + escapeHTML(score) : ""}
                    </div>

                </div>

            `;

        }

    });

}


/* =========================================================
   ADD EDUCATION
========================================================= */

function addEducation(){

    const container =
        document.getElementById(
            "educationContainer"
        );


    const item =
        document.createElement("div");

    item.className =
        "dynamic-item education-item";


    item.innerHTML = `

        <button class="remove"
                onclick="removeItem(this)">
            Remove
        </button>

        <div class="grid">

            <div class="field">
                <label>DEGREE</label>
                <input class="edu-degree"
                       placeholder="B.Tech / BCA / MCA">
            </div>

            <div class="field">
                <label>COLLEGE / UNIVERSITY</label>
                <input class="edu-college"
                       placeholder="College Name">
            </div>

            <div class="field">
                <label>YEAR</label>
                <input class="edu-year"
                       placeholder="2024 - 2028">
            </div>

            <div class="field">
                <label>CGPA / PERCENTAGE</label>
                <input class="edu-score"
                       placeholder="8.5 CGPA">
            </div>

        </div>

    `;


    container.appendChild(item);

    addDynamicListeners();

    updateResume();

}


/* =========================================================
   EXPERIENCE
========================================================= */

function updateExperience(){

    const items =
        document.querySelectorAll(
            ".experience-item"
        );

    const preview =
        document.getElementById(
            "previewExperience"
        );

    preview.innerHTML = "";


    items.forEach(item => {

        const title =
            item.querySelector(
                ".exp-title"
            ).value.trim();

        const company =
            item.querySelector(
                ".exp-company"
            ).value.trim();

        const duration =
            item.querySelector(
                ".exp-duration"
            ).value.trim();

        const desc =
            item.querySelector(
                ".exp-desc"
            ).value.trim();


        if(title || company || desc){

            preview.innerHTML += `

                <div class="resume-item">

                    <div class="resume-item-title">
                        ${escapeHTML(title || "Experience")}
                    </div>

                    <div class="resume-item-sub">
                        ${escapeHTML(company || "Company")}
                        ${duration ? " | " + escapeHTML(duration) : ""}
                    </div>

                    <p class="resume-item-desc">
                        ${escapeHTML(desc || "")}
                    </p>

                </div>

            `;

        }

    });

}


/* =========================================================
   ADD EXPERIENCE
========================================================= */

function addExperience(){

    const container =
        document.getElementById(
            "experienceContainer"
        );


    const item =
        document.createElement("div");

    item.className =
        "dynamic-item experience-item";


    item.innerHTML = `

        <button class="remove"
                onclick="removeItem(this)">
            Remove
        </button>

        <div class="grid">

            <div class="field">
                <label>JOB TITLE</label>
                <input class="exp-title"
                       placeholder="Software Intern">
            </div>

            <div class="field">
                <label>COMPANY</label>
                <input class="exp-company"
                       placeholder="Company Name">
            </div>

            <div class="field">
                <label>DURATION</label>
                <input class="exp-duration"
                       placeholder="June 2026 - August 2026">
            </div>

            <div class="field full">
                <label>DESCRIPTION</label>
                <textarea class="exp-desc"
                          placeholder="Describe your work..."></textarea>
            </div>

        </div>

    `;


    container.appendChild(item);

    addDynamicListeners();

    updateResume();

}


/* =========================================================
   PROJECTS
========================================================= */

function updateProjects(){

    const items =
        document.querySelectorAll(
            ".project-item"
        );

    const preview =
        document.getElementById(
            "previewProjects"
        );

    preview.innerHTML = "";


    items.forEach(item => {

        const name =
            item.querySelector(
                ".project-name"
            ).value.trim();

        const tech =
            item.querySelector(
                ".project-tech"
            ).value.trim();

        const desc =
            item.querySelector(
                ".project-desc"
            ).value.trim();

        const link =
            item.querySelector(
                ".project-link"
            ).value.trim();


        if(name || tech || desc){

            preview.innerHTML += `

                <div class="resume-item">

                    <div class="resume-item-title">
                        ${escapeHTML(name || "Project")}
                    </div>

                    <div class="resume-item-sub">
                        ${escapeHTML(tech || "Technologies")}
                    </div>

                    <p class="resume-item-desc">
                        ${escapeHTML(desc || "")}
                    </p>

                    ${
                        link
                        ? `<div class="resume-item-sub">
                             🔗 ${escapeHTML(link)}
                           </div>`
                        : ""
                    }

                </div>

            `;

        }

    });

}


/* =========================================================
   ADD PROJECT
========================================================= */

function addProject(){

    const container =
        document.getElementById(
            "projectContainer"
        );


    const item =
        document.createElement("div");

    item.className =
        "dynamic-item project-item";


    item.innerHTML = `

        <button class="remove"
                onclick="removeItem(this)">
            Remove
        </button>

        <div class="grid">

            <div class="field">

                <label>PROJECT NAME</label>

                <input class="project-name"
                       placeholder="My Awesome Project">

            </div>


            <div class="field">

                <label>TECHNOLOGIES</label>

                <input class="project-tech"
                       placeholder="HTML, CSS, JavaScript">

            </div>


            <div class="field full">

                <label>DESCRIPTION</label>

                <textarea class="project-desc"
                          placeholder="Describe your project..."></textarea>

            </div>


            <div class="field full">

                <label>PROJECT LINK</label>

                <input class="project-link"
                       placeholder="github.com/username/project">

            </div>

        </div>

    `;


    container.appendChild(item);

    addDynamicListeners();

    updateResume();

}


/* =========================================================
   REMOVE ITEM
========================================================= */

function removeItem(button){

    const item =
        button.parentElement;

    item.remove();

    updateResume();

}


/* =========================================================
   DYNAMIC LISTENERS
========================================================= */

function addDynamicListeners(){

    document
    .querySelectorAll(
        ".dynamic-item input, .dynamic-item textarea"
    )
    .forEach(input => {

        input.removeEventListener(
            "input",
            updateResume
        );

        input.addEventListener(
            "input",
            updateResume
        );

    });

}


/* =========================================================
   SKILLS
========================================================= */

function addSkill(){

    const input =
        document.getElementById(
            "skillInput"
        );

    const value =
        input.value.trim();


    if(!value){
        return;
    }


    if(skills.includes(value)){
        showToast("Skill already added!");
        return;
    }


    skills.push(value);

    input.value = "";

    renderSkills();

    updateResume();

}


document
.getElementById("skillInput")
.addEventListener("keydown",function(event){

    if(event.key === "Enter"){

        event.preventDefault();

        addSkill();

    }

});


function renderSkills(){

    const container =
        document.getElementById(
            "skillList"
        );

    container.innerHTML = "";


    skills.forEach((skill,index) => {

        const tag =
            document.createElement("div");

        tag.className =
            "skill-tag";

        tag.innerHTML =
            `${escapeHTML(skill)}
             <span onclick="removeSkill(${index})">
                 ×
             </span>`;

        container.appendChild(tag);

    });

}


function removeSkill(index){

    skills.splice(index,1);

    renderSkills();

    updateResume();

}


function updateSkillsPreview(){

    const container =
        document.getElementById(
            "previewSkills"
        );

    container.innerHTML = "";


    if(skills.length === 0){

        container.innerHTML =
            `<span class="resume-skill">
                Your Skills
             </span>`;

        return;

    }


    skills.forEach(skill => {

        container.innerHTML +=
            `<span class="resume-skill">
                ${escapeHTML(skill)}
             </span>`;

    });

}


/* =========================================================
   SURPRISE ME
========================================================= */

function surpriseMe(){

    const random =
        summaries[
            Math.floor(
                Math.random() *
                summaries.length
            )
        ];


    document.getElementById(
        "summaryInput"
    ).value = random;


    updateResume();

    showToast(
        "✨ Professional summary generated!"
    );

}


/* =========================================================
   SAMPLE DATA
========================================================= */

function fillSample(){

    document.getElementById("name").value =
        "Harsh Sharma";

    document.getElementById("role").value =
        "B.Tech Computer Science Student";

    document.getElementById("email").value =
        "harsh@example.com";

    document.getElementById("phone").value =
        "+91 98765 43210";

    document.getElementById("location").value =
        "New Delhi, India";

    document.getElementById("linkedin").value =
        "linkedin.com/in/harshsharma";

    document.getElementById("github").value =
        "github.com/harshsharma";


    document.getElementById(
        "summaryInput"
    ).value =
        summaries[0];


    document.querySelector(
        ".edu-degree"
    ).value =
        "B.Tech Computer Science";

    document.querySelector(
        ".edu-college"
    ).value =
        "ABC Engineering College";

    document.querySelector(
        ".edu-year"
    ).value =
        "2024 - 2028";

    document.querySelector(
        ".edu-score"
    ).value =
        "8.5 CGPA";


    document.querySelector(
        ".exp-title"
    ).value =
        "Web Development Intern";

    document.querySelector(
        ".exp-company"
    ).value =
        "Tech Solutions Pvt. Ltd.";

    document.querySelector(
        ".exp-duration"
    ).value =
        "May 2026 - July 2026";

    document.querySelector(
        ".exp-desc"
    ).value =
        "Developed responsive web pages using HTML, CSS and JavaScript and collaborated with a team to improve user experience.";


    document.querySelector(
        ".project-name"
    ).value =
        "Campus Flow AI";

    document.querySelector(
        ".project-tech"
    ).value =
        "Python, Flask, HTML, CSS, SQLite";

    document.querySelector(
        ".project-desc"
    ).value =
        "A campus complaint management platform that helps students register complaints and enables administrators to prioritize and manage them efficiently.";

    document.querySelector(
        ".project-link"
    ).value =
        "github.com/harshsharma/campus-flow";


    document.getElementById(
        "certificationsInput"
    ).value =
        "Python Programming Certification\nHackathon Finalist\nWeb Development Bootcamp";


    skills = [
        "HTML",
        "CSS",
        "JavaScript",
        "Python",
        "Flask",
        "SQL",
        "Git",
        "Problem Solving",
        "Teamwork"
    ];


    renderSkills();

    updateResume();

    showToast(
        "✨ Sample data loaded!"
    );

}


/* =========================================================
   SCORE
========================================================= */

function updateScore(){

    const fields = [

        "name",
        "email",
        "role",
        "phone",
        "location",
        "linkedin",
        "github",
        "summaryInput",
        "certificationsInput"

    ];


    let completed = 0;


    fields.forEach(id => {

        if(
            document
            .getElementById(id)
            .value
            .trim()
        ){

            completed++;

        }

    });


    if(
        document.querySelector(
            ".edu-degree"
        )?.value.trim()
    ){

        completed++;

    }


    if(skills.length >= 2){
        completed++;
    }


    if(
        document.querySelector(
            ".project-name"
        )?.value.trim()
    ){

        completed++;

    }


    if(
        document.querySelector(
            ".exp-title"
        )?.value.trim()
    ){

        completed++;

    }


    const total = 13;

    let percentage =
        Math.round(
            (completed / total) * 100
        );


    percentage =
        Math.min(100,percentage);


    document.getElementById(
        "scoreNumber"
    ).textContent =
        percentage + "%";


    document.getElementById(
        "progressBar"
    ).style.width =
        percentage + "%";


    document.getElementById(
        "scoreCircle"
    ).style
    .setProperty(
        "--score",
        percentage + "%"
    );


    const title =
        document.getElementById(
            "scoreTitle"
        );

    const message =
        document.getElementById(
            "scoreMessage"
        );


    if(percentage < 30){

        title.textContent =
            "Let's get started! 🚀";

        message.textContent =
            "Add your basic information to begin.";

    }
    else if(percentage < 60){

        title.textContent =
            "Good start! 👍";

        message.textContent =
            "Keep adding information to strengthen your resume.";

    }
    else if(percentage < 90){

        title.textContent =
            "Looking great! 🔥";

        message.textContent =
            "You're almost there. Add a few more details.";

    }
    else if(percentage < 100){

        title.textContent =
            "Almost perfect! ⭐";

        message.textContent =
            "Just a few more details to complete your resume.";

    }
    else{

        title.textContent =
            "Resume complete! 🏆";

        message.textContent =
            "Your resume is ready to impress employers.";

        celebrate();

    }

}


/* =========================================================
   CHARACTER COUNT
========================================================= */

function updateCharacterCount(){

    const value =
        document.getElementById(
            "summaryInput"
        ).value.length;

    document.getElementById(
        "charCount"
    ).textContent =
        value;

}


/* =========================================================
   DARK MODE
========================================================= */

function toggleDark(){

    document.body.classList.toggle(
        "dark"
    );


    const isDark =
        document.body.classList.contains(
            "dark"
        );


    localStorage.setItem(
        "resumeDark",
        isDark
    );

}


/* =========================================================
   COLOR
========================================================= */

function setColor(color){

    document.documentElement
        .style
        .setProperty(
            "--primary",
            color
        );

    showToast(
        "🎨 Theme changed!"
    );

}


/* =========================================================
   RESUME TEMPLATE
========================================================= */

function template(type,button){

    const resume =
        document.getElementById(
            "resume"
        );


    resume.classList.remove(
        "classic",
        "creative"
    );


    if(type !== "modern"){

        resume.classList.add(
            type
        );

    }


    document
    .querySelectorAll(
        ".template-btn"
    )
    .forEach(btn => {

        btn.classList.remove(
            "active"
        );

    });


    button.classList.add(
        "active"
    );


    showToast(
        "🎨 Template changed!"
    );

}


/* =========================================================
   SAVE
========================================================= */

function saveResume(){

    const data = {};


    document
    .querySelectorAll(
        "input, textarea"
    )
    .forEach(element => {

        if(element.id){

            data[element.id] =
                element.value;

        }

    });


    data.skills = skills;


    localStorage.setItem(
        "resumeData",
        JSON.stringify(data)
    );


    showToast(
        "💾 Resume saved successfully!"
    );

}


/* =========================================================
   AUTO SAVE
========================================================= */

let autoSaveTimer;

function autoSave(){

    clearTimeout(
        autoSaveTimer
    );


    autoSaveTimer =
        setTimeout(() => {

            const data = {};


            document
            .querySelectorAll(
                "input, textarea"
            )
            .forEach(element => {

                if(element.id){

                    data[element.id] =
                        element.value;

                }

            });


            data.skills = skills;


            localStorage.setItem(
                "resumeAutoSave",
                JSON.stringify(data)
            );

        },500);

}


/* =========================================================
   LOAD
========================================================= */

function loadResume(){

    const saved =
        localStorage.getItem(
            "resumeData"
        ) ||
        localStorage.getItem(
            "resumeAutoSave"
        );


    if(!saved){
        return;
    }


    try{

        const data =
            JSON.parse(saved);


        Object.keys(data).forEach(key => {

            if(key === "skills"){

                skills =
                    data.skills || [];

                return;

            }


            const element =
                document.getElementById(
                    key
                );


            if(element){

                element.value =
                    data[key];

            }

        });


        renderSkills();

        updateResume();

    }
    catch(error){

        console.log(
            "Could not load saved data."
        );

    }

}


/* =========================================================
   RESET
========================================================= */

function resetResume(){

    if(
        !confirm(
            "Are you sure you want to reset your resume?"
        )
    ){

        return;

    }


    document
    .querySelectorAll(
        "input, textarea"
    )
    .forEach(element => {

        element.value = "";

    });


    skills = [];

    renderSkills();

    updateResume();

    showToast(
        "↻ Resume has been reset."
    );

}


/* =========================================================
   SHARE
========================================================= */

function shareResume(){

    if(
        navigator.clipboard
    ){

        navigator.clipboard.writeText(
            window.location.href
        );

        showToast(
            "🔗 Page link copied!"
        );

    }
    else{

        showToast(
            "Share link unavailable."
        );

    }

}


/* =========================================================
   PDF
========================================================= */

function downloadPDF(){

    window.print();

}


/* =========================================================
   TIPS
========================================================= */

function showTips(){

    const tips =
        document.getElementById(
            "tips"
        );


    if(
        tips.style.display === "none"
    ){

        tips.style.display =
            "grid";

    }
    else{

        tips.style.display =
            "none";

    }

}


/* =========================================================
   NAVIGATION
========================================================= */

function scrollToSection(id){

    const element =
        document.getElementById(id);


    if(element){

        element.scrollIntoView({
            behavior:"smooth",
            block:"start"
        });

    }

}


/* =========================================================
   CELEBRATION
========================================================= */

let celebrated = false;


function celebrate(){

    if(celebrated){
        return;
    }


    celebrated = true;


    setTimeout(() => {

        document
        .getElementById(
            "celebrate"
        )
        .classList.add(
            "show"
        );

    },500);

}


function closeCelebration(){

    document
    .getElementById(
        "celebrate"
    )
    .classList.remove(
        "show"
    );

}


/* =========================================================
   TOAST
========================================================= */

let toastTimer;


function showToast(message){

    const toast =
        document.getElementById(
            "toast"
        );


    toast.textContent =
        message;


    toast.classList.add(
        "show"
    );


    clearTimeout(
        toastTimer
    );


    toastTimer =
        setTimeout(() => {

            toast.classList.remove(
                "show"
            );

        },2500);

}


/* =========================================================
   KEYBOARD SHORTCUTS
========================================================= */

document.addEventListener(
    "keydown",
    function(event){

        /* Ctrl + S */

        if(
            event.ctrlKey &&
            event.key.toLowerCase() === "s"
        ){

            event.preventDefault();

            saveResume();

        }


        /* Ctrl + P */

        if(
            event.ctrlKey &&
            event.key.toLowerCase() === "p"
        ){

            event.preventDefault();

            downloadPDF();

        }


        /* Ctrl + R */

        if(
            event.ctrlKey &&
            event.key.toLowerCase() === "r"
        ){

            event.preventDefault();

            resetResume();

        }

    }
);


/* =========================================================
   SECURITY / HTML ESCAPE
========================================================= */

function escapeHTML(value){

    return value
        .replaceAll("&","&amp;")
        .replaceAll("<","&lt;")
        .replaceAll(">","&gt;")
        .replaceAll('"',"&quot;")
        .replaceAll("'","&#039;");

}


/* =========================================================
   INITIALIZATION
========================================================= */

if(
    localStorage.getItem(
        "resumeDark"
    ) === "true"
){

    document.body.classList.add(
        "dark"
    );

}


loadResume();

addDynamicListeners();

updateResume();

</script>

</body>
</html>
```
