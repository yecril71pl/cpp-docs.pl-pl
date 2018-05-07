---
title: Aktywacja (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC], activation
- OLE items [MFC], visual editing
- activation [MFC]
- OLE [MFC], in-place activation
- OLE [MFC], activation
- in-place activation, embedded and linked items
- activating objects
- visual editing, activation
- visual editing
- documents [MFC], OLE
- embedded objects [MFC]
- OLE [MFC], editing
- in-place activation
- activation [MFC], embedded OLE items
- OLE activation [MFC]
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34b6d6e9313092a8f9a0a11967c7c6a62ed15e15
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="activation-c"></a>Aktywacja (C++)
W tym artykule opisano rolę aktywacji w edycja wizualna elementy OLE. Po użytkownika osadzone elementu OLE w dokumencie kontenera, może być konieczne można użyć. Aby to zrobić, użytkownik kliknie dwukrotnie element, który uaktywnia elementu. Najczęstsze działania dotyczące aktywacji jest edytowany. Wiele bieżącego elementów OLE, gdy aktywowany do edycji, spowodować okno ramowe bieżący można zmieniać, aby odzwierciedlić te należące do aplikacji serwera, który utworzył element menu i pasków narzędzi. To zachowanie, znany jako aktywacja w miejscu, umożliwia użytkownikowi Edytuj dowolny element osadzonego wewnątrz złożonego dokumentu bez opuszczania okno dokumentu kontenera.  
  
 Jest również możliwe edytowanie elementy osadzone OLE w osobnym oknie. Dzieje się tak, jeśli aplikacja kontenera lub serwer nie obsługuje aktywacji w miejscu. W takim przypadku gdy użytkownik kliknie dwukrotnie element osadzony, aplikacja jest uruchamiana w oddzielnym oknie i osadzonych element będzie wyświetlany jako własny dokument. Użytkownik edytuje element w tym oknie. Po zakończeniu edycji użytkownik zamyka aplikację serwera i zwraca do aplikacji kontenera.  
  
 Alternatywnie, użytkownik może wybrać "Edytowanie otwartej" z  **\<obiektu > Otwórz** na **Edytuj** menu. Spowoduje to otwarcie obiekt w osobnym oknie.  
  
> [!NOTE]
>  Edytowanie elementów osadzonych w osobnym oknie był standardowe zachowanie w wersji 1 OLE, a niektóre aplikacje OLE może obsługiwać tylko ten styl edycji.  
  
 Aktywacja w miejscu zamienia zorientowany sposobem tworzenia dokumentu. Użytkownika można traktować złożonego dokumentu jako pojedynczy element pracy bez przełączania się między aplikacjami. Jednak Aktywacja w miejscu jest używany tylko dla elementów osadzonych, a nie dla połączonych elementów: musi być edytowany w osobnym oknie. Jest to spowodowane połączonego elementu jest przechowywane w innym miejscu. Edytowanie połączonego elementu odbywa się w kontekście rzeczywistych danych, oznacza to, gdzie są przechowywane dane. Edytowanie połączonego elementu w osobnym oknie przypomina o tym użytkownika, który danych należy do innego dokumentu.  
  
 MFC nie obsługuje zagnieżdżonych aktywacji w miejscu. Jeśli tworzenie aplikacji kontenera/serwera i że kontener/serwer jest osadzony w innym kontenerze i aktywowana w miejscu jej nie w miejscu Aktywuj osadzone w nim obiekty.  
  
 Co się dzieje na element osadzony, gdy użytkownik kliknie dwukrotnie zależy od zleceń zdefiniowany dla elementu. Aby uzyskać informacje, zobacz [Aktywacja: zlecenia](../mfc/activation-verbs.md).  
  
## <a name="see-also"></a>Zobacz też  
 [OLE](../mfc/ole-in-mfc.md)   
 [Kontenery](../mfc/containers.md)   
 [Serwery](../mfc/servers.md)

