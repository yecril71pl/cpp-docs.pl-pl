---
title: CSession::StartTransaction | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSession::StartTransaction
- StartTransaction
- ATL.CSession.StartTransaction
- CSession.StartTransaction
- ATL::CSession::StartTransaction
dev_langs: C++
helpviewer_keywords: StartTransaction method
ms.assetid: cd7bd2be-fad1-4e2b-932b-79d308efb8fb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d1aa3f42702f3d181fa83a495c751dae339d8537
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="csessionstarttransaction"></a>CSession::StartTransaction
Rozpoczyna nową transakcję dla tej sesji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT StartTransaction(  
   ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,  
   ULONG isoFlags = 0,  
   ITransactionOptions* pOtherOptions = NULL,  
   ULONG* pulTransactionLevel = NULL   
) const throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CSession](../../data/oledb/csession-class.md)