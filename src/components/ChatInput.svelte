/***
*ANDREU
 * ChatInput component
 * Campo de texto com placeholder e botão de envio
 */

function abrir() {
    let janela = document.getElementById("janelaChat");

    if (janela.style.display === "block") {
        janela.style.display = "none";
    } else {
        janela.style.display = "block";
    }
}

function enviar() {
    let campo = document.getElementById("texto");
    let mensagem = campo.value.trim();

    // Impede mensagens vazias
    if (mensagem === "") {
        return;
    }

    let nova = document.createElement("div");
    nova.className = "mensagem";
    nova.textContent = mensagem;

    document.getElementById("mensagens").appendChild(nova);

    campo.value = "";

    let lista = document.getElementById("mensagens");
    lista.scrollTop = lista.scrollHeight;

    campo.focus();
}

document.addEventListener("keydown", function(e) {
    if (e.key === "Enter" &&
        document.activeElement.id === "texto") {
        enviar();
    }
});


const estilo = document.createElement("style");

estilo.textContent = `
#chat {
    position: fixed;
    bottom: 20px;
    right: 20px;
    font-family: Arial, sans-serif;
    z-index: 9999;
}

#abrirChat {
    background: #b8860b;
    color: white;
    border: none;
    border-radius: 50%;
    width: 55px;
    height: 55px;
    font-size: 24px;
    cursor: pointer;
}

#janelaChat {
    display: none;
    width: 280px;
    height: 350px;
    background: white;
    border-radius: 12px;
    box-shadow: 0 2px 15px #0005;
    margin-bottom: 10px;
    overflow: hidden;
}

#cabecalho {
    background: #b8860b;
    color: white;
    padding: 15px;
    font-weight: bold;
}

#mensagens {
    height: 235px;
    padding: 10px;
    overflow-y: auto;
    font-size: 14px;
}

#entrada {
    display: flex;
    padding: 8px;
    gap: 5px;
}

#texto {
    width: 100%;
    min-width: 0;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

#entrada button {
    background: #b8860b;
    color: white;
    border: none;
    padding: 8px;
    border-radius: 5px;
    cursor: pointer;
}

.mensagem {
    background: #eee;
    padding: 8px;
    margin-bottom: 8px;
    border-radius: 8px;
    overflow-wrap: anywhere;
}
`;

document.head.appendChild(estilo);


