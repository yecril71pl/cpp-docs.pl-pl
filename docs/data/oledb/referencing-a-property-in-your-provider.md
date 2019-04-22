---
title: Odwoływanie się do właściwości w dostawcy
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: c3e620cd760aa04df7d7d2209ef009a606675276
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028463"
---
# <a name="referencing-a-property-in-your-provider"></a>Odwoływanie się do właściwości w dostawcy

Znajdź grupy właściwości i Identyfikatora właściwości dla właściwości, które chcesz. Aby uzyskać więcej informacji, zobacz [właściwości OLE DB](/previous-versions/windows/desktop/ms722734(v=vs.85)) w **OLE DB Podręcznik programisty**.

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

## <a name="see-also"></a>Zobacz także

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)