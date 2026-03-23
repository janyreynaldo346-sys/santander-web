# santander-web
santander-web
// Substitua sua função aplicar e adicione o carregamento automático
window.onload = function() {
    const salvoNome = localStorage.getItem('nome');
    const salvoSaldo = localStorage.getItem('saldo');
    if(salvoNome) document.getElementById('nome-titular').innerText = salvoNome;
    if(salvoSaldo) document.getElementById('saldo-display').innerText = salvoSaldo;
};

function aplicar() {
    const nome = document.getElementById('in-nome').value;
    const saldo = parseFloat(document.getElementById('in-saldo').value);

    if (nome) {
        const nomeFormatado = nome.toUpperCase();
        document.getElementById('nome-titular').innerText = nomeFormatado;
        localStorage.setItem('nome', nomeFormatado); // Salva o nome
    }

    if (!isNaN(saldo)) {
        const saldoF = saldo.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
        document.getElementById('saldo-display').innerText = saldoF;
        localStorage.setItem('saldo', saldoF); // Salva o saldo
    }
    toggleGerador();
}
