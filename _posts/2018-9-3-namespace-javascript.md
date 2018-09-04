---
published: true
layout: post
title: Utilizando Namespaces no Javascript!
---
	Conforme o desenvolvimento se torna mais complexo, surge a necessidade de agruparmos as funcionalidades do código em pacotes. Inclusive criando subpacotes relacionados, chamados namespaces, muito conhecidos em linguagens como Python e Java.
	Porém o que algumas pessoas não sabem é que esta técnica também pode ser utilizada em Javascript.<br />
Como os objetos do JS não apenas conjuntos de elementos, que podem inclusive ser outros objetos, podemos criar uma estrutura de namespaces de forma simples seguindo o formato:

```javascript
	<script>
    window.criaNamespace = function(str) {
    	/**
        	Cria namespaces de acordo com a str informada.
            @param {String} str - Nome do novo namespace a ser criado, separando pacotes por '.'
        */
        var lst = str.split('.'),
        	chk = /^\(\{\}\)$/,
        	idx = window;
        if (lst[0] == 'window') lst.shift() //Não é necessário iniciar o namespace com window.
        for (var i = 0; i < lst.length; i++) {
        	if (idx[lst[i]] === null) {
            	idx[lst[i]] = {};
            	idx = idx[lst[i]];
        	} else if(chk.test(idx[lst[i]].toSource()) {
            	idx = idx[lst[i]];
            } else {
            	console.log("O nome " + lst[i] + " do namespace " + str + " ja é uma propriedade em uso");
            	return;
            }
        }
    }
    </script>
```
    Não há necessidade de retornar o namespace criado, uma vez que todos irão partir do objeto window que é global. Um fator interessante a ser levado em consideração no código, é a variável chk. No nosso código, não queremos gerar o mesmo problema que pode acontecer quando criamos namespaces manualmente, que é: você cria um namespace com vários métodos e depois em outro script, você define novamente o namespace e perde todos os métodos que foram implementados. 
    Para que isso não aconteça, temos que checar se um dos elementos da string do namespace já existe no nosso objeto window. E é nessa hora que o javascript pode dar algumas dores de cabeça: como checar se um objeto é um elemento object?
    Primeiramente, podemos pensar da forma mais simples: o método build in: typeof, que retorna exatamente o tipo da variável. Mas ai temos o problema com os seguintes testes:
    Objetos null, arrays, strings criadas no formato new String(), e números criados com new Number(), além dos objetos, retornam todos o typeof 'object'!!!
    Depois poderiamos pensar em testar uma propriedade específica, como por exemplo: Arrays tem a propriedade length. Porém, isso não é garantido, por que essas propriedades podem ser definidas dentro de um objeto comum. A saída neste método foi o método toSource() que retorna o construtor do objeto. No caso de um objeto, é a string '({})'.
    Fora isso, o método não é complicado, apenas dividimos a string através do '.', e se for colocado o namespace window no começo ele é removido para que não seja criado um namespace como window.window.pacote.
    Depois a lista é percorrida e os objetos são criados recursivamente. Se um dos objetos já existe, ele não é sobrescrito. Se for encontrado algum nome que já exista e não é um objeto e sim uma propriedade, enviamos uma mensagem de erro e paramos a execução. Você pode modificar o método para lançar uma exceção, ou testar o caminho do namespace antes de criá-lo.
    
