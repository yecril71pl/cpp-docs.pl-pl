---
title: Struktura WSADATA | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WSADATA
dev_langs: C++
helpviewer_keywords: WSADATA structure [MFC]
ms.assetid: 80cc60e5-f9ae-4290-8ed5-07003136627d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f74980fdecc1a3ed0045aad969bb7c015f64d80d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="wsadata-structure"></a>Struktura WSADATA
`WSADATA` Struktury jest używany do przechowywania informacji inicjowania Windows Sockets zwrócony przez wywołanie do `AfxSocketInit` funkcji globalnej.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct WSAData {  
    WORD wVersion;  
    WORD wHighVersion;  
    char szDescription[WSADESCRIPTION_LEN+1];  
    char szSystemStatus[WSASYSSTATUS_LEN+1];  
    unsigned short iMaxSockets;  
    unsigned short iMaxUdpDg;  
    char FAR* lpVendorInfo;  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 *wVersion*  
 Wersja specyfikacji Windows Sockets, że biblioteki DLL Windows Sockets oczekuje obiekt wywołujący, aby użyć.  
  
 *wHighVersion*  
 Najwyższa wersja specyfikacji Windows Sockets, która może obsługiwać tę bibliotekę DLL (również kodowany jak powyżej). Zazwyczaj jest to ten sam **wVersion**.  
  
 *szDescription*  
 Ciąg ASCII zerem, do którego biblioteki DLL Windows Sockets kopiuje opis implementacji Windows Sockets, w tym identyfikator dostawcy. Tekst (do 256 znaków) może zawierać żadnych znaków, ale dostawców są cautioned przed tym kontroli i formatowanie znaków: jest najprawdopodobniej użycia, która aplikacja umieści to do wyświetlania (prawdopodobnie obcięte) komunikatu o stanie.  
  
 *szSystemStatus*  
 Ciąg ASCII zerem, do którego biblioteki DLL Windows Sockets kopiuje istotne informacje dotyczące stanu i konfiguracji. Biblioteki DLL Windows Sockets należy użyć w tym polu tylko wtedy, gdy informacje mogą być przydatne do użytkownika lub obsługuje personel; go nie należy traktować jako rozszerzenie **szDescription** pola.  
  
 *iMaxSockets*  
 Maksymalna liczba gniazd, które potencjalnie może otworzyć jednego procesu. Implementacja Windows Sockets zapewniają globalnej puli gniazd do przydzielenia do dowolnego procesu; Alternatywnie go przydzielić zasobów na proces dla gniazda. Numer można również odzwierciedlają sposób, w którym skonfigurowano biblioteki DLL Windows Sockets lub oprogramowanie sieciowe. Numer ten może posłużyć surowych wskazuje, czy jest używana przez aplikację implementacji usługi Windows Sockets zapisywania aplikacji. Na przykład X w systemie Windows server może sprawdzić **iMaxSockets** podczas pierwszego uruchomienia: Jeśli jest mniejszy niż 8, aplikacja będzie wyświetlony komunikat o błędzie Jeśli użytkownik ponownie skonfigurować oprogramowanie sieciowe. (Jest to sytuacja, w którym **szSystemStatus** tekst może być używany.) Oczywiście nie ma żadnej gwarancji, określonej aplikacji faktycznie można przydzielić **iMaxSockets** gniazda, ponieważ może być używane inne aplikacje Windows Sockets.  
  
 *iMaxUdpDg*  
 Rozmiar w bajtach największego datagramu protokołu UDP (User Datagram), które mogą być wysyłane lub odbierane przez aplikację usługi Windows Sockets. Jeśli implementacja nakłada brak limitu **iMaxUdpDg** wynosi zero. Wiele implementacji gniazd Berkeley ma niejawne limit 8192 bajtów na datagramy protokołu UDP, (która jest pofragmentowana. Jeśli to konieczne). Implementacja Windows Sockets można nakładają limit, na przykład na podstawie przyznawania bufory ponownego asemblowania fragmentu. Minimalna wartość **iMaxUdpDg** zgodne usługi Windows Sockets implementacja jest 512. Należy pamiętać, że niezależnie od wartości **iMaxUdpDg**, nie zaleca się próbę wysłania emisji datagramu, który jest większy niż maksymalna jednostka transmisji (MTU) dla sieci. (Gniazda interfejsu API systemu Windows nie zapewnia mechanizm, aby dowiedzieć się, rozmiar jednostki MTU, ale musi być mniejsza niż 512 bajtów).  
  
 *lpVendorInfo*  
 Daleko wskaźnik do struktury danych specyficznych dla dostawcy. Definicja tej struktury (Jeśli podany) wykracza poza zakres specyfikacji Windows Sockets.  
  
> [!NOTE]
>  W MFC `WSADATA` struktury jest zwracany przez `AfxSocketInit` funkcji, należy wywołać w Twojej `InitInstance` funkcji. Można pobrać struktury i zapisz go w programie, jeśli należy użyć informacji z niego później.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winsock2.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit)

