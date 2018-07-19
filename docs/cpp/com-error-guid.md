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
ms.openlocfilehash: e324a84a16874a7e33f8687943b1302fbdd73a7a
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939029"
---
# <a name="comerrorguid"></a>_com_error::GUID
**Microsoft Specific**  
  
 Wywołania `IErrorInfo::GetGUID` funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
GUID GUID( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wynik `IErrorInfo::GetGUID` dla `IErrorInfo` obiektu rejestrować się w ramach `_com_error` obiektu. Jeśli nie `IErrorInfo` obiektu jest rejestrowane, zwraca GUID_NULL.  
  
## <a name="remarks"></a>Uwagi  
 Jakiekolwiek niepowodzenie podczas wywoływania `IErrorInfo::GetGUID` metody jest ignorowana.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error, klasa](../cpp/com-error-class.md)