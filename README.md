# Bypass IoT Environment

Um ambiente containerizado para o desenvolvimento do nosso app (nome do app).

📋 Requisitos

- Docker (Guia de Instalação)

- Docker Compose (geralmente incluso com o Docker)

- Linux/Windows/macOS (com suporte a Docker)


## 🚀 Executando o Projeto
**1. Iniciar os Containers**

Modo detached (segundo plano):
```
docker-compose up -d
```

Modo attached (logs no terminal):
```
docker-compose up
```

**2. Acessar os Serviços**

Container ArchLinux (para testes):
```
docker-compose exec archlinux bash
```

Outros Serviços (se definidos no docker-compose.yml):
Verifique as portas e acesse via http://localhost:<porta_mapeada>
```
docker-compose down
```

## 🔧 Solução de Problemas
**1. Container Sai Imediatamente**

  - Verifique se há um command mantendo-o em execução (ex: tail -f /dev/null).

  - Verifique os logs:
```
docker-compose logs archlinux
```

**2. Problemas de Permissão**
   
- Linux

Se o Docker retornar erros de permissão:
```
sudo chmod 666 /var/run/docker.sock  # Solução temporária (não recomendado para produção)  
```

Ou adicione seu usuário ao grupo docker:
```
sudo usermod -aG docker $USER && newgrp docker  
```

- Windows

Execute o Docker Desktop como administrador.

Verifique se o WSL2 está configurado corretamente (se estiver usando WSL).

3. Conflitos de Porta
- Linux/macOS

Verifique se a porta está em uso:
```
sudo netstat -tulnp | grep <porta>  # Linux  
lsof -i :<porta>                    # macOS  
```

- Windows

Verifique portas em uso no PowerShell:
```
netstat -ano | findstr "<porta>"
```

Altere a porta no docker-compose.yml se necessário.
