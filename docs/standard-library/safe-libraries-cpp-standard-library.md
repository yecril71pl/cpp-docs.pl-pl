---
title: 'Bezpieczne biblioteki: Standardowa biblioteka C++ | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
dev_langs:
- C++
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
ms.assetid: 3993340f-1f29-4d81-b3f5-52a52bc8e148
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 73af558c7d192ba335e79605935a79579353ef64
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="safe-libraries-c-standard-library"></a>Bezpieczne biblioteki: Standardowa biblioteka C++

Wprowadzono kilka ulepszeń bibliotek, które są dostarczane z programem Visual C++, w tym standardowa biblioteka C++, aby były bardziej bezpieczne.

Kilka metod w standardowej bibliotece C++ zostały zidentyfikowane jako potencjalnie niebezpieczne, ponieważ mogą one prowadzić do przepełnienia buforu lub inne zmiany kodu. Nie zaleca się korzystanie z tych metod i utworzono nowe, bardziej bezpieczne metody je zastąpić. Te nowe metody wszystkie zakończone w `_s`.

Aby lepiej zabezpieczyć Iteratory i algorytmy wprowadzono również kilka ulepszeń. Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md), [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md) i [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Uwagi

W poniższej tabeli przedstawiono metody standardowa biblioteka C++, które są potencjalnie niebezpieczne, a także ich odpowiedniki bezpieczniejsze:

|Potencjalnie niebezpiecznych — metoda|Odpowiednik bezpieczniejsze|
|-------------------------------|----------------------|
|[Kopiuj](../standard-library/basic-string-class.md#copy)|[basic_string::_Copy_s](../standard-library/basic-string-class.md#copy_s)|
|[Kopiuj](../standard-library/char-traits-struct.md#copy)|[char_traits::_Copy_s](../standard-library/char-traits-struct.md#copy_s)|

Jeśli wywołujesz jednej z metod potencjalnie niebezpieczne, powyżej lub korzystania z Iteratory kompilator wygeneruje [C4996 ostrzeżenie kompilatora (poziom 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Aby uzyskać informacje dotyczące wyłączenie tych ostrzeżeń, zobacz [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="in-this-section"></a>W tej sekcji

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)

[_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)

[Zaznaczone iteratory](../standard-library/checked-iterators.md)

[Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
