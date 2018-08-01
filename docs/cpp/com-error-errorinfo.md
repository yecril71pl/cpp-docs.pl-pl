---
title: _com_error::ErrorInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3f4d105efb7269c0c1344d6a9399ebbe4fa9fd2
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404297"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo
**Microsoft Specific**  
  
 Pobiera `IErrorInfo` obiekt przekazany do konstruktora.  
  
## <a name="syntax"></a>Składnia  
  
```  
IErrorInfo * ErrorInfo( ) const throw( );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Nieprzetworzone `IErrorInfo` element przekazany do konstruktora.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera zhermetyzowany `IErrorInfo` pozycja `_com_error` obiekt lub wartość NULL, jeśli nie `IErrorInfo` elementu są rejestrowane. Obiekt wywołujący musi wywołać `Release` na zwracanym obiekcie po zakończeniu korzystania z niego.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [_com_error, klasa](../cpp/com-error-class.md)