---
title: IRowsetImpl::GetData | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
dev_langs:
- C++
helpviewer_keywords:
- GetData method [OLE DB]
ms.assetid: cb15f1cc-bd25-4b74-93c3-db71aa93829c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 64bc8d6b84195aef8fd9dc3b0093221cc8e057d7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetimplgetdata"></a>IRowsetImpl::GetData
Pobiera dane z kopii zestawu wierszy wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(GetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pDstData);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowset::GetData](https://msdn.microsoft.com/en-us/library/ms716988.aspx) w *OLE DB Podręcznik programisty*.  
  
 Niektóre parametry odpowiadają *OLE DB Podręcznik programisty* parametry różnych nazw, które zostały opisane w **IRowset::GetData**:  
  
|Parametry szablonu OLE DB|*OLE DB Podręcznik programisty* parametrów|  
|--------------------------------|------------------------------------------------|  
|*pDstData*|`pData`|  
  
## <a name="remarks"></a>Uwagi  
 Obsługuje także konwersja danych za pomocą konwersji danych OLE DB biblioteki DLL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IRowsetImpl, klasa](../../data/oledb/irowsetimpl-class.md)