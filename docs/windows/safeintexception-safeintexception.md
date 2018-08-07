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
ms.openlocfilehash: 744bf034572745cd88a35f47a1ca2da03e900fd8
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606660"
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException
Tworzy **safeintexception —** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *kodu*  
 Wartość danych wyliczany, który opisuje błąd, który wystąpił.  
  
## <a name="remarks"></a>Uwagi  
 Możliwe wartości parametru *kodu* są zdefiniowane w pliku Safeint.h. Dla wygody możliwe wartości są również wymienione tutaj.  
  
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