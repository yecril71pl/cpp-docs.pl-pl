---
title: "Pliki źródłowe, za pomocą MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 342c687ad992b6c587ea7518811e43bcca9db6b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-the-mfc-source-files"></a>Korzystanie z plików źródłowych MFC
Biblioteka Microsoft Foundation Class (MFC) udostępnia pełny kod źródłowy. Pliki nagłówków (.h) znajdują się w katalogu \atlmfc\include; pliki implementacji (.cpp) znajdują się w katalogu \atlmfc\src\mfc.  
  
 Tej rodziny artykułów opisano konwencje używane przez MFC do komentowania różne części każdej klasy, co oznaczają te komentarze i co należy oczekiwać można znaleźć w każdej sekcji. Kreatorów Visual C++ Użyj konwencji podobne dla klasy, które tworzą automatycznie i będzie prawdopodobnie użyteczna tych konwencji własnego kodu.  
  
 Być może należy zapoznać się z **publicznego**, `protected`, i `private` słowa kluczowe języka C++. Podczas przeglądania plików nagłówek MFC, możesz znaleźć, każda klasa może mieć kilka z nich. Na przykład może być zmiennych publicznych elementów członkowskich i funkcji w więcej niż jeden **publicznego** — słowo kluczowe. Jest to spowodowane MFC oddziela zmiennych Członkowskich i funkcji na podstawie ich użycia, nie według typu dozwolony dostęp do. Używa MFC `private` oszczędnie; nawet elementy uznawane za szczegóły implementacji są zwykle chronione i często są publiczne. Chociaż dostęp do szczegółów implementacji nie jest zalecane, MFC pozostawia decyzja do Ciebie.  
  
 W plikach źródłowych MFC i pliki tworzone przez Kreatora aplikacji MFC można znaleźć komentarze, takich jak te w deklaracjach klas (zwykle w podanej kolejności):  
  
 `// Constructors`  
  
 `// Attributes`  
  
 `// Operations`  
  
 `// Overridables`  
  
 `// Implementation`  
  
 Tematy w tej rodzinie artykułów obejmują:  
  
-   [Przykład komentarzy](../mfc/an-example-of-the-comments.md)  
  
-   [/ / Comment implementacji](../mfc/decrement-implementation-comment.md)  
  
-   [/ / Komentarz dotyczący konstruktorów](../mfc/decrement-constructors-comment.md)  
  
-   [/ / Attributes komentarza](../mfc/decrement-attributes-comment.md)  
  
-   [/ / Operations comment](../mfc/decrement-operations-comment.md)  
  
-   [/ / Comment z możliwością zastąpienia](../mfc/decrement-overridables-comment.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)

