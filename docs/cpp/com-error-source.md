---
title: _com_error::źródło | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Source
dev_langs:
- C++
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f904fa11195c27f8e08856ef391d0ba8adbedece
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939680"
---
# <a name="comerrorsource"></a>_com_error::Source
**Microsoft Specific**  
  
 Wywołania `IErrorInfo::GetSource` funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
_bstr_t Source() const;  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wynik `IErrorInfo::GetSource` dla `IErrorInfo` obiektu rejestrować się w ramach `_com_error` obiektu. Wynikowy BSTR jest hermetyzowany w `_bstr_t` obiektu. Jeśli nie `IErrorInfo` jest rejestrowane, zwraca pustą `_bstr_t`.  
  
## <a name="remarks"></a>Uwagi  
 Jakiekolwiek niepowodzenie podczas wywoływania `IErrorInfo::GetSource` metody jest ignorowana.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error, klasa](../cpp/com-error-class.md)