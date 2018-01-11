---
title: "--Atrybutów komentarz | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- comments, Attributes
- Attributes comment in MFC source files
- MFC source files, Attributes comment
- public attributes comment
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 18a142cc0434e0e09e69d9bffc30826c461cf185
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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

