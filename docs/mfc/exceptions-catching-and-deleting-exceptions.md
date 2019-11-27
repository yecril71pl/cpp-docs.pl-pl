---
title: 'Wyjątki: przechwytywanie i usuwanie wyjątków'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
ms.openlocfilehash: 0142ffddfb391ae8da878d9e5fe34629cf16cb52
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246693"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Wyjątki: przechwytywanie i usuwanie wyjątków

Poniższe instrukcje i przykłady pokazują, jak przechwytywać i usuwać wyjątki. Aby uzyskać więcej informacji na temat **try**, **catch**i **throw** słów kluczowych, [Zobacz C++ nowoczesne najlepsze rozwiązania dotyczące wyjątków i obsługi błędów](../cpp/errors-and-exception-handling-modern-cpp.md).

Programy obsługi wyjątków muszą usuwać obiekty wyjątków, które są przez nie obsługiwane, ponieważ usunięcie wyjątku powoduje przeciek pamięci, gdy ten kod przechwytuje wyjątek.

Blok **catch** musi usuwać wyjątek, gdy:

- Blok **catch** zgłasza nowy wyjątek.

   Oczywiście nie należy usuwać wyjątku, jeśli zgłosić ten sam wyjątek ponownie:

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- Wykonanie zwraca z wewnątrz bloku **catch** .

> [!NOTE]
>  Podczas usuwania `CException`należy użyć funkcji elementu członkowskiego `Delete`, aby usunąć wyjątek. Nie należy używać słowa kluczowego **delete** , ponieważ może się nie powieść, jeśli na stercie nie ma wyjątku.

#### <a name="to-catch-and-delete-exceptions"></a>Aby przechwytywać i usuwać wyjątki

1. Użyj słowa kluczowego **try** , aby skonfigurować blok **try** . Wykonaj wszelkie instrukcje programu, które mogą zgłosić wyjątek w bloku **try** .

   Użyj słowa kluczowego **catch** , aby skonfigurować blok **catch** . Umieść kod obsługi wyjątków w bloku **catch** . Kod w bloku **catch** jest wykonywany tylko wtedy, gdy kod w bloku **try** zgłasza wyjątek typu określonego w instrukcji **catch** .

   Poniższy szkielet pokazuje, jak bloki **try** i **catch** są zwykle rozmieszczone:

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Gdy wyjątek jest zgłaszany, kontrola przechodzi do pierwszego bloku **catch** , którego deklaracja wyjątku pasuje do typu wyjątku. Można wybiórczo obsługiwać różne typy wyjątków za pomocą bloków kolejnych **catch** , jak pokazano poniżej:

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Aby uzyskać więcej informacji, zobacz [wyjątki: konwertowanie z makr wyjątków MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
