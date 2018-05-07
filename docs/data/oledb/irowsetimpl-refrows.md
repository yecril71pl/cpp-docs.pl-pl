---
title: IRowsetImpl::RefRows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
dev_langs:
- C++
helpviewer_keywords:
- RefRows method
ms.assetid: 1c048a2a-65dc-4bba-9c81-a23c0dc249c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9aa841444f9cfa2758e8d5a8d8d4ec831a531d6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetimplrefrows"></a>IRowsetImpl::RefRows
Wywoływane przez [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) i [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md) zwiększać lub zwolnij licznika odwołań do istniejących uchwyt wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```
HRESULT RefRows(DBCOUNTITEM cRows,  
   const HROWrghRows[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[],  
   BOOL bAdd);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowset::AddRefRows](https://msdn.microsoft.com/en-us/library/ms719619.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Irowsetimpl — klasa](../../data/oledb/irowsetimpl-class.md)   
 [CSimpleRow, klasa](../../data/oledb/csimplerow-class.md)