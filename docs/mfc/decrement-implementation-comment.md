---
title: — Implementacja komentarz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Implementation comment in MFC source files
- comments, MFC
- MFC source files, Implementation comment
- comments, Implementation comments
ms.assetid: 4d799c07-8e71-4a6b-90ab-8282d6ff48ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1556c690478b242d929b8a5558264218ddf0b63e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-implementation-comment"></a>Komentarz // Implementation
`// Implementation` Sekcji jest najbardziej istotną częścią żadnych deklaracji klasy MFC.  
  
 W tej sekcji przechowuje wszystkie szczegóły implementacji. Zarówno zmiennych Członkowskich i funkcji elementów członkowskich może występować w tej sekcji. Wszystko poniżej tego wiersza, można zmienić w przyszłej wersji biblioteki MFC. O ile nie można go uniknąć, nie należy polegać na szczegóły poniżej `// Implementation` wiersza. Ponadto elementów członkowskich zadeklarowanych poniżej wiersza implementacji nie opisano, mimo że niektóre implementacja została szczegółowo opisana w Uwagi techniczne. Zastępowanie funkcji wirtualnych w klasie podstawowej znajdują się w tej sekcji, niezależnie od tego, która sekcja funkcji klasy podstawowej jest zdefiniowana, ponieważ przyjęto, że fakt, że funkcja zastępuje implementację klasy podstawowej szczegóły implementacji. Zazwyczaj te elementy członkowskie są chronione, ale nie zawsze.  
  
 Zwróć uwagę, z `CStdioFile` wyświetlania w obszarze [przykład komentarzy](../mfc/an-example-of-the-comments.md) że członkowie zadeklarowanym poniżej `// Implementation` komentarz może być zadeklarowana jako **publicznego**, `protected`, lub `private`. Tych elementów członkowskich należy używać ostrożnie, tylko, ponieważ mogą one ulec zmianie w przyszłości. Deklarowanie grupy elementów członkowskich jako **publicznego** mogą być niezbędne do implementacji klasy biblioteki działał prawidłowo. Jednak nie oznacza to bezpiecznie może używać elementów członkowskich, więc zadeklarowanych.  
  
> [!NOTE]
>  Może się okazać komentarze pozostałych typów powyżej lub poniżej `// Implementation` komentarza. W obu przypadkach opisują rodzaje elementów członkowskich zadeklarowanych znajdującą się pod nimi. Jeśli występują poniżej `// Implementation` komentarz, powinien założyć, że elementy Członkowskie mogą ulec zmianie w przyszłych wersji biblioteki MFC.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z plików źródłowych MFC](../mfc/using-the-mfc-source-files.md)   
 [Przykład komentarzy](../mfc/an-example-of-the-comments.md)   
 [Komentarz / / constructors](../mfc/decrement-constructors-comment.md)   
 [Komentarz / / Attributes](../mfc/decrement-attributes-comment.md)   
 [Komentarz / / Operations](../mfc/decrement-operations-comment.md)   
 [Komentarz / / Overridables](../mfc/decrement-overridables-comment.md)

