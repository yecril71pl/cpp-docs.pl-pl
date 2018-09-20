---
title: 'Serwery automatyzacji: Kwestie okresu istnienia obiektów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a53d1a9d3849798fa1e583c0758b156d282a401c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397120"
---
# <a name="automation-servers-object-lifetime-issues"></a>Serwery automatyzacji: kwestie okresu istnienia obiektów

Klienta automatyzacji tworzy lub uaktywnia element OLE, serwer przekazuje klienta wskaźnikiem tego obiektu. Odwołanie do obiektu przez wywołanie funkcji OLE nawiązaniu przez klienta [IUnknown::AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref). Ta dokumentacja jest włączona do momentu wywołania klienta [IUnknown::Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release). (Aplikacje klienckie pisane przy użyciu klasy OLE bibliotekę Microsoft Foundation Class nie musi wprowadzać te wywołania; wykonuje tę platformę). OLE system i sam serwer może utworzyć odwołania do obiektu. Serwer powinien niszczy obiekt tak długo, jak obowiązywały odwołania zewnętrzne do obiektu.

Struktura przechowuje wewnętrzny liczba Liczba odwołań do dowolnego obiektu serwera pochodzącego z [CCmdTarget](../mfc/reference/ccmdtarget-class.md). Ten licznik jest aktualizowany, gdy klient usługi Automation lub inny organ dodaje lub zwalnia odwołanie do obiektu.

Gdy licznik odwołań staje się 0, struktura wywołuje funkcję wirtualną [CCmdTarget::OnFinalRelease](../mfc/reference/ccmdtarget-class.md#onfinalrelease). Domyślna implementacja ta funkcja wywołuje **Usuń** operator, aby usunąć ten obiekt.

Bibliotekę Microsoft Foundation Class udostępnia dodatkowe funkcje służące do kontrolowania zachowania aplikacji, gdy odwołania do obiektów w aplikacji dla klientów zewnętrznych. Oprócz obsługi liczba odwołań do każdego obiektu, serwery Obsługa globalnego liczba obiektów usługi active. Funkcje globalne [AfxOleLockApp](../mfc/reference/application-control.md#afxolelockapp) i [AfxOleUnlockApp](../mfc/reference/application-control.md#afxoleunlockapp) aktualizacji aplikacji liczba aktywnych obiektów. Jeśli ta liczba jest różna od zera, aplikacja nie kończy się po użytkownik wybierze zamknięcia z menu systemowego lub Zakończ w menu Plik. Zamiast tego okna głównego aplikacji jest ukryty (ale nie są niszczone) dopóki wszystkie oczekujące klienta, które zostały ukończone żądania. Zazwyczaj `AfxOleLockApp` i `AfxOleUnlockApp` są wywoływane w konstruktory i destruktory, odpowiednio, klas, które obsługują automatyzacji.

Czasami okoliczności wymusić zakończenie, gdy klient nadal ma odwołania do obiektu. Na przykład zasobów, od którego zależy serwera mogą stać się niedostępne, powodując server do wystąpienia błędu. Użytkownik może też zamknąć dokument serwera, który zawiera obiekty, do których odwołują się inne aplikacje.

W zestawie Windows SDK, zobacz `IUnknown::AddRef` i `IUnknown::Release`.

## <a name="see-also"></a>Zobacz też

[Serwery automatyzacji](../mfc/automation-servers.md)<br/>
[Afxolecanexitapp —](../mfc/reference/application-control.md#afxolecanexitapp)

