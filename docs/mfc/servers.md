---
title: Serwery | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC]
- OLE server applications [MFC], activation
- full-server
- servers
- mini-server
- OLE server applications [MFC], server types
- server applications [MFC]
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d153d73889520deaff12b64da36567a8b9a4087
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381783"
---
# <a name="servers"></a>Serwery
Aplikacja serwera (lub składników aplikacji) tworzy elementy OLE (lub składników) do użycia przez aplikacje kontenera. Visual edytowania aplikacji serwera obsługuje również edycja wizualna lub Aktywacja w miejscu. Formularz innego serwera OLE [serwer automatyzacji](../mfc/automation-servers.md). Niektóre aplikacje serwera obsługuje tylko tworzenie elementy osadzone; obsługuje inne tworzenia elementów zarówno osadzone i połączone. Niektóre obsługiwana jest konsolidacja tylko, ale jest to rzadko. Wszystkie aplikacje serwera musi obsługiwać aktywacji przez kontener aplikacji, gdy użytkownik chce edytować element. Aplikacja może być zarówno kontener, jak i serwera. Innymi słowy go można jednocześnie dołączyć dane do swoich dokumentów i tworzyć dane, które można włączyć jako elementy w dokumentach inne aplikacje.  
  
 Miniserver jest specjalnym rodzajem aplikacji serwera, która może zostać uruchomiona tylko przez kontener. Microsoft Draw i Microsoft Graph przedstawiono miniservers. Miniserver nie przechowuje dokumenty jako pliki na dysku. Zamiast tego swoje dokumenty z odczytuje i zapisuje je w elementy w dokumentach należących do kontenerów. W związku z tym miniserver obsługuje tylko osadzanie w nie łączenie.  
  
 Pełny serwer można uruchamiać w aplikacji autonomicznej lub uruchomić aplikacji kontenera. Pełny serwer może przechowywać dokumenty jako pliki na dysku. Może obsługiwać tylko osadzanie zarówno osadzanie i łączenie lub łączenie tylko. Użytkownik aplikacji kontenera można utworzyć element osadzony, wybierając polecenia Wytnij lub Kopiuj serwera i polecenia Wklej w kontenerze. Połączony element jest tworzony przez wybranie polecenia kopiowania na serwerze i Wklej łącze w kontenerze. Możesz też użytkownik może utworzyć elementu osadzonych lub połączonych w oknie dialogowym Wstaw obiekt.  
  
 Poniższa tabela zawiera podsumowanie właściwości różnych typów serwerów:  
  
### <a name="server-characteristics"></a>Właściwości serwera  
  
|Typ serwera|Obsługuje wiele wystąpień|Elementy w dokumencie|Dokumenty dla każdego wystąpienia|  
|--------------------|---------------------------------|------------------------|----------------------------|  
|Miniserver|Tak|1|1|  
|SDI pełny serwer|Tak|1 (Jeśli połączenie jest obsługiwany, 1 lub więcej)|1|  
|Pełny serwer MDI|Brak (nie wymagane)|1 (Jeśli połączenie jest obsługiwany, 1 lub więcej)|0 lub więcej|  
  
 Aplikację serwer powinien obsługiwać wiele kontenerów jednocześnie, w przypadku, gdy będzie można użyć więcej niż jednego kontenera Aby edytować element osadzony lub połączony. Jeśli serwer znajduje się aplikacja SDI (lub miniserver z interfejsem — okno dialogowe), musi być można uruchamiać jednocześnie wiele wystąpień serwera. Dzięki temu oddzielnego wystąpienia aplikacji do obsługi każdego żądania kontenera.  
  
 Serwer w przypadku aplikacji MDI, go utworzyć nowe podrzędne okno MDI zawsze należy edytować element kontenera. W ten sposób pojedyncze wystąpienie aplikacji może obsługiwać wiele kontenerów.  
  
 Aplikacja serwera należy wskazać OLE systemowej biblioteki DLL co zrobić, jeśli jedno wystąpienie serwera jest już uruchomiona w chwili innego kontenera żądań swoich usług: Określa, czy należy uruchomić nowe wystąpienie serwera lub kontenery wszystkie żądania kierowane do jednego wystąpienia serwer.  
  
 Aby uzyskać więcej informacji na serwerach zobacz:  
  
-   [Serwery: implementowanie serwera](../mfc/servers-implementing-a-server.md)  
  
-   [Serwery: implementowanie dokumentów serwera](../mfc/servers-implementing-server-documents.md)  
  
-   [Serwery: implementowanie okien ramowych w miejscu](../mfc/servers-implementing-in-place-frame-windows.md)  
  
-   [Serwery: elementy serwera](../mfc/servers-server-items.md)  
  
-   [Serwery: kwestie dotyczące interfejsu użytkownika](../mfc/servers-user-interface-issues.md)  
  
## <a name="see-also"></a>Zobacz też  
 [OLE](../mfc/ole-in-mfc.md)   
 [Kontenery](../mfc/containers.md)   
 [Kontenery: Funkcje zaawansowane](../mfc/containers-advanced-features.md)   
 [Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)   
 [Rejestracji](../mfc/registration.md)   
 [Serwery automatyzacji](../mfc/automation-servers.md)

