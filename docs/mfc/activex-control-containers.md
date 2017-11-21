---
title: "Kontenery formantów ActiveX | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e564ee0c9d8ec47db68c49db1dfcbdc86b393e02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="activex-control-containers"></a>Kontenery kontrolek ActiveX
Kontenera formantu ActiveX jest kontenerem, który w pełni obsługuje formantów ActiveX i włączyć je do swoich własnych systemu windows lub w oknach dialogowych. Formant ActiveX jest element oprogramowania wielokrotnego użytku, który można używać w wielu rozwoju projektów. Formanty umożliwiają użytkownika aplikacji do bazy danych programu access, monitorować dane, a różne opcje w aplikacjach. Aby uzyskać więcej informacji na formantów ActiveX, zobacz artykuł [kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md).  
  
 Kontenery formantów zwykle mieć dwie formy w projekcie:  
  
-   Okna dialogowe i windows okno dialogowe podobne takich jak widoki formularzy, gdzie formantu ActiveX jest używane miejsce w oknie dialogowym.  
  
-   Systemu Windows w aplikacji, gdy formant ActiveX jest używany w paska narzędzi lub innej lokalizacji, w oknie użytkownika.  
  
 Widoczne ActiveX formantu kontenera wchodzi w interakcję z formantem za pośrednictwem [metody](../mfc/mfc-activex-controls-methods.md) i [właściwości](../mfc/mfc-activex-controls-properties.md). Te metody i właściwości, które mogą być dostępne i zmodyfikowane przez kontener formantu, są dostępne za pośrednictwem klasy otoki w projekcie kontenera formantu ActiveX. Osadzonego formantu ActiveX można także interakcję z kontenerem przy wyzwalania (wysyłającym) [zdarzenia](../mfc/mfc-activex-controls-events.md) powiadomiono kontenera, w którym działanie miało miejsce. Kontener formantu można operować na te powiadomienia, czy nie.  
  
 Dodatkowe artykuły omówiono kilka tematów z Tworzenie projektu kontenera formantu ActiveX do implementacji podstawowych problemy związane z kontenery formantów ActiveX skompilowanej za pomocą języka Visual C++:  
  
-   [Tworzenie kontenera kontrolek ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md)  
  
-   [Kontenery formantów ActiveX](../mfc/containers-for-activex-controls.md)  
  
-   [Kontenery formantów ActiveX: Ręczne Włączanie zawierania formantów ActiveX](../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)  
  
-   [Kontenery formantów ActiveX: Wstawianie formantu do aplikacji kontenera formantów](../mfc/inserting-a-control-into-a-control-container-application.md)  
  
-   [Kontenery formantów ActiveX: Łączenie formantu ActiveX ze zmienną członkowską](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)  
  
-   [Kontenery formantów ActiveX: Obsługa zdarzeń z ActiveX kontroli](../mfc/activex-control-containers-handling-events-from-an-activex-control.md)  
  
-   [Kontenery formantów ActiveX: Wyświetlanie i modyfikowanie właściwości formantu](../mfc/activex-control-containers-viewing-and-modifying-control-properties.md)  
  
-   [Kontenery formantów ActiveX: Programowanie formantów ActiveX w kontenerze formantów ActiveX](../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
-   [Kontenery formantów ActiveX: Używanie formantów w kontenerze bez okien dialogowych](../mfc/activex-control-containers-using-controls-in-a-non-dialog-container.md)  
  
 Aby uzyskać więcej informacji o używaniu formantów ActiveX w oknie dialogowym, zobacz [Edytor okien dialogowych](../windows/dialog-editor.md) tematów.  
  
 Lista artykułów, które opisano szczegóły Programowanie formantów ActiveX przy użyciu programu Visual C++ i klasy formantów MFC ActiveX, zobacz [kontrolki MFC ActiveX](../mfc/mfc-activex-controls.md). Artykuły są pogrupowane według kategorii funkcjonalności.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

