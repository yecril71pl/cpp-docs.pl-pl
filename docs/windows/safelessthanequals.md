---
title: SafeLessThanEquals | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: SafeLessThanEquals
dev_langs: C++
helpviewer_keywords: SafeLessThanEquals function
ms.assetid: cbd70526-faf2-4fbc-96a0-b61e8cf5f04a
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cb5765d9ea353558d7a297fb7867c6889be928ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="safelessthanequals"></a>SafeLessThanEquals
Porównanie dwóch liczb.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename T, typename U>  
inline bool SafeLessThanEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`t`  
 Pierwsza liczba do porównania. To musi być typu T.  
  
 [in]`u`  
 Druga liczba do porównania. Musi to być typ U.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli `t` jest mniejsza niż lub równa `u`; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 `SafeLessThanEquals`Rozszerza operator porównania regularne, dzięki któremu można porównywać wartości różnych typów dwie liczb.  
  
 Ta metoda jest częścią [Biblioteka SafeInt](../windows/safeint-library.md) i jest przeznaczony dla operacji porównywania pojedynczego bez tworzenia wystąpienia [safeint — klasa](../windows/safeint-class.md).  
  
> [!NOTE]
>  Tej metody należy używać tylko w przypadku, gdy jednej operacji matematycznych muszą być chronione. Jeśli istnieje wiele operacji, należy użyć `SafeInt` klasy zamiast kontaktować się z poszczególnych funkcji autonomicznych.  
  
 Aby uzyskać więcej informacji o typach szablonu T oraz U, zobacz [safeint — funkcje](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** safeint.h  
  
 **Namespace:** Microsoft::Utilities  
  
## <a name="see-also"></a>Zobacz też  
 [Safeint — funkcje](../windows/safeint-functions.md)   
 [Biblioteka SafeInt](../windows/safeint-library.md)   
 [Safeint — klasa](../windows/safeint-class.md)   
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeLessThan](../windows/safelessthan.md)   
 [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)