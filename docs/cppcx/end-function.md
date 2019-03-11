---
title: End — funkcja
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::end
helpviewer_keywords:
- end Function
ms.assetid: fb837bff-fc76-4bae-9096-facf0e03041c
ms.openlocfilehash: c46c601be2b2ed78cf79641a7fcf5324e615a771
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745074"
---
# <a name="end-function"></a>End — funkcja

Zwraca iterator, który wskazuje poza końcem kolekcji, która jest dostępna za pomocą parametru określonego interfejsu.

## <a name="syntax"></a>Składnia

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    end(
        IVector<T>^ v       );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    end(
        IVectorView<T>^ v
       );
template <typename T>
    ::Platform::Collections::InputIterator<T>
    end(
        IIterable<T>^ i
       );
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Parametrowi typu szablonu.

*v*<br/>
Kolekcja wektora\<T > lub VectorView\<T > obiekty, które są używane przez IVector\<T >, lub IVectorView\<T > interfejsu.

*i*<br/>
Zbiór arbitraty Windows Runtime obiekty, które są dostępne dla IIterable\<T > interfejsu.

### <a name="return-value"></a>Wartość zwracana

Iterator, który wskazuje poza końcem kolekcji.

### <a name="remarks"></a>Uwagi

Pierwsze dwie funkcje szablonów zwracają Iteratory, a trzecia funkcja szablonu zwraca iterator danych wejściowych.

[Platform::Collections:: vectorviewiterator](../cppcx/platform-collections-vectorviewiterator-class.md) obiektu, który jest zwracany przez `end` jest iteratorem serwera proxy, który przechowuje elementy typu `VectorProxy<T>`. Jednak obiekt serwera proxy prawie nigdy nie jest widoczne dla kodu użytkownika. Aby uzyskać więcej informacji, zobacz [kolekcje (C + +/ CX)](../cppcx/collections-c-cx.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Namespace:** Windows::Foundation::Collections

## <a name="see-also"></a>Zobacz także

[Windows::Foundation:: Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)
