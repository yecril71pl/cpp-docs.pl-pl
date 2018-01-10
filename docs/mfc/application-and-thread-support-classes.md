---
title: "Obsługa aplikacji i wątków klas | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.support
dev_langs: C++
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e443c2393d9d3a8a0f61df6adddb2c83e7672723
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="application-and-thread-support-classes"></a>Klasy obsługi aplikacji i wątków
Każda aplikacja ma jeden i tylko jeden obiekt aplikacji; Ten obiekt koordynuje innych obiektów w programie uruchomiony program i pochodzi z `CWinApp`.  
  
 Biblioteka Microsoft Foundation Class (MFC) obsługuje wiele wątków wykonywania w aplikacji. Wszystkie aplikacje muszą mieć co najmniej jeden wątek; Wątek używany przez Twoje `CWinApp` obiekt jest to podstawowy wątku.  
  
 `CWinThread`hermetyzuje część możliwości wątków systemu operacyjnego. Aby używanie wielu wątków łatwiejsze, MFC także synchronizacji klas obiektów interfejs C++ do obiektów synchronizacji Win32.  
  
## <a name="application-and-thread-classes"></a>Klasy aplikacji i wątków  
 [CWinApp](../mfc/reference/cwinapp-class.md)  
 Hermetyzuje kod, aby zainicjować, uruchamiania i zakończyć działanie aplikacji. Obiekt aplikacji będzie dziedziczyć po tej klasie.  
  
 [Cwinthread —](../mfc/reference/cwinthread-class.md)  
 Klasa podstawowa dla wszystkich wątków. Użyj bezpośrednio lub klasa wyprowadzona z `CWinThread` Jeśli Twoje wątku wykonuje funkcje interfejsu użytkownika. `CWinApp`jest pochodną `CWinThread`.  
  
## <a name="synchronization-object-classes"></a>Klasy obiektu synchronizacji  
 [CSyncObject](../mfc/reference/csyncobject-class.md)  
 Klasa podstawowa klasy obiektu synchronizacji.  
  
 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
 Klasy synchronizacji, która umożliwia tylko jeden wątek w ramach jednego procesu w celu dostępu do obiektu.  
  
 [CSemaphore](../mfc/reference/csemaphore-class.md)  
 Klasy synchronizacji, która umożliwia od jednej do określoną maksymalną liczbę równoczesnych dostępów do obiektu.  
  
 [CMutex](../mfc/reference/cmutex-class.md)  
 Klasy synchronizacji, która umożliwia tylko jeden wątek w dowolnej liczby procesów dostępu do obiektu.  
  
 [CEvent](../mfc/reference/cevent-class.md)  
 Klasy synchronizacji powiadamiająca aplikacji po wystąpieniu zdarzenia.  
  
 [CSingleLock](../mfc/reference/csinglelock-class.md)  
 Używane w funkcjach Członkowskich klas wątkowo do blokowania na jeden obiekt synchronizacji.  
  
 [CMultiLock](../mfc/reference/cmultilock-class.md)  
 Używane w funkcjach Członkowskich klas wątkowo do blokowania na co najmniej jeden obiekt synchronizacji z tablicę obiektów synchronizacji.  
  
## <a name="related-classes"></a>Klasy pokrewne  
 [CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)  
 Analizuje wiersza polecenia, z którym program został uruchomiony.  
  
 [CWaitCursor](../mfc/reference/cwaitcursor-class.md)  
 Umieszcza kursor oczekiwania na ekranie. Używany podczas operacji długie.  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 Obsługuje trwałego magazynu o dokowania pasków sterowania dane o stanie.  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 Przechowuje listy ostatnio używanych (MRU) pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

