---
title: Serwery automatyzacji
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
ms.openlocfilehash: 39e870db2f5476a630a8ed3bc68944dbb164d469
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305136"
---
# <a name="automation-servers"></a>Serwery automatyzacji

Automatyzacja sprawiają, że aplikacja do manipulowania obiektami implementowane w innej aplikacji lub do udostępnienia obiektów, dzięki czemu można manipulować. Serwer automatyzacji to aplikacja, która udostępnia programowalne obiekty (nazywane obiektami automatyzacji) do innych aplikacji (nazywane [klientów automatyzacji](../mfc/automation-clients.md)). Serwery automatyzacji są czasami nazywane składniki automatyzacji.

Udostępnianie obiektów automatyzacji umożliwia klientom automatyzacji niektórych procedur, uzyskując bezpośrednio dostęp do obiektów i udostępnia funkcje serwera. Udostępnianie obiektów w ten sposób jest korzystne w przypadku, gdy aplikacje oferują funkcje, które są przydatne w przypadku innych aplikacji. Na przykład do edytora tekstów może narazić swoje funkcje sprawdzania pisowni, aby mogły z niego korzystać inne programy. Narażenia obiektów w związku z tym umożliwia dostawcom ulepszyć funkcje swoich aplikacji za pomocą gotowych do użycia funkcji innych aplikacji.

Te obiekty automatyzacji mają właściwości i metod jako ich interfejs zewnętrzny. Właściwości są nazywane atrybutów obiektu automatyzacji. Właściwości są takie jak członkowie danych klasy języka C++. Metody są funkcje, które działają na obiektów automatyzacji. Metody są takie jak publiczne funkcje Członkowskie klasy języka C++.

> [!NOTE]
>  Właściwości są podobne elementy członkowskie danych języka C++, nie są one dostępne. Aby zapewnić dostęp przezroczyste, skonfiguruj zmiennej wewnętrznej w obiekcie automatyzacji przy użyciu pary pobierania/ustawiania elementów członkowskich, aby uzyskiwać do nich dostęp.

Zapewniając funkcjonalność aplikacji za pomocą interfejsu wspólny, dobrze zdefiniowanych, automatyzacji pozwala na tworzenie aplikacji w jednym ogólne języku programowania, takich jak Microsoft Visual Basic zamiast w makrze różnorodnych aplikacji, Języki.

##  <a name="_core_support_for_automation_servers"></a> Obsługa w przypadku serwerów automatyzacji

Visual C++ i MFC framework zapewnia rozbudowaną obsługę w przypadku serwerów automatyzacji. Obsługują wiele kłopotów związanych z wprowadzeniem serwera automatyzacji, dzięki czemu możesz skoncentrować się na funkcjonalności aplikacji.

W ramach mechanizmu jednostki do obsługi automatyzacji jest mapa wysyłania, zestaw makra, który rozszerza się w deklaracji i wywołania wymagane do udostępnienia właściwości i metody dla mechanizmu OLE. Mapy wysyłania typowe wygląda następująco:

[!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]

Okno właściwości i widoku klas pomagają w zachowaniu mapy wysyłania. Po dodaniu nowej metody lub właściwości do klasy, Visual C++ dodaje odnośny `DISP_FUNCTION` lub `DISP_PROPERTY` z parametrami wskazującą nazwę klasy, metody lub właściwości i typy danych wewnętrznych i zewnętrznych nazwy.

**Dodaj klasę** okno dialogowe upraszcza również deklaracji klasy automatyzacji i zarządzania ich właściwości i operacji. Gdy używasz okno dialogowe Dodaj klasę, aby dodać klasę do projektu, należy określić jej klasy bazowej. Jeśli klasa podstawowa umożliwia automatyzację, okno dialogowe Dodaj klasę Wyświetla formanty, które służy do określania, czy nowa klasa powinien obsługiwać automatyzacji, czy jest "OLE możliwość utworzenia" (oznacza to, czy obiekty klasy można utworzyć na żądanie w kliencie COM) i nazwę zewnętrznego dla klientów modelu COM do użycia.

**Dodaj klasę** okno dialogowe tworzy następnie deklaracji klasy, w tym makra odpowiednie dla funkcji OLE określono. Dodaje także szkielet kodu dla implementacji funkcji elementów członkowskich tej klasy.

Kreator aplikacji MFC upraszcza etapy wprowadzenie aplikację serwera automatyzacji na wyższy. Jeśli wybierzesz **automatyzacji** pole wyboru **funkcje zaawansowane** strony, Kreator aplikacji MFC, dodaje do aplikacji `InitInstance` wywołaniach wymaganych do zarejestrowania automatyzacji funkcji obiekty, i uruchom aplikację jako serwer automatyzacji.

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

- [Dowiedz się więcej o klientach automatyzacji](../mfc/automation-clients.md)

- [Dowiedz się więcej na temat klasy CCmdTarget](../mfc/reference/ccmdtarget-class.md)

- [Dowiedz się więcej o klasa COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)

## <a name="see-also"></a>Zobacz także

[Automatyzacja](../mfc/automation.md)<br/>
[Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md)
