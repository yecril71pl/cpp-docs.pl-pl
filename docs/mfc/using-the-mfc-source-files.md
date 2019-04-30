---
title: Korzystanie z plików źródłowych MFC
ms.date: 11/04/2016
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: ac8d8ea64de9fd93487b3108857669931e31d0be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411464"
---
# <a name="using-the-mfc-source-files"></a>Korzystanie z plików źródłowych MFC

Biblioteka Microsoft Foundation Class (MFC) dostarcza pełny kod źródłowy. Pliki nagłówkowe (.h) znajdują się w katalogu \atlmfc\include. pliki implementacji (.cpp) znajdują się w katalogu \atlmfc\src\mfc.

Tej rodziny artykułów opisano konwencje, używane przez MFC do komentarzy z różnymi częściami usługi każdej klasy, co oznaczają te komentarze i czego oczekiwać można znaleźć w każdej sekcji. Kreatorów Visual C++ Użyj podobne konwencje dla klas, które tworzą dla Ciebie, a użytkownik będzie prawdopodobnie przydatne tych konwencji własnego kodu.

Można zapoznać się z **publicznych**, **chronione**, i **prywatnej** słów kluczowych języka C++. Podczas wyszukiwania w plikach nagłówkowych MFC, znajdzie się, że każda klasa może mieć kilka z nich. Na przykład może być publicznego elementu członkowskiego zmiennych i funkcji w obszarze więcej niż jeden **publicznych** — słowo kluczowe. Jest to spowodowane MFC oddziela zmienne Członkowskie i funkcje w zależności od ich użycia, nie przez typ dostępu przyznany. MFC wykorzystuje **prywatnej** oszczędnie; nawet elementy uważane za szczegółów implementacji ogólnie są chronione oraz wiele razy były publiczne. Chociaż dostęp do szczegółów implementacji nie zaleca się, MFC pozostawia decyzji dla Ciebie.

W plikach źródłowych MFC i plików tworzonych przez Kreatora aplikacji MFC można znaleźć komentarze, takie jak te w obrębie deklaracji klasy (zwykle w tej kolejności):

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

Tematy omówione w tej rodzinie artykuły obejmują:

- [Przykład komentarzy](../mfc/an-example-of-the-comments.md)

- [/ / Komentarz dotyczący implementacji](../mfc/decrement-implementation-comment.md)

- [/ / Komentarz dotyczący konstruktorów](../mfc/decrement-constructors-comment.md)

- [/ / Atrybuty komentarz](../mfc/decrement-attributes-comment.md)

- [/ / Komentarz dotyczący operacji](../mfc/decrement-operations-comment.md)

- [/ / / / Overridables komentarz](../mfc/decrement-overridables-comment.md)

## <a name="see-also"></a>Zobacz także

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
