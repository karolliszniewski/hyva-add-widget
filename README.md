Dla Hyva, najlepiej dodać widget przez layout XML. Oto jak to zrobić:

Najpierw stwórz plik layout XML w swojej temie Hyva:

`app/design/frontend/Vendor/hyva-theme/Magento_Catalog/layout/catalog_product_view.xml`

Dodaj następującą zawartość:

```xml
<?xml version="1.0"?>
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
      xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <body>
        <referenceContainer name="hyva.product.info.main">
            <!-- Dla widgetu CMS Page Link -->
            <block class="Magento\Cms\Block\Widget\Page\Link"
                   name="custom.cms.link.widget"
                   template="Magento_Cms::widget/link/link_block.phtml">
                <arguments>
                    <!-- Tu dodaj argumenty widgetu -->
                    <argument name="title" xsi:type="string">Test Link</argument>
                    <argument name="page_id" xsi:type="string">your-cms-page-id</argument>
                </arguments>
            </block>
        </referenceContainer>
    </body>
</page>
```
Możesz też stworzyć własny template dla widgetu w:

`app/design/frontend/Vendor/hyva-theme/Magento_Cms/templates/widget/link/link_block.phtml`

Zawartość template'a:

```php
<?php
/** @var \Magento\Cms\Block\Widget\Page\Link $block */
?>
<div class="cms-page-link-widget">
    <a href="<?= $block->escapeUrl($block->getHref()) ?>" 
       class="text-primary hover:text-primary-darker">
        <?= $block->escapeHtml($block->getTitle()) ?>
    </a>
</div>
```
Możliwe lokalizacje dla widgetu w Hyva:
```xml
<!-- Pod głównym tytułem produktu -->
<referenceContainer name="hyva.product.info.main">

<!-- W szczegółach produktu -->
<referenceContainer name="hyva.product.details">

<!-- W sekcji mediów produktu -->
<referenceContainer name="hyva.product.media">

<!-- Pod główną treścią produktu -->
<referenceContainer name="content">
```
Po dodaniu:

Wyczyść cache: bin/magento cache:clean
Odśwież pliki statyczne: bin/magento setup:static-content:deploy

Dla innych typów widgetów trzeba odpowiednio dostosować klasę bloku i template. Który konkretnie widget chcesz dodać? Mogę pokazać bardziej szczegółowy przykład dla konkretnego przypadku. CopyRetryClaude does not have the ability to run the code it generates yet.
