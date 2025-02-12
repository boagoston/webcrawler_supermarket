## Prova tecnica 

## Passo a passo para subir o conteiner Docker

Criar um arquivo chamado .env no mesmo diretorio do Dockerfile e adicionar os valores recolhidos ao logar no site servimed ao fazer o login com a DevTools aberta e olhar alguma requisição Fetch/XHR e recolher o accesstoken e os Cookies como na imagem abaixo 

ps: isso é necessario devido a dificuldade em gerar/recolher o accesstoken porem o processo de login e dos cookies é possivel observar no arquivo [crawler.py](https://github.com/boagoston/webcrawler_prova/blob/main/webcrawler_servimed/webcrawler_servimed/webcrawler_servimed/spiders/crawler.py)  

![enter image description here](https://i.imgur.com/Kwt9Ig2.png)

![enter image description here](https://i.imgur.com/nO0HSGB.png)

Conforme o exemplo acima, a env ficaria:

    ACCESS_TOKEN=02dbc370-dc61-11ef-8fbf-8ff4685df6b0
    
    COOKIES=sessiontoken=eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb2RpZ29Vc3VhcmlvIjoyMjg1MCwidG9rZW4iOiIwMmRiYzM3MC1kYzYxLTExZWYtOGZiZi04ZmY0Njg1ZGY2YjAiLCJpYXQiOjE3Mzc5NDk0NjksImV4cCI6MTczNzk5MjY2OSwiYXVkIjoiaHR0cDovL3NlcnZpbWVkLmNvbS5iciIsImlzcyI6IlNlcnZpbWVkIiwic3ViIjoic2VydmltZWRAU2VydmltZWQuY29tLmJyIn0.AYMWbjbv7tj6eJmF--wWrEqGbtjfAE__COokrXK8mFVL0KLoxoN9RLCDfk6vi2f_cyzpp6STce4cExsBbvWbFQ; accesstoken=eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb2RpZ29Vc3VhcmlvIjoyMjg1MCwidG9rZW4iOiIwMmRiYzM3MC1kYzYxLTExZWYtOGZiZi04ZmY0Njg1ZGY2YjAiLCJpYXQiOjE3Mzc5NDk0NjksImV4cCI6MTczNzk5MjY2OSwiYXVkIjoiaHR0cDovL3NlcnZpbWVkLmNvbS5iciIsImlzcyI6IlNlcnZpbWVkIiwic3ViIjoic2VydmltZWRAU2VydmltZWQuY29tLmJyIn0.AYMWbjbv7tj6eJmF--wWrEqGbtjfAE__COokrXK8mFVL0KLoxoN9RLCDfk6vi2f_cyzpp6STce4cExsBbvWbFQ

Execute o comando abaixo no mesmo local em que o **Dockerfile** está localizado

    docker build -t <nome_da_imagem> .

***não esquecer do " . " no final do comando***

Após isso é possivel verificar sua imagem construida  no docker utilizando o comando docker images, após isso confirmar o nome de sua imagem e executar o container com bash utilizando *docker run*:

    docker images

    sudo docker run -it <nome_da_imagem> bash

Com isso , se dermos um **ls** para confirmarmos os arquivos da pasta, teremos o resultado abaixo.

![enter image description here](https://i.imgur.com/9LjycDB.png)

Após este momento, as execuções serão separadas nos repectivos readme.md abaixo.

### Questão 1. **Web Crawler - Compra Agora**

Este projeto de web scraping utiliza Scrapy para extrair dados de produtos do site Compra Agora. O crawler coleta informações como nome, marca e URL da imagem dos produtos de várias categorias, além de salvar as URLs processadas em um arquivo `processed_urls.txt`. O login foi descartado pois os dados necessários podem ser extraídos sem autenticação. O script começa a coleta a partir das categorias do site e processa as páginas de produtos, exibindo logs no terminal.

[Mais detalhes no readme do projeto (Clique aqui)](https://github.com/boagoston/webcrawler_prova/blob/main/webcrawler_supermarket/README.md)

----------

### Questão 2. **Servimed - Web Scraping para Retorno de Faturamento**

Este scraper foi desenvolvido com Scrapy para coletar detalhes de pedidos do sistema da Servimed. Ele extrai informações como motivo de rejeição e itens do pedido (código, descrição e quantidade faturada), utilizando tokens de autenticação fixos. O script simula um navegador Chrome para evitar bloqueios de acesso e manipula requisições HTTP com a ajuda do middleware `CurlCffiMiddleware`. A saída é retornada no formato JSON e salva em um arquivo.

[Mais detalhes no readme do projeto (Clique aqui)](https://github.com/boagoston/webcrawler_prova/blob/main/webcrawler_servimed/webcrawler_servimed/readme.md)

### Questão 3. Fibonacci Recursivo

A solução esta no arquivo [fibonacci_recursivo.py](https://github.com/boagoston/webcrawler_prova/blob/main/fibonacci_recursivo.py)

Para execução, é só estar na raiz do Docker e rodar o comando abaixo, sendo n = numero_desejado

    python3 fibonnaci_recursivo.py <numero_desejado>



### Questão 4. 

O problema de calcular o 50º número de Fibonacci é uma tarefa clássica. A sequência de Fibonacci é uma sequência matemática em que cada número é a soma dos dois números anteriores. 

A forma mais simples de calcular esse número é com um código recursivo. Porém, isso pode ser ineficiente para valores grandes como **F(50)**. A sobrecarga no cálculo de Fibonacci, quando feita de forma recursiva sem otimizações, ocorre devido a uma repetição excessiva de cálculos. 

Por exemplo, para calcular F(5):

    F(5) = F(4) + F(3) 
	    F(4) = F(3) + F(2) 
		    F(3) = F(2) + F(1) 
			    F(2) = F(1) + F(0)

Aqui, F(3) e F(2) são recalculados várias vezes, o que torna a solução muito ineficiente. Essa repetição causa uma explosão no número de chamadas, e o tempo de execução cresce de forma exponencial. Para valores maiores de n, como F(50), isso se torna um problema sério.


#### Questão 5

-   **VPN e Subnets**:
    
    -   A VPN permite que você conecte redes de forma segura. Em uma infraestrutura de nuvem, você pode criar uma VPN para conectar a rede local da sua empresa a uma subnet privada na nuvem. Isso permite que dispositivos na sua rede local acessem recursos na nuvem de maneira segura, como se estivessem na mesma rede.
    -   Ao usar VPN, as subnets são importantes porque você precisa especificar quais subnets na nuvem devem ser acessíveis via VPN.
    
-   **VPN e Security Groups**:
    
    -   Quando você usa uma VPN para conectar sua rede local à nuvem, os **security groups** entram em cena para proteger as instâncias ou recursos na nuvem. A VPN cria um "túnel" de tráfego seguro, mas as regras de segurança (nos security groups) controlam qual tráfego pode acessar seus recursos.
    -   Por exemplo, um security group pode ser configurado para permitir tráfego somente da sua rede local (via VPN) , bloquear tráfego de outras redes, gerenciamento do acesso com niveis diferentes para estrutura.

-   **Subnets e Security Groups**:
    
    -   As subnets e os **security groups** trabalham juntos para isolar e proteger suas instâncias. A subnet define o "contexto" de rede (onde suas instâncias estão localizadas), enquanto os security groups controlam quem pode acessar essas instâncias.
    -   Você pode ter uma instância em uma subnet privada que só pode ser acessada de outras instâncias dentro da mesma subnet ou de instâncias em subnets públicas (se configurado com regras adequadas nos security groups).
    - um grupo de segurança atua como um firewall que controla o tráfego permitido de e para os recursos em sua nuvem privada virtual (VPC).