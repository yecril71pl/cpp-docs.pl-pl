---
title: — Komentarz dotyczący implementacji
ms.date: 11/04/2016
helpviewer_keywords:
- Implementation comment in MFC source files
- comments, MFC
- MFC source files, Implementation comment
- comments, Implementation comments
ms.assetid: 4d799c07-8e71-4a6b-90ab-8282d6ff48ce
ms.openlocfilehash: ab69fa25cc8dece635097f17bae97f831f7ec87f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552896"
---
# <a name="-implementation-comment"></a>Komentarz // Implementation

`// Implementation` Sekcji jest najbardziej ważną częścią dowolnego deklaracji klasy MFC.

Ta sekcja zawiera wszystkie wszystkich szczegółów implementacji. Zmienne Członkowskie i funkcje składowe mogą być wyświetlane w tej sekcji. Wszystko, czego poniżej tego wiersza można zmienić w przyszłych wydaniach MFC. Chyba, że nie można uniknąć, nie należy polegać na poniższe szczegóły `// Implementation` wiersza. Ponadto elementów członkowskich zadeklarowanych pod linią implementacją nie zostały zamieszczone, mimo że niektóre implementacja została omówiona w Uwagi techniczne. Zastąpienia funkcji wirtualnych w klasie bazowej znajdują się w tej sekcji, niezależnie od tego, która sekcja funkcji klasy bazowej jest zdefiniowana, ponieważ przyjęto, że fakt, że funkcja zastępuje implementacji klasy podstawowej szczegółowo opisuje implementacja. Zazwyczaj te elementy członkowskie są chronione, ale nie zawsze.

Zwróć uwagę, z `CStdioFile` listę w obszarze [przykład komentarzy](../mfc/an-example-of-the-comments.md) , elementy członkowskie zadeklarowany poniżej `// Implementation` komentarz może być zadeklarowana jako **publicznych**, **chronione**, lub **prywatnej**. Te elementy członkowskie należy używać ostrożnie, tylko, ponieważ mogą one ulec zmianie w przyszłości. Deklarowanie grupy elementów członkowskich jako **publicznych** może być konieczne w celu wykonania biblioteki klasy do prawidłowego działania. Oznacza to jednak nie może być bezpiecznie używać elementów członkowskich zadeklarowanych tak.

> [!NOTE]
>  Może się okazać komentarze pozostałe typy powyżej lub poniżej `// Implementation` komentarz. W obu przypadkach opisano rodzaje elementów członkowskich zadeklarowanych pod nimi. Jeśli występują one poniżej `// Implementation` komentarz, należy przyjąć, że członkowie mogą ulec zmianie w przyszłych wersji MFC.

## <a name="see-also"></a>Zobacz też

[Korzystanie z plików źródłowych MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Przykład komentarzy](../mfc/an-example-of-the-comments.md)<br/>
[Komentarz / / constructors](../mfc/decrement-constructors-comment.md)<br/>
[Komentarz / / Attributes](../mfc/decrement-attributes-comment.md)<br/>
[Komentarz / / Operations](../mfc/decrement-operations-comment.md)<br/>
[Komentarz / / Overridables](../mfc/decrement-overridables-comment.md)

