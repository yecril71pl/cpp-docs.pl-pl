---
title: Odwoływanie się do właściwości w dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f6730746cbb3da08e52b5a4d9936aa48a8484886
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052565"
---
# <a name="referencing-a-property-in-your-provider"></a>Odwoływanie się do właściwości w dostawcy

Znajdź grupy właściwości i Identyfikatora właściwości dla właściwości, które chcesz. Aby uzyskać więcej informacji, zobacz [właściwości OLE DB](/previous-versions/windows/desktop/ms722734\(v=vs.85\)) w *OLE DB Podręcznik programisty*.  
  
W poniższym przykładzie założono, próby pobrania właściwości z zestawu wierszy. Kod przy użyciu sesji lub polecenia są podobne, ale używa innego interfejsu.  
  
Tworzenie [cdbpropset —](../../data/oledb/cdbpropset-class.md) przy użyciu grupy właściwości jako parametr do konstruktora. Na przykład:  
  
```cpp  
CDBPropSet propset(DBPROPSET_ROWSET);  
```  
  
Wywołaj [AddProperty](../../data/oledb/cdbpropset-addproperty.md), przekazanie jej identyfikator właściwości i wartość do przypisania do właściwości. Typ wartości jest zależna od właściwości, którego używasz.  
  
```cpp  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_IRowsetChange, true);  

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);  
```  
  
Użyj `IRowset` interfejsu do wywołania `GetProperties`. Przekaż właściwość, Ustaw jako parametr. Poniżej przedstawiono końcowy kodu:  
  
```cpp  
CAgentRowset<CMyProviderCommand>* pRowset = (CAgentRowset<CMyProviderCommand>*) pThis;  
  
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