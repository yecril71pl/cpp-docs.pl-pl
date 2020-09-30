---
title: Odwoływanie się do właściwości w dostawcy
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: ecb11c54d4c5926fbead0196c441ec23e8b0891f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509515"
---
# <a name="referencing-a-property-in-your-provider"></a>Odwoływanie się do właściwości w dostawcy

Znajdź grupę właściwości i identyfikator właściwości dla właściwości, którą chcesz. Aby uzyskać więcej informacji, zobacz [OLE DB właściwości](/previous-versions/windows/desktop/ms722734(v=vs.85)) w **kompendium programisty OLE DB**.

W poniższym przykładzie założono, że próbujesz pobrać właściwość z zestawu wierszy. Kod służący do korzystania z sesji lub polecenia jest podobny, ale używa innego interfejsu.

Utwórz obiekt [CDBPropSet](../../data/oledb/cdbpropset-class.md) za pomocą grupy właściwości jako parametr do konstruktora. Na przykład:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

Wywołaj metodę [AddProperty](./cdbpropset-class.md#addproperty), przekazując ją do identyfikatora właściwości i wartości, która ma zostać przypisana do właściwości. Typ wartości zależy od używanej właściwości.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

Użyj `IRowset` interfejsu do wywołania `GetProperties` . Przekaż właściwość ustawioną jako parametr. Oto ostatni kod:

```cpp
CAgentRowset<CCustomCommand>* pRowset = (CAgentRowset<CCustomCommand>*) pThis;

CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;

DBPROPIDSET set;
set.AddPropertyID(DBPROP_BOOKMARKS);

DBPROPSET* pPropSet = NULL;
ULONG ulPropSet = 0;

HRESULT hr;

if (spRowsetProps)
   hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

if (pPropSet)
{
   CComVariant var = pPropSet->rgProperties[0].vValue;
   CoTaskMemFree(pPropSet->rgProperties);
   CoTaskMemFree(pPropSet);

   if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))
   {
      ...  // Use property here
   }
}
```

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
