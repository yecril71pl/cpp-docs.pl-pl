---
title: Obsługa wielowątkowości w przypadku starszego kodu (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4ecd5f210aa01c41b3806ce15e19e77b8c93324
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)
Visual C++ pozwala mieć wiele współbieżnych wątków wykonywania jednocześnie uruchomione. Z wielowątkowości, można pokrętła wyłączyć zadania w tle, zarządzać równoczesnych strumieni danych wejściowych, zarządzanie interfejsu użytkownika i o wiele więcej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wielowątkowość z językiem C i podsystemem Win32](../parallel/multithreading-with-c-and-win32.md)  
 Zapewnia obsługę tworzenia wielowątkowe aplikacje w systemie Microsoft Windows  
  
 [Wielowątkowość z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md)  
 Opisuje, jakie są procesów i wątków i MFC podejścia do wielowątkowość jest.  
  
 [Wielowątkowość i ustawienia regionalne](../parallel/multithreading-and-locales.md)  
 W tym artykule omówiono problemy, które wystąpić podczas korzystania z funkcji ustawień regionalnych biblioteki wykonawczej C i standardowa biblioteka C++ w aplikacji wielowątkowych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [CWinThread](../mfc/reference/cwinthread-class.md)  
 Reprezentuje wątku do wykonania w aplikacji.  
  
 [CSyncObject](../mfc/reference/csyncobject-class.md)  
 Opisuje czystej wirtualnej klasę, która udostępnia funkcje wspólne dla obiektów synchronizacji Win32.  
  
 [CSemaphore](../mfc/reference/csemaphore-class.md)  
 Reprezentuje semafora, który jest obiektem synchronizacji, który zapewnia ograniczoną liczbę wątków w jeden lub więcej procesów do uzyskania dostępu do zasobu.  
  
 [CMutex](../mfc/reference/cmutex-class.md)  
 Reprezentuje obiektu mutex, który jest obiektem synchronizacji, umożliwiająca jeden wątek wykluczają się wzajemnie dostęp do zasobu.  
  
 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
 Reprezentuje sekcję krytyczny, który jest obiektem synchronizacji, który umożliwia jeden wątek jednocześnie dostęp do zasobów lub sekcji kodu.  
  
 [CEvent](../mfc/reference/cevent-class.md)  
 Reprezentuje zdarzenia, który jest obiektem synchronizacji, umożliwiająca jeden wątek, aby powiadomić innego wystąpienia zdarzenia.  
  
 [CMultiLock](../mfc/reference/cmultilock-class.md)  
 Reprezentuje mechanizm kontroli dostępu, używany w kontrolowania dostępu do zasobów w programie wielowątkowych.  
  
 [CSingleLock](../mfc/reference/csinglelock-class.md)  
 Reprezentuje mechanizm kontroli dostępu, używany w kontroli dostępu do zasobów w programie wielowątkowych.  
