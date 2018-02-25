---
title: IOpenRowsetImpl::CreateRowset | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c03b94464b8a326b911b11cc7dab6d09c88ce9a4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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