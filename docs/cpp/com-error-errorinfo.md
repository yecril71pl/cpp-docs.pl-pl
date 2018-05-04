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
ms.openlocfilehash: 8fbc735dfae1b30209eccfd14f1170826fb07680
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo
**Microsoft Specific**  
  
 Pobiera **IErrorInfo** obiekt przekazany do konstruktora.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
IErrorInfo * ErrorInfo( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Nieprzetworzona **IErrorInfo** element przekazany do konstruktora.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera hermetyzowany **IErrorInfo** elementu `_com_error` obiekt, lub **NULL** Jeśli nie **IErrorInfo** elementu jest rejestrowany. Obiekt wywołujący musi wywołać **wersji** na zwracanym obiekcie po zakończeniu używa jej.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error, klasa](../cpp/com-error-class.md)