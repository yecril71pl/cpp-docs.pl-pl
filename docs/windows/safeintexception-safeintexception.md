---
title: SafeIntException::SafeIntException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs: C++
helpviewer_keywords: SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: d9a1e2666aef593cde385f121065397226bad9d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException
Tworzy `SafeIntException` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`code`  
 Wartość wyliczenia danych opisujący wystąpił błąd.  
  
## <a name="remarks"></a>Uwagi  
 Możliwe wartości `code` są zdefiniowane w pliku Safeint.h. Dla wygody możliwe wartości znajdują się w tym miejscu.  
  
-   `SafeIntNoError`  
  
-   `SafeIntArithmeticOverflow`  
  
-   `SafeIntDivideByZero`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka SafeInt](../windows/safeint-library.md)   
 [Safeintexception — klasa](../windows/safeintexception-class.md)   
 [Safeint — klasa](../windows/safeint-class.md)