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
ms.openlocfilehash: 6f23f792f750e4352494bf3e4bde08f0fe360439
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980486"
---
# <a name="using-the-mfc-source-files"></a>Korzystanie z plików źródłowych MFC

Biblioteka Microsoft Foundation Class (MFC) oferuje pełny kod źródłowy. Pliki nagłówkowe (. h) znajdują się w katalogu \atlmfc\include; Pliki implementacji (. cpp) znajdują się w katalogu \atlmfc\src\mfc.

W tej rodzinie artykułów objaśniono konwencje, które są używane przez MFC do komentowania różnych części każdej klasy, co oznaczają te komentarze i czego należy oczekiwać w każdej sekcji. Kreatorzy C++ wizualizacji używają podobnych Konwencji dla klas, które tworzy dla Ciebie, i prawdopodobnie te konwencje będą przydatne dla własnego kodu.

Być może znasz **publiczne**, **chronione**i **prywatne** C++ słowa kluczowe. W plikach nagłówkowych MFC każda klasa może zawierać kilka z nich. Na przykład publiczne zmienne składowe i funkcje mogą znajdować się w więcej niż jednym **publicznym** słowie kluczowym. Jest to spowodowane tym, że MFC oddziela zmienne składowe i funkcje na podstawie ich użycia, a nie typu dostępu, który jest dozwolony. MFC zużywa oszczędne różnice. Nawet elementy uznawane za szczegóły implementacji są często **chronione**i wiele razy są **publiczne**. Chociaż dostęp do szczegółów implementacji nie jest odradzany, MFC nie opuszcza tej decyzji.

Zarówno w przypadku plików źródłowych MFC, jak i plików nagłówkowych tworzonych przez Kreatora aplikacji MFC, znajdziesz Komentarze takie jak te, które znajdują się w deklaracjach klas (zwykle w tej kolejności):

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

Tematy omówione w tej rodzinie artykułów obejmują:

- [Przykład komentarzy](../mfc/an-example-of-the-comments.md)

- [Komentarz//implementacji](../mfc/decrement-implementation-comment.md)

- [Komentarz//konstruktory](../mfc/decrement-constructors-comment.md)

- [Komentarz//atrybuty](../mfc/decrement-attributes-comment.md)

- [Komentarz operacji//](../mfc/decrement-operations-comment.md)

- [Komentarz//— zażądane](../mfc/decrement-overridables-comment.md)

## <a name="see-also"></a>Zobacz także

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
