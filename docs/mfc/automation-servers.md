---
title: Serwery automatyzacji
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
ms.openlocfilehash: 4c2ef77e20b7dccfa8cd6830c090111601331642
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619419"
---
# <a name="automation-servers"></a>Serwery automatyzacji

Automatyzacja pozwala aplikacji na manipulowanie obiektami zaimplementowanymi w innej aplikacji lub Uwidacznianie obiektów, aby można było manipulować nimi. Serwer automatyzacji to aplikacja, która uwidacznia obiekty programowalne (zwane obiektami automatyzacji) innym aplikacjom (nazywanym [klientami usługi Automation](automation-clients.md)). Serwery automatyzacji są czasami nazywane składnikami automatyzacji.

Uwidacznianie obiektów automatyzacji umożliwia klientom Automatyzowanie niektórych procedur przez bezpośrednie uzyskiwanie dostępu do obiektów i funkcji udostępnianych przez serwer. Uwidacznianie obiektów w ten sposób jest korzystne, gdy aplikacje udostępniają funkcje, które są przydatne w przypadku innych aplikacji. Na przykład edytor tekstów może uwidaczniać swoją funkcję sprawdzania pisowni, tak aby inne programy mogły z niej korzystać. Narażenie obiektów umożliwia dostawcom ulepszanie funkcji aplikacji przy użyciu gotowych funkcji innych aplikacji.

Te obiekty automatyzacji mają właściwości i metody jako ich interfejs zewnętrzny. Właściwości są nazwanymi atrybutami obiektu automatyzacji. Właściwości są podobne do elementów członkowskich danych klasy języka C++. Metody to funkcje, które działają na obiektach automatyzacji. Metody są podobne do publicznych funkcji członkowskich klasy języka C++.

> [!NOTE]
> Chociaż właściwości są podobne do elementów członkowskich danych języka C++, nie są one bezpośrednio dostępne. Aby zapewnić przezroczysty dostęp, skonfiguruj wewnętrzną zmienną w obiekcie automatyzacji za pomocą pary funkcji elementu członkowskiego Pobierz/ustaw, aby uzyskać do nich dostęp.

Dzięki udostępnieniu funkcjonalności aplikacji za pomocą wspólnego, dobrze zdefiniowanego interfejsu, Automatyzacja umożliwia tworzenie aplikacji w jednym ogólnym języku programowania, takim jak Microsoft Visual Basic, zamiast różnorodnych języków makr specyficznych dla aplikacji.

## <a name="support-for-automation-servers"></a><a name="_core_support_for_automation_servers"></a>Obsługa serwerów automatyzacji

Visual C++ i platforma MFC zapewnia szeroką obsługę serwerów automatyzacji. Obsługują one większość nakładów związanych z tworzeniem serwera automatyzacji, dzięki czemu możesz skupić się na działaniach aplikacji.

Głównym mechanizmem obsługi automatyzacji jest mapa wysyłania, zestaw makr, które rozwijają deklaracje i wywołania potrzebne do udostępnienia metod i właściwości dla OLE. Typowa Mapa wysyłania wygląda następująco:

[!code-cpp[NVC_MFCAutomation#1](codesnippet/cpp/automation-servers_1.cpp)]

[Kreator klas](reference/mfc-class-wizard.md) i widok klasy pomaga w zachowaniu map wysyłania. Po dodaniu nowej metody lub właściwości do klasy program Visual Studio dodaje odpowiednie `DISP_FUNCTION` lub `DISP_PROPERTY` makro z parametrami wskazującymi nazwę klasy, zewnętrzne i wewnętrzne nazwy metody lub właściwości oraz typy danych.

Okno dialogowe **Dodawanie klasy** upraszcza również deklarację klas automatyzacji i zarządzanie ich właściwościami i operacjami. W przypadku dodawania klasy do projektu przy użyciu okna dialogowego Dodawanie klasy należy określić jego klasę bazową. Jeśli klasa bazowa umożliwia automatyzację, w oknie dialogowym Dodawanie klasy są wyświetlane kontrolki używane do określenia, czy nowa klasa powinna obsługiwać automatyzację, czy jest to "OLE tworzące" (czyli czy obiekty klasy mogą być tworzone na żądanie od klienta COM), a zewnętrzna Nazwa klienta COM ma być używana.

W oknie dialogowym **Dodaj klasę** zostanie utworzona deklaracja klasy, włącznie z odpowiednimi makrami dla określonych funkcji OLE. Dodaje również kod szkieletu do implementacji funkcji składowych klasy.

Kreator aplikacji MFC upraszcza kroki, które należy wykonać w celu uzyskania aplikacji serwera automatyzacji. W przypadku zaznaczenia pola wyboru **Automatyzacja** na stronie **funkcje zaawansowane** Kreator aplikacji MFC dodaje do `InitInstance` funkcji aplikacji wywołania wymagane do zarejestrowania obiektów automatyzacji i uruchomienia aplikacji jako serwera automatyzacji.

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

- [Informacje o klientach automatyzacji](automation-clients.md)

- [Dowiedz się więcej o klasie CCmdTarget](reference/ccmdtarget-class.md)

- [Dowiedz się więcej o klasie COleDispatchDriver](reference/coledispatchdriver-class.md)

## <a name="see-also"></a>Zobacz też

[Automatyzacja](automation.md)<br/>
[Kreator aplikacji MFC](reference/mfc-application-wizard.md)
