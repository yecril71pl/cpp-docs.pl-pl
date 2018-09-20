---
title: 'Wielowątkowość: Kiedy używać klas synchronizacji MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 08/27/2018
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
ms.openlocfilehash: 018623e9e6a093c4f86b8768e0fd5329f4ea3282
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443777"
---
# <a name="multithreading-when-to-use-the-mfc-synchronization-classes"></a>Wielowątkowość: Kiedy używać klas synchronizacji MFC

Wielowątkowe klas dostarczonych z MFC można podzielić na dwie kategorie: obiekty synchronizacji ([CSyncObject](../mfc/reference/csyncobject-class.md), [CSemaphore](../mfc/reference/csemaphore-class.md), [CMutex](../mfc/reference/cmutex-class.md), [ CCriticalSection](../mfc/reference/ccriticalsection-class.md), i [CEvent](../mfc/reference/cevent-class.md)) i synchronizacji uzyskiwanie dostępu do obiektów ([CMultiLock](../mfc/reference/cmultilock-class.md) i [CSingleLock](../mfc/reference/csinglelock-class.md)).

Klasy synchronizacji są używane, gdy dostęp do zasobów, muszą być kontrolowane do zapewnienia integralności zasobu. Klasy dostępu synchronizacji są używane do uzyskiwania dostępu do tych zasobów kontrolowany. W tym temacie opisano, kiedy należy używać każdej klasy.

Aby ustalić, która klasa synchronizacji, należy użyć, poproś następujące serię pytań:

1. Czy aplikacja ma oczekiwać na coś, co ma być wykonywana, zanim uzyskają dostęp do zasobów (na przykład danych musi być pobrany z portem komunikacyjnym przed mogą być one zapisywane do pliku)?

     Jeśli tak, użyj `CEvent`.

2. Można więcej niż jeden wątek w ramach tego samego dostępu do aplikacji tego zasobu w tym samym czasie (na przykład aplikacja pozwala maksymalnie pięć okien z widokami tego samego dokumentu)?

     Jeśli tak, użyj `CSemaphore`.

3. Można użyć więcej niż jedną aplikację tego zasobu (na przykład zasób znajduje się w bibliotece DLL)?

     Jeśli tak, użyj `CMutex`.

     Jeśli nie, użyj `CCriticalSection`.

`CSyncObject` nigdy nie jest używany bezpośrednio. Jest klasą bazową dla czterech innych klas synchronizacji.

## <a name="example-1-using-three-synchronization-classes"></a>Przykład 1: Przy użyciu trzech klas synchronizacji

Na przykład potrwać aplikację, która utrzymuje połączonej listy kont. Ta aplikacja umożliwia maksymalnie trzy konta do badania w oddzielnych okien, ale w danym momencie można zaktualizować tylko jeden. Gdy konto zostanie zaktualizowany, zaktualizowane dane są wysyłane przez sieć do archiwum danych.

Ta przykładowa aplikacja używa wszystkich trzech typów klas synchronizacji. Ponieważ zezwala ona na maksymalnie trzy konta do badania, w tym samym czasie, używa `CSemaphore` Aby ograniczyć dostęp do trzy obiekty widoku. Podczas próby wyświetlenia czwarty konta występuje, aplikacji, albo oczekuje, aż jeden z pierwszych trzech systemu windows zostanie zamknięty lub zakończy się niepowodzeniem. Gdy konto zostanie zaktualizowany, aplikacja używa `CCriticalSection` aby upewnić się, że tylko jedno konto jest aktualizowana w danym momencie. Po aktualizacji zakończy się powodzeniem, sygnalizuje `CEvent`, które zwalnia oczekiwania na zdarzenie, które ma być zasygnalizowany wątku. Ten wątek wysyła nowe dane do archiwum danych.

## <a name="example-2-using-synchronization-access-classes"></a>Przykład 2: Używanie klasy dostępu synchronizacji

Wybranie opcji, które klasy dostępu synchronizacji jest jeszcze prostsze. Jeśli aplikacja dotyczy tylko pojedynczy zasób kontrolowany dostęp, użyj `CSingleLock`. Jeśli potrzebuje dostępu do jednej liczby zasobów, kontrolowanego, użyj `CMultiLock`. W przykładzie 1 `CSingleLock` byłby używany, ponieważ w każdym przypadku potrzebna jest tylko jeden zasób w danym momencie.

Aby uzyskać informacje dotyczące używania klas synchronizacji, zobacz [wielowątkowość: jak używać klas synchronizacji](multithreading-how-to-use-the-synchronization-classes.md). Aby uzyskać informacje o synchronizacji, zobacz [synchronizacji](/windows/desktop/Sync/synchronization) w zestawie Windows SDK. Aby dowiedzieć się, obsługa wielowątkowości w MFC, zobacz [wielowątkowość z C++ i MFC](multithreading-with-cpp-and-mfc.md).

## <a name="see-also"></a>Zobacz też

[Wielowątkowość z C++ i MFC](multithreading-with-cpp-and-mfc.md)