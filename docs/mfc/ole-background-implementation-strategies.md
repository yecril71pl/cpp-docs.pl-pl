---
title: 'Podstawy OLE: Strategie implementacji | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE [MFC], development strategy
- OLE applications [MFC], implementing OLE
- applications [OLE], implementing OLE
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 68c6bd5c910f33a5d9262738a8746f2a4f2c56d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ole-background-implementation-strategies"></a>Podstawy OLE: strategie implementacji
W zależności od aplikacji dostępne są cztery strategie implementacji możliwe dodanie obsługi:  
  
-   Pisania nowej aplikacji.  
  
     Taka sytuacja zwykle wymaga najmniej pracy. Uruchom Kreator aplikacji MFC i wybierz funkcje zaawansowane lub Obsługa dokumentów złożonych, aby utworzyć szkielet aplikacji. Aby uzyskać informacje dotyczące tych opcji i co zrobić, zobacz artykuł [tworzenia programu MFC EXE](../mfc/reference/mfc-application-wizard.md).  
  
-   Masz program napisane na platformie Microsoft Foundation Class Library w wersji 2.0 lub nowszej, który nie obsługuje OLE.  
  
     Utwórz nową aplikację przy użyciu Kreatora aplikacji MFC, jak wcześniej wspomniano, a następnie skopiuj i Wklej kod z nowej aplikacji do istniejącej aplikacji. To będzie działać dla serwerów, kontenery lub automatycznych aplikacji. Zobacz MFC [BAZGROŁY](../visual-cpp-samples.md) przykładowa przykład tej strategii.  
  
-   Masz program Microsoft Foundation Class Library, która implementuje obsługi wersji 1.0.  
  
     Zobacz [MFC techniczne Uwaga 41](../mfc/tn041-mfc-ole1-migration-to-mfc-ole-2.md) dla tej strategii konwersji.  
  
-   Korzystasz z aplikacji, który nie został zapisany przy użyciu Microsoft Foundation Classes i które mogą lub nie zostały zaimplementowane obsługi.  
  
     Taka sytuacja wymaga większość pracy. Jednym z podejść jest tworzenie nowej aplikacji, tak jak pierwszy strategii, a następnie skopiuj i Wklej istniejący kod do niego. Jeśli istniejący kod jest napisany w języku C, następnie należy go zmodyfikować, aby można go skompilować jako kod języka C++. Jeśli kod C wywołuje interfejs API systemu Windows, nie trzeba zmienić go do użycia Microsoft Foundation classes. Takie podejście, prawdopodobnie będzie wymagać niektórych restrukturyzacji programu do obsługi architektury dokument/widok używany przez w wersji 2.0 lub nowszej programu Microsoft Foundation Classes. Aby uzyskać więcej informacji dotyczących tej architektury, zobacz [25 Uwaga techniczna](../mfc/tn025-document-view-and-frame-creation.md).  
  
 Po podjęciu decyzji dotyczącej strategii, należy albo odczytu [kontenery](../mfc/containers.md) lub [serwerów](../mfc/servers.md) artykuły (w zależności od typu aplikacji pisania) lub sprawdzić przykładowe programy lub oba. Przykłady MFC OLE [OCLIENT](../visual-cpp-samples.md) i [HIERSVR](../visual-cpp-samples.md) opisano Implementowanie różnych aspektów kontenery i serwery, odpowiednio. W różnych punktach w tych artykułach będzie ona nazywana pewne funkcje w tych przykładów jako przykłady techniki omawiana.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy OLE](../mfc/ole-background.md)   
 [Kontenery: Implementowanie kontenera](../mfc/containers-implementing-a-container.md)   
 [Serwery: Implementowanie serwera](../mfc/servers-implementing-a-server.md)   
 [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md)

