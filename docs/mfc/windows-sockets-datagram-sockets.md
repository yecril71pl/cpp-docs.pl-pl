---
title: "Windows Sockets: Gniazda do przesyłania datagramów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f8c19280645edad0d449708434ebbc0ee646e981
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-datagram-sockets"></a>Windows Sockets: gniazda do przesyłania datagramów
W tym artykule opisano gniazda do przesyłania datagramów, jeden z dwóch typów gniazda Windows dostępne. (Jest innego typu [gniazda strumienia](../mfc/windows-sockets-stream-sockets.md).)  
  
 Gniazda do przesyłania datagramów obsługuje dwukierunkowy przepływ danych, która nie jest gwarantowana sekwencjonowania lub unduplicated. Datagramy również nie ma gwarancji wiarygodne; mogą one nie zostanie dostarczona. Danych datagramu może pojawić się poza kolejnością i prawdopodobnie zduplikowane, ale rekordów granice danych są zachowywane tak długo, jak rekordy są mniejsze niż limit rozmiaru wewnętrzny odbiorcy. Jest odpowiedzialny za zarządzanie sekwencjonowania i niezawodności. (Niezawodność jest dobra na lokalnej sieci LAN] ale mniej rozległej itd. sieci WAN], na przykład Internetem).  
  
 Datagramy są "bez połączenia", czyli nie jawne jest ustanowić połączenia; Wyślij wiadomość datagramu do określonego gniazda i mogą odbierać komunikaty z określonym gniazda.  
  
 Przykładem gniazdo datagramu jest aplikacja, która przechowuje zegarami systemowymi sieci zsynchronizowane. Przedstawiono to dodatkowe możliwości w co najmniej niektóre ustawienia gniazda do przesyłania datagramów: wiadomości emisji do wielu adresów sieciowych.  
  
 Gniazda do przesyłania datagramów są lepsze niż gniazda strumieni danych zorientowane na rekordy. Aby uzyskać więcej informacji na temat gniazda do przesyłania datagramów zobacz specyfikację Windows Sockets, dostępne w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Sockets w MFC](../mfc/windows-sockets-in-mfc.md)   
 [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)

