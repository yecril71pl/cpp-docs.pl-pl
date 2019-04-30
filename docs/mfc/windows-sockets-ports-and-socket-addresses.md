---
title: 'Windows Sockets: Porty i adresy gniazd'
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
ms.openlocfilehash: c33ec1376c1898272cf80e8d77c5cc273e16f9de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389375"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets: Porty i adresy gniazd

W tym artykule opisano terminy "port" i "address" jako używane z Windows Sockets.

##  <a name="_core_port"></a> Port

Port identyfikuje unikatowy procesu, dla którego można podać usługi. W kontekście obecne port jest skojarzony z aplikacją, która obsługuje Windows Sockets. Chodzi o to, aby jednoznacznie zidentyfikować każdej aplikacji Windows Sockets, dlatego może mieć więcej niż jedną aplikację Windows Sockets uruchomione na komputerze, w tym samym czasie.

Niektóre porty są zarezerwowane dla typowych usług, takich jak FTP. Należy unikać używania tych portów, chyba że udostępniasz tego rodzaju usługi. Specyfikacja Windows Sockets szczegóły tych zarezerwowanych portów. Plik usługi WINSOCK. H wyświetla je.

Aby umożliwić Windows Sockets DLL, wybierz portu można używać, należy przekazać wartość 0 jako wartość portu. MFC wybiera port wartość większą niż 1024 dziesiętną. Można pobrać wartość portu, który MFC wybrany przez wywołanie metody [CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) funkcja elementu członkowskiego.

##  <a name="_core_socket_address"></a> Adres gniazda

Każdy obiekt gniazda jest skojarzony z adres protokołu internetowego (IP) w sieci. Zazwyczaj adres jest nazwa komputera, na przykład "pod adresem", lub liczbą kropkowana, takie jak "128.56.22.8".

Podczas wyszukiwania można utworzyć gniazda, zazwyczaj nie trzeba określić własny adres.

> [!NOTE]
>  Istnieje możliwość, że Twoja maszyna ma kilka kart sieciowych (lub aplikację kiedyś mogą być uruchamiane w takiego komputera z systemem) reprezentuje inną sieć. Jeśli tak, konieczne może być przypisany adres, aby określić, która karta sieciowa będzie używać gniazda. Jest to pewne, zaawansowanych funkcji i możliwości przenoszenia problemu.

Aby uzyskać więcej informacji, zobacz:

- [Windows Sockets: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz także

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)
