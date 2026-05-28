import { useState, useEffect, useRef } from "react";

const initialInventory = [
  { id: 1, name: "Paracetamol 500mg", category: "Tablet", stock: 200, price: 2.5, supplier: "Sun Pharma", supplierPhone: "9876543210", minStock: 50, expiry: "2026-12-31" },
  { id: 2, name: "Amoxicillin 250mg", category: "Capsule", stock: 30, price: 8.0, supplier: "Cipla", supplierPhone: "9123456789", minStock: 40, expiry: "2026-08-15" },
  { id: 3, name: "Omeprazole 20mg", category: "Capsule", stock: 5, price: 5.5, supplier: "Dr. Reddy's", supplierPhone: "9988776655", minStock: 30, expiry: "2027-01-20" },
  { id: 4, name: "Cetirizine 10mg", category: "Tablet", stock: 150, price: 3.0, supplier: "Mankind Pharma", supplierPhone: "9871234567", minStock: 40, expiry: "2026-11-10" },
  { id: 5, name: "Metformin 500mg", category: "Tablet", stock: 0, price: 4.0, supplier: "Sun Pharma", supplierPhone: "9876543210", minStock: 50, expiry: "2027-03-05" },
  { id: 6, name: "Azithromycin 500mg", category: "Tablet", stock: 60, price: 15.0, supplier: "Cipla", supplierPhone: "9123456789", minStock: 20, expiry: "2026-09-30" },
  { id: 7, name: "Atorvastatin 10mg", category: "Tablet", stock: 90, price: 7.0, supplier: "Lupin", supplierPhone: "9765432100", minStock: 30, expiry: "2027-02-28" },
  { id: 8, name: "Pantoprazole 40mg", category: "Tablet", stock: 12, price: 6.5, supplier: "Zydus Cadila", supplierPhone: "9654321098", minStock: 25, expiry: "2026-10-15" },
];

const TABS = ["Dashboard", "Inventory", "Billing", "Orders", "Low Stock Alert"];

