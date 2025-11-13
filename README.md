# Kernel – Perguntas e Respostas

## O que é um Kernel?
O **kernel** é o **núcleo do sistema operacional**, responsável por fazer a ponte entre **hardware** e **software**, controlando os recursos do sistema.

---

## O que o kernel faz?

### 1. Como o kernel gerencia recursos de hardware?
O kernel controla:
- Uso da CPU  
- Memória RAM  
- Acesso a dispositivos (teclado, mouse, disco, placa de rede)

Ele garante que cada programa utilize o hardware corretamente e sem conflitos.

---

### 2. Como o kernel fornece uma interface entre hardware e software?
Os programas **não acessam o hardware diretamente**.  
Eles fazem chamadas ao kernel, que traduz essas solicitações para operações que o hardware consegue executar.

Isso garante segurança e estabilidade.

---

### 3. Como o kernel controla processos e memória?
Ele é responsável por:
- Criar e encerrar processos  
- Gerenciar qual processo usa a CPU (escalonamento)  
- Trocar processos da memória para o disco (memória virtual)  
- Garantir que um processo não interfira em outro

---

### 4. Como o kernel gerencia o sistema de arquivos?
O kernel controla:
- Criação, leitura e exclusão de arquivos  
- Permissões de acesso  
- Montagem de partições e dispositivos de armazenamento  

Ele garante que os dados sejam lidos e gravados de forma segura.
