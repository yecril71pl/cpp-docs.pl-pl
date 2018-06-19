---
title: _com_error::HRESULTToWCode | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HRESULTToWCode
dev_langs:
- C++
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e3955fcda665e08e5415652a1e8f1f232d0fe13
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412267"
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode
**Microsoft Specific**  
  
 Mapuje 32-bitowych `HRESULT` do 16-bitowych `wCode`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      static WORD HRESULTToWCode(  
   HRESULT hr   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `hr`  
 32-bitową `HRESULT` mają być mapowane do 16-bitowych `wCode`.  
  
## <a name="return-value"></a>Wartość zwracana  
 16-bitowych `wCode` zamapowany z 32-bitową `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [_com_error::WCode](../cpp/com-error-wcode.md) Aby uzyskać więcej informacji.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error::WCode](../cpp/com-error-wcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error, klasa](../cpp/com-error-class.md)