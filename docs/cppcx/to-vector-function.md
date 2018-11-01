---
title: to_vector, funkcja
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
ms.openlocfilehash: a2054e6e787dcf9137a087dd53264c7f98461d69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508956"
---
# <a name="tovector-function"></a>to_vector, funkcja

Zwraca `std::vector` którego wartość jest taka sama jak kolekcja podstawowy określony parametr IVector lub IVectorView.

## <a name="syntax"></a>Składnia

```
template <typename T>
inline ::std::vector<T> to_vector(IVector<T>^ v);

template <typename T>
inline ::std::vector<T> to_vector(IVectorView<T>^ v);
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Parametrowi typu szablonu.

*v*<br/>
Interfejs IVector lub IVectorView, która zapewnia dostęp do bazowego obiektu wektora lub VectorView.

### <a name="return-value"></a>Wartość zwracana

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Namespace:** Windows::Foundation:: Collections

## <a name="see-also"></a>Zobacz też

[Windows::Foundation:: Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)