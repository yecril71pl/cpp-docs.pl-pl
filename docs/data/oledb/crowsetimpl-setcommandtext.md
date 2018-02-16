---
title: CRowsetImpl::SetCommandText | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
dev_langs:
- C++
helpviewer_keywords:
- SetCommandText method
ms.assetid: e016d7df-c1a0-4dee-b19b-c876680221fd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 18508fed21bb459f4b4c6a653437b1546c8d1a2b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetimplsetcommandtext"></a>CRowsetImpl::SetCommandText
Weryfikuje i przechowuje **DBID**s w dwóch ciągów ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pTableID`  
 [in] Wskaźnik do **DBID** reprezentujący identyfikator tabeli.  
  
 `pIndexID`  
 [in] Wskaźnik do **DBID** reprezentujący identyfikator indeksu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 **SetCommentText** metoda jest wywoływana przez `CreateRowset`, statyczna metoda, którego ma zastosowany szablon `IOpenRowsetImpl`.  
  
 Ta metoda deleguje swojej pracy, wywołując [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) i [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md) za pośrednictwem upcasted wskaźnika.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [CRowsetImpl, klasa](../../data/oledb/crowsetimpl-class.md)