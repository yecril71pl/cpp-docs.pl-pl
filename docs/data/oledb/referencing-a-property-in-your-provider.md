---
title: Odwoływanie się do właściwości w dostawcy
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: 642e6219f72e506205e8192770be7d8af5d0d817
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556476"
---
# <a name="referencing-a-property-in-your-provider"></a>Odwoływanie się do właściwości w dostawcy

Znajdź grupy właściwości i Identyfikatora właściwości dla właściwości, które chcesz. Aby uzyskać więcej informacji, zobacz [właściwości OLE DB](https://docs.microsoft.com/previous-versions/windows/desktop/ms722734(v=vs.85)) w **OLE DB Podręcznik programisty**.

W poniższym przykładzie założono, że próbujesz pobrać właściwości z zestawu wierszy. Kod przy użyciu sesji lub polecenia są podobne, ale używa innego interfejsu.

Tworzenie [cdbpropset —](../../data/oledb/cdbpropset-class.md) przy użyciu grupy właściwości jako parametr do konstruktora. Na przykład:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

Wywołaj [AddProperty](../../data/oledb/cdbpropset-addproperty.md), przekazanie jej identyfikator właściwości i wartość do przypisania do właściwości. Typ wartości jest zależna od właściwości, których używasz.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

Użyj `IRowset` interfejsu do wywołania `GetProperties`. Przekaż właściwość, Ustaw jako parametr. Poniżej przedstawiono końcowy kodu:

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