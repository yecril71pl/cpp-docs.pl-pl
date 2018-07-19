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
ms.openlocfilehash: dbcbd73f1a4a6d80ed30a5d70ca43d5fe45677f9
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941720"
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
  
## <a name="see-also"></a>Zobacz też  
 [_com_error::WCode](../cpp/com-error-wcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error, klasa](../cpp/com-error-class.md)