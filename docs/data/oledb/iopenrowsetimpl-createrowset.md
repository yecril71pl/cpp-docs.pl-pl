---
title: IOpenRowsetImpl::CreateRowset | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateRowset method
ms.assetid: 69041cf6-7a2f-4409-a26e-6e984c24986e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2d4554a2aeee3218ce505dc2c135167a3e38d55c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105182"
---
# <a name="iopenrowsetimplcreaterowset"></a>IOpenRowsetImpl::CreateRowset
Tworzy obiekt zestawu wierszy. Nie należy wywoływać bezpośrednio przez użytkownika. Zobacz [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) w *OLE DB Podręcznik programisty.*  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      template template <class RowsetClass  
      >  
HRESULT CreateRowset(IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj);  
```  
  
#### <a name="parameters"></a>Parametry  
 `RowsetClass`  
 Szablon elementu członkowskiego klasy reprezentujący użytkownika klasy zestawu wierszy. Zwykle generowane przez kreatora.  
  
 `pRowsetObj`  
 [out] Wskaźnik do obiektu zestawu wierszy. Zazwyczaj ten parametr nie jest używany, ale można używać, jeśli w zestawie wierszy przed przekazaniem go do obiektu COM należy wykonać więcej pracy. Okres istnienia `pRowsetObj` jest powiązany `ppRowset`.  
  
 Dla innych parametrów, zobacz [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) w *OLE DB Podręcznik programisty.*  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IOpenRowsetImpl, klasa](../../data/oledb/iopenrowsetimpl-class.md)