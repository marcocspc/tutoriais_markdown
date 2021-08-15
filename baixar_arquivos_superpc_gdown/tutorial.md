# Como baixar arquivos no super-computador do NPAD utilizando o gdown

## Tutorial

- Este tutorial leva em conta que você já tem acesso ao supercomputador do npad. Se não souber, consulte [este](http://npad.ufrn.br/tutoriais/introducaoSupercomputador-parte1-windows.php) link para Windows ou [este](http://npad.ufrn.br/tutoriais/introducaoSupercomputador-parte1-linux.php) para Linux.

1. Após acessar o supercomputador com ssh, você deve carregar o Python para poder instalar a ferramenta necessária para baixar arquivos do Google Drive na sua pasta pessoal. Para isso, faça:

`$ module avail |& grep python`

2. A saída no momento da escrita deste tutorial foi a seguinte:

```
softwares/cutadapt/1.18-gnu7.3-python3.6
softwares/python/2.7-anaconda-5.0.1
softwares/python/2.7.13-gnu-4.8
softwares/python/2.7.13-gnu-4.8_sh_lib
softwares/python/3.6-anaconda-5.0.1
softwares/python/3.6.1-gnu-4.8
softwares/python/3.6.3-gnu-4.8_sh_lib
```

3. Pode-se verificar que existem várias versões de Python disponíveis. No contexto deste tutorial o que se quer é a versão 3 do interpretador. Então pode ser escolhida a versão 'softwares/python/3.6.1-gnu-4.8' e carregá-la, da seguinte forma:

`$ module load softwares/python/3.6.1-gnu-4.8`

4. Após isso, para realizar a instalação da ferramenta gdown de forma isolada, em um ambiente separado, precisamos criar uma área virtual. Para isso instalamos o virtualenv da seguinte forma:

`$ python3 -m pip install virtualenv`

5. Enfim criamos nosso ambiente virtual. Recomenda-se fazer isso em uma pasta específica, da seguinte forma:

```
$ mkdir $HOME/envs
$ cd $HOME/envs
$ python3 -m virtualenv gdown
```

6. Após a criação do ambiente, deve-se ativá-lo. Da seguinte forma:

`$ source $HOME/envs/gdown/bin/activate` 

7. Enfim, podemos instalar o gdown. Para isto, podemos utilizar o pip3, que realizará a instalação no nosso ambiente virtual:

`$ pip3 install gdrive`

8. Após realizada a instalação, pode-se fazer o download do arquivo desejado utilizando o programa. No entanto, é necessário compreender como *converter* o link para o formato que o gdown compreende. Em geral, os links compartilhados do google drive estão no formato "https://drive.google.com/file/d/<XXX>/view?usp=sharing", onde <XXX> é o ID do arquivo a ser baixado. Com posse do ID, você deve reescrever a URL da seguinte forma: "https://drive.google.com/uc?id=<XXX>". Por fim, para realizar o download do arquivo, pode-se proceder da seguinte maneira:

`$ gdown https://drive.google.com/uc?id=<XXX>`

9. O arquivo será baixado para o diretório atual.

## Observações e dicas

- Caso o download não esteja ocorrendo de forma satisfatória, verifique se as permissões no google drive estão configuradas para que qualquer pessoa com o link possa visualizar o arquivo. Para isso, no Google Drive, clique com o botão direito no arquivo > Compartilhar. Na parte de baixo, clique em "alterar para qualquer pessoa com o link" e copie o link exibido.

- Você pode pedir para o próprio gdown realizar a conversão do link para você. Basta executar o comando:

`$ gdown https://drive.google.com/file/d/<XXX>/view?usp=sharing`

- Ele deverá retornar a seguinte saída:

```
UserWarning: You specified Google Drive Link but it is not the correct link to download the file. Maybe you should try: https://drive.google.com/uc?id=<XXX>
```

- O link ao final da linha será a conversão requisitada.

- Para mais ajuda com o gdown, basta seguir [este](https://github.com/wkentaro/gdown) link.

