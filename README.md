<h1>Source Model Para Magento 1</h1>
</br>
Alguns campos criados no system.xml do Magento 1 utilizão um array de valores como 'values' e para que possuam isso é necessário setar um Source Model no momento de declara-los.

<h2>Source Models padrões do Magento 1</h2>
O magento já contém varios Models que nos retornem um array para utilizarmos nos nossos campos, sendo eles:

<strong>Allregion.php</br>
Category.php</br>
Checktype.php</br>
Country.php</br>
Currency.php</br>
Website.php</br>
Yesno.php</br>
Enabledisable.php</br>
Entre outros...</br></strong></br>

O que todos eles tem em comum? É que todos possuem a função <strong>toOptionArray</strong> onde por padrão o Magento pega o retorno dessa função para ser utilizado nos seus campos campos de admin.


