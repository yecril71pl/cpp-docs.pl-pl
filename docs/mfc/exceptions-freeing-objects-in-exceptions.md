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
ms.openlocfilehash: 49c7c6b0481f90baa23609c1bb1596deda49f7bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371997"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Wyjątki: zwalnianie obiektów w wyjątkach

W tym artykule wyjaśniono potrzebę i metodę zwalniania obiektów, gdy wystąpi wyjątek. Tematy obejmują:

- [Obsługa wyjątku lokalnie](#_core_handling_the_exception_locally)

- [Zgłaszanie wyjątków po zniszczeniu obiektów](#_core_throwing_exceptions_after_destroying_objects)

Wyjątki generowane przez strukturę lub przez aplikację przerwać normalny przepływ programu. W związku z tym jest bardzo ważne, aby zachować ścisłą śledzić obiektów, dzięki czemu można prawidłowo usunąć je w przypadku, gdy wyjątek.

Istnieją dwie podstawowe metody, aby to zrobić.

- Obsługa wyjątków lokalnie przy użyciu **try** i **catch** słowa kluczowe, a następnie zniszczyć wszystkie obiekty z jednej instrukcji.

- Zniszczyć dowolny obiekt w bloku **catch** przed zrzuceniem wyjątku poza blokiem do dalszej obsługi.

Te dwa podejścia są zilustrowane poniżej jako rozwiązania następującego problematycznego przykładu:

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

Jak napisano powyżej, nie zostaną usunięte, `myPerson` jeśli `SomeFunc`wyjątek jest generowany przez . Wykonanie przeskakuje bezpośrednio do następnego zewnętrznego programu obsługi wyjątków, pomijając normalne wyjście funkcji i kod, który usuwa obiekt. Wskaźnik do obiektu wykracza poza zakres, gdy wyjątek opuszcza funkcję, a pamięć zajęta przez obiekt nigdy nie zostanie odzyskana, dopóki program jest uruchomiony. Jest to przeciek pamięci; zostanie wykryty przy użyciu diagnostyki pamięci.

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a>Obsługa wyjątku lokalnie

Paradygmat **try/catch** zapewnia defensywną metodę programowania, aby uniknąć przecieków pamięci i upewnić się, że obiekty są niszczone, gdy występują wyjątki. Na przykład przykład pokazany wcześniej w tym artykule można przepisać w następujący sposób:

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

W tym nowym przykładzie konfiguruje program obsługi wyjątków, aby przechwyć wyjątek i obsłużyć go lokalnie. Następnie opuszcza funkcję normalnie i niszczy obiekt. Ważnym aspektem tego przykładu jest, że kontekst do połowu wyjątek jest ustanawiany z **try/catch** bloków. Bez lokalnej ramki wyjątku funkcja nigdy nie wie, że wyjątek został zgłoszony i nie będzie miał szansy, aby zakończyć normalnie i zniszczyć obiekt.

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a>Zgłaszanie wyjątków po zniszczeniu obiektów

Innym sposobem obsługi wyjątków jest przekazanie ich do następnego kontekstu obsługi wyjątków zewnętrznych. W bloku **catch** można wykonać pewne oczyszczanie lokalnie przydzielonych obiektów, a następnie zgłosić wyjątek do dalszego przetwarzania.

Funkcja rzucania może lub nie musi zdążeć alokacji obiektów sterty. Jeśli funkcja zawsze określa alokacji obiektu sterty przed zwróceniem w normalnym przypadku, funkcja powinna również zdyskontować obiekt sterty przed zgłosić wyjątek. Z drugiej strony, jeśli funkcja zwykle nie decolokować obiektu przed zwróceniem w normalnym przypadku, następnie należy zdecydować w zależności od przypadku, czy obiekt sterty powinny być cofnięte alokacji.

W poniższym przykładzie pokazano, jak lokalnie przydzielone obiekty mogą być czyszczone:

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

Mechanizm wyjątku automatycznie przydziela obiekty ramki; destruktor obiektu ramki jest również nazywany.

Jeśli wywołasz funkcje, które mogą zgłaszać wyjątki, można użyć **try/catch** bloków, aby upewnić się, że można złapać wyjątki i mają szansę zniszczyć wszystkie obiekty, które zostały utworzone. W szczególności należy pamiętać, że wiele funkcji MFC można zgłaszać wyjątki.

Aby uzyskać więcej informacji, zobacz [Wyjątki: Przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
