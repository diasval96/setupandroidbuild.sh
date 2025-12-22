# 📜 README – Script `setupandroidbuild.sh`

## 📖 Sobre
Este script foi criado para transformar qualquer celular Android moderno em um **ambiente de build** usando **Termux**.  
Ele instala todos os pacotes necessários, configura o Python e prepara o ambiente para que o **Buildozer** baixe automaticamente **SDK, NDK e Gradle** na primeira compilação.  

Com isso, você pode compilar **APKs Android em Python** diretamente no celular, sem precisar de Android Studio ou de um PC potente.

---

## 📦 O que o script instala
- **Pacotes Termux essenciais**: `git`, `python`, `clang`, `zip`, `unzip`, `libffi`, `openssl`, `libjpeg-turbo`, `freetype`, `sqlite`, `android-tools`  
- **Ferramentas Python**: `pip`, `setuptools`, `wheel`, `cython`  
- **Frameworks Python**: `kivy`, `kivymd`, `plyer`, `flask`, `buildozer`  
- **Configuração de armazenamento**: libera acesso ao `/sdcard` com `termux-setup-storage`  
- **Ambiente Android**: Buildozer baixa **SDK, NDK e Gradle** automaticamente na primeira compilação  

---

## 🛠️ Requisitos
- **Android 7.0 ou superior**  
- **Arquitetura arm64-v8a** (a maioria dos celulares modernos)  
- **Espaço livre**: pelo menos **5 GB** para SDK/NDK/Gradle  
- **Conexão estável**: primeira compilação consome entre **3–5 GB de internet**  

---

## 🚀 Como usar

1. Abra o Termux e crie o arquivo:
   ```bash
   nano setupandroidbuild.sh
   ```

2. Cole o conteúdo do script.
   ```bash
   #!/data/data/com.termux/files/usr/bin/bash
   # Script para configurar Termux como ambiente de build Android
   
   echo "🔧 Atualizando pacotes..."
   pkg update -y && pkg upgrade -y
   
   echo "📦 Instalando pacotes essenciais..."
   pkg install -y git python clang zip unzip libffi openssl libjpeg-turbo freetype sqlite android-tools
   
   echo "🐍 Atualizando pip e ferramentas Python..."
   pip install --upgrade pip setuptools wheel cython
   
   echo "🎨 Instalando frameworks Python..."
   pip install kivy kivymd plyer flask buildozer
   
   echo "📂 Configurando acesso ao armazenamento..."
   termux-setup-storage
   
   echo "✅ Ambiente pronto! Use 'buildozer init' para começar."
   ``` 

3. Dê permissão de execução:
   ```bash
   chmod +x setupandroidbuild.sh
   ```

4. Execute:
   ```bash
   ./setupandroidbuild.sh
   ```

---

## 📂 Estrutura esperada após execução
- Termux configurado com pacotes essenciais  
- Python atualizado com pip e bibliotecas instaladas  
- Buildozer pronto para inicializar projetos  
- Acesso liberado ao armazenamento interno  

---

## 🚀 Próximos passos
1. Crie um novo projeto:
   ```bash
   buildozer init
   ```
2. Edite o arquivo `buildozer.spec` conforme seu app.  
3. Compile:
   ```bash
   buildozer -v android debug
   ```
4. Instale o APK gerado:
   ```bash
   pm install bin/*.apk
   ```

---
