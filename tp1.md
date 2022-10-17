# Trabalho Prático 1

## 1. Connectividade:

### a. Faça traceroute do Term2 para cada uma das interfaces do RLin.(outRes)
Usamos o comando ```traceroute``` para traçar o percurso até ao nó de destino (routers atravessados):

```bash
$ traceroute -n -N 1 170.2.0.3
```
(add image)

### b. Faça traceroute do Term1 para cada uma das interfaces do Term2 nas seguintes condições:

#### i. RCis2 sem rota para a rede 170.2.0.0/16 (outRes)
Removemos a rota ```107.2.0.0``` do ```RCis2```:

```bash
# no ip route 107.2.0.0 255.255.0.0 195.70.40.25
```

(add image do output do traceroute)

- É enviado um sinal a partir do ```Term1``` até ao ```Term2```.
- O sinal é recebido por ```RLin``` que responde por estarem ligados na mesma sub rede.
- O sinal chega a ```Term2``` e este ao enviar uma resposta, envia pela interface ```ens4``` e chega ao ```RCis2```. O sinal não consegue ser devolvido porque a rota ```195.70.40.25``` foi apagada, daí o output ```* * *```.

#### ii. RCis2 com rota para a rede 170.2.0.0/16 através de RCis1 (outRes); indique também o comando usado para criar a rota (confRes)
...

#### iii. RCis2 com rota para a rede 170.2.0.0/16 através de RLin (outRes)
...

### c. Desligue agora o RCis1 para simular que avariou e repita a alínea anterior.
NOTA: RCis1 deverá permanecer desligado para o resto do trabalho.

### d. Explique o que se passa em cada um dos casos na alínea anterior. (texRes)
...

### e. Tendo em conta as duas alíneas anteriores, identifique condições genéricas que tornam vantajoso o uso de encaminhamento dinâmico numa rede. Justifique. (texRes)
...

### f. Faça um traceroute do Term2 para o Term1 nas três condições indicadas na alínea b. (outRes)
...

### g. Tendo em conta os resultados da alínea anterior, seria útil ter encaminhamento dinâmico nos routers para conseguir resposta ao traceroute? Justifique.(texRes)
...

### h. Em RCis2, coloque a rota para a rede 170.2.0.0/16 através de RLin.
...

#### i. Inicie uma captura na ligação de Term2 à sub-rede 192.180.40.0/24; faça traceroute desse terminal para um endereço IP da rede 170.2.0.0/16 ao qual não corresponda nenhuma máquina. Repita o traceroute (a saída deve ser diferente; caso seja igual, repita os dois traceroutes com outro endereço IP). (outRes + capRes)
...

#### ii. Por que razão é diferente a saída do traceroute? (texRes)
...

## 2. ARP. Inicie uma captura na ligação de Term2 ao switch da sub-rede 192.180.40.0/24.
### a. Faça ping -c 1 192.180.40.55 e capture o resultado do ping. (capRes)
### b. Repita a alínea anterior para o endereço 192.180.40.3
### c. Comente os pacotes ARP e ICMP capturados nas alíneas anteriores, usando-os para explicar o funcionamento do protocolo ARP (incluindo timeouts e retransmissões). (texRes)

## 3. Faça as capturas indicadas nas alíneas seguintes definindo filtros para 'apanhar' apenas pacotes TCP, com a flag PUSH activa e com um comprimento do pacote IP menor que 128 bytes. Faça ssh do terminal 1 para a interface 192.180.30.44 do terminal 2.
NOTAS: Pode testar os filtros usando, na shell da máquina remota, a='#'; while true; do echo $a; sleep 1; a=$a'#'; done
Se não conseguir fazer ssh (“connection refused”), vá ao Term2 e corra o seguinte comando como root: systemctl start sshd.service
### a. Utilize o tcpdump no Term2, capturando em todas as interfaces (tcpdump -l -n -i any filtro) e indique o filtro usado. (confRes + capRes)
### b. Utilize o wireshark com filtro de visualização (captura na ligação de Term1 à rede) e indique o filtro usado. (confRes + capRes)
### c. Como se pode calcular o tamanho do campo de dados no pacote IP? (texRes)
