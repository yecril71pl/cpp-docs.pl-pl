---
title: Korzystanie z setjmp i longjmp
ms.date: 08/14/2018
f1_keywords:
- longjmp_cpp
- setjmp_cpp
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
ms.openlocfilehash: 6adbe22eb684c9a1dda080f6d35a99c55d6c3d30
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227000"
---
# <a name="using-setjmp-and-longjmp"></a>Korzystanie z setjmp i longjmp

Gdy [setjmp](../c-runtime-library/reference/setjmp.md) i [longjmp](../c-runtime-library/reference/longjmp.md) są używane razem, umożliwiają wykonywanie nielokalnych **`goto`** . Są one zwykle używane w kodzie języka C do przekazywania kontroli wykonania do kodu obsługi błędów lub odzyskiwania w wcześniej wywołanej procedurze bez użycia standardowych konwencji wywoływania lub powrotu.

> [!CAUTION]
> Ponieważ `setjmp` i `longjmp` nie obsługują poprawnego niszczenia obiektów ramek stosu portów między kompilatorami C++ i ponieważ mogą one obniżać wydajność, zapobiegając optymalizacji w zmiennych lokalnych, nie zalecamy ich używania w programach C++. Zalecamy użycie **`try`** **`catch`** konstrukcji i.

Jeśli zdecydujesz się używać `setjmp` programów i `longjmp` w programie w języku C++, Dołącz także \<setjmp.h> lub \<setjmpex.h> , aby zapewnić poprawną interakcję między funkcjami a obsługą wyjątków strukturalnych (SEH) lub obsługą wyjątków C++.

**Specyficzne dla firmy Microsoft**

Jeśli użyjesz opcji [/EH](../build/reference/eh-exception-handling-model.md) do skompilowania kodu C++, destruktory dla obiektów lokalnych są wywoływane podczas rozwinięcia stosu. Jeśli jednak użyjesz **/EHS** lub **/EHsc** do kompilowania, a jedna z funkcji, która używa wywołań [noexcept](../cpp/noexcept-cpp.md) `longjmp` , to może się zdarzyć, że w zależności od stanu Optymalizatora zostanie wyłączany destruktor dla tej funkcji.

W kodzie przenośnym, gdy `longjmp` wywołanie jest wykonywane, poprawne zniszczenie obiektów opartych na ramce jest jawnie niegwarantowane przez Standard i może nie być obsługiwane przez inne kompilatory. Aby poinformować Cię, na poziomie ostrzeżenia 4, wywołanie `setjmp` powoduje wystąpienie ostrzegawcze C4611: interakcja między "_setjmp" i zniszczeniem obiektu języka C++ nie jest przenośna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Mieszanie wyjątków C (Structured) i C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)
