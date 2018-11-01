---
title: — Komentarz dotyczący atrybutów
ms.date: 11/04/2016
helpviewer_keywords:
- comments, Attributes
- Attributes comment in MFC source files
- MFC source files, Attributes comment
- public attributes comment
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
ms.openlocfilehash: 33ee18400e03b55a26c4ad17e8d1ba6853ccda88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486076"
---
# <a name="-attributes-comment"></a>Komentarz // Attributes

`// Attributes` Część deklaracji klasy MFC zawiera publiczny atrybutów (lub właściwości) obiektu. Zazwyczaj są to zmiennych składowych lub funkcje Get/Set. Funkcji "Get" i "Set" mogą być lub może nie być wirtualne. Funkcje "Get" są zwykle **const**, ponieważ w większości przypadków nie mają skutki uboczne. Te elementy członkowskie są zwykle publiczne; atrybuty chronionego i prywatnych, zwykle znajdują się w sekcji implementacji.

W przykładzie z klasy `CStdioFile`w obszarze [przykład komentarzy](../mfc/an-example-of-the-comments.md), lista zawiera jedną zmienną elementu członkowskiego, *m_pStream*. Klasa `CDC` Wyświetla niemal 20 członków w ramach tego komentarza.

> [!NOTE]
>  Duże klasy takie jak `CDC` i `CWnd`, może mieć wiele elementów członkowskich, które po prostu wyświetlanie listy wszystkich atrybutów w jednej grupie nie wprowadziłaby dodatkowej zbyt wiele, by przejrzystości. W takich przypadkach biblioteki klas używa innych komentarzy jako nagłówki do dalszego odróżnić elementów członkowskich. Na przykład `CDC` używa `// Device-Context Functions`, `// Drawing Tool Functions`, `// Drawing Attribute Functions`i nie tylko. Grupy, które reprezentują atrybuty są zgodne z typowej składni opisane powyżej. Wiele klas OLE ma sekcji wdrożenia o nazwie `// Interface Maps`.

## <a name="see-also"></a>Zobacz też

[Korzystanie z plików źródłowych MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Przykład komentarzy](../mfc/an-example-of-the-comments.md)<br/>
[Komentarz / / Implementation](../mfc/decrement-implementation-comment.md)<br/>
[Komentarz / / constructors](../mfc/decrement-constructors-comment.md)<br/>
[Komentarz / / Operations](../mfc/decrement-operations-comment.md)<br/>
[Komentarz / / Overridables](../mfc/decrement-overridables-comment.md)

