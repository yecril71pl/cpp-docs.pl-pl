---
title: SafeGreaterThan | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeGreaterThan
dev_langs:
- C++
helpviewer_keywords:
- SafeGreaterThan function
ms.assetid: 32cecac9-ba88-43eb-a7a4-30e390456739
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0944feb32f9dbd8b73d0710b248139c003e41410
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888786"
---
# <a name="safegreaterthan"></a>SafeGreaterThan
Porównanie dwóch liczb.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename T, typename U>  
inline bool SafeGreaterThan (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `t`  
 Pierwsza liczba do porównania. To musi być typu T.  
  
 [in] `u`  
 Druga liczba do porównania. Musi to być typ U.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `t` jest większa niż `u`; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 `SafeGreaterThan` Rozszerza operator porównania regularne, dzięki któremu można porównywać wartości różnych typów dwie liczb.  
  
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
 [SafeLessThan](../windows/safelessthan.md)   
 [SafeLessThanEquals](../windows/safelessthanequals.md)   
 [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)