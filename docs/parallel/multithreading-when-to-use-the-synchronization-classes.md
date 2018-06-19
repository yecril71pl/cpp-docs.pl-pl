---
title: 'Wielowątkowość: Kiedy używać klas synchronizacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [MFC], synchronization classes
- resources [C++], multithreading
- synchronization classes [C++]
- synchronization [C++], multithreading
- controlled resource access [C++]
- synchronization access classes [C++]
- threading [C++], synchronization
- multithreading [C++], synchronization classes
ms.assetid: 4914f54e-68ac-438f-93c9-c013455a657e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b05922b826de81b5192b183e1c0afdfcda189f03
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688261"
---
# <a name="multithreading-when-to-use-the-synchronization-classes"></a>Wielowątkowość: kiedy używać klas synchronizacji
Wielowątkowe klasy wyposażone w MFC można podzielić na dwie kategorie: obiekty synchronizacji ([CSyncObject](../mfc/reference/csyncobject-class.md), [CSemaphore](../mfc/reference/csemaphore-class.md), [CMutex](../mfc/reference/cmutex-class.md), [ CCriticalSection](../mfc/reference/ccriticalsection-class.md), i [CEvent](../mfc/reference/cevent-class.md)) i synchronizacji uzyskiwanie dostępu do obiektów ([CMultiLock](../mfc/reference/cmultilock-class.md) i [CSingleLock](../mfc/reference/csinglelock-class.md)).  
  
 Klasy synchronizacji są używane podczas dostępu do zasobu muszą być kontrolowane w celu zapewnienia integralności zasobu. Klasy dostępu synchronizacji są używane do uzyskiwania dostępu do tych zasobów kontrolowany. W tym temacie opisano, kiedy należy używać każdej klasy.  
  
 Aby określić, która klasa synchronizacji, należy użyć, poproś serii następujące pytania:  
  
1.  Czy aplikacja ma oczekiwać na coś na to, aby umożliwić dostęp do zasobów (na przykład danych musi być pobrany z portem komunikacyjnym przed mogą być zapisywane do pliku)?  
  
     Jeśli tak, użyj `CEvent`.  
  
2.  Można więcej niż jeden wątek w tym samym dostęp do aplikacji ten zasób w tym samym czasie (na przykład aplikacja pozwala do pięciu systemu windows z widoków na tym samym dokumencie)?  
  
     Jeśli tak, użyj `CSemaphore`.  
  
3.  Więcej niż jedną aplikację można użyć tego zasobu (na przykład zasób jest w bibliotece DLL)?  
  
     Jeśli tak, użyj `CMutex`.  
  
     Jeśli nie, użyj `CCriticalSection`.  
  
 **CSyncObject** nie jest nigdy używana bezpośrednio. Jest klasą bazową dla innych cztery klas synchronizacji.  
  
## <a name="example-1-using-three-synchronization-classes"></a>Przykład 1: Użycie trzech klas synchronizacji  
 Na przykład mieć aplikację, która przechowuje połączonej listy kont. Ta aplikacja pozwala maksymalnie trzy konta należy zbadać w oddzielnych okien, ale tylko jeden z nich może być aktualizowana w dowolnym momencie konkretnego. Po zaktualizowaniu konta zaktualizowane dane są wysyłane przez sieć do archiwum danych.  
  
 Ta przykładowa aplikacja używa wszystkie trzy typy klas synchronizacji. Ponieważ zezwala ona na maksymalnie trzy konta należy zbadać w tym samym czasie, używa `CSemaphore` zajmującym się trzy obiekty widoku. Podczas próby wyświetlenia czwarty konta występuje, aplikacji, albo czeka, aż jeden z trzech pierwszych windows powoduje zamknięcie lub nie jest on. Po zaktualizowaniu konta, aplikacja używa `CCriticalSection` aby upewnić się, że tylko jedno konto jest aktualizowany w czasie. Po aktualizacji zakończy się powodzeniem, sygnały `CEvent`, które zwalnia wątku oczekiwania na zdarzenie zostać zgłoszony. Ten wątek wysyła nowe dane do archiwum danych.  
  
## <a name="example-2-using-synchronization-access-classes"></a>Przykład 2: Użycie klasy dostępu synchronizacji  
 Wybranie opcji, które klasy dostępu synchronizacji jest nawet prostsze. Jeśli aplikacja dotyczy korzystają tylko z pojedynczego zasobu kontrolowane, użyj `CSingleLock`. Wymaga dostępu do dowolnego Liczba kontrolowanych zasobów, użyj `CMultiLock`. W przykładzie 1 `CSingleLock` zostałaby użyta, ponieważ w każdym przypadku potrzebna jest tylko jeden zasób w dowolnym momencie konkretnego.  
  
 Aby uzyskać informacje dotyczące używania klas synchronizacji, zobacz [Multithreading: jak używać klas synchronizacji](../parallel/multithreading-how-to-use-the-synchronization-classes.md). Aby uzyskać informacje o synchronizacji, zobacz [synchronizacji](http://msdn.microsoft.com/library/windows/desktop/ms686353) w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Aby uzyskać informacje o wielowątkowości Obsługa w MFC, zobacz [Multithreading z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md)