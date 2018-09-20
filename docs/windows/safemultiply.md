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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0eb1b8b37737d1c0c36af28da9b0c656e26de7d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396752"
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

*t*<br/>
[in] Pierwszy numer do pomnożenia. To musi być typu `T`.

*u*<br/>
[in] Druga liczba do pomnożenia. To musi być typu `U`.

*wynik*<br/>
[out] Parametr gdzie **SafeMultiply** zapisuje wynik.

## <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli żaden błąd nie wystąpi; **false** w przypadku wystąpienia błędu.

## <a name="remarks"></a>Uwagi

Ta metoda jest częścią [Biblioteka SafeInt](../windows/safeint-library.md) i jest przeznaczony dla jednego mnożenie bez tworzenia wystąpienia obiektu [safeint — klasa](../windows/safeint-class.md).

> [!NOTE]
> Ta metoda ją stosować tylko po jednej operacji matematycznych muszą być chronione. Jeśli istnieje wiele operacji, należy użyć `SafeInt` klasy zamiast wywoływania poszczególnych funkcjami autonomicznymi.

Aby uzyskać więcej informacji na temat typów szablonu `T` i `U`, zobacz [safeint — funkcje](../windows/safeint-functions.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Zobacz też

[SafeInt, funkcje](../windows/safeint-functions.md)<br/>
[Biblioteka SafeInt](../windows/safeint-library.md)<br/>
[SafeInt, klasa](../windows/safeint-class.md)<br/>
[SafeDivide](../windows/safedivide.md)