---
title: _com_error::opis | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Description
dev_langs:
- C++
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7df1fb3a8ca600b888e5d6f2c51fc44fda17dd27
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414262"
---
# <a name="comerrordescription"></a>_com_error::Description
**Microsoft Specific**  
  
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