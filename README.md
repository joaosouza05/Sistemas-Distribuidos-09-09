import socket


servidor = socket.socket(
    socket.AF_INET,
    socket.SOCK_DGRAM
)

servidor.bind(("localhost", 5000))

print("Servidor UDP aguardando mensagens ... ")

dados, endereco = servidor.recvfrom(1024)

mensagem = dados.decode()

print("Cliente:", endereco)
print("Mensagem recebida:", mensagem)

resposta = "Mensagem recebida pelo servidor UDP!"

servidor.sendto(
    resposta.encode(),
    endereco
)
servidor.close()


import socket

cliente = socket.socket(
    socket.AF_INET,
    socket.SOCK_DGRAM
)


mensagem = input("Digite sua mensagem: ")

cliente.sendto(
    mensagem.encode(),
    ("localhost", 5000)
)
dados, endereco = cliente.recvfrom(1024)

print("Resposta do servidor:")
print(dados.decode())

cliente.close()
