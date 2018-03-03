---
title: _com_error::ErrorInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 642078d84f72a553e9b2407b279265a3a7e77522
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo
**Dotyczące firmy Microsoft**  
  
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