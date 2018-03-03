---
title: _com_error::opis | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::Description
dev_langs:
- C++
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f3ed306a8eba4e76c2eefc738b617117188e85c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comerrordescription"></a>_com_error::Description
**Dotyczące firmy Microsoft**  
  
 Wywołania **IErrorInfo::GetDescription** funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
_bstr_t Description( ) const;  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wynik **IErrorInfo::GetDescription** dla **IErrorInfo** obiektu zarejestrowane w ramach `_com_error` obiektu. Powstałe w ten sposób `BSTR` jest hermetyzowany w `_bstr_t` obiektu. Jeśli nie **IErrorInfo** jest rejestrowane, zwraca pustą `_bstr_t`.  
  
## <a name="remarks"></a>Uwagi  
 Wywołania **IErrorInfo::GetDescription** funkcji i pobiera **IErrorInfo** zarejestrowane w ramach `_com_error` obiektu. Wszelkie wystąpił błąd podczas wywoływania **IErrorInfo::GetDescription** metody jest ignorowana.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error, klasa](../cpp/com-error-class.md)