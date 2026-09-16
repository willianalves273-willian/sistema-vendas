<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Prévia — Edição de Produtos</title>
<style>
*{box-sizing:border-box}
body{font-family:Arial,sans-serif;margin:0;background:#f3f4f6;color:#222}
header{background:#1f2937;color:white;padding:18px}
header h1{margin:0 0 5px}
nav{background:white;padding:10px;display:flex;gap:8px;flex-wrap:wrap;box-shadow:0 2px 5px #ccc}
button{padding:10px 14px;border:0;border-radius:6px;cursor:pointer;background:#2563eb;color:white;font-size:14px}
button:hover{opacity:.9}
button.excluir{background:#dc2626}
button.editar{background:#15803d}
button.secundario{background:#6b7280}
.container{max-width:1100px;margin:20px auto;padding:0 15px}
.card{background:white;padding:20px;margin-bottom:20px;border-radius:10px;box-shadow:0 2px 8px #ddd}
input{padding:10px;margin:5px;border:1px solid #bbb;border-radius:5px;font-size:16px;max-width:100%}
table{width:100%;border-collapse:collapse;margin-top:15px}
th,td{border:1px solid #ddd;padding:9px;text-align:left}
th{background:#e5e7eb}
.oculto{display:none}
.aviso{background:#fff7ed;border:1px solid #fed7aa;padding:12px;border-radius:7px;margin:10px 0}
.modal{position:fixed;inset:0;background:rgba(0,0,0,.55);display:flex;align-items:center;justify-content:center;padding:15px;z-index:20}
.caixa{background:white;border-radius:10px;padding:20px;width:min(520px,100%);box-shadow:0 10px 30px rgba(0,0,0,.3)}
.caixa h2{margin-top:0}
.acoes{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px}
@media(max-width:700px){
header{padding:14px}header h1{font-size:23px}
nav{padding:8px}nav button{flex:1 1 45%;min-height:45px}
.container{margin:10px auto;padding:0 8px}.card{padding:14px}
input{width:100%;margin:5px 0}table{font-size:13px}th,td{padding:7px 5px}
button{min-height:42px}.acoes button{width:100%}
}
</style>
</head>
<body>
<header>
<h1>Sistema de Vendas</h1>
<div>Prévia da alteração — Cadastro de Produtos</div>
</header>

<nav>
<button>Início</button>
<button>Produtos</button>
<button>Nova Venda</button>
<button>Vendas</button>
<button>🖨️ Imprimir Vendas</button>
<button>Estoque</button>
<button>Relatórios</button>
</nav>

<div class="container">
<section class="card">
<h2>Cadastro de Produtos</h2>

<div class="aviso">
<b>PRÉVIA:</b> o produto não será excluído. Ao clicar em <b>✏️ Editar</b>,
somente os campos que você modificar serão atualizados.
</div>

<input placeholder="Nome do produto" value="Café 500g">
<input placeholder="Preço de venda" value="18.00">
<input placeholder="Custo" value="12.00">
<input placeholder="Quantidade" value="25">
<input placeholder="Estoque mínimo" value="5">
<button>Cadastrar</button>

<div style="overflow-x:auto">
<table>
<thead>
<tr>
<th>Produto</th>
<th>Preço</th>
<th>Custo</th>
<th>Estoque</th>
<th>Mínimo</th>
<th>Ação</th>
</tr>
</thead>
<tbody>
<tr>
<td>Café 500g</td>
<td>R$ 18,00</td>
<td>R$ 12,00</td>
<td>25</td>
<td>5</td>
<td>
<button class="editar" onclick="abrir()">✏️ Editar</button>
<button class="excluir">Excluir</button>
</td>
</tr>
<tr>
<td>Arroz 5 kg</td>
<td>R$ 28,00</td>
<td>R$ 20,00</td>
<td>12</td>
<td>5</td>
<td>
<button class="editar" onclick="abrir2()">✏️ Editar</button>
<button class="excluir">Excluir</button>
</td>
</tr>
</tbody>
</table>
</div>
</section>

<section class="card">
<h3>O que acontece ao editar?</h3>
<p>Exemplo: você muda apenas o preço do Café de <b>R$ 18,00</b> para <b>R$ 19,00</b>.</p>
<p>O cadastro continua sendo o mesmo:</p>
<ul>
<li>Produto: Café 500g — permanece</li>
<li>Custo: R$ 12,00 — permanece</li>
<li>Estoque: 25 — permanece</li>
<li>Mínimo: 5 — permanece</li>
<li><b>Preço: R$ 19,00 — alterado</b></li>
</ul>
</section>
</div>

<div id="modal" class="modal oculto">
<div class="caixa">
<h2>✏️ Editar produto</h2>
<div class="aviso">Você está editando o cadastro existente. <b>Não é necessário excluir o produto.</b></div>
<label>Produto</label>
<input id="nome" value="Café 500g">
<label>Preço de venda</label>
<input id="preco" type="number" step="0.01" value="18.00">
<label>Custo</label>
<input id="custo" type="number" step="0.01" value="12.00">
<label>Estoque atual</label>
<input id="estoque" type="number" value="25">
<label>Estoque mínimo</label>
<input id="minimo" type="number" value="5">
<div class="acoes">
<button onclick="salvar()">💾 Salvar alteração</button>
<button class="secundario" onclick="fechar()">Cancelar</button>
</div>
</div>
</div>

<script>
function abrir(){document.getElementById('modal').classList.remove('oculto')}
function abrir2(){document.getElementById('modal').classList.remove('oculto');document.getElementById('nome').value='Arroz 5 kg';document.getElementById('preco').value='28.00';document.getElementById('custo').value='20.00';document.getElementById('estoque').value='12';document.getElementById('minimo').value='5'}
function fechar(){document.getElementById('modal').classList.add('oculto')}
function salvar(){alert('Prévia: a alteração seria salva no mesmo produto, sem excluir o cadastro.');fechar()}
</script>
</body>
</html>
