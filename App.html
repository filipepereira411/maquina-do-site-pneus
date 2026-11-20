import { useEffect, useState } from "react";

type Role = "cliente" | "admin";
type User = { nome: string; email: string; senha: string; role: Role };
type Produto = { id: number; nome: string; medida: string; preco: number; tag: string };
type Agend = { id: number; email: string; nome: string; whats: string; servico: string; status: string; data: string };
type Pedido = { id: number; email: string; itens: string[]; total: number; data: string };

const prodIniciais: Produto[] = [
  { id: 1, nome: "Michelin Primacy 4", medida: "205/55 R16", preco: 689, tag: "Mais vendido" },
  { id: 2, nome: "Pirelli Cinturato P7", medida: "195/65 R15", preco: 549, tag: "Economia" },
  { id: 3, nome: "Goodyear EfficientGrip", medida: "185/60 R15", preco: 479, tag: "" },
  { id: 4, nome: "Bridgestone Dueler A/T", medida: "265/70 R16", preco: 1129, tag: "SUV / 4x4" },
  { id: 5, nome: "Continental PowerContact", medida: "175/70 R14", preco: 389, tag: "Oferta" },
  { id: 6, nome: "Pirelli Scorpion Verde", medida: "225/65 R17", preco: 899, tag: "" },
];
const usersIniciais: User[] = [
  { nome: "Administrador", email: "admin@rodaforte.com", senha: "admin123", role: "admin" },
  { nome: "Cliente Teste", email: "cliente@teste.com", senha: "123456", role: "cliente" },
];
const servicos = [
  ["🔧", "Montagem grátis", "Na compra de 4 pneus, montagem e válvula inclusas."],
  ["⚖️", "Balanceamento", "Equipamento computadorizado de alta precisão."],
  ["📐", "Alinhamento 3D", "Mais segurança e menos desgaste dos pneus."],
  ["🛞", "Rodízio e calibragem", "Calibragem com nitrogênio para clientes."],
];

function useLS<T>(k: string, init: T) {
  const [v, setV] = useState<T>(() => {
    try { const s = localStorage.getItem(k); return s ? JSON.parse(s) : init; } catch { return init; }
  });
  useEffect(() => localStorage.setItem(k, JSON.stringify(v)), [k, v]);
  return [v, setV] as const;
}
const brl = (n: number) => n.toLocaleString("pt-BR", { style: "currency", currency: "BRL" });
const inp = "bg-zinc-900 border border-zinc-800 rounded-lg p-3 w-full focus:outline-none focus:border-yellow-400";
const btn = "bg-yellow-400 text-black font-bold px-4 py-2 rounded-lg hover:bg-yellow-300";

export default function App() {
  const [users, setUsers] = useLS<User[]>("rf_users", usersIniciais);
  const [produtos, setProdutos] = useLS<Produto[]>("rf_prod", prodIniciais);
  const [agends, setAgends] = useLS<Agend[]>("rf_ag", []);
  const [pedidos, setPedidos] = useLS<Pedido[]>("rf_ped", []);
  const [sessao, setSessao] = useLS<string | null>("rf_sess", null);
  const [carrinho, setCarrinho] = useState<Produto[]>([]);
  const [view, setView] = useState<"loja" | "login" | "painel" | "carrinho">("loja");
  const user = users.find((u) => u.email === sessao) || null;

  const logout = () => { setSessao(null); setCarrinho([]); setView("loja"); };

  return (
    <div className="min-h-screen bg-zinc-950 text-zinc-100 font-sans">
      <header className="sticky top-0 z-20 bg-zinc-950/90 backdrop-blur border-b border-zinc-800">
        <div className="max-w-6xl mx-auto flex items-center justify-between p-4 gap-3">
          <button onClick={() => setView("loja")} className="text-2xl font-black tracking-tight">
            Roda<span className="text-yellow-400">Forte</span>
          </button>
          <div className="flex items-center gap-2 text-sm">
            <button onClick={() => setView("carrinho")} className="bg-zinc-800 rounded-full px-4 py-2">🛒 {carrinho.length}</button>
            {user ? (
              <>
                <button onClick={() => setView("painel")} className="bg-zinc-800 rounded-full px-4 py-2">
                  {user.role === "admin" ? "⚙️ Admin" : "👤 Minha conta"}
                </button>
                <button onClick={logout} className="border border-zinc-700 rounded-full px-4 py-2 hover:border-red-400">Sair</button>
              </>
            ) : (
              <button onClick={() => setView("login")} className={btn + " rounded-full"}>Entrar</button>
            )}
          </div>
        </div>
      </header>

      {view === "login" && <Login users={users} setUsers={setUsers} onOk={(e) => { setSessao(e); setView("painel"); }} />}
      {view === "carrinho" && (
        <Carrinho itens={carrinho} setItens={setCarrinho} user={user} irLogin={() => setView("login")}
          finalizar={() => {
            setPedidos([...pedidos, { id: Date.now(), email: user!.email, itens: carrinho.map((c) => c.nome), total: carrinho.reduce((s, c) => s + c.preco, 0), data: new Date().toLocaleString("pt-BR") }]);
            setCarrinho([]); setView("painel");
          }} />
      )}
      {view === "painel" && user?.role === "admin" && (
        <Admin produtos={produtos} setProdutos={setProdutos} agends={agends} setAgends={setAgends} pedidos={pedidos} users={users} />
      )}
      {view === "painel" && user?.role === "cliente" && (
        <Cliente user={user} agends={agends.filter((a) => a.email === user.email)} pedidos={pedidos.filter((p) => p.email === user.email)} />
      )}
      {view === "loja" && (
        <Loja produtos={produtos} add={(p) => setCarrinho([...carrinho, p])} user={user}
          agendar={(a) => setAgends([...agends, { ...a, id: Date.now(), status: "Pendente", data: new Date().toLocaleString("pt-BR") }])} />
      )}

      <footer className="border-t border-zinc-800 py-8 text-center text-sm text-zinc-500">
        © {new Date().getFullYear()} RodaForte Pneus · Seg–Sáb 8h às 18h
      </footer>
    </div>
  );
}

