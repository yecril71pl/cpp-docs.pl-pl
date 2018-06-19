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
ms.openlocfilehash: a33834df20606e8380e6a328a41435522185ac70
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412348"
---
# <a name="comerrorsource"></a>_com_error::Source
**Microsoft Specific**  
  
 Wywołania **IErrorInfo::GetSource** funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
_bstr_t Source() const;  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wynik **IErrorInfo::GetSource** dla **IErrorInfo** obiektu zarejestrowane w ramach `_com_error` obiektu. BSTR wynikowe są umieszczane w `_bstr_t` obiektu. Jeśli nie **IErrorInfo** jest rejestrowane, zwraca pustą `_bstr_t`.  
  
## <a name="remarks"></a>Uwagi  
 Wszelkie wystąpił błąd podczas wywoływania **IErrorInfo::GetSource** metody jest ignorowana.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error, klasa](../cpp/com-error-class.md)