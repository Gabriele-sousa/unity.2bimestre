# unity.2bim
Esse é um projeto solicitado pela Orientadora Aline Firmino, com o objetivo de aprender a usar assets, scripts e fisica em uma cena no Unity.

## Requisitos 
Para ver essa cena é necessario o Unity com a versão 2022.2.15f1

## Instalação 
1. Clonar o projeto `https://github.com/Gabriele-sousa/unity.2bim.git`.
2. Abrir o projeto no Unity.

## Desenvolvimento
Para criar esse projeto foram utilizados os seguintes passos:
1. Baixar assets na asset store.
 * Esses foram os assets baixados para o projeto
 <img src="img/3.png"/>
2. Colocar os game objects na cena.
 * Para a cena foi adicionados Arvores, Presentes, Bonecos de neve e Obstáculos.
 <img src="img/1.png"/>
 
 * Colocar o personagem que irá receber os scripts e a camera dentro da pasta do personagem, tambem será necessario colocar um rigidbody e um box collider para que o personagem não caia direto no void ou fique flutuando. 
 <img src="img/2.png"/>
 
3. Criar os scripts e programar
 * Foram criados dois scripts.
 <img src="img/4.png"/>
 
 - Programando o andar 
   - Para fazer o Pinguim andar no script foi adicionado `if (Input.getKey (KeyCode.W))` e `transform.Translate (0.0f, 0f, 0.01f);` e para o fazer andar pra frente e o mesmo código mas com o `(KeyCode.S)` e o `transform.Translate (0.0f, 0, -0.01f);`.
   - Para fazer o Pinguim olhar para o lado foi adicionado `if (Input.getKey (KeyCode.D))` e `transform.Rotate (0.0f, 0.2f, 0f)` e para fazer o pinguim olhar pro outro lado `if (Input.getKey (KeyCode.A))` e o `transform.Rotate (0.0f, 0.2f, 0f);`.
   - O código final fica assim 
 <img src="img/5.png"/>
 
 4. Programando o playerjump
 * Primeiro requisitamos o componente RigidBody
 * Depois usaremos uma variável que controla força do pulo `public float jumpForce = 3.0;` e colocaremos uma variável que controla a massa/peso `public float mass = 3.0f;`.
 * Depois acessamos o compenente Rigidbody atráves dessa variável `private Rigidbody rigidbody;`
 * Usaremos uma variável de controle que diz de se o personagem está no chão ou não `private bool isGround = false;`
 - Dento do `void Start()`
   - Assim que o script é executado,obtemos o componente Rigidbody e atribuimos a nossa variável `rigidbody = GetComponent<Rigidbody>();`
   - Definimos o valor da massa via script `rigidbody.mass = mass;`
 - Dentro do `void Update()`
   - É verificado se o usuário não precionou a tecla Space ou se não está no chão `if (!Input.GetKeyDown(keycode.Space) || !isGround)` e `return;`
   
   - Depois adicionamos uma força ao Rigidbody `rigidbody.AddForce(`
     - `Vector3.up * jumpforce,` Para fazer o personagem pular, então iremos multiplicar (0, 1, 0) pelo valor do pulo.
     - `ForceMode.Impulse` awui nós ajustamos a força para o tipo Impulse.

- Verifica se o personagem tocou no chão `void OnCollisonEnter(Collision collision)` e `isGround = true;` 
 
 - Verifica se o personagem saiu do chão `void OnCollisonExit(Collision collision)` e `isGround = false;` 
* O código final fica assim:
<img src="img/6.png"/>

## Autores
Gabriele Batista Sousa e Arthur Victor Sousa Mascate
