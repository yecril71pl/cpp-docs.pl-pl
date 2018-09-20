---
title: 'Windows Sockets: Do przesyłania datagramów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a63caa786ce5198fb902b8d48101507fb2b4113
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444219"
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

