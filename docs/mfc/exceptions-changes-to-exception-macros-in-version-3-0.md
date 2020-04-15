---
title: 'Wyjątki: zmiany w makrach wyjątków w wersji 3.0'
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 82320b0c7ccd6766e016f0437633339f8f8f61d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365494"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Wyjątki: zmiany w makrach wyjątków w wersji 3.0

Jest to zaawansowany temat.

W wersji MFC 3.0 i nowszych makra obsługi wyjątków zostały zmienione na używanie wyjątków języka C++. W tym artykule opisano, jak te zmiany mogą wpływać na zachowanie istniejącego kodu, który używa makr.

W tym artykule omówiono następujące tematy:

- [Typy wyjątków i makro CATCH](#_core_exception_types_and_the_catch_macro)

- [Ponowne zgłaszanie wyjątków](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a>Typy wyjątków i makro CATCH

We wcześniejszych wersjach MFC makr **CATCH** używane informacje o typie wykonywania MFC do określenia typu wyjątku; typ wyjątku jest określany, innymi słowy, w miejscu połowu. Z wyjątkami C++ jednak typ wyjątku jest zawsze określany w witrynie zgłaszania przez typ obiektu wyjątku, który jest zgłaszany. Spowoduje to niezgodności w rzadkich przypadkach, gdy typ wskaźnika do obiektu thrown różni się od typu obiektu generowanego.

Poniższy przykład ilustruje konsekwencję tej różnicy między MFC w wersji 3.0 i wcześniejszych wersjach:

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

Ten kod zachowuje się inaczej w wersji 3.0, ponieważ formant zawsze przechodzi do pierwszego bloku **catch** z pasującą deklaracją wyjątku. Wynik wyrażenia throw

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

jest wyrzucany `CException*`jako , nawet jeśli `CCustomException`jest skonstruowany jako . Makr **CATCH** w wersjach MFC 2.5 i wcześniejszych używa `CObject::IsKindOf` do testowania typu w czasie wykonywania. Ponieważ wyrażenie

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

true, pierwszy blok catch połowy połowy wyjątek. W wersji 3.0, która używa wyjątków C++ do implementacji wielu makr obsługi `CException`wyjątków, drugi blok catch pasuje do rzuconego .

Kod taki jak ten jest rzadkością. Zwykle pojawia się, gdy obiekt wyjątku jest przekazywany do innej funkcji, która akceptuje ogólne, `CException*`wykonuje "pre-throw" przetwarzania i na koniec zgłasza wyjątek.

Aby obejść ten problem, przenieś wyrażenie throw z funkcji do kodu wywołującego i zgłosić wyjątek rzeczywistego typu znanego kompilatorowi w czasie generowania wyjątku.

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a>Ponowne zgłaszanie wyjątków

Blok catch nie może zgłosić tego samego wskaźnika wyjątku, który został przechwycony.

Na przykład ten kod był prawidłowy w poprzednich wersjach, ale będzie miał nieoczekiwane wyniki w wersji 3.0:

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

Za pomocą **THROW** w catch `e` bloku powoduje, że wskaźnik zostanie usunięty, tak, że zewnętrzna witryna catch otrzyma nieprawidłowy wskaźnik. Użyj **THROW_LAST,** aby ponownie `e`rzucić .

Aby uzyskać więcej informacji, zobacz [Wyjątki: Przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
