---
title: _com_error::HelpContext | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::HelpContext
dev_langs:
- C++
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2dbdd52b311a35d390a61a0601a63c1b680f79b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext
**Dotyczące firmy Microsoft**  
  
 Wywołania **IErrorInfo::GetHelpContext** funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
DWORD HelpContext( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wynik **IErrorInfo::GetHelpContext** dla **IErrorInfo** obiektu zarejestrowane w ramach `_com_error` obiektu. Jeśli nie **IErrorInfo** obiektu jest rejestrowany, zwracana jest wartość zero.  
  
## <a name="remarks"></a>Uwagi  
 Wszelkie wystąpił błąd podczas wywoływania **IErrorInfo::GetHelpContext** metody jest ignorowana.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error, klasa](../cpp/com-error-class.md)