function Login({ users, setUsers, onOk }: { users: User[]; setUsers: (u: User[]) => void; onOk: (e: string) => void }) {
  const [modo, setModo] = useState<"in" | "up">("in");
  const [f, setF] = useState({ nome: "", email: "", senha: "" });
  const [erro, setErro] = useState("");
  const submit = (e: React.FormEvent) => {
    e.preventDefault(); setErro("");
    const email = f.email.trim().toLowerCase();
    if (modo === "in") {
      const u = users.find((u) => u.email === email && u.senha === f.senha);
      return u ? onOk(u.email) : setErro("E-mail ou senha inválidos.");
    }
    if (users.some((u) => u.email === email)) return setErro("E-mail já cadastrado.");
    if (f.senha.length < 6) return setErro("A senha deve ter pelo menos 6 caracteres.");
    setUsers([...users, { nome: f.nome, email, senha: f.senha, role: "cliente" }]);
    onOk(email);
  };
  return (
    <section className="max-w-md mx-auto px-4 py-20">
      <div className="bg-zinc-900 border border-zinc-800 rounded-2xl p-8">
        <div className="flex mb-6 bg-zinc-950 rounded-lg p-1">
          {(["in", "up"] as const).map((m) => (
            <button key={m} onClick={() => { setModo(m); setErro(""); }} className={`flex-1 py-2 rounded-md font-semibold ${modo === m ? "bg-yellow-400 text-black" : "text-zinc-400"}`}>
              {m === "in" ? "Entrar" : "Criar conta"}
            </button>
          ))}
        </div>
        <form onSubmit={submit} className="grid gap-3">
          {modo === "up" && <input required placeholder="Nome" className={inp} value={f.nome} onChange={(e) => setF({ ...f, nome: e.target.value })} />}
          <input required type="email" placeholder="E-mail" className={inp} value={f.email} onChange={(e) => setF({ ...f, email: e.target.value })} />
          <input required type="password" placeholder="Senha" className={inp} value={f.senha} onChange={(e) => setF({ ...f, senha: e.target.value })} />
          {erro && <p className="text-red-400 text-sm">{erro}</p>}
          <button className={btn + " py-3"}>{modo === "in" ? "Entrar" : "Cadastrar"}</button>
        </form>
        <div className="mt-6 text-xs text-zinc-500 bg-zinc-950 rounded-lg p-3">
          <p className="font-semibold text-zinc-400 mb-1">Contas de demonstração:</p>
          <p>Admin: admin@rodaforte.com / admin123</p>
          <p>Cliente: cliente@teste.com / 123456</p>
        </div>
      </div>
    </section>
  );
}

