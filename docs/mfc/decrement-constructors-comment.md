---
title: --Komentarz / / constructors | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 25b6ebff4108b47e70b34aa6d83293bede78ee97
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="-constructors-comment"></a>Komentarz // Constructors
`// Constructors` Sekcji deklaracji klasy MFC deklaruje konstruktorów (w tym sensie C++), a także wszystkie funkcje inicjowania wymagane do naprawdę użyć obiektu. Na przykład `CWnd::Create` znajduje się w sekcji konstruktorów, ponieważ przed użyciem `CWnd` obiekt musi być "pełni skonstruowany" najpierw wywoływania konstruktora C++, a następnie podczas wywoływania **Utwórz** funkcji. Zazwyczaj te elementy członkowskie są publiczne.  
  
 Na przykład klasa `CStdioFile` ma trzy konstruktorów, z których jeden jest wyświetlany na liście w obszarze [przykład komentarzy](../mfc/an-example-of-the-comments.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z plików źródłowych MFC](../mfc/using-the-mfc-source-files.md)   
 [Implementacja — komentarz](../mfc/decrement-implementation-comment.md)   
 [Komentarz / / Attributes](../mfc/decrement-attributes-comment.md)   
 [Komentarz / / Operations](../mfc/decrement-operations-comment.md)   
 [Komentarz / / Overridables](../mfc/decrement-overridables-comment.md)

