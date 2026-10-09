"use client"
import { useEffect, useState } from "react"

export default function Home() {
  const [logged, setLogged] = useState(false)
  const APP_ID = "34yECzDw0yVKnawr421rn"
  const LOGIN = `https://oauth.deriv.com/oauth2/authorize?app_id=${APP_ID}`

  useEffect(()=>{
    const p = new URLSearchParams(window.location.search)
    const t = p.get("token") || p.get("token1")
    if(t){ localStorage.setItem("tok", t); setLogged(true); history.replaceState({},"","/")}
    else if(localStorage.getItem("tok")) setLogged(true)
  },[])

  if(logged){
    return (
      <div style={{background:"#080e1f", minHeight:"100vh", color:"white", padding:20}}>
        <div style={{display:"flex", justifyContent:"space-between"}}>
          <b><span style={{color:"#4ade80"}}>dollar</span><span style={{color:"#ef4444"}}>crypto</span></b>
          <span style={{background:"#111a33", padding:"6px 12px", borderRadius:20, fontSize:12}}>Balance: $10,000 Virtual</span>
        </div>
        <div style={{display:"grid", gridTemplateColumns:"1fr 1fr", gap:12, marginTop:24}}>
          <div style={{background:"#22c55e", color:"black", padding:24, borderRadius:16, fontWeight:"bold", textAlign:"center"}}>🤖 Start Bot</div>
          <div style={{background:"#111a33", padding:24, borderRadius:16, textAlign:"center"}}>📊 Copy Trade</div>
          <div style={{background:"#111a33", padding:24, borderRadius:16, textAlign:"center"}}>📈 Manual</div>
          <div style={{background:"#111a33", padding:24, borderRadius:16, textAlign:"center"}}>💰 Withdraw</div>
        </div>
        <button onClick={()=>{localStorage.clear(); setLogged(false)}} style={{marginTop:30, color:"#ef4444"}}>Logout</button>
      </div>
    )
  }

  return (
    <div style={{background:"#080e1f", minHeight:"100vh", color:"white", textAlign:"center", padding:"20px 20px 0"}}>
      <div style={{display:"flex", justifyContent:"space-between", alignItems:"center"}}>
        <b style={{fontSize:20}}><span style={{color:"#4ade80"}}>dollar</span><span style={{color:"#ef4444"}}>crypto</span></b>
        <a href={LOGIN} style={{background:"white", color:"black", padding:"8px 16px", borderRadius:20, textDecoration:"none", fontSize:13, fontWeight:700}}>Login Now →</a>
      </div>
      <div style={{marginTop:16, border:"1px solid #22c55e33", display:"inline-block", padding:"6px 12px", borderRadius:20, fontSize:12, color:"#4ade80"}}>✓ Trusted by 50,000+ Traders</div>
      <h1 style={{fontSize:38, fontWeight:900, marginTop:20, lineHeight:1}}>Welcome to<br/><span style={{color:"#4ade80"}}>Dollar</span> <span style={{color:"#ef4444"}}>crypto</span></h1>
      <p style={{color:"#94a3b8", fontSize:13, marginTop:12}}>Your all-in-one workspace for automated trading, smart bots, and real-time market insights.</p>
      <a href={LOGIN} style={{display:"block", background:"#22c55e", color:"black", padding:"16px", borderRadius:12, fontWeight:800, textDecoration:"none", marginTop:24}}>Start Trading Now</a>
      <a href={LOGIN} style={{display:"block", border:"1px solid #334155", padding:"14px", borderRadius:12, color:"white", textDecoration:"none", marginTop:12}}>Sign up</a>
    </div>
  )
}
