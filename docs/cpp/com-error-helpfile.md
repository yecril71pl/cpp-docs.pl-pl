---
title: _com_error::HelpFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpFile
dev_langs:
- C++
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acd909224d6a682a210e15eebf04d2c8429a8a3c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939561"
---
# <a name="comerrorhelpfile"></a>_com_error::HelpFile
**Microsoft Specific**  
  
 Wywołania `IErrorInfo::GetHelpFile` funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
_bstr_t HelpFile() const;  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wynik `IErrorInfo::GetHelpFile` dla `IErrorInfo` obiektu rejestrować się w ramach `_com_error` obiektu. Wynikowy BSTR jest hermetyzowany w `_bstr_t` obiektu. Jeśli nie `IErrorInfo` jest rejestrowane, zwraca pustą `_bstr_t`.  
  
## <a name="remarks"></a>Uwagi  
 Jakiekolwiek niepowodzenie podczas wywoływania `IErrorInfo::GetHelpFile` metody jest ignorowana.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error, klasa](../cpp/com-error-class.md)