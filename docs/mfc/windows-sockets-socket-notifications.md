---
title: 'Windows Sockets: Gniazda powiadomienia | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa9fb14dd09ace2d641fa69fa4cf39ccefeb3d01
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets: powiadomienia dotyczące gniazd
W tym artykule opisano funkcje powiadomień z klas gniazd. Funkcje Członkowskie są funkcje wywołania zwrotnego, które struktura wywołuje powiadomiono obiektu gniazda ważnych zdarzeń. Dostępne są następujące funkcje powiadomień:  
  
-   [Zdarzenia OnReceive](../mfc/reference/casyncsocket-class.md#onreceive): powiadamia tego gniazda, że istnieje dane w buforze, aby pobrać przez wywołanie metody [Receive](../mfc/reference/casyncsocket-class.md#receive).  
  
-   [OnSend](../mfc/reference/casyncsocket-class.md#onsend): powiadamia tego gniazda, aby teraz przesyłania danych przez wywołanie metody [wysyłania](../mfc/reference/casyncsocket-class.md#send).  
  
-   [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept): powiadamia tego gniazda nasłuchiwania, który może zaakceptować oczekujących żądań połączenia, wywołując [Akceptuj](../mfc/reference/casyncsocket-class.md#accept).  
  
-   [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect): powiadamia o tym nawiązywania połączenia z gniazdem zakończenia jego próba połączenia: być może pomyślnie lub prawdopodobnie błędu.  
  
-   [OnClose](../mfc/reference/casyncsocket-class.md#onclose): powiadamia tego gniazda, które jest podłączony do gniazda zostało zamknięte.  
  
    > [!NOTE]
    >  Funkcja powiadomień dodatkowe jest [OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata). To powiadomienie informuje gniazda odbierania, że wysyłania gniazda ma do wysłania dane "poza pasmem". Dane poza pasmem są logicznie niezależny kanał skojarzone z każdej pary gniazda strumieni połączonych. Kanał poza pasmem jest zazwyczaj używany do wysyłania danych "pilnych". MFC obsługuje dane poza pasmem. Zaawansowane użytkownicy pracujący z klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md) może być konieczne użycie kanału poza pasmem, ale użytkownicy klasy [CSocket —](../mfc/reference/csocket-class.md) są niezalecane korzystanie z niego. Jest prostszy sposób utworzyć drugi gniazda przekazywania tych danych. Aby uzyskać więcej informacji na temat danych poza pasmem zobacz specyfikację Windows Sockets, dostępne w zestawie Windows SDK.  
  
 Jeśli pochodzi z klasy `CAsyncSocket`, konieczne jest przesłonięcie funkcji powiadomień dla tych sieci zdarzeń do aplikacji. Jeśli klasa jest pochodzi z klasy `CSocket`, jest wybór czy mają być zastępowane funkcje powiadomień zainteresowań. Można również użyć `CSocket` , w którym to przypadku powiadomienia funkcje domyślne do żadne czynności.  
  
 Te funkcje są funkcje wywołania zwrotnego możliwym do zastąpienia. `CAsyncSocket`i `CSocket` przekonwertować komunikaty powiadomień, ale musi implementować jak powiadomienia funkcjonuje odpowiada, jeśli chcesz używać ich. Funkcje powiadomień są wywoływane w czasie Twojej gniazda jest powiadamiany o zdarzenia publicznej, takich jak obecności danych do odczytu.  
  
 MFC wywołuje funkcje powiadomień pozwala dostosować zachowanie programu gniazda w czasie, który ma otrzymywać powiadomienia. Na przykład może wywołać **Receive** z Twojej `OnReceive` funkcję powiadomień, oznacza to, na czym powiadomiony, że dane do odczytu, należy wywołać **Receive** do jego odczytu. Ta metoda nie jest konieczne, ale to nieprawidłowy scenariusz. Alternatywnie, można użyć funkcji powiadomień, aby śledzić postęp, wydrukować **śledzenia** wiadomości i tak dalej.  
  
 Zastępowanie funkcji powiadomień w klasie pochodnej gniazda i podając implementację możliwość korzystania z te powiadomienia.  
  
 Podczas operacji, takich jak odbieranie i wysyłanie danych `CSocket` obiekt staje się synchronicznego. W stanie synchronicznym przeznaczone dla innych sockets powiadomienia są umieszczane w kolejce podczas oczekiwania powiadomienie, które chce bieżącego gniazda. (Na przykład podczas **Receive** połączenia gniazda chce powiadomienie do odczytu.) Po gniazda ukończeniu dotyczącej jej operacji synchronicznych i asynchronicznych zostanie ponownie, inne gniazda można rozpocząć odbieranie powiadomień w kolejce.  
  
> [!NOTE]
>  W `CSocket`, `OnConnect` nigdy nie została wywołana funkcja powiadomień. Dla połączeń, należy wywołać **Connect**, który zwróci po zakończeniu połączenia (pomyślnie lub błąd). Sposób obsługi powiadomień połączenia jest szczegółów implementacji MFC.  
  
 Aby uzyskać szczegółowe informacje dotyczące każdej funkcji powiadomień, zobacz opis funkcji poniżej klasy `CAsyncSocket` w *odwołania MFC*. Kod źródłowy i informacje o MFC — przykłady, zobacz [MFC — przykłady](../visual-cpp-samples.md).  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Gniazda systemu Windows: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Gniazda systemu Windows: jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Gniazda systemu Windows: blokowanie](../mfc/windows-sockets-blocking.md)  
  
-   [Gniazda systemu Windows: określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Gniazda systemu Windows: konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)

