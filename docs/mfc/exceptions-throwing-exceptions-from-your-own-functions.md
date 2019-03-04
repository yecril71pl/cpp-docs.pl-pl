---
title: 'Wyjątki: Zgłaszanie wyjątków z własnych funkcji'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
ms.openlocfilehash: 030bf3db9ff305f35cbfb0b518c8704114ce083d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297947"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Wyjątki: Zgłaszanie wyjątków z własnych funkcji

Jest to możliwe za pomocą modelu obsługi wyjątków MFC wyłącznie przechwytują wyjątki zgłaszane przez funkcje MFC lub inne biblioteki. Oprócz przechwytywanie wyjątków zgłaszanych przez kod biblioteki, może generować wyjątki z własnego kodu podczas pisania funkcji, które mogą występować w wyjątkowych warunkach.

Gdy wyjątek jest zgłaszany, wykonywanie bieżącej funkcji jest zatrzymana, a następnie przechodzi bezpośrednio do **catch** bloku ramki najbardziej wewnętrzny wyjątek. Mechanizm wyjątków pomija ścieżki normalne wyjście z funkcji. W związku z tym należy koniecznie Usuń te bloki pamięci, które zostaną usunięte w normalne wyjście.

#### <a name="to-throw-an-exception"></a>Aby zgłosić wyjątek

1. Użyj jednej z funkcji pomocnika MFC, takich jak `AfxThrowMemoryException`. Te funkcje zgłaszać obiekt przydzielony wstępnie wyjątek odpowiedniego typu.

   W poniższym przykładzie funkcja próbuje przydzielić dwóch bloków pamięci i zgłasza wyjątek, jeśli albo alokacja nie powiedzie się:

   [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   Jeśli pierwsza alokacja nie powiedzie się, można po prostu Zgłoś wyjątek pamięci. Jeśli pierwszy alokacji zakończy się pomyślnie, ale drugi kończy się niepowodzeniem, należy zwolnić pierwszego bloku alokacji przed zostanie zgłoszony wyjątek. Jeśli oba alokacje powiedzie się, możesz przejść normalnie i wolne bloki, podczas zamykania funkcji.

     - lub —

1. Użyj wyjątków zdefiniowanych przez użytkownika, aby wskazać Warunek problem. Element dowolnego typu, a nawet całą klasę, może zgłosić jako wyjątek.

   Poniższy przykład próbuje odtwarzanie dźwięku za pomocą urządzenia wave i zgłasza wyjątek, jeśli wystąpi awaria.

   [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
>  Biblioteki MFC domyślna obsługa wyjątków, który ma zastosowanie tylko do wskaźników do `CException` obiektów (i obiektów `CException`-klas pochodnych). W powyższym przykładzie pomija mechanizm wyjątków MFC.

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
