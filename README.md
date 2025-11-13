# Kernel – Relato Técnico Completo

## Qual foi a versão do kernel que você compilou, e por que escolheu essa versão?
Compilei a versão **6.1.0**, uma versão LTS bastante estável e amplamente utilizada em ambientes de produção.  
Escolhi essa versão porque ela oferece uma excelente combinação de estabilidade, compatibilidade com hardware mais recente e suporte prolongado. Além disso, possui melhorias importantes no gerenciamento de processos e otimizações de desempenho que não estavam presentes no kernel padrão da minha distribuição.

---

## Que configuração você modificou no menuconfig? Por que fez essa modificação? O que espera que essa modificação altere no comportamento do sistema?
Na configuração do `menuconfig`, desativei módulos relacionados a sistemas de arquivos que não utilizo, como o ReiserFS e o JFS, e também removi alguns drivers de áudio e rede que não são compatíveis com meu hardware.

Fiz essa modificação para:
- Reduzir o tamanho final do kernel  
- Diminuir o tempo de inicialização  
- Evitar o carregamento desnecessário de módulos que nunca serão usados  

Com isso, espero que o sistema tenha:
- Um boot mais rápido  
- Menos consumo de memória  
- Menos pontos potenciais de falha, devido à redução de componentes desnecessários  

---

## Durante a compilação você encontrou algum erro, advertência ou comportamento inesperado? Como resolveu ou o que faria para resolver?
Encontrei um erro logo no início: o `make menuconfig` não abriu porque a biblioteca `libncurses` não estava instalada.  
Resolvi isso rapidamente instalando a dependência.

Durante a compilação, surgiram alguns warnings referentes a módulos antigos marcados como deprecated, mas nenhum deles interrompeu o processo. Se algum warning tivesse se transformado em erro, eu teria revisado o arquivo `.config` e desabilitado os módulos problemáticos.

---

## Quais os riscos e benefícios de “rodar” um kernel compilado por você mesmo em comparação com usar o kernel padrão da distribuição?

**Benefícios:**
- Melhor desempenho por ter apenas os módulos necessários  
- Kernel mais leve e otimizado para o hardware específico  
- Possibilidade de incluir recursos novos antes da distribuição  
- Maior controle sobre segurança e comportamento interno do sistema  

**Riscos:**
- O sistema pode não inicializar se a configuração estiver incorreta  
- Maior necessidade de manutenção manual  
- Ausência de atualizações automáticas  
- Incompatibilidade com ferramentas da distribuição que dependem de módulos padrão  
- Possibilidade de introduzir falhas difíceis de diagnosticar  

---

## Em quais cenários você considera “vale a pena” compilar seu próprio kernel?

1. **Sistemas embarcados ou dispositivos IoT**  
   Onde o kernel precisa ser o mais enxuto possível para economizar recursos e melhorar o desempenho.

2. **Servidores de alta performance**  
   Onde cada milissegundo importa, e remover módulos desnecessários ajuda a reduzir latência e aumentar estabilidade.

Outros cenários incluem pesquisa acadêmica, aprendizado sobre sistemas operacionais e suporte a hardware muito novo que a distribuição ainda não reconhece.

---

## Se o sistema não inicializar após a compilação/instalação do kernel, qual seria seu plano de contingência para recuperar o sistema?

Se o novo kernel falhasse ao inicializar, meu plano seria:

1. Tentar inicializar usando o kernel antigo disponível no GRUB.  
2. Caso isso não funcionasse, utilizaria um Live USB Linux para:
   - Montar a partição raiz  
   - Verificar a pasta `/boot`  
   - Remover ou substituir o kernel defeituoso  
   - Corrigir as entradas do GRUB se necessário  
3. Reinstalar o kernel padrão da distribuição para restaurar o funcionamento básico.  
4. Revisar o arquivo `.config` e recompilar o kernel com configurações mais seguras.

Assim, garantiria que o sistema fosse recuperado mesmo após uma falha crítica.
