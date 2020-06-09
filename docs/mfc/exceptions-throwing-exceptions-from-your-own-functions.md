---
title: 'Wyjątki: zgłaszanie wyjątków z własnych funkcji'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
ms.openlocfilehash: ebdfea18e6e8445dd734bf43fb6a4ecf422975e9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622747"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Wyjątki: zgłaszanie wyjątków z własnych funkcji

Istnieje możliwość użycia modelu obsługi wyjątków MFC wyłącznie do przechwytywania wyjątków zgłoszonych przez funkcje w MFC lub innych bibliotekach. Oprócz przechwytywania wyjątków zgłoszonych przez kod biblioteki można generować wyjątki z własnego kodu, jeśli piszesz funkcje, które mogą napotkać wyjątkowe warunki.

Gdy wyjątek jest zgłaszany, wykonywanie bieżącej funkcji jest zatrzymane i przechodzi bezpośrednio do bloku **catch** najbardziej wewnętrznej ramki wyjątku. Mechanizm wyjątków pomija normalne ścieżki wyjścia z funkcji. W związku z tym należy koniecznie usunąć te bloki pamięci, które zostałyby usunięte w normalnym zakończeniu.

#### <a name="to-throw-an-exception"></a>Aby zgłosić wyjątek

1. Użyj jednej z funkcji pomocnika MFC, takich jak `AfxThrowMemoryException` . Te funkcje generują wstępnie przydzielony obiekt wyjątku dla odpowiedniego typu.

   W poniższym przykładzie funkcja próbuje przydzielić dwa bloki pamięci i zgłasza wyjątek, jeśli alokacja nie powiedzie się:

   [!code-cpp[NVC_MFCExceptions#17](codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   Jeśli pierwsze alokacja nie powiedzie się, można po prostu zgłosić wyjątek pamięci. Jeśli pierwsza alokacja zakończyła się pomyślnie, ale druga z nich kończy się niepowodzeniem, przed wygenerowaniem wyjątku należy zwolnić pierwszy blok alokacji. Jeśli obie alokacje powiodło się, można normalnie wykonać normalne i zwolnić bloki podczas kończenia funkcji.

     - oraz

1. Użyj wyjątku zdefiniowanego przez użytkownika, aby wskazać warunek problemu. Można zgłosić element dowolnego typu, nawet całą klasę, jako wyjątek.

   Poniższy przykład próbuje odtworzyć dźwięk przez urządzenie Wave i zgłasza wyjątek w przypadku wystąpienia błędu.

   [!code-cpp[NVC_MFCExceptions#18](codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
> Domyślna obsługa wyjątków MFC ma zastosowanie tylko do wskaźników do `CException` obiektów (i obiektów `CException` klas pochodnych). W powyższym przykładzie pominięto mechanizm wyjątków MFC.

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](exception-handling-in-mfc.md)
