---
title: unchecked_array_iterator — Klasa
ms.date: 11/04/2016
f1_keywords:
- stdext::unchecked_array_iterator
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
ms.openlocfilehash: 9b3db474bedca50922334bd4dbd09c71d4e6e987
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626203"
---
# <a name="uncheckedarrayiterator-class"></a>unchecked_array_iterator — Klasa

`unchecked_array_iterator` Klasa umożliwia owijanie tablicy lub wskaźnika w niesprawdzony iterator. Ta klasa jest używana jako otoka (przy użyciu [make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator) funkcji) dla surowych wskaźników lub tablic jako ukierunkowany sposób zarządzania ostrzeżeniami niezaznaczonych wskaźników zamiast globalnego wyciszania tych ostrzeżeń. Jeśli to możliwe, Preferuj sprawdzonej wersji tej klasy, [checked_array_iterator](../standard-library/checked-array-iterator-class.md).

> [!NOTE]
> Ta klasa jest rozszerzeniem Microsoft standardowej biblioteki języka C++. Kod zaimplementowany przy użyciu tej funkcji nie jest przenośny do standardowych środowisk kompilacji C++, które nie obsługują tego rozszerzenia Microsoft.

## <a name="syntax"></a>Składnia

```cpp
template <class Iterator>
class unchecked_array_iterator;
```

## <a name="remarks"></a>Uwagi

Ta klasa jest zdefiniowana w [stdext](../standard-library/stdext-namespace.md) przestrzeni nazw.

To jest niesprawdzona wersja [klasy checked_array_iterator](../standard-library/checked-array-iterator-class.md) i obsługuje te same przeciążenia i członków. Aby uzyskać więcej informacji na temat funkcji sprawdzonego iteratora z przykładami kodu, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iterator >

**Namespace:** stdext

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
