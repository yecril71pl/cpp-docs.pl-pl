---
title: 'Wyjątki: zgłaszanie wyjątków z własnych funkcji'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
ms.openlocfilehash: 6484594df7636fd52ac46ab1cc212c8e2ec0278e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359275"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Wyjątki: zgłaszanie wyjątków z własnych funkcji

Istnieje możliwość użycia paradygmatu obsługi wyjątków MFC wyłącznie do połowu wyjątków zgłaszanych przez funkcje w MFC lub innych bibliotek. Oprócz przechwytywania wyjątków zgłaszanych przez kod biblioteki, można zgłaszać wyjątki z własnego kodu, jeśli piszesz funkcje, które mogą wystąpić wyjątkowe warunki.

Gdy wyjątek, wykonanie bieżącej funkcji jest zatrzymany i przeskakuje bezpośrednio do **catch** bloku wewnętrznej ramki wyjątku. Mechanizm wyjątku pomija normalną ścieżkę wyjścia z funkcji. W związku z tym należy pamiętać, aby usunąć te bloki pamięci, które zostaną usunięte w normalnym wyjściu.

#### <a name="to-throw-an-exception"></a>Aby zgłosić wyjątek

1. Użyj jednej z funkcji pomocnika MFC, takich jak `AfxThrowMemoryException`. Te funkcje zgłaszają wstępnie przydzielony obiekt wyjątku odpowiedniego typu.

   W poniższym przykładzie funkcja próbuje przydzielić dwa bloki pamięci i zgłasza wyjątek, jeśli albo alokacji nie powiedzie się:

   [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   Jeśli pierwsza alokacja nie powiedzie się, można po prostu zgłosić wyjątek pamięci. Jeśli pierwsza alokacja zakończy się pomyślnie, ale drugi nie powiedzie się, należy zwolnić pierwszy blok alokacji przed wyzwoleniem wyjątku. Jeśli obie alokacje powiedzie się, można postępować normalnie i zwolnić bloki po zamknięciu funkcji.

     - lub -

1. Użyj wyjątku zdefiniowanego przez użytkownika, aby wskazać warunek problemu. Można zgłosić element dowolnego typu, nawet całej klasy, jako wyjątek.

   Poniższy przykład próbuje odtworzyć dźwięk za pośrednictwem urządzenia wave i zgłasza wyjątek, jeśli występuje błąd.

   [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
> Domyślna obsługa wyjątków MFC dotyczy tylko wskaźników `CException` do obiektów `CException`(i obiektów klas pochodnych). Powyższy przykład pomija mechanizm wyjątków MFC.

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
