---
title: 'Wyjątki: zmiany w makrach wyjątków w wersji 3.0'
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 72b343641b0b43d408c5820ca2a2af1de94ce327
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225062"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Wyjątki: zmiany w makrach wyjątków w wersji 3.0

To jest zaawansowany temat.

W MFC w wersji 3,0 i nowszych makra obsługi wyjątków zostały zmienione, aby używać wyjątków C++. Ten artykuł zawiera informacje o tym, jak te zmiany mogą wpływać na zachowanie istniejącego kodu, który używa makr.

W tym artykule omówiono następujące tematy:

- [Typy wyjątków i makro CATCH](#_core_exception_types_and_the_catch_macro)

- [Ponowne wyrzucanie wyjątków](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a>Typy wyjątków i makro CATCH

We wcześniejszych wersjach MFC makro **catch** używało informacji o typie czasu wykonywania MFC do określenia typu wyjątku; Typ wyjątku jest określany innymi słowy w witrynie catch. W przypadku wyjątków języka C++ typ wyjątku jest zawsze określany w witrynie throw przez typ generowanego obiektu wyjątku. Spowoduje to niezgodności w rzadkich przypadkach, gdy typ wskaźnika do wygenerowanego obiektu różni się od typu wygenerowanego obiektu.

Poniższy przykład ilustruje wynik różnicy między wersjami MFC w wersji 3,0 i wcześniejszych:

[!code-cpp[NVC_MFCExceptions#1](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

Ten kod działa inaczej w wersji 3,0, ponieważ kontrolka zawsze przechodzi do pierwszego **`catch`** bloku przy użyciu zgodnej deklaracji wyjątku. Wynik wyrażenia throw

[!code-cpp[NVC_MFCExceptions#19](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

jest zgłaszany jako `CException*` , mimo że jest konstruowany jako `CCustomException` . Makro **catch** w MFC w wersji 2,5 i starszych używa `CObject::IsKindOf` do testowania typu w czasie wykonywania. Ponieważ wyrażenie

[!code-cpp[NVC_MFCExceptions#20](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

ma wartość true, pierwszy blok catch przechwytuje wyjątek. W wersji 3,0, która używa wyjątków C++ do implementowania wielu makr obsługi wyjątków, drugi blok catch pasuje do zgłoszonych `CException` .

Kod podobny do tego jest nietypowy. Zwykle pojawia się, gdy obiekt wyjątku jest przenoszona do innej funkcji, która akceptuje generyczne `CException*` , wykonuje przetwarzanie wstępne, a wreszcie zgłasza wyjątek.

Aby obejść ten problem, Przenieś wyrażenie throw z funkcji do kodu wywołującego i Zgłoś wyjątek rzeczywistego typu znanego dla kompilatora w momencie wygenerowania wyjątku.

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a>Ponowne wyrzucanie wyjątków

Blok catch nie może zgłosić tego samego wskaźnika wyjątku, który został przechwycony.

Na przykład ten kod był prawidłowy w poprzednich wersjach, ale będzie miał nieoczekiwane wyniki w wersji 3,0:

[!code-cpp[NVC_MFCExceptions#2](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

Użycie instrukcji **throw** w bloku catch powoduje usunięcie wskaźnika `e` , dzięki czemu zewnętrzna witryna przechwytywania otrzyma nieprawidłowy wskaźnik. Użyj **THROW_LAST** , aby ponownie zgłosić `e` .

Aby uzyskać więcej informacji, zobacz [wyjątki: Przechwytywanie i usuwanie wyjątków](exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](exception-handling-in-mfc.md)
