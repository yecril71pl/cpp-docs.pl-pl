---
title: 'Bezpieczne biblioteki: Standardowa biblioteka C++'
ms.date: 11/04/2016
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
ms.assetid: 3993340f-1f29-4d81-b3f5-52a52bc8e148
ms.openlocfilehash: 0c8f2de77255015254eabe018399f913b4582b7c
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220470"
---
# <a name="safe-libraries-c-standard-library"></a>Bezpieczne biblioteki: Standardowa biblioteka C++

Wprowadzono kilka ulepszeń bibliotek, które są dostarczane z firmą Microsoft C++, w tym C++ bibliotekę standardową, aby zwiększyć ich bezpieczeństwo.

Kilku metod w standardowej biblioteki języka C++ zostały zidentyfikowane jako potencjalnie niebezpieczne, ponieważ mogą one prowadzić do przepełnienia buforu lub innych wada kodu. Nie zaleca się korzystanie z tych metod i je zastąpić zostały utworzone nowe, bardziej bezpiecznymi metodami. Te nowe metody wszystkie zakończone w `_s`.

Aby zwiększyć bezpieczeństwo iteratorów i algorytmów wprowadzono również kilka ulepszeń. Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md), [Debug Iterator Support](../standard-library/debug-iterator-support.md) i [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Uwagi

W poniższej tabeli wymieniono metody standardowej biblioteki języka C++, które są potencjalnie niebezpieczne, a także ich odpowiednika bezpieczniejsze:

|Potencjalnie niebezpieczne — metoda|Odpowiednik bezpieczniejsze|
|-------------------------------|----------------------|
|[Kopiuj](../standard-library/basic-string-class.md#copy)|[basic_string::_Copy_s](../standard-library/basic-string-class.md#copy_s)|
|[Kopiuj](../standard-library/char-traits-struct.md#copy)|[char_traits::_Copy_s](../standard-library/char-traits-struct.md#copy_s)|

Jeśli wywołanie jednej z powyższych metod potencjalnie niebezpieczne lub jeśli używasz niepoprawnie Iteratory, kompilator wygeneruje [ostrzeżenie kompilatora (poziom 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Aby uzyskać informacji na temat sposobu wyłączania te ostrzeżenia, zobacz [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="in-this-section"></a>W tej sekcji

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)

[_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)

[Zaznaczone iteratory](../standard-library/checked-iterators.md)

[Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