function Loja({ produtos, add, user, agendar }: { produtos: Produto[]; add: (p: Produto) => void; user: User | null; agendar: (a: { email: string; nome: string; whats: string; servico: string }) => void }) {
  const [enviado, setEnviado] = useState(false);
  const [f, setF] = useState({ nome: user?.nome || "", whats: "", servico: "Troca de pneus" });
  return (
    <>
      <section className="relative overflow-hidden">
        <div className="absolute inset-0 bg-[radial-gradient(circle_at_80%_30%,rgba(250,204,21,0.25),transparent_50%)]" />
        <div className="max-w-6xl mx-auto px-4 py-24 grid md:grid-cols-2 gap-10 items-center relative">
          <div>
            <p className="text-yellow-400 font-semibold uppercase tracking-widest text-sm">Pneus novos com garantia</p>
            <h1 className="text-5xl md:text-6xl font-black leading-tight mt-3">Segurança que roda com você.</h1>
            <p className="text-zinc-400 mt-5 text-lg">As melhores marcas, preço justo e montagem grátis. Parcele em até 10x sem juros.</p>
            <div className="flex gap-3 mt-8">
              <a href="#produtos" className={btn + " px-6 py-3"}>Ver pneus</a>
              <a href="#contato" className="border border-zinc-700 px-6 py-3 rounded-lg hover:border-yellow-400">Agendar serviço</a>
            </div>
          </div>
          <div className="flex justify-center">
            <div className="w-72 h-72 rounded-full border-[28px] border-zinc-800 shadow-2xl flex items-center justify-center animate-[spin_12s_linear_infinite] [background:repeating-conic-gradient(#27272a_0_10deg,#18181b_10deg_20deg)]">
              <div className="w-28 h-28 rounded-full bg-zinc-300 border-8 border-zinc-500" />
            </div>
          </div>
        </div>
      </section>

      <section id="produtos" className="max-w-6xl mx-auto px-4 py-20">
        <h2 className="text-3xl font-black">Pneus em destaque</h2>
        <div className="grid sm:grid-cols-2 lg:grid-cols-3 gap-6 mt-8">
          {produtos.map((p) => (
            <div key={p.id} className="bg-zinc-900 border border-zinc-800 rounded-2xl p-6 hover:border-yellow-400 transition">
              <div className="flex justify-between items-start">
                <span className="text-4xl">🛞</span>
                {p.tag && <span className="text-xs bg-yellow-400/15 text-yellow-400 px-2 py-1 rounded">{p.tag}</span>}
              </div>
              <h3 className="font-bold text-lg mt-4">{p.nome}</h3>
              <p className="text-zinc-400 text-sm">{p.medida}</p>
              <p className="text-2xl font-black mt-4">{brl(p.preco)}</p>
              <p className="text-xs text-zinc-500">ou 10x de {brl(p.preco / 10)}</p>
              <button onClick={() => add(p)} className={btn + " mt-5 w-full"}>Adicionar ao carrinho</button>
            </div>
          ))}
        </div>
      </section>

      <section className="bg-zinc-900 py-20">
        <div className="max-w-6xl mx-auto px-4">
          <h2 className="text-3xl font-black">Serviços</h2>
          <div className="grid sm:grid-cols-2 lg:grid-cols-4 gap-6 mt-8">
            {servicos.map(([i, t, d]) => (
              <div key={t} className="bg-zinc-950 rounded-2xl p-6 border border-zinc-800">
                <div className="text-3xl">{i}</div>
                <h3 className="font-bold mt-3">{t}</h3>
                <p className="text-zinc-400 text-sm mt-2">{d}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      <section id="contato" className="max-w-3xl mx-auto px-4 py-20">
        <h2 className="text-3xl font-black text-center">Agende seu atendimento</h2>
        {enviado ? (
          <p className="text-center mt-8 text-yellow-400 font-semibold">✅ Recebemos seu pedido! {user && "Acompanhe em Minha conta."}</p>
        ) : (
          <form onSubmit={(e) => { e.preventDefault(); agendar({ ...f, email: user?.email || "visitante" }); setEnviado(true); }} className="grid gap-4 mt-8">
            <input required placeholder="Nome" className={inp} value={f.nome} onChange={(e) => setF({ ...f, nome: e.target.value })} />
            <input required placeholder="WhatsApp" className={inp} value={f.whats} onChange={(e) => setF({ ...f, whats: e.target.value })} />
            <select className={inp} value={f.servico} onChange={(e) => setF({ ...f, servico: e.target.value })}>
              <option>Troca de pneus</option><option>Alinhamento e balanceamento</option><option>Orçamento</option>
            </select>
            <button className={btn + " py-3"}>Enviar</button>
          </form>
        )}
      </section>
    </>
  );
}

function Carrinho({ itens, setItens, user, irLogin, finalizar }: { itens: Produto[]; setItens: (p: Produto[]) => void; user: User | null; irLogin: () => void; finalizar: () => void }) {
  const total = itens.reduce((s, p) => s + p.preco, 0);
  return (
    <section className="max-w-3xl mx-auto px-4 py-16">
      <h2 className="text-3xl font-black mb-6">Carrinho</h2>
      {itens.length === 0 ? <p className="text-zinc-400">Seu carrinho está vazio.</p> : (
        <>
          {itens.map((p, i) => (
            <div key={i} className="flex justify-between items-center bg-zinc-900 border border-zinc-800 rounded-xl p-4 mb-2">
              <div><p className="font-bold">{p.nome}</p><p className="text-sm text-zinc-400">{p.medida}</p></div>
              <div className="flex items-center gap-4">
                <span>{brl(p.preco)}</span>
                <button onClick={() => setItens(itens.filter((_, j) => j !== i))} className="text-red-400">✕</button>
              </div>
            </div>
          ))}
          <div className="flex justify-between items-center mt-6">
            <p className="text-2xl font-black">Total: {brl(total)}</p>
            {user ? <button onClick={finalizar} className={btn + " py-3"}>Finalizar pedido</button>
              : <button onClick={irLogin} className={btn + " py-3"}>Entre para finalizar</button>}
          </div>
        </>
      )}
    </section>
  );
}

const statusCor: Record<string, string> = { Pendente: "text-yellow-400", Confirmado: "text-green-400", Concluído: "text-blue-400", Cancelado: "text-red-400" };

function Cliente({ user, agends, pedidos }: { user: User; agends: Agend[]; pedidos: Pedido[] }) {
  return (
    <section className="max-w-4xl mx-auto px-4 py-16">
      <h2 className="text-3xl font-black">Olá, {user.nome} 👋</h2>
      <p className="text-zinc-400">{user.email}</p>
      <h3 className="text-xl font-bold mt-10 mb-3">Meus pedidos</h3>
      {pedidos.length === 0 ? <p className="text-zinc-500">Nenhum pedido ainda.</p> : pedidos.map((p) => (
        <div key={p.id} className="bg-zinc-900 border border-zinc-800 rounded-xl p-4 mb-2">
          <div className="flex justify-between"><span className="text-sm text-zinc-400">{p.data}</span><b>{brl(p.total)}</b></div>
          <p className="text-sm mt-1">{p.itens.join(", ")}</p>
        </div>
      ))}
      <h3 className="text-xl font-bold mt-10 mb-3">Meus agendamentos</h3>
      {agends.length === 0 ? <p className="text-zinc-500">Nenhum agendamento.</p> : agends.map((a) => (
        <div key={a.id} className="bg-zinc-900 border border-zinc-800 rounded-xl p-4 mb-2 flex justify-between">
          <div><p className="font-bold">{a.servico}</p><p className="text-sm text-zinc-400">{a.data}</p></div>
          <span className={statusCor[a.status]}>{a.status}</span>
        </div>
      ))}
    </section>
  );
}

function Admin({ produtos, setProdutos, agends, setAgends, pedidos, users }: { produtos: Produto[]; setProdutos: (p: Produto[]) => void; agends: Agend[]; setAgends: (a: Agend[]) => void; pedidos: Pedido[]; users: User[] }) {
  const [aba, setAba] = useState<"prod" | "ag" | "ped" | "cli">("prod");
  const vazio = { nome: "", medida: "", preco: "", tag: "" };
  const [f, setF] = useState(vazio);
  const [edit, setEdit] = useState<number | null>(null);
  const salvar = (e: React.FormEvent) => {
    e.preventDefault();
    const p = { nome: f.nome, medida: f.medida, preco: Number(f.preco), tag: f.tag };
    setProdutos(edit ? produtos.map((x) => (x.id === edit ? { ...x, ...p } : x)) : [...produtos, { id: Date.now(), ...p }]);
    setF(vazio); setEdit(null);
  };
  const stats = [
    ["Produtos", produtos.length], ["Agendamentos", agends.length],
    ["Pedidos", pedidos.length], ["Faturamento", brl(pedidos.reduce((s, p) => s + p.total, 0))],
  ];
  const abas = [["prod", "Produtos"], ["ag", "Agendamentos"], ["ped", "Pedidos"], ["cli", "Clientes"]] as const;
  return (
    <section className="max-w-6xl mx-auto px-4 py-16">
      <h2 className="text-3xl font-black">Painel administrativo</h2>
      <div className="grid grid-cols-2 md:grid-cols-4 gap-4 mt-6">
        {stats.map(([l, v]) => (
          <div key={l} className="bg-zinc-900 border border-zinc-800 rounded-xl p-4">
            <p className="text-sm text-zinc-400">{l}</p><p className="text-2xl font-black text-yellow-400">{v}</p>
          </div>
        ))}
      </div>
      <div className="flex gap-2 mt-8 flex-wrap">
        {abas.map(([k, l]) => (
          <button key={k} onClick={() => setAba(k)} className={`px-4 py-2 rounded-lg font-semibold ${aba === k ? "bg-yellow-400 text-black" : "bg-zinc-900"}`}>{l}</button>
        ))}
      </div>

      <div className="mt-6">
        {aba === "prod" && (
          <>
            <form onSubmit={salvar} className="grid md:grid-cols-5 gap-3 mb-6">
              <input required placeholder="Nome" className={inp} value={f.nome} onChange={(e) => setF({ ...f, nome: e.target.value })} />
              <input required placeholder="Medida" className={inp} value={f.medida} onChange={(e) => setF({ ...f, medida: e.target.value })} />
              <input required type="number" min="0" placeholder="Preço" className={inp} value={f.preco} onChange={(e) => setF({ ...f, preco: e.target.value })} />
              <input placeholder="Etiqueta" className={inp} value={f.tag} onChange={(e) => setF({ ...f, tag: e.target.value })} />
              <button className={btn}>{edit ? "Salvar" : "+ Adicionar"}</button>
            </form>
            {produtos.map((p) => (
              <div key={p.id} className="flex justify-between items-center bg-zinc-900 border border-zinc-800 rounded-xl p-4 mb-2">
                <div><b>{p.nome}</b> <span className="text-zinc-400 text-sm">· {p.medida} · {brl(p.preco)}</span></div>
                <div className="flex gap-3 text-sm">
                  <button onClick={() => { setEdit(p.id); setF({ nome: p.nome, medida: p.medida, preco: String(p.preco), tag: p.tag }); }} className="text-yellow-400">Editar</button>
                  <button onClick={() => confirm("Remover produto?") && setProdutos(produtos.filter((x) => x.id !== p.id))} className="text-red-400">Remover</button>
                </div>
              </div>
            ))}
          </>
        )}
        {aba === "ag" && (agends.length === 0 ? <p className="text-zinc-500">Nenhum agendamento.</p> : agends.map((a) => (
          <div key={a.id} className="flex flex-wrap justify-between items-center gap-3 bg-zinc-900 border border-zinc-800 rounded-xl p-4 mb-2">
            <div><b>{a.nome}</b> <span className="text-zinc-400 text-sm">· {a.whats} · {a.servico} · {a.data}</span></div>
            <select value={a.status} onChange={(e) => setAgends(agends.map((x) => (x.id === a.id ? { ...x, status: e.target.value } : x)))} className={`bg-zinc-950 border border-zinc-700 rounded p-2 ${statusCor[a.status]}`}>
              {Object.keys(statusCor).map((s) => <option key={s}>{s}</option>)}
            </select>
          </div>
        )))}
        {aba === "ped" && (pedidos.length === 0 ? <p className="text-zinc-500">Nenhum pedido.</p> : pedidos.map((p) => (
          <div key={p.id} className="bg-zinc-900 border border-zinc-800 rounded-xl p-4 mb-2">
            <div className="flex justify-between"><span>{p.email} <span className="text-zinc-500 text-sm">· {p.data}</span></span><b>{brl(p.total)}</b></div>
            <p className="text-sm text-zinc-400 mt-1">{p.itens.join(", ")}</p>
          </div>
        )))}
        {aba === "cli" && users.filter((u) => u.role === "cliente").map((u) => (
          <div key={u.email} className="bg-zinc-900 border border-zinc-800 rounded-xl p-4 mb-2 flex justify-between">
            <b>{u.nome}</b><span className="text-zinc-400">{u.email}</span>
          </div>
        ))}
      </div>
    </section>
  );
}
