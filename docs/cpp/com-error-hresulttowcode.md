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
ms.openlocfilehash: f0ddac28c4f39cdf11abbdf38c3af5d00c22413a
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401909"
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode
**Microsoft Specific**  
  
 Mapuje HRESULT 32-bitowego do 16-bitowych `wCode`.  
  
## <a name="syntax"></a>Składnia  
  
```  
static WORD HRESULTToWCode(  
   HRESULT hr   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *godz.*  
 HRESULT 32-bitowe mają być mapowane do 16-bitowych `wCode`.  
  
## <a name="return-value"></a>Wartość zwracana  
 16-bitowych `wCode` mapowane z HRESULT 32-bitowych.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [_com_error::WCode](../cpp/com-error-wcode.md) Aby uzyskać więcej informacji.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [_com_error::WCode](../cpp/com-error-wcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error, klasa](../cpp/com-error-class.md)