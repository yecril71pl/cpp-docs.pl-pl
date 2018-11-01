---
title: 'Wyjątki: zwalnianie obiektów w wyjątkach'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
ms.openlocfilehash: 6e03d46a2600458f3107efa6e0b6b0d643c9b160
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442474"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Wyjątki: zwalnianie obiektów w wyjątkach

W tym artykule opisano potrzebę oraz sposób zwalnianie obiektów w przypadku, gdy wystąpi wyjątek. Tematy obejmują:

- [Obsługa wyjątku lokalnie](#_core_handling_the_exception_locally)

- [Zgłaszanie wyjątków po niszczenie obiektów](#_core_throwing_exceptions_after_destroying_objects)

Wyjątki zgłaszane przez platformę lub przepływu normalnego program przerwania aplikacji. W związku z tym jest bardzo ważne szczegółowe śledzenie obiektów, dzięki czemu można poprawnie usunięcia z nich w przypadku, gdy zostanie zgłoszony wyjątek.

Istnieją dwie podstawowe metody, aby to zrobić.

- Obsługa wyjątków lokalnie przy użyciu **spróbuj** i **catch** słów kluczowych, a następnie zniszcz wszystkich obiektów za pomocą jednej instrukcji.

- Zniszcz dowolnego obiektu w **catch** blok przed zgłaszania wyjątku poza blokiem więcej obsługę.

Poniżej przedstawiono te dwie metody jako rozwiązania do następujących problemów:

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

Jak napisany powyżej, `myPerson` nie zostaną usunięte, jeśli wyjątek jest generowany przez `SomeFunc`. Wykonywanie przeskakuje bezpośrednio do następnego obsługi wyjątków zewnętrzne, z pominięciem zakończenia normalnej funkcji i kod, który usuwa obiekt. Wskaźnik do obiektu wykracza poza zakres, gdy wyjątek pozostawia funkcji, a pamięć zajęta przez obiekt nigdy nie będzie można odzyskać, tak długo, jak działa program. Jest to przeciek pamięci; może zostać wykryte za pomocą diagnostyki pamięci.

##  <a name="_core_handling_the_exception_locally"></a> Obsługa wyjątku lokalnie

**Bloku try/catch** paradygmat zapewnia obrony programowania unikanie przecieków pamięci i zapewnienie, że obiekty są niszczone, wystąpieniu wyjątku. Na przykład przykładzie przedstawionym wcześniej w tym artykule można dopasować w następujący sposób:

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

W tym przykładzie nowe konfiguruje obsługi wyjątków w celu wyłapania wyjątku i obsługiwać go lokalnie. Następnie kończy działanie funkcji normalnie i niszczy obiekt. Ważnym aspektem w tym przykładzie jest to, że kontekstu, aby przechwycić wyjątek jest nawiązywane z **bloku try/catch** bloków. Bez ramki lokalnego wyjątek funkcji będzie nigdy nie wiadomo, że wyjątek gdyby były zgłaszane i nie będzie zawierało szansę, aby zamknąć normalnie i zniszcz obiekt.

##  <a name="_core_throwing_exceptions_after_destroying_objects"></a> Zgłaszanie wyjątków po niszczenie obiektów

Innym sposobem obsługi wyjątków jest przekazać je dalej zewnętrzne kontekście obsługi wyjątków. W swojej **catch** bloku, można wykonać niektóre Oczyszczanie lokalnie przydzielonych obiektów i następnie generują wyjątku celu dalszego przetwarzania.

Zgłaszanie funkcji może lub nie może być konieczne cofnięcie przydziału obiektów sterty. Jeśli funkcja zawsze powoduje cofnięcie przydziału obiektu sterty przed zwróceniem w to normalna sytuacja, a następnie funkcja powinna również cofnięcie przydziału obiekt sterty przed zostanie zgłoszony wyjątek. Z drugiej strony Jeśli funkcja nie zwykle cofnięcie przydziału obiektu przed zwróceniem w przypadku normalnych, następnie należy zdecydować, w przypadku, czy obiekt sterty należy cofnąć przydział.

W poniższym przykładzie pokazano, jak lokalnie przydzielone obiekty można czyścić:

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

Mechanizm wyjątków automatycznie zwalnia ramki obiektów; Skrót destruktor obiekt w ramce.

Jeśli chcesz wywołać funkcje, które mogą zgłosić wyjątek, możesz użyć **bloku try/catch** bloków, aby upewnić się, możesz rejestrować wyjątki i zdąży niszczy wszystkie obiekty, które zostały utworzone. W szczególności należy pamiętać, że wiele funkcji MFC mogą zgłaszać wyjątki.

Aby uzyskać więcej informacji, zobacz [wyjątki: wyjątki połowowe i usuwanie](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

