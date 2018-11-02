---
title: 'Windows Sockets: gniazda do przesyłania datagramów'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
ms.openlocfilehash: 886409d4072a77244cff415c6f0a6a3f533e42d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462130"
---
# <a name="windows-sockets-datagram-sockets"></a>Windows Sockets: gniazda do przesyłania datagramów

W tym artykule opisano do przesyłania datagramów, jeden z dwóch typów gniazda Windows dostępne. (Jest innego typu [gniazda strumieni](../mfc/windows-sockets-stream-sockets.md).)

Do przesyłania datagramów obsługi przepływu danych dwukierunkowy, który nie jest gwarantowane sekwencjonowanie zostało zakończone lub unduplicated. Datagramy również nie ma gwarancji, być zawodne; mogą one nie zostanie dostarczona. Dane datagram może pojawić się poza kolejnością i prawdopodobnie zduplikowanych, ale rekord granic w danych zostaną zachowane, tak długo, jak rekordy są mniejsze niż limit rozmiaru wewnętrznego odbiornika. Odpowiedzialność za zarządzanie sekwencjonowania i niezawodności. (Niezawodności jest zwykle dobry w lokalnej sieci LAN], ale mniej itd rozległej sieci WAN], takich jak Internet.)

Datagramy są "bez połączenia", oznacza to, nie jawnego połączenie zostanie nawiązane; Wyślij wiadomość datagramu do gniazda określonego i może odbierać komunikaty z określonym gniazda.

Przykładem gniazdo datagramu to aplikacja umożliwiająca zegary systemowe w sieci synchronizacji. Obrazuje to dodatkowe możliwości w co najmniej niektóre ustawienia do przesyłania datagramów: emisji wiadomości do dużej liczby adresów sieciowych.

Do przesyłania datagramów są lepsze niż gniazda strumieni zorientowane danych. Aby uzyskać więcej informacji na temat do przesyłania datagramów zobacz specyfikację Windows Sockets, dostępne w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)

