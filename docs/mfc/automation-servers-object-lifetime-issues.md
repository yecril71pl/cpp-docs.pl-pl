---
title: "Serwery automatyzacji: Kwestie okresu istnienia obiektów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c9fab7af74dee482c5e8dffb327da9c037796fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="automation-servers-object-lifetime-issues"></a>Serwery automatyzacji: kwestie okresu istnienia obiektów
Gdy klient automatyzacji tworzy lub uaktywnia element OLE, serwer przekazuje klienta wskaźnik tego obiektu. Odwołanie do obiektu poprzez wywołanie funkcji OLE nawiązaniu przez klienta [IUnknown::AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379). To odwołanie jest włączona do momentu połączenia klienta [IUnknown::Release](http://msdn.microsoft.com/library/windows/desktop/ms682317). (Aplikacje klienckie napisany za pomocą biblioteki Microsoft Foundation klasy klasy OLE nie muszą wprowadzać tych wywołań; wykonuje tę platformę). OLE system i serwera może utworzyć odwołania do obiektu. Serwer nie należy zniszczyć obiektu tak długo, jak obowiązują zewnętrznych odwołań do obiektu.  
  
 Platformę przechowuje wewnętrzny liczba Liczba odwołań do dowolnego obiektu serwera pochodzi od [CCmdTarget](../mfc/reference/ccmdtarget-class.md). Ten licznik jest aktualizowany, gdy klient automatyzacji lub inny podmiot dodaje lub zwalnia odwołania do obiektu.  
  
 Gdy liczba odwołań staje się 0, struktura wywołuje funkcję wirtualną [CCmdTarget::OnFinalRelease](../mfc/reference/ccmdtarget-class.md#onfinalrelease). Domyślna implementacja ta funkcja wymaga **usunąć** operatora, aby usunąć ten obiekt.  
  
 Microsoft Foundation Class Library udostępnia dodatkowe urządzenia do kontrolowania zachowania aplikacji po klientów zewnętrznych odwołują się do obiektów w aplikacji. Oprócz obsługi liczba odwołań do każdego obiektu, serwery Obsługa globalną liczbę obiektów aktywnych. Funkcje globalne [AfxOleLockApp](../mfc/reference/application-control.md#afxolelockapp) i [AfxOleUnlockApp](../mfc/reference/application-control.md#afxoleunlockapp) aktualizacji aplikacji liczba aktywnych obiektów. Jeśli ta liczba jest różna od zera, aplikacji nie wygasa, gdy użytkownik wybierze Zamknij z menu systemowego lub zakończenia w menu Plik. Zamiast tego głównego okna aplikacji jest ukryty (ale nie zostały zniszczone) dopóki wszystkie oczekujące klienta, które zostały ukończone żądania. Zazwyczaj `AfxOleLockApp` i `AfxOleUnlockApp` są nazywane konstruktory i destruktory, odpowiednio, klas, które obsługują automatyzacji.  
  
 Czasami okoliczności wymusić zakończenie, gdy klient nadal zawiera odwołanie do obiektu. Na przykład zasobów, od którego zależy serwera mogą stać się niedostępne, powodując serwera mogą wystąpić błąd. Użytkownik może także zamknąć dokument serwera, który zawiera obiekty, do których odwołują się inne aplikacje.  
  
 W zestawie SDK systemu Windows, temacie `IUnknown::AddRef` i `IUnknown::Release`.  
  
## <a name="see-also"></a>Zobacz też  
 [Serwery automatyzacji](../mfc/automation-servers.md)   
 [Afxolecanexitapp —](../mfc/reference/application-control.md#afxolecanexitapp)

