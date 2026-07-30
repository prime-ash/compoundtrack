<!DOCTYPE html><html lang="en"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1.0"><title>CompoundTrack v3</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=DM+Mono:wght@400;500&display=swap');
*{box-sizing:border-box;margin:0;padding:0}
:root{--bg:#f7f6f3;--s:#fff;--b:#e4e2dc;--t:#1a1916;--m:#7a7870;--bk:#0b6e4f;--bkb:#edf7f3;--hl:#1a5fa8;--hlb:#eaf2fc;--cc:#4f35b5;--ccb:#eeecfb;--st:#8a4f0a;--stb:#fdf0e0;--ol:#2d6a1a;--olb:#edf5e8;--px:#a82222;--pxb:#fceaea;--ab:#8a1f5a;--abb:#fceaf4;--dn:#a82222;--dnb:#fceaea;--dnbr:#f5c1c1;--wn:#8a4f0a;--wnb:#fdf0e0;--wnbr:#f5d5a0;--sc:#0b6e4f;--scb:#edf7f3;--in:#1a5fa8;--inb:#eaf2fc}
body{font-family:'DM Sans',sans-serif;font-size:13px;background:var(--bg);color:var(--t);min-height:100vh}
.ls{position:fixed;top:0;left:0;right:0;bottom:0;background:var(--t);display:flex;align-items:center;justify-content:center;z-index:1000}
.lb{background:var(--s);border-radius:16px;padding:32px;width:380px;max-width:95vw}
.ll{font-size:20px;font-weight:600;margin-bottom:6px}.ll span{color:#6ee7b7}
.ls2{font-size:12px;color:var(--m);margin-bottom:24px}
.llab{font-size:11px;font-weight:500;text-transform:uppercase;letter-spacing:.4px;color:var(--m);margin-bottom:4px;display:block}
.lin{width:100%;padding:10px 12px;border:.5px solid var(--b);border-radius:8px;font-family:'DM Sans',sans-serif;background:var(--s);color:var(--t);font-size:13px;margin-bottom:14px}
.lpin{width:100%;padding:10px 12px;border:.5px solid var(--b);border-radius:8px;font-size:16px;font-family:'DM Mono',monospace;letter-spacing:4px;margin-bottom:6px;text-align:center;background:var(--s);color:var(--t)}
.lpin:focus{border-color:var(--t);outline:none}
.lh{font-size:11px;color:var(--m);margin-bottom:18px;text-align:center}
.le{font-size:12px;color:var(--dn);margin-bottom:10px;text-align:center;min-height:16px}
.lbtn{width:100%;padding:11px;background:var(--t);color:white;border:none;border-radius:8px;font-size:14px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif}
.rb{display:inline-flex;align-items:center;gap:6px;padding:3px 10px;border-radius:20px;font-size:11px;font-weight:600;margin-left:8px}
.rb.admin{background:#edf7f3;color:#0b6e4f}.rb.coordinator{background:#eaf2fc;color:#1a5fa8}.rb.provider{background:#eeecfb;color:#4f35b5}.rb.staff{background:#fdf0e0;color:#8a4f0a}
.app{display:flex;flex-direction:column;min-height:100vh}
.tb{background:var(--t);color:white;padding:0 20px;display:flex;align-items:center;gap:16px;height:50px;flex-shrink:0;position:sticky;top:0;z-index:200;width:100vw;margin-left:calc(-50vw + 50%);box-sizing:border-box}
.lg{font-size:15px;font-weight:600;letter-spacing:-.3px;white-space:nowrap}.lg span{color:#6ee7b7}
.nv{display:flex;gap:1px;flex:1;overflow-x:auto}
.nv button{background:none;border:none;padding:0 14px;height:50px;font-size:13px;cursor:pointer;color:rgba(255,255,255,.6);font-family:'DM Sans',sans-serif;font-weight:500;white-space:nowrap;border-bottom:2px solid transparent;transition:all .15s}
.nv button:hover{color:white;background:rgba(255,255,255,.07)}.nv button.active{color:white;border-bottom-color:#6ee7b7}
.ct{flex:1;padding:18px 20px;max-width:1400px;width:100%;margin:0 auto}
.sts{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;margin-bottom:16px}
.st{background:var(--s);border:.5px solid var(--b);border-radius:10px;padding:12px 14px}
.stl{font-size:10px;text-transform:uppercase;letter-spacing:.5px;color:var(--m);margin-bottom:4px;font-weight:500}
.stv{font-size:22px;font-weight:600;font-family:'DM Mono',monospace}
.stv.dn{color:var(--dn)}.stv.wn{color:var(--wn)}.stv.sc{color:var(--sc)}
.cd{background:var(--s);border:.5px solid var(--b);border-radius:12px;overflow:hidden}
.cp{padding:14px 16px}
.sh{display:flex;align-items:center;justify-content:space-between;margin-bottom:12px}
.sh h2{font-size:16px;font-weight:600;color:#fff}
table{width:100%;border-collapse:collapse;font-size:12px}
th{text-align:left;padding:7px 12px;font-weight:500;font-size:10px;text-transform:uppercase;letter-spacing:.5px;color:var(--m);border-bottom:.5px solid var(--b);background:#faf9f7}
td{padding:7px 12px;border-bottom:.5px solid #f0efe9;vertical-align:top;line-height:1.5}
tr:last-child td{border-bottom:none}tr:hover td{background:#fafaf8}
.btn{display:inline-flex;align-items:center;gap:5px;padding:7px 13px;border-radius:8px;border:.5px solid var(--b);background:none;cursor:pointer;font-size:12px;font-family:'DM Sans',sans-serif;color:var(--t);font-weight:500;transition:all .15s}
.btn:hover{background:var(--bg)}.btn.p{background:var(--t);color:white;border-color:var(--t)}.btn.p:hover{opacity:.88}
.btn.sm{padding:4px 9px;font-size:11px}.btn.dn{color:var(--dn);border-color:var(--dnbr)}.btn.dn:hover{background:var(--dnb)}
.hb{display:none;background:none;border:none;color:white;font-size:22px;cursor:pointer;padding:0 4px}
.bdg{display:inline-block;padding:2px 8px;border-radius:20px;font-size:10px;font-weight:600;white-space:nowrap;min-width:130px;text-align:center}
.bdg.awaiting-payment-verification{background:#faeeda;color:#854f0b}
.bdg.payment-confirmed-ready-to-place{background:#edf7f3;color:#0b6e4f}
.bdg.ordered{background:#eaf2fc;color:#1a5fa8}.bdg.processing{background:#eeecfb;color:#4f35b5}
.bdg.shipped{background:#edf5e8;color:#2d6a1a}.bdg.delivered{background:#edf7f3;color:#0b6e4f;font-weight:700}
.bdg.on-hold{background:#fceaea;color:#a82222}.bdg.returned-to-provider{background:#fceaea;color:#a82222;font-weight:700}
.bdg.pending{background:#faeeda;color:#854f0b}.bdg.on-subscription{background:#eeecfb;color:#4f35b5;font-weight:700}
/* PAYMENT BADGES */
.bdg.pay-paid{background:#edf7f3;color:#0b6e4f;min-width:90px}
.bdg.pay-bal{background:#fceaea;color:#a82222;min-width:90px}
.bdg.pay-unk{background:#f0efe9;color:#7a7870;min-width:90px}
.fl{display:inline-block;padding:1px 5px;border-radius:4px;font-size:9px;font-weight:700;letter-spacing:.3px;margin:1px}
.fl.ctrl{background:var(--pxb);color:var(--px)}.fl.research{background:var(--abb);color:var(--ab)}
.fl.watch{background:var(--stb);color:var(--st)}.fl.inoffice{background:var(--hlb);color:var(--hl)}
.fl.goodrx{background:#edf7f3;color:#0b6e4f}.fl.noorder{background:#f0efe9;color:#7a7870}
.ph{display:inline-block;padding:2px 7px;border-radius:10px;font-size:10px;font-weight:600;white-space:nowrap}
.ph.brooksville{background:var(--bkb);color:var(--bk)}.ph.hallandale{background:var(--hlb);color:var(--hl)}
.ph.centercity{background:var(--ccb);color:var(--cc)}.ph.strive{background:var(--stb);color:var(--st)}
.ph.olympia{background:var(--olb);color:var(--ol)}.ph.pdrx{background:var(--pxb);color:var(--px)}
.ph.alphabio,.ph.soma{background:var(--abb);color:var(--ab)}.ph.stryker,.ph.southlake,.ph.nucare{background:#faf5e0;color:#6a5500}.ph.betterlife{background:#e8f7ee;color:#1d7a3f}
.fr{margin-bottom:11px}
.fr label{display:block;font-size:11px;font-weight:500;color:var(--m);margin-bottom:3px;text-transform:uppercase;letter-spacing:.3px}
.fr input,.fr select,.fr textarea{width:100%;padding:8px 10px;border:.5px solid var(--b);border-radius:8px;background:var(--s);color:var(--t);font-size:13px;font-family:'DM Sans',sans-serif;outline:none}
.fr input:focus,.fr select:focus,.fr textarea:focus{border-color:#1a1916}
.fr textarea{min-height:68px;resize:vertical}
.f2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.cr{display:flex;align-items:center;gap:8px;padding:8px 10px;border:.5px solid var(--b);border-radius:8px;margin-bottom:7px;cursor:pointer}
.cr:hover{background:var(--bg)}.cr input[type=checkbox]{width:15px;height:15px;cursor:pointer;accent-color:var(--t)}.cr label{cursor:pointer;font-size:12px;line-height:1.4}
.al{padding:10px 13px;border-radius:8px;font-size:12px;margin-bottom:10px;display:flex;align-items:flex-start;gap:8px;line-height:1.5}
.al.dn{background:var(--dnb);border:.5px solid var(--dnbr);color:var(--dn)}
.al.wn{background:var(--wnb);border:.5px solid var(--wnbr);color:var(--wn)}
.al.in{background:var(--inb);border:.5px solid #c5d8f5;color:var(--in)}
.al.sc{background:var(--scb);border:.5px solid #b0e0cc;color:var(--sc)}
.dt{background:var(--bg);border-radius:10px;padding:13px;margin-top:8px;font-size:12px}
.dr{display:flex;justify-content:space-between;padding:5px 0;border-bottom:.5px solid var(--b)}
.dr:last-child{border-bottom:none}.dl{color:var(--m);font-weight:500}
.hn{background:var(--wnb);border:.5px solid var(--wnbr);border-radius:6px;padding:7px 10px;margin-top:8px;font-size:11px;color:var(--wn)}
.phc{background:var(--s);border:.5px solid var(--b);border-radius:12px;padding:14px 16px;margin-bottom:10px}
.phn{font-weight:600;font-size:13px;margin-bottom:2px}.phm{font-size:11px;color:var(--m);line-height:1.7}
.phmd{display:flex;flex-wrap:wrap;gap:4px;margin-top:8px}
.phmdt{background:var(--bg);border:.5px solid var(--b);border-radius:10px;padding:2px 8px;font-size:10px;color:var(--m)}
.cts{display:flex;gap:3px;flex-wrap:wrap;margin-bottom:12px}
.ct2{background:none;border:.5px solid transparent;padding:4px 11px;border-radius:6px;font-size:12px;cursor:pointer;color:rgba(255,255,255,.85);font-family:'DM Sans',sans-serif;font-weight:500}
.ct2.active{border-color:var(--b);background:var(--s);color:var(--t)}.ct2:hover:not(.active){background:rgba(255,255,255,.15);color:#fff}
.ch{font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.5px;color:var(--m);padding:7px 12px;background:#faf9f7;border-bottom:.5px solid var(--b)}
.pv{font-family:'DM Mono',monospace;font-size:11px;color:var(--m)}.pv.best{color:var(--bk);font-weight:600}
.bc{font-family:'DM Mono',monospace;font-size:12px;font-weight:600;color:var(--bk)}.nt{font-size:10px;color:#aaa;font-style:italic}
.lg2{display:flex;gap:7px;flex-wrap:wrap;align-items:center;font-size:11px;color:var(--m);padding:10px 0;margin-bottom:4px}
.emp{text-align:center;padding:40px;color:var(--m);font-size:13px}
/* PAYMENT CHECKER TOOL */
.puz{border:1.5px dashed var(--b);border-radius:10px;padding:18px;text-align:center;cursor:pointer;transition:background .15s,border-color .15s;background:var(--bg);color:var(--m);font-size:12px}
.puz:hover,.puz.drag-over{background:var(--inb);border-color:var(--in);color:var(--in)}
.pcm{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:10px}
.pcm label{font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.3px;color:var(--m);display:block;margin-bottom:3px}
.pcm select{width:100%;padding:6px 9px;border:.5px solid var(--b);border-radius:7px;font-size:12px;font-family:'DM Sans',sans-serif;background:var(--s);color:var(--t)}
.pmr{display:flex;align-items:center;gap:10px;padding:7px 10px;border-bottom:.5px solid var(--b);font-size:12px}
.pmr:last-child{border-bottom:none}
.qb{background:#0f3d2e;border-radius:12px;padding:16px 20px;margin-bottom:16px}
.qb h3{font-size:14px;font-weight:600;color:white;margin-bottom:2px}
.qb p{font-size:11px;color:rgba(255,255,255,.55);margin-bottom:12px}
.qg{display:grid;grid-template-columns:1.2fr 1.5fr 1fr auto;gap:8px;align-items:end}
.qf label{display:block;font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.4px;color:rgba(255,255,255,.5);margin-bottom:4px}
.qf input,.qf select{width:100%;padding:9px 11px;border:1px solid rgba(255,255,255,.15);border-radius:8px;font-size:13px;font-family:'DM Sans',sans-serif;background:rgba(255,255,255,.1);color:white;outline:none}
.qf input::placeholder{color:rgba(255,255,255,.35)}.qf select option{background:#1a1916;color:white}
.qf input:focus,.qf select:focus{background:rgba(255,255,255,.18);border-color:rgba(255,255,255,.35)}
.qs{padding:10px 16px;background:#6ee7b7;color:#0b3d28;border:none;border-radius:8px;font-size:13px;font-weight:700;cursor:pointer;font-family:'DM Sans',sans-serif;white-space:nowrap}
.qsg{background:rgba(255,255,255,.08);border:1px solid rgba(110,231,183,.3);border-radius:8px;padding:10px 14px;margin-top:10px;font-size:12px;display:none}
.qsg.show{display:block}.qpr{font-size:13px;font-weight:700;color:#6ee7b7;margin-bottom:3px}
.qpm{font-size:11px;color:rgba(255,255,255,.55)}
.qw{background:rgba(200,80,0,.2);border:1px solid rgba(200,80,0,.3);border-radius:6px;padding:7px 11px;font-size:11px;color:#fbbf7a;margin-top:6px}
.clo{position:fixed;top:0;left:0;right:0;bottom:0;background:rgba(0,0,0,.5);display:flex;align-items:center;justify-content:center;z-index:600}
.clb{background:white;border-radius:16px;width:580px;max-width:95vw;max-height:88vh;overflow-y:auto;box-shadow:0 24px 80px rgba(0,0,0,.25)}
.clh{padding:18px 22px 14px;border-bottom:.5px solid var(--b);display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;background:white;z-index:1}
.clh h2{font-size:15px;font-weight:600}.clp{font-size:12px;color:var(--m);margin-top:2px}
.clst{padding:16px 22px 22px}
.cls{display:flex;gap:12px;align-items:flex-start;padding:13px 14px;border-radius:10px;margin-bottom:8px;border:.5px solid var(--b);background:var(--bg)}
.cls.done{background:#edf7f3;border-color:#b0e0cc}.cls.active{background:#fffbef;border-color:#f5c55a}.cls.locked{opacity:.4;pointer-events:none}
.cln{width:26px;height:26px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;flex-shrink:0;margin-top:1px;background:var(--b);color:var(--m)}
.cls.done .cln{background:#0b6e4f;color:white}.cls.active .cln{background:#d97706;color:white}
.clbd{flex:1;min-width:0}.clt{font-size:13px;font-weight:600;color:var(--t);margin-bottom:2px}.cld{font-size:11px;color:var(--m);line-height:1.55}
.cla{margin-top:8px;display:flex;gap:6px;flex-wrap:wrap;align-items:center}
.clbt{padding:7px 14px;border-radius:7px;font-size:12px;font-weight:600;border:none;cursor:pointer;font-family:'DM Sans',sans-serif}
.clbt.p{background:#1a1916;color:white}.clbt.sc{background:#0b6e4f;color:white}.clbt.sec{background:var(--s);color:var(--t);border:.5px solid var(--b)}
.clw{background:var(--wnb);border:.5px solid var(--wnbr);border-radius:8px;padding:9px 12px;margin-top:6px;font-size:11px;color:var(--wn);line-height:1.55}
.cli{width:100%;padding:8px 10px;border:.5px solid var(--b);border-radius:7px;font-size:13px;font-family:'DM Mono',sans-serif;background:var(--bg);color:var(--t);margin-top:6px;outline:none}
.clc{display:flex;align-items:center;gap:8px;padding:8px 10px;background:var(--s);border:.5px solid var(--b);border-radius:7px;margin-top:6px;cursor:pointer}
.clc input[type=checkbox]{width:15px;height:15px;accent-color:#0b6e4f;cursor:pointer}.clc label{font-size:12px;cursor:pointer;line-height:1.4}
.prc{background:var(--s);border:.5px solid var(--b);border-radius:14px;padding:18px 20px;margin-bottom:12px;display:flex;align-items:flex-start;gap:18px}
.pri{width:44px;height:44px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0;margin-top:2px}
.prb{flex:1;min-width:0}.prn{font-size:14px;font-weight:600;margin-bottom:2px}.prt{font-size:11px;color:var(--m);margin-bottom:10px}
.prf{display:flex;flex-direction:column;gap:6px;margin-bottom:12px}
.prfi{display:flex;align-items:center;gap:8px;background:var(--bg);border:.5px solid var(--b);border-radius:8px;padding:7px 11px}
.prfl{font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.4px;color:var(--m);width:70px;flex-shrink:0}
.prfv{font-family:'DM Mono',monospace;font-size:12px;flex:1;word-break:break-all}.prfv.msk{letter-spacing:3px;font-size:14px;color:var(--m)}
.pra{display:flex;gap:7px;flex-wrap:wrap}
.aib{display:inline-flex;align-items:center;gap:8px;padding:14px 24px;background:var(--t);color:white;border:none;border-radius:10px;font-size:14px;font-weight:600;cursor:pointer;font-family:'DM Sans',sans-serif;text-decoration:none}
.acb{display:inline-flex;align-items:center;gap:6px;padding:10px 18px;background:none;border:.5px solid var(--b);border-radius:8px;font-size:13px;font-weight:500;cursor:pointer;font-family:'DM Sans',sans-serif;color:var(--t);margin-left:10px}
.acp{background:var(--bg);border:.5px solid var(--b);border-radius:8px;padding:12px;font-size:11px;font-family:'DM Mono',monospace;color:var(--m);max-height:180px;overflow-y:auto;margin-top:12px;white-space:pre-wrap;line-height:1.6}
.iic{background:var(--s);border:.5px solid var(--in);border-radius:12px;padding:18px 20px;margin-bottom:16px}
.iis{display:flex;gap:12px;align-items:flex-start;margin-bottom:12px}
.iin{width:24px;height:24px;border-radius:50%;background:var(--in);color:white;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;flex-shrink:0;margin-top:2px}
tr.rno td{background:#fffbef!important;border-bottom-color:#f5e7a0!important}
tr.rno td:first-child{border-left:3px solid #d97706}
tr.rip td{background:#f0faf5!important;border-bottom-color:#b0e0cc!important}
tr.rip td:first-child{border-left:3px solid #0b6e4f}
tr.rsb td{background:#f5f3ff!important;border-bottom-color:#c4b5fd!important}
tr.rsb td:first-child{border-left:3px solid #7c3aed}
.cd table td,.cd table th{text-align:center;vertical-align:middle;padding:10px 6px}
.cd table td:nth-child(1),.cd table th:nth-child(1),.cd table td:nth-child(2),.cd table th:nth-child(2),.cd table td:nth-child(3),.cd table th:nth-child(3){text-align:left!important;padding-left:16px!important}
.rb2{display:inline-flex;align-items:center;gap:4px;padding:4px 10px;background:#edf7f3;border:.5px solid #b0e0cc;border-radius:6px;font-size:11px;font-weight:600;color:#0b6e4f;cursor:pointer;font-family:'DM Sans',sans-serif}
.vt{display:flex;align-items:center;gap:8px;padding:4px 10px;background:rgba(255,255,255,.1);border-radius:8px;font-size:11px;color:rgba(255,255,255,.8)}
.vt select{background:transparent;border:none;color:white;font-size:11px;font-family:'DM Sans',sans-serif;cursor:pointer;outline:none}
.vt select option{background:#1a1916;color:white}
@media(max-width:850px){
.sts{grid-template-columns:1fr 1fr}.qg{grid-template-columns:1fr;gap:12px}.f2{grid-template-columns:1fr}
.cd,.phc{overflow-x:auto;-webkit-overflow-scrolling:touch}table{white-space:nowrap;min-width:600px}
.tb{padding:12px 16px;flex-wrap:nowrap}.hb{display:block}
.nv{display:none;position:absolute;top:100%;left:0;right:0;background:#1a1916;flex-direction:column;padding:10px 20px 20px;border-top:1px solid rgba(255,255,255,.1);box-shadow:0 20px 30px rgba(0,0,0,.5);z-index:1000}
.nv.open{display:flex}.nv button{width:100%;text-align:left;padding:14px 10px;height:auto;border-bottom:1px solid rgba(255,255,255,.05)}
#ui{font-size:11px!important;display:flex;align-items:center;white-space:nowrap}
.cls{flex-direction:column;gap:8px}.dr{flex-direction:column;align-items:flex-start;gap:4px;padding:8px 0}
.ct{padding:12px 10px}.pcm{grid-template-columns:1fr}}
@media(max-width:480px){.sts{grid-template-columns:1fr}.lb{padding:24px 20px}}
</style></head><body>
<div class="app">
<div class="tb" id="tbe" style="display:none;position:relative">
  <div class="lg">Compound<span>Track</span> <span style="font-size:10px;opacity:.5;font-weight:400">v3</span></div>
  <nav class="nv" id="nav"></nav>
  <div style="display:flex;align-items:center;gap:10px;margin-left:auto;flex-shrink:0">
    <div id="ptw"></div>
    <div id="ui" style="font-size:11px;color:rgba(255,255,255,.7)"></div>
    <button onclick="logout()" style="background:rgba(255,255,255,.1);border:none;color:white;padding:5px 10px;border-radius:6px;font-size:11px;cursor:pointer;font-family:'DM Sans',sans-serif">Sign out</button>
    <button class="hb" onclick="toggleMenu()">☰</button>
  </div>
</div>
<div id="lm"></div>
<div class="ct" id="mc" style="display:none"></div>
</div>
<script>
window.onerror=function(m,s,l){const e=document.getElementById('lm');if(e&&!e.innerHTML)e.innerHTML='<div style="padding:40px;font-family:sans-serif;color:#a82222;background:#fceaea;border-radius:12px;margin:40px auto;max-width:600px"><strong>Load error</strong><br><br>'+m+'<br>Line: '+l+'</div>';return false;};
</script>
<script>
// Firebase SDK is loaded dynamically inside boot() below — static script tags
// are unreliable inside GoHighLevel custom-code blocks (stripped or loaded async),
// which caused "firebase is not defined" errors.
</script>
<script>
const USERS=[
{id:'ashlee',name:'Ashlee Montalvo',role:'admin',email:'ashlee@primehrt.clinic',password:''},
{id:'tamara',name:'Tamara Dismukes',role:'admin',email:'tamara@primehrt.clinic',password:''},
{id:'jessica',name:'Jessica Fox',role:'admin',email:'jessicafoxprime@gmail.com',password:''},
{id:'ewillis',name:'Eric Willis',role:'admin',email:'eric@primehrt.clinic',password:'',canPreview:true},
{id:'najla',name:'Najla OPS',role:'admin',email:'najla.shaaban@gmail.com',password:''},
{id:'jakemontalvo',name:'Jake Montalvo',role:'admin',email:'jake@primehrt.clinic',password:''},
{id:'kristen',name:'Kristen',role:'staff',email:'kristen@primehrt.clinic',password:'kristen1234'},
{id:'jacey',name:'Jacey Montalvo',role:'staff',email:'jacey@primehrt.clinic',password:''},
{id:'testprovider',name:'Test Provider',role:'provider',email:'testprovider',password:'1234'},
{id:'testcoord',name:'Test Coordinator',role:'coordinator',email:'testcoordinator',password:'5678'},
];
let CU=null,PR=null;
function aR(){if(!CU)return null;if(PR)return PR;return CU.role;}
function cS(f){const r=aR();const ru={admin:{orders:1,new:1,patients:1,pharmacies:1,formulary:1,invoices:1,cogs:1,portals:1,settings:1},provider:{orders:1,new:1,patients:1,pharmacies:1,formulary:1},coordinator:{orders:1,pharmacies:1,formulary:1},staff:{orders:1,new:1,patients:1,pharmacies:1,formulary:1,portals:1}};return !!(ru[r]&&ru[r][f]);}
async function loadUsers(){try{const s=await db.ref('primeHRT/users').once('value');const d=s.val();if(d)d.forEach(su=>{const u=USERS.find(x=>x.id===su.id);if(u&&su.password)u.password=su.password;});}catch(e){}}
async function saveUsers(){try{await db.ref('primeHRT/users').set(USERS.map(u=>({id:u.id,password:u.password})));}catch(e){}}
function showResetUI(){document.getElementById('lpw').value='';document.getElementById('lpw').placeholder='Type NEW password...';document.getElementById('lh').textContent='Type email and NEW password, then click Save.';const b=document.getElementById('lbm');b.textContent='Save New Password';b.onclick=executeReset;}
function executeReset(){const e=(document.getElementById('le2').value||'').trim(),p=document.getElementById('lpw').value,er=document.getElementById('lerr');if(!e){er.textContent='Please enter your email.';return;}if(!p||p.length<4){er.textContent='Password must be at least 4 characters.';return;}const u=USERS.find(u=>u.email&&u.email.toLowerCase()===e.toLowerCase());if(!u){er.textContent='Email not recognised.';return;}u.password=p;saveUsers();er.style.color='var(--sc)';er.textContent='Password reset! Logging you in...';setTimeout(()=>{er.style.color='var(--dn)';tryLogin(e,p);renderApp();},1200);}
function tryLogin(email,pw){const u=USERS.find(u=>u.email&&u.email.toLowerCase()===email.toLowerCase().trim());if(!u)return false;if(!u.password){u.password=pw;saveUsers();CU=u;PR=null;return true;}if(u.password===pw){CU=u;PR=null;return true;}return false;}
function logout(){CU=null;PR=null;ST.tab='orders';renderApp();}
function renderLogin(){return`<div class="ls"><div class="lb"><div class="ll">Compound<span>Track</span></div><div class="ls2">Prime HRT & Weight Loss</div><label class="llab">Email</label><input class="lin" id="le2" type="email" placeholder="you@primehrt.clinic" onkeydown="if(event.key==='Enter')document.getElementById('lpw').focus()"><label class="llab">Password</label><input class="lpin" id="lpw" type="password" placeholder="••••••••" style="letter-spacing:2px" onkeydown="if(event.key==='Enter')doLogin()"><div class="lh" id="lh">First login? Enter your email and set a new password.</div><div class="le" id="lerr"></div><button class="lbtn" id="lbm" onclick="doLogin()" style="margin-bottom:12px">Sign in</button><div style="text-align:center;font-size:11px"><a href="#" onclick="showResetUI();return false" style="color:var(--m);text-decoration:none;border-bottom:.5px solid var(--m)">Forgot password?</a></div></div></div>`;}
function doLogin(){const e=(document.getElementById('le2').value||'').trim(),p=document.getElementById('lpw').value,er=document.getElementById('lerr');if(!e){er.textContent='Please enter your email.';return;}if(!p||p.length<4){er.textContent='Password must be at least 4 characters.';return;}const u=USERS.find(u=>u.email&&u.email.toLowerCase()===e.toLowerCase());if(!u){er.textContent='Email not recognised.';return;}if(tryLogin(e,p)){er.textContent='';renderApp();}else{er.textContent='Incorrect password.';document.getElementById('lpw').value='';}}

const PH=[
{id:'hallandale',name:'Hallandale Pharmacy',type:'Compound 503a',ta:'48 hours',method:'LifeFile',login:'Provider login (NP/PA separately)',contact:{phone:'954-455-3822',email:'tanya@hallandalerx.com',rep:'Tanya T'},notes:'BUD law Dec 2024 — max 2×5mL testosterone vials. FORTE Tirzepatide 15mg/mL for >10mg/wk.',meds:['Female Testosterone 50mg/mL 2mL ($12)','Tirzepatide FORTE 15mg/mL 4mL ($283)','Enclomiphene 50mg ($1.50/ea)','Glutathione 30mL ($45)']},
{id:'centercity',name:'Center City Pharmacy',type:'Compound 503a+',ta:'48 hours',method:'LifeFile',login:'Provider login',contact:{phone:'813-416-6404',email:'maxb@centercityrx503a.com',rep:'Max Benson'},notes:'Can ship 10mL testosterone. Best tirzepatide pricing. 30mg ($150) / 60mg ($265).',meds:['Testosterone 200mg/mL 10mL ($40)','Tirzepatide 30mg ($150)/60mg ($265)','Semaglutide ($55/mL)']},
{id:'strive',name:'Strive Pharmacy',type:'Compound',ta:'1-2 weeks',method:'LifeFile/eRx Optimantra',login:'Provider login',contact:{phone:'507-591-6932',email:'gparsa@strivepharmacy.com',rep:'Gionna Parsa'},notes:'BUD split issue on enclomiphene = double shipping. Good for LDN, oxandrolone, stanozolol, thyroid.',meds:['LDN 4.5mg 90ct ($72)','Stanozolol 25mg ($3/ea)','NP Thyroid all strengths']},
{id:'brooksville',name:'Brooksville Pharmacy',type:'Compound',ta:'3-5 days',method:'LifeFile',login:'Provider login',contact:{phone:'352-848-3446',email:'Angel@brooksvillerx.com',rep:'Angel Felicies'},notes:'Best for high-dose testosterone, Deca, anabolics. Cheapest Armour Thyroid ($1.50/ea).',meds:['Testosterone HIGH DOSE 250mg/mL 10mL ($132)','Nandrolone (Deca) 200mg/mL','Armour Thyroid ($1.50/ea)']},
{id:'southlake',name:'Southlake Pharmacy',type:'Compound 503a',ta:'Up to 2 weeks',method:'ScriptScan Portal',login:'scriptscan.info/slpharmacy/doctor — ashlee@primehrt.clinic / ASHlou02!!',contact:{phone:'813-395-5667',email:'antoine@slcompounding.com',rep:'Antoine Prescod',cell:'407-440-1198'},notes:'TB500 only 503a source. Sermorelin 30mg best value at $5/mg.',meds:['TB500 standalone (503a)','Sermorelin 30mg ($150+ship)']},
{id:'stryker',name:'Stryker Pharmacy',type:'503a',ta:'Unknown',method:'LifeFile',login:'Provider login',contact:{phone:'',email:''},notes:'LAST RESORT — $23.50/mg Retatrutide. No North Dakota.',meds:['Retatrutide 30mg $705 (last resort)']},
{id:'betterlife',name:'BetterLife Pharmacy',type:'Compound 503a',ta:'TBD',method:'LifeFile',login:'Individual provider accounts — see Portals tab',contact:{phone:'(727) 900-6404',email:'thebetterlifepharmacy@gmail.com'},notes:'Set up by Tamara 7/26. Fax orders: (727) 900-6427. RETATRUTIDE 503a — best per-mg source anywhere (beats Stryker AND research suppliers). Watch payer-type: order forms show patient-pay prices, "Price list 8 May" shows clinic prices — some items differ (e.g. BPC-157 $150 clinic vs $175 form). Shipping rates TBD.',meds:['Retatrutide 8mg $175 / 16mg $215 / 32mg $255 / 48mg $295 (503a!)','Tirzepatide-Pyridoxine 20-25mg/mL (60-75mg 3mL $220)','Testosterone Cyp CSO 10mL ($50)','BPC-157 15mg ($150 clinic)','MIC-L-Carnitine-B12 LIPO-C 10mL ($60)','Phentermine 3.75mg 30ct ($20)']},
{id:'olympia',name:'Olympia Pharmacy',type:'503a/503b',ta:'Standard',method:'Direct portal (not LifeFile)',login:'olympiapharmacy.drscriptportal.com — Prime35754',contact:{phone:'407-673-2222',email:'Kendall.Green@olympiapharmacy.com',rep:'Kendall Green'},notes:'NOT LifeFile. Two invoice streams: Olympia + Wesley Pharmaceuticals LLC.',meds:['Glutathione 5mL ($23.80)/30mL ($51.51)','NAD+ 10mL ($64.80)','Full IV kit line']},
{id:'pdrx',name:'PDRX (In-Office)',type:'In-Office',ta:'Same day',method:'Print label in office',login:'In-office system',contact:{phone:'',email:''},notes:'In-office only. Bill before dispensing. E-FORCSE for testosterone/phentermine.',meds:['Anastrozole 1mg 90ct $0.13 (#111043)','Metformin 500mg 90ct $5.11 (#111209)','Tadalafil 5mg 90ct $11.39 (#111452)','Testosterone 200mg/mL 10mL $44.50 (#609134)']},
{id:'alphabio',name:'Alpha Bio Labs',type:'Research (drop-ship)',ta:'~48 hours',method:'Website — partner login',login:'alphabiomedlabs.com partner login',contact:{phone:'888-890-8143',email:'support@alphabiomedlabs.com',rep:'Customer Service'},notes:'SIGNED CONSENT required every order. True cost = list + $15 ship + 6.25% tax.',meds:['BPC-157/TB500 blends','GHK-Cu, KPV, Kisspeptin','Retatrutide (research)','NAD+ 1000mg']},
{id:'soma',name:'SOMA Peptides',type:'Research (office only)',ta:'Standard',method:'Direct order',login:'Direct account',contact:{phone:'888-818-6543',email:'care@somapeptides.com'},notes:'Backup for Alpha Bio. Office only. Consent required.',meds:['Retatrutide 20mg ($400 in-office)']},
{id:'nucare',name:'NuCare (In-Office)',type:'In-Office',ta:'Same day',method:'In-office',login:'In-office',contact:{phone:'714-450-6151',email:'mike@nucarerxusa.com',rep:'Mike'},notes:'HCG in office. Office stock ~$170/vial (approx — confirm w/ Mike). Patient charge $250.',meds:['HCG Pregnyl 10,000 IU — ~$170 COG / $250 patient']},
];
const PHARMACIES=PH,PN=PH.map(p=>p.name);

const FM=[
{c:'GLP-1 — Semaglutide',n:'Semaglutide 2.5mg/mL 1mL',r:[{ph:'centercity',l:'Center City',p:55},{ph:'hallandale',l:'Hallandale',p:55}],f:[]},
{c:'GLP-1 — Semaglutide',n:'Semaglutide 2.5mg/mL 4mL (10mg)',r:[{ph:'centercity',l:'Center City',p:100},{ph:'hallandale',l:'Hallandale',p:150}],f:[]},
{c:'GLP-1 — Semaglutide',n:'Semaglutide 2.5mg/mL 5mL (12.5mg)',r:[{ph:'centercity',l:'Center City',p:110},{ph:'hallandale',l:'Hallandale',p:140}],f:[]},
{c:'GLP-1 — Tirzepatide',n:'Tirzepatide/Glycine 10mg/mL 3mL (30mg)',r:[{ph:'centercity',l:'Center City',p:150,n:'≤10mg/wk — fully loaded incl. shipping'},{ph:'hallandale',l:'Hallandale',p:150}],f:[]},
{c:'GLP-1 — Tirzepatide',n:'Tirzepatide/Glycine 10mg/mL 6mL (60mg)',r:[{ph:'centercity',l:'Center City ⭐',p:205,n:'≤10mg/wk only — fully loaded incl. shipping (drug $175 + ~$30 ship)'}],f:[]},
{c:'GLP-1 — Tirzepatide',n:'Tirzepatide FORTE 15mg/mL 4mL — >10mg/wk',r:[{ph:'hallandale',l:'Hallandale ⭐',p:283,n:'Single poke >10mg/wk'}],f:['watch']},
{c:'GLP-1 — Retatrutide',n:'Retatrutide 12mg vial',r:[{ph:'alphabio',l:'Alpha Bio',p:174.38}],f:['research']},
{c:'GLP-1 — Retatrutide',n:'Retatrutide 20mg (SOMA)',r:[{ph:'soma',l:'SOMA bulk',p:129.52,n:'Office only'}],f:['research']},
{c:'GLP-1 — Retatrutide',n:'Retatrutide 24mg vial',r:[{ph:'alphabio',l:'Alpha Bio',p:280.62}],f:['research']},
{c:'GLP-1 — Retatrutide',n:'Retatrutide 60mg in-office',r:[{ph:'alphabio',l:'Alpha Bio',p:513.60}],f:['research']},
{c:'GLP-1 — Retatrutide',n:'Retatrutide 16mg (503a pharmacy)',r:[{ph:'betterlife',l:'BetterLife ⭐',p:215,n:'CONFIRMED 7/6/26 provider form. Full tiers: 8mg/$175 · 16mg/$215 · 32mg/$255 · 48mg/$295 ($6.15/mg at 48mg — beats Stryker $23.50/mg AND research suppliers). Shipping cost TBD — drug price only'}],f:['watch']},
{c:'GLP-1 — Retatrutide',n:'Retatrutide 30mg (Stryker last resort)',r:[{ph:'stryker',l:'Stryker',p:705}],f:[]},
{c:'GLP-1 — Liraglutide',n:'Liraglutide 6mg/mL 5mL',r:[{ph:'olympia',l:'Olympia',p:125},{ph:'strive',l:'Strive',p:120}],f:[]},
{c:'GLP-1 — Liraglutide',n:'Liraglutide 6mg/mL 10mL',r:[{ph:'olympia',l:'Olympia',p:215}],f:[]},
{c:'Testosterone — Male',n:'Test Cyp 200mg/mL 5mL',r:[{ph:'hallandale',l:'Hallandale',p:40,n:'GSO, fully loaded incl. shipping'},{ph:'centercity',l:'Center City',p:27.50,n:'Always ordered 2 vials/order — real per-vial fully loaded cost'}],f:['ctrl']},
{c:'Testosterone — Male',n:'Test Cyp 200mg/mL 10mL mfg',r:[{ph:'centercity',l:'Center City',p:55,n:'Fully loaded incl. shipping (drug $40 + ~$15 ship, single-vial order)'},{ph:'pdrx',l:'PDRX',p:44.50}],f:['ctrl']},
{c:'Testosterone — Male',n:'Test Cyp 250mg/mL 10mL HIGH DOSE',r:[{ph:'brooksville',l:'Brooksville',p:28}],f:['ctrl']},
{c:'Testosterone — Male',n:'Test Cyp 200mg/mL 5mL (1 bottle)',r:[{ph:'centercity',l:'Center City',p:27.50,n:'Cottonseed/mfg, 1 vial'}],f:['ctrl']},
{c:'Testosterone — Male',n:'Test Cyp 200mg/mL — 2×5mL (10mL total)',r:[{ph:'centercity',l:'Center City',p:55,n:'Cottonseed/mfg, 2 vials (most common)'}],f:['ctrl']},
{c:'Testosterone — Male',n:'Test Cyp 200mg/mL 5mL grapeseed (1 bottle)',r:[{ph:'hallandale',l:'Hallandale',p:40,n:'GSO, 1 vial'}],f:['ctrl']},
{c:'Testosterone — Male',n:'Test Cyp 200mg/mL grapeseed — 2×5mL (10mL total)',r:[{ph:'hallandale',l:'Hallandale',p:80,n:'GSO, 2 vials — shorter BUD, may need sig quantity to justify release'}],f:['ctrl','watch']},
{c:'Testosterone — Male',n:'Test Cyp 200mg/mL 5mL MCT (1 bottle)',r:[{ph:'hallandale',l:'Hallandale',p:40,n:'MCT, 1 vial'}],f:['ctrl']},
{c:'Testosterone — Male',n:'Test Cyp 200mg/mL MCT — 2×5mL (10mL total)',r:[{ph:'hallandale',l:'Hallandale',p:80,n:'MCT, 2 vials'}],f:['ctrl']},
{c:'Testosterone — Male',n:'Test Enanthate 200mg/mL 5mL',r:[{ph:'hallandale',l:'Hallandale',p:25}],f:['ctrl']},
{c:'Testosterone — Female',n:'Test 50mg/mL 2mL (female)',r:[{ph:'hallandale',l:'Hallandale',p:27,n:'Fully loaded incl. shipping (drug $12 + $15 ship, single order)'}],f:['ctrl']},
{c:'Testosterone — Female',n:'Test 25mg/mL 5mL (female MCT)',r:[{ph:'brooksville',l:'Brooksville',p:20,n:'Women\'s low-dose MCT oil'}],f:['ctrl']},
{c:'Testosterone — Female',n:'Test cream 30g Topiclick',r:[{ph:'centercity',l:'Center City ⭐',p:null,n:'PRIMARY per Ashlee 7/6/26 — known vendor, easy to work with. Catalog ~$1.34/gram (~$40/30g) but NOT invoice-confirmed; get real per-tube quote & confirm Topiclick metered dispenser + strength'},{ph:'olympia',l:'Olympia',p:61,n:'Alternate — 30g Topiclick, +$25 ship'}],f:['ctrl']},
{c:'Anabolics',n:'Stanozolol 12.5mg cap (ea)',r:[{ph:'strive',l:'Strive',p:2.20}],f:[]},
{c:'Anabolics',n:'Stanozolol 25mg cap (ea)',r:[{ph:'strive',l:'Strive',p:3.00},{ph:'brooksville',l:'Brooksville',p:5.00}],f:[]},
{c:'Anabolics',n:'Oxandrolone 2.5mg #30',r:[{ph:'strive',l:'Strive',p:48,n:'Clinic COG per Gionna (rep) + shipping. 2FA CTRL — Ashlee/Tamara only. Patient price $60'}],f:['ctrl','watch']},
{c:'Anabolics',n:'Oxandrolone 2.5mg #60',r:[{ph:'strive',l:'Strive',p:96,n:'Clinic COG per Gionna + shipping. 2FA CTRL. Patient $120'}],f:['ctrl','watch']},
{c:'Anabolics',n:'Oxandrolone 2.5mg #90',r:[{ph:'strive',l:'Strive',p:136,n:'Clinic COG per Gionna + shipping. 2FA CTRL. Patient $170'}],f:['ctrl','watch']},
{c:'Anabolics',n:'Oxandrolone 5mg #30',r:[{ph:'strive',l:'Strive',p:56,n:'Clinic COG per Gionna + shipping. 2FA CTRL. Patient $70'}],f:['ctrl','watch']},
{c:'Anabolics',n:'Oxandrolone 5mg #60',r:[{ph:'strive',l:'Strive',p:104,n:'Clinic COG per Gionna + shipping. 2FA CTRL. Patient $130'}],f:['ctrl','watch']},
{c:'Anabolics',n:'Oxandrolone 5mg #90',r:[{ph:'strive',l:'Strive',p:144,n:'Clinic COG per Gionna + shipping. 2FA CTRL. Patient $180'}],f:['ctrl','watch']},
{c:'Anabolics',n:'Oxandrolone 10mg #90',r:[{ph:'strive',l:'Strive',p:170,n:'~$1.89/cap fully loaded (invoice-confirmed). 2FA CTRL — Ashlee/Tamara only'}],f:['ctrl','watch']},
{c:'Anabolics',n:'Oxandrolone 25mg #30',r:[{ph:'strive',l:'Strive',p:108,n:'~$3.60/cap fully loaded (invoice-confirmed). 2FA CTRL'}],f:['ctrl','watch']},
{c:'Anabolics',n:'Oxandrolone 25mg #60',r:[{ph:'strive',l:'Strive',p:188,n:'~$3.13/cap fully loaded (invoice-confirmed). 2FA CTRL'}],f:['ctrl','watch']},
{c:'Anabolics',n:'Oxandrolone 25mg #90',r:[{ph:'strive',l:'Strive',p:248,n:'~$2.76/cap fully loaded (invoice-confirmed). 2FA CTRL'}],f:['ctrl','watch']},
{c:'Anabolics',n:'Nandrolone (Deca) 200mg/mL 10mL',r:[{ph:'brooksville',l:'Brooksville',p:98.00,n:'$9.80/mL fully loaded x 10mL'}],f:[]},
{c:'Anabolics',n:'Omnitrope HGH 5.8mg kit',r:[{ph:'hallandale',l:'Hallandale',p:350},{ph:'centercity',l:'Center City',p:399}],f:[]},
{c:'Fertility',n:'Enclomiphene 50mg ea',r:[{ph:'hallandale',l:'Hallandale',p:1.67,n:'Fully loaded incl. per-unit shipping share ($1.50 drug + ~$0.17 ship/tab on a 90ct order)'},{ph:'centercity',l:'Center City',p:3.50}],f:['watch']},
{c:'Fertility',n:'Enclomiphene 37.5mg (¾ of 50mg flex tab)',r:[{ph:'strive',l:'Strive',p:1.62,n:'50mg Flex-Dose tab taken as ¾ = 37.5mg dose. INVOICE-CONFIRMED $1.50/tab drug (~$1.62 loaded). Order in WHOLE tablets — use the tablet-qty calculator: 90-day supply = 68 tabs'}],f:['watch']},
{c:'Fertility',n:'Enclomiphene 50mg Flex-Dose tab (Strive)',r:[{ph:'strive',l:'Strive',p:1.62,n:'50mg flex tablet — splits for 12.5/25/37.5/50mg dosing. INVOICE-CONFIRMED $1.50/tab. Order whole tablets per the calculator'}],f:['watch']},
{c:'Fertility',n:'Enclomiphene 25mg ea',r:[{ph:'hallandale',l:'Hallandale',p:1.17,n:'Fully loaded incl. per-unit shipping share ($1.00 drug + ~$0.17 ship/tab on a 90ct order)'},{ph:'centercity',l:'Center City',p:2.00}],f:[]},
{c:'Fertility',n:'Enclomiphene 12.5mg ea',r:[{ph:'hallandale',l:'Hallandale',p:1.00}],f:[]},
{c:'Fertility',n:'HCG Pregnyl 10,000 IU',r:[{ph:'nucare',l:'NuCare (in-office)',p:170,n:'IN-OFFICE office stock ~$170/vial (APPROX per Ashlee — confirm w/ Mike). Patient charge $250 = ~$80 margin'},{ph:'strive',l:'Strive (ordered/mailed)',p:270,n:'~$270 + shipping if ordered out. APPROX — confirm on next order'},{ph:'hallandale',l:'Hallandale (ordered/mailed)',p:270,n:'~$270 + shipping if ordered out. APPROX — confirm on next order'}],f:['watch']},
{c:'Fertility',n:'Gonadorelin 200mcg/mL 5mL',r:[{ph:'brooksville',l:'Brooksville',p:25},{ph:'hallandale',l:'Hallandale',p:32}],f:[]},
{c:'Fertility',n:'Gonadorelin 200mcg/mL 10mL',r:[{ph:'brooksville',l:'Brooksville',p:40},{ph:'hallandale',l:'Hallandale',p:45}],f:[]},
{c:'Anastrozole',n:'Anastrozole 0.125mg ea',r:[{ph:'hallandale',l:'Hallandale',p:0.50},{ph:'brooksville',l:'Brooksville',p:0.65}],f:[]},
{c:'Anastrozole',n:'Anastrozole 0.5mg ea',r:[{ph:'brooksville',l:'Brooksville',p:0.65},{ph:'centercity',l:'Center City',p:0.85}],f:[]},
{c:'Anastrozole',n:'Anastrozole 1mg ea',r:[{ph:'pdrx',l:'PDRX',p:1.00},{ph:'centercity',l:'Center City',p:1.05}],f:[]},
{c:'Injectable Vitamins',n:'Glutathione 200mg/mL 10mL',r:[{ph:'southlake',l:'Southlake',p:40,n:'Fully loaded (drug $20 + $10 ground + $10 cold pack) — per 7/6/26 catalog; 2-vial $36 / 3-vial $50 drug tiers'},{ph:'hallandale',l:'Hallandale',p:null,n:'PRICE NOT YET CONFIRMED — need an invoice for this size specifically'}],f:['watch']},
{c:'Injectable Vitamins',n:'Glutathione 200mg/mL 30mL',r:[{ph:'hallandale',l:'Hallandale',p:60,n:'Fully loaded incl. shipping (drug $45 + $15 ship, single order)'},{ph:'olympia',l:'Olympia',p:61.51,n:'Fully loaded incl. shipping (drug $51.51 + ~$10 avg ship)'}],f:[]},
{c:'Injectable Vitamins',n:'B12 Methylcobalamin 5mg/mL 10mL',r:[{ph:'strive',l:'Strive',p:30},{ph:'olympia',l:'Olympia',p:51.19}],f:[]},
{c:'Injectable Vitamins',n:'B12 Methylcobalamin 5mg/mL 30mL',r:[{ph:'olympia',l:'Olympia',p:58.31}],f:[]},
{c:'Injectable Vitamins',n:'NAD+ 100mg/mL 10mL',r:[{ph:'hallandale',l:'Hallandale',p:85},{ph:'olympia',l:'Olympia',p:89.80}],f:['noorder']},
{c:'Injectable Vitamins',n:'L-Carnitine 500mg/mL 30mL',r:[{ph:'hallandale',l:'Hallandale',p:45},{ph:'strive',l:'Strive',p:45}],f:[]},
{c:'Injectable Vitamins',n:'Vitamin D3 50,000IU/mL 30mL',r:[{ph:'olympia',l:'Olympia',p:60.22,n:'Fully loaded incl. shipping (drug $53.55 + ~$6.67 avg ship)'}],f:[]},
{c:'Peptides',n:'BPC-157 15mg injectable (standalone)',r:[{ph:'southlake',l:'Southlake 503a ⭐',p:150,n:'503a pharmaceutical — Rx dispensing, NO research consent. 15mg lyophilized + mixing kit. 30mg $260 / 45mg $330'},{ph:'alphabio',l:'Alpha Bio (research)',p:103,n:'Research-grade — CONSENT form required. Wolverine blend also available'}],f:[]},
{c:'Peptides',n:'BPC-157 500mcg capsule (standalone)',r:[{ph:'southlake',l:'Southlake 503a',p:2.50,n:'CONFIRMED invoice — 503a oral cap. 100mcg $1 / 1000mcg $4'}],f:[]},
{c:'Peptides',n:'BPC-157 10mg / TB-500 10mg (Wolverine blend)',r:[{ph:'alphabio',l:'Alpha Bio (research)',p:103,n:'Research-grade blend — CONSENT required'}],f:['research']},
{c:'Peptides',n:'TB-500 (Thymosin Beta-4) standalone',r:[{ph:'southlake',l:'Southlake 503a ⭐',p:150,n:'503a — Rx dispensing, no consent. 15mg'},{ph:'alphabio',l:'Alpha Bio (research)',p:103,n:'Research — consent required (usually in Wolverine blend)'}],f:[]},
{c:'Peptides',n:'GLOW 50 — GHK-Cu 30mg/BPC/TB500',r:[{ph:'alphabio',l:'Alpha Bio',p:100}],f:['research']},
{c:'Peptides',n:'KLOW 80 — GHK-Cu 50mg/KPV/BPC/TB500',r:[{ph:'alphabio',l:'Alpha Bio',p:167.99}],f:['research']},
{c:'Peptides',n:'GHK-Cu 50mg injectable (standalone)',r:[{ph:'betterlife',l:'BetterLife 503a ⭐',p:150,n:'503a standalone copper peptide — Rx, no consent (per 5/8/26). 10mg/mL 5mL vial'},{ph:'alphabio',l:'Alpha Bio (research)',p:100,n:'Research — only in GLOW/KLOW blends, consent required'}],f:[]},
{c:'GLP-1 — Retatrutide',n:'Retatrutide 60mg (Triple Regulator, Alpha Bio research)',r:[{ph:'alphabio',l:'Alpha Bio (research)',p:513.60,n:'Research-grade — CONSENT required. This IS retatrutide 60mg. Compare: BetterLife 503a Retatrutide 48mg $295 is cheaper per-mg AND pharmaceutical'}],f:['research']},
{c:'Peptides',n:'Sermorelin 30mg vial (503a)',r:[{ph:'southlake',l:'Southlake ⭐',p:160,n:'PRIMARY — 30mg (2×15mg), 503a Rx no consent. $150 drug + $10 ship. Patient charge $250'}],f:[]},
{c:'Peptides',n:'Sermorelin 15mg vial (503a)',r:[{ph:'southlake',l:'Southlake',p:110,n:'15mg, 503a. $100 drug + $10 ship. Patient $175'}],f:[]},
{c:'Peptides',n:'Sermorelin 15mg vial Hallandale (503a)',r:[{ph:'hallandale',l:'Hallandale',p:120,n:'15mg alternate, 503a Rx no consent. Patient $175'}],f:[]},
{c:'Peptides',n:'Sermorelin 10mg vial (research)',r:[{ph:'alphabio',l:'Alpha Bio',p:84,n:'10mg research-grade — CONSENT required. Patient $150'}],f:['research']},
{c:'Peptides',n:'Tesamorelin 14mg (503a pharmacy)',r:[{ph:'southlake',l:'Southlake ⭐',p:170,n:'ONLY 503a compound pharmacy source — pharmaceutical grade, Rx dispensing, no research consent needed. Fully loaded (drug $150 + $10 ground + $10 cold pack); 28mg 2-vial tier $280 drug. Per 7/6/26 catalog'}],f:[]},
{c:'Peptides',n:'Tesamorelin 10mg (Alpha Bio research)',r:[{ph:'alphabio',l:'Alpha Bio (research)',p:96.30,n:'Research-grade — CONSENT required. South Lake 503a version preferred if no consent on file'}],f:['research']},
{c:'Peptides',n:'Kisspeptin 10mg',r:[{ph:'alphabio',l:'Alpha Bio (research)',p:107,n:'Research — CONSENT required. No 503a source currently'}],f:['research']},
{c:'Peptides',n:'NAD+ 1000mg Synthetic',r:[{ph:'alphabio',l:'Alpha Bio (research)',p:103.79,n:'Research — consent required'}],f:['research']},
{c:'Sexual Wellness',n:'Tadalafil (ALL strengths)',r:[{ph:'pdrx',l:'GoodRx at pt pharmacy',p:45,n:'ALWAYS first'}],f:['goodrx']},
{c:'Sexual Wellness',n:'Tadalafil 5mg ea (compound only)',r:[{ph:'strive',l:'Strive',p:2.00},{ph:'centercity',l:'Center City',p:2.25}],f:[]},
{c:'Sexual Wellness',n:'Sildenafil 100mg ea',r:[{ph:'centercity',l:'Center City',p:2.25},{ph:'strive',l:'Strive',p:4.00}],f:[]},
{c:'Weight / Metabolic',n:'Metformin 500mg ea',r:[{ph:'hallandale',l:'Hallandale',p:0.50},{ph:'pdrx',l:'PDRX 90ct',p:45}],f:[]},
{c:'Weight / Metabolic',n:'LDN 4.5mg 90ct',r:[{ph:'strive',l:'Strive',p:81.90,n:'$0.91/tab fully loaded x 90'}],f:[]},
{c:'Weight / Metabolic',n:'Ketotifen 1mg 90ct',r:[{ph:'strive',l:'Strive',p:78}],f:[]},
{c:'Weight / Metabolic',n:'Aminophylline/Glycyrrhetinic cream 2.5%/0.5% 60g (spot fat loss)',r:[{ph:'southlake',l:'Southlake',p:90,n:'INVOICE-CONFIRMED 7/7/26: $80 drug (60g = 2×30g @ $40, matches catalog) + $10 UPS Ground = $90/tube. Bodybuilder spot-fat-loss cream. 30g option = $50 loaded ($40+$10 ship)'}],f:[]},
{c:'Weight / Metabolic',n:'Sirolimus 5mg ea',r:[{ph:'southlake',l:'Southlake ⭐',p:2.50,n:'$0.50/mg — cheapest per mg (vs Strive 3mg at $0.80/mg); + $10 ground ship/order. Per 7/6/26 catalog'}],f:[]},
{c:'HRT — Women',n:'Progesterone 100mg cap ea',r:[{ph:'brooksville',l:'Brooksville',p:0.60},{ph:'centercity',l:'Center City',p:1.25}],f:[]},
{c:'HRT — Women',n:'Progesterone 200mg cap ea',r:[{ph:'brooksville',l:'Brooksville',p:0.60},{ph:'hallandale',l:'Hallandale',p:1.50}],f:[]},
{c:'HRT — Women',n:'Progesterone 100mg troche',r:[{ph:'strive',l:'Strive',p:null,n:'Troche form — price TBD, confirm on first order'}],f:['watch']},
{c:'HRT — Women',n:'Progesterone 200mg troche',r:[{ph:'brooksville',l:'Brooksville',p:null,n:'Troche form — price TBD, confirm on first order'}],f:['watch']},
{c:'HRT — Women',n:'Progesterone cream',r:[{ph:'',l:'TBD',p:null,n:'Available but never ordered — no source/price confirmed yet. Coordinator to source on first request'}],f:['watch']},
{c:'HRT — Women',n:'Bi-Est 80/20 cream (per gram)',r:[{ph:'hallandale',l:'Hallandale',p:1.25},{ph:'centercity',l:'Center City',p:1.34}],f:[]},
{c:'HRT — Women',n:'Estradiol cream (per gram)',r:[{ph:'betterlife',l:'BetterLife ⭐',p:1.00,n:'Cheapest confirmed — $1/gram single-ingredient HRT cream (per 5/8/26 price list). Est. ~$30/30g'},{ph:'hallandale',l:'Hallandale',p:1.25,n:'Est. from Bi-Est cream base rate'},{ph:'centercity',l:'Center City',p:1.34}],f:[]},
{c:'HRT — Women',n:'Estradiol 1.5mg capsule',r:[{ph:'betterlife',l:'BetterLife',p:1.00,n:'$1/capsule (per 5/8/26 list)'}],f:[]},
{c:'Testosterone — Female',n:'Testosterone cream — women (per gram)',r:[{ph:'betterlife',l:'BetterLife ⭐',p:1.00,n:'$1/gram single-ingredient (per 5/8/26 list). Est ~$30/30g'},{ph:'centercity',l:'Center City',p:1.34,n:'~$40/30g'},{ph:'olympia',l:'Olympia',p:null,n:'30g Topiclick $61 +$25 ship (alternate)'}],f:['ctrl']},
{c:'Testosterone — Male',n:'Testosterone cream — men (per gram)',r:[{ph:'betterlife',l:'BetterLife ⭐',p:1.00,n:'$1/gram single-ingredient (per 5/8/26 list). Higher strength/volume for male dosing'},{ph:'centercity',l:'Center City',p:1.34}],f:['ctrl']},
{c:'Testosterone — Female',n:'Testosterone LPT sublingual 500mcg tab (women)',r:[{ph:'strive',l:'Strive',p:0.62,n:'CONFIRMED invoice — liposomal sublingual tab, $0.53 drug + ship. NEW product, started on female pt'}],f:['ctrl']},
{c:'Testosterone — Male',n:'Testosterone LPT sublingual 500mcg tab (men)',r:[{ph:'strive',l:'Strive',p:0.62,n:'Same liposomal sublingual product as women\'s — available for men, none started yet. Higher qty/strength likely for male dosing'}],f:['ctrl']},
{c:'HRT — Women',n:'Euphoria/Climax cream',r:[{ph:'strive',l:'Strive',p:60},{ph:'olympia',l:'Olympia',p:90}],f:[]},
{c:'Thyroid',n:'Armour Thyroid 60mg ea',r:[{ph:'brooksville',l:'Brooksville',p:1.50},{ph:'hallandale',l:'Hallandale',p:2.25}],f:[]},
{c:'Thyroid',n:'NP Thyroid 60mg 30ct',r:[{ph:'strive',l:'Strive',p:45}],f:[]},
{c:'Thyroid',n:'Liothyronine T3 25mcg 90ct',r:[{ph:'strive',l:'Strive',p:52},{ph:'brooksville',l:'Brooksville',p:81}],f:[]},
{c:'Olympia — IV',n:'Myers Cocktail premix 10mL',r:[{ph:'olympia',l:'Olympia',p:55.01}],f:[]},
{c:'Olympia — IV',n:'B-Lean IV Kit',r:[{ph:'olympia',l:'Olympia',p:144.07}],f:[]},
{c:'Olympia — IV',n:'Lipo-Mino 30mL w/Carnitine',r:[{ph:'olympia',l:'Olympia',p:72.45}],f:[]},
{c:'In-Office (PDRX)',n:'Anastrozole 1mg 90ct (#111043)',r:[{ph:'pdrx',l:'In-office',p:0.13}],f:['inoffice']},
{c:'In-Office (PDRX)',n:'Metformin 500mg 90ct (#111209)',r:[{ph:'pdrx',l:'In-office',p:5.11}],f:['inoffice']},
{c:'In-Office (PDRX)',n:'Tadalafil 5mg 90ct (#111452)',r:[{ph:'pdrx',l:'In-office',p:11.39}],f:['inoffice']},
{c:'In-Office (PDRX)',n:'Testosterone Cyp 200mg/mL 10mL',r:[{ph:'pdrx',l:'In-office',p:44.50}],f:['ctrl','inoffice']},
{c:'IV Infusions',n:'Iron Infusion — Venofer 200mg',r:[{ph:'pdrx',l:'Henry Schein',p:95.62}],f:['inoffice']},
{c:'IV Infusions',n:'Ceftriaxone 1g vial',r:[{ph:'pdrx',l:'Henry Schein',p:0.717}],f:['inoffice']},
{c:'IV Infusions',n:'Toradol 30mg/mL 1mL',r:[{ph:'pdrx',l:'Henry Schein',p:0.66}],f:['inoffice']},
];
const FORMULARY=FM.map(x=>({cat:x.c,name:x.n,rows:x.r,flags:x.f}));

// ── STRUCTURED MEDICATION PICKER ──
// Providers pick medication → type → dose/size. Pharmacy is auto-assigned (hidden from provider).
// conc = mg per mL, used by the dosing calculator for day-supply math.
const MEDPICK={
  'Testosterone':{
    controlled:true,
    types:[
      {type:'Cottonseed oil (manufactured) — DEFAULT, most patients',options:[
        {label:'5mL (1 bottle)',conc:200,vol:5,pharmacy:'Center City Pharmacy',cog:27.50,medName:'Test Cyp 200mg/mL 5mL (1 bottle)'},
        {label:'10mL total (2 bottles) — most common',conc:200,vol:10,pharmacy:'Center City Pharmacy',cog:55,medName:'Test Cyp 200mg/mL — 2×5mL (10mL total)'},
      ]},
      {type:'Grapeseed oil (for cottonseed allergy)',budFlag:true,options:[
        {label:'5mL (1 bottle)',conc:200,vol:5,pharmacy:'Hallandale Pharmacy',cog:40,medName:'Test Cyp 200mg/mL 5mL grapeseed (1 bottle)'},
        {label:'10mL total (2 bottles) — see BUD note',conc:200,vol:10,pharmacy:'Hallandale Pharmacy',cog:80,medName:'Test Cyp 200mg/mL grapeseed — 2×5mL (10mL total)'},
      ]},
      {type:'MCT oil (standard dose)',options:[
        {label:'5mL (1 bottle)',conc:200,vol:5,pharmacy:'Hallandale Pharmacy',cog:40,medName:'Test Cyp 200mg/mL 5mL MCT (1 bottle)'},
        {label:'10mL total (2 bottles)',conc:200,vol:10,pharmacy:'Hallandale Pharmacy',cog:80,medName:'Test Cyp 200mg/mL MCT — 2×5mL (10mL total)'},
      ]},
      {type:'MCT oil — HIGH DOSE',options:[
        {label:'250mg/mL · 10mL vial',conc:250,vol:10,pharmacy:'Brooksville Pharmacy',cog:28,medName:'Test Cyp 250mg/mL 10mL HIGH DOSE'},
      ]},
      {type:"Women's — grapeseed oil",options:[
        {label:'50mg/mL · 2mL vial',conc:50,vol:2,pharmacy:'Hallandale Pharmacy',cog:27,medName:'Test 50mg/mL 2mL (female)'},
      ]},
      {type:"Women's — MCT oil",options:[
        {label:'25mg/mL · 5mL vial',conc:25,vol:5,pharmacy:'Brooksville Pharmacy',cog:20,medName:"Test 25mg/mL 5mL (female MCT)"},
      ]},
      {type:"Women's — cream (Topiclick/clicks)",options:[
        {label:'Cream, per gram — strength as prescribed',conc:null,vol:null,pharmacy:'BetterLife Pharmacy',cog:1.00,medName:'Testosterone cream — women (per gram)'},
      ]},
      {type:"Women's — liposomal SUBLINGUAL tab (no clicks)",options:[
        {label:'500mcg sublingual tablet',conc:null,vol:null,pharmacy:'Strive Pharmacy',cog:0.62,medName:'Testosterone LPT sublingual 500mcg tab (women)'},
      ]},
      {type:"Men's — cream (Topiclick/clicks)",options:[
        {label:'Cream, per gram — strength as prescribed',conc:null,vol:null,pharmacy:'BetterLife Pharmacy',cog:1.00,medName:'Testosterone cream — men (per gram)'},
      ]},
      {type:"Men's — liposomal SUBLINGUAL tab (no clicks)",options:[
        {label:'500mcg sublingual tablet',conc:null,vol:null,pharmacy:'Strive Pharmacy',cog:0.62,medName:'Testosterone LPT sublingual 500mcg tab (men)'},
      ]},
    ]
  },
  'Estradiol (Estrogen)':{
    controlled:false,
    types:[
      {type:'Cream (topical, clicks) — for patch shortage',options:[
        {label:'Cream, per gram — strength as prescribed',conc:null,vol:null,pharmacy:'BetterLife Pharmacy',cog:1.00,medName:'Estradiol cream (per gram)'},
      ]},
      {type:'Capsule (oral)',options:[
        {label:'Capsule 1.5mg — strength as prescribed',conc:null,vol:null,pharmacy:'BetterLife Pharmacy',cog:1.00,medName:'Estradiol 1.5mg capsule'},
      ]},
    ]
  },
  'Sermorelin':{
    controlled:false,
    types:[
      {type:'30mg vial (2×15mg) — PRIMARY, best value',options:[
        {label:'30mg per vial → $250 patient',conc:null,vol:null,pharmacy:'South Lake Pharmacy',cog:160,medName:'Sermorelin 30mg vial (503a)'},
      ]},
      {type:'15mg vial',options:[
        {label:'15mg per vial → $175 patient',conc:null,vol:null,pharmacy:'South Lake Pharmacy',cog:110,medName:'Sermorelin 15mg vial (503a)'},
        {label:'15mg per vial (Hallandale) → $175 patient',conc:null,vol:null,pharmacy:'Hallandale Pharmacy',cog:120,medName:'Sermorelin 15mg vial Hallandale (503a)'},
      ]},
      {type:'10mg vial (Alpha Bio — research, consent required)',options:[
        {label:'10mg per vial → $150 patient',conc:null,vol:null,pharmacy:'Alpha Bio Labs',cog:84,medName:'Sermorelin 10mg vial (research)'},
      ]},
    ]
  },
  'Oxandrolone (Anavar)':{
    controlled:true,
    types:[
      {type:'2.5mg capsule',options:[
        {label:'#30 caps (min qty)',conc:null,vol:null,pharmacy:'Strive Pharmacy',cog:48,medName:'Oxandrolone 2.5mg #30'},
        {label:'#60 caps',conc:null,vol:null,pharmacy:'Strive Pharmacy',cog:96,medName:'Oxandrolone 2.5mg #60'},
        {label:'#90 caps (max qty)',conc:null,vol:null,pharmacy:'Strive Pharmacy',cog:136,medName:'Oxandrolone 2.5mg #90'},
      ]},
      {type:'5mg capsule',options:[
        {label:'#30 caps (min qty)',conc:null,vol:null,pharmacy:'Strive Pharmacy',cog:56,medName:'Oxandrolone 5mg #30'},
        {label:'#60 caps',conc:null,vol:null,pharmacy:'Strive Pharmacy',cog:104,medName:'Oxandrolone 5mg #60'},
        {label:'#90 caps (max qty)',conc:null,vol:null,pharmacy:'Strive Pharmacy',cog:144,medName:'Oxandrolone 5mg #90'},
      ]},
      {type:'10mg capsule',options:[
        {label:'#90 caps (~$1.89/cap invoice)',conc:null,vol:null,pharmacy:'Strive Pharmacy',cog:170,medName:'Oxandrolone 10mg #90'},
      ]},
      {type:'25mg capsule',options:[
        {label:'#30 caps (~$3.60/cap invoice)',conc:null,vol:null,pharmacy:'Strive Pharmacy',cog:108,medName:'Oxandrolone 25mg #30'},
        {label:'#60 caps (~$3.13/cap invoice)',conc:null,vol:null,pharmacy:'Strive Pharmacy',cog:188,medName:'Oxandrolone 25mg #60'},
        {label:'#90 caps (~$2.76/cap invoice)',conc:null,vol:null,pharmacy:'Strive Pharmacy',cog:248,medName:'Oxandrolone 25mg #90'},
      ]},
    ]
  },
  'Progesterone':{
    controlled:false,
    types:[
      {type:'Capsule (oral)',options:[
        {label:'100mg capsule',conc:null,vol:null,pharmacy:'Brooksville Pharmacy',cog:0.60,medName:'Progesterone 100mg cap ea'},
        {label:'200mg capsule',conc:null,vol:null,pharmacy:'Brooksville Pharmacy',cog:0.60,medName:'Progesterone 200mg cap ea'},
        {label:'Custom strength (50–400mg) — type mg',custom:true,customRange:'50-400',conc:null,vol:null,pharmacy:'Brooksville Pharmacy',cog:0.60,medName:'Progesterone {MG}mg cap ea'},
      ]},
      {type:'Troche (sublingual)',options:[
        {label:'100mg troche',conc:null,vol:null,pharmacy:'Strive Pharmacy',cog:null,medName:'Progesterone 100mg troche'},
        {label:'200mg troche',conc:null,vol:null,pharmacy:'Brooksville Pharmacy',cog:null,medName:'Progesterone 200mg troche'},
        {label:'Custom strength (50–400mg) — type mg',custom:true,customRange:'50-400',conc:null,vol:null,pharmacy:'Brooksville Pharmacy',cog:null,medName:'Progesterone {MG}mg troche'},
      ]},
      {type:'Cream (topical) — available, not commonly ordered',options:[
        {label:'Cream (per gram, strength as prescribed)',conc:null,vol:null,pharmacy:'',cog:null,medName:'Progesterone cream'},
      ]},
    ]
  }
};
const HR=['Missing provider signature','BUD date delay','Awaiting billing confirmation','Out of stock','Wrong vial size','Missing patient info','Fax not received','Payment not confirmed','Research consent missing','Other'];
const SS=['Awaiting Payment Verification','Payment Confirmed — Ready to Place','Ordered','Processing','Shipped','Delivered','On Hold','Returned to Provider'];

let ST={tab:'orders',orders:[],invoices:[],mailouts:[],selOrder:null,filterStatus:'all',filterPh:'all',filterSearch:'',pharmFilter:'all',catFilter:'All',formSearch:'',newOrder:{},showNewInvoice:false,showGmailImport:false,pricingSearch:'',pricingCat:'All',pricingFilter:'all',newMailout:{},showNewMailout:false};

// ── PAYMENT STATUS STORE ──
let PS={};
async function loadPS(){try{const s=await db.ref('primeHRT/payStatus').once('value');PS=s.val()||{};}catch(e){PS={};}}
async function savePS(){try{await db.ref('primeHRT/payStatus').set(PS);}catch(e){}}

function rPB(oid,clickable){
  const ps=PS[oid];
  const clk=clickable?`onclick="event.stopPropagation();cyclePS('${oid}')" style="cursor:pointer" title="Click to update"`:'';
  if(!ps||!ps.st||ps.st==='unk')return`<span class="bdg pay-unk" ${clk}>— Unverified</span>`;
  if(ps.st==='paid')return`<span class="bdg pay-paid" ${clk}>✓ Paid</span>`;
  const a=ps.amt?` $${parseFloat(ps.amt).toFixed(2)}`:'';
  return`<span class="bdg pay-bal" ${clk}>⚠ Balance${a}</span>`;
}
function rPBR(st,amt){if(st==='paid')return`<span class="bdg pay-paid">✓ Paid</span>`;if(st==='bal'){const a=amt?` $${parseFloat(amt).toFixed(2)}`:'';return`<span class="bdg pay-bal">⚠ Balance${a}</span>`;}return`<span class="bdg pay-unk">— Unverified</span>`;}
function cyclePS(oid){const cur=PS[oid]?.st||'unk';const nx=cur==='unk'?'paid':cur==='paid'?'bal':'unk';if(!PS[oid])PS[oid]={};PS[oid].st=nx;PS[oid].ts=new Date().toISOString();PS[oid].by=CU?.name||'';savePS();render();}
function setPS(oid,st,amt){if(!PS[oid])PS[oid]={};PS[oid].st=st;PS[oid].amt=amt||0;PS[oid].ts=new Date().toISOString();PS[oid].by=CU?.name||'';savePS();render();}

// ── PAYMENT CHECKER TOOL ──
function rPCT(){
  if(!window._pu)window._pu={step:'upload'};
  const pu=window._pu;
  if(pu.step==='upload')return`
    <div class="puz" ondragover="event.preventDefault();this.classList.add('drag-over')" ondragleave="this.classList.remove('drag-over')" ondrop="event.preventDefault();this.classList.remove('drag-over');hPCSV(event.dataTransfer.files[0])">
      <div style="font-size:22px;margin-bottom:6px">📄</div>
      <div style="font-weight:600;margin-bottom:4px">Drop OptiMantra CSV here, or click to browse</div>
      <div style="font-size:11px;color:var(--m)">Export from OptiMantra: Reports → Superbill or Aging Report → Export CSV</div>
      <input type="file" id="pcfi" accept=".csv,.txt" style="display:none" onchange="hPCSV(this.files[0])">
      <button class="btn sm" style="margin-top:10px" onclick="document.getElementById('pcfi').click()">Browse file</button>
    </div>
    <div style="margin-top:10px;text-align:center;font-size:11px;color:var(--m)">— or manually update one patient —</div>
    <div style="margin-top:8px;display:flex;gap:8px;flex-wrap:wrap">
      <input id="pmn" style="flex:2;min-width:160px;padding:7px 10px;border:.5px solid var(--b);border-radius:8px;font-size:12px;font-family:'DM Sans',sans-serif" placeholder="Patient name (as in the tracker)">
      <select id="pms" style="flex:1;min-width:120px;padding:7px 9px;border:.5px solid var(--b);border-radius:8px;font-size:12px;font-family:'DM Sans',sans-serif">
        <option value="paid">✓ Paid in full</option><option value="bal">⚠ Has balance</option>
      </select>
      <input id="pma" type="number" step="0.01" placeholder="Balance $" style="flex:1;min-width:90px;padding:7px 9px;border:.5px solid var(--b);border-radius:8px;font-size:12px;font-family:'DM Mono',monospace">
      <button class="btn p" onclick="applyMPS()">Apply</button>
    </div>`;
  if(pu.step==='map'){
    const h=pu.headers||[];
    const nO=h.map(c=>`<option value="${c}" ${c.toLowerCase().includes('name')||c.toLowerCase().includes('patient')?'selected':''}>${c}</option>`).join('');
    const bO=`<option value="">— not in file —</option>`+h.map(c=>`<option value="${c}" ${c.toLowerCase().includes('bal')?'selected':''}>${c}</option>`).join('');
    const pO=`<option value="">— not in file —</option>`+h.map(c=>`<option value="${c}" ${c.toLowerCase().includes('paid')||c.toLowerCase().includes('payment')?'selected':''}>${c}</option>`).join('');
    const cO=`<option value="">— not in file —</option>`+h.map(c=>`<option value="${c}" ${c.toLowerCase().includes('charge')||c.toLowerCase().includes('total')?'selected':''}>${c}</option>`).join('');
    return`<div class="al in" style="margin-bottom:10px">✓ File loaded — <strong>${pu.rawRows.length} rows</strong>. Match the columns then click Run.</div>
      <div class="pcm"><div><label>Patient name column *</label><select id="cn1">${nO}</select></div><div><label>Balance owed column</label><select id="cb1">${bO}</select></div><div><label>Amount paid column</label><select id="cp1">${pO}</select></div><div><label>Total charge column</label><select id="cc1">${cO}</select></div></div>
      <div style="display:flex;gap:8px"><button class="btn p" onclick="runPM()">▶ Run matching</button><button class="btn" onclick="window._pu={step:'upload'};render()">← Start over</button></div>`;}
  if(pu.step==='results'){
    const m=pu.matches||[],mt=m.filter(x=>x.oid),um=m.filter(x=>!x.oid);
    return`<div style="display:flex;gap:10px;margin-bottom:10px;flex-wrap:wrap;align-items:center">
        <div class="al sc" style="margin:0;flex:1">✓ <strong>${mt.length}</strong> orders matched and updated</div>
        ${um.length?`<div class="al wn" style="margin:0;flex:1">⚠ <strong>${um.length}</strong> names couldn't be matched</div>`:''}
        <button class="btn sm p" onclick="window._pu={step:'upload'};render()">Upload another</button>
      </div>
      <div style="font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.4px;color:var(--m);margin-bottom:6px">Matched orders</div>
      <div style="max-height:200px;overflow-y:auto;border:.5px solid var(--b);border-radius:8px;background:var(--s)">
        ${mt.map(x=>`<div class="pmr"><span style="flex:1;font-weight:500">${x.tn}</span><span style="flex:1;color:var(--m);font-size:11px;font-family:'DM Mono',monospace">${x.on}</span><span style="min-width:110px">${rPBR(x.st,x.amt)}</span><span style="font-size:10px;color:var(--m);min-width:50px;text-align:right">${x.sc}%</span></div>`).join('')}
      </div>
      ${um.length?`<div style="font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.4px;color:var(--m);margin:10px 0 6px">Unmatched — assign manually</div>
        <div style="border:.5px solid var(--b);border-radius:8px;background:var(--s);max-height:160px;overflow-y:auto">
          ${um.map(x=>{const sk=x.on.replace(/[^a-zA-Z0-9]/g,'_');return`<div class="pmr"><span style="flex:1.5;color:var(--m);font-size:11px;font-family:'DM Mono',monospace">${x.on}</span><span style="min-width:110px">${rPBR(x.st,x.amt)}</span><div style="display:flex;gap:6px;align-items:center"><select id="um_${sk}" style="padding:4px 7px;border:.5px solid var(--b);border-radius:6px;font-size:11px;font-family:'DM Sans',sans-serif;max-width:160px"><option value="">Select order...</option>${ST.orders.map(o=>`<option value="${o.id}">${o.patientName} — ${o.medication.substring(0,20)}</option>`).join('')}</select><button class="btn sm" onclick="applyUM('${x.on.replace(/'/g,"\\'")}','${sk}','${x.st}',${x.amt||0})">Apply</button></div></div>`;}).join('')}
        </div>`:``}`;
  }
  return'';
}

function hPCSV(file){if(!file)return;const r=new FileReader();r.onload=e=>{const rows=pCSV(e.target.result);if(!rows.length){alert('Could not read file — make sure it is a CSV.');return;}window._pu={step:'map',headers:Object.keys(rows[0]),rawRows:rows};render();};r.readAsText(file);}
function pCSV(text){const lines=text.trim().split(/\r?\n/);if(lines.length<2)return[];const hdrs=sCSVL(lines[0]);return lines.slice(1).filter(l=>l.trim()).map(l=>{const v=sCSVL(l);const o={};hdrs.forEach((h,i)=>{o[h.trim()]=(v[i]||'').trim();});return o;});}
function sCSVL(line){const r=[];let cur='',inQ=false;for(let i=0;i<line.length;i++){const c=line[i];if(c==='"'){inQ=!inQ;continue;}if(c===','&&!inQ){r.push(cur);cur='';continue;}cur+=c;}r.push(cur);return r;}
function runPM(){const pu=window._pu,cN=document.getElementById('cn1')?.value,cB=document.getElementById('cb1')?.value,cP=document.getElementById('cp1')?.value,cC=document.getElementById('cc1')?.value;if(!cN){alert('Please select the patient name column.');return;}const matches=[];pu.rawRows.forEach(row=>{const on=(row[cN]||'').trim();if(!on)return;const bal=cB?parseFloat((row[cB]||'0').replace(/[$,]/g,''))||0:0;const paid=cP?parseFloat((row[cP]||'0').replace(/[$,]/g,''))||0:0;const charge=cC?parseFloat((row[cC]||'0').replace(/[$,]/g,''))||0:0;let st='unk';if(cB&&bal>0.50)st='bal';else if(cB&&bal<=0.50)st='paid';else if(cP&&cC&&paid>=charge-0.50)st='paid';else if(cP&&cC&&paid<charge-0.50)st='bal';else if(cP&&paid>0)st='paid';const{oid,tn,sc}=fMP(on);if(oid&&sc>=70){PS[oid]={st,amt:bal||(charge-paid)||0,optiName:on,ts:new Date().toISOString(),by:CU?.name||'CSV import'};matches.push({oid,tn,on,st,amt:bal,sc});}else{matches.push({oid:null,tn:null,on,st,amt:bal,sc:sc||0});}});savePS();pu.step='results';pu.matches=matches;render();}
function fMP(optiName){if(!optiName)return{oid:null,tn:null,sc:0};const nm=n=>n.toLowerCase().replace(/[,.]/g,' ').replace(/\s+/g,' ').trim();const nO=nm(optiName),pts=nO.split(' '),rev=pts.length>=2?pts.slice(1).join(' ')+' '+pts[0]:nO;let best={oid:null,tn:null,sc:0};const seen=new Set();ST.orders.forEach(o=>{if(!o.patientName||seen.has(o.patientName.toLowerCase()))return;seen.add(o.patientName.toLowerCase());const nT=nm(o.patientName);const sc=Math.round(Math.max(dSim(nO,nT),dSim(rev,nT))*100);if(sc>best.sc)best={oid:o.id,tn:o.patientName,sc};});return best;}
function dSim(a,b){if(a===b)return 1;if(a.length<2||b.length<2)return 0;const bg=s=>{const m=new Map();for(let i=0;i<s.length-1;i++){const k=s.slice(i,i+2);m.set(k,(m.get(k)||0)+1);}return m;};const aG=bg(a),bG=bg(b);let n=0;aG.forEach((c,k)=>{n+=Math.min(c,bG.get(k)||0);});return(2*n)/(a.length+b.length-2);}
function applyMPS(){const nmEl=document.getElementById('pmn'),stEl=document.getElementById('pms'),amtEl=document.getElementById('pma'),on=nmEl?.value?.trim();if(!on){alert('Enter the patient name.');return;}const{oid,tn,sc}=fMP(on);if(!oid||sc<60){alert(`Could not find a match for "${on}" (best score: ${sc}%). Check the spelling.`);return;}const st=stEl?.value||'paid',amt=parseFloat(amtEl?.value)||0;setPS(oid,st,amt);if(nmEl)nmEl.value='';if(amtEl)amtEl.value='';toast(`✓ ${tn} marked as ${st==='paid'?'Paid in full':'Balance $'+amt.toFixed(2)} (${sc}% match)`);}
function applyUM(on,sk,st,amt){const sel=document.getElementById(`um_${sk}`);if(!sel?.value){alert('Select an order.');return;}setPS(sel.value,st,amt);window._pu.matches=window._pu.matches.filter(x=>x.on!==on);render();}

const FC={apiKey:"AIzaSyCAOlkUIwNxn-7EzndUucWDC_MXOYbbInY",authDomain:"primehrt-tracker.firebaseapp.com",databaseURL:"https://primehrt-tracker-default-rtdb.firebaseio.com",projectId:"primehrt-tracker",storageBucket:"primehrt-tracker.firebasestorage.app",messagingSenderId:"611243668328",appId:"1:611243668328:web:0b8baf66661e269da124dd"};
let db=null;
function loadScript(src){return new Promise((res,rej)=>{const s=document.createElement('script');s.src=src;s.onload=res;s.onerror=()=>rej(new Error('Failed to load '+src));document.head.appendChild(s);});}
async function initFirebase(){
  if(typeof firebase==='undefined'||!firebase.database){
    try{
      await loadScript('https://www.gstatic.com/firebasejs/8.10.1/firebase-app.js');
      await loadScript('https://www.gstatic.com/firebasejs/8.10.1/firebase-database.js');
    }catch(e){
      try{
        await loadScript('https://cdn.jsdelivr.net/npm/firebase@8.10.1/firebase-app.js');
        await loadScript('https://cdn.jsdelivr.net/npm/firebase@8.10.1/firebase-database.js');
      }catch(e2){
        await loadScript('https://cdnjs.cloudflare.com/ajax/libs/firebase/8.10.1/firebase-app.js');
        await loadScript('https://cdnjs.cloudflare.com/ajax/libs/firebase/8.10.1/firebase-database.js');
      }
    }
  }
  if(!firebase.apps.length)firebase.initializeApp(FC);
  db=firebase.database();
}

async function load(){
  db.ref('primeHRT/orders').on('value',s=>{ST.orders=s.val()||[];render();});
  db.ref('primeHRT/invoices').on('value',s=>{ST.invoices=s.val()||[];render();});
  db.ref('primeHRT/mailouts').on('value',s=>{ST.mailouts=s.val()||[];render();});
  db.ref('primeHRT/patientPrices').on('value',s=>{const d=s.val();if(d&&Array.isArray(d)){const o={};d.forEach(i=>{if(i.name)o[i.name]=i.price;});PP={...DP,...o};if(ST.tab==='pricing')renderPT();}});
}
async function sO(){try{await db.ref('primeHRT/orders').set(JSON.parse(JSON.stringify(ST.orders)));}catch(e){}}
async function sMO(){try{await db.ref('primeHRT/mailouts').set(JSON.parse(JSON.stringify(ST.mailouts)));}catch(e){}}
async function sI(){try{await db.ref('primeHRT/invoices').set(JSON.parse(JSON.stringify(ST.invoices)));}catch(e){}}
async function sPP(){try{await db.ref('primeHRT/patientPrices').set(Object.entries(PP).map(([k,v])=>({name:k,price:v})));}catch(e){}}

function toggleMenu(){document.getElementById('nav').classList.toggle('open');}
function go(tab){ST.tab=tab;ST.selOrder=null;const n=document.getElementById('nav');if(n)n.classList.remove('open');renderApp();}
let _rt=null;
function dR(){clearTimeout(_rt);_rt=setTimeout(render,180);}

function render(){
  document.querySelectorAll('.nv button').forEach(b=>b.classList.remove('active'));
  const tb2=document.getElementById('tab-'+ST.tab);if(tb2)tb2.classList.add('active');
  const role=aR(),isP=role==='provider';
  const oV=isP?rCO:rO,fV=isP?rFFR:rF;
  if(typeof window._fx==='undefined'){const tmp=rD;window.rD=rCD;window.rCD=tmp;window._fx=true;}
  const fns={orders:oV,new:rN,mailout:rMO,patients:rPt,pharmacies:rPh,formulary:fV,invoices:rInv,pricing:rPr,portals:rPor,settings:rSet,ai:rAI};
  document.getElementById('mc').innerHTML=(fns[ST.tab]||rO)();
  const ib=document.getElementById('do_gi');
  if(ib)ib.addEventListener('click',function(){iIG(document.getElementById('gi_in')?.value||'');});
}

function sCls(s){return s?s.toLowerCase().replace(/[ —\/]+/g,'-').replace(/[^a-z0-9-]/g,''):'awaiting-payment-verification';}
function oRC(o){if(o.onSubscription)return 'rsb';const ip=!!o.orderNumber&&!['Delivered'].includes(o.status);const no=!o.orderNumber&&!['Delivered','On Hold','Returned to Provider'].includes(o.status);if(ip)return 'rip';if(no)return 'rno';return '';}

function rO(){
  const all=ST.orders;
  if(ST.selOrder){const o=all.find(x=>x.id===ST.selOrder);if(o){return`<div style="max-width:680px"><div style="display:flex;align-items:center;gap:10px;margin-bottom:14px"><button onclick="ST.selOrder=null;render()" style="background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.2);color:#fff;padding:7px 14px;border-radius:8px;font-size:12px;cursor:pointer;font-family:'DM Sans',sans-serif">← Back</button><span style="font-size:13px;color:rgba(255,255,255,.8);font-weight:500">${o.patientName} — ${o.medication}</span></div><div class="cd cp">${rD(o)}</div></div>`;}}
  const aw=all.filter(o=>o.status==='Awaiting Payment Verification').length,rp=all.filter(o=>o.status==='Payment Confirmed — Ready to Place').length,hd=all.filter(o=>o.status==='On Hold'||o.status==='Returned to Provider').length,ac=all.filter(o=>['Ordered','Processing'].includes(o.status)).length;
  const pyPd=all.filter(o=>PS[o.id]?.st==='paid').length,pyBl=all.filter(o=>PS[o.id]?.st==='bal').length,pyUk=all.filter(o=>!PS[o.id]||PS[o.id]?.st==='unk'||!PS[o.id]?.st).length;
  return`<div class="sts"><div class="st"><div class="stl">Awaiting payment</div><div class="stv ${aw>0?'wn':''}">${aw}</div></div><div class="st"><div class="stl">Ready to place</div><div class="stv ${rp>0?'sc':''}">${rp}</div></div><div class="st"><div class="stl">Active</div><div class="stv">${ac}</div></div><div class="st"><div class="stl">On hold/returned</div><div class="stv ${hd>0?'dn':''}">${hd}</div></div></div>
  <div class="sts" style="margin-bottom:8px"><div class="st"><div class="stl">✓ Paid in full</div><div class="stv sc">${pyPd}</div></div><div class="st"><div class="stl">⚠ Has balance</div><div class="stv ${pyBl>0?'dn':''}">${pyBl}</div></div><div class="st"><div class="stl">— Unverified</div><div class="stv ${pyUk>0?'wn':''}">${pyUk}</div></div><div class="st"><div class="stl">Total orders</div><div class="stv">${all.length}</div></div></div>
  ${rColl('pay_ck','💳 Payment Status Checker',rPCT(),'var(--sc)')}
  ${rColl('ph_lu','🔍 Pharmacy Lookup',`<input id="phLI" style="width:100%;padding:8px 11px;border:.5px solid var(--b);border-radius:8px;font-size:13px;font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--t)" list="phLL" placeholder="Start typing a medication..." oninput="rPhL(this.value)" autocomplete="off"><datalist id="phLL">${FORMULARY.filter(f=>f.rows.some(r=>r.p>0)).map(f=>`<option value="${f.name}">`).join('')}</datalist><div id="phLR" style="margin-top:8px"></div>`,'var(--in)')}
  <div class="cd"><div style="display:flex;gap:7px;padding:12px 14px;border-bottom:.5px solid var(--b);flex-wrap:wrap;align-items:center"><input id="osi" placeholder="Search patient or medication..." value="${ST.filterSearch}" oninput="ST.filterSearch=this.value;rOT()" style="flex:1;min-width:180px;padding:7px 10px;border:.5px solid var(--b);border-radius:8px;font-size:12px;font-family:'DM Sans',sans-serif;outline:none"><select onchange="ST.filterStatus=this.value;rOT()" style="padding:7px 10px;border:.5px solid var(--b);border-radius:8px;font-size:12px;font-family:'DM Sans',sans-serif;min-width:140px"><option value="all">All statuses</option>${SS.map(s=>`<option ${ST.filterStatus===s?'selected':''}>${s}</option>`).join('')}</select><select onchange="ST.filterPh=this.value;rOT()" style="padding:7px 10px;border:.5px solid var(--b);border-radius:8px;font-size:12px;font-family:'DM Sans',sans-serif;min-width:140px"><option value="all">All pharmacies</option>${PN.map(n=>`<option ${ST.filterPh===n?'selected':''}>${n}</option>`).join('')}</select><button class="btn p" onclick="go('new')">+ New order</button></div><div id="otb">${rOTH()}</div></div>`;
}

function rOT(){const el=document.getElementById('otb');if(el)el.innerHTML=rOTH();}
function rOTH(){
  const role=aR(),hP=role==='provider'||role==='staff';
  const shown=ST.orders.filter(o=>{if(ST.filterStatus!=='all'&&o.status!==ST.filterStatus)return false;if(ST.filterPh!=='all'&&o.pharmacy!==ST.filterPh)return false;if(ST.filterSearch){const s=ST.filterSearch.toLowerCase();if(!o.patientName.toLowerCase().includes(s)&&!o.medication.toLowerCase().includes(s))return false;}return true;});
  if(!shown.length)return`<div class="emp">${ST.orders.length===0?'No orders yet.':'No results match.'}</div>`;
  return`<table><thead><tr><th>Patient</th><th>Medication</th>${!hP?'<th>Pharmacy</th>':''}<th>Status</th><th>Payment</th><th>Ordered</th><th>Order#/Tracking</th><th></th></tr></thead><tbody>${shown.map(o=>{
    const rec=gPR(o.medication),pd=o.pharmacy||(rec?'→ '+rec.pN:'—'),iS=['Ordered','Shipped','Delivered'].includes(o.status);
    return`<tr class="${oRC(o)}" style="cursor:pointer;opacity:${iS?.75:1}" onclick="selO('${o.id}')">
    <td style="display:flex;align-items:center;gap:8px"><div onclick="event.stopPropagation();toggleSentStatus('${o.id}')" style="width:20px;height:20px;border-radius:6px;border:1px solid ${iS?'var(--sc)':'var(--b)'};background:${iS?'var(--sc)':'#fff'};display:flex;align-items:center;justify-content:center;color:white;cursor:pointer">${iS?'<span style="font-size:14px;line-height:1;font-weight:bold">✓</span>':''}</div>
    <div><strong>${o.patientName}</strong><span style="cursor:pointer;font-size:12px;margin-left:4px" onclick="event.stopPropagation();editPatientInfo('${o.id}')">✏️</span>${o.onSubscription?' <span class="bdg on-subscription" style="min-width:auto;margin-left:4px;font-size:9px">📋 Sub</span>':''}${o.patientDOB?`<br><span style="color:var(--m);font-size:10px">${o.patientDOB}</span>`:''}</div></td>
    <td><div style="font-weight:600">${o.medication}</div>${o.quantity||o.daySupply?`<div style="font-size:10px;color:var(--m);margin-top:2px">${o.quantity?`Qty ${o.quantity}`:''}${o.quantity&&o.daySupply?' · ':''}${o.daySupply?`${o.daySupply}d supply`:''}</div>`:''}${o.sig?`<div style="font-size:11px;color:var(--in);margin-top:3px;font-family:'DM Mono',monospace;background:var(--inb);padding:3px 6px;border-radius:4px">→ ${o.sig}</div>`:''}</td>
    ${!hP?`<td style="font-size:11px;color:var(--in)">${pd}</td>`:''}
    <td><span class="bdg ${sCls(o.status)}">${o.status}</span>${o.onSubscription?'<br><span style="font-size:10px;color:#7c3aed;font-weight:600;margin-top:3px;display:block">📋 Subscription</span>':''}</td>
    <td onclick="event.stopPropagation()">${rPB(o.id,true)}</td>
    <td style="font-size:11px;color:var(--m)">${o.dateOrdered||'—'}</td>
    <td style="font-size:11px">${o.orderNumber?`<div style="color:var(--sc);font-family:'DM Mono',monospace;font-weight:600">🧾 ${o.orderNumber}</div>`:''}${o.trackingNumber?`<div>🚚 ${o.trackingNumber}</div>`:''}${!o.orderNumber&&!o.trackingNumber?'<span style="color:var(--m)">Pending</span>':''}</td>
    <td onclick="event.stopPropagation()"><button class="btn sm dn" style="padding:4px 8px" onclick="dOrd('${o.id}')">🗑️</button></td></tr>`;
  }).join('')}</tbody></table>`;
}

function rColl(id,label,body,color){
  if(!window._cl)window._cl={};if(window._cl[id]===undefined)window._cl[id]=false;const open=window._cl[id];
  return`<div class="cd cp" style="margin-bottom:8px;border-color:${open?color:'var(--b)'}"><div style="display:flex;align-items:center;justify-content:space-between;cursor:pointer;user-select:none" onclick="window._cl['${id}']=!window._cl['${id}'];render()"><div style="font-size:11px;font-weight:600;text-transform:uppercase;letter-spacing:.4px;color:${open?color:'var(--m)'}">${label}</div><div style="font-size:16px;color:var(--m);line-height:1">${open?'▲':'▼'}</div></div>${open?`<div style="margin-top:12px">${body}</div>`:''}</div>`;
}

function selO(id){ST.selOrder=ST.selOrder===id?null:id;render();}

function rD(o){
  const ph=PHARMACIES.find(p=>p.name===o.pharmacy);
  return`<div class="dt"><div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px"><strong>${o.patientName} — ${o.medication}</strong><button class="btn sm" onclick="ST.selOrder=null;render()">✕</button></div>
  ${o.onSubscription?'<div class="al in" style="margin-bottom:8px">📋 <strong>Subscription patient</strong> — do not charge separately.</div>':''}
  <div class="dr"><span class="dl">Provider billed</span><span>${o.billingConfirmed?'✓ Yes':'⚠ Not confirmed'}</span></div>
  <div class="dr"><span class="dl">On subscription</span><span style="display:flex;gap:6px;align-items:center">${o.onSubscription?'<span style="color:#7c3aed;font-weight:600">✓ Monthly</span>':'<span style="color:var(--m)">No</span>'}<button class="btn sm" style="padding:4px 10px;font-size:11px" onclick="uO('${o.id}','onSubscription',!${!!o.onSubscription});render()">${o.onSubscription?'Remove':'Mark subscription'}</button></span></div>
  <div class="dr"><span class="dl">OptiMantra payment</span>
    <span style="display:flex;gap:6px;align-items:center;flex-wrap:wrap">
      ${rPB(o.id,false)}
      <button class="btn sm" onclick="setPS('${o.id}','paid',0)">✓ Mark paid</button>
      <span style="display:flex;align-items:center;gap:4px">
        <input type="number" id="ba_${o.id}" placeholder="$ balance" step="0.01" style="width:80px;padding:4px 7px;border:.5px solid var(--b);border-radius:6px;font-size:11px;font-family:'DM Mono',monospace">
        <button class="btn sm dn" onclick="setPS('${o.id}','bal',parseFloat(document.getElementById('ba_${o.id}').value)||0)">Set balance</button>
      </span>
    </span>
  </div>
  <div class="dr"><span class="dl">Patient paid</span><span style="display:flex;gap:6px;align-items:center">${o.patientPaid?'<span style="color:var(--sc);font-weight:600">✓ Paid</span>':'<span style="color:var(--wn)">⏳ Not confirmed</span>'}<button class="btn sm" style="padding:4px 10px;font-size:11px" onclick="uO('${o.id}','patientPaid',!${!!o.patientPaid});render()">${o.patientPaid?'Mark unpaid':'Mark paid'}</button></span></div>
  <div class="dr"><span class="dl">Order #</span><span>${o.orderNumber?`<span style="font-family:'DM Mono',monospace;font-weight:600">${o.orderNumber}</span>`:'<span style="color:var(--m)">Not placed</span>'}</span></div>
  <div class="dr"><span class="dl">Tracking #</span><span>${o.trackingNumber?`<span style="font-family:'DM Mono',monospace">${o.trackingNumber}</span>`:'<span style="color:var(--m)">Pending</span>'}</span></div>
  <div class="dr"><span class="dl">Status</span><span><select style="padding:4px 8px;border:.5px solid var(--b);border-radius:6px;font-size:12px;font-family:'DM Sans',sans-serif" onchange="uO('${o.id}','status',this.value)">${SS.map(s=>`<option ${o.status===s?'selected':''}>${s}</option>`).join('')}</select></span></div>
  <div class="dr"><span class="dl">Method</span><span>${o.method||ph?.method||'—'}</span></div>
  <div class="dr"><span class="dl">Ordered by</span><span>${o.orderedBy||'—'}</span></div>
  ${o.sig?`<div class="dr"><span class="dl">Sig</span><span style="font-family:'DM Mono',monospace;font-size:12px;font-weight:600">${o.sig}</span></div>`:''}
  ${o.quantity||o.daySupply?`<div class="dr"><span class="dl">Qty / Day supply</span><span style="font-family:'DM Mono',monospace;font-size:12px;font-weight:600">${o.quantity?`Qty: ${o.quantity}`:''}${o.quantity&&o.daySupply?' · ':''}${o.daySupply?`${o.daySupply}-day supply`:''}</span></div>`:''}
  ${o.controlled?`<div class="dr"><span class="dl">Controlled</span><span style="color:var(--dn)">Print → wet sig → fax</span></div>`:''}
  <div style="margin-top:10px"><label style="font-size:10px;color:var(--m);font-weight:500;text-transform:uppercase;letter-spacing:.3px;display:block;margin-bottom:4px">Hold reason</label>
  <div style="display:flex;gap:6px;margin-bottom:6px"><select id="hr_${o.id}" style="flex:1;padding:6px 8px;border:.5px solid var(--b);border-radius:6px;font-size:12px;font-family:'DM Sans',sans-serif"><option value="">Select...</option>${HR.map(r=>`<option ${o.holdReason===r?'selected':''}>${r}</option>`).join('')}</select><button class="btn sm" onclick="uO('${o.id}','holdReason',document.getElementById('hr_${o.id}').value)">Set</button></div>
  ${o.holdReason?`<div class="hn">Hold: ${o.holdReason}</div>`:''}</div>
  <div style="margin-top:10px"><label style="font-size:10px;color:var(--m);font-weight:500;text-transform:uppercase;letter-spacing:.3px;display:block;margin-bottom:4px">Staff notes</label>
  <textarea id="nt_${o.id}" style="width:100%;padding:7px 9px;border:.5px solid var(--b);border-radius:6px;font-size:12px;font-family:'DM Sans',sans-serif;min-height:56px;resize:vertical" placeholder="Add a note...">${o.notes||''}</textarea>
  <button class="btn sm" style="margin-top:4px" onclick="uO('${o.id}','notes',document.getElementById('nt_${o.id}').value)">Save note</button></div>
  <div style="margin-top:10px;display:flex;gap:6px">${o.status==='Returned to Provider'?`<button class="btn sm p" onclick="resubO('${o.id}')">↩ Edit & resubmit</button>`:''}<button class="btn sm dn" onclick="dOrd('${o.id}')">Delete order</button></div></div>`;
}

function uO(id,f,v){const o=ST.orders.find(x=>x.id===id);if(o){o[f]=v;sO();render();}}
function dOrd(id){if(confirm('Delete this order?')){ST.orders=ST.orders.filter(o=>o.id!==id);ST.selOrder=null;sO();render();}}
function resubO(id){const o=ST.orders.find(x=>x.id===id);if(!o)return;ST.newOrder={patientName:o.patientName,patientDOB:o.patientDOB,pharmacy:o.pharmacy,medication:o.medication,method:o.method,orderedBy:o.orderedBy,controlled:o.controlled,researchConsent:o.researchConsent,billingConfirmed:o.billingConfirmed,notes:o.notes,returnedReason:o.returnedReason};ST.orders=ST.orders.filter(x=>x.id!==id);ST.selOrder=null;sO();ST.tab='new';renderApp();}
function oCR(sid){const src=ST.orders.find(x=>x.id===sid);if(!src)return;const rec=gPR(src.medication);CLO={id:'ord_'+Date.now(),patientName:src.patientName,patientDOB:src.patientDOB||'',medication:src.medication,pharmacy:src.pharmacy||rec?.pN||'',method:src.method||'',controlled:src.controlled||false,researchConsent:src.researchConsent||false,onSubscription:src.onSubscription||false,orderedBy:src.orderedBy||CU.name,billingConfirmed:false,paymentVerifiedInOpti:false,status:'Awaiting Payment Verification',dateOrdered:new Date().toISOString().split('T')[0],_rec:rec};CLD=[];CS=0;rCOL();}

function rN(){
  const o=ST.newOrder,role=aR(),ps=o._providerPlaced;
  const mp=o.medication?(()=>{const m=FORMULARY.find(f=>f.name===o.medication);return m?(PP[m.name]||null):null;})():null;
  return`<div style="max-width:560px"><div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px"><h2 style="font-size:16px;font-weight:600;color:#fff">New medication order</h2><button class="btn sm" onclick="go('orders')" style="background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.2);color:#fff">✕</button></div>
  ${o.onSubscription?`<div class="al" style="background:#ede9fe;border-color:#c4b5fd;color:#6d28d9">📋 Subscription — do not charge for this fill.</div>`:''}
  ${o.controlled?`<div class="al wn">⚠ Controlled — print, wet signature, fax to pharmacy.</div>`:''}
  <div class="cd cp">
    <div class="f2" style="margin-bottom:0"><div class="fr"><label>Patient name *</label><input value="${o.patientName||''}" placeholder="Full name" oninput="ST.newOrder.patientName=this.value"></div><div class="fr"><label>Date of birth *</label><input value="${o.patientDOB||''}" placeholder="MM/DD/YYYY" oninput="ST.newOrder.patientDOB=this.value"></div></div>
    <div class="f2"><div class="fr"><label>Ordering provider *</label><select onchange="ST.newOrder.orderedBy=this.value"><option value="">Select provider...</option><option value="Ashlee Montalvo NP" ${o.orderedBy==='Ashlee Montalvo NP'?'selected':''}>Ashlee Montalvo NP</option><option value="Tamara Dismukes PA" ${o.orderedBy==='Tamara Dismukes PA'?'selected':''}>Tamara Dismukes PA</option><option value="Leniel Santana MD" ${o.orderedBy==='Leniel Santana MD'?'selected':''}>Leniel Santana MD</option></select></div><div class="fr"><label>Date ordered</label><input type="date" value="${o.dateOrdered||new Date().toISOString().split('T')[0]}" onchange="ST.newOrder.dateOrdered=this.value"></div></div>
    <div style="font-size:11px;color:var(--m);margin:-4px 0 10px;padding:6px 10px;background:var(--bg);border-radius:6px">📝 Placing this order as: <strong style="color:var(--t)">${CU?CU.name:'—'}</strong>${CU&&aR()!=='provider'?' (staff — recorded for provider above)':''}</div>
    <div class="fr" style="margin-bottom:0"><label>Medication *</label>
      <select id="medsel" onchange="pickMed(this.value)" style="width:100%;padding:8px 10px;border:.5px solid var(--b);border-radius:8px;background:var(--s);color:var(--t);font-size:13px;font-family:'DM Sans',sans-serif">
        <option value="">Select medication...</option>
        <optgroup label="⭐ Guided pick (type &amp; dose)">
          <option value="__Testosterone" ${o._structured==='Testosterone'?'selected':''}>Testosterone</option>
          <option value="__Estradiol (Estrogen)" ${o._structured==='Estradiol (Estrogen)'?'selected':''}>Estradiol (Estrogen)</option>
          <option value="__Progesterone" ${o._structured==='Progesterone'?'selected':''}>Progesterone</option>
          <option value="__Oxandrolone (Anavar)" ${o._structured==='Oxandrolone (Anavar)'?'selected':''}>Oxandrolone (Anavar)</option>
          <option value="__Sermorelin" ${o._structured==='Sermorelin'?'selected':''}>Sermorelin</option>
        </optgroup>
        <optgroup label="All other medications (A–Z)">
          ${FORMULARY.filter(f=>!/^Test /.test(f.name)&&!/^Testosterone /.test(f.name)&&!/^Progesterone/.test(f.name)&&!/^Estradiol/.test(f.name)&&!/^Oxandrolone/.test(f.name)&&!/^Sermorelin/.test(f.name)).sort((a,b)=>a.name.localeCompare(b.name)).map(f=>`<option value="${f.name}" ${o.medication===f.name&&!o._structured?'selected':''}>${f.name}</option>`).join('')}
        </optgroup>
      </select>
    </div>
    ${o._structured?rMedPicker(o):''}
    <div id="mpd" style="margin-bottom:6px">${mp?`<div class="al sc" style="margin-bottom:6px"><strong>Patient price: $${mp}</strong></div>`:o.medication?`<div class="al wn" style="margin-bottom:6px">Price not found — contact admin.</div>`:''}</div>
    ${rDoseCalc(o)}
    <div class="fr"><label>Sig * <span style="font-weight:400;text-transform:none;color:var(--m);letter-spacing:0">— how patient uses it</span></label><input value="${o.sig||''}" placeholder="e.g. Inject 0.50mL twice weekly IM" oninput="ST.newOrder.sig=this.value" style="font-family:'DM Mono',monospace;font-size:13px"></div>
    ${rDoseFields(o)}
    <div class="fr"><label>Notes for coordinator</label><textarea placeholder="MCT oil only, new address, allergies..." oninput="ST.newOrder.notes=this.value" style="min-height:48px">${o.notes||''}</textarea></div>
    <div style="border-top:.5px solid var(--b);margin:14px 0"></div>
    <div style="font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:.5px;color:var(--m);margin-bottom:8px">Billing & flags</div>
    <div class="cr" onclick="ST.newOrder.billingConfirmed=!ST.newOrder.billingConfirmed;render()" style="margin-bottom:6px"><input type="checkbox" ${o.billingConfirmed?'checked':''} readonly><label><strong>I have billed the patient${mp?' $'+mp:''}</strong> in Optimantra</label></div>
    <div class="cr" onclick="ST.newOrder.onSubscription=!ST.newOrder.onSubscription;render()" style="margin-bottom:6px;${o.onSubscription?'background:#ede9fe;border-color:#c4b5fd':''}"><input type="checkbox" ${o.onSubscription?'checked':''} readonly style="accent-color:#7c3aed"><label style="${o.onSubscription?'color:#6d28d9;font-weight:600':''}">📋 Patient is on subscription — do not bill for this fill</label></div>
    <div class="cr" onclick="ST.newOrder.controlled=!ST.newOrder.controlled;render()" style="margin-bottom:6px"><input type="checkbox" ${o.controlled?'checked':''} readonly><label>Controlled substance — wet signature + fax required</label></div>
    <div class="cr" onclick="ST.newOrder.researchConsent=!ST.newOrder.researchConsent;render()" style="margin-bottom:6px"><input type="checkbox" ${o.researchConsent?'checked':''} readonly><label>Research use (Alpha Bio/SOMA) — consent on file</label></div>
    <div class="cr" onclick="ST.newOrder.bacWater=!ST.newOrder.bacWater;render()" style="margin-bottom:0;background:var(--inb);border-color:#c5d8f5"><input type="checkbox" ${o.bacWater?'checked':''} readonly><label style="color:var(--in);font-weight:600">💧 Add BAC Water & Syringes</label></div>
    <div style="border-top:.5px solid var(--b);margin:14px 0"></div>
    <div style="font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:.5px;color:var(--m);margin-bottom:8px">Did you place this in LifeFile?</div>
    <div style="display:flex;gap:8px;margin-bottom:10px"><button class="btn${ps===true?' p':''}" style="flex:1;padding:10px;font-size:13px;justify-content:center" onclick="ST.newOrder._providerPlaced=true;render()">✓ Yes — I placed it</button><button class="btn${ps===false?' p':''}" style="flex:1;padding:10px;font-size:13px;justify-content:center" onclick="ST.newOrder._providerPlaced=false;render()">✗ No — coordinator to order</button></div>
    ${ps===true?`<div class="fr" style="margin-bottom:10px"><label style="color:var(--sc)">LifeFile order # *</label><input value="${o.orderNumber||''}" placeholder="Paste order number..." oninput="ST.newOrder.orderNumber=this.value" style="font-family:'DM Mono',monospace;font-size:14px;border-color:var(--sc);background:var(--scb)"></div>`:ps===false?`<div style="padding:9px 12px;background:var(--inb);border:.5px solid #c5d8f5;border-radius:8px;font-size:12px;color:var(--in);margin-bottom:10px">ℹ️ Flagged for coordinator.</div>`:`<div style="padding:8px 12px;background:var(--bg);border:.5px solid var(--b);border-radius:8px;font-size:11px;color:var(--m);margin-bottom:10px">Select Yes or No above.</div>`}
    <button class="btn p" style="width:100%;padding:12px;font-size:14px" onclick="subO()">Submit order →</button>
  </div></div>`;
}

function rDoseFields(o){
  // Auto-calculating day supply from structured dose + frequency. Free-text sig stays separate for the label.
  // Determine med type + available total (vial mL or tablet/troche count) from the structured picker when present.
  let conc=null,totalVol=null,pickOral=false,pickCount=null;
  if(o._structured&&o._pickType!=null&&o._pickOpt!=null){
    const spec=MEDPICK[o._structured];const op=spec&&spec.types[o._pickType]&&spec.types[o._pickType].options[o._pickOpt];
    if(op){conc=op.conc||null;totalVol=op.vol||null;
      // detect oral qty embedded in medName like "#30 / #60 / #90"
      const mm=(op.medName||'').match(/#(\d+)/);if(mm)pickCount=parseInt(mm[1]);
      if(/troche|cap|tablet|tab|sublingual/i.test(op.medName||''))pickOral=true;
    }
  }
  const med=o.medication||'';
  const isInjMed=(conc&&totalVol)||/mg\/mL|injectable|vial/i.test(med);
  const isOralMed=pickOral||/troche|capsule|\bcap\b|tablet|\btab\b|sublingual|RDT/i.test(med);
  const mode=o._doseMode||(isOralMed&&!isInjMed?'oral':isInjMed?'inj':'oral');
  let calc='',qtyOut='',daysOut='';
  if(mode==='inj'){
    const amt=parseFloat(o.doseAmt)||0,every=parseFloat(o.doseEvery)||0,vv=parseFloat(o.doseTotalVol)||totalVol||0;
    if(amt>0&&every>0&&vv>0){const doses=vv/amt;const days=Math.floor(doses*every);daysOut=days;qtyOut=1;
      calc=`<div class="al sc" style="margin:6px 0 0;font-size:12px"><div><strong>${days}-day supply</strong> · ${doses.toFixed(1)} doses per ${vv}mL vial (${amt}mL every ${every}d)${vv>totalVol&&totalVol?` · needs ${Math.ceil(vv/totalVol)} vials`:''}</div></div>`;}
    return`<div style="background:var(--bg);border:.5px solid var(--b);border-radius:10px;padding:11px;margin:0 0 11px">
      <div style="font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.4px;color:var(--in);margin-bottom:8px">💉 Dose → auto day-supply ${doseModeToggle(mode)}</div>
      <div class="f2" style="margin-bottom:8px"><div class="fr" style="margin-bottom:0"><label>Amount per dose (mL)</label><input type="number" step="0.05" value="${o.doseAmt||''}" placeholder="e.g. 0.5" oninput="ST.newOrder.doseAmt=this.value;recalcDS()" onblur="render()" style="font-family:'DM Mono',monospace"></div><div class="fr" style="margin-bottom:0"><label>Every __ days</label><input type="number" step="0.5" value="${o.doseEvery||''}" placeholder="7 = weekly" oninput="ST.newOrder.doseEvery=this.value;recalcDS()" onblur="render()" style="font-family:'DM Mono',monospace"></div></div>
      <div class="fr" style="margin-bottom:0"><label>Total mL in vial ${totalVol?'(auto from selection)':''}</label><input type="number" value="${o.doseTotalVol||totalVol||''}" placeholder="e.g. 5" oninput="ST.newOrder.doseTotalVol=this.value;recalcDS()" onblur="render()" style="font-family:'DM Mono',monospace"></div>
      ${calc}</div>`;
  } else {
    const perDay=parseFloat(o.doseAmt)||0,days=parseFloat(o.doseDays)||0;
    if(perDay>0&&days>0){const qty=Math.ceil(perDay*days);daysOut=days;qtyOut=qty;
      calc=`<div class="al sc" style="margin:6px 0 0;font-size:12px"><div><strong>Order ${qty}</strong> · ${perDay}/day × ${days} days = ${qty}${(perDay*days)%1!==0?` (rounded up from ${perDay*days})`:''}</div></div>`;}
    return`<div style="background:var(--bg);border:.5px solid var(--b);border-radius:10px;padding:11px;margin:0 0 11px">
      <div style="font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.4px;color:var(--in);margin-bottom:8px">💊 Dose → auto quantity ${doseModeToggle(mode)}</div>
      <div class="f2" style="margin-bottom:8px"><div class="fr" style="margin-bottom:0"><label>How many per day</label><input type="number" step="0.25" value="${o.doseAmt||''}" placeholder="e.g. 1" oninput="ST.newOrder.doseAmt=this.value;recalcDS()" onblur="render()" style="font-family:'DM Mono',monospace"></div><div class="fr" style="margin-bottom:0"><label>Day supply</label><input type="number" value="${o.doseDays||''}" placeholder="e.g. 90" oninput="ST.newOrder.doseDays=this.value;recalcDS()" onblur="render()" style="font-family:'DM Mono',monospace"></div></div>
      ${calc}</div>`;
  }
}
function doseModeToggle(mode){return `<span style="float:right;font-weight:400;text-transform:none"><button type="button" class="btn sm ${mode==='inj'?'p':''}" style="font-size:9px;padding:2px 6px" onclick="ST.newOrder._doseMode='inj';render()">Injectable</button> <button type="button" class="btn sm ${mode==='oral'?'p':''}" style="font-size:9px;padding:2px 6px" onclick="ST.newOrder._doseMode='oral';render()">Oral</button></span>`;}
function recalcDS(){
  const o=ST.newOrder;const mode=o._doseMode||'oral';
  // recompute quantity + daySupply onto the order silently (no full re-render, keeps cursor)
  if(mode==='inj'){
    const amt=parseFloat(o.doseAmt)||0,every=parseFloat(o.doseEvery)||0,vv=parseFloat(o.doseTotalVol)||0;
    if(amt>0&&every>0&&vv>0){const doses=vv/amt;o.daySupply=String(Math.floor(doses*every));o.quantity=String(Math.max(1,Math.ceil(vv/vv)));}
  }else{
    const perDay=parseFloat(o.doseAmt)||0,days=parseFloat(o.doseDays)||0;
    if(perDay>0&&days>0){o.quantity=String(Math.ceil(perDay*days));o.daySupply=String(days);}
  }
  // update just the calc line without disturbing inputs
  const host=document.querySelector('.al.sc');
}
function rDoseCalc(o){
  if(!window._dc)window._dc={open:false};
  const dc=window._dc,open=dc.open;
  // determine concentration: from structured picker, or try to infer from medication name
  let conc=o._pickConc||null,totalVol=null,totalMg=null;
  const med=o.medication||'';
  // pull vial volume from structured pick
  if(o._structured&&o._pickType!=null&&o._pickOpt!=null){
    const spec=MEDPICK[o._structured];const op=spec&&spec.types[o._pickType]&&spec.types[o._pickType].options[o._pickOpt];
    if(op){conc=op.conc;totalVol=op.vol;}
  }
  const isGLP=/semaglutide|tirzepatide|retatrutide|liraglutide/i.test(med);
  const isOral=/troche|capsule|\bcap\b|tablet|\btab\b|sublingual|RDT/i.test(med);
  const isInj=conc&&totalVol;
  if(!open){
    return`<div style="margin:0 0 11px"><button type="button" class="btn sm" style="font-size:11px" onclick="window._dc.open=true;render()">🧮 Open dosing / day-supply calculator</button></div>`;
  }
  let result='';
  const d=dc.data||{};
  if(dc.mode==='inj'||(!dc.mode&&isInj&&!isGLP)){
    dc.mode='inj';
    const units=parseFloat(d.units)||0,freq=parseFloat(d.freq)||0,vialVol=parseFloat(d.vialVol)||totalVol||0,cc=parseFloat(d.conc)||conc||0;
    const mlPerDose=units/100; // U-100 syringe: 100 units = 1mL
    const mgPerDose=mlPerDose*cc;
    let out='';
    if(units&&freq&&vialVol){
      const dosesPerVial=vialVol/mlPerDose;
      const daysBetween=parseFloat(d.freq)||0;
      const totalDays=daysBetween>0?Math.floor(dosesPerVial*daysBetween):0;
      out=`<div class="al sc" style="margin:8px 0 0"><div><strong>${mlPerDose.toFixed(2)} mL per dose</strong> (${units} units on a U-100 syringe = ${mgPerDose.toFixed(1)}mg)<br><strong>${Math.floor(dosesPerVial)} doses per ${vialVol}mL vial</strong>${daysBetween>0?`<br><strong style="font-size:14px">≈ ${totalDays} day supply</strong> (dosing every ${daysBetween} day${daysBetween!=1?'s':''})`:''}</div></div>`;
    }
    result=`<div class="f2" style="margin-bottom:8px"><div class="fr" style="margin-bottom:0"><label>Concentration (mg/mL)</label><input type="number" value="${d.conc||conc||''}" placeholder="${conc||'e.g. 200'}" oninput="window._dc.data={...(window._dc.data||{}),conc:this.value};render()" style="font-family:'DM Mono',monospace"></div><div class="fr" style="margin-bottom:0"><label>Vial size (mL)</label><input type="number" value="${d.vialVol||totalVol||''}" placeholder="${totalVol||'e.g. 5'}" oninput="window._dc.data={...(window._dc.data||{}),vialVol:this.value};render()" style="font-family:'DM Mono',monospace"></div></div>
    <div class="f2" style="margin-bottom:0"><div class="fr" style="margin-bottom:0"><label>Units per injection (U-100)</label><input type="number" value="${d.units||''}" placeholder="e.g. 20" oninput="window._dc.data={...(window._dc.data||{}),units:this.value};render()" style="font-family:'DM Mono',monospace"></div><div class="fr" style="margin-bottom:0"><label>Inject every __ days</label><input type="number" value="${d.freq||''}" placeholder="7 = weekly, 3.5 = 2x/wk" oninput="window._dc.data={...(window._dc.data||{}),freq:this.value};render()" style="font-family:'DM Mono',monospace"></div></div>${out}`;
  } else if(dc.mode==='glp'||(!dc.mode&&isGLP)){
    dc.mode='glp';
    const mgDose=parseFloat(d.mgDose)||0,daysBetween=parseFloat(d.freq)||7,totalMgV=parseFloat(d.totalMg)||0;
    let out='';
    if(mgDose&&totalMgV){
      const doses=totalMgV/mgDose;
      const totalDays=Math.floor(doses*daysBetween);
      out=`<div class="al sc" style="margin:8px 0 0"><div><strong>${doses.toFixed(1)} doses per vial</strong> (${totalMgV}mg ÷ ${mgDose}mg)<br><strong style="font-size:14px">≈ ${totalDays} day supply</strong> (every ${daysBetween} day${daysBetween!=1?'s':''})</div></div>`;
    }
    result=`<div class="f2" style="margin-bottom:8px"><div class="fr" style="margin-bottom:0"><label>Total mg in vial</label><input type="number" value="${d.totalMg||''}" placeholder="e.g. 30" oninput="window._dc.data={...(window._dc.data||{}),totalMg:this.value};render()" style="font-family:'DM Mono',monospace"></div><div class="fr" style="margin-bottom:0"><label>mg per dose</label><input type="number" step="0.25" value="${d.mgDose||''}" placeholder="e.g. 2.5" oninput="window._dc.data={...(window._dc.data||{}),mgDose:this.value};render()" style="font-family:'DM Mono',monospace"></div></div>
    <div class="fr" style="margin-bottom:0"><label>Dose every __ days</label><input type="number" value="${d.freq||'7'}" placeholder="7 = weekly" oninput="window._dc.data={...(window._dc.data||{}),freq:this.value};render()" style="font-family:'DM Mono',monospace"></div>${out}`;
  } else if(dc.mode==='tab'){
    dc.mode='tab';
    const frac=parseFloat(d.tabFrac)||0,days=parseFloat(d.tabDays)||90;
    let out='';
    if(frac>0&&days>0){
      const exact=days*frac;
      const order=Math.ceil(exact);
      const doseMg=frac*50; // 50mg flex tablet base
      out=`<div class="al sc" style="margin:8px 0 0"><div><strong>${exact} tablets needed</strong> (${days} days × ${frac} tablet/day = ${doseMg}mg dose)<br><strong style="font-size:15px">→ Order ${order} whole tablets</strong> (rounded up from ${exact})<br><span style="font-size:11px">Strive won't accept fractional quantities — order the whole-tablet number above.</span></div></div>`;
    }
    result=`<div style="font-size:11px;color:var(--m);margin-bottom:8px">For flex-dose tablets split by the patient (e.g. enclomiphene 50mg tab taken as ¾ = 37.5mg). Calculates whole tablets to order.</div>
    <div class="f2" style="margin-bottom:8px"><div class="fr" style="margin-bottom:0"><label>Tablet fraction/day</label><select onchange="window._dc.data={...(window._dc.data||{}),tabFrac:this.value};render()" style="width:100%;padding:8px 10px;border:.5px solid var(--b);border-radius:8px;background:var(--s);color:var(--t);font-size:13px"><option value="">Select...</option><option value="0.25" ${d.tabFrac=='0.25'?'selected':''}>¼ tablet (12.5mg)</option><option value="0.5" ${d.tabFrac=='0.5'?'selected':''}>½ tablet (25mg)</option><option value="0.75" ${d.tabFrac=='0.75'?'selected':''}>¾ tablet (37.5mg)</option><option value="1" ${d.tabFrac=='1'?'selected':''}>full tablet (50mg)</option></select></div><div class="fr" style="margin-bottom:0"><label>Day supply</label><input type="number" value="${d.tabDays||'90'}" placeholder="90" oninput="window._dc.data={...(window._dc.data||{}),tabDays:this.value};render()" style="font-family:'DM Mono',monospace"></div></div>${out}`;
  } else {
    dc.mode='oral';
    const perDay=parseFloat(d.oralPerDay)||0,days=parseFloat(d.oralDays)||90;
    let out='';
    if(perDay>0&&days>0){
      const qty=Math.ceil(perDay*days);
      const unitWord=(d.oralUnit||'troche');
      out=`<div class="al sc" style="margin:8px 0 0"><div><strong style="font-size:15px">→ Order ${qty} ${unitWord}${qty!=1?'s':''}</strong><br><span style="font-size:12px">${perDay} ${unitWord}${perDay!=1?'s':''}/day × ${days} days = ${qty}</span><br><span style="font-size:11px;color:var(--m)">Quantity to enter on the order = ${qty}. Day supply = ${days}.</span></div></div>`;
    }
    result=`<div style="font-size:11px;color:var(--m);margin-bottom:8px">For troches, capsules, tablets & other oral meds taken a set number per day (e.g. progesterone 100mg troche, 1 under tongue at bedtime = 1/day). Tells you the quantity to order.</div>
    <div class="f2" style="margin-bottom:8px"><div class="fr" style="margin-bottom:0"><label>Form</label><select onchange="window._dc.data={...(window._dc.data||{}),oralUnit:this.value};render()" style="width:100%;padding:8px 10px;border:.5px solid var(--b);border-radius:8px;background:var(--s);color:var(--t);font-size:13px"><option value="troche" ${(d.oralUnit||'troche')=='troche'?'selected':''}>Troche</option><option value="capsule" ${d.oralUnit=='capsule'?'selected':''}>Capsule</option><option value="tablet" ${d.oralUnit=='tablet'?'selected':''}>Tablet</option></select></div><div class="fr" style="margin-bottom:0"><label>How many per day</label><input type="number" step="0.5" value="${d.oralPerDay||''}" placeholder="e.g. 1" oninput="window._dc.data={...(window._dc.data||{}),oralPerDay:this.value};render()" style="font-family:'DM Mono',monospace"></div></div>
    <div class="fr" style="margin-bottom:0"><label>Day supply</label><input type="number" value="${d.oralDays||'90'}" placeholder="90" oninput="window._dc.data={...(window._dc.data||{}),oralDays:this.value};render()" style="font-family:'DM Mono',monospace"></div>${out}`;
  }
  return`<div style="background:var(--inb);border:.5px solid #c5d8f5;border-radius:10px;padding:12px;margin:0 0 11px">
    <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:10px"><div style="font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.4px;color:var(--in)">🧮 Dosing / Day-Supply Calculator</div><div style="display:flex;gap:6px;flex-wrap:wrap"><button type="button" class="btn sm ${dc.mode==='inj'?'p':''}" style="font-size:10px;padding:3px 8px" onclick="window._dc.mode='inj';render()">Injectable</button><button type="button" class="btn sm ${dc.mode==='glp'?'p':''}" style="font-size:10px;padding:3px 8px" onclick="window._dc.mode='glp';render()">GLP-1 (mg)</button><button type="button" class="btn sm ${dc.mode==='oral'?'p':''}" style="font-size:10px;padding:3px 8px" onclick="window._dc.mode='oral';render()">Oral/Troche</button><button type="button" class="btn sm ${dc.mode==='tab'?'p':''}" style="font-size:10px;padding:3px 8px" onclick="window._dc.mode='tab';render()">Flex tablet</button><button type="button" class="btn sm" style="font-size:10px;padding:3px 8px" onclick="window._dc.open=false;render()">✕</button></div></div>
    ${result}
    <div style="font-size:10px;color:var(--m);margin-top:8px;line-height:1.5">Estimate only — actual day supply may be capped by pharmacy BUD (some meds discarded before full use). Coordinator confirms final limits.</div>
  </div>`;
}
function pickMed(val){
  ST.newOrder.budCounseled=false;
  if(val.startsWith('__')){
    ST.newOrder._structured=val.slice(2);
    ST.newOrder._pickType=null;ST.newOrder._pickOpt=null;
    ST.newOrder.medication='';ST.newOrder.pharmacy='';ST.newOrder.controlled=(MEDPICK[val.slice(2)]||{}).controlled||false;
  }else{
    ST.newOrder._structured=null;ST.newOrder._pickType=null;ST.newOrder._pickOpt=null;
    ST.newOrder.medication=val;
  }
  render();
}
function rMedPicker(o){
  const spec=MEDPICK[o._structured];if(!spec)return'';
  const typeOpts=spec.types.map((t,i)=>`<option value="${i}" ${o._pickType==i?'selected':''}>${t.type}</option>`).join('');
  let doseBlock='';
  if(o._pickType!=null&&o._pickType!==''){
    const t=spec.types[o._pickType];
    if(t){
      const dOpts=t.options.map((op,j)=>`<option value="${j}" ${o._pickOpt==j?'selected':''}>${op.label}</option>`).join('');
      doseBlock=`<div class="fr" style="margin-bottom:0"><label>Dose / vial size *</label><select onchange="pickDose(${o._pickType},this.value)" style="width:100%;padding:8px 10px;border:.5px solid var(--b);border-radius:8px;background:var(--s);color:var(--t);font-size:13px;font-family:'DM Sans',sans-serif"><option value="">Select dose...</option>${dOpts}</select></div>`;
    }
  }
  let confirm2='',customBlock='',budBlock='';
  if(o._pickType!=null&&o._pickOpt!=null&&o._pickOpt!==''){
    const t=spec.types[o._pickType];
    const op=t.options[o._pickOpt];
    if(op){
      if(op.custom){
        const mg=o._customMg||'';
        const valid=mg&&parseFloat(mg)>=50&&parseFloat(mg)<=400;
        customBlock=`<div class="fr" style="margin:11px 0 0"><label>Strength in mg (${op.customRange||'custom'}) *</label><input type="number" min="50" max="400" value="${mg}" placeholder="e.g. 150" oninput="setCustomMgLive(this.value)" onblur="render()" style="font-family:'DM Mono',monospace"/>${mg&&!valid?'<div style="font-size:11px;color:var(--dn);margin-top:3px">⚠ Enter a value between 50 and 400mg</div>':''}</div>`;
        if(valid){const phTxt=op.pharmacy?`Auto-routes to <strong>${op.pharmacy}</strong>`:'<strong>Pharmacy TBD</strong>';confirm2=`<div class="al sc" style="margin:8px 0 0"><div>✓ <strong>${op.medName.replace('{MG}',mg)}</strong><br><span style="font-size:11px">${aR()==='provider'?'Selection confirmed — coordinator handles pharmacy':phTxt}</span></div></div>`;}
      }else{
        const phTxt=op.pharmacy?`Auto-routes to <strong>${op.pharmacy}</strong>`:'<strong>Pharmacy TBD</strong> — coordinator will assign';
        confirm2=`<div class="al sc" style="margin:8px 0 0"><div>✓ <strong>${op.medName}</strong><br><span style="font-size:11px">${aR()==='provider'?'Selection confirmed — coordinator handles pharmacy':phTxt}</span></div></div>`;
      }
      // Grapeseed BUD reminder — only on 2-bottle (10mL) grapeseed selections
      if(t.budFlag&&op.vol===10){
        budBlock=`<div class="al wn" style="margin:8px 0 0;flex-direction:column;align-items:stretch">
          <div style="display:flex;gap:8px;align-items:flex-start"><span>⚠</span><div><strong>Grapeseed BUD note.</strong> Grapeseed has a shorter beyond-use date, so Hallandale may not release 2 vials unless the sig quantity supports it within dating. If you adjust the pharmacy sig to release both vials, the <strong>label dose will differ from the patient's actual intended dose</strong> — you must counsel the patient directly on what to really take.</div></div>
          <div class="cr" onclick="ST.newOrder.budCounseled=!ST.newOrder.budCounseled;render()" style="margin:8px 0 0;background:var(--s)"><input type="checkbox" ${o.budCounseled?'checked':''} readonly><label>I have counseled (or will counsel) the patient that the pharmacy label dose differs from their actual directions</label></div>
        </div>`;
      }
    }
  }
  return`<div style="background:var(--bg);border:.5px solid var(--b);border-radius:10px;padding:12px;margin:8px 0">
    <div class="fr" style="margin-bottom:${doseBlock?'11px':'0'}"><label>${o._structured} — type *</label><select onchange="pickType(this.value)" style="width:100%;padding:8px 10px;border:.5px solid var(--b);border-radius:8px;background:var(--s);color:var(--t);font-size:13px;font-family:'DM Sans',sans-serif"><option value="">Select type...</option>${typeOpts}</select></div>
    ${doseBlock}${customBlock}${confirm2}${budBlock}</div>`;
}
function pickType(i){ST.newOrder._pickType=i===''?null:parseInt(i);ST.newOrder._pickOpt=null;ST.newOrder.medication='';ST.newOrder.pharmacy='';ST.newOrder.budCounseled=false;render();}
function pickDose(ti,j){
  if(j===''){ST.newOrder._pickOpt=null;ST.newOrder.medication='';ST.newOrder.pharmacy='';ST.newOrder._customMg='';render();return;}
  const op=MEDPICK[ST.newOrder._structured].types[ti].options[parseInt(j)];
  ST.newOrder._pickOpt=parseInt(j);
  ST.newOrder.pharmacy=op.pharmacy||'';
  ST.newOrder._pickConc=op.conc;
  if(op.custom){
    ST.newOrder._customMg='';
    ST.newOrder.medication='';// wait for mg entry
  }else{
    ST.newOrder.medication=op.medName;
  }
  render();
}
function setCustomMgLive(v){
  // Update state + medication WITHOUT re-rendering, so the input keeps focus while typing.
  const o=ST.newOrder,spec=MEDPICK[o._structured];
  const op=spec&&spec.types[o._pickType]&&spec.types[o._pickType].options[o._pickOpt];
  o._customMg=v;
  if(op&&op.custom&&v){o.medication=op.medName.replace('{MG}',v);}else{o.medication='';}
}
function setCustomMg(v){
  const o=ST.newOrder,spec=MEDPICK[o._structured];
  const op=spec&&spec.types[o._pickType]&&spec.types[o._pickType].options[o._pickOpt];
  o._customMg=v;
  if(op&&op.custom&&v){o.medication=op.medName.replace('{MG}',v);}else{o.medication='';}
  render();
}
function uMP(){const el=document.getElementById('mpd');if(!el)return;const med=ST.newOrder.medication||'',price=PP[med];if(price){el.innerHTML=`<div class="al sc" style="margin-bottom:10px"><strong>Patient price: $${price}</strong></div>`;}else if(med.length>2){const p=Object.keys(PP).find(k=>k.toLowerCase().includes(med.toLowerCase()));if(p)el.innerHTML=`<div class="al in" style="margin-bottom:10px">Did you mean <strong>${p}</strong>? ($${PP[p]})</div>`;else el.innerHTML='';}else el.innerHTML='';}

function subO(){
  const o=ST.newOrder;
  if(!o.patientName){alert('Please enter the patient name.');return;}
  if(!o.patientDOB){alert('Please enter the date of birth.');return;}
  if(!o.medication){alert('Please enter the medication.');return;}
  if(!o.sig){alert('Please enter the sig.');return;}
  if(!o.orderedBy){alert('Please select who is ordering.');return;}
  if(!o.billingConfirmed&&!o.onSubscription){alert('Please confirm billing or mark as subscription.');return;}
  if(o._providerPlaced===undefined){alert('Please answer the LifeFile question.');return;}
  if(o._providerPlaced===true&&!o.orderNumber){alert('Please enter the LifeFile order number.');return;}
  const dup=ST.orders.some(ex=>ex.patientName.toLowerCase()===o.patientName.trim().toLowerCase()&&ex.medication.toLowerCase()===o.medication.trim().toLowerCase());
  if(dup&&!confirm(`⚠️ DUPLICATE: ${o.patientName} already has an order for ${o.medication}.\n\nCreate anyway?`))return;
  const order={...o,id:'ord_'+Date.now(),placedBy:CU?CU.name:'',placedByRole:aR(),status:o._providerPlaced===true?'Ordered':'Awaiting Payment Verification',dateOrdered:o.dateOrdered||new Date().toISOString().split('T')[0],paymentConfirmed:false,returnedReason:'',_needsCoordinatorOrder:o._providerPlaced!==true,_providerPlaced:undefined,_structured:undefined,_pickType:undefined,_pickOpt:undefined,_pickConc:undefined,_customMg:undefined,_doseMode:undefined,doseAmt:undefined,doseEvery:undefined,doseTotalVol:undefined,doseDays:undefined};
  ST.orders.unshift(order);ST.newOrder={};sO();ST.tab='orders';alert('Order submitted.');renderApp();
}

function rPt(){
  const role=aR(),hP=role==='provider'||role==='staff',srch=(ST.filterSearch||'').toLowerCase(),pts={};
  ST.orders.forEach(o=>{const k=o.patientName.toLowerCase().trim();if(!pts[k])pts[k]={name:o.patientName,dob:o.patientDOB,orders:[]};pts[k].orders.push(o);});
  const list=Object.values(pts).filter(p=>!srch||p.name.toLowerCase().includes(srch));
  return`<div class="sh"><h2>Patient order history</h2><input style="padding:7px 10px;border:.5px solid var(--b);border-radius:8px;font-size:12px;font-family:'DM Sans',sans-serif;width:240px" placeholder="Search patients..." oninput="ST.filterSearch=this.value;dR()" value="${ST.filterSearch||''}"></div>
  ${list.length===0?`<div class="emp">${ST.orders.length===0?'No orders yet.':'No patients match.'}</div>`:''}
  ${list.map(p=>`<div class="phc"><div style="display:flex;align-items:baseline;justify-content:space-between;margin-bottom:8px"><div><div class="phn">${p.name}</div><div class="phm">DOB: ${p.dob||'—'} · ${p.orders.length} order${p.orders.length!==1?'s':''}</div></div><button class="btn sm p" onclick="ST.newOrder={patientName:'${p.name}',patientDOB:'${p.dob||''}'};go('new')">+ New order</button></div>
  <table style="font-size:11px"><thead><tr><th>Medication</th><th>Pharmacy</th><th>Payment</th><th>Status</th><th>Tracking</th><th>Date</th><th></th></tr></thead>
  <tbody>${p.orders.map(o=>`<tr><td>${o.medication}${o.onSubscription?' <span class="bdg on-subscription" style="min-width:auto;font-size:9px">📋</span>':''}</td><td>${hP?'—':(o.pharmacy||'—')}</td><td>${rPB(o.id,true)}</td><td><span class="bdg ${sCls(o.status)}">${o.status}</span></td><td>${o.trackingNumber||'—'}</td><td style="color:var(--m)">${o.dateOrdered||'—'}</td><td style="display:flex;gap:6px;align-items:center"><button class="rb2" onclick="oCR('${o.id}')">↻ Reorder</button><button class="btn sm dn" style="padding:4px 8px" onclick="dOrd('${o.id}')">🗑️</button></td></tr>`).join('')}</tbody></table></div>`).join('')}`;
}

function rPh(){
  const types=[{id:'all',l:'All'},{id:'Compound',l:'Compound'},{id:'503a',l:'503a'},{id:'503a/503b',l:'Olympia'},{id:'In-Office',l:'In-Office'},{id:'Research',l:'Research'}];
  const vis=PHARMACIES.filter(p=>ST.pharmFilter==='all'||p.type.includes(ST.pharmFilter));
  return`<div class="cts" style="margin-bottom:14px">${types.map(t=>`<button class="ct2 ${ST.pharmFilter===t.id?'active':''}" onclick="ST.pharmFilter='${t.id}';render()">${t.l}</button>`).join('')}</div>
  ${vis.map(p=>`<div class="phc"><div class="phn">${p.name} <span style="font-size:10px;font-weight:400;color:var(--m);margin-left:6px">${p.type}</span></div>
  <div class="phm"><strong>Turnaround:</strong> ${p.ta} · <strong>Method:</strong> ${p.method} · <strong>Login:</strong> ${p.login}${(p.contact.rep||p.contact.phone||p.contact.email)?`<br><strong>Contact:</strong> ${p.contact.rep?`<strong style="color:var(--t)">${p.contact.rep}</strong> · `:''}${p.contact.phone?`📞 <a href="tel:${p.contact.phone}" style="color:var(--in);text-decoration:none">${p.contact.phone}</a>`:''}${p.contact.cell?` · 📱 <a href="tel:${p.contact.cell}" style="color:var(--in);text-decoration:none">${p.contact.cell}</a>`:''}${p.contact.email?` · ✉️ <a href="mailto:${p.contact.email}" style="color:var(--in);text-decoration:none">${p.contact.email}</a>`:''}`:''}
  </div><div style="font-size:11px;color:var(--m);margin-top:6px;line-height:1.6">${p.notes}</div>
  <div class="phmd">${p.meds.map(m=>`<span class="phmdt">${m}</span>`).join('')}</div></div>`).join('')}`;
}

function bP(rows){const v=rows.filter(r=>r.p!=null);return v.length?Math.min(...v.map(r=>r.p)):null;}
function fmt(p){return p==null?'—':'$'+(p%1===0?p:p.toFixed(2));}
function fE(f){const m={ctrl:'CTRL',research:'CONSENT',watch:'WATCH',inoffice:'IN-OFFICE',goodrx:'GOODRX',noorder:'REF ONLY'};return`<span class="fl ${f}">${m[f]||f}</span>`;}

function rF(){
  const cats=['All',...[...new Set(FORMULARY.map(x=>x.cat))]];
  return`<div style="display:flex;gap:8px;margin-bottom:10px"><input id="afs" style="flex:1;min-width:200px;padding:7px 10px;border:.5px solid var(--b);border-radius:8px;font-size:12px;font-family:'DM Sans',sans-serif" placeholder="Search medications..." oninput="ST.formSearch=this.value;rAFR()" value="${ST.formSearch}"></div>
  <div class="lg2"><span class="ph brooksville">Brooksville</span><span class="ph hallandale">Hallandale</span><span class="ph centercity">Center City</span><span class="ph strive">Strive</span><span class="ph olympia">Olympia</span><span class="ph pdrx">PDRX</span><span class="ph alphabio">Alpha Bio</span> · <strong style="color:var(--bk)">Green = best price</strong></div>
  <div class="cts">${cats.map(c=>`<button class="ct2 ${ST.catFilter===c?'active':''}" onclick="ST.catFilter='${c}';render()">${c}</button>`).join('')}</div>
  <div id="afr">${bAFR()}</div>`;
}
function bAFR(){const srch=ST.formSearch.toLowerCase();let items=FORMULARY;if(ST.catFilter!=='All')items=items.filter(d=>d.cat===ST.catFilter);if(srch)items=items.filter(d=>d.name.toLowerCase().includes(srch)||d.rows.some(r=>r.l.toLowerCase().includes(srch)));return bFT(items,ST.catFilter==='All'&&!srch);}
function rAFR(){const el=document.getElementById('afr');if(el)el.innerHTML=bAFR();}
function bFT(items,grouped){if(!items.length)return`<div class="emp">No results.</div>`;if(grouped){const g={};items.forEach(i=>{(g[i.cat]=g[i.cat]||[]).push(i);});return Object.entries(g).map(([cat,rows])=>`<div class="cd" style="margin-bottom:10px"><div class="ch">${cat}</div>${fT(rows)}</div>`).join('');}return`<div class="cd">${fT(items)}</div>`;}
function fT(items){return`<table><thead><tr><th style="width:30%">Medication</th><th>Pharmacy & price</th><th style="width:70px">Best</th><th style="width:95px">Flags</th></tr></thead><tbody>${items.map(row=>{const b=bP(row.rows);return`<tr><td><strong style="font-size:12px">${row.name}</strong></td><td>${row.rows.map(r=>`<div style="display:flex;align-items:baseline;gap:6px;margin-bottom:3px"><span class="ph ${r.ph}">${r.l}</span><span class="pv${r.p===b&&b!=null?' best':''}">${fmt(r.p)}</span>${r.n?`<span class="nt">${r.n}</span>`:''}</div>`).join('')}</td><td><span class="bc">${b!=null?fmt(b):''}</span></td><td>${row.flags.map(fE).join('')}</td></tr>`;}).join('')}</tbody></table>`;}

function rInv(){
  const inv=ST.invoices,bP2={};
  inv.forEach(i=>{const ph=i.pharmacy||'Unknown';if(!bP2[ph])bP2[ph]=[];bP2[ph].push(i);});
  return`<div class="sh"><h2>Invoice reconciliation</h2><div style="display:flex;gap:8px"><button class="btn p" onclick="ST.showNewInvoice=!ST.showNewInvoice;ST.showGmailImport=false;render()">+ Log invoice</button><button class="btn" onclick="ST.showGmailImport=!ST.showGmailImport;ST.showNewInvoice=false;render()">📧 Import from Gmail</button></div></div>
  ${ST.showGmailImport?`<div class="iic"><div style="font-size:14px;font-weight:600;margin-bottom:4px">📧 Import pharmacy invoices from Gmail</div><div style="font-size:12px;color:var(--m);margin-bottom:14px">Pharmacy emails go to <strong>admin@primehrt.clinic</strong>.</div>
  <div class="iis"><div class="iin">1</div><div><div style="font-size:12px;font-weight:600;margin-bottom:3px">Copy this prompt and paste into Claude.ai</div><button class="btn sm p" onclick="cGP()">📋 Copy Gmail import prompt</button></div></div>
  <div class="iis"><div class="iin">2</div><div><div style="font-size:12px;font-weight:600;margin-bottom:3px">Use Gmail connector to scan admin@primehrt.clinic</div></div></div>
  <div class="iis"><div class="iin">3</div><div><div style="font-size:12px;font-weight:600;margin-bottom:3px">Paste the JSON here and click Import</div><textarea id="gi_in" rows="4" style="width:100%;padding:8px 10px;border:.5px solid var(--b);border-radius:6px;font-size:11px;font-family:'DM Mono',monospace;background:var(--bg);color:var(--t);resize:vertical;margin-top:8px" placeholder="Paste Claude JSON here..."></textarea><div style="display:flex;gap:8px;margin-top:8px"><button id="do_gi" class="btn p">Import invoices</button><button class="btn" onclick="ST.showGmailImport=false;render()">Cancel</button></div></div></div></div>`:''}
  ${ST.showNewInvoice?`<div class="cd cp" style="max-width:580px;margin-bottom:14px"><h2 style="margin-bottom:12px">Log invoice line item</h2><div class="f2"><div class="fr"><label>Pharmacy *</label><select id="i_ph"><option value="">Select...</option>${PN.map(n=>`<option>${n}</option>`).join('')}</select></div><div class="fr"><label>Order # *</label><input id="i_id" placeholder="e.g. 76309101"></div></div><div class="f2"><div class="fr"><label>Patient *</label><input id="i_pt" placeholder="Last, First"></div><div class="fr"><label>Date *</label><input id="i_date" type="date" value="${new Date().toISOString().split('T')[0]}"></div></div><div class="fr"><label>Medication *</label><input id="i_med" placeholder="e.g. Tirzepatide 6mL"></div><div class="f2"><div class="fr"><label>Med charge ($)</label><input id="i_amt" type="number" step="0.01" placeholder="0.00"></div><div class="fr"><label>Shipping ($)</label><input id="i_ship" type="number" step="0.01" placeholder="0.00"></div></div><div style="display:flex;gap:8px;margin-top:4px"><button class="btn p" onclick="subInv()">Save</button><button class="btn" onclick="ST.showNewInvoice=false;render()">Cancel</button></div></div>`:''}
  ${inv.length===0?`<div class="emp">No invoices logged yet.</div>`:`<div style="margin-bottom:10px;display:flex;gap:8px;align-items:center"><div style="font-size:12px;color:var(--m)">${inv.length} item${inv.length!==1?'s':''}</div><div style="font-size:12px;font-weight:600;color:var(--sc)">Total: $${inv.reduce((s,i)=>(s+parseFloat(i.amount||0)+parseFloat(i.shipping||0)),0).toFixed(2)}</div></div>
  ${Object.entries(bP2).map(([ph,items])=>{const tot=items.reduce((s,i)=>(s+parseFloat(i.amount||0)+parseFloat(i.shipping||0)),0);return`<div style="margin-bottom:14px"><div style="font-size:11px;font-weight:600;text-transform:uppercase;letter-spacing:.5px;padding:6px 12px;background:var(--s);border-radius:6px;margin-bottom:4px;display:flex;justify-content:space-between"><span>${ph} — ${items.length} item${items.length!==1?'s':''}</span><span style="font-family:'DM Mono',monospace;color:var(--sc)">$${tot.toFixed(2)}</span></div>
  <div class="cd"><table><thead><tr><th>Date</th><th>Patient</th><th>Order #</th><th>Medication</th><th style="text-align:right">Med</th><th style="text-align:right">Ship</th><th style="text-align:right">Total</th><th>Status</th><th></th></tr></thead><tbody>${items.map(i=>{const t2=(parseFloat(i.amount||0)+parseFloat(i.shipping||0)).toFixed(2);return`<tr><td style="font-size:11px;color:var(--m)">${i.date||'—'}</td><td style="font-size:12px;font-weight:500">${i.patient||'—'}</td><td style="font-size:11px;font-family:'DM Mono',monospace">${i.invoiceId||'—'}</td><td style="font-size:11px;max-width:200px">${i.medication||'—'}</td><td style="font-family:'DM Mono',monospace;font-size:12px;text-align:right">$${parseFloat(i.amount||0).toFixed(2)}</td><td style="font-family:'DM Mono',monospace;font-size:12px;text-align:right;color:var(--m)">$${parseFloat(i.shipping||0).toFixed(2)}</td><td style="font-family:'DM Mono',monospace;font-size:12px;font-weight:600;text-align:right">$${t2}</td><td><span class="bdg ${i.reconciled?'delivered':'pending'}">${i.reconciled?'✓ Reconciled':'Pending'}</span></td><td style="white-space:nowrap"><button class="btn sm" onclick="mR('${i.id}')">${i.reconciled?'Unmark':'Reconcile'}</button><button class="btn sm dn" style="margin-left:4px" onclick="dInv('${i.id}')">✕</button></td></tr>`;}).join('')}</tbody></table></div></div>`;}).join('')}`}`;
}
function cGP(){const p=`Please scan the Gmail inbox for admin@primehrt.clinic and find all pharmacy invoice emails from the past 30 days. Pharmacies: Hallandale, Center City, Strive, Brooksville, Southlake, Olympia, Alpha Bio, Stryker, NuCare, Wesley Pharmaceuticals.\n\nReturn ONLY a JSON array (no markdown):\n[{"sourceId":"unique ID","pharmacy":"name","patient":"Last, First","invoiceId":"order number","medication":"name and strength","amount":0.00,"shipping":0.00,"date":"YYYY-MM-DD"}]`;navigator.clipboard.writeText(p).then(()=>toast('✓ Prompt copied — paste into Claude.ai')).catch(()=>alert(p));}
function subInv(){const ph=document.getElementById('i_ph').value,pt=document.getElementById('i_pt').value,med=document.getElementById('i_med').value;if(!ph||!pt||!med){alert('Please fill in all required fields.');return;}ST.invoices.unshift({id:'inv_'+Date.now(),pharmacy:ph,patient:pt,invoiceId:document.getElementById('i_id').value||'—',medication:med,amount:parseFloat(document.getElementById('i_amt').value)||0,shipping:parseFloat(document.getElementById('i_ship').value)||0,date:document.getElementById('i_date').value,reconciled:false});ST.showNewInvoice=false;sI();render();}
function mR(id){const i=ST.invoices.find(x=>x.id===id);if(i){i.reconciled=!i.reconciled;sI();render();}}
function dInv(id){if(confirm('Remove this line item?')){ST.invoices=ST.invoices.filter(x=>x.id!==id);sI();render();}}
async function iIG(json){if(!json||!json.trim()){alert('Please paste the JSON first.');return;}try{const items=JSON.parse(json.trim().replace(/^```json\n?/,'').replace(/\n?```$/,''));if(!Array.isArray(items))throw new Error('Expected JSON array');const ex=new Set(ST.invoices.map(i=>i.sourceId).filter(Boolean));let added=0;items.forEach(item=>{if(item.sourceId&&ex.has(item.sourceId))return;ST.invoices.unshift({id:'inv_'+Date.now()+'_'+Math.random().toString(36).slice(2,6),sourceId:item.sourceId||null,pharmacy:item.pharmacy||'Unknown',patient:item.patient||'—',invoiceId:item.invoiceId||'—',medication:item.medication||'—',amount:parseFloat(item.amount)||0,shipping:parseFloat(item.shipping)||0,date:item.date||new Date().toISOString().split('T')[0],reconciled:false});added++;});sI();ST.showGmailImport=false;render();toast(`✅ Imported ${added} item${added!==1?'s':''}`);}catch(err){alert('Could not parse JSON: '+err.message);}}
function toast(msg){const t=document.createElement('div');t.textContent=msg;Object.assign(t.style,{position:'fixed',bottom:'24px',left:'50%',transform:'translateX(-50%)',background:'#1a1916',color:'white',padding:'10px 20px',borderRadius:'8px',fontSize:'13px',fontWeight:'600',zIndex:'9999',pointerEvents:'none',fontFamily:"'DM Sans',sans-serif",opacity:'1',transition:'opacity .3s'});document.body.appendChild(t);setTimeout(()=>{t.style.opacity='0';setTimeout(()=>t.remove(),350);},2200);}

function rMO(){
  const items=ST.mailouts||[],o=ST.newMailout||{};
  const pending=items.filter(m=>!m.trackingNumber&&!m.mailed);
  const mailed=items.filter(m=>m.trackingNumber||m.mailed);
  return`<div style="max-width:1000px">
  <div class="al in" style="margin-bottom:14px;background:#fff7ed;border-color:#fed7aa;color:#9a3412">📦 <div><strong>In-Office Mail-Out — this is NOT the pharmacy order pipeline.</strong> Use this ONLY for items shipped directly from the office (HCG and occasional others). Workflow: charge patient in OptiMantra → package it → take to post office → drop the tracking number here. Coordinators do not order these through LifeFile.</div></div>
  <div class="sts" style="margin-bottom:14px"><div class="st"><div class="stl">📦 To mail</div><div class="stv ${pending.length?'wn':''}">${pending.length}</div></div><div class="st"><div class="stl">✓ Mailed</div><div class="stv sc">${mailed.length}</div></div><div class="st"><div class="stl">Total this list</div><div class="stv">${items.length}</div></div><div class="st"><div class="stl">&nbsp;</div><div class="stv"><button class="btn p" style="font-size:13px" onclick="ST.showNewMailout=!ST.showNewMailout;render()">+ New mail-out</button></div></div></div>
  ${ST.showNewMailout?`<div class="cd cp" style="max-width:600px;margin-bottom:14px;border-color:#fed7aa"><h2 style="margin-bottom:12px;color:#9a3412">Log a new in-office mail-out</h2>
    <div class="f2"><div class="fr"><label>Patient name *</label><input value="${o.patientName||''}" placeholder="Full name" oninput="ST.newMailout.patientName=this.value"></div><div class="fr"><label>Date of birth</label><input value="${o.patientDOB||''}" placeholder="MM/DD/YYYY" oninput="ST.newMailout.patientDOB=this.value"></div></div>
    <div class="f2"><div class="fr"><label>Item being mailed *</label><input value="${o.item||''}" list="moil" placeholder="e.g. HCG 10,000 IU" oninput="ST.newMailout.item=this.value"><datalist id="moil"><option value="HCG Pregnyl 10,000 IU"><option value="HCG 5,000 IU"><option value="Sermorelin"><option value="Testosterone supplies"><option value="BAC water & syringes"></datalist></div><div class="fr"><label>Ordering provider</label><select onchange="ST.newMailout.orderedBy=this.value"><option value="">Select...</option><option value="Ashlee Montalvo NP" ${o.orderedBy==='Ashlee Montalvo NP'?'selected':''}>Ashlee Montalvo NP</option><option value="Tamara Dismukes PA" ${o.orderedBy==='Tamara Dismukes PA'?'selected':''}>Tamara Dismukes PA</option><option value="Leniel Santana MD" ${o.orderedBy==='Leniel Santana MD'?'selected':''}>Leniel Santana MD</option></select></div></div>
    <div class="cr" onclick="ST.newMailout.billed=!ST.newMailout.billed;render()" style="margin-bottom:8px;${o.billed?'background:var(--scb);border-color:#b0e0cc':''}"><input type="checkbox" ${o.billed?'checked':''} readonly><label style="${o.billed?'color:var(--sc);font-weight:600':''}">✓ Patient charged in OptiMantra</label></div>
    <div class="fr"><label>Notes</label><input value="${o.notes||''}" placeholder="Ship-to address change, cold pack, etc." oninput="ST.newMailout.notes=this.value"></div>
    <div style="display:flex;gap:8px;margin-top:4px"><button class="btn p" onclick="subMO()">Add to mail-out list</button><button class="btn" onclick="ST.showNewMailout=false;ST.newMailout={};render()">Cancel</button></div></div>`:''}
  ${pending.length?`<div style="font-size:11px;font-weight:600;text-transform:uppercase;letter-spacing:.5px;color:#9a3412;margin-bottom:6px;padding:6px 12px;background:#fff7ed;border-radius:6px">📦 Ready to mail — needs tracking # (${pending.length})</div>
  <div class="cd" style="margin-bottom:16px"><table><thead><tr><th>Patient</th><th>Item</th><th>Provider</th><th>Billed?</th><th>Logged</th><th style="width:280px">Add tracking # & mark mailed</th><th></th></tr></thead><tbody>${pending.map(m=>`<tr class="rno"><td><strong>${m.patientName}</strong>${m.patientDOB?`<br><span style="color:var(--m);font-size:10px">${m.patientDOB}</span>`:''}</td><td style="font-size:12px">${m.item}</td><td style="font-size:11px">${m.orderedBy||'—'}</td><td>${m.billed?'<span style="color:var(--sc)">✓</span>':'<span style="color:var(--wn)">⚠ No</span>'}</td><td style="font-size:11px;color:var(--m)">${m.dateLogged||'—'}<br><span style="font-size:10px">by ${m.loggedBy||'—'}</span></td><td><div style="display:flex;gap:6px"><input id="mot_${m.id}" placeholder="Tracking number..." style="flex:1;padding:6px 9px;border:.5px solid var(--b);border-radius:6px;font-size:12px;font-family:'DM Mono',monospace"><button class="btn sm p" onclick="setMOTrack('${m.id}')">✓ Mailed</button></div></td><td><button class="btn sm dn" onclick="dMO('${m.id}')">🗑️</button></td></tr>`).join('')}</tbody></table></div>`:'<div class="emp" style="margin-bottom:16px">Nothing waiting to be mailed. 📭</div>'}
  ${mailed.length?`<div style="font-size:11px;font-weight:600;text-transform:uppercase;letter-spacing:.5px;color:var(--sc);margin-bottom:6px;padding:6px 12px;background:var(--scb);border-radius:6px">✓ Mailed (${mailed.length})</div>
  <div class="cd"><table><thead><tr><th>Patient</th><th>Item</th><th>Provider</th><th>Tracking #</th><th>Mailed by</th><th>Date</th><th></th></tr></thead><tbody>${mailed.map(m=>`<tr class="rip"><td><strong>${m.patientName}</strong></td><td style="font-size:12px">${m.item}</td><td style="font-size:11px">${m.orderedBy||'—'}</td><td style="font-family:'DM Mono',monospace;font-size:12px;color:var(--sc)">🚚 ${m.trackingNumber||'(marked mailed)'}</td><td style="font-size:11px">${m.mailedBy||'—'}</td><td style="font-size:11px;color:var(--m)">${m.dateMailed||'—'}</td><td><button class="btn sm dn" onclick="dMO('${m.id}')">🗑️</button></td></tr>`).join('')}</tbody></table></div>`:''}
  </div>`;
}
function subMO(){const o=ST.newMailout||{};if(!o.patientName){alert('Enter the patient name.');return;}if(!o.item){alert('Enter the item being mailed.');return;}ST.mailouts.unshift({id:'mo_'+Date.now(),patientName:o.patientName.trim(),patientDOB:o.patientDOB||'',item:o.item.trim(),orderedBy:o.orderedBy||'',billed:!!o.billed,notes:o.notes||'',trackingNumber:'',mailed:false,dateLogged:new Date().toISOString().split('T')[0],loggedBy:CU?CU.name:''});ST.newMailout={};ST.showNewMailout=false;sMO();render();}
function setMOTrack(id){const inp=document.getElementById('mot_'+id),trk=inp?inp.value.trim():'';const m=ST.mailouts.find(x=>x.id===id);if(!m)return;m.trackingNumber=trk;m.mailed=true;m.dateMailed=new Date().toISOString().split('T')[0];m.mailedBy=CU?CU.name:'';sMO();render();}
function dMO(id){if(confirm('Remove this mail-out entry?')){ST.mailouts=ST.mailouts.filter(x=>x.id!==id);sMO();render();}}

function renderApp(){
  const lm=document.getElementById('lm'),ce=document.getElementById('mc'),tb2=document.getElementById('tbe');
  if(!CU){lm.innerHTML=renderLogin();ce.style.display='none';tb2.style.display='none';return;}
  lm.innerHTML='';ce.style.display='block';tb2.style.display='flex';
  const role=aR();
  const aT=[{id:'orders',label:'Orders'},{id:'new',label:'+ New Order'},{id:'mailout',label:'📦 In-Office Mail-Out'},{id:'patients',label:'Patients'},{id:'pharmacies',label:'Pharmacy Guide'},{id:'formulary',label:'Formulary'},{id:'invoices',label:'Invoices'},{id:'pricing',label:'$ Pricing'},{id:'portals',label:'🔐 Portals'},{id:'settings',label:'⚙ Users'},{id:'ai',label:'🤖 Ask AI'}];
  const vis=aT.filter(t=>{if(t.id==='new'&&!cS('new'))return false;if(t.id==='patients'&&!cS('patients'))return false;if(t.id==='pharmacies'&&!cS('pharmacies'))return false;if(t.id==='formulary'&&!cS('formulary'))return false;if(t.id==='invoices'&&!cS('invoices'))return false;if(t.id==='pricing'&&role!=='admin')return false;if(t.id==='portals'&&!cS('portals'))return false;if(t.id==='settings'&&!cS('settings'))return false;return true;});
  if(!vis.find(t=>t.id===ST.tab))ST.tab='orders';
  document.getElementById('nav').innerHTML=vis.map(t=>`<button onclick="go('${t.id}')" id="tab-${t.id}" class="${ST.tab===t.id?'active':''}">${t.label}</button>`).join('');
  const rm={admin:'Admin',provider:'Provider',coordinator:'Coordinator',staff:'Staff'};
  document.getElementById('ui').innerHTML=`${CU.name} <span class="rb ${role}">${PR?'Previewing: ':''}${rm[role]||role}</span>`;
  const pw=document.getElementById('ptw');
  if(CU.canPreview){pw.innerHTML=`<div class="vt"><span style="color:rgba(255,255,255,.6);font-size:10px">Preview:</span><select onchange="setPrev(this.value)"><option value="" ${!PR?'selected':''}>Admin</option><option value="provider" ${PR==='provider'?'selected':''}>Provider</option><option value="coordinator" ${PR==='coordinator'?'selected':''}>Coordinator</option><option value="staff" ${PR==='staff'?'selected':''}>Staff</option></select></div>`;}else{pw.innerHTML='';}
  render();
}
function setPrev(r){PR=r||null;renderApp();}

let CLO=null,CS=0,CLD=[];
function gPR(mn){if(!mn)return null;const match=FORMULARY.find(f=>f.name===mn||mn.toLowerCase().includes(f.name.toLowerCase().substring(0,12)));if(!match)return null;const nl=mn.toLowerCase();let pid=null;if(nl.includes('testosterone')||nl.includes('test cyp')){if(nl.includes('female')||nl.includes('50mg')||nl.includes('women'))pid='hallandale';else if(nl.includes('250mg')||nl.includes('high'))pid='brooksville';else pid='centercity';}else if(nl.includes('semaglutide'))pid='centercity';else if(nl.includes('bpc')||nl.includes('peptide'))pid='alphabio';const priced=match.rows.filter(r=>r.p!=null&&r.p>0).sort((a,b)=>a.p-b.p);let best=priced.length?priced[0]:null;if(pid){const f=match.rows.find(r=>r.ph===pid);if(f)best=f;}if(!best)return null;const phD=PHARMACIES.find(p=>p.id===best.ph);return{formularyItem:match,bestRow:best,phD,pN:best.l?best.l.replace(/ -.*/,'').replace(/Alpha Bio -.*/,'Alpha Bio'):'Unknown',isCtrl:match.flags.includes('ctrl'),needsConsent:match.flags.includes('research'),patientPrice:PP[match.name]||null};}

function rQCB(){const mo=FORMULARY.filter(f=>f.rows.some(r=>r.p>0)).map(f=>`<option value="${f.name}">${f.name}</option>`).join('');return`<div class="qb"><h3>⚡ Quick capture</h3><p>Provider tells you patient + medication. Fill this out and hit Submit.</p><div class="qg"><div class="qf"><label>Patient name</label><input id="qp" placeholder="Full name" oninput="qcU()"></div><div class="qf"><label>Medication</label><input id="qm" list="qml" placeholder="Start typing..." oninput="qcU()" autocomplete="off"><datalist id="qml">${mo}</datalist></div><div class="qf"><label>Provider</label><select id="qpv"><option value="">Select...</option><option value="Ashlee Montalvo NP">Ashlee</option><option value="Tamara Dismukes PA">Tamara</option><option value="Leniel Santana MD">Leniel</option></select></div><button class="qs" onclick="qcS()">Start checklist →</button></div><div class="qsg" id="qsg"></div></div>`;}
function qcU(){const med=document.getElementById('qm')?.value||'',sg=document.getElementById('qsg');if(!sg)return;if(med.length<3){sg.className='qsg';return;}const rec=gPR(med);if(!rec){sg.className='qsg';return;}const ph=rec.phD;sg.className='qsg show';sg.innerHTML=`<div class="qpr">→ Order from: ${rec.pN}${ph?' · '+ph.ta:''}</div><div class="qpm">Method: ${ph?ph.method:'—'} · Login: ${ph?ph.login:'See pharmacy guide'}</div>${rec.isCtrl?'<div class="qw">⚠ Controlled — wet signature + fax required</div>':''}${rec.needsConsent?'<div class="qw">Research peptide — consent form must be on file</div>':''}${rec.patientPrice?`<div style="font-size:11px;color:#6ee7b7;margin-top:4px;font-weight:600">Patient charge: $${rec.patientPrice}</div>`:''}`;}
function qcS(){const patient=document.getElementById('qp')?.value?.trim(),med=document.getElementById('qm')?.value?.trim(),provider=document.getElementById('qpv')?.value;if(!patient){alert('Enter the patient name.');return;}if(!med){alert('Enter the medication.');return;}const dup=ST.orders.some(o=>o.patientName.toLowerCase()===patient.toLowerCase()&&o.medication.toLowerCase()===med.toLowerCase());if(dup&&!confirm(`⚠️ DUPLICATE: ${patient} already has an order for ${med}.\n\nCreate anyway?`))return;const rec=gPR(med);CLO={id:'ord_'+Date.now(),patientName:patient,medication:med,orderedBy:provider||'Provider',pharmacy:rec?.pN||'',method:rec?.phD?.method||'',controlled:rec?.isCtrl||false,researchConsent:rec?.needsConsent||false,billingConfirmed:false,paymentVerifiedInOpti:false,status:'Awaiting Payment Verification',dateOrdered:new Date().toISOString().split('T')[0],_rec:rec};CS=0;CLD=[];rCOL();}

function rCOL(){const ex=document.getElementById('cl_ov');if(ex)ex.remove();const o=CLO;if(!o)return;const rec=o._rec||gPR(o.medication),pp=rec?.patientPrice||PP[o.medication]||null;
const steps=[
  {id:'billing',title:'Step 1 — Confirm patient billed',desc:`Provider must confirm billing.${pp?' Patient price: <strong>$'+pp+'</strong>':''}`,action:`<div class="clc" onclick="this.querySelector('input').click()"><input type="checkbox" id="clb" onchange="clCB()"><label for="clb">Provider confirmed patient was billed${pp?' <strong>$'+pp+'</strong>':''}</label></div>`},
  {id:'sig',title:'Step 2 — Sig / directions',desc:'Enter the sig as it appears on the label.',action:`<input class="cli" id="cls2" style="margin-top:6px;font-family:'DM Mono',monospace;font-size:13px" placeholder="e.g. Inject 0.50mL twice weekly IM" value="${o.sig||''}"><div style="font-size:10px;color:var(--m);margin-top:4px">e.g. Inject 0.25mL once weekly SubQ · Take ½ tablet daily</div><div class="cla" style="margin-top:8px"><button class="clbt sc" onclick="clSS()">Save & continue →</button></div>`},
  {id:'place',title:'Step 3 — Place order in LifeFile',desc:'Did you place this in LifeFile?',action:`${o.controlled?`<div class="clw">⚠ CONTROLLED — Print, get WET SIGNATURE, fax BEFORE placing in LifeFile.</div>`:''}${o.researchConsent?`<div class="clw" style="background:var(--abb);border-color:#e0a8d0;color:var(--ab)">Research peptide — confirm consent on file.</div>`:''}
  <div style="display:flex;gap:8px;margin-top:10px;margin-bottom:10px"><button class="clbt sc" style="flex:1;justify-content:center" onclick="clSOF()">✓ Yes — I placed it</button><button class="clbt sec" style="flex:1;justify-content:center" onclick="clFC()">✗ No — flag for coordinator</button></div>
  <div id="cl_onw" style="display:none"><label style="font-size:10px;font-weight:600;text-transform:uppercase;color:var(--m);display:block;margin-bottom:4px">LifeFile order #</label><div style="display:flex;gap:6px"><input class="cli" style="margin-top:0;font-family:'DM Mono',monospace" id="cl_on" placeholder="Paste order number..."><button class="clbt sc" onclick="clSON()" style="white-space:nowrap">Save →</button></div></div>`},
  {id:'done',title:'✓ Order logged',desc:o._needsCoordinatorOrder?'Queued for coordinator.':'Order placed. Add tracking when available.',action:o._needsCoordinatorOrder?`<div class="al in">ℹ️ Flagged for coordinator to place in LifeFile.</div><button class="clbt sc" style="width:100%;padding:11px;justify-content:center" onclick="clFin()">Done ✓</button>`:`<div style="display:flex;gap:6px;margin-bottom:10px"><input class="cli" style="margin-top:0" id="cl_tr" placeholder="Tracking # (optional)"><button class="clbt p" onclick="clST()">Save</button></div><button class="clbt sc" style="width:100%;padding:11px;justify-content:center" onclick="clFin()">Done ✓</button>`}
];
const ov=document.createElement('div');ov.id='cl_ov';ov.className='clo';
ov.innerHTML=`<div class="clb"><div class="clh"><div style="display:flex;align-items:center;gap:10px">${CS>0?`<button onclick="clBk()" style="background:none;border:.5px solid var(--b);border-radius:7px;padding:5px 12px;font-size:12px;font-weight:600;cursor:pointer;color:var(--t);font-family:'DM Sans',sans-serif">← Back</button>`:''}<div><h2>Order checklist</h2><div class="clp">${o.patientName} — ${o.medication}</div></div></div><button onclick="clCl()" style="background:none;border:none;font-size:20px;cursor:pointer;color:var(--m)">✕</button></div>
<div class="clst">${steps.map((s,i)=>{const done=CLD.includes(s.id),active=i===CS,locked=i>CS;return`<div class="cls ${done?'done':active?'active':locked?'locked':''}"><div class="cln">${done?'✓':i+1}</div><div class="clbd"><div class="clt">${s.title}</div><div class="cld">${s.desc}</div>${active||done?`<div class="cla" id="cla_${s.id}">${active?s.action:''}</div>`:''}</div></div>`;}).join('')}</div></div>`;
document.body.appendChild(ov);}

function clAdv(sid){if(!CLD.includes(sid))CLD.push(sid);CS++;rCOL();}
function clBk(){if(CS<=0)return;CS--;const ids=['billing','sig','place','done'];CLD=CLD.filter(id=>id!==ids[CS]);rCOL();}
function clCB(){const cb=document.getElementById('clb');if(cb&&cb.checked){CLO.billingConfirmed=true;setTimeout(()=>clAdv('billing'),300);}}
function clSS(){const sig=document.getElementById('cls2')?.value?.trim();if(!sig){alert('Please enter the sig.');return;}CLO.sig=sig;clAdv('sig');}
function clSOF(){const w=document.getElementById('cl_onw');if(w)w.style.display='block';document.getElementById('cl_on')?.focus();}
function clFC(){CLO.status='Awaiting Payment Verification';CLO._needsCoordinatorOrder=true;const ex=ST.orders.find(o=>o.id===CLO.id);if(!ex)ST.orders.unshift({...CLO});else Object.assign(ex,CLO);sO();clAdv('place');}
function clSON(){const num=document.getElementById('cl_on')?.value?.trim();if(!num){alert('Enter the order number.');return;}CLO.orderNumber=num;CLO.status='Ordered';const ex=ST.orders.find(o=>o.id===CLO.id);if(!ex)ST.orders.unshift({...CLO});else Object.assign(ex,CLO);sO();clAdv('place');}
function clST(){const trk=document.getElementById('cl_tr')?.value?.trim();if(trk){CLO.trackingNumber=trk;const ex=ST.orders.find(o=>o.id===CLO.id);if(ex)ex.trackingNumber=trk;sO();}}
function clFin(){const ex=ST.orders.find(o=>o.id===CLO.id);if(!ex)ST.orders.unshift({...CLO});sO();clCl();ST.tab='orders';render();}
function clCl(){const el=document.getElementById('cl_ov');if(el)el.remove();CLO=null;CS=0;CLD=[];}

function rCO(){
  if(ST.selOrder){const o=ST.orders.find(x=>x.id===ST.selOrder);if(o){return`<div style="max-width:680px"><div style="display:flex;align-items:center;gap:10px;margin-bottom:14px"><button onclick="ST.selOrder=null;render()" style="background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.2);color:#fff;padding:7px 14px;border-radius:8px;font-size:12px;cursor:pointer;font-family:'DM Sans',sans-serif">← Back</button><span style="font-size:13px;color:rgba(255,255,255,.8);font-weight:500">${o.patientName} — ${o.medication}</span></div><div class="cd cp">${rCD(o)}</div></div>`;}}
  const aw=ST.orders.filter(o=>o.status==='Awaiting Payment Verification'),rp=ST.orders.filter(o=>o.status==='Payment Confirmed — Ready to Place'),ac=ST.orders.filter(o=>['Ordered','Processing'].includes(o.status)),ot=ST.orders.filter(o=>!['Awaiting Payment Verification','Payment Confirmed — Ready to Place','Ordered','Processing'].includes(o.status));
  const srch=(ST.filterSearch||'').toLowerCase(),fo=arr=>srch?arr.filter(o=>o.patientName.toLowerCase().includes(srch)||o.medication.toLowerCase().includes(srch)):arr;
  function oRow(o){const sc=[o.billingConfirmed,o.paymentVerifiedInOpti,o.pharmacy,o.doseAmount,o.orderNumber].filter(Boolean).length;return`<tr class="${oRC(o)}" onclick="selO('${o.id}')" style="cursor:pointer"><td style="font-size:12px"><div style="font-weight:600">${o.orderedBy||'—'}</div>${o.placedBy&&o.placedBy!==o.orderedBy?`<div style="font-size:10px;color:var(--in);margin-top:2px">placed by ${o.placedBy}</div>`:''}</td><td><strong>${o.patientName}</strong>${o.onSubscription?' <span class="bdg on-subscription" style="min-width:auto;font-size:9px">📋</span>':''}${o.patientDOB?`<br><span style="color:var(--m);font-size:10px">${o.patientDOB}</span>`:''}</td><td style="font-size:12px">${o.medication}</td><td onclick="event.stopPropagation()">${rPB(o.id,true)}</td><td><span class="bdg ${sCls(o.status)}">${o.status}</span></td><td style="font-family:'DM Mono',monospace;font-size:11px">${o.trackingNumber||'—'}</td><td onclick="event.stopPropagation()" style="display:flex;gap:6px;align-items:center"><button class="clbt sc" style="font-size:11px;padding:5px 11px" onclick="oCFL('${o.id}')">▶ (${sc}/5)</button><button class="btn sm dn" style="padding:4px 8px" onclick="dOrd('${o.id}')">🗑️</button></td></tr>`;}
  function sec(title,color,orders){if(!orders.length)return '';return`<div style="margin-bottom:14px"><div style="font-size:11px;font-weight:600;text-transform:uppercase;letter-spacing:.5px;color:${color};margin-bottom:6px;padding:6px 12px;background:${color}18;border-radius:6px">${title} (${orders.length})</div><div class="cd"><table><thead><tr><th>Provider</th><th>Patient</th><th>Medication</th><th>Payment</th><th>Status</th><th>Tracking</th><th></th></tr></thead><tbody>${orders.map(o=>oRow(o)).join('')}</tbody></table></div></div>`;}
  return rQCB()+`<div style="margin-bottom:10px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:8px"><div style="font-size:13px;font-weight:600;color:var(--m)">Open orders</div><input style="padding:7px 10px;border:.5px solid var(--b);border-radius:8px;font-size:12px;font-family:'DM Sans',sans-serif;width:220px" placeholder="Search..." oninput="ST.filterSearch=this.value;dR()" value="${ST.filterSearch||''}"></div>`+sec('⚠ Awaiting payment','#8a4f0a',fo(aw))+sec('✓ Ready to place','#0b6e4f',fo(rp))+sec('Active','#1a5fa8',fo(ac))+(fo(ot).length?`<details style="margin-top:8px"><summary style="cursor:pointer;font-size:12px;color:var(--m);padding:4px 0">Completed / other (${fo(ot).length})</summary><div class="cd" style="margin-top:6px"><table><thead><tr><th>Provider</th><th>Patient</th><th>Medication</th><th>Payment</th><th>Status</th><th>Tracking</th><th></th></tr></thead><tbody>${fo(ot).map(o=>oRow(o)).join('')}</tbody></table></div></details>`:'');
}

function oCFL(oid){const o=ST.orders.find(x=>x.id===oid);if(!o)return;CLO={...o,_rec:gPR(o.medication)};CLD=[];if(o.billingConfirmed)CLD.push('billing');if(o.paymentVerifiedInOpti)CLD.push('payment');if(o.pharmacy)CLD.push('pharmacy');if(o.orderNumber)CLD.push('place');CS=CLD.length;rCOL();}

function rCD(o){
  const fm=FORMULARY.find(f=>f.name===o.medication),po=fm?fm.rows.filter(r=>r.p>0).sort((a,b)=>a.p-b.p):[];
  return`<div class="dt"><div style="margin-bottom:10px;display:flex;justify-content:space-between;align-items:center"><div><strong>${o.patientName} — ${o.medication}</strong><div style="font-size:11px;color:var(--m);margin-top:3px">Ordering provider: <strong style="color:var(--t)">${o.orderedBy||'—'}</strong>${o.placedBy&&o.placedBy!==o.orderedBy?` · placed by <strong style="color:var(--in)">${o.placedBy}</strong>`:''}</div></div><button class="btn sm" onclick="ST.selOrder=null;render()">✕</button></div>
  ${o.onSubscription?'<div class="al in" style="margin-bottom:8px">📋 <strong>Subscription patient</strong> — do NOT charge.</div>':''}
  ${o.controlled?`<div class="al wn" style="margin-bottom:8px">Controlled — print, wet sig, fax</div>`:''}
  ${po.length?`<div style="margin-bottom:12px"><div style="font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.4px;color:var(--m);margin-bottom:6px">Where to order</div><table style="font-size:11px;width:100%"><thead><tr><th>Pharmacy</th><th>Turnaround</th><th>Method</th><th>Notes</th></tr></thead><tbody>${po.map((r,i)=>{const pd=PHARMACIES.find(p=>p.id===r.ph);return`<tr style="${i===0?'background:var(--scb)':''}"><td><span class="ph ${r.ph||'stryker'}">${r.l.replace(/ —.*/,'')}</span>${i===0?' ⭐':''}</td><td style="font-size:10px">${pd?pd.ta:'—'}</td><td style="font-size:10px">${pd?pd.method:'—'}</td><td style="color:var(--m);font-size:10px">${r.n||'—'}</td></tr>`;}).join('')}</tbody></table></div>`:''}
  <div style="display:flex;flex-direction:column;gap:10px">
    <div class="dr"><span class="dl">Provider billed</span><span>${o.billingConfirmed?'✓ Yes':'⚠ Not confirmed'}</span></div>
    <div class="dr"><span class="dl">On subscription</span><span style="display:flex;gap:6px;align-items:center">${o.onSubscription?'<span style="color:#7c3aed;font-weight:600">✓ Monthly</span>':'<span style="color:var(--m)">No</span>'}<button class="btn sm" style="padding:3px 8px;font-size:10px" onclick="uO('${o.id}','onSubscription',!${!!o.onSubscription});render()">${o.onSubscription?'Remove':'Mark subscription'}</button></span></div>
    <div style="padding:10px 12px;border:.5px solid var(--sc);border-radius:8px;background:var(--scb);display:flex;justify-content:space-between;align-items:center"><span style="font-size:11px;color:var(--m);font-weight:500;text-transform:uppercase;letter-spacing:.3px">Patient charge</span><span style="font-size:16px;font-weight:700;color:${o.onSubscription?'#7c3aed':'var(--sc)'}">${o.onSubscription?'📋 No charge':PP[o.medication]?'$'+PP[o.medication]:'<span style="font-size:12px;color:var(--wn)">Not set</span>'}</span></div>
    <div style="padding:10px 12px;border:.5px solid var(--b);border-radius:8px;background:var(--s);display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px"><span style="font-size:11px;font-weight:600;color:var(--m);text-transform:uppercase;letter-spacing:.3px">OptiMantra payment</span><span style="display:flex;align-items:center;gap:8px;flex-wrap:wrap">${rPB(o.id,false)}<button class="btn sm" onclick="setPS('${o.id}','paid',0)">✓ Paid</button><input type="number" id="cba_${o.id}" placeholder="$ bal" step="0.01" style="width:70px;padding:4px 6px;border:.5px solid var(--b);border-radius:6px;font-size:11px;font-family:'DM Mono',monospace"><button class="btn sm dn" onclick="setPS('${o.id}','bal',parseFloat(document.getElementById('cba_${o.id}').value)||0)">Set balance</button></span></div>
    <div><label style="font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.3px;color:var(--m);display:block;margin-bottom:5px">Pharmacy</label><select onchange="uO('${o.id}','pharmacy',this.value);render()" style="width:100%;padding:8px 10px;border:.5px solid var(--b);border-radius:6px;font-size:12px;font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--t)"><option value="">Select...</option>${PHARMACIES.filter(p=>!['Coming Soon','Research'].includes(p.type)).map(p=>`<option value="${p.name}" ${o.pharmacy===p.name?'selected':''}>${p.name}</option>`).join('')}</select>${o.pharmacy?rIP(o.pharmacy):'<div style="font-size:11px;color:var(--m);margin-top:4px">Select pharmacy to see login info</div>'}</div>
    <div style="display:flex;align-items:center;justify-content:space-between;padding:9px 12px;border:.5px solid ${o.paymentVerifiedInOpti?'var(--sc)':'var(--b)'};border-radius:8px;background:${o.paymentVerifiedInOpti?'var(--scb)':'var(--s)'}"><span style="font-size:12px;font-weight:500;color:${o.paymentVerifiedInOpti?'var(--sc)':'var(--t)'}">Payment verified in Opti${o.paymentVerifiedInOpti&&o.paymentVerifiedBy?' — by '+o.paymentVerifiedBy:''}</span>${o.paymentVerifiedInOpti?`<span style="font-size:18px">✅</span>`:`<button class="btn sm p" onclick="cVP('${o.id}',true)">Mark verified</button>`}</div>
    <div><label style="font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.3px;color:var(--m);display:block;margin-bottom:5px">LifeFile Order #</label><div style="display:flex;gap:6px"><input id="on_${o.id}" value="${o.orderNumber||''}" placeholder="Type order number..." style="flex:1;padding:8px 10px;border:.5px solid var(--b);border-radius:6px;font-size:13px;font-family:'DM Mono',sans-serif;background:var(--bg);color:var(--t)"><button class="btn sm p" onclick="cSON('${o.id}',document.getElementById('on_${o.id}').value)">Save</button></div>${o.orderNumber?`<div style="font-size:11px;color:var(--sc);margin-top:4px">✓ Saved</div>`:''}</div>
    <div><label style="font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.3px;color:var(--m);display:block;margin-bottom:5px">Tracking #</label><div style="display:flex;gap:6px"><input id="ct_${o.id}" value="${o.trackingNumber||''}" placeholder="Type tracking number..." style="flex:1;padding:8px 10px;border:.5px solid var(--b);border-radius:6px;font-size:13px;font-family:'DM Mono',sans-serif;background:var(--bg);color:var(--t)"><button class="btn sm p" onclick="uO('${o.id}','trackingNumber',document.getElementById('ct_${o.id}').value)">Save</button></div>${o.trackingNumber?`<div style="font-size:11px;color:var(--sc);margin-top:4px">✓ Saved</div>`:''}</div>
    <div><label style="font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:.3px;color:var(--m);display:block;margin-bottom:5px">Staff note</label><textarea id="cn_${o.id}" style="width:100%;padding:8px 10px;border:.5px solid var(--b);border-radius:6px;font-size:12px;font-family:'DM Sans',sans-serif;min-height:52px;resize:vertical;background:var(--bg);color:var(--t)" placeholder="Notes visible to all staff...">${o.notes||''}</textarea><button class="btn sm" style="margin-top:4px" onclick="uO('${o.id}','notes',document.getElementById('cn_${o.id}').value)">Save note</button></div>
    <div><button class="btn sm dn" onclick="cSB('${o.id}')">↩ Send back to provider</button></div>
  </div></div>`;
}

function rPhL(q){const el=document.getElementById('phLR');if(!el)return;if(!q||q.length<2){el.innerHTML='';return;}const ql=q.toLowerCase(),matches=FORMULARY.filter(f=>f.name.toLowerCase().includes(ql)&&f.rows.some(r=>r.p>0)).slice(0,8);if(!matches.length){el.innerHTML=`<div style="font-size:12px;color:var(--m);padding:6px 0">No medications found matching "${q}".</div>`;return;}const isA=aR()==='admin';el.innerHTML=matches.map(f=>{const rows=f.rows.filter(r=>r.p>0).sort((a,b)=>a.p-b.p),best=rows[0],bpn=best.l.replace(/ —.*/,'').replace(/Alpha Bio —.*/,'Alpha Bio'),pp2=PP[f.name],pd=PHARMACIES.find(p=>p.id===best.ph),pns=[...new Set(rows.map(r=>r.l.replace(/ —.*/,'').replace(/Alpha Bio —.*/,'Alpha Bio')))];return`<div style="border:.5px solid var(--b);border-radius:8px;padding:10px 12px;margin-bottom:6px;background:var(--bg)"><div style="display:flex;justify-content:space-between;align-items:baseline;margin-bottom:6px"><div style="font-size:12px;font-weight:600">${f.name}</div><div style="font-size:11px;color:var(--sc);font-weight:600">${pp2?'Charge: $'+pp2:'<span style="color:var(--wn)">Price not set</span>'}</div></div><div style="display:flex;gap:6px;flex-wrap:wrap;margin-bottom:6px">${pns.map((name,i)=>`<div style="font-size:11px;padding:3px 8px;border-radius:10px;background:${i===0?'var(--scb)':'var(--s)'};border:.5px solid ${i===0?'var(--sc)':'var(--b)'};color:${i===0?'var(--sc)':'var(--t)'}">${name}${i===0?' ⭐':''}${isA&&rows[i]?' · COG $'+rows[i].p:''}</div>`).join('')}</div><div style="font-size:11px;color:var(--m)"><strong style="color:var(--t)">Best: ${bpn}</strong> · ${pd?pd.ta:'—'} · ${pd?pd.method:'—'}${f.flags.includes('ctrl')?'<span style="margin-left:6px;color:var(--dn);font-weight:600">■ Controlled</span>':''}${f.flags.includes('research')?'<span style="margin-left:6px;color:var(--ab);font-weight:600">Consent required</span>':''}</div></div>`;}).join('');}

function cVP(id,c){const o=ST.orders.find(x=>x.id===id);if(!o)return;o.paymentVerifiedInOpti=c;o.paymentVerifiedBy=c?CU.name:'';sO();render();}
function cSON(id,num){if(!num||!num.trim()){alert('Please enter an order number.');return;}const o=ST.orders.find(x=>x.id===id);if(!o)return;o.orderNumber=num.trim();o.status='Ordered';o.orderedAt=new Date().toLocaleDateString();sO();render();}
function cSB(id){const reason=prompt('Reason for sending back:');if(reason===null)return;if(!reason.trim()){alert('Please enter a reason.');return;}const o=ST.orders.find(x=>x.id===id);if(o){o.status='Returned to Provider';o.returnedReason=reason.trim();o.returnedBy=CU.name;sO();renderApp();}}

function rFFR(){const cats=['All',...[...new Set(FORMULARY.map(x=>x.cat))]];return`<div style="display:flex;gap:8px;margin-bottom:10px"><input id="fsi" style="flex:1;padding:7px 10px;border:.5px solid var(--b);border-radius:8px;font-size:12px;font-family:'DM Sans',sans-serif" placeholder="Search medications..." oninput="ST.formSearch=this.value;rFR()" value="${ST.formSearch}"></div><div class="al in" style="margin-bottom:12px">Ordering reference — patient pricing shown. Contact Admin for full cost details.</div><div class="cts">${cats.map(c=>`<button class="ct2 ${ST.catFilter===c?'active':''}" onclick="ST.catFilter='${c}';render()">${c}</button>`).join('')}</div><div id="fr2">${bFR()}</div>`;}
function bFR(){const srch=ST.formSearch.toLowerCase();let items=FORMULARY;if(ST.catFilter!=='All')items=items.filter(d=>d.cat===ST.catFilter);if(srch)items=items.filter(d=>d.name.toLowerCase().includes(srch)||d.rows.some(r=>r.l.toLowerCase().includes(srch)));items=items.filter(d=>!d.cat.includes('In-Office (PDRX)')&&!d.cat.includes('IV Infusions'));return bPFT(items,ST.catFilter==='All'&&!srch);}
function rFR(){const el=document.getElementById('fr2');if(el)el.innerHTML=bFR();}
function bPFT(items,grouped){if(!items.length)return`<div class="emp">No results.</div>`;if(grouped){const g={};items.forEach(i=>{(g[i.cat]=g[i.cat]||[]).push(i);});return Object.entries(g).map(([cat,rows])=>`<div class="cd" style="margin-bottom:10px"><div class="ch">${cat}</div>${pFT(rows)}</div>`).join('');}return`<div class="cd">${pFT(items)}</div>`;}
function pFT(items){const isP=aR()==='provider';return`<table><thead><tr><th style="width:35%">Medication</th>${!isP?'<th>Pharmacy</th>':''}<th style="width:120px">Method</th><th style="width:100px">Patient price</th><th style="width:80px">Flags</th></tr></thead><tbody>${items.map(row=>{const pns=[...new Set(row.rows.map(r=>r.l.replace(/ — .*/,'').replace(/Alpha Bio —.*/,'Alpha Bio')))].join(', ');const method=row.rows[0]?.n?.includes('LifeFile')?'LifeFile':row.rows[0]?.n?.includes('eRx')?'eRx/Optimantra':row.rows[0]?.n?.includes('Website')?'Website':'See guide';const pd2=PP[row.name]>0?'$'+PP[row.name]:PP[row.name]===0?'<span style="color:var(--m);font-size:11px">Bundled</span>':'<span style="color:var(--m);font-style:italic">—</span>';return`<tr><td><strong style="font-size:12px">${row.name.replace('⚠️ ','')}</strong></td>${!isP?`<td style="font-size:12px">${pns}</td>`:''}<td style="font-size:11px;color:var(--m)">${method}</td><td style="font-size:12px;font-weight:600;color:var(--sc)">${pd2}</td><td>${row.flags.filter(f=>f!=='inoffice').map(fE).join('')}</td></tr>`;}).join('')}</tbody></table>`;}

const DP={'Tirzepatide/Glycine 10mg/mL 3mL (30mg)':299,'Tirzepatide/Glycine 10mg/mL 6mL (60mg)':699,'Tirzepatide FORTE 15mg/mL 4mL — >10mg/wk':699,'Semaglutide 2.5mg/mL 4mL (10mg)':279,'Semaglutide 2.5mg/mL 5mL (12.5mg)':279,'Semaglutide 2.5mg/mL 1mL':110,'Retatrutide 12mg vial':350,'Retatrutide 20mg (SOMA)':400,'Retatrutide 24mg vial':450,'Retatrutide 60mg in-office':975,'Test Cyp 200mg/mL 5mL':129,'Test Cyp 200mg/mL 10mL mfg':99,'Test Cyp 250mg/mL 10mL HIGH DOSE':132,'Test 50mg/mL 2mL (female)':65,'Stanozolol 25mg cap (ea)':5,'Stanozolol 50mg cap (ea)':6,'Oxandrolone 2.5mg #30':85,'Oxandrolone 2.5mg #60':175,'Oxandrolone 2.5mg #90':245,'Oxandrolone 5mg #30':100,'Oxandrolone 5mg #60':190,'Oxandrolone 5mg #90':260,'Oxandrolone 10mg #90':310,'Oxandrolone 25mg #30':195,'Oxandrolone 25mg #60':340,'Oxandrolone 25mg #90':450,'Aminophylline/Glycyrrhetinic cream 2.5%/0.5% 60g (spot fat loss)':165,'Nandrolone (Deca) 200mg/mL 10mL':150,'Omnitrope HGH 5.8mg kit':700,'Enclomiphene 50mg ea':4.44,'Enclomiphene 37.5mg (¾ of 50mg flex tab)':3.50,'Enclomiphene 50mg Flex-Dose tab (Strive)':4.44,'Enclomiphene 25mg ea':2.0,'Enclomiphene 12.5mg ea':2.0,'HCG Pregnyl 10,000 IU':250,'Gonadorelin 200mcg/mL 5mL':40,'Gonadorelin 200mcg/mL 10mL':80,'Wolverine BPC-157 10mg/TB500 10mg':170,'GLOW 50 — GHK-Cu 30mg/BPC/TB500':175,'KLOW 80 — GHK-Cu 50mg/KPV/BPC/TB500':280,'Triple Regulator 60mg':975,'Sermorelin 30mg vial (503a)':250,'Sermorelin 15mg vial (503a)':175,'Sermorelin 15mg vial Hallandale (503a)':175,'Sermorelin 10mg vial (research)':150,'Tesamorelin 10mg':120,'Kisspeptin 10mg':210,'NAD+ 1000mg Synthetic':180,'Tadalafil (ALL strengths)':38,'Tadalafil 5mg ea (compound only)':4.0,'Sildenafil 100mg ea':4.5,'Metformin 500mg ea':0.50,'LDN 4.5mg 90ct':140,'Ketotifen 1mg 90ct':160,'Sirolimus 3mg ea':8,'Progesterone 100mg cap ea':2.5,'Progesterone 200mg cap ea':4.0,'Euphoria/Climax cream':99,'Armour Thyroid 60mg ea':3.0,'NP Thyroid 60mg 30ct':70,'Liothyronine T3 25mcg 90ct':80,'Glutathione 200mg/mL 30mL':99,'B12 Methylcobalamin 5mg/mL 10mL':50,'NAD+ 100mg/mL 10mL':130,'L-Carnitine 500mg/mL 30mL':99,'Vitamin D3 50,000IU/mL 30mL':100,'Myers Cocktail premix 10mL':150,'B-Lean IV Kit':150,'Lipo-Mino 30mL w/Carnitine':99,'Iron Infusion — Venofer 200mg':200,'Ceftriaxone 1g vial':40,'Toradol 30mg/mL 1mL':30};
let PP={...DP};
function gMC(p){if(p===null||isNaN(p))return 'var(--m)';if(p<30)return 'var(--dn)';if(p<60)return 'var(--wn)';return 'var(--sc)';}
function gME(p){if(p===null||isNaN(p))return '⚪';if(p<30)return '🔴';if(p<60)return '🟡';return '🟢';}

function rPr(){
  const cats=[...new Set(FORMULARY.map(x=>x.cat))],srch=(ST.pricingSearch||'').toLowerCase(),catF=ST.pricingCat||'All';
  let items=FORMULARY.filter(f=>{const hc=f.rows.some(r=>r.p&&r.p>0);if(!hc)return false;if(catF!=='All'&&f.cat!==catF)return false;if(srch&&!f.name.toLowerCase().includes(srch)&&!f.cat.toLowerCase().includes(srch))return false;return true;});
  const priced=items.filter(f=>PP[f.name]),red=priced.filter(f=>{const bc=Math.min(...f.rows.filter(r=>r.p>0).map(r=>r.p)),pp2=PP[f.name],m=pp2?((pp2-bc)/pp2)*100:null;return m!==null&&m<30;}),green=priced.filter(f=>{const bc=Math.min(...f.rows.filter(r=>r.p>0).map(r=>r.p)),pp2=PP[f.name],m=pp2?((pp2-bc)/pp2)*100:null;return m!==null&&m>=60;});
  return`<div><div class="sh"><h2>Pricing & Margin Calculator</h2><span style="font-size:11px;color:var(--m)">Admin only</span></div>
  <div class="sts" style="margin-bottom:16px"><div class="st"><div class="stl">Items to price</div><div class="stv wn">${items.length-priced.length}</div></div><div class="st"><div class="stl">🔴 Low margin</div><div class="stv dn">${red.length}</div></div><div class="st"><div class="stl">🟢 Healthy</div><div class="stv sc">${green.length}</div></div><div class="st"><div class="stl">Total priced</div><div class="stv">${priced.length}/${items.length}</div></div></div>
  <div style="display:flex;gap:8px;margin-bottom:12px;flex-wrap:wrap"><input id="psi" style="flex:1;min-width:180px;padding:7px 10px;border:.5px solid var(--b);border-radius:8px;font-size:12px;font-family:'DM Sans',sans-serif" placeholder="Search..." oninput="ST.pricingSearch=this.value;renderPT()" value="${ST.pricingSearch||''}"><select style="padding:7px 10px;border:.5px solid var(--b);border-radius:8px;font-size:12px;font-family:'DM Sans',sans-serif" onchange="ST.pricingCat=this.value;renderPT()"><option value="All">All categories</option>${cats.map(c=>`<option value="${c}" ${catF===c?'selected':''}>${c}</option>`).join('')}</select><select style="padding:7px 10px;border:.5px solid var(--b);border-radius:8px;font-size:12px;font-family:'DM Sans',sans-serif" onchange="ST.pricingFilter=this.value;renderPT()"><option value="all">Show all</option><option value="unpriced">Unpriced</option><option value="red">🔴 Low</option><option value="yellow">🟡 OK</option><option value="green">🟢 Healthy</option></select></div>
  <div class="cd"><table><thead><tr><th style="width:32%">Medication</th><th style="width:14%">Best COG</th><th style="width:16%">Source</th><th style="width:14%">Patient $</th><th style="width:10%">Profit</th><th style="width:10%">Margin</th><th style="width:4%"></th></tr></thead><tbody id="pt">${bPR()}</tbody></table></div></div>`;
}
function bPR(){const srch=(ST.pricingSearch||'').toLowerCase(),catF=ST.pricingCat||'All',pf=ST.pricingFilter||'all',fe=f=>`<span class="bdg ${f}">${f}</span>`;return FORMULARY.filter(f=>{if(!f.rows.some(r=>r.p>0))return false;if(catF!=='All'&&f.cat!==catF)return false;if(srch&&!f.name.toLowerCase().includes(srch)&&!f.cat.toLowerCase().includes(srch))return false;const bc=Math.min(...f.rows.filter(r=>r.p>0).map(r=>r.p)),pp2=PP[f.name]||0,m=pp2?((pp2-bc)/pp2)*100:null;if(pf==='unpriced')return !pp2;if(pf==='red')return m!==null&&m<30;if(pf==='yellow')return m!==null&&m>=30&&m<60;if(pf==='green')return m!==null&&m>=60;return true;}).map(f=>{const cr=f.rows.filter(r=>r.p&&r.p>0);if(!cr.length)return '';const br=cr.reduce((a,b)=>a.p<=b.p?a:b),bc=br.p,bs=br.l.replace(/ — .*/,'').replace(/Alpha Bio —.*/,'Alpha Bio'),pp2=PP[f.name]||'',profit=pp2?(pp2-bc).toFixed(2):'—',mp=pp2?((pp2-bc)/pp2*100).toFixed(0):null,mc=gMC(mp?parseFloat(mp):null),me=gME(mp?parseFloat(mp):null),key=f.name.replace(/'/g,"\\'").replace(/"/g,'&quot;');return`<tr style="${!pp2?'background:#fffdf5':''}"><td><div style="font-size:12px;font-weight:500;line-height:1.3">${f.name.replace('⚠️ ','')}</div><div style="font-size:10px;color:var(--m)">${f.cat}</div></td><td style="font-family:'DM Mono',monospace;font-size:12px">$${bc.toFixed(2)}</td><td style="font-size:11px;color:var(--m)">${bs}</td><td><div style="display:flex;align-items:center;gap:4px"><span style="font-size:12px;color:var(--m)">$</span><input type="number" min="0" step="0.01" style="width:75px;padding:4px 6px;border:.5px solid var(--b);border-radius:6px;font-size:12px;font-family:'DM Mono',monospace;background:${!pp2?'#fffbea':'var(--s)'}" value="${pp2||''}" placeholder="0.00" onchange="setPP('${key}',parseFloat(this.value)||0)"></div></td><td style="font-family:'DM Mono',monospace;font-size:12px;color:${pp2&&parseFloat(profit)>0?'var(--sc)':pp2?'var(--dn)':'var(--m)'}">${pp2?'$'+profit:'—'}</td><td style="font-size:13px;font-weight:600;color:${mc}">${mp?me+' '+mp+'%':'<span style="color:var(--m);font-weight:400;font-size:11px">Not set</span>'}</td><td>${f.flags.filter(x=>x!=='inoffice').map(fe).join('')}</td></tr>`;}).join('');}
function renderPT(){const t=document.getElementById('pt');if(t)t.innerHTML=bPR();}
function setPP(name,val){PP[name]=val;sPP();renderPT();}

const PTLS=[
  {id:'centercity',name:'Center City Pharmacy',icon:'🏙️',bg:'var(--ccb)',type:'LifeFile Portal — 503a+',url:'https://host3.lifefile.net:40443/centercitypharmacy/doctor',username:'PrimeHRTAdmin',password:'Ashlou02!',notes:'Temp password — change after first login.',status:'active'},
  {id:'hallandale',name:'Hallandale Pharmacy',icon:'💊',bg:'var(--hlb)',type:'LifeFile Portal — 503a',url:'https://host6d.lifefile.net:40443/application_main_zfw/login/login/vendor_name/hallandalerx/access/doctor',username:'EWillis',password:'Ashlou02!',notes:'Temp password — change after first login.',status:'active'},
  {id:'brooksville',name:'Brooksville Pharmacy',icon:'🌿',bg:'var(--bkb)',type:'LifeFile Portal',url:'https://host1.lifefile.net:40443/brooksvillerx/doctor',notes:'Individual provider accounts only.',status:'active',users:[{name:'Ashlee Montalvo',username:'Amontalvo',password:'ASHlou02!!'},{name:'Tamara Dismukes',username:'tamara@primehrt.clinic',password:'Monstertruck41!'}]},
  {id:'strive',name:'Strive Pharmacy',icon:'⚡',bg:'var(--stb)',type:'LifeFile Portal',url:'https://host5d.lifefile.net/application_main_zfw/login/login/vendor_name/strivepharmacy/access/doctor',notes:'Individual provider accounts.',status:'active',users:[{name:'Ashlee Montalvo',username:'a.montalvo',password:'ASHlou02!!'}]},
  {id:'southlake',name:'Southlake Pharmacy',icon:'🔬',bg:'#faf5e0',type:'ScriptScan Portal — 503a',url:'https://scriptscan.info/slpharmacy/doctor',notes:'ScriptScan — not LifeFile.',status:'active',users:[{name:'Ashlee Montalvo',username:'ashlee@primehrt.clinic',password:'ASHlou02!!'}]},
  {id:'olympia',name:'Olympia Pharmacy',icon:'⚗️',bg:'var(--olb)',type:'Direct Portal (not LifeFile)',url:'https://olympiapharmacy.drscriptportal.com',notes:'Not LifeFile. Two invoice streams: Olympia + Wesley Pharmaceuticals.',status:'active',users:[{name:'Ashlee Montalvo',username:'Prime35754',password:'Prime35754'},{name:'Tamara Dismukes',username:'TD35754',password:'Seltz8544!'}]},
  {id:'betterlife',name:'BetterLife Pharmacy',icon:'🌱',bg:'#e8f7ee',type:'LifeFile Portal',url:'https://host100.lifefile.net/betterlifepharmacy/doctor',notes:'Added 7/6/26 — new pharmacy, details TBD.',status:'active',users:[{name:'Ashlee Montalvo',username:'amontalvo',password:'PRImeHRT2025!!'}]},
  {id:'alphabio',name:'Alpha Bio Labs',icon:'🧬',bg:'var(--abb)',type:'Website — Partner Login',url:'https://alphabiomedlabs.com/account/login',username:'ashlee@primehrt.clinic',password:'PZp25C!#sNncsXe',notes:'Consent required before every order. Drop-ships to patients.',status:'active'},
];
let PR2={};
function rPor(){if(!cS('portals'))return`<div class="emp">Access restricted.</div>`;return`<div style="max-width:720px"><div class="sh"><h2>Pharmacy Portals</h2><span style="font-size:11px;color:var(--m)">Admin & Staff · ${PTLS.length} active</span></div><div class="al in" style="margin-bottom:16px">🔐 Credentials visible to admins and staff only.</div>${PTLS.map(p=>pCard(p)).join('')}</div>`;}
function pCard(p){const uf=`<div class="prfi"><span class="prfl">URL</span><span class="prfv" style="font-size:11px;color:var(--m)">${p.url||'—'}</span>${p.url?`<button class="btn sm" onclick="cpTxt('${p.url}','URL copied')">⎘</button>`:''}</div>`;
if(p.users){const rows=p.users.map((u,i)=>{const rk=p.id+'_'+i,rv=PR2[rk];return`<div style="padding:8px 0;border-bottom:.5px solid var(--b);margin-bottom:4px"><div style="font-size:11px;font-weight:600;color:var(--t);margin-bottom:6px">${u.name}</div><div class="prf" style="margin-bottom:6px"><div class="prfi"><span class="prfl">Username</span><span class="prfv">${u.username}</span><button class="btn sm" onclick="cpTxt('${u.username}','Username copied')">⎘</button></div><div class="prfi"><span class="prfl">Password</span><span class="prfv ${rv?'':'msk'}">${rv?u.password:'••••••••'}</span><button class="btn sm" onclick="tR('${rk}')">${rv?'Hide':'Reveal'}</button><button class="btn sm" onclick="cpTxt('${u.password}','Password copied')">⎘</button></div></div></div>`;}).join('');return`<div class="prc"><div class="pri" style="background:${p.bg}">${p.icon}</div><div class="prb"><div class="prn">${p.name}</div><div class="prt">${p.type}</div>${p.notes?`<div style="font-size:11px;color:var(--wn);margin-bottom:10px">⚠ ${p.notes}</div>`:''}<div class="prf">${uf}</div><div style="margin-top:8px">${rows}</div><div class="pra" style="margin-top:10px">${p.url?`<button class="btn p" onclick="window.open('${p.url}','_blank')">Open Portal →</button>`:''}</div></div></div>`;}
const rv=PR2[p.id];return`<div class="prc"><div class="pri" style="background:${p.bg}">${p.icon}</div><div class="prb"><div class="prn">${p.name}</div><div class="prt">${p.type}</div><div class="prf">${uf}<div class="prfi"><span class="prfl">Username</span><span class="prfv">${p.username||'—'}</span>${p.username?`<button class="btn sm" onclick="cpTxt('${p.username}','Username copied')">⎘</button>`:''}</div><div class="prfi"><span class="prfl">Password</span><span class="prfv ${rv?'':'msk'}">${rv?p.password:'••••••••'}</span>${p.password?`<button class="btn sm" onclick="tR('${p.id}')">${rv?'Hide':'Reveal'}</button><button class="btn sm" onclick="cpTxt('${p.password}','Password copied')">⎘</button>`:''}</div></div>${p.notes?`<div style="font-size:11px;color:var(--wn);margin-bottom:10px">⚠ ${p.notes}</div>`:''}<div class="pra">${p.url?`<button class="btn p" onclick="window.open('${p.url}','_blank')">Open Portal →</button>`:''}<button class="btn sm" onclick="cpTxt('${p.username}','Username copied')">Copy username</button><button class="btn sm" onclick="cpTxt('${p.password}','Password copied')">Copy password</button></div></div></div>`;}
function tR(pid){PR2[pid]=!PR2[pid];render();}
function cpTxt(text,msg){if(!text)return;navigator.clipboard.writeText(text).then(()=>toast('✓ '+(msg||'Copied'))).catch(()=>alert(text));}

function rSet(){return`<div style="max-width:560px"><div class="sh"><h2>User login management</h2></div><div class="al in" style="margin-bottom:16px">Each user logs in with their clinic email. On first login they set their own password.</div>${USERS.map(u=>`<div class="phc" style="margin-bottom:8px"><div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:6px"><div><div style="font-weight:600;font-size:13px">${u.name}</div><div style="font-size:11px;color:var(--m)">${{admin:'Admin',provider:'Provider',coordinator:'Coordinator',staff:'Staff'}[u.role]||u.role}${u.canPreview?' · Can preview all roles':''}</div></div><div style="display:flex;gap:6px;align-items:center"><span style="font-size:11px;color:${u.password?'var(--sc)':'var(--wn)'}">${u.password?'✓ Set':'⏳ Not set'}</span>${u.password?`<button class="btn sm dn" onclick="rPW('${u.id}')">Reset</button>`:''}</div></div><div style="display:flex;align-items:center;gap:8px;font-size:11px;color:var(--m)"><span>📧</span><span style="font-family:'DM Mono',monospace;font-size:11px">${u.email||'—'}</span>${u.email?`<button class="btn sm" onclick="cpTxt('${u.email}','Email copied')" style="padding:2px 7px;font-size:10px">⎘</button>`:''}</div></div>`).join('')}</div>`;}
function rPW(uid){if(!confirm('Reset this password?'))return;const u=USERS.find(x=>x.id===uid);if(u){u.password='';saveUsers();render();}}

function rAI(){
  const orders=ST.orders.slice(0,20);
  const p=orders.filter(o=>['Awaiting Payment Verification','Payment Confirmed — Ready to Place'].includes(o.status));
  const a=orders.filter(o=>['Ordered','Processing','Shipped'].includes(o.status));
  const h=orders.filter(o=>['On Hold','Returned to Provider'].includes(o.status));
  return`<div style="max-width:860px"><div style="margin-bottom:16px"><h2 style="font-size:16px;font-weight:600;color:#fff;margin-bottom:4px">🤖 CompoundTrack AI Assistant</h2><p style="font-size:12px;color:var(--m)">Opens Claude.ai pre-loaded with your formulary, routing rules, and current orders.</p></div>
  <div style="background:var(--s);border:.5px solid var(--b);border-radius:12px;padding:20px;margin-bottom:16px"><div style="font-size:13px;font-weight:600;margin-bottom:4px">How to use</div><div style="font-size:12px;color:var(--m);margin-bottom:16px;line-height:1.6">1. Click <strong>Copy context prompt</strong><br>2. Click <strong>Open Claude.ai</strong><br>3. Paste context then ask your question</div>
  <div style="display:flex;gap:10px;flex-wrap:wrap;margin-bottom:16px"><a href="https://claude.ai/new" target="_blank" class="aib">🤖 Open Claude.ai →</a><button class="acb" onclick="cAIC()">📋 Copy context prompt</button></div>
  <div style="font-size:11px;font-weight:600;text-transform:uppercase;letter-spacing:.4px;color:var(--m);margin-bottom:6px">Current snapshot</div>
  <div class="acp">Pending (${p.length}): ${p.map(o=>o.patientName+' | '+o.medication).join(', ')||'None'}\nActive (${a.length}): ${a.map(o=>o.patientName+' | '+o.medication).join(', ')||'None'}\nHold (${h.length}): ${h.map(o=>o.patientName+' | '+o.status).join(', ')||'None'}</div></div>
  <div style="background:var(--s);border:.5px solid var(--b);border-radius:12px;padding:16px 20px"><div style="font-size:12px;font-weight:600;margin-bottom:10px">Quick prompts</div><div style="display:flex;flex-wrap:wrap;gap:6px">${['Tirzepatide routing for >10mg/week?','Cheapest progesterone pharmacy?','How to place a controlled substance order?','How to order BPC-157 from Alpha Bio?','Female testosterone routing rule?','Which orders are on hold?','Tadalafil — compound or GoodRx?'].map(q=>`<button onclick="cAIP('${q.replace(/'/g,"\\'")}',this)" style="padding:6px 12px;border:.5px solid var(--b);border-radius:20px;font-size:11px;cursor:pointer;background:var(--bg);color:var(--m);font-family:'DM Sans',sans-serif">${q}</button>`).join('')}</div></div></div>`;
}
function cAIC(){
  const orders=ST.orders.slice(0,20),p=orders.filter(o=>['Awaiting Payment Verification','Payment Confirmed — Ready to Place'].includes(o.status)),a=orders.filter(o=>['Ordered','Processing','Shipped'].includes(o.status)),h=orders.filter(o=>['On Hold','Returned to Provider'].includes(o.status));
  const text=`You are CompoundTrack AI for Prime HRT & Weight Loss (Clearwater FL). Be direct and specific.\n\n== KEY ROUTING RULES ==\n- Female testosterone → Hallandale 50mg/mL 2mL grapeseed ($12). Wet sig + fax. E-FORCSE.\n- Male testosterone standard → Center City 200mg/mL mfg ($40). Wet sig + fax. E-FORCSE.\n- Male testosterone high-dose >200mg/wk → Brooksville 250mg/mL ($28/10-pack).\n- Tirzepatide ≤10mg/wk → Center City 10mg/mL (30mg $150 / 60mg $265).\n- Tirzepatide >10mg/wk → Hallandale FORTE 15mg/mL ($283). Single poke. REQUIRED.\n- Semaglutide → Center City. LifeFile.\n- Research peptides → Alpha Bio. CONSENT FORM required before ordering.\n- Tadalafil → GoodRx first. Compound only if needed.\n- Controlled substances → print Rx, WET SIGNATURE, fax BEFORE LifeFile.\n- Enclomiphene → Hallandale ($1.00-1.50/ea). Avoid Strive.\n- Sermorelin → Southlake 30mg ($150, $5/mg, 2wk turnaround).\n- LDN → Strive ($72/90ct). Progesterone → Brooksville ($0.60/cap).\n\n== CURRENT ORDERS ==\nPending (${p.length}): ${p.map(o=>o.patientName+' | '+o.medication+(o.onSubscription?' [SUB]':'')).join(', ')||'None'}\nActive (${a.length}): ${a.map(o=>o.patientName+' | '+o.medication+' | '+(o.trackingNumber||'no tracking')).join(', ')||'None'}\nOn hold (${h.length}): ${h.map(o=>o.patientName+' | '+o.medication+' | '+o.status).join(', ')||'None'}\n\nNow answer my question:`;
  navigator.clipboard.writeText(text).then(()=>toast('✓ Context copied — paste into Claude.ai')).catch(()=>alert('Copy failed.'));
}
function cAIP(q,btn){cAIC();setTimeout(()=>window.open('https://claude.ai/new','_blank'),300);if(btn){btn.style.background='var(--scb)';btn.style.color='var(--sc)';setTimeout(()=>{btn.style.background='';btn.style.color='';},2000);}}

function rIP(pharmName){if(!pharmName)return '';const portal=PTLS.find(p=>pharmName.toLowerCase().includes(p.id)||p.name.toLowerCase().includes(pharmName.toLowerCase().split(' ')[0]));if(!portal)return `<div style="font-size:11px;color:var(--m);margin-top:6px">No portal on file — check Portals tab.</div>`;const rk='il_'+portal.id;if(portal.users){const rows=portal.users.map((u,i)=>{const k=rk+'_'+i,rv=PR2[k];return`<div style="padding:7px 0;border-bottom:.5px solid var(--b)"><div style="font-size:11px;font-weight:600;margin-bottom:4px">${u.name}</div><div style="display:flex;flex-direction:column;gap:3px"><div style="display:flex;align-items:center;gap:6px;font-size:11px"><span style="color:var(--m);width:70px;flex-shrink:0">Username</span><span style="font-family:'DM Mono',monospace">${u.username}</span><button class="btn sm" onclick="cpTxt('${u.username}','Username copied')" style="padding:2px 7px;font-size:10px">⎘</button></div><div style="display:flex;align-items:center;gap:6px;font-size:11px"><span style="color:var(--m);width:70px;flex-shrink:0">Password</span><span style="font-family:'DM Mono',monospace">${rv?u.password:'••••••••'}</span><button class="btn sm" onclick="PR2['${k}']=!PR2['${k}'];render()" style="padding:2px 7px;font-size:10px">${rv?'Hide':'Show'}</button><button class="btn sm" onclick="cpTxt('${u.password}','Password copied')" style="padding:2px 7px;font-size:10px">⎘</button></div></div></div>`;}).join('');return`<div style="margin-top:8px;padding:10px 12px;background:var(--inb);border:.5px solid #c5d8f5;border-radius:8px"><div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:8px"><div style="font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:.4px;color:var(--in)">🔐 ${portal.name}</div>${portal.url?`<button class="btn sm p" onclick="window.open('${portal.url}','_blank')" style="font-size:10px;padding:3px 9px">Open →</button>`:''}</div>${rows}</div>`;}
const rv=PR2[rk];return`<div style="margin-top:8px;padding:10px 12px;background:var(--inb);border:.5px solid #c5d8f5;border-radius:8px"><div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:8px"><div style="font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:.4px;color:var(--in)">🔐 ${portal.name}</div>${portal.url?`<button class="btn sm p" onclick="window.open('${portal.url}','_blank')" style="font-size:10px;padding:3px 9px">Open →</button>`:''}</div><div style="display:flex;flex-direction:column;gap:5px"><div style="display:flex;align-items:center;gap:6px;font-size:11px"><span style="color:var(--m);width:70px;flex-shrink:0">Username</span><span style="font-family:'DM Mono',monospace">${portal.username||'—'}</span>${portal.username?`<button class="btn sm" onclick="cpTxt('${portal.username}','Username copied')" style="padding:2px 7px;font-size:10px">⎘</button>`:''}</div><div style="display:flex;align-items:center;gap:6px;font-size:11px"><span style="color:var(--m);width:70px;flex-shrink:0">Password</span><span style="font-family:'DM Mono',monospace">${rv?portal.password:'••••••••'}</span><button class="btn sm" onclick="PR2['${rk}']=!PR2['${rk}'];render()" style="padding:2px 7px;font-size:10px">${rv?'Hide':'Show'}</button>${portal.password?`<button class="btn sm" onclick="cpTxt('${portal.password}','Password copied')" style="padding:2px 7px;font-size:10px">⎘</button>`:''}</div></div></div>`;}

async function boot(){
  try{await initFirebase();}
  catch(e){const lm=document.getElementById('lm');if(lm)lm.innerHTML='<div style="padding:40px;font-family:sans-serif;color:#a82222;background:#fceaea;border-radius:12px;margin:40px auto;max-width:600px"><strong>Could not load the database connection</strong><br><br>The app tried three sources (Google, jsDelivr, Cloudflare) and all were blocked or unreachable.<br><br><strong>Try:</strong> a hard refresh (Ctrl+Shift+R / Cmd+Shift+R). If it still fails on this network, the network or GHL may be blocking outside scripts — try a different network or contact Eric.<br><br><span style="font-size:11px;color:#7a2222">Technical detail: '+e.message+'</span></div>';return;}
  await loadUsers();await loadPS();await load();renderApp();
}
boot();

window.toggleSentStatus=function(id){const o=ST.orders.find(x=>x.id===id);if(o){o.status=(o.status==='Ordered')?'Processing':'Ordered';sO();render();}};
window.editPatientInfo=function(id){const o=ST.orders.find(x=>x.id===id);if(!o)return;const n=prompt('Edit Patient Name:',o.patientName);if(n===null)return;const d=prompt('Edit DOB (MM/DD/YYYY):',o.patientDOB||'');if(d===null)return;o.patientName=n.trim();o.patientDOB=d.trim();sO();render();};
</script></body></html>
