---
title: --Komentarz / / constructors | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors comment
- declarations, constructors
- MFC source files, Constructors comment
- declaring constructors, code comments
- comments, MFC
- comments, constructors comment
- constructors [MFC], declaring
- instance constructors, code comments
ms.assetid: f400774e-ba85-49ed-85b7-70ef2f7dcb2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f58c8410de51a4692dd0e7f018d40eaa28c0dae8
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929585"
---
# <a name="-constructors-comment"></a>Komentarz // Constructors
`// Constructors` Sekcji deklaracji klasy MFC deklaruje konstruktorów (w tym sensie C++), a także wszystkie funkcje inicjowania wymagane do naprawdę użyć obiektu. Na przykład `CWnd::Create` znajduje się w sekcji konstruktorów, ponieważ przed użyciem `CWnd` obiekt musi być "pełni skonstruowany" najpierw wywoływania konstruktora C++, a następnie podczas wywoływania `Create` funkcji. Zazwyczaj te elementy członkowskie są publiczne.  
  
 Na przykład klasa `CStdioFile` ma trzy konstruktorów, z których jeden jest wyświetlany na liście w obszarze [przykład komentarzy](../mfc/an-example-of-the-comments.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z plików źródłowych MFC](../mfc/using-the-mfc-source-files.md)   
 [Implementacja — komentarz](../mfc/decrement-implementation-comment.md)   
 [Komentarz / / Attributes](../mfc/decrement-attributes-comment.md)   
 [Komentarz / / Operations](../mfc/decrement-operations-comment.md)   
 [Komentarz / / Overridables](../mfc/decrement-overridables-comment.md)

