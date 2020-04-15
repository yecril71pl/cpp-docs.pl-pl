---
title: Serwery automatyzacji
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
ms.openlocfilehash: 391cb2f6ff5673296f40e21113e3a6510f71d475
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370838"
---
# <a name="automation-servers"></a>Serwery automatyzacji

Automatyzacja umożliwia aplikacji manipulowanie obiektami zaimplementowanymi w innej aplikacji lub uwidacznianie obiektów, dzięki czemu można nimi manipulować. Serwer automatyzacji to aplikacja, która udostępnia programowalne obiekty (o nazwie Obiekty automatyzacji) innym aplikacjom (o nazwie [Klienci automatyzacji).](../mfc/automation-clients.md) Serwery automatyzacji są czasami nazywane składnikami automatyzacji.

Udostępnianie automatyzacji obiektów umożliwia klientom zautomatyzować niektóre procedury poprzez bezpośredni dostęp do obiektów i funkcji serwera udostępnia. Uwidacznianie obiektów w ten sposób jest korzystne, gdy aplikacje zapewniają funkcje, które są przydatne dla innych aplikacji. Na przykład edytor tekstu może narazić jego funkcje sprawdzania pisowni, tak aby inne programy mogą go używać. Ekspozycja obiektów umożliwia w ten sposób dostawcom poprawę funkcjonalności swoich aplikacji przy użyciu gotowych funkcji innych aplikacji.

Te obiekty automatyzacji mają właściwości i metody jako ich interfejs zewnętrzny. Właściwości są nazwane atrybuty Automation obiektu. Właściwości są podobne do elementów członkowskich danych klasy C++. Metody są funkcje, które działają na automatyzacji obiektów. Metody są podobne do funkcji elementów członkowskich publicznych klasy C++.

> [!NOTE]
> Chociaż właściwości są podobne do elementów członkowskich danych języka C++, nie są one bezpośrednio dostępne. Aby zapewnić przejrzysty dostęp, należy skonfigurować zmienną wewnętrzną w obiekcie Automatyzacja za pomocą pary funkcji elementu członkowskiego get/set, aby uzyskać do nich dostęp.

Udostępniając funkcje aplikacji za pośrednictwem wspólnego, dobrze zdefiniowanego interfejsu, automatyzacja umożliwia tworzenie aplikacji w jednym ogólnym języku programowania, takim jak Microsoft Visual Basic, a nie w różnych językach makr specyficznych dla aplikacji.

## <a name="support-for-automation-servers"></a><a name="_core_support_for_automation_servers"></a>Obsługa serwerów automatyzacji

Visual C++ i struktura MFC zapewniają szeroką obsługę serwerów automatyzacji. Obsługują one wiele narzutów związanych z tworzeniem serwera automatyzacji, dzięki czemu można skupić swoje wysiłki na funkcjonalności aplikacji.

Głównym mechanizmem struktury do obsługi automatyzacji jest mapa wysyłki, zestaw makr, który rozszerza się do deklaracji i wywołań potrzebnych do udostępnienia metod i właściwości ole. Typowa mapa wysyłki wygląda następująco:

[!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]

[Kreator klas](reference/mfc-class-wizard.md) i widok klasy pomagają w utrzymywaniu map wysyłki. Po dodaniu nowej metody lub właściwości do klasy `DISP_FUNCTION` visual `DISP_PROPERTY` studio dodaje odpowiednie lub makro z parametrami wskazującymi nazwę klasy, nazwy zewnętrzne i wewnętrzne metody lub właściwości i typów danych.

Okno dialogowe **Dodaj klasę** upraszcza również deklarację klasy automatyzacji i zarządzanie ich właściwościami i operacjami. Korzystając z okna dialogowego Dodawanie klasy, aby dodać klasę do projektu, należy określić jego klasę podstawową. Jeśli klasa podstawowa zezwala na automatyzację, w oknie dialogowym Dodaj klasę są wyświetlane formanty używane do określenia, czy nowa klasa powinna obsługiwać automatyzację, czy jest "tworzona przez OLE" (czyli czy obiekty klasy mogą być tworzone na żądanie klienta COM) oraz zewnętrzna nazwa klienta COM do użycia.

Okno dialogowe **Dodawanie klasy** następnie tworzy deklarację klasy, w tym odpowiednie makra dla określonych funkcji OLE. Dodaje również kod szkieletu do implementacji funkcji członkowskich klasy.

Kreator aplikacji MFC upraszcza kroki związane z uzyskiwaniem aplikacji serwera automatyzacji z ziemi. Jeśli **zaznaczysz** pole wyboru Automatyzacja ze strony **Funkcje zaawansowane,** Kreator `InitInstance` aplikacji MFC doda do funkcji aplikacji wywołania wymagane do zarejestrowania obiektów automatyzacji i uruchomienia aplikacji jako serwera automatyzacji.

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

- [Dowiedz się więcej o klientach automatyzacji](../mfc/automation-clients.md)

- [Dowiedz się więcej o klasie CCmdTarget](../mfc/reference/ccmdtarget-class.md)

- [Dowiedz się więcej o klasie COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)

## <a name="see-also"></a>Zobacz też

[Automatyzacja](../mfc/automation.md)<br/>
[Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md)
