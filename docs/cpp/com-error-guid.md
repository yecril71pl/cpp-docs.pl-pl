---
title: _com_error::GUID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::GUID
dev_langs:
- C++
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c592607732eb5558ce74edb7b71adbc023b2ae52
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402286"
---
# <a name="comerrorguid"></a>_com_error::GUID
**Microsoft Specific**  
  
 Wywołania `IErrorInfo::GetGUID` funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
GUID GUID( ) const throw( );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wynik `IErrorInfo::GetGUID` dla `IErrorInfo` obiektu rejestrować się w ramach `_com_error` obiektu. Jeśli nie `IErrorInfo` obiektu jest rejestrowane, zwraca `GUID_NULL`.  
  
## <a name="remarks"></a>Uwagi  
 Jakiekolwiek niepowodzenie podczas wywoływania `IErrorInfo::GetGUID` metody jest ignorowana.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [_com_error, klasa](../cpp/com-error-class.md)