---
title: _com_error::WCodeToHRESULT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::WCodeToHRESULT
dev_langs:
- C++
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31b9df8305d0eea772979904f63847f6d6c2325a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT
**Microsoft Specific**  
  
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