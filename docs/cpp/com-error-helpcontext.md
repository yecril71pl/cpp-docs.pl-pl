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
ms.openlocfilehash: b1edf990697aa6becca0ad377f18e8f7045c96a4
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401847"
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
  
## <a name="see-also"></a>Zobacz także  
 [_com_error, klasa](../cpp/com-error-class.md)