---
title: CSession::Commit | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSession.Commit
- ATL.CSession.Commit
- ATL::CSession::Commit
- CSession::Commit
dev_langs:
- C++
helpviewer_keywords:
- Commit method
ms.assetid: 1d5f56b9-000c-4bae-a975-89d3452f499f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 44fdeef9462bf30a30226ea292024a4cdb1bf8ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="csessioncommit"></a>CSession::Commit
Zatwierdza transakcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Commit(BOOL bRetaining = FALSE,   
   DWORD grfTC = XACTTC_SYNC,   
   DWORD grfRM = 0) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [metody ITransaction::Commit](https://msdn.microsoft.com/en-us/library/ms713008.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [metody ITransaction::Commit](https://msdn.microsoft.com/en-us/library/ms713008.aspx).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CSession, klasa](../../data/oledb/csession-class.md)