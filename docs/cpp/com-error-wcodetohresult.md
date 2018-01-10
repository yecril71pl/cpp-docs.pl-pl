---
title: _com_error::WCodeToHRESULT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::WCodeToHRESULT
dev_langs: C++
helpviewer_keywords: WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ca20bfa7574f604187734040b3ccc001d6aaf68d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT
**Dotyczące firmy Microsoft**  
  
 Mapuje 16-bitowych `wCode` do 32-bitowych `HRESULT`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      static HRESULT WCodeToHRESULT(  
   WORD wCode   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `wCode`  
 16-bitowych `wCode` można mapować na 32-bitowych `HRESULT`.  
  
## <a name="return-value"></a>Wartość zwracana  
 32-bitowych `HRESULT` zamapowany z 16-bitowych `wCode`.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [Kodostrzeżenia](../cpp/com-error-wcode.md) funkcję elementu członkowskiego.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error::WCode](../cpp/com-error-wcode.md)   
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error, klasa](../cpp/com-error-class.md)