---
title: 'Wyjątki: Przechwytywanie i usuwanie wyjątków | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ad6ad1c4d1d7d74f60acbd985ee549d708ae28f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074127"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Wyjątki: przechwytywanie i usuwanie wyjątków

Następujące instrukcje i przykłady pokazują, jak przechwytywać i usuwanie wyjątków. Aby uzyskać więcej informacji na temat **spróbuj**, **catch**, i **throw** słów kluczowych, zobacz [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md).

Inne programy obsługi wyjątków należy usunąć obiekty wyjątków, które obsługują, ponieważ nie można usunąć wyjątku powoduje przeciek pamięci, zawsze wtedy, gdy ten kod przechwytuje wyjątek.

Twoje **catch** bloku musi usunąć wyjątek po:

- **Catch** bloku zgłasza nowy wyjątek.

   Nie należy oczywiście usunąć wyjątek, jeśli zgłosić ten sam wyjątek:

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- Wykonywanie powraca z poziomu **catch** bloku.

> [!NOTE]
>  Podczas usuwania `CException`, użyj `Delete` funkcja elementu członkowskiego, można usunąć wyjątku. Nie używaj **Usuń** — słowo kluczowe, ponieważ jego może zakończyć się niepowodzeniem, jeśli wyjątek nie znajduje się na stosie.

#### <a name="to-catch-and-delete-exceptions"></a>Aby przechwycić i usuwanie wyjątków

1. Użyj **spróbuj** — słowo kluczowe, aby skonfigurować **spróbuj** bloku. Wykonaj wszelkie instrukcje programu, które mogą zgłosić wyjątek w ramach **spróbuj** bloku.

   Użyj **catch** — słowo kluczowe, aby skonfigurować **catch** bloku. Umieść kod obsługi wyjątków w **catch** bloku. Kod w **catch** blok jest wykonywany tylko wtedy, gdy kod w **spróbuj** bloku zgłasza wyjątek typu określonego w **catch** instrukcji.

   Poniższej przedstawiono szkielet jak **spróbuj** i **catch** zwykle ułożone bloków:

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Gdy wyjątek jest zgłaszany, kontrola przechodzi do pierwszej **catch** bloku, w których deklaracji wyjątku jest zgodny z typem wyjątku. Selektywnie mogą obsługiwać różne rodzaje wyjątków za pomocą sekwencyjne **catch** blokuje wymienione poniżej:

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Aby uzyskać więcej informacji, zobacz [wyjątki: konwertowanie z makr wyjątków MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

