---
title: SafeIntException::SafeIntException | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ef3c1d11c0f814699ca1492f7ec1fb49c43c3d76
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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
 [in] `code`  
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
 [SafeInt, klasa](../windows/safeint-class.md)