---
title: Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)
ms.date: 08/27/2018
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
ms.openlocfilehash: 649e26c3f0704dfd6740b1a250613545e29316a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407747"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)

Visual C++ pozwala na posiadanie wielu równoczesnych wątków wykonawczych uruchomionych jednocześnie. Za pomocą wielowątkowości, można uruchamianie zadań w tle, zarządzać równoczesnymi strumieniami danych wejściowych, zarządzać interfejsem użytkownika i o wiele więcej.

## <a name="in-this-section"></a>W tej sekcji

[Wielowątkowość z językiem C i podsystemem Win32](multithreading-with-c-and-win32.md)<br/>
Dodano obsługę tworzenia aplikacji wielowątkowym z Microsoft Windows

[Wielowątkowość z C++ i MFC](multithreading-with-cpp-and-mfc.md)<br/>
Opisuje co to są procesy i wątki oraz co to jest podejście MFC do wielowątkowości jest.

[Wielowątkowość i ustawienia regionalne](multithreading-and-locales.md)<br/>
W tym artykule omówiono zagadnienia, które powstają, gdy za pomocą funkcji ustawień regionalnych, biblioteka uruchomieniowa C i standardowej biblioteki C++ w aplikacji wielowątkowych.

## <a name="related-sections"></a>Sekcje pokrewne

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
Przedstawia wątek wykonania wewnątrz aplikacji.

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
Opisuje czystą klasę wirtualną, która zapewnia funkcje wspólne dla obiektów synchronizacji w systemie Win32.

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
Przedstawia semafor, który jest obiektem synchronizacji umożliwiającym ograniczonej liczbę wątków w jeden lub więcej procesów, aby uzyskać dostęp do zasobu.

[CMutex](../mfc/reference/cmutex-class.md)<br/>
Przedstawia muteks, który jest obiektem synchronizacji, która umożliwia jeden wątek wzajemnie wykluczających się uzyskanie dostępu do zasobu.

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
Reprezentuje sekcję krytyczną, która jest obiektem synchronizacji umożliwiającym jednemu wątkowi w czasie uzyskać dostęp do zasobów lub sekcji kodu.

[CEvent](../mfc/reference/cevent-class.md)<br/>
Przedstawia zdarzenie, które jest obiektem synchronizacji umożliwiającym jednemu wątkowi na powiadomienie drugiego o zdarzeniu.

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
Przedstawia mechanizm kontroli dostępu wykorzystywany w kontrolowaniu dostępu do zasobów w programie wielowątkowym.

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
Przedstawia mechanizm kontroli dostępu wykorzystywany w kontrolowaniu dostępu do zasobu w programie wielowątkowym.