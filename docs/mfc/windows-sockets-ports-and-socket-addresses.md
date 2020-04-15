---
title: 'Windows Sockets: porty i adresy gniazd'
ms.date: 11/04/2016
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
ms.openlocfilehash: 791bf07c927e80e65e0fda79fae8a50235bc2def
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371044"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets: porty i adresy gniazd

W tym artykule wyjaśniono terminy "port" i "adres" używane w systemach Windows Sockets.

## <a name="port"></a><a name="_core_port"></a>Portu

Port identyfikuje unikatowy proces, dla którego można ować usługę. W obecnym kontekście port jest skojarzony z aplikacją, która obsługuje gniazda systemu Windows. Chodzi o to, aby zidentyfikować każdą aplikację Windows Sockets jednoznacznie, dzięki czemu można mieć więcej niż jedną aplikację Windows Sockets działa na komputerze w tym samym czasie.

Niektóre porty są zarezerwowane dla typowych usług, takich jak FTP. Należy unikać korzystania z tych portów, chyba że są świadczenia tego rodzaju usługi. Specyfikacja windows sockets zawiera szczegółowe informacje o tych zarezerwowanych portach. Plik WINSOCK. H również je wymienia.

Aby umożliwić biblioteki DLL sockets systemu Windows wybranie portu użytkowego, przekaż 0 jako wartość portu. MFC wybiera wartość portu większą niż 1024 dziesiętne. Można pobrać wartość portu, który MFC wybrany przez wywołanie [CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) funkcji elementu członkowskiego.

## <a name="socket-address"></a><a name="_core_socket_address"></a>Adres gniazda

Każdy obiekt gniazda jest skojarzony z adresem IP w sieci. Zazwyczaj adres jest nazwą komputera, taką jak "ftp.microsoft.com" lub numerem kropkowanym, na przykład "128.56.22.8".

Podczas próby utworzenia gniazda, zazwyczaj nie trzeba określać swój własny adres.

> [!NOTE]
> Jest możliwe, że komputer ma wiele kart sieciowych (lub aplikacja może kiedyś działać na takim komputerze), z których każda reprezentuje inną sieć. Jeśli tak, może być konieczne podanie adresu, aby określić, która karta sieciowa będzie używana przez gniazdo. Z pewnością jest to zaawansowany problem z użyciem i możliwością przenoszenia.

Aby uzyskać więcej informacji, zobacz:

- [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)

- [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)
