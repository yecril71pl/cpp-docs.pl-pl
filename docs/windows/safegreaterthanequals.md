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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5b7ab93665ce4f5f15aed68520a130897bdcd90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397159"
---
# <a name="safegreaterthanequals"></a>SafeGreaterThanEquals

Porównuje dwie liczby.

## <a name="syntax"></a>Składnia

```cpp
template <typename T, typename U>
inline bool SafeGreaterThanEquals (
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

**wartość true,** Jeśli *t* jest większa niż lub równa *u*; w przeciwnym razie **false**.

## <a name="remarks"></a>Uwagi

**SafeGreaterThanEquals** zwiększa operator porównania standardowe, ponieważ umożliwia porównywanie dwa różne typy liczb.

Ta metoda jest częścią [Biblioteka SafeInt](../windows/safeint-library.md) i jest przeznaczony dla operacji jedno porównanie bez tworzenia wystąpienia obiektu [safeint — klasa](../windows/safeint-class.md).

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
[SafeGreaterThan](../windows/safegreaterthan.md)<br/>
[SafeLessThanEquals](../windows/safelessthanequals.md)<br/>
[SafeLessThan](../windows/safelessthan.md)