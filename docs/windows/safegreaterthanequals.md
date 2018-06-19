---
title: SafeGreaterThanEquals | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeGreaterThanEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeGreaterThanEquals function
ms.assetid: 43312fa9-d925-4f9f-a352-a190c02b3005
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c8b08e9262c1fc251de9ce2e23ba37783e97ab9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888763"
---
# <a name="safegreaterthanequals"></a>SafeGreaterThanEquals
Porównanie dwóch liczb.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename T, typename U>  
inline bool SafeGreaterThanEquals (  
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
 `true` Jeśli `t` jest większa niż lub równa `u`; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 `SafeGreaterThanEquals` zwiększa operator porównania standardowa, ponieważ umożliwia porównywanie dwa różne typy liczb.  
  
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
 [SafeLessThanEquals](../windows/safelessthanequals.md)   
 [SafeLessThan](../windows/safelessthan.md)