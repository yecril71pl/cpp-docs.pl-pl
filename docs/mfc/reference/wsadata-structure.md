---
title: Struktura WSADATA | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WSADATA
dev_langs:
- C++
helpviewer_keywords:
- WSADATA structure [MFC]
ms.assetid: 80cc60e5-f9ae-4290-8ed5-07003136627d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dadc502900285d879f2fd77af69b1fcf08a4ba1e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880934"
---
# <a name="wsadata-structure"></a>Struktura WSADATA
`WSADATA` Struktury jest używany do przechowywania informacji na temat inicjalizacji Windows Sockets zwracany przez wywołanie `AfxSocketInit` funkcja globalna.  
  
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
 Wersja specyfikacji Windows Sockets, że biblioteki DLL Windows Sockets oczekuje, że obiekt wywołujący, aby użyć.  
  
 *wHighVersion*  
 Najwyższa wersja specyfikacji Windows Sockets, który może obsługiwać tę bibliotekę DLL (również kodowane tak jak powyżej). Zazwyczaj jest taka sama jak *wVersion*.  
  
 *szDescription*  
 Ciąg ASCII zakończony znakiem null, w której Biblioteka DLL Windows Sockets kopiuje opis implementacji Windows Sockets, w tym identyfikator dostawcy. Tekst (maksymalnie 256 znaków) może zawierać żadnych znaków, ale dostawców są ostrzeżenie przed tym kontroli i formatowanie znaków: najprawdopodobniej użycia, która aplikacja umieści to do trwa do wyświetlania go (prawdopodobnie obcięty) komunikatu o stanie.  
  
 *szSystemStatus*  
 Ciąg ASCII zakończony znakiem null, do którego biblioteki DLL Windows Sockets kopiuje odpowiednie informacje o stanie lub konfiguracji. Biblioteki DLL Windows Sockets należy użyć tego pola, tylko wtedy, gdy informacje mogą być przydatne dla użytkownika lub obsługi pracowników nie należy jej w rozszerzenie *szDescription* pola.  
  
 *iMaxSockets*  
 Maksymalna liczba gniazd, które potencjalnie otworzeniem pojedynczego procesu. Implementacja Windows Sockets może zapewnić globalnej puli gniazd dla przydziału procesowi; Alternatywnie go przydzielić zasoby na proces dla gniazda. Numer można również odzwierciedlają sposób, w której została skonfigurowana biblioteka DLL Windows Sockets lub oprogramowanie sieciowe. Numer ten może posłużyć surowych wskazanie, czy może być używany przez aplikację jest implementacja Windows Sockets autorzy aplikacji. Na przykład na serwerze Windows X może również obejmować kontrolę *iMaxSockets* podczas pierwszego uruchomienia: Jeśli jest to mniej niż 8, aplikacja zostanie wyświetlony komunikat o błędzie Jeśli użytkownik ponownie skonfigurować oprogramowanie sieciowe. (Jest to sytuacja, w którym *szSystemStatus* tekst może być używany.) Oczywiście nie ma żadnej gwarancji, która faktycznie przydzielić określonej aplikacji *iMaxSockets* gniazd, ponieważ może być używane inne aplikacje Windows Sockets.  
  
 *iMaxUdpDg*  
 Rozmiar w bajtach największego datagramu protokołu UDP (User Datagram), które mogą być wysyłane lub odbierane przez aplikację Windows Sockets. Jeśli implementacja nakłada bez ograniczeń *iMaxUdpDg* wynosi zero. W wielu implementacjach Berkeley gniazd ma niejawne limit 8192 bajtów na datagramy protokołu UDP, (która jest pofragmentowana. Jeśli to konieczne). Implementacja Windows Sockets może nałożyć limit, na przykład na podstawie alokacji buforów ponownego asemblowania fragmentu. Minimalna wartość *iMaxUdpDg* zgodności usługi Windows Sockets implementacja to 512. Należy pamiętać, że bez względu na wartość *iMaxUdpDg*, nie zaleca się próba wysłania emisji datagramu, który jest większy niż maksymalna jednostka transmisji (MTU) dla sieci. (Interfejs API Windows Sockets nie udostępniają mechanizm odnajdywania rozmiar jednostki MTU, ale musi być nie mniejsza niż 512 bajtów).  
  
 *lpVendorInfo*  
 Daleki wskaźnik do struktury danych specyficznych dla dostawcy. Definicja tej struktury (Jeśli podano) wykracza poza zakres specyfikacji Windows Sockets.  
  
> [!NOTE]
>  W MFC `WSADATA` struktury jest zwracany przez `AfxSocketInit` funkcji, która wywołania w swojej `InitInstance` funkcji. Można pobrać struktury i zapisz go w programie, jeśli należy użyć informacji z niego później.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winsock2.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit)

