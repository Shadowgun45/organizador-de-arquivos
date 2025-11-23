import os
import shutil

print("=== Organizador Automático de Arquivos ===\n")

# Usuário digita o caminho da pasta
caminho = input("Digite o caminho completo da pasta que você quer organizar:\n> ")

# Verifica se a pasta existe
if not os.path.isdir(caminho):
    print("\n❌ Erro: Essa pasta não existe. Verifique o caminho e tente novamente.")
    exit()

# Dicionário com tipos de arquivos e suas extensões
categorias = {
    "Imagens": [".png", ".jpg", ".jpeg", ".gif"],
    "Vídeos": [".mp4", ".mov", ".avi"],
    "Documentos": [".txt", ".docx", ".doc", ".pptx"],
    "PDFs": [".pdf"],
    "Executáveis": [".exe"],
    "Outros": []
}

# Criar pastas se não existirem
for pasta in categorias:
    caminho_pasta = os.path.join(caminho, pasta)
    if not os.path.exists(caminho_pasta):
        os.mkdir(caminho_pasta)

# Organizar arquivos
for arquivo in os.listdir(caminho):
    caminho_arquivo = os.path.join(caminho, arquivo)

    # Ignorar pastas
    if os.path.isdir(caminho_arquivo):
        continue

    # Pegar extensão
    _, extensao = os.path.splitext(arquivo)
    extensao = extensao.lower()

    # Verificar categoria
    movido = False
    for categoria, extensoes in categorias.items():
        if extensao in extensoes:
            shutil.move(caminho_arquivo, os.path.join(caminho, categoria, arquivo))
            print(f"✔ Movido: {arquivo} → {categoria}")
            movido = True
            break

    # Se não se encaixa → vai para "Outros"
    if not movido:
        shutil.move(caminho_arquivo, os.path.join(caminho, "Outros", arquivo))
        print(f"✔ Movido: {arquivo} → Outros")

print("\n🎉 Organização concluída!")
