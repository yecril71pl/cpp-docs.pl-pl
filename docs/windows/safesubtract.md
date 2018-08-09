---
title: SafeSubtract | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeSubtract
dev_langs:
- C++
helpviewer_keywords:
- SafeSubtract function
ms.assetid: c2712ddc-173f-46a1-b09c-e7ebbd9e68b2
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a82281f1078acd5e3ed0662964a0171ccd72c336
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018377"
---
# <a name="safesubtract"></a>SafeSubtract
Odejmuje dwie liczby, w sposób zapewniający ochronę przed przepełnienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename T, typename U>  
inline bool SafeSubtract (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *t*  
 Pierwszy numer w odejmowania. To musi być typu `T`.  
  
 [in] *u*  
 Liczba, którą chcesz odjąć od *t*. To musi być typu `U`.  
  
 [out] *wynik*  
 Parametr gdzie **SafeSubtract** zapisuje wynik.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli żaden błąd nie wystąpi; **false** w przypadku wystąpienia błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest częścią [Biblioteka SafeInt](../windows/safeint-library.md) i jest przeznaczony dla operacji odejmowania pojedynczego bez tworzenia wystąpienia obiektu [safeint — klasa](../windows/safeint-class.md).  
  
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
 [SafeAdd](../windows/safeadd.md)