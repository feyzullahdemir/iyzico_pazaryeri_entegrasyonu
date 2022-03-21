# iyzico_pazaryeri_entegrasyonu
İyzico alt yapısını kullanrak pazaryeri entegrasyonu nasıl yapılır ? 

```PHP
$request = new \Iyzipay\Request\CreateSubMerchantRequest();
$request->setLocale(\Iyzipay\Model\Locale::TR);
$request->setConversationId(123456789);
$request->setSubMerchantExternalId('SubMerchant sistemimizdeki id değeri');
$request->setSubMerchantType(\Iyzipay\Model\SubMerchantType::PERSONAL);
$request->setAddress('adres bilgileri');
$request->setContactName('satıcı adı');
$request->setContactSurname('satıcı soyadı');
$request->setEmail('e-posta adresi');
$request->setGsmNumber('telefon numarası');
$request->setName('adı soyadı');
$request->setIban('satıcı iban numarası');
$request->setIdentityNumber('satıcı tc kimlik numarası');
$request->setCurrency(\Iyzipay\Model\Currency::TL);
# make request
$subMerchant = \Iyzipay\Model\SubMerchant::create($request, Config::options());
```
Satıcıyı create veya update yaptıktan sonra echo print_r($subMerchant); yaparak dönen değerleri görebiliriz.  echo $subMerchant->getStatus(); yaptığımızda success değeri dönüyorsa işlemimiz başarılı demektir.

$subMerchant->getSubMerchantKey(); ile satıcının SubMerchantKey değerini alıp  kaydedebilirsiniz.

Satış işlemi gerçekleşirken ise standart entegrasyondan farklı olarak sepet ürünlerini gönderirken ise satılan ürüne ait setSubMerchantKey ve setSubMerchantPrice değerlerini gönderiyoruz. setSubMerchantKey değeri  daha önce kaydettiğimiz satıcının id değerini, setSubMerchantPrice ise satıcıya ne kadar ödeme geçeceğini belirtiyor.
