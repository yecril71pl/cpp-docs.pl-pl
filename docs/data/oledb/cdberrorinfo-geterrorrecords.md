---
title: CDBErrorInfo::GetErrorRecords | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- GetErrorRecords
- CDBErrorInfo::GetErrorRecords
dev_langs: C++
helpviewer_keywords: GetErrorRecords method
ms.assetid: 07746774-bcca-4833-8f55-a619e9777c17
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 584915a27a6f980933cd9aa71f67f6a223f743be
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdberrorinfogeterrorrecords"></a>CDBErrorInfo::GetErrorRecords
Pobiera błąd rekordów dla określonego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT GetErrorRecords(   
   IUnknown* pUnk,   
   const IID& iid,   
   ULONG* pcRecords    
) throw( );  
HRESULT GetErrorRecords(   
   ULONG* pcRecords    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *pUnk*  
 [in] Interfejs do obiektu, dla którego można pobrać rekordów błędów.  
  
 `iid`  
 [in] Uzyskanie identyfikatora IID interfejsu skojarzonego z powodu błędu.  
  
 *pcRecords*  
 [out] Wskaźnik do rekordów błędów liczby (w oparciu o jeden).  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Formularz pierwszej funkcji, jeśli chcesz sprawdzić, które interfejs, aby uzyskać informacje o błędzie z. W przeciwnym razie użyj drugi formularz.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdberrorinfo — klasa](../../data/oledb/cdberrorinfo-class.md)