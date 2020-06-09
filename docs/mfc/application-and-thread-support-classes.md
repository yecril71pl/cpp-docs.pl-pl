---
title: Klasy obsługi aplikacji i wątków
ms.date: 11/04/2016
f1_keywords:
- vc.classes.support
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
ms.openlocfilehash: 7e64cc50a121f457b7e32e0ed549db2fa9950843
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619436"
---
# <a name="application-and-thread-support-classes"></a>Klasy obsługi aplikacji i wątków

Każda aplikacja ma jeden i tylko jeden obiekt aplikacji; Ten obiekt koordynuje inne obiekty w uruchomionym programie i pochodzi od `CWinApp` .

Biblioteka Microsoft Foundation Class (MFC) obsługuje wiele wątków wykonywania w aplikacji. Wszystkie aplikacje muszą mieć co najmniej jeden wątek; Wątek używany przez `CWinApp` obiekt jest tym wątkiem podstawowym.

`CWinThread`hermetyzuje część możliwości wątkowości systemu operacyjnego. Aby ułatwić korzystanie z wielu wątków, MFC udostępnia również klasy obiektów synchronizacji w celu zapewnienia interfejsu języka C++ dla obiektów synchronizacji Win32.

## <a name="application-and-thread-classes"></a>Klasy aplikacji i wątków

[CWinApp](reference/cwinapp-class.md)<br/>
Hermetyzuje kod w celu zainicjowania, uruchomienia i zakończenia aplikacji. Obiekt aplikacji zostanie pochodny od tej klasy.

[CWinThread](reference/cwinthread-class.md)<br/>
Klasa bazowa dla wszystkich wątków. Użyj bezpośrednio lub Utwórz klasę z, `CWinThread` Jeśli wątek wykonuje funkcje interfejsu użytkownika. `CWinApp`pochodzi od `CWinThread` .

## <a name="synchronization-object-classes"></a>Klasy obiektów synchronizacji

[CSyncObject](reference/csyncobject-class.md)<br/>
Klasa bazowa klas obiektów synchronizacji.

[CCriticalSection](reference/ccriticalsection-class.md)<br/>
Klasa synchronizacji, która zezwala na dostęp do obiektu tylko jednemu wątkowi w ramach jednego procesu.

[CSemaphore](reference/csemaphore-class.md)<br/>
Klasa synchronizacji, która umożliwia między jedną i określoną maksymalną liczbę równoczesnych dostępu do obiektu.

[CMutex](reference/cmutex-class.md)<br/>
Klasa synchronizacji, która zezwala na dostęp do obiektu tylko jednemu wątkowi w dowolnej liczbie procesów.

[CEvent](reference/cevent-class.md)<br/>
Klasa synchronizacji, która powiadamia aplikację o wystąpieniu zdarzenia.

[CSingleLock](reference/csinglelock-class.md)<br/>
Używane w funkcjach składowych klas bezpiecznych wątków do blokowania na jednym obiekcie synchronizacji.

[CMultiLock](reference/cmultilock-class.md)<br/>
Używane w funkcjach składowych klas bezpiecznych wątków do blokowania na jednym lub większej liczbie obiektów synchronizacji z tablicy obiektów synchronizacji.

## <a name="related-classes"></a>Powiązane klasy

[CCommandLineInfo](reference/ccommandlineinfo-class.md)<br/>
Analizuje wiersz polecenia, za pomocą którego uruchomiono program.

[CWaitCursor](reference/cwaitcursor-class.md)<br/>
Umieszcza kursor oczekiwania na ekranie. Używane podczas długotrwałych operacji.

[CDockState](reference/cdockstate-class.md)<br/>
Obsługuje trwały magazyn danych stanu dokowania dla pasków sterowania.

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
Zachowuje ostatnio używaną listę plików (MRU).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
