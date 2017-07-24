## Path

~/Library/Preferences/PhpStorm20xx.x

## Commands

# -db
/* @var $db \Doctrine\DBAL\Connection */
$db = Shopware()->Container()->get('dbal_connection');

# -crud
/** @var \Shopware\Bundle\AttributeBundle\Service\CrudService $attributeService */
$attributeService = Shopware()->Container()->get('shopware_attribute.crud_service');

//Update here --crud--update

$modelmanager = Shopware()->Container()->get('models');
/** @var \Doctrine\Common\Cache\Cache $metaDataCache */
$metaDataCache = $modelmanager->getConfiguration()->getMetadataCacheImpl();
$metaDataCache->deleteAll();

$modelmanager->generateAttributeModels(
[
's_articles_attributes',
]
);

# -crud--update
$attributeService->update(
's_articles_attributes',
'product_label',
\Shopware\Bundle\AttributeBundle\Service\TypeMapping::TYPE_STRING,
            [
                'label'            => 'Produkt Label',
                'displayInBackend' => true,
                'custom'           => true,
            ]);