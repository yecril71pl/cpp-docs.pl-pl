---
title: SafeAdd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeAdd
dev_langs:
- C++
helpviewer_keywords:
- SafeAdd function
ms.assetid: 3f82b91d-59fe-4ee1-873b-d056182fa8be
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b0450820afdde3eb330948a65f8d052fa54017dc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="safeadd"></a>SafeAdd
Dodaje dwie liczb w sposób zapewniający ochronę przed przepełnienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename T, typename U>  
inline bool SafeAdd (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `t`  
 Pierwszy numer do dodania. To musi być typu T.  
  
 [in] `u`  
 Druga liczba do dodania. Musi to być typ U.  
  
 [out] `result`  
 Parametr gdzie `SafeAdd` zapisuje wynik.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli nie występują błędy; `false` w przypadku wystąpienia błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest częścią [Biblioteka SafeInt](../windows/safeint-library.md) i jest przeznaczony dla operacji dodawania jednego bez tworzenia wystąpienia [safeint — klasa](../windows/safeint-class.md).  
  
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
 [SafeSubtract](../windows/safesubtract.md)