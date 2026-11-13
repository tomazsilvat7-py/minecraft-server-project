
# Instalação do Servidor Minecraft

Este documento apresenta as etapas utilizadas
para instalar e configurar o servidor Minecraft
em um ambiente computacional com Debian 13.

## 1. Pré-requisitos

- Computador hospedeiro.
- Rede:Conexão via **cabo Ethernet** (evite Wi-Fi para evitar lag e perda de pacotes).
- Pendrive: Mínimo de 4 GB com a imagem `debian-13.x.x-amd64-netinst.iso` gravada.

## 2. Instalação do Debian 13
## ⚙️ 2.1 Configuração da BIOS/UEFI e Boot

1. Insira o pendrive bootável na máquina física desligada.
2. Ligue o computador e pressione repetidamente a tecla de acesso à **BIOS/UEFI** ou ao **Menu de Boot** (geralmente `F2`, `F12`, `Del` ou `Esc`, dependendo do fabricante).
3. **Ajustes recomendados na BIOS/UEFI:**
   * **Fast Boot (Inicialização Rápida):** Desative (`Disabled`).
   * **Secure Boot:** O Debian 13 possui suporte nativo, mas caso enfrente problemas com drivers proprietários (como placas NVIDIA), desative (`Disabled`).
   * **Modo SATA/Storage:** Certifique-se de que esteja em `AHCI` (evite `RAID` ou `Intel RST`, pois podem ocultar o SSD/HD no instalador).
4. Selecione o pendrive como dispositivo principal de inicialização e salve as alterações (`F10`).

---

## 🚀 2.2. Passo a Passo da Instalação

Quando o menu inicial do Debian aparecer, selecione **`Graphical install`** (Instalação Gráfica) e pressione `Enter`.

### Etapa 1: Localização e Teclado
1. **Idioma:** Selecione `Portuguese (Brazil)` (Português do Brasil).
2. **Localização:** Selecione `Brasil`.
3. **Mapa de teclado:** Selecione `Português (Brasil)` (padrão ABNT2) ou `Inglês (EUA)` caso seu teclado não tenha a tecla `Ç`.

### Etapa 2: Configuração de Rede
1. **Placa de rede:** Caso tenha cabo Ethernet e Wi-Fi, dê preferência ao cabo (`eth0` ou `enp...`) para maior estabilidade. Se usar Wi-Fi, selecione sua rede e digite a senha.
2. **Nome da máquina (Hostname):** Defina um nome para o computador na rede (ex: `minecraft` ou `mc-server`).
3. **Nome de domínio:** Deixe em branco (a menos que esteja em uma rede corporativa) e clique em *Continuar*.

### Etapa 3: Usuários e Senhas
1. **Senha do Root (Administrador):**
   * *Dica:* Se você **deixar em branco**, o instalador desativa o login direto como `root` e dá permissões de administrador (`sudo`) automaticamente ao seu usuário comum. Se definir uma senha, terá que configurar o `sudo` manualmente depois.
2. **Nome completo do usuário:** Digite seu nome.
3. **Nome de usuário da conta:** Digite seu login em letras minúsculas e sem espaços (ex: `joao`).
4. **Senha do usuário:** Crie e confirme uma senha forte.
5. **Fuso horário:** Selecione seu estado para ajustar o relógio do sistema.

### Etapa 4: Particionamento de Disco
⚠️ *Atenção: Esta etapa apaga os dados do disco selecionado.*

1. Escolha o método **`Assistido - usar o disco inteiro`** (para iniciantes ou instalação limpa).
2. Selecione o HD ou SSD físico onde o sistema será instalado.
3. No esquema de particionamento, escolha **`Todos os arquivos em uma partição`** (recomendado para uso pessoal) ou **`Partição /home separada`** (ideal para manter seus arquivos pessoais intactos em futuras formatações).
4. Revise o resumo das partições criadas (EFI, raiz `/` e `swap`) e selecione **`Finalizar o particionamento e escrever as mudanças no disco`**.
5. Confirme marcando **`Sim`** e clique em *Continuar*.

### Etapa 5: Gerenciador de Pacotes e Softwares
1. **Mídia adicional:** Quando perguntar se deseja ler outra mídia de instalação, marque **`Não`**.
2. **Espelho de rede (Mirror):** Selecione `Brasil` e escolha o servidor `deb.debian.org`. Deixe o proxy HTTP em branco e avance.
3. **Popularity-contest:** Escolha se deseja enviar estatísticas anônimas de uso de pacotes (`Sim` ou `Não`).
4. **Seleção de Software (`tasksel`):**
   * Desmarque **`Ambiente de área de trabalho Debian`** (para deixar o sistema em terminal puro e melhorar o desempenho do servidor).
   * Deixe marcado **`utilitários padrão do sistema`**.
   * Marque `servidor SSH` para controlar o servidor remotamente pela rede.
   * Clique em *Continuar* e aguarde o download e instalação dos pacotes.

### Etapa 6: Gerenciador de Inicialização (GRUB) e Conclusão
1. Caso o instalador pergunte se deseja instalar o carregador de inicialização **GRUB** no registro mestre, marque **`Sim`** e selecione o disco rígido principal (ex: `/dev/sda` ou `/dev/nvme0n1` — **nunca** selecione o pendrive).
2. Ao ver a mensagem **"Instalação completada"**, remova o pendrive da porta USB e clique em **`Continuar`** para reiniciar a máquina.

## 3. Instalação das ferramentas

Descreva a instalação e verificação
do ambiente Java.

## 5. Instalação do Minecraft Forge

Explique como foi instalado o Forge 1.20.1
e como os arquivos do servidor foram preparados.

## 6. Primeiro teste

Descreva como o servidor foi iniciado
pela primeira vez e quais testes foram realizados.

## 7. Considerações finais

Registre o resultado da instalação e
eventuais problemas encontrados.
