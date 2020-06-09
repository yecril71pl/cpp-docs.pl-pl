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
ms.openlocfilehash: 5db90422f78fc6ca3bc2a182f9569c33db56cad1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623207"
---
# <a name="creating-stack-and-queue-collections"></a>Tworzenie kolekcji stosów i kolejek

W tym artykule wyjaśniono, jak utworzyć inne struktury danych, takie jak [stosy](#_core_stacks) i [kolejki](#_core_queues), z klas MFC list. Przykłady używają klas pochodnych z `CList` , ale można ich używać `CList` bezpośrednio, o ile nie trzeba dodawać funkcjonalności.

## <a name="stacks"></a><a name="_core_stacks"></a>Stack

Ponieważ standardowa kolekcja list ma zarówno nagłówek, jak i ogon, można łatwo utworzyć kolekcję list pochodnych, która śladuje zachowanie pierwszego stosu. Stos przypomina stos zasobników w Cafeteria. Gdy zasobniki są dodawane do stosu, są one umieszczane na stosie. Ostatni dodany zasobnik jest pierwszym, który ma zostać usunięty. Funkcja członkowska kolekcji list `AddHead` i `RemoveHead` może służyć do dodawania i usuwania elementów specyficznych dla nagłówka listy. w ten sposób ostatnio dodany element jest pierwszy do usunięcia.

#### <a name="to-create-a-stack-collection"></a>Aby utworzyć kolekcję stosu

1. Utwórz nową klasę listy z jednej z istniejących klas list MFC i Dodaj więcej funkcji Członkowskich, aby zapewnić obsługę funkcji operacji stosu.

   Poniższy przykład pokazuje, jak dodać funkcje członkowskie, aby wypchnąć elementy na stosie, wgląd do górnego elementu stosu i wyskakujący górny element ze stosu:

   [!code-cpp[NVC_MFCCollections#20](codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

Należy zauważyć, że takie podejście ujawnia `CObList` klasę bazową. Użytkownik może wywołać dowolną `CObList` funkcję członkowską, niezależnie od tego, czy ma sens dla stosu, czy nie.

## <a name="queues"></a><a name="_core_queues"></a>Tworzone

Ponieważ standardowa kolekcja list ma zarówno nagłówek, jak i ogon, można również łatwo utworzyć kolekcję list pochodnych, która naśladuje zachowanie kolejki pierwszej w pierwszej kolejności. Kolejka jest taka sama jak linia osób w Cafeteria. Pierwszy użytkownik w wierszu jest pierwszym, który ma być obsługiwany. W miarę jak coraz więcej osób przechodzi do końca wiersza w celu zaczekania. Funkcja członkowska kolekcji list `AddTail` i `RemoveHead` może służyć do dodawania i usuwania elementów specyficznych dla głowy lub ogona listy. w ten sposób ostatnio dodany element jest zawsze ostatni do usunięcia.

#### <a name="to-create-a-queue-collection"></a>Aby utworzyć kolekcję kolejek

1. Utwórz nową klasę listy z jednej ze wstępnie zdefiniowanych klas list dostarczonych z biblioteka MFC i Dodaj więcej funkcji Członkowskich do obsługi semantyki operacji w kolejce.

   Poniższy przykład pokazuje, jak można dołączyć funkcje członkowskie, aby dodać element na końcu kolejki i pobrać element z przodu kolejki.

   [!code-cpp[NVC_MFCCollections#21](codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>Zobacz też

[Kolekcje](collections.md)
