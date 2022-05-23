# GameEngine-N2
Repositório para entrega do trabalho Game Engine N2

## Restauração de Saúde

### custom event Healing
Evento responsável por aumentar a vida do player, possui uma variável de entrada float chamada ToHeal. Se o jogador estiver morto, ou se a vida estiver no máximo, nada acontece.

![image](https://user-images.githubusercontent.com/78811958/168908691-25cba7b2-acd1-4a45-b4ba-e080183df8e4.png)

### Healing(press)
Chama o evento healing apenas uma vez quando a tecla(J) é precionada.

![image][https://user-images.githubusercontent.com/78811958/168909075-34db758d-af37-4653-8784-ad23b0f4ef95.png]

![image](https://im3.ezgif.com/tmp/ezgif-3-b5af3ac389.gif)


### Healing(hold)
Comportamento responável por recuerar o valor de vida do player em decorrencia do tempo, enquanto um tecla(H) está precionada. Com o input da tecla, a variável (bool)is_h_hold é definida como true, e é chamado o custom event H_pressed. No H_pressed é chamado o evento **Healing**, em seguida acontece um atraso de 0,1 segundos, se is_h_press for verdadeiro e vida for menor que a vida máxima, é chamado o custom event H_Pressed e o loop é repetido, se não o loop é quebrado. Quando a tecla é solta, is_h_pressed é definida como falsa.

![image](https://user-images.githubusercontent.com/78811958/168911320-7a794d62-5f92-4729-b933-f257402cc23d.png)

## Actions

### Jump

![image](https://im3.ezgif.com/tmp/ezgif-3-1a873302a4.gif)

Comportamento de pulo. Com o InputAction Jump, se o player está no chão e energia for maior que 0.25f e não estiver atacando, é chamado a função do componente Movimento do Personagem e a energia é decrementada em 0.25f.

![image](https://user-images.githubusercontent.com/78811958/168912229-fd700c47-4885-428c-81d6-9fdebbb83190.png)

### Attack
![image](ttps://im3.ezgif.com/tmp/ezgif-3-ca796c81a5.gif)
Comportamento de ataque. Com o InputAction Atack sse a enregia for maior que 0.25f e não estiver atacando, ocorre uma sequencia de 0 a 1. A 0 seria o começo do ataque, is_atacking é definifa como true, a energia é decrementada em 0.25f e a velocidade máxima do jogador é definida para 0. O 1 seria a duração e o fim do pulo, é chamado um atraso de 1.2 segundos, com o fim desse atraso, is_atacking é definida como false e a velocidade máxima do jogador retorna ao normal, para 600.0f.

![image](https://user-images.githubusercontent.com/78811958/168913119-82049a3b-4766-4b79-abc2-f224505c6f34.png)

# Take Damage
Controle de dano recebido e morte.

![image](https://im3.ezgif.com/tmp/ezgif-3-d1c888deb9.gif)

## custom event Take Damage
Recebe como entrada uma variável float damageToTake, se is_dead for falso, a vida é decrementada no valor de damageToTake, se a vida for menor que ou iguak a 0, é chamado o evento Death e isDead é igual a true.

![image](https://user-images.githubusercontent.com/78811958/168917771-8d680f71-886a-494f-b97c-003064c84320.png)

## custom event Death
É chamado a função Definir Simukar Física da  malha esquelética como true, e a movimentação e desabilitada. A predefinição de colisão da malha esquelética deve ser igual a Ragdoll.

![image](https://user-images.githubusercontent.com/78811958/168915126-32e829ff-965b-47d5-bada-1d45583209be.png)

## Eventos de dano
Quando a tecla é apertada(f), é chamado o evento Take Damage com a entrada de 0.25f.

![image](https://user-images.githubusercontent.com/78811958/168928014-5713630f-0b8a-40d1-ba25-373c1eafd3fd.png)

Quando a tecla é apertada(k), é chamado o evento Take Damage com a entrada de 1f, ou seja, o player irá morrer de qualquer jeito.

![image](https://user-images.githubusercontent.com/78811958/168928034-1c96222a-652f-42f0-b234-bb91a00e33a7.png)
