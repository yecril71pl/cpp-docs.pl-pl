---
title: Jak struktura wywołuje kod | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- control flow [MFC], MFC framework and your code
- events [MFC], command routing in MFC
- command routing [MFC], framework
- command handling [MFC], calling handlers and code in MFC
- events [MFC], event-driven programming
- MFC, calling code from
- MFC, calling code
- application-specific events [MFC]
- command routing [MFC], MFC
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f746ce3c3d658ab1dccc098939410b52d91b1188
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348182"
---
# <a name="how-the-framework-calls-your-code"></a>Jak struktura wywołuje kod
Odgrywa zrozumienie relacji między kodu źródłowego i kodu w ramach MFC. Po uruchomieniu aplikacji, większość przepływu sterowania znajduje się w kodzie struktury. Platformę zarządza pętli komunikatów, która umożliwia pobieranie wiadomości z systemu Windows jako użytkownik wybiera poleceń i umożliwia edycję danych widoku. Zdarzenia, które w ramach może obsłużyć samodzielnie nie należy polegać na kodzie w ogóle. Na przykład platformę zna sposób zamknięcia systemu windows i zamknij aplikację w odpowiedzi na polecenia użytkownika. Jak te zadania, platformę używa programy obsługi wiadomości i funkcji wirtualnych C++ do udzielenia odpowiedzi na te zdarzenia, a także możliwości. Kod nie ma kontroli, jednak; jest platformę.  
  
 Struktura wywołuje kod dla zdarzenia specyficzne dla aplikacji. Na przykład, gdy użytkownik wybierze polecenie menu, platformę kieruje polecenie wzdłuż sekwencji obiektów C++: bieżące okno widoku i ramki, dokument skojarzony z widoku, dokumentu w szablonie i obiektu aplikacji. Jeśli jeden z tych obiektów może obsłużyć polecenia, tak, wywołanie funkcji odpowiednie obsługi wiadomości. Wszelkie danego polecenia kod wywołuje może być należy do Ciebie, lub może być framework.  
  
 To rozmieszczenie jest nieco znanych programistom wystąpił z tradycyjnego programowanie dla systemu Windows lub programowanie sterowane zdarzeniami.  
  
 W powiązanych tematach możesz przeczytać co ramach ponieważ inicjuje i uruchamia aplikację i następnie czyści jako kończy aplikacji. Również wiedzieć, gdzie tworzonego kodu znajdzie się.  
  
 Aby uzyskać więcej informacji, zobacz [klasa CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md) i [szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Opieranie się na strukturze](../mfc/building-on-the-framework.md)

