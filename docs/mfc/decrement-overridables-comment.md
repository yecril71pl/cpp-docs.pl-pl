---
title: "— Z możliwością zastąpienia komentarz | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Overridables comment in MFC source files
- MFC source files, Overridables comment
- overriding, Overridables comment in MFC source files
- comments, MFC
ms.assetid: 8968dea5-0d94-451f-bcb2-991580e65ba2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ca52bcc3846971af1811551411199785c3d4e102
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="-overridables-comment"></a>Komentarz // Overridables
`// Overridables` Sekcja deklaracji klasy MFC zawiera funkcje wirtualne, które można zmienić w klasie pochodnej, jeśli trzeba zmodyfikować zachowanie klasy podstawowej. Są zwykle nazywane począwszy od "Włączone", mimo że nie jest to niezbędne. Funkcje w tym miejscu są przeznaczone do przesłonięcia i często zaimplementować lub podaj jakieś "wywołania zwrotnego" lub "Połącz". Zazwyczaj te elementy członkowskie są chronione.  
  
 W MFC samego czystych funkcji wirtualnych są zawsze umieszczane w tej sekcji. W języku C++ czystej funkcji wirtualnej jest jednym z formularza:  
  
 `virtual void OnDraw( ) = 0;`  
  
 W przykładzie z klasy `CStdioFile`w [przykład komentarzy](../mfc/an-example-of-the-comments.md), lista nie zawiera żadnych części z możliwością zastąpienia. Klasa **CDocument**, z drugiej strony, zawiera listę około 10 funkcji Członkowskich możliwym do zastąpienia.  
  
 W niektórych klas może również wystąpić komentarz `// Advanced Overridables`. Są funkcje, które tylko zaawansowanych programistów powinny podejmować próby zastąpienia. Prawdopodobnie nigdy nie należy zastąpić je.  
  
> [!NOTE]
>  Konwencje opisane w tym artykule można tu również, ogólnie rzecz biorąc, dla właściwości i metod automatyzacji (wcześniej znane jako automatyzacji OLE). Metody automatyzacji są podobne do operacji MFC. Właściwości automatyzacji są podobne do atrybutów MFC. Zdarzenia automatyzacji (obsługiwane dla formantów ActiveX, wcześniej znana jako formantów OLE) są podobne do funkcji Członkowskich możliwym do zastąpienia MFC.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z plików źródłowych MFC](../mfc/using-the-mfc-source-files.md)   
 [Przykład komentarzy](../mfc/an-example-of-the-comments.md)   
 [Implementacja — komentarz](../mfc/decrement-implementation-comment.md)   
 [Komentarz / / constructors](../mfc/decrement-constructors-comment.md)   
 [Komentarz / / Attributes](../mfc/decrement-attributes-comment.md)   
 [Komentarz / / Operations](../mfc/decrement-operations-comment.md)

