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
ms.workload: cplusplus
ms.openlocfilehash: 1165f53027c5b8a116f97cd2660c7ca12c9e7302
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
 [_com_error, klasa](../cpp/com-error-class.md)