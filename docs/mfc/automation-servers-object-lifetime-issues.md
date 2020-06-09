---
title: 'Serwery automatyzacji: kwestie okresu istnienia obiektów'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
ms.openlocfilehash: 6e8c4189e8c895cf41323528c70d9277645d8f9d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619069"
---
# <a name="automation-servers-object-lifetime-issues"></a>Serwery automatyzacji: kwestie okresu istnienia obiektów

Gdy klient automatyzacji tworzy lub aktywuje element OLE, serwer przekazuje klientowi wskaźnik do tego obiektu. Klient tworzy odwołanie do obiektu za pośrednictwem wywołania funkcji OLE [IUnknown:: AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref). To odwołanie obowiązuje do momentu wywołania przez klienta elementu [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release). (Aplikacje klienckie zapisywane z klasami OLE biblioteka MFC nie potrzebują tych wywołań; struktura robi to.) System OLE i sam serwer mogą nawiązywać odwołania do obiektu. Serwer nie powinien zniszczyć obiektu, o ile odwołania zewnętrzne do obiektu pozostają w mocy.

Struktura zachowuje wewnętrzną liczbę odwołań do dowolnego obiektu serwera pochodnego od [CCmdTarget](reference/ccmdtarget-class.md). Ta liczba jest aktualizowana, gdy klient usługi Automation lub inna jednostka dodaje lub zwalnia odwołanie do obiektu.

Gdy liczba odwołań zmieni się na 0, struktura wywołuje funkcję wirtualną [CCmdTarget:: OnFinalRelease](reference/ccmdtarget-class.md#onfinalrelease). Domyślna implementacja tej funkcji wywołuje operator **delete** , aby usunąć ten obiekt.

Biblioteka MFC zapewnia dodatkowe możliwości kontrolowania zachowania aplikacji, gdy klienci zewnętrzni odwołują się do obiektów aplikacji. Oprócz utrzymywania liczby odwołań do poszczególnych obiektów serwery zachowują globalną liczbę aktywnych obiektów. Funkcje globalne [metodę AfxOleLockApp](reference/application-control.md#afxolelockapp) i [funkcję AfxOleUnlockApp](reference/application-control.md#afxoleunlockapp) aktualizują liczbę aktywnych obiektów aplikacji. Jeśli ta liczba jest różna od zera, aplikacja nie zostanie zakończona, gdy użytkownik wybierze opcję Zamknij z menu systemowego lub zakończy pracę z menu plik. Zamiast tego okno główne aplikacji jest ukryte (ale nie zniszczone), dopóki nie zostaną ukończone wszystkie oczekujące żądania klienta. Zwykle `AfxOleLockApp` i `AfxOleUnlockApp` są wywoływane odpowiednio w konstruktorach i destruktorach klas, które obsługują automatyzację.

Czasami okoliczności wymuszają przerwanie działania serwera, gdy klient nadal ma odwołanie do obiektu. Na przykład zasób, od którego zależy serwer, może stać się niedostępny, powodując wystąpienie błędu na serwerze. Użytkownik może również zamknąć dokument serwera zawierający obiekty, do których odwołują się inne aplikacje.

W Windows SDK, zobacz `IUnknown::AddRef` i `IUnknown::Release` .

## <a name="see-also"></a>Zobacz też

[Serwery automatyzacji](automation-servers.md)<br/>
[AfxOleCanExitApp](reference/application-control.md#afxolecanexitapp)
