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
ms.openlocfilehash: 667725a60fb0c907a9c2d017674f9d097d1f4946
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394679"
---
# <a name="application-and-thread-support-classes"></a>Klasy obsługi aplikacji i wątków

Każda aplikacja ma jeden i tylko jeden obiekt aplikacji; Ten obiekt służy do koordynowania innych obiektów w uruchomionego programu i jest tworzony na podstawie `CWinApp`.

Biblioteka Microsoft Foundation Class (MFC) obsługuje wielu wątków wykonania wewnątrz aplikacji. Wszystkie aplikacje muszą mieć co najmniej jeden wątek; Wątek używany przez usługi `CWinApp` obiekt jest główny wątek.

`CWinThread` hermetyzuje część możliwości wątku systemu operacyjnego. Aby upewnić się, przy użyciu wielu wątków jest łatwiejsze, MFC również zapewnia synchronizację klas obiektów, aby udostępnić interfejs C++ Win32 obiektów synchronizacji.

## <a name="application-and-thread-classes"></a>Klasy aplikacji i wątków

[CWinApp](../mfc/reference/cwinapp-class.md)<br/>
Hermetyzuje kod, aby zainicjować, uruchamiania i zakończyć działanie aplikacji. Obiekt aplikacji będą pochodzić z tej klasy.

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
Klasa bazowa dla wszystkich wątków. Użyj bezpośrednio lub wyprowadzić klasę z `CWinThread` Jeśli wątek wykonuje funkcje interfejsu użytkownika. `CWinApp` jest tworzony na podstawie `CWinThread`.

## <a name="synchronization-object-classes"></a>Klasy obiektu synchronizacji

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
Klasa bazowa, klasy obiektu synchronizacji.

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
Klasa synchronizacji, która zezwala na tylko jeden wątek w ramach jednego procesu w celu dostępu do obiektu.

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
Klasa synchronizacji, która umożliwia od jednej do określoną maksymalną liczbę równoczesnych dostępy do do obiektu.

[CMutex](../mfc/reference/cmutex-class.md)<br/>
Klasa synchronizacji, która zezwala na tylko jeden wątek w ramach dowolnej liczby procesów dostępu do obiektu.

[CEvent](../mfc/reference/cevent-class.md)<br/>
Klasa synchronizacji, która powiadamia aplikacji po wystąpieniu zdarzenia.

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
Używane w funkcje Członkowskie klas metodą o bezpiecznych wątkach, można zablokować na jeden obiekt synchronizacji.

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
Używane w funkcji składowych klas metodą o bezpiecznych wątkach, można zablokować na co najmniej jeden obiekt synchronizacji z tablicy obiektów synchronizacji.

## <a name="related-classes"></a>Klasy pokrewne

[CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)<br/>
Analizuje wiersza polecenia, z którym program został uruchomiony.

[CWaitCursor](../mfc/reference/cwaitcursor-class.md)<br/>
Umieszcza kursor oczekiwania na ekranie. Używany podczas długotrwałej operacji.

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
Obsługuje trwałego magazynowania dokowania pasków sterowania dane o stanie.

[CRecentFileList](../mfc/reference/crecentfilelist-class.md)<br/>
Obsługuje listy ostatnio używanych (MRU) pliku.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../mfc/class-library-overview.md)
