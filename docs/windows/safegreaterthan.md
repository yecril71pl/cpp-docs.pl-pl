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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d17f464fd618f69279a5fe2e65c1abf8147eec9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724805"
---
# <a name="safegreaterthan"></a>SafeGreaterThan

Porównuje dwie liczby.

## <a name="syntax"></a>Składnia

```cpp
template<typename T, typename U>
inline bool SafeGreaterThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] Pierwsza liczba do porównania. To musi być typu `T`.

*u*<br/>
[in] Druga liczba do porównania. To musi być typu `U`.

## <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *t* jest większa niż *u*; w przeciwnym razie **false**.

## <a name="remarks"></a>Uwagi

**SafeGreaterThan** rozszerza operator porównania regularnych, dzięki któremu można porównać dwa różne typy liczb.

Ta metoda jest częścią [Biblioteka SafeInt](../windows/safeint-library.md) i jest przeznaczony dla operacji jedno porównanie bez tworzenia wystąpienia obiektu [safeint — klasa](../windows/safeint-class.md).

> [!NOTE]
> Ta metoda ją stosować tylko po jednej operacji matematycznych muszą być chronione. Jeśli istnieje wiele operacji, należy użyć `SafeInt` klasy zamiast wywoływania poszczególnych funkcjami autonomicznymi.

Aby uzyskać więcej informacji na temat typów szablonu `T` i `U`, zobacz [safeint — funkcje](../windows/safeint-functions.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Zobacz też

[SafeInt, funkcje](../windows/safeint-functions.md)  
[Biblioteka SafeInt](../windows/safeint-library.md)  
[SafeInt, klasa](../windows/safeint-class.md)  
[SafeLessThan](../windows/safelessthan.md)  
[SafeLessThanEquals](../windows/safelessthanequals.md)  
[SafeGreaterThanEquals](../windows/safegreaterthanequals.md)