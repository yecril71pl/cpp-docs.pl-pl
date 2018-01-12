---
title: Monikery asynchroniczne w Internecie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX controls [MFC], asynchronous
- MFC, asynchronous monikers
- asynchronous monikers [MFC]
- Web applications [MFC], asynchronous
- downloading Internet resources and asynchronous monikers
- optimization [MFC], asynchronous downloading across Internet
- Internet [MFC], asynchronous downloading
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cd7b6be66c3049c1d82aa549cf362a840fd6f265
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="asynchronous-monikers-on-the-internet"></a>Minikery asynchroniczne w Internecie
Internet wymaga nowe podejście do projektowania aplikacji ze względu na dostęp do niej wolną sieć. Aplikacje powinny działać dostępu do sieci asynchronicznie, aby uniknąć Gaśnięcie silnika interfejsu użytkownika. Klasy MFC [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) zapewnia obsługę asynchronicznego pobierania plików.  
  
 Monikery asynchroniczne mogą rozszerzanie aplikacji modelu COM pobieranie asynchroniczne w Internecie oraz zapewnienie progresywnego renderowania duże obiekty, takie jak mapy bitowe i VRML obiektów. Monikery asynchroniczne Włącz właściwość formantu ActiveX lub pliku w Internecie, aby pobrać bez blokowania odpowiedzi interfejsu użytkownika.  
  
## <a name="advantages-of-asynchronous-monikers"></a>Zalety monikery asynchroniczne  
 Możesz użyć monikery asynchroniczne do:  
  
-   Pobierz kod i pliki bez blokowania.  
  
-   Pobierz właściwości w formantach ActiveX bez blokowania.  
  
-   Otrzymuj powiadomienia postępu pobierania.  
  
-   Śledź postęp i informacje o stanie gotowe.  
  
-   Podaj informacje o stanie użytkownika dotyczące postępu.  
  
-   Zezwalaj użytkownikowi na pobieranie w dowolnym momencie anulować.  
  
## <a name="mfc-classes-for-asynchronous-monikers"></a>Klasy MFC do monikery asynchroniczne  
 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) jest pochodną [CMonikerFile](../mfc/reference/cmonikerfile-class.md), który z kolei jest określana na podstawie [COleStreamFile](../mfc/reference/colestreamfile-class.md). A `COleStreamFile` reprezentuje obiekt, a strumień danych; `CMonikerFile` obiekt używa `IMoniker` do uzyskiwania danych, a `CAsyncMonikerFile` obiektu wykonuje asynchronicznie.  
  
 Monikery asynchroniczne są używane głównie w przypadku aplikacji korzystających z Internetu i formantów ActiveX do udostępniają interfejs użytkownika odpowiadać podczas transferu plików. Podstawowym przykładem jest użycie [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md) zapewnienie właściwości asynchronicznego dla formantów ActiveX.  
  
## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>Klasy MFC do ścieżek danych w kontrolkach ActiveX  
 Klasy MFC `CDataPathProperty` i [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md) implementuje właściwości formantu ActiveX, które mogą być ładowane asynchronicznie. Załadowano asynchroniczne właściwości po rozpoczęciu synchronicznego. Asynchroniczne formantów ActiveX wielokrotnie wywoływać wskazująca dostępności nowych danych podczas procesu wymiany właściwości długie wywołania zwrotnego.  
  
 `CDataPathProperty`jest pochodną `CAsyncMonikerFile`. `CCachedDataPathProperty`jest pochodną `CDataPathProperty`. Aby zaimplementować właściwości asynchronicznego w formantów ActiveX, klasa wyprowadzona z `CDataPathProperty` lub `CCachedDataPathProperty`i Zastąp [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) i inne powiadomienia chcesz otrzymywać.  
  
#### <a name="to-download-a-file-using-asynchronous-monikers"></a>Aby pobrać plik za pomocą monikery asynchroniczne  
  
1.  Deklarowanie klasy pochodzącej od [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).  
  
2.  Zastąpienie [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) do wyświetlania danych.  
  
3.  Zastąpienie innych funkcji elementów członkowskich, w tym [OnProgress](../mfc/reference/casyncmonikerfile-class.md#onprogress), [OnStartBinding](../mfc/reference/casyncmonikerfile-class.md#onstartbinding), i [OnStopBinding](../mfc/reference/casyncmonikerfile-class.md#onstopbinding).  
  
4.  Zadeklaruj wystąpienie tej klasy i używać go na otwieranie adresów URL.  
  
 Aby dowiedzieć się, jak asynchronicznie pobieranie formantu ActiveX, zobacz [formantów ActiveX w Internecie](../mfc/activex-controls-on-the-internet.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania związane z programowaniem Internetu MFC](../mfc/mfc-internet-programming-tasks.md)   
 [MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)

