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
ms.openlocfilehash: c911ff2f0dcd43a6f07144f893b91f3a97c6708b
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42464648"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)
Visual C++ pozwala na posiadanie wielu równoczesnych wątków wykonawczych uruchomionych jednocześnie. Za pomocą wielowątkowości, można uruchamianie zadań w tle, zarządzać równoczesnymi strumieniami danych wejściowych, zarządzać interfejsem użytkownika i o wiele więcej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 
[Wielowątkowość z językiem C i podsystemem Win32](../parallel/multithreading-with-c-and-win32.md)  
Dodano obsługę tworzenia aplikacji wielowątkowym z Microsoft Windows  
  
[Wielowątkowość z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md)  
Opisuje co to są procesy i wątki oraz co to jest podejście MFC do wielowątkowości jest.  
  
[Wielowątkowość i ustawienia regionalne](../parallel/multithreading-and-locales.md)  
W tym artykule omówiono zagadnienia, które powstają, gdy za pomocą funkcji ustawień regionalnych, biblioteka uruchomieniowa C i standardowej biblioteki C++ w aplikacji wielowątkowych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 
[CWinThread](../mfc/reference/cwinthread-class.md)  
Przedstawia wątek wykonania wewnątrz aplikacji.  
  
[CSyncObject](../mfc/reference/csyncobject-class.md)  
Opisuje czystą klasę wirtualną, która zapewnia funkcje wspólne dla obiektów synchronizacji w systemie Win32.  
  
[CSemaphore](../mfc/reference/csemaphore-class.md)  
Przedstawia semafor, który jest obiektem synchronizacji umożliwiającym ograniczonej liczbę wątków w jeden lub więcej procesów, aby uzyskać dostęp do zasobu.  
  
[CMutex](../mfc/reference/cmutex-class.md)  
Przedstawia muteks, który jest obiektem synchronizacji, która umożliwia jeden wątek wzajemnie wykluczających się uzyskanie dostępu do zasobu.  
  
[CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
Reprezentuje sekcję krytyczną, która jest obiektem synchronizacji umożliwiającym jednemu wątkowi w czasie uzyskać dostęp do zasobów lub sekcji kodu.  
  
[CEvent](../mfc/reference/cevent-class.md)  
Przedstawia zdarzenie, które jest obiektem synchronizacji umożliwiającym jednemu wątkowi na powiadomienie drugiego o zdarzeniu.  
  
[CMultiLock](../mfc/reference/cmultilock-class.md)  
Przedstawia mechanizm kontroli dostępu wykorzystywany w kontrolowaniu dostępu do zasobów w programie wielowątkowym.  
  
[CSingleLock](../mfc/reference/csinglelock-class.md)  
Przedstawia mechanizm kontroli dostępu wykorzystywany w kontrolowaniu dostępu do zasobu w programie wielowątkowym.  