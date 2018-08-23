---
title: SafeLessThan | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeLessThan
dev_langs:
- C++
helpviewer_keywords:
- SafeLessThan function
ms.assetid: 9d85bc0d-8d94-4d59-9b72-ef3c63a120a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 499b621c804f13f6a56bc2ce9be0ba91ab824a48
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592403"
---
# <a name="safelessthan"></a>SafeLessThan

Określa, czy jeden jest mniejszy niż inny.

## <a name="syntax"></a>Składnia

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

[in] *t*  
Pierwsza liczba. To musi być typu `T`.

[in] *u*  
Drugi numer. To musi być typu `U`.

## <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *t* jest mniejsza niż *u*; w przeciwnym razie **false**.

## <a name="remarks"></a>Uwagi

Ta metoda zwiększa operator porównania standardowe, ponieważ **SafeLessThan** umożliwia porównywanie dwa różne typy liczby.

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
[SafeLessThanEquals](../windows/safelessthanequals.md)  
[SafeGreaterThan](../windows/safegreaterthan.md)  
[SafeGreaterThanEquals](../windows/safegreaterthanequals.md)