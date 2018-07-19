---
title: _com_error::HelpContext | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpContext
dev_langs:
- C++
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e800bd3100fa0199534f3e9bdf6646aa0ffc6860
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940901"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext
**Microsoft Specific**  
  
 Wywołania `IErrorInfo::GetHelpContext` funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
DWORD HelpContext( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wynik `IErrorInfo::GetHelpContext` dla `IErrorInfo` obiektu rejestrować się w ramach `_com_error` obiektu. Jeśli nie `IErrorInfo` obiektu jest rejestrowane, zwracana jest wartość zero.  
  
## <a name="remarks"></a>Uwagi  
 Jakiekolwiek niepowodzenie podczas wywoływania `IErrorInfo::GetHelpContext` metody jest ignorowana.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error, klasa](../cpp/com-error-class.md)