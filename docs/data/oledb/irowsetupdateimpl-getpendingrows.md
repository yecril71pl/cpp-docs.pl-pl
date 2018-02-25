---
title: IRowsetUpdateImpl::GetPendingRows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
dev_langs:
- C++
helpviewer_keywords:
- GetPendingRows method
ms.assetid: 2d1ef748-da6d-4184-98dc-096427358dfd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a1086059facf686cca3bc876c78a44f298c1e4d3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetupdateimplgetpendingrows"></a>IRowsetUpdateImpl::GetPendingRows
Zwraca listę wierszy z oczekującymi zmianami.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,  
   DBPENDINGSTATUS dwRowStatus,  
   DBCOUNTITEM* pcPendingRows,  
   HROW** prgPendingRows,  
   DBPENDINGSTATUS** prgPendingStatus);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hReserved`  
 [in] Odpowiada `hChapter` parametru w [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx).  
  
 Dla innych parametrów, zobacz [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IRowsetUpdateImpl, klasa](../../data/oledb/irowsetupdateimpl-class.md)