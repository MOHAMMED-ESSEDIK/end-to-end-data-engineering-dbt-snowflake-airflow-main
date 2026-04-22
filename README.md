<html><head><style>
@import url('https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=Syne:wght@400;500;600;700;800&display=swap');
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --syne:'Syne',sans-serif;
  --mono:'DM Mono',monospace;
  --accent-snow:#29B5E8;
  --accent-dbt:#FF694A;
  --accent-air:#017CEE;
  --accent-dim:rgba(255,255,255,0.06);
  --surface:rgba(255,255,255,0.04);
  --border:rgba(255,255,255,0.1);
  --text:#F0EEE8;
  --muted:rgba(240,238,232,0.45);
}
body{background:#0D0F12;color:var(--text);font-family:var(--syne);padding:0;min-height:100vh}
.wrap{padding:2rem 1.5rem 3rem;max-width:700px;margin:0 auto}

/* HERO */
.hero{margin-bottom:2.5rem;padding-bottom:2rem;border-bottom:0.5px solid var(--border)}
.badge-row{display:flex;gap:8px;margin-bottom:1.2rem;flex-wrap:wrap}
.badge{font-family:var(--mono);font-size:11px;font-weight:500;padding:3px 10px;border-radius:100px;border:0.5px solid}
.badge-snow{color:var(--accent-snow);border-color:var(--accent-snow);background:rgba(41,181,232,0.08)}
.badge-dbt{color:var(--accent-dbt);border-color:var(--accent-dbt);background:rgba(255,105,74,0.08)}
.badge-air{color:var(--accent-air);border-color:var(--accent-air);background:rgba(1,124,238,0.08)}
.badge-py{color:#F5D26B;border-color:#F5D26B;background:rgba(245,210,107,0.08)}
.hero-title{font-size:28px;font-weight:800;line-height:1.15;letter-spacing:-0.5px;margin-bottom:0.6rem}
.hero-title span{color:var(--accent-snow)}
.hero-sub{font-size:14px;color:var(--muted);line-height:1.6;max-width:520px}

/* PIPELINE */
.section-label{font-family:var(--mono);font-size:11px;letter-spacing:0.12em;color:var(--muted);text-transform:uppercase;margin-bottom:1rem}
.pipeline{display:flex;align-items:center;gap:0;margin-bottom:2.5rem;overflow-x:auto;padding-bottom:0.5rem}
.pipe-step{flex:1;min-width:110px;background:var(--surface);border:0.5px solid var(--border);border-radius:10px;padding:14px 12px;position:relative;transition:border-color .2s}
.pipe-step:hover{border-color:rgba(255,255,255,0.25)}
.pipe-step .ps-num{font-family:var(--mono);font-size:10px;color:var(--muted);margin-bottom:6px}
.pipe-step .ps-icon{font-size:18px;margin-bottom:6px;line-height:1}
.pipe-step .ps-name{font-size:13px;font-weight:600;margin-bottom:2px}
.pipe-step .ps-desc{font-size:11px;color:var(--muted);line-height:1.4}
.pipe-arrow{color:var(--muted);font-size:16px;padding:0 6px;flex-shrink:0;align-self:center}

/* TECH TABLE */
.tech-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:2.5rem}
.tech-card{background:var(--surface);border:0.5px solid var(--border);border-radius:10px;padding:14px 16px;transition:border-color .2s;cursor:default}
.tech-card:hover{border-color:rgba(255,255,255,0.2)}
.tc-top{display:flex;align-items:center;gap:10px;margin-bottom:8px}
.tc-dot{width:8px;height:8px;border-radius:50%;flex-shrink:0}
.tc-name{font-size:14px;font-weight:600}
.tc-desc{font-size:12px;color:var(--muted);line-height:1.5}
.tc-tag{font-family:var(--mono);font-size:10px;padding:2px 8px;border-radius:100px;background:rgba(255,255,255,0.06);color:var(--muted);display:inline-block;margin-top:8px}

/* CODE BLOCKS */
.code-section{margin-bottom:2.5rem}
.code-tabs{display:flex;gap:6px;margin-bottom:10px;flex-wrap:wrap}
.ctab{font-family:var(--mono);font-size:11px;padding:4px 12px;border-radius:6px;border:0.5px solid var(--border);background:transparent;color:var(--muted);cursor:pointer;transition:.15s}
.ctab.active{background:rgba(255,255,255,0.08);color:var(--text);border-color:rgba(255,255,255,0.2)}
.code-box{background:#0A0C0F;border:0.5px solid var(--border);border-radius:10px;overflow:hidden}
.code-header{display:flex;align-items:center;justify-content:space-between;padding:10px 14px;border-bottom:0.5px solid var(--border)}
.code-header-left{display:flex;gap:6px}
.dot{width:9px;height:9px;border-radius:50%}
.dot-r{background:#FF5F57}.dot-y{background:#FFBD2E}.dot-g{background:#28C840}
.code-fname{font-family:var(--mono);font-size:11px;color:var(--muted)}
.code-content{padding:16px;overflow-x:auto}
.code-content pre{font-family:var(--mono);font-size:12px;line-height:1.7;color:#C9D1D9;white-space:pre}
.kw{color:#FF7B72}.fn{color:#D2A8FF}.str{color:#A5D6FF}.cmt{color:#8B949E}.num{color:#79C0FF}.prop{color:#7EE787}

/* TROUBLESHOOT */
.trouble-list{display:flex;flex-direction:column;gap:8px;margin-bottom:2.5rem}
.trouble-item{display:grid;grid-template-columns:auto 1fr 1fr;gap:0;background:var(--surface);border:0.5px solid var(--border);border-radius:10px;overflow:hidden}
.ti-cell{padding:11px 14px;font-size:12px;line-height:1.4}
.ti-cell:not(:last-child){border-right:0.5px solid var(--border)}
.ti-err{font-family:var(--mono);color:var(--accent-dbt);font-size:11px;white-space:nowrap}
.ti-cause{color:var(--muted)}
.ti-fix{color:var(--prop);font-family:var(--mono);font-size:11px}

/* LEARNINGS */
.learnings{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:2rem}
.learn-item{background:var(--surface);border:0.5px solid var(--border);border-radius:10px;padding:12px 14px}
.learn-item .li-num{font-family:var(--mono);font-size:10px;color:var(--muted);margin-bottom:4px}
.learn-item .li-title{font-size:13px;font-weight:600;margin-bottom:3px}
.learn-item .li-desc{font-size:11px;color:var(--muted);line-height:1.4}

/* FOOTER */
.footer{border-top:0.5px solid var(--border);padding-top:1.5rem;display:flex;align-items:center;justify-content:space-between;flex-wrap:gap}
.footer-text{font-size:11px;color:var(--muted);font-family:var(--mono)}
.gh-link{font-family:var(--mono);font-size:11px;color:var(--accent-snow);text-decoration:none;border:0.5px solid rgba(41,181,232,0.3);padding:4px 12px;border-radius:6px;background:rgba(41,181,232,0.06)}
.gh-link:hover{background:rgba(41,181,232,0.12)}
</style>

</head><body><div class="wrap">

<div class="hero">
  <div class="badge-row">
    <span class="badge badge-snow">Snowflake</span>
    <span class="badge badge-dbt">dbt Core</span>
    <span class="badge badge-air">Airflow</span>
    <span class="badge badge-py">Python · SQL</span>
  </div>
  <h1 class="hero-title">End-to-End<br><span>Data Engineering</span> Pipeline</h1>
  <p class="hero-sub">Raw data to analytics-ready tables — automated, tested, and orchestrated on the modern data stack.</p>
</div>

<div class="section-label">Data flow</div>
<div class="pipeline">
  <div class="pipe-step">
    <div class="ps-num">01</div>
    <div class="ps-name" style="color:var(--accent-snow)">Ingest</div>
    <div class="ps-desc">CSV seeds land in Snowflake RAW schema</div>
  </div>
  <div class="pipe-arrow">→</div>
  <div class="pipe-step">
    <div class="ps-num">02</div>
    <div class="ps-name" style="color:var(--accent-dbt)">Stage</div>
    <div class="ps-desc">dbt cleans, casts, and standardizes fields</div>
  </div>
  <div class="pipe-arrow">→</div>
  <div class="pipe-step">
    <div class="ps-num">03</div>
    <div class="ps-name" style="color:#D2A8FF">Model</div>
    <div class="ps-desc">Fact &amp; dim tables, SCD snapshots built</div>
  </div>
  <div class="pipe-arrow">→</div>
  <div class="pipe-step">
    <div class="ps-num">04</div>
    <div class="ps-name" style="color:#7EE787">Validate</div>
    <div class="ps-desc">dbt tests assert nulls &amp; relationships</div>
  </div>
  <div class="pipe-arrow">→</div>
  <div class="pipe-step">
    <div class="ps-num">05</div>
    <div class="ps-name" style="color:var(--accent-air)">Orchestrate</div>
    <div class="ps-desc">Airflow DAG triggers daily end-to-end run</div>
  </div>
</div>

<div class="section-label">Stack</div>
<div class="tech-grid">
  <div class="tech-card">
    <div class="tc-top"><div class="tc-dot" style="background:var(--accent-snow)"></div><div class="tc-name">Snowflake</div></div>
    <div class="tc-desc">Scalable cloud data warehouse. Hosts both raw ingestion and final analytics schemas.</div>
    <span class="tc-tag">Data Warehouse</span>
  </div>
  <div class="tech-card">
    <div class="tc-top"><div class="tc-dot" style="background:var(--accent-dbt)"></div><div class="tc-name">dbt Core</div></div>
    <div class="tc-desc">Modular SQL modeling with staging, marts, snapshots, and automated data quality tests.</div>
    <span class="tc-tag">Transformation</span>
  </div>
  <div class="tech-card">
    <div class="tc-top"><div class="tc-dot" style="background:var(--accent-air)"></div><div class="tc-name">Apache Airflow</div></div>
    <div class="tc-desc">Schedules and monitors the full pipeline. DAG visible at <code style="font-size:10px">localhost:8080</code>.</div>
    <span class="tc-tag">Orchestration</span>
  </div>
  <div class="tech-card">
    <div class="tc-top"><div class="tc-dot" style="background:#F5D26B"></div><div class="tc-name">Python · SQL</div></div>
    <div class="tc-desc">DAG scripting in Python, transformation logic in modular SQL models with Jinja templating.</div>
    <span class="tc-tag">Language</span>
  </div>
</div>

<div class="section-label">Quick start</div>
<div class="code-section">
  <div class="code-tabs">
    <button class="ctab active" onclick="showCode('setup')">Setup</button>
    <button class="ctab" onclick="showCode('profile')">profiles.yml</button>
    <button class="ctab" onclick="showCode('run')">Run</button>
    <button class="ctab" onclick="showCode('airflow')">Airflow</button>
  </div>
  <div class="code-box">
    <div class="code-header">
      <div class="code-header-left"><div class="dot dot-r"></div><div class="dot dot-y"></div><div class="dot dot-g"></div></div>
      <span class="code-fname" id="code-fname">bash</span>
    </div>
    <div class="code-content">
      <pre id="code-display"><span class="cmt"># Clone the repo and activate environment</span>
<span class="fn">git</span> <span class="kw">clone</span> <span class="str">https://github.com/MOHAMMED-ESSEDIK/end-to-end-data-engineering-dbt-snowflake-airflow-main.git</span>
<span class="fn">cd</span> snowflake_data_project

<span class="fn">python</span> -m venv venv
<span class="fn">source</span> venv/bin/activate  <span class="cmt"># Windows: venv\Scripts\activate</span>
<span class="fn">pip</span> install -r requirements.txt</pre>
    </div>
  </div>
</div>

<div class="section-label">Troubleshooting</div>
<div class="trouble-list">
  <div class="trouble-item">
    <div class="ti-cell ti-err">Database Error</div>
    <div class="ti-cell ti-cause">Incorrect Snowflake credentials</div>
    <div class="ti-cell ti-fix">Check profiles.yml account/role</div>
  </div>
  <div class="trouble-item">
    <div class="ti-cell ti-err">dbt: not found</div>
    <div class="ti-cell ti-cause">Virtual env not activated</div>
    <div class="ti-cell ti-fix">source venv/bin/activate</div>
  </div>
  <div class="trouble-item">
    <div class="ti-cell ti-err">Port 8080 in use</div>
    <div class="ti-cell ti-cause">Airflow port conflict</div>
    <div class="ti-cell ti-fix">airflow webserver -p 8081</div>
  </div>
  <div class="trouble-item">
    <div class="ti-cell ti-err">Incremental fail</div>
    <div class="ti-cell ti-cause">Schema mismatch on model</div>
    <div class="ti-cell ti-fix">dbt run --full-refresh --select &lt;model&gt;</div>
  </div>
</div>

<div class="section-label">Key learnings</div>
<div class="learnings">
  <div class="learn-item"><div class="li-num">01</div><div class="li-title">Modular SQL</div><div class="li-desc">Complex queries broken into reusable, testable dbt models</div></div>
  <div class="learn-item"><div class="li-num">02</div><div class="li-title">SCD Handling</div><div class="li-desc">Type-2 snapshots tracking historical record changes over time</div></div>
  <div class="learn-item"><div class="li-num">03</div><div class="li-title">Incremental Loads</div><div class="li-desc">Performance gains by processing only new or updated data</div></div>
  <div class="learn-item"><div class="li-num">04</div><div class="li-title">DAG Automation</div><div class="li-desc">Airflow manages task dependencies and pipeline scheduling</div></div>
  <div class="learn-item"><div class="li-num">05</div><div class="li-title">Data Quality</div><div class="li-desc">Automated tests enforce schema integrity and null constraints</div></div>
  <div class="learn-item"><div class="li-num">06</div><div class="li-title">Governance</div><div class="li-desc">Documentation and lineage built directly into dbt models</div></div>
</div>

<div class="footer">
  <span class="footer-text">Built for the Modern Data Stack community</span>
  <a class="gh-link" href="https://github.com/MOHAMMED-ESSEDIK/end-to-end-data-engineering-dbt-snowflake-airflow-main">GitHub →</a>
</div>

</div>

<script>
const codes = {
  setup: {
    fname: 'bash',
    html: `<span class="cmt"># Clone the repo and activate environment</span>\n<span class="fn">git</span> <span class="kw">clone</span> <span class="str">https://github.com/MOHAMMED-ESSEDIK/end-to-end-data-engineering-dbt-snowflake-airflow-main.git</span>\n<span class="fn">cd</span> snowflake_data_project\n\n<span class="fn">python</span> -m venv venv\n<span class="fn">source</span> venv/bin/activate  <span class="cmt"># Windows: venv\\Scripts\\activate</span>\n<span class="fn">pip</span> install -r requirements.txt`
  },
  profile: {
    fname: '~/.dbt/profiles.yml',
    html: `<span class="prop">snowflake_project</span>:\n  <span class="prop">outputs</span>:\n    <span class="prop">dev</span>:\n      <span class="prop">type</span>: <span class="str">snowflake</span>\n      <span class="prop">account</span>: <span class="str">your_account_id</span>\n      <span class="prop">user</span>: <span class="str">dbt_user</span>\n      <span class="prop">password</span>: <span class="str">your_password</span>\n      <span class="prop">role</span>: <span class="str">ACCOUNTADMIN</span>\n      <span class="prop">database</span>: <span class="str">finance_db</span>\n      <span class="prop">warehouse</span>: <span class="str">finance_wh</span>\n      <span class="prop">schema</span>: <span class="str">raw</span>\n  <span class="prop">target</span>: <span class="str">dev</span>`
  },
  run: {
    fname: 'bash',
    html: `<span class="cmt"># Load, transform, and test in sequence</span>\n<span class="fn">dbt</span> <span class="kw">seed</span>    <span class="cmt"># Load CSVs from /seeds into Snowflake</span>\n<span class="fn">dbt</span> <span class="kw">run</span>     <span class="cmt"># Build all models: Staging → Marts</span>\n<span class="fn">dbt</span> <span class="kw">test</span>    <span class="cmt"># Run data quality tests</span>`
  },
  airflow: {
    fname: 'bash',
    html: `<span class="cmt"># Launch Airflow and trigger the DAG</span>\n<span class="kw">export</span> <span class="prop">AIRFLOW_HOME</span>=<span class="str">$(pwd)</span>\n<span class="fn">airflow</span> standalone\n\n<span class="cmt"># Access the UI at http://localhost:8080</span>\n<span class="cmt"># Trigger the dbt DAG to run the full pipeline</span>`
  }
};
function showCode(key) {
  document.getElementById('code-display').innerHTML = codes[key].html;
  document.getElementById('code-fname').textContent = codes[key].fname;
  document.querySelectorAll('.ctab').forEach((t,i) => t.classList.toggle('active', ['setup','profile','run','airflow'][i]===key));
}
</script>
</body></html>
