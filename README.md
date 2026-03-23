# santander-web
santander-web
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <title>Santander | Internet Banking</title>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=0">
    <style>
        :root {
            --santander-red: #ec0000;
            --bg-gray: #f4f4f4;
            --text-dark: #333333;
            --text-light: #666666;
        }

        body {
            font-family: 'Open Sans', Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--bg-gray);
            color: var(--text-dark);
        }

        /* Topo Vermelho Oficial */
        .header {
            background-color: var(--santander-red);
            height: 60px;
            display: flex;
            align-items: center;
            padding: 0 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            position: fixed;
            top: 0;
            width: 100%;
            z-index: 1000;
        }

        .logo-simulada {
            color: white;
            font-weight: 800;
            font-size: 1.5rem;
            letter-spacing: -1px;
        }

        /* Boas-vindas */
        .user-bar {
            background: white;
            margin-top: 60px;
            padding: 15px 25px;
            border-bottom: 1px solid #ddd;
            font-size: 0.9rem;
        }

        .main-content {
            padding: 25px;
            max-width: 1000px;
            margin: 0 auto;
        }

        /* Card de Conta Corrente */
        .account-card {
            background: white;
            border-radius: 4px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            width: 100%;
            max-width: 400px;
            overflow: hidden;
            border-left: 6px solid var(--santander-red);
        }

        .card-header {
            padding: 20px;
        }

        .card-label {
            color: var(--text-light);
            font-size: 0.8rem;
            text-transform: uppercase;
            display: block;
            margin-bottom: 8px;
        }

        .card-value {
            font-size: 2rem;
            font-weight: 700;
            color: var(--text-dark);
        }

        .card-footer {
            background: #f9f9f9;
            padding: 12px 20px;
            border-top: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            font-size: 0.85rem;
            color: var(--text-light);
        }

        /* Botões de Ação Rápidas */
        .quick-actions {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .btn-action {
            background: white;
            border: 1px solid #ddd;
            padding: 10px 20px;
            border-radius: 4px;
            font-size: 0.8rem;
            cursor: pointer;
            flex: 1;
            text-align: center;
        }

        /* Painel do Gerador (Discreto) */
        #gerador-container {
            display: none;
            position: fixed;
            bottom: 80px;
            right: 20px;
            background: white;
            width: 280px;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 5px 25px rgba(0,0,0,0.2);
            z-index: 2000;
            border-top: 4px solid var(--santander-red);
        }

        #gerador-container h4 { margin-top: 0; color: var(--santander-red); }
        
        input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
            box-sizing: border-box;
        }

        .btn-aplicar {
            background: var(--santander-red);
            color: white;
            border: none;
            width: 100%;
            padding: 12px;
            border-radius: 4px;
            font-weight: bold;
            cursor: pointer;
        }

        .open-console {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #333;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 30px;
            cursor: pointer;
            font-size: 0.8rem;
            z-index: 1001;
        }
    </style>
</head>

<body>

    <div class="header">
        <div class="logo-simulada">Santander</div>
    </div>

    <div class="user-bar">
        Olá, <strong id="nome-titular">ADMIN_USER</strong> | Conta: <strong>1234567-8</strong>
    </div>

    <div class="main-content">
        <div class="account-card">
            <div class="card-header">
                <span class="card-label">Saldo em conta corrente</span>
                <span class="card-value" id="saldo-display">R$ 0,00</span>
            </div>
            <div class="card-footer">
                <span>Agência 0001</span>
                <span>Saldo disponível</span>
            </div>
        </div>

        <div class="quick-actions">
            <div class="btn-action">Pix</div>
            <div class="btn-action">Pagamentos</div>
            <div class="btn-action">Extrato</div>
        </div>
    </div>

    <button class="open-console" onclick="toggleGerador()">Configurar Saldo</button>

    <div id="gerador-container">
        <h4>Painel de Controle</h4>
        <label style="font-size: 12px;">NOME DO CLIENTE</label>
        <input type="text" id="in-nome" placeholder="Nome...">
        
        <label style="font-size: 12px;">SALDO DESEJADO (R$)</label>
        <input type="number" id="in-saldo" placeholder="Ex: 1500.00">
        
        <button class="btn-aplicar" onclick="aplicar()">Atualizar Internet Banking</button>
    </div>

    <script>
        function toggleGerador() {
            const painel = document.getElementById('gerador-container');
            painel.style.display = (painel.style.display === 'block') ? 'none' : 'block';
        }

        function aplicar() {
            const nome = document.getElementById('in-nome').value;
            const saldo = parseFloat(document.getElementById('in-saldo').value);

            if (nome) {
                document.getElementById('nome-titular').innerText = nome.toUpperCase();
            }

            if (!isNaN(saldo)) {
                document.getElementById('saldo-display').innerText = saldo.toLocaleString('pt-BR', { 
                    style: 'currency', 
                    currency: 'BRL' 
                });
            }
            
            toggleGerador();
        }
    </script>

</body>
</html>
