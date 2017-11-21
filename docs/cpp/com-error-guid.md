---
title: _com_error::GUID | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::GUID
dev_langs: C++
helpviewer_keywords: GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b6c15c3890e5d5aa6e20cd0898f30aa0f56f50cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comerrorguid"></a>_com_error::GUID
**Dotyczące firmy Microsoft**  
  
 Wywołania **IErrorInfo::GetGUID** funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
GUID GUID( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wynik **IErrorInfo::GetGUID** dla **IErrorInfo** obiektu zarejestrowane w ramach `_com_error` obiektu. Jeśli nie **IErrorInfo** obiektu jest rejestrowany, zwraca `GUID_NULL`.  
  
## <a name="remarks"></a>Uwagi  
 Wszelkie wystąpił błąd podczas wywoływania **IErrorInfo::GetGUID** metody jest ignorowana.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error — klasa](../cpp/com-error-class.md)