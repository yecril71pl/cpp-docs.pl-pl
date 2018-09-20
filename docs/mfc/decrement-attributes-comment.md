---
title: — Komentarz atrybuty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- comments, Attributes
- Attributes comment in MFC source files
- MFC source files, Attributes comment
- public attributes comment
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04288cb4482ad477d0ddf69f621afc0b12b3bf93
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414852"
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

