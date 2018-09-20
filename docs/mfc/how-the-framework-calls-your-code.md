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
ms.openlocfilehash: 68db9107a8d2d113e9118c9cf125acb2798edcd4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373873"
---
# <a name="how-the-framework-calls-your-code"></a>Jak struktura wywołuje kod

Niezwykle ważne jest zrozumienie relacji między kodem źródłowym i kodu w ramach MFC. Po uruchomieniu aplikacji, większość przepływ sterowania znajduje się w kodzie programu framework. Szablon zarządza pętli komunikatów, która pobiera komunikaty z Windows, kiedy użytkownik wybierze poleceń i dokona edycji danych w widoku. Zdarzenia, które struktura może obsługiwać samodzielnie, nie należy polegać na jej kodzie na wszystkich. Na przykład platformę zna sposób zamknięcia systemu windows i zamknij aplikację w odpowiedzi na polecenia użytkownika. Sposób jak te zadania, struktura używa programy obsługi komunikatów i funkcji wirtualnych C++, co zapewnia możliwości, aby odpowiedzieć na te zdarzenia, jak również. Twój kod jest nie w kontrolce. Struktura jest.

Struktura wywołuje kod dla zdarzeń specyficznych dla aplikacji. Na przykład, gdy użytkownik wybierze polecenie menu, struktura kieruje polecenia wzdłuż sekwencji obiektów C++: bieżące okno widoku i ramki, dokument skojarzony z widoku, w szablonie dokumentu i obiekt aplikacji. Jeśli jeden z tych obiektów można obsługiwać polecenia, robi, wywołanie funkcji odpowiedni program obsługi komunikatów. Dla dowolnego polecenia kod wywołuje się, może być należy do Ciebie, lub może być struktury.

Taki układ jest dość dobrze znanych programistom technicznego z systemem Windows tradycyjnego programowania i programowanie sterowane zdarzeniami.

W powiązanych tematach możesz przeczytać co struktura ponieważ inicjuje i uruchamia aplikację i następnie czyści jako zakończenia aplikacji. Również wiedzieć, gdzie tworzonego kodu znajdzie się.

Aby uzyskać więcej informacji, zobacz [klasa CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md) i [szablonów dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="see-also"></a>Zobacz też

[Opieranie się na strukturze](../mfc/building-on-the-framework.md)

