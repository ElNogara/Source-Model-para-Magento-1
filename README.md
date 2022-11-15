Para dar continuidade é necessário que entenda <a href="https://github.com/ElNogara/Primeiro-Modulo-Magento-1">como criar um módulo no Magento 1</a> e também ter conhecimento de <a href="https://github.com/ElNogara/System-Campos-de-configuracao-Magento-1">como criar seus campos no admin do Magento 1</a>.

<h1>Source Model Para Magento 1</h1>
</br>
Alguns campos criados no system.xml do Magento 1 utilizam um array de valores como 'values' e para que possuam isso é necessário setar um Source Model no momento de declara-los.

<h2>Source Models padrões do Magento 1</h2>
O magento contém varios Models que nos retornam um array para utilizarmos nos nossos campos, sendo eles:

<strong>Allregion.php</br>
Category.php</br>
Checktype.php</br>
Country.php</br>
Currency.php</br>
Website.php</br>
Yesno.php</br>
Enabledisable.php</br>
Entre outros...</br></strong>

O que todos eles tem em comum? É que todos possuem a função <strong>toOptionArray</strong> onde por padrão o Magento pega o retorno dessa função para ser utilizado nos seus campos de admin.

<h2>Como criar meus próprios Source Models?</h2>
É bem simples, você só precisa ter um Model dentro do seu módulo que possua a função <strong>toOptionArray</strong> e retorne um array com opções como exemplo abaixo o mais simples de todos Yesno:

```
    public function toOptionArray()
    {

        return array( //Array com as opções que será retornado.
            0 => Mage::helper('adminhtml')->__('No'),
            1 => Mage::helper('adminhtml')->__('Yes'),
        );
    }
```

Abaixo estou criando meu próprio Model, dentro do meu módulo Elnogara_Sistemaconfig. Criei a pasta Model e o arquivo dentro dela chamado de Yesorno.php:

```
<?php

class Elnogara_Sistemaconfig_Model_Yesorno extends Mage_Core_Model_Abstract{
    
    public function toOptionArray()
    {
        $valores = array( 
            0 => Mage::helper('adminhtml')->__('Wellington'),
            1 => Mage::helper('adminhtml')->__('Nogara'),
        );

        return $valores;
    }
}
```

Além de criar o Model é necessário referênciar a minha pasta 'Model' dentro do meu config.xml:
```
<?xml version="1.0" encoding="UTF-8"?>
<config>
    <modules>
        <Elnogara_Sistemaconfig>
            <version>1.0.0</version>
        </Elnogara_Sistemaconfig>
    </modules>
    <global>
	 <models>
	     <nogarasystem>
	          <class>Elnogara_Sistemaconfig_Model</class>
	     </nogarasystem>
	 </models>
     </global>
</config>
```

Feito isso, é necessário pegarmos esse caminho e inserir na declaração do campo que vai utilizar esse Source Model criado por nós:

![image](https://user-images.githubusercontent.com/50090354/201718392-8777ca8a-065d-42f1-97b7-8bb0c030b472.png)

Observe, que o caminho informado é 'nogarasystem/Yesorno' onde eu informei o apelido da minha pasta Model dentro do meu módulo e o nome do arquivo.

Minha função vai me retornar um array com duas opções, sendo elas 'Wellington' e 'Nogara' onde respectivamente seus 'values' são 0 e 1. Dentro do meu campo criado no meu admin, ficará exibido da seguinte forma:

![image](https://user-images.githubusercontent.com/50090354/201716136-cd9c1ab5-e7ce-43af-bc52-16d8d259880d.png)

<strong>Espero muito ter ajudado. Mas qualquer dúvida estou a disposição - <a href="https://wellingtonnogara.com/" style="color: red;">Wellington Nogara</a>.</strong>
