---
title: Tworzenie kolekcji stosów i kolejek
ms.date: 11/04/2016
helpviewer_keywords:
- MFC collection classes [MFC], stack collections
- collections, stack
- stack
- collection classes [MFC], creating
- queue collections
- MFC collection classes [MFC], queue collections
- stack collections
- collections, queue
ms.assetid: 3c7bc198-35f0-4fc3-aaed-6005a0f22638
ms.openlocfilehash: 5b3427f7bb2e46435ddf2768bcbb816f9d7e5c1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371606"
---
# <a name="creating-stack-and-queue-collections"></a>Tworzenie kolekcji stosów i kolejek

W tym artykule wyjaśniono, jak utworzyć inne struktury danych, takie jak [stosy](#_core_stacks) i [kolejki,](#_core_queues)z klas listy MFC. Przykłady używają klas pochodnych , `CList`ale `CList` można użyć bezpośrednio, chyba że trzeba dodać funkcje.

## <a name="stacks"></a><a name="_core_stacks"></a>Stosy

Ponieważ standardowa kolekcja listy ma zarówno głowy i ogona, jest łatwe do utworzenia kolekcji listy pochodnej, która naśladuje zachowanie stosu last-in-first-out. Stos jest jak stos tac w stołówce. Gdy tace są dodawane do stosu, idą na szczycie stosu. Ostatnia dodana taca jest pierwszą, która zostanie usunięta. Funkcje `AddHead` członkowskie kolekcji listy i `RemoveHead` może służyć do dodawania i usuwania elementów specjalnie z głowy listy; w związku z tym ostatnio dodany element jest pierwszym, który zostanie usunięty.

#### <a name="to-create-a-stack-collection"></a>Aby utworzyć kolekcję stosu

1. Wywodź nową klasę listy z jednej z istniejących klas listy MFC i dodaj więcej funkcji członkowskich do obsługi funkcji operacji stosu.

   W poniższym przykładzie pokazano, jak dodać funkcje elementu członkowskiego do wypychania elementów na stosie, zajrzeć do górnego elementu stosu i pop górny element ze stosu:

   [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

Należy zauważyć, że to `CObList` podejście udostępnia podstawowej klasy. Użytkownik może wywołać dowolną `CObList` funkcję elementu członkowskiego, czy ma sens dla stosu, czy nie.

## <a name="queues"></a><a name="_core_queues"></a>Kolejek

Ponieważ standardowa kolekcja listy ma zarówno głowę, jak i ogon, jest również łatwe do utworzenia kolekcji listy pochodnej, która naśladuje zachowanie kolejki first-in-first-out. Kolejka jest jak linia ludzi w stołówce. Pierwsza osoba w kolejce jest pierwszą, która zostanie doręczona. Jak więcej ludzi przychodzi, idą do końca linii, aby czekać na swoją kolej. Funkcje `AddTail` elementu członkowskiego `RemoveHead` kolekcji listy i może służyć do dodawania i usuwania elementów specjalnie z głowy lub ogona listy; w związku z tym ostatnio dodany element jest zawsze ostatnim, który ma zostać usunięty.

#### <a name="to-create-a-queue-collection"></a>Aby utworzyć kolekcję kolejki

1. Wygeneruj nową klasę listy z jednej ze wstępnie zdefiniowanych klas listy dostarczonych z biblioteką klas Programu Microsoft Foundation i dodaj więcej funkcji członkowskich do obsługi semantyki operacji kolejek.

   Poniższy przykład pokazuje, jak można dołączyć funkcje członkowskie, aby dodać element na końcu kolejki i uzyskać element z przodu kolejki.

   [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>Zobacz też

[Kolekcje](../mfc/collections.md)
