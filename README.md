# Kernel – Relato Técnico Resumido

## Qual foi a versão do kernel que você compilou, e por que escolheu essa versão?
Compilei o kernel **6.1.0 LTS** por ser estável, bem suportado e trazer melhorias importantes de desempenho e segurança em relação ao kernel padrão da distribuição.

---

## Que configuração você modificou no menuconfig? Por que fez essa modificação?
Desativei drivers e sistemas de arquivos que não uso (como ReiserFS, JFS e drivers antigos).  
Fiz isso para reduzir o tamanho do kernel, acelerar o boot e evitar carregamento desnecessário de módulos.

---

## Durante a compilação você encontrou algum erro? Como resolveu?
Sim. O `menuconfig` não abriu por falta da biblioteca `libncurses`.  
Instalei a dependência e a compilação prosseguiu normalmente.  
Os demais alertas eram apenas warnings de módulos antigos.

---

## Riscos e benefícios de rodar um kernel compilado por você mesmo

**Benefícios:**  
- Kernel mais leve e rápido  
- Melhor desempenho  
- Suporte a recursos e drivers mais novos  

**Riscos:**  
- Sistema pode não inicializar  
- Atualizações e manutenção são manuais  
- Possível incompatibilidade com ferramentas da distribuição  

---

## Em quais cenários vale a pena compilar seu próprio kernel?
- Sistemas embarcados/IoT que precisam de kernel mínimo  
- Servidores que exigem o máximo desempenho  
- Hardware muito recente sem suporte no kernel padrão  

---

## Plano de contingência caso o sistema não inicialize
- Inicializar pelo kernel antigo via GRUB  
- Usar Live USB para montar o sistema e remover o kernel quebrado  
- Reinstalar o kernel padrão da distribuição  
- Revisar o `.config` e recompilar com opções mais seguras
