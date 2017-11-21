---
title: _com_error::HRESULTToWCode | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::HRESULTToWCode
dev_langs: C++
helpviewer_keywords: HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2dac335f3cc2ea26602a5f8a91a47db7d1ebe39b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode
**Dotyczące firmy Microsoft**  
  
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
 [_com_error — klasa](../cpp/com-error-class.md)