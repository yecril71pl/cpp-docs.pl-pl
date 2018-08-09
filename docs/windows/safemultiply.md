---
title: SafeMultiply | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeMultiply
dev_langs:
- C++
helpviewer_keywords:
- SafeMultiply function
ms.assetid: 81d988a5-fac7-4930-8c37-c24fa8e2c853
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c0c78a8c17c47ea91d89b3dc7451d60ed0a567b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019095"
---
# <a name="safemultiply"></a>SafeMultiply
Mnoży dwie liczby razem w sposób zapewniający ochronę przed przepełnienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename T, typename U>  
inline bool SafeMultiply (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *t*  
 Pierwszy numer do pomnożenia. To musi być typu `T`.  
  
 [in] *u*  
 Druga liczba do pomnożenia. To musi być typu `U`.  
  
 [out] *wynik*  
 Parametr gdzie **SafeMultiply** zapisuje wynik.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli żaden błąd nie wystąpi; **false** w przypadku wystąpienia błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest częścią [Biblioteka SafeInt](../windows/safeint-library.md) i jest przeznaczony dla jednego mnożenie bez tworzenia wystąpienia obiektu [safeint — klasa](../windows/safeint-class.md).  
  
> [!NOTE]
>  Ta metoda ją stosować tylko po jednej operacji matematycznych muszą być chronione. Jeśli istnieje wiele operacji, należy użyć `SafeInt` klasy zamiast wywoływania poszczególnych funkcjami autonomicznymi.  
  
 Aby uzyskać więcej informacji na temat typów szablonu `T` i `U`, zobacz [safeint — funkcje](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** safeint.h  
  
 **Namespace:** Microsoft::Utilities  
  
## <a name="see-also"></a>Zobacz też  
 [Safeint — funkcje](../windows/safeint-functions.md)   
 [Biblioteka SafeInt](../windows/safeint-library.md)   
 [Safeint — klasa](../windows/safeint-class.md)   
 [SafeDivide](../windows/safedivide.md)