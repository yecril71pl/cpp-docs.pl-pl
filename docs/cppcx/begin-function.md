---
title: BEGIN — funkcja
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::begin
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
ms.openlocfilehash: 5ff8765d759a14cab63e3c8ae0ba2bc419b00775
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628530"
---
# <a name="begin-function"></a>BEGIN — funkcja

Zwraca iterator, który wskazuje na początku kolekcji, która jest dostępna za pomocą parametru określonego interfejsu.

## <a name="syntax"></a>Składnia

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    begin(
          IVector<T>^ v         );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    begin(
          IVectorView<T>^ v
         );

template <typename T>
    ::Platform::Collections::InputIterator<T>
    begin(
          IIterable<T>^ i         );
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Parametrowi typu szablonu.

*v*<br/>
Kolekcja wektora\<T > lub VectorView\<T > obiekty, które są używane przez IVector\<T > lub IVectorView\<T > interfejsu.

*i*<br/>
Zbiór dowolnego Windows środowiska wykonawczego obiektów, które są używane przez IIterable\<T > interfejsu.

### <a name="return-value"></a>Wartość zwracana

Iterator, który wskazuje na początku kolekcji.

### <a name="remarks"></a>Uwagi

Pierwsze dwie funkcje szablonów zwracają Iteratory, a trzecia funkcja szablonu zwraca iterator danych wejściowych.

VectorIterator, obiekt, który jest zwracany przez rozpoczęcie jest iteratora serwera proxy, który przechowuje elementy typu VectorProxy\<T >. Jednak obiekt serwera proxy prawie nigdy nie jest widoczne dla kodu użytkownika. Aby uzyskać więcej informacji, zobacz [kolekcje (C + +/ CX)](../cppcx/collections-c-cx.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Namespace:** Windows::Foundation:: Collections

## <a name="see-also"></a>Zobacz też

[Windows::Foundation:: Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)