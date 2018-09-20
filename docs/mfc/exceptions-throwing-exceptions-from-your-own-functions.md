---
title: 'Wyjątki: Zgłaszanie wyjątków z własnych funkcji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6ef86f54442031b4383e6a0b8cc6f57e4e53d58
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418427"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Wyjątki: zgłaszanie wyjątków z własnych funkcji

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

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

