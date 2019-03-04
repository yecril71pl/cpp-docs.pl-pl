---
title: 'Wyjątki: Zmiany w makrach wyjątków w wersji 3.0 lub nowszej'
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: fb51ad91e001f0ed153bf4fdb5aa598ab5ba5042
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291226"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Wyjątki: Zmiany w makrach wyjątków w wersji 3.0 lub nowszej

Jest to zaawansowane tematu.

W MFC w wersji 3.0 i nowszych należy używać wyjątków języka C++ zostały zmienione makra obsługi wyjątków. W tym artykule wyjaśniono, jak te zmiany mogą wpływać na zachowania istniejący kod, który używa makra.

W tym artykule omówiono następujące tematy:

- [Typy wyjątków i makra CATCH](#_core_exception_types_and_the_catch_macro)

- [Ponownie zgłaszanie wyjątków](#_core_re.2d.throwing_exceptions)

##  <a name="_core_exception_types_and_the_catch_macro"></a> Typy wyjątków i makra CATCH

We wcześniejszych wersjach programu MFC **CATCH** — makro używane informacje typu run-time MFC, aby określić typ wyjątku; ustalić typ wyjątku, oznacza to, w obszarze przechwytywania. Poza wyjątkami C++ jednak typ wyjątku jest zawsze określany w lokalizacją throw według typu obiektu wyjątku, który jest generowany. To spowoduje niezgodności w rzadkich przypadkach, gdy typ wskaźnika do obiektu zgłoszony różni się od typu obiektu zgłoszony.

Poniższy przykład ilustruje konsekwencją tej różnicy między MFC w wersji 3.0 i wcześniejszych wersji:

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

Ten kod zachowuje się inaczej w wersji 3.0 lub nowszej, ponieważ kontrola zawsze przechodzi do pierwszej **catch** blok z pasujących deklaracji wyjątku. Wynik wyrażenia throw

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

jest zgłaszany jako `CException*`, nawet jeśli jest konstruowany jako `CCustomException`. **CATCH** makra w MFC w wersji 2.5 i wcześniejszych zastosowań `CObject::IsKindOf` do testowania typu w czasie wykonywania. Ponieważ wyrażenie

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

ma wartość true, pierwszy blok catch przechwytuje wyjątek. Drugi blok catch w wersji 3.0, która używa wyjątków języka C++, aby zaimplementować wiele makra obsługi wyjątków, pasuje do zgłoszenia `CException`.

Kod jest mało prawdopodobna. Jest zwykle wyświetlany, gdy obiekt wyjątku jest przekazywany do innej funkcji, która akceptuje ogólnego `CException*`, wykonuje przetwarzanie "throw przed" i na koniec zgłasza wyjątek.

Aby obejść ten problem, Przenieś wyrażenia throw z funkcji do kodu wywołującego i wyjątku rzeczywistego typu, o których wiadomo w czasie, kompilator wyjątek jest generowany.

##  <a name="_core_re.2d.throwing_exceptions"></a> Ponownie zgłaszanie wyjątków

W bloku catch nie można zgłosić tego samego wskaźnika wyjątek, który go przechwycił.

Na przykład, ten kod był prawidłowy w poprzednich wersjach, ale będzie mieć nieoczekiwane wyniki z wersji 3.0 lub nowszej:

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

Za pomocą **THROW** w catch block powoduje, że wskaźnik `e` do usunięcia, tak aby witryny zewnętrznej catch, zostanie wyświetlony nieprawidłowy wskaźnik. Użyj **THROW_LAST** ponownie zgłosić `e`.

Aby uzyskać więcej informacji, zobacz [wyjątków: Przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
