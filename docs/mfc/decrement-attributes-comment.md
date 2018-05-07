---
title: --Atrybutów komentarz | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 74398d731c51223ea74fc6b827b0626af89286b5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-attributes-comment"></a>Komentarz // Attributes
`// Attributes` Sekcja deklaracji klasy MFC zawiera publiczne atrybuty lub właściwości obiektu. Zazwyczaj są to zmiennych Członkowskich lub funkcje Get i Set. Funkcji "Get" i "Set" może lub nie mogą być wirtualne. Funkcji "Get" są zwykle **const**, ponieważ w większości przypadków ma efekty uboczne. Elementy te są zwykle publiczne; atrybuty chronionego i prywatnych zwykle znajdują się w sekcji implementacji.  
  
 W przykładzie z klasy `CStdioFile`w obszarze [przykład komentarzy](../mfc/an-example-of-the-comments.md), lista zawiera jeden zmiennej członkowskiej, `m_pStream`. Klasa `CDC` Wyświetla listę członków prawie 20 w ramach tego komentarza.  
  
> [!NOTE]
>  Duży klas, takich jak `CDC` i `CWnd`, może mieć wiele elementów członkowskich, które, po prostu lista wszystkie atrybuty w jednej grupie nie może dodać wiele przejrzystości. W takich przypadkach biblioteki klas używa innych uwag nagłówkami do dalszego odróżniać elementów członkowskich. Na przykład `CDC` używa `// Device-Context Functions`, `// Drawing Tool Functions`, `// Drawing Attribute Functions`itd. Grupy, które reprezentują atrybuty zastosują się zwykle składnia opisane powyżej. Wiele klas OLE ma sekcji implementacja `// Interface Maps`.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z plików źródłowych MFC](../mfc/using-the-mfc-source-files.md)   
 [Przykład komentarzy](../mfc/an-example-of-the-comments.md)   
 [Implementacja — komentarz](../mfc/decrement-implementation-comment.md)   
 [Komentarz / / constructors](../mfc/decrement-constructors-comment.md)   
 [Komentarz / / Operations](../mfc/decrement-operations-comment.md)   
 [Komentarz / / Overridables](../mfc/decrement-overridables-comment.md)