export default function App() {
  const [inventory, setInventory] = useState(initialInventory);
  const [activeTab, setActiveTab] = useState("Dashboard");
  const [searchTerm, setSearchTerm] = useState("");
  const [cart, setCart] = useState([]);
  const [bills, setBills] = useState([]);
  const [patientName, setPatientName] = useState("");
  const [patientPhone, setPatientPhone] = useState("");
  const [orders, setOrders] = useState([]);
  const [orderQty, setOrderQty] = useState({});
  const [showBillPreview, setShowBillPreview] = useState(null);
  const [showAddModal, setShowAddModal] = useState(false);
  const [newMed, setNewMed] = useState({ name: "", category: "Tablet", stock: "", price: "", supplier: "", supplierPhone: "", minStock: "", expiry: "" });
  const [editId, setEditId] = useState(null);
  const [notification, setNotification] = useState(null);
  const billRef = useRef(null);

  const lowStockItems = inventory.filter(i => i.stock <= i.minStock);
  const outOfStock = inventory.filter(i => i.stock === 0);

  const showNotif = (msg, type = "success") => {
    setNotification({ msg, type });
    setTimeout(() => setNotification(null), 3000);
  };

  const filteredInventory = inventory.filter(i =>
    i.name.toLowerCase().includes(searchTerm.toLowerCase()) ||
    i.category.toLowerCase().includes(searchTerm.toLowerCase())
  );

  const addToCart = (item) => {
    if (item.stock === 0) { showNotif("Yeh dawai stock mein nahi hai!", "error"); return; }
    const existing = cart.find(c => c.id === item.id);
    if (existing) {
      if (existing.qty >= item.stock) { showNotif("Itni quantity stock mein nahi hai!", "error"); return; }
      setCart(cart.map(c => c.id === item.id ? { ...c, qty: c.qty + 1 } : c));
    } else {
      setCart([...cart, { ...item, qty: 1 }]);
    }
  };

  const removeFromCart = (id) => setCart(cart.filter(c => c.id !== id));
  const updateCartQty = (id, qty) => {
    const item = inventory.find(i => i.id === id);
    if (qty > item.stock) { showNotif("Stock mein itni quantity nahi!", "error"); return; }
    if (qty <= 0) { removeFromCart(id); return; }
    setCart(cart.map(c => c.id === id ? { ...c, qty } : c));
  };

  const totalAmount = cart.reduce((s, c) => s + c.price * c.qty, 0);
  const gst = totalAmount * 0.05;
  const grandTotal = totalAmount + gst;

  const generateBill = () => {
    if (!patientName) { showNotif("Patient ka naam daalna zaroori hai!", "error"); return; }
    if (cart.length === 0) { showNotif("Cart mein koi item nahi!", "error"); return; }
    const bill = {
      id: `BILL-${Date.now()}`,
      date: new Date().toLocaleString("hi-IN"),
      patient: patientName,
      phone: patientPhone,
      items: [...cart],
      subtotal: totalAmount,
      gst,
      total: grandTotal,
    };
    setBills([bill, ...bills]);
    setInventory(inventory.map(i => {
      const cartItem = cart.find(c => c.id === i.id);
      return cartItem ? { ...i, stock: i.stock - cartItem.qty } : i;
    }));
    setCart([]);
    setPatientName("");
    setPatientPhone("");
    setShowBillPreview(bill);
    showNotif("Bill successfully generate ho gaya!");
  };

  const placeOrder = () => {
    const orderItems = lowStockItems.filter(i => orderQty[i.id] && orderQty[i.id] > 0);
    if (orderItems.length === 0) { showNotif("Koi item select nahi kiya order ke liye!", "error"); return; }
    const order = {
      id: `ORD-${Date.now()}`,
      date: new Date().toLocaleString("hi-IN"),
      status: "Placed",
      items: orderItems.map(i => ({ ...i, orderQty: orderQty[i.id] })),
    };
    setOrders([order, ...orders]);
    setOrderQty({});
    showNotif(`Order ${order.id} successfully place ho gaya!`);
  };

  const exportExcel = () => {
    const headers = ["ID", "Dawai Ka Naam", "Category", "Stock", "Price (₹)", "Supplier", "Phone", "Min Stock", "Expiry Date", "Status"];
    const rows = inventory.map(i => [
      i.id, i.name, i.category, i.stock, i.price, i.supplier, i.supplierPhone, i.minStock, i.expiry,
      i.stock === 0 ? "OUT OF STOCK" : i.stock <= i.minStock ? "LOW STOCK" : "OK"
    ]);
    let csv = headers.join(",") + "\n";
    rows.forEach(r => { csv += r.join(",") + "\n"; });
    const blob = new Blob([csv], { type: "text/csv;charset=utf-8;" });
    const url = URL.createObjectURL(blob);
    const a = document.createElement("a"); a.href = url; a.download = "Medical_Inventory.csv"; a.click();
    showNotif("Excel sheet download ho rahi hai!");
  };

  const saveEdit = () => {
    if (!newMed.name || !newMed.price || !newMed.stock) { showNotif("Saari zaruri fields bharo!", "error"); return; }
    if (editId) {
      setInventory(inventory.map(i => i.id === editId ? { ...i, ...newMed, price: +newMed.price, stock: +newMed.stock, minStock: +newMed.minStock } : i));
      showNotif("Dawai update ho gayi!");
    } else {
      setInventory([...inventory, { ...newMed, id: Date.now(), price: +newMed.price, stock: +newMed.stock, minStock: +newMed.minStock }]);
      showNotif("Nayi dawai add ho gayi!");
    }
    setShowAddModal(false);
    setNewMed({ name: "", category: "Tablet", stock: "", price: "", supplier: "", supplierPhone: "", minStock: "", expiry: "" });
    setEditId(null);
  };

  const openEdit = (item) => {
    setEditId(item.id); setNewMed({ ...item }); setShowAddModal(true);
  };

  const printBill = () => window.print();

  return (
    <div style={{ fontFamily: "'Noto Sans', sans-serif", minHeight: "100vh", background: "#0f1117", color: "#e8eaf6" }}>
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Noto+Sans:wght@400;600;700&family=Baloo+2:wght@700;800&display=swap');
        * { box-sizing: border-box; margin: 0; padding: 0; }
        ::-webkit-scrollbar { width: 6px; } ::-webkit-scrollbar-track { background: #1a1d2e; } ::-webkit-scrollbar-thumb { background: #3d5afe; border-radius: 3px; }
        input, select, textarea { outline: none; }
        @media print { .no-print { display: none !important; } .print-area { display: block !important; } }
        .tab-btn { transition: all 0.2s; }
        .tab-btn:hover { background: rgba(61,90,254,0.15) !important; }
        .card { background: #1a1d2e; border-radius: 16px; border: 1px solid rgba(255,255,255,0.07); }
        .btn-primary { background: linear-gradient(135deg, #3d5afe, #00bcd4); color: white; border: none; border-radius: 10px; padding: 10px 20px; cursor: pointer; font-weight: 700; font-size: 14px; transition: all 0.2s; }
        .btn-primary:hover { transform: translateY(-1px); box-shadow: 0 4px 20px rgba(61,90,254,0.4); }
        .btn-danger { background: linear-gradient(135deg, #ff5252, #ff1744); color: white; border: none; border-radius: 8px; padding: 6px 14px; cursor: pointer; font-weight: 600; font-size: 13px; }
        .btn-secondary { background: rgba(255,255,255,0.08); color: #e8eaf6; border: 1px solid rgba(255,255,255,0.15); border-radius: 8px; padding: 8px 16px; cursor: pointer; font-weight: 600; font-size: 13px; transition: all 0.2s; }
        .btn-secondary:hover { background: rgba(255,255,255,0.14); }
        .inp { background: #252838; border: 1.5px solid rgba(255,255,255,0.1); border-radius: 10px; padding: 10px 14px; color: #e8eaf6; font-size: 14px; width: 100%; }
        .inp:focus { border-color: #3d5afe; }
        .badge-ok { background: rgba(0,230,118,0.15); color: #00e676; border-radius: 6px; padding: 3px 10px; font-size: 12px; font-weight: 700; }
        .badge-low { background: rgba(255,193,7,0.15); color: #ffc107; border-radius: 6px; padding: 3px 10px; font-size: 12px; font-weight: 700; }
        .badge-out { background: rgba(255,82,82,0.15); color: #ff5252; border-radius: 6px; padding: 3px 10px; font-size: 12px; font-weight: 700; }
        .modal-overlay { position: fixed; inset: 0; background: rgba(0,0,0,0.75); z-index: 1000; display: flex; align-items: center; justify-content: center; }
        .notif { position: fixed; top: 20px; right: 20px; z-index: 2000; padding: 14px 22px; border-radius: 12px; font-weight: 700; font-size: 14px; animation: slideIn 0.3s ease; }
        @keyframes slideIn { from { transform: translateX(100%); opacity: 0; } to { transform: translateX(0); opacity: 1; } }
        .stat-card { background: linear-gradient(135deg, var(--c1), var(--c2)); border-radius: 16px; padding: 20px; }
        table { border-collapse: collapse; width: 100%; }
        th { background: rgba(61,90,254,0.15); color: #90caf9; font-size: 12px; text-transform: uppercase; letter-spacing: 0.5px; padding: 12px 14px; text-align: left; }
        td { padding: 11px 14px; border-bottom: 1px solid rgba(255,255,255,0.05); font-size: 14px; }
        tr:hover td { background: rgba(61,90,254,0.07); }
      `}</style>

      {/* Notification */}
      {notification && (
        <div className="notif" style={{ background: notification.type === "error" ? "#b71c1c" : "#1b5e20" }}>
          {notification.type === "error" ? "⚠️" : "✅"} {notification.msg}
        </div>
      )}

      {/* Header */}
      <div className="no-print" style={{ background: "linear-gradient(90deg, #1a1d2e, #0f1117)", borderBottom: "1px solid rgba(255,255,255,0.08)", padding: "0 24px", display: "flex", alignItems: "center", justifyContent: "space-between", height: 64 }}>
        <div style={{ display: "flex", alignItems: "center", gap: 12 }}>
          <div style={{ width: 38, height: 38, background: "linear-gradient(135deg,#3d5afe,#00bcd4)", borderRadius: 10, display: "flex", alignItems: "center", justifyContent: "center", fontSize: 20 }}>💊</div>
          <div>
            <div style={{ fontFamily: "'Baloo 2'", fontWeight: 800, fontSize: 18, color: "#fff", lineHeight: 1.2 }}>MedStore Pro</div>
            <div style={{ fontSize: 11, color: "#90a4ae" }}>Inventory Management System</div>
          </div>
        </div>
        <div style={{ display: "flex", gap: 4 }}>
          {lowStockItems.length > 0 && (
            <div onClick={() => setActiveTab("Low Stock Alert")} style={{ cursor: "pointer", background: "rgba(255,82,82,0.15)", border: "1px solid rgba(255,82,82,0.3)", borderRadius: 20, padding: "6px 14px", fontSize: 12, color: "#ff5252", fontWeight: 700 }}>
              🔴 {lowStockItems.length} Low Stock
            </div>
          )}
          {outOfStock.length > 0 && (
            <div onClick={() => setActiveTab("Low Stock Alert")} style={{ cursor: "pointer", background: "rgba(255,193,7,0.15)", border: "1px solid rgba(255,193,7,0.3)", borderRadius: 20, padding: "6px 14px", fontSize: 12, color: "#ffc107", fontWeight: 700 }}>
              ⚠️ {outOfStock.length} Out of Stock
            </div>
          )}
        </div>
      </div>

      {/* Tabs */}
      <div className="no-print" style={{ display: "flex", gap: 4, padding: "12px 24px", background: "#0f1117", borderBottom: "1px solid rgba(255,255,255,0.06)" }}>
        {TABS.map(t => (
          <button key={t} className="tab-btn" onClick={() => setActiveTab(t)} style={{
            background: activeTab === t ? "linear-gradient(135deg,#3d5afe,#00bcd4)" : "transparent",
            color: activeTab === t ? "#fff" : "#90a4ae", border: "none", borderRadius: 10, padding: "8px 18px",
            fontWeight: 700, fontSize: 13, cursor: "pointer",
            boxShadow: activeTab === t ? "0 4px 15px rgba(61,90,254,0.3)" : "none",
          }}>
            {t === "Low Stock Alert" && lowStockItems.length > 0 ? `⚠️ ${t}` : t}
          </button>
        ))}
      </div>

      <div className="no-print" style={{ padding: "24px", maxWidth: 1400, margin: "0 auto" }}>

        {/* DASHBOARD */}
        {activeTab === "Dashboard" && (
          <div>
            <div style={{ fontSize: 22, fontFamily: "'Baloo 2'", fontWeight: 800, marginBottom: 20 }}>📊 Dashboard</div>
            <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fit, minmax(200px, 1fr))", gap: 16, marginBottom: 24 }}>
              {[
                { label: "Kul Dawaiyan", val: inventory.length, icon: "💊", c1: "#1a237e", c2: "#283593" },
                { label: "Total Stock Value", val: `₹${inventory.reduce((s,i)=>s+i.stock*i.price,0).toFixed(0)}`, icon: "💰", c1: "#1b5e20", c2: "#2e7d32" },
                { label: "Low Stock Items", val: lowStockItems.length, icon: "⚠️", c1: "#e65100", c2: "#f57c00" },
                { label: "Out of Stock", val: outOfStock.length, icon: "🚫", c1: "#b71c1c", c2: "#c62828" },
                { label: "Aaj Ke Bills", val: bills.length, icon: "🧾", c1: "#4a148c", c2: "#6a1b9a" },
                { label: "Placed Orders", val: orders.length, icon: "📦", c1: "#006064", c2: "#00838f" },
              ].map(s => (
                <div key={s.label} className="stat-card" style={{ "--c1": s.c1, "--c2": s.c2 }}>
                  <div style={{ fontSize: 28 }}>{s.icon}</div>
                  <div style={{ fontSize: 26, fontWeight: 800, fontFamily: "'Baloo 2'", marginTop: 6 }}>{s.val}</div>
                  <div style={{ fontSize: 12, opacity: 0.85, marginTop: 2 }}>{s.label}</div>
                </div>
              ))}
            </div>
            {lowStockItems.length > 0 && (
              <div className="card" style={{ padding: 20, borderLeft: "4px solid #ff5252" }}>
                <div style={{ fontWeight: 700, color: "#ff5252", marginBottom: 12 }}>🔴 Urgent — Inhe abhi order karo!</div>
                <table>
                  <thead><tr><th>Dawai</th><th>Stock</th><th>Min Required</th><th>Supplier</th><th>Phone</th></tr></thead>
                  <tbody>
                    {lowStockItems.map(i => (
                      <tr key={i.id}>
                        <td>{i.name}</td>
                        <td><span className={i.stock === 0 ? "badge-out" : "badge-low"}>{i.stock}</span></td>
                        <td>{i.minStock}</td>
                        <td>{i.supplier}</td>
                        <td><a href={`tel:${i.supplierPhone}`} style={{ color: "#00bcd4" }}>📞 {i.supplierPhone}</a></td>
                      </tr>
                    ))}
                  </tbody>
                </table>
              </div>
            )}
          </div>
        )}

        {/* INVENTORY */}
        {activeTab === "Inventory" && (
          <div>
            <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 20, flexWrap: "wrap", gap: 12 }}>
              <div style={{ fontSize: 22, fontFamily: "'Baloo 2'", fontWeight: 800 }}>💊 Inventory</div>
              <div style={{ display: "flex", gap: 10, flexWrap: "wrap" }}>
                <input className="inp" style={{ width: 280 }} placeholder="🔍 Dawai ka naam ya category dhundo..." value={searchTerm} onChange={e => setSearchTerm(e.target.value)} />
                <button className="btn-primary" onClick={() => { setShowAddModal(true); setEditId(null); setNewMed({ name: "", category: "Tablet", stock: "", price: "", supplier: "", supplierPhone: "", minStock: "", expiry: "" }); }}>+ Nayi Dawai Add Karo</button>
                <button className="btn-secondary" onClick={exportExcel}>📥 Excel Export</button>
              </div>
            </div>
            <div className="card" style={{ overflow: "auto" }}>
              <table>
                <thead><tr><th>Dawai Ka Naam</th><th>Category</th><th>Stock</th><th>Price</th><th>Supplier</th><th>Phone</th><th>Expiry</th><th>Status</th><th>Actions</th></tr></thead>
                <tbody>
                  {filteredInventory.map(item => (
                    <tr key={item.id}>
                      <td style={{ fontWeight: 600 }}>{item.name}</td>
                      <td><span style={{ background: "rgba(0,188,212,0.15)", color: "#00bcd4", borderRadius: 6, padding: "2px 8px", fontSize: 12 }}>{item.category}</span></td>
                      <td style={{ fontWeight: 700, color: item.stock === 0 ? "#ff5252" : item.stock <= item.minStock ? "#ffc107" : "#00e676" }}>{item.stock}</td>
                      <td>₹{item.price}</td>
                      <td>{item.supplier}</td>
                      <td><a href={`tel:${item.supplierPhone}`} style={{ color: "#00bcd4", textDecoration: "none" }}>📞 {item.supplierPhone}</a></td>
                      <td style={{ color: "#90a4ae", fontSize: 13 }}>{item.expiry}</td>
                      <td>{item.stock === 0 ? <span className="badge-out">Out of Stock</span> : item.stock <= item.minStock ? <span className="badge-low">Low Stock</span> : <span className="badge-ok">OK</span>}</td>
                      <td>
                        <button className="btn-secondary" style={{ marginRight: 6, fontSize: 12 }} onClick={() => openEdit(item)}>✏️ Edit</button>
                        <button className="btn-primary" style={{ fontSize: 12, padding: "6px 12px" }} onClick={() => { addToCart(item); setActiveTab("Billing"); }}>🛒 Add</button>
                      </td>
                    </tr>
                  ))}
                </tbody>
              </table>
            </div>
          </div>
        )}

        {/* BILLING */}
        {activeTab === "Billing" && (
          <div style={{ display: "grid", gridTemplateColumns: "1fr 380px", gap: 20 }}>
            <div>
              <div style={{ fontSize: 22, fontFamily: "'Baloo 2'", fontWeight: 800, marginBottom: 16 }}>🧾 Billing</div>
              <div className="card" style={{ padding: 20, marginBottom: 16 }}>
                <div style={{ fontWeight: 700, marginBottom: 14, color: "#90caf9" }}>Patient Ki Details</div>
                <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 12 }}>
                  <div><label style={{ fontSize: 12, color: "#90a4ae" }}>Patient Ka Naam *</label><input className="inp" style={{ marginTop: 4 }} value={patientName} onChange={e => setPatientName(e.target.value)} placeholder="Naam daalo..." /></div>
                  <div><label style={{ fontSize: 12, color: "#90a4ae" }}>Phone Number</label><input className="inp" style={{ marginTop: 4 }} value={patientPhone} onChange={e => setPatientPhone(e.target.value)} placeholder="Phone..." /></div>
                </div>
              </div>
              <div className="card" style={{ padding: 20, marginBottom: 16 }}>
                <div style={{ fontWeight: 700, marginBottom: 14, color: "#90caf9" }}>Dawai Dhundo & Add Karo</div>
                <input className="inp" placeholder="🔍 Dawai ka naam dhundo..." value={searchTerm} onChange={e => setSearchTerm(e.target.value)} />
                <div style={{ maxHeight: 260, overflowY: "auto", marginTop: 10 }}>
                  {filteredInventory.filter(i => searchTerm).map(item => (
                    <div key={item.id} style={{ display: "flex", justifyContent: "space-between", alignItems: "center", padding: "10px 12px", background: "#252838", borderRadius: 10, marginBottom: 6 }}>
                      <div>
                        <div style={{ fontWeight: 600, fontSize: 14 }}>{item.name}</div>
                        <div style={{ fontSize: 12, color: "#90a4ae" }}>Stock: {item.stock} | ₹{item.price}</div>
                      </div>
                      <button className="btn-primary" style={{ fontSize: 12, padding: "6px 14px" }} onClick={() => addToCart(item)}>+ Add</button>
                    </div>
                  ))}
                  {searchTerm && filteredInventory.filter(i => searchTerm).length === 0 && <div style={{ color: "#90a4ae", textAlign: "center", padding: 20 }}>Koi dawai nahi mili</div>}
                </div>
              </div>
              <div className="card" style={{ padding: 20 }}>
                <div style={{ fontWeight: 700, marginBottom: 12, color: "#90caf9" }}>Purane Bills ({bills.length})</div>
                {bills.length === 0 ? <div style={{ color: "#90a4ae", fontSize: 14 }}>Abhi koi bill nahi</div> : bills.map(b => (
                  <div key={b.id} onClick={() => setShowBillPreview(b)} style={{ cursor: "pointer", display: "flex", justifyContent: "space-between", padding: "10px 14px", background: "#252838", borderRadius: 10, marginBottom: 6 }}>
                    <div><div style={{ fontWeight: 600, fontSize: 14 }}>{b.patient}</div><div style={{ fontSize: 12, color: "#90a4ae" }}>{b.date} • {b.items.length} items</div></div>
                    <div style={{ fontWeight: 800, color: "#00e676" }}>₹{b.total.toFixed(2)}</div>
                  </div>
                ))}
              </div>
            </div>
            <div>
              <div className="card" style={{ padding: 20, position: "sticky", top: 20 }}>
                <div style={{ fontWeight: 800, fontSize: 16, marginBottom: 16, fontFamily: "'Baloo 2'" }}>🛒 Cart ({cart.length} items)</div>
                {cart.length === 0 ? <div style={{ color: "#90a4ae", fontSize: 14, textAlign: "center", padding: 20 }}>Cart khaali hai<br/>Inventory se dawai add karo</div> : <>
                  {cart.map(item => (
                    <div key={item.id} style={{ background: "#252838", borderRadius: 10, padding: 12, marginBottom: 8 }}>
                      <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start" }}>
                        <div style={{ fontWeight: 600, fontSize: 13, flex: 1 }}>{item.name}</div>
                        <button className="btn-danger" style={{ fontSize: 11, padding: "3px 8px", marginLeft: 8 }} onClick={() => removeFromCart(item.id)}>✕</button>
                      </div>
                      <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginTop: 8 }}>
                        <div style={{ display: "flex", alignItems: "center", gap: 8 }}>
                          <button onClick={() => updateCartQty(item.id, item.qty - 1)} style={{ width: 26, height: 26, background: "#3d5afe", border: "none", borderRadius: 6, color: "#fff", cursor: "pointer", fontWeight: 700 }}>−</button>
                          <span style={{ fontWeight: 700, minWidth: 24, textAlign: "center" }}>{item.qty}</span>
                          <button onClick={() => updateCartQty(item.id, item.qty + 1)} style={{ width: 26, height: 26, background: "#3d5afe", border: "none", borderRadius: 6, color: "#fff", cursor: "pointer", fontWeight: 700 }}>+</button>
                        </div>
                        <div style={{ fontWeight: 700, color: "#00e676" }}>₹{(item.price * item.qty).toFixed(2)}</div>
                      </div>
                    </div>
                  ))}
                  <div style={{ borderTop: "1px solid rgba(255,255,255,0.1)", marginTop: 12, paddingTop: 12 }}>
                    <div style={{ display: "flex", justifyContent: "space-between", fontSize: 13, marginBottom: 6, color: "#90a4ae" }}><span>Subtotal</span><span>₹{totalAmount.toFixed(2)}</span></div>
                    <div style={{ display: "flex", justifyContent: "space-between", fontSize: 13, marginBottom: 10, color: "#90a4ae" }}><span>GST (5%)</span><span>₹{gst.toFixed(2)}</span></div>
                    <div style={{ display: "flex", justifyContent: "space-between", fontWeight: 800, fontSize: 16 }}><span>Total</span><span style={{ color: "#00e676" }}>₹{grandTotal.toFixed(2)}</span></div>
                  </div>
                  <button className="btn-primary" style={{ width: "100%", marginTop: 14, padding: 12, fontSize: 15 }} onClick={generateBill}>🧾 Bill Generate Karo</button>
                </>}
              </div>
            </div>
          </div>
        )}

        {/* ORDERS */}
        {activeTab === "Orders" && (
          <div>
            <div style={{ fontSize: 22, fontFamily: "'Baloo 2'", fontWeight: 800, marginBottom: 16 }}>📦 Order Management</div>
            <div className="card" style={{ padding: 20, marginBottom: 20 }}>
              <div style={{ fontWeight: 700, marginBottom: 14, color: "#90caf9" }}>Nayi Order Banao — Sab suppliers ke saath phone numbers</div>
              {inventory.map(item => (
                <div key={item.id} style={{ display: "grid", gridTemplateColumns: "2fr 1fr 1fr 1fr 1fr 100px", gap: 10, alignItems: "center", padding: "10px 12px", background: item.stock <= item.minStock ? "rgba(255,82,82,0.06)" : "#252838", borderRadius: 10, marginBottom: 6, border: item.stock <= item.minStock ? "1px solid rgba(255,82,82,0.2)" : "1px solid transparent" }}>
                  <div>
                    <div style={{ fontWeight: 600, fontSize: 13 }}>{item.name}</div>
                    <div style={{ fontSize: 11, color: "#90a4ae" }}>{item.supplier}</div>
                  </div>
                  <div style={{ fontSize: 12 }}>Stock: <span style={{ color: item.stock === 0 ? "#ff5252" : item.stock <= item.minStock ? "#ffc107" : "#00e676", fontWeight: 700 }}>{item.stock}</span></div>
                  <div style={{ fontSize: 12, color: "#90a4ae" }}>Min: {item.minStock}</div>
                  <a href={`tel:${item.supplierPhone}`} style={{ fontSize: 12, color: "#00bcd4", textDecoration: "none" }}>📞 {item.supplierPhone}</a>
                  <input type="number" className="inp" style={{ padding: "6px 10px" }} placeholder="Qty..." min="0" value={orderQty[item.id] || ""} onChange={e => setOrderQty({ ...orderQty, [item.id]: +e.target.value })} />
                  {orderQty[item.id] > 0 && <span style={{ fontSize: 12, color: "#3d5afe", fontWeight: 700 }}>₹{(item.price * orderQty[item.id]).toFixed(0)}</span>}
                </div>
              ))}
              <div style={{ marginTop: 16, display: "flex", gap: 12, justifyContent: "flex-end" }}>
                <button className="btn-secondary" onClick={exportExcel}>📥 Excel Export</button>
                <button className="btn-primary" style={{ padding: "12px 28px" }} onClick={placeOrder}>📦 Order Place Karo</button>
              </div>
            </div>
            {orders.length > 0 && (
              <div className="card" style={{ padding: 20 }}>
                <div style={{ fontWeight: 700, marginBottom: 14, color: "#90caf9" }}>Order History</div>
                {orders.map(o => (
                  <div key={o.id} style={{ background: "#252838", borderRadius: 12, padding: 16, marginBottom: 12 }}>
                    <div style={{ display: "flex", justifyContent: "space-between", marginBottom: 10 }}>
                      <div><span style={{ fontWeight: 800, color: "#3d5afe" }}>{o.id}</span> <span style={{ fontSize: 12, color: "#90a4ae", marginLeft: 8 }}>{o.date}</span></div>
                      <span style={{ background: "rgba(0,230,118,0.15)", color: "#00e676", borderRadius: 6, padding: "3px 10px", fontSize: 12, fontWeight: 700 }}>✅ {o.status}</span>
                    </div>
                    {o.items.map(i => <div key={i.id} style={{ fontSize: 13, color: "#b0bec5", marginBottom: 4 }}>• {i.name}: <b style={{ color: "#e8eaf6" }}>{i.orderQty} units</b> from {i.supplier} (📞 {i.supplierPhone})</div>)}
                  </div>
                ))}
              </div>
            )}
          </div>
        )}

        {/* LOW STOCK ALERT */}
        {activeTab === "Low Stock Alert" && (
          <div>
            <div style={{ fontSize: 22, fontFamily: "'Baloo 2'", fontWeight: 800, marginBottom: 16 }}>⚠️ Low Stock Alerts</div>
            {outOfStock.length > 0 && (
              <div className="card" style={{ padding: 20, marginBottom: 20, borderLeft: "4px solid #ff5252" }}>
                <div style={{ fontWeight: 800, color: "#ff5252", fontSize: 16, marginBottom: 14 }}>🚫 OUT OF STOCK — Abhi Order Karo!</div>
                <table>
                  <thead><tr><th>Dawai</th><th>Supplier</th><th>Phone</th><th>Price</th><th>Action</th></tr></thead>
                  <tbody>{outOfStock.map(i => (
                    <tr key={i.id}>
                      <td style={{ fontWeight: 700 }}>{i.name}</td>
                      <td>{i.supplier}</td>
                      <td><a href={`tel:${i.supplierPhone}`} style={{ color: "#00bcd4", fontWeight: 700 }}>📞 {i.supplierPhone}</a></td>
                      <td>₹{i.price}</td>
                      <td><button className="btn-primary" style={{ fontSize: 12, padding: "6px 14px" }} onClick={() => setActiveTab("Orders")}>📦 Order Karo</button></td>
                    </tr>
                  ))}</tbody>
                </table>
              </div>
            )}
            {lowStockItems.filter(i => i.stock > 0).length > 0 && (
              <div className="card" style={{ padding: 20, borderLeft: "4px solid #ffc107" }}>
                <div style={{ fontWeight: 800, color: "#ffc107", fontSize: 16, marginBottom: 14 }}>⚠️ Low Stock — Jaldi Order Karo!</div>
                <table>
                  <thead><tr><th>Dawai</th><th>Current Stock</th><th>Min Required</th><th>Supplier</th><th>Phone</th><th>Action</th></tr></thead>
                  <tbody>{lowStockItems.filter(i => i.stock > 0).map(i => (
                    <tr key={i.id}>
                      <td style={{ fontWeight: 700 }}>{i.name}</td>
                      <td><span className="badge-low">{i.stock}</span></td>
                      <td>{i.minStock}</td>
                      <td>{i.supplier}</td>
                      <td><a href={`tel:${i.supplierPhone}`} style={{ color: "#00bcd4", fontWeight: 700 }}>📞 {i.supplierPhone}</a></td>
                      <td><button className="btn-primary" style={{ fontSize: 12, padding: "6px 14px" }} onClick={() => setActiveTab("Orders")}>📦 Order Karo</button></td>
                    </tr>
                  ))}</tbody>
                </table>
              </div>
            )}
            {lowStockItems.length === 0 && <div style={{ textAlign: "center", padding: 60, color: "#00e676", fontWeight: 700, fontSize: 18 }}>✅ Sab theek hai! Koi bhi dawai low stock nahi hai.</div>}
          </div>
        )}
      </div>

      {/* ADD/EDIT MODAL */}
      {showAddModal && (
        <div className="modal-overlay">
          <div style={{ background: "#1a1d2e", borderRadius: 20, padding: 28, width: "90%", maxWidth: 520, border: "1px solid rgba(255,255,255,0.1)" }}>
            <div style={{ fontFamily: "'Baloo 2'", fontWeight: 800, fontSize: 18, marginBottom: 20 }}>{editId ? "✏️ Dawai Edit Karo" : "➕ Nayi Dawai Add Karo"}</div>
            <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 12 }}>
              {[
                { label: "Dawai Ka Naam *", key: "name", placeholder: "e.g. Paracetamol 500mg", full: true },
                { label: "Stock Quantity *", key: "stock", placeholder: "e.g. 100", type: "number" },
                { label: "Price (₹) *", key: "price", placeholder: "e.g. 5.50", type: "number" },
                { label: "Min Stock Alert", key: "minStock", placeholder: "e.g. 30", type: "number" },
                { label: "Supplier Ka Naam", key: "supplier", placeholder: "e.g. Sun Pharma" },
                { label: "Supplier Phone", key: "supplierPhone", placeholder: "e.g. 9876543210" },
                { label: "Expiry Date", key: "expiry", type: "date" },
              ].map(f => (
                <div key={f.key} style={{ gridColumn: f.full ? "1/-1" : "auto" }}>
                  <label style={{ fontSize: 12, color: "#90a4ae", display: "block", marginBottom: 4 }}>{f.label}</label>
                  <input className="inp" type={f.type || "text"} placeholder={f.placeholder} value={newMed[f.key]} onChange={e => setNewMed({ ...newMed, [f.key]: e.target.value })} />
                </div>
              ))}
              <div>
                <label style={{ fontSize: 12, color: "#90a4ae", display: "block", marginBottom: 4 }}>Category</label>
                <select className="inp" value={newMed.category} onChange={e => setNewMed({ ...newMed, category: e.target.value })}>
                  {["Tablet", "Capsule", "Syrup", "Injection", "Ointment", "Drops", "Other"].map(c => <option key={c}>{c}</option>)}
                </select>
              </div>
            </div>
            <div style={{ display: "flex", gap: 10, marginTop: 20, justifyContent: "flex-end" }}>
              <button className="btn-secondary" onClick={() => { setShowAddModal(false); setEditId(null); }}>Cancel</button>
              <button className="btn-primary" onClick={saveEdit}>{editId ? "✅ Update Karo" : "✅ Add Karo"}</button>
            </div>
          </div>
        </div>
      )}

      {/* BILL PREVIEW MODAL */}
      {showBillPreview && (
        <div className="modal-overlay" onClick={() => setShowBillPreview(null)}>
          <div onClick={e => e.stopPropagation()} style={{ background: "#fff", color: "#000", borderRadius: 16, padding: 30, width: "90%", maxWidth: 480, maxHeight: "90vh", overflowY: "auto" }} ref={billRef}>
            <div style={{ textAlign: "center", marginBottom: 20 }}>
              <div style={{ fontSize: 22, fontWeight: 800, color: "#1a237e" }}>💊 MedStore Pro</div>
              <div style={{ fontSize: 12, color: "#555" }}>Medical Store Inventory System</div>
              <div style={{ borderBottom: "2px dashed #ccc", margin: "12px 0" }}></div>
              <div style={{ fontWeight: 800, fontSize: 16 }}>BILL / RECEIPT</div>
            </div>
            <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 6, marginBottom: 14, fontSize: 13 }}>
              <div><b>Bill No:</b> {showBillPreview.id}</div>
              <div><b>Date:</b> {showBillPreview.date}</div>
              <div><b>Patient:</b> {showBillPreview.patient}</div>
              {showBillPreview.phone && <div><b>Phone:</b> {showBillPreview.phone}</div>}
            </div>
            <table style={{ width: "100%", fontSize: 13, marginBottom: 14 }}>
              <thead style={{ background: "#f0f4ff" }}>
                <tr><th style={{ padding: "8px 6px", textAlign: "left" }}>Dawai</th><th style={{ padding: "8px 6px" }}>Qty</th><th style={{ padding: "8px 6px" }}>Rate</th><th style={{ padding: "8px 6px", textAlign: "right" }}>Amount</th></tr>
              </thead>
              <tbody>
                {showBillPreview.items.map(i => (
                  <tr key={i.id} style={{ borderBottom: "1px solid #eee" }}>
                    <td style={{ padding: "7px 6px" }}>{i.name}</td>
                    <td style={{ padding: "7px 6px", textAlign: "center" }}>{i.qty}</td>
                    <td style={{ padding: "7px 6px", textAlign: "center" }}>₹{i.price}</td>
                    <td style={{ padding: "7px 6px", textAlign: "right", fontWeight: 600 }}>₹{(i.price * i.qty).toFixed(2)}</td>
                  </tr>
                ))}
              </tbody>
            </table>
            <div style={{ borderTop: "1px solid #ccc", paddingTop: 10, fontSize: 13 }}>
              <div style={{ display: "flex", justifyContent: "space-between", marginBottom: 4 }}><span>Subtotal:</span><span>₹{showBillPreview.subtotal.toFixed(2)}</span></div>
              <div style={{ display: "flex", justifyContent: "space-between", marginBottom: 8, color: "#555" }}><span>GST (5%):</span><span>₹{showBillPreview.gst.toFixed(2)}</span></div>
              <div style={{ display: "flex", justifyContent: "space-between", fontWeight: 800, fontSize: 16, borderTop: "2px solid #1a237e", paddingTop: 8 }}><span>TOTAL:</span><span style={{ color: "#1a237e" }}>₹{showBillPreview.total.toFixed(2)}</span></div>
            </div>
            <div style={{ textAlign: "center", marginTop: 16, fontSize: 11, color: "#888" }}>Aapki sehat hi hamari pehli zimmedari hai. Get well soon! 🙏</div>
            <div style={{ display: "flex", gap: 10, marginTop: 16, justifyContent: "center" }}>
              <button className="btn-primary" style={{ background: "#1a237e", color: "#fff" }} onClick={printBill}>🖨️ Print Karo</button>
              <button className="btn-secondary" style={{ color: "#000" }} onClick={() => setShowBillPreview(null)}>Band Karo</button>
            </div>
          </div>
        </div>
      )}
    </div>
  );
}
