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
ms.openlocfilehash: ed0ad9b98a69e56df4e66b25bc6ca08cdaaad413
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242409"
---
# <a name="creating-stack-and-queue-collections"></a>Tworzenie kolekcji stosów i kolejek

W tym artykule opisano sposób tworzenia innych struktur danych, takich jak [stosy](#_core_stacks) i [kolejek](#_core_queues), MFC lista klas. W przykładach użyto klasy pochodne `CList`, ale można użyć `CList` bezpośrednio o ile nie trzeba dodawać funkcje.

##  <a name="_core_stacks"></a> Stosy

Ponieważ kolekcji standardowych listy ma head i ogon, to można łatwo utworzyć kolekcję listy pochodnej, która naśladuje zachowanie stosu ostatni wejściu — pierwszy na wyjściu. Stos jest jak stos zasobniki w danymi stołówki. Gdy zasobniki są dodawane do stosu, przejdź na górze stosu. Ostatni zasobnik, dodano jest pierwszy do usunięcia. Funkcje elementów członkowskich kolekcji listy `AddHead` i `RemoveHead` może służyć do dodawania i usuwania elementów w szczególności nagłówek listy; w związku z tym, najbardziej niedawno dodano element jest pierwszy do usunięcia.

#### <a name="to-create-a-stack-collection"></a>Aby utworzyć kolekcję stosu

1. Pochodzić nowa klasa listy z jednej z istniejących klas MFC w liście, a następnie dodać więcej funkcji elementów członkowskich do obsługi funkcji operacji stosu.

   Poniższy przykład przedstawia sposób dodawania elementów członkowskich i wypychania elementów do stosu rzut oka na górnego elementu stosu, pop górnego elementu ze stosu:

   [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

Należy pamiętać, że tego podejścia ujawnia podstawowe `CObList` klasy. Użytkownik może wywoływać dowolną `CObList` funkcję członkowską, czy sens dla stosu lub nie.

##  <a name="_core_queues"></a> kolejki

Ponieważ kolekcji standardowych listy ma head i ogon, również jest łatwo utworzyć kolekcję listy pochodnej, która naśladuje zachowanie kolejką pierwszy wejściu — pierwszy na wyjściu. Kolejka jest jak linia osób z danymi stołówki. Pierwszą osobą w wierszu jest pierwszym, który ma być obsługiwana. Ponieważ pochodzą więcej osób, przejdź do końca wiersza, wyłącz ich oczekiwania. Funkcje elementów członkowskich kolekcji listy `AddTail` i `RemoveHead` może służyć do dodania i usunięcia elementów w szczególności związanych z węzłem głównym lub tail listy; w związku z tym, najbardziej niedawno dodano element zawsze jest ostatnim do usunięcia.

#### <a name="to-create-a-queue-collection"></a>Aby utworzyć kolekcję kolejki

1. Pochodzić nowa klasa listy z jednej ze wstępnie zdefiniowanej listy klas, wyposażone w bibliotece klas Microsoft Foundation, a następnie dodać więcej funkcji elementów członkowskich do obsługi semantykę operacji kolejki.

   Poniższy przykład pokazuje, jak można dołączyć funkcji elementów członkowskich do dodania elementu do końca kolejki i pobrać element z przodu kolejki.

   [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>Zobacz także

[Kolekcje](../mfc/collections.md)
