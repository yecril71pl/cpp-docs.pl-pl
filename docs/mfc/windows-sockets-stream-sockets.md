---
title: 'Windows Sockets: Gniazda Stream'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- stream sockets [MFC]
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
ms.openlocfilehash: 91f06c4a36e76638708edf085987e51418913fd6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271297"
---
# <a name="windows-sockets-stream-sockets"></a>Windows Sockets: Gniazda Stream

W tym artykule opisano gniazda strumieni, jeden z dwóch typów gniazda Windows dostępne. (Jest innego typu [gniazdo datagramu](../mfc/windows-sockets-datagram-sockets.md).)

Gniazda Stream zapewnienia przepływu danych, bez rekordów granic: strumień bajtów, które mogą być dwukierunkowe (aplikacja jest pełny dupleks: go mogą przesyłać i odbierać za pośrednictwem gniazda). Strumienie mogą być powoływane dostarczać sekwencji, unduplicated danych. ("Sekwencjonowania" oznacza, że pakiety są dostarczane w kolejności wysyłane. "Unduplicated" oznacza, że pobieranie określonego pakietu tylko raz.) Strumień komunikatach jest gwarantowane i strumieni dobrze nadają się do obsługi dużych ilości danych.

Warstwa transportu sieciowego może podzielić lub grupowania danych w pakiety odpowiednią wielkość. `CSocket` Klasy będzie obsługiwać, pakowanie i rozpakowywanie dla Ciebie.

Strumienie są oparte na jawne połączeń: gniazda, A żądania połączenia gniazda B; gniazda B zaakceptuje lub odrzuci żądanie połączenia.

Połączenia telefonicznego zapewnia dobre odpowiednio dla strumienia. W normalnych warunkach otrzymującej rozmawia wypowiadanych w kolejności, powiedz, bez duplikacji i utraty. Gniazda Stream są właściwe, na przykład w przypadku implementacji takich jak protokół FTP (File Transfer), mechanizm przesyłania ASCII lub pliki binarne o dowolnym rozmiarze.

Gniazda Stream są preferowane w porównaniu do przesyłania datagramów, gdy dane muszą być dotrą do celu i gdy rozmiar danych jest duży. Aby uzyskać więcej informacji na temat gniazda strumieni zobacz specyfikację Windows Sockets. Specyfikacja jest dostępna w zestawie Windows SDK.

Korzystanie z gniazda strumieni może być nadrzędne w stosunku do aplikacje przeznaczone do użytku rozgłaszania do wszystkich gniazd odbieranie w sieci, ponieważ gniazdo datagram

- Problemy z siecią powódź (lub "storm") podlega opłacie emisji modelu.

- Modelu klient serwer, późniejsze jest bardziej wydajne.

- Modelu strumienia dostaw transfer danych niezawodne, gdzie model datagramów nie.

- Końcowego modelu wykorzystuje mającym uprawienia do komunikacji między ANSI i Unicode aplikacji wykorzystujących gniazda tej klasy, które CArchive przyczyni się do klasy CSocket.

    > [!NOTE]
    >  Jeśli używasz klasy `CSocket`, należy użyć strumienia. Potwierdzenie MFC zakończy się niepowodzeniem, jeśli określony typ gniazda jako **SOCK_DGRAM**.

## <a name="see-also"></a>Zobacz także

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows Sockets: Tło](../mfc/windows-sockets-background.md)
