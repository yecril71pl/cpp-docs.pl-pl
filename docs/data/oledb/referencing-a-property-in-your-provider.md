---
title: Odwołanie do właściwości w dostawcy | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 36965ac33fc0a563951c0c0dfdce60d9d0e4f55b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106547"
---
# <a name="referencing-a-property-in-your-provider"></a>Odwoływanie się do właściwości w dostawcy
Znajdź grupy właściwości i Identyfikatora właściwości dla właściwości, które mają. Aby uzyskać więcej informacji, zobacz [właściwości OLE DB](https://msdn.microsoft.com/en-us/library/ms722734.aspx) w *OLE DB Podręcznik programisty*.  
  
 W poniższym przykładzie założono, że próbujesz uzyskać właściwości z zestawu wierszy. Kod za pomocą sesji lub polecenia jest podobny, ale używa innego interfejsu.  
  
 Utwórz [cdbpropset —](../../data/oledb/cdbpropset-class.md) obiekt, za pomocą grupy właściwości jako parametr do konstruktora. Na przykład:  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
```  
  
 Wywołanie [AddProperty](../../data/oledb/cdbpropset-addproperty.md), przekazanie jej Identyfikatora właściwości i wartość do przypisania do właściwości. Typ wartości jest zależna od właściwości, które są używane.  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_IRowsetChange, true);  

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);  
```  
  
 Użyj `IRowset` interfejs do wywołania **GetProperties**. Przekaż właściwość ustawić jako parametr. Oto kod końcowego:  
  
```  
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