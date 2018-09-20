---
title: SafeModulus | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeModulus
dev_langs:
- C++
helpviewer_keywords:
- SafeModulus function
ms.assetid: ae5c81eb-5dcf-45a5-aa76-465fdfe68654
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 48feb16696243479849492171732b0d070ce032f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427917"
---
# <a name="safemodulus"></a>SafeModulus

Wykonuje operację modulo na dwóch liczb.

## <a name="syntax"></a>Składnia

```cpp
template<typename T, typename U>
inline bool SafeModulus (
   const T t,
   const U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] Dzielnik. To musi być typu `T`.

*u*<br/>
[in] Dzielna. To musi być typu `U`.

*wynik*<br/>
[out] Parametr gdzie **SafeModulus** zapisuje wynik.

## <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli żaden błąd nie wystąpi; **false** w przypadku wystąpienia błędu.

## <a name="remarks"></a>Uwagi

Ta metoda jest częścią [Biblioteka SafeInt](../windows/safeint-library.md) i jest przeznaczony dla operacji modulo pojedynczego bez tworzenia wystąpienia obiektu [safeint — klasa](../windows/safeint-class.md).

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