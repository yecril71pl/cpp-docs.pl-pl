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
ms.openlocfilehash: 5c1edd4c5d31d9a0e8e5270d074d25b5dd129a0f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184250"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Wyjątki: przechwytywanie i usuwanie wyjątków

Poniższe instrukcje i przykłady pokazują, jak przechwytywać i usuwać wyjątki. Aby uzyskać więcej informacji na **`try`** temat **`catch`** słów kluczowych, i, **`throw`** Zobacz [nowoczesne C++ Best Practices for Exceptions and Error](../cpp/errors-and-exception-handling-modern-cpp.md).

Programy obsługi wyjątków muszą usuwać obiekty wyjątków, które są przez nie obsługiwane, ponieważ usunięcie wyjątku powoduje przeciek pamięci, gdy ten kod przechwytuje wyjątek.

**`catch`** Blok musi usunąć wyjątek, gdy:

- **`catch`** Blok zgłasza nowy wyjątek.

   Oczywiście nie należy usuwać wyjątku, jeśli zgłosić ten sam wyjątek ponownie:

   [!code-cpp[NVC_MFCExceptions#3](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- Wykonanie zwraca z wewnątrz **`catch`** bloku.

> [!NOTE]
> W przypadku usuwania elementu `CException` należy użyć `Delete` funkcji członkowskiej, aby usunąć wyjątek. Nie używaj **`delete`** słowa kluczowego, ponieważ może się to nie powieść, jeśli na stercie nie ma wyjątku.

#### <a name="to-catch-and-delete-exceptions"></a>Aby przechwytywać i usuwać wyjątki

1. Użyj **`try`** słowa kluczowego, aby skonfigurować **`try`** blok. Wykonaj wszelkie instrukcje programu, które mogą zgłosić wyjątek w **`try`** bloku.

   Użyj **`catch`** słowa kluczowego, aby skonfigurować **`catch`** blok. Umieść kod obsługi wyjątków w **`catch`** bloku. Kod w **`catch`** bloku jest wykonywany tylko wtedy, gdy kod w **`try`** bloku zgłasza wyjątek typu określonego w **`catch`** instrukcji.

   Poniższy szkielet pokazuje, jak **`try`** i **`catch`** bloki są zwykle rozmieszczone:

   [!code-cpp[NVC_MFCExceptions#4](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Gdy wyjątek jest zgłaszany, kontrola przechodzi do pierwszego **`catch`** bloku, którego deklaracja wyjątku pasuje do typu wyjątku. Można wybiórczo obsługiwać różne typy wyjątków za pomocą bloków sekwencyjnych **`catch`** , jak pokazano poniżej:

   [!code-cpp[NVC_MFCExceptions#5](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Aby uzyskać więcej informacji, zobacz [wyjątki: konwertowanie z makr wyjątków MFC](exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](exception-handling-in-mfc.md)
