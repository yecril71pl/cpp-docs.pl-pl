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
ms.openlocfilehash: 74022c8bc6af1d2cdf74fa452d4e0483637e542e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365514"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Wyjątki: przechwytywanie i usuwanie wyjątków

Poniższe instrukcje i przykłady pokazują, jak przechwytywać i usuwać wyjątki. Aby uzyskać więcej informacji na temat **try**, **catch**, i **throw** słowa kluczowe, zobacz [Nowoczesne C++ najlepsze rozwiązania dotyczące wyjątków i obsługi błędów.](../cpp/errors-and-exception-handling-modern-cpp.md)

Programy obsługi wyjątków należy usunąć obiekty wyjątków, które obsługują, ponieważ nieuczyszczenie wyjątku powoduje przeciek pamięci, gdy ten kod połowy wyjątek.

Blok **catch** musi usunąć wyjątek, gdy:

- Catch **catch** bloku zgłasza nowy wyjątek.

   Oczywiście nie należy usuwać wyjątku, jeśli ponownie zgłosić ten sam wyjątek:

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- Wykonanie zwraca z wewnątrz **catch** bloku.

> [!NOTE]
> Podczas usuwania `CException`funkcji `Delete` elementu członkowskiego należy użyć funkcji elementu członkowskiego, aby usunąć wyjątek. Nie należy używać **delete** słowa kluczowego, ponieważ może zakończyć się niepowodzeniem, jeśli wyjątek nie znajduje się na stosie.

#### <a name="to-catch-and-delete-exceptions"></a>Aby wychwyć i usunąć wyjątki

1. Użyj słowa kluczowego **try,** aby skonfigurować blok **try.** Wykonaj wszystkie instrukcje programu, które mogą zgłaszać wyjątek w ramach bloku **try.**

   Użyj **catch** słowa kluczowego, aby skonfigurować blok **catch.** Umieść kod obsługi wyjątków w bloku **catch.** Kod w bloku **catch** jest wykonywany tylko wtedy, gdy kod w bloku **try** zgłasza wyjątek typu określonego w **catch** instrukcji.

   Poniższy szkielet pokazuje, jak **próbują** i **złapać** bloki są zwykle rozmieszczone:

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Gdy wyjątek, kontrola przechodzi do pierwszego **bloku catch,** którego deklaracja wyjątku pasuje do typu wyjątku. Można selektywnie obsługiwać różne typy wyjątków z kolejnych bloków **catch,** jak podano poniżej:

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Aby uzyskać więcej informacji, zobacz [Wyjątki: Konwertowanie z makr wyjątków MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
