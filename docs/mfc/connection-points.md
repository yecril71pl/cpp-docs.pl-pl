---
title: Punkty połączenia
ms.date: 11/04/2016
f1_keywords:
- IConnectionPoint
helpviewer_keywords:
- IConnectionPoint interface
- connections, connection points
- OLE COM connection points
- MFC COM, connection points
- COM, connection points
- interfaces, IConnectionPoint
- MFC, COM support
- connection points [MFC]
- CCmdTarget class [MFC], and connection points
- sinks, connection points
ms.assetid: bc9fd7c7-8df6-4752-ac8c-0b177442c88d
ms.openlocfilehash: cddbdb30cbc5f5ddb5fa98524ad067655f262be1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517640"
---
# <a name="connection-points"></a>Punkty połączenia

W tym artykule wyjaśniono, jak zaimplementować punktów połączenia (wcześniej znane jako punkty połączenia OLE) przy użyciu klas MFC `CCmdTarget` i `CConnectionPoint`.

W przeszłości Component Object Model (COM) zdefiniowany mechanizm ogólnego (`IUnknown::QueryInterface`*), mogą obiekty do wdrożenia i ujawniać funkcjonalność w interfejsach. Odpowiedni mechanizm, który może obiekty do udostępnienia możliwość wywołania określonych interfejsów nie została zdefiniowana. Oznacza to, COM zdefiniowane przychodzącymi wskaźników do obiektów zostały obsłużone (wskaźników do tego obiektu interfejsów), ale nie miał jawnego modelu dla wychodzących interfejsów (obiekt przechowuje inne obiekty interfejsy wskaźników). COM ma teraz modelu o nazwie punktów połączenia, która obsługuje tę funkcję.

Połączenie ma dwie części: obiekt wywołujący interfejs o nazwie źródło i obiekt implementujący interfejs o nazwie ujścia. Punkt połączenia jest interfejs udostępnianych przez źródło. Dzięki uwidocznieniu działania punktu połączenia, źródłem umożliwia ujścia do nawiązywania połączeń z samym sobą (źródło). Przez połączenie punktu mechanizm ( `IConnectionPoint` interface), wskaźnik do interfejsu ujścia jest przekazywany do obiektu źródłowego. This, wskaźnik zawiera źródła dzięki dostępowi do implementacji obiektu sink zestaw elementów członkowskich. Na przykład aby wyzwolić zdarzenie implementowany przez obiekt sink, źródła można wywołać odpowiedniej metody wdrożenia ujścia. Na poniższym rysunku pokazano połączenie punktu właśnie opisanego.

![Zaimplementowane punktu połączenia](../mfc/media/vc37lh1.gif "vc37lh1") zaimplementowane punktu połączenia

MFC implementuje ten model w [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md) i [CCmdTarget](../mfc/reference/ccmdtarget-class.md) klasy. Klasy pochodne `CConnectionPoint` zaimplementować `IConnectionPoint` interfejsu, używany do udostępnienia punkty połączenia do innych obiektów. Klasy pochodne `CCmdTarget` zaimplementować `IConnectionPointContainer` interfejs, który można wymieniać wszystkich obiektów dostępnych punktów połączenia lub znajdowania punktu określonego połączenia.

Dla każdego punktu połączenia jest zaimplementowana w klasie należy zadeklarować części połączenia, który implementuje punkt połączenia. W przypadku zastosowania jednego lub więcej punktów połączenia, musi również zadeklarować mapę jednego połączenia w klasie. Mapy połączeń znajduje się tabela punktów połączenia obsługiwane przez kontrolkę ActiveX.

W poniższych przykładach pokazano mapy prostego połączenia i jedno połączenie punkt. Pierwszy przykład deklaruje mapie połączenia, a punkt; drugi przykład implementuje mapy i punkt. Należy pamiętać, że `CMyClass` musi być `CCmdTarget`-klasy pochodnej. W pierwszym przykładzie kod jest wstawiany w deklaracji klasy, w obszarze **chronione** sekcji:

[!code-cpp[NVC_MFCConnectionPoints#1](../mfc/codesnippet/cpp/connection-points_1.h)]

**BEGIN_CONNECTION_PART** i **END_CONNECTION_PART** makra, Zadeklaruj klasę osadzone `XSampleConnPt` (pochodną `CConnectionPoint`), że implementacja tego konkretnego połączenia punktu. Jeśli chcesz przesłonić `CConnectionPoint` funkcji składowych lub Dodaj funkcje Członkowskie samodzielnie, zadeklarować je między te dwa makra. Na przykład `CONNECTION_IID` zastępuje — makro `CConnectionPoint::GetIID` funkcja elementu członkowskiego umieszczone między te dwa makra.

W drugim przykładzie kod jest wstawiany w pliku implementacji formantu (plik .cpp). Ten kod implementuje mapy połączenia, który zawiera punkt połączenia, `SampleConnPt`:

[!code-cpp[NVC_MFCConnectionPoints#2](../mfc/codesnippet/cpp/connection-points_2.cpp)]

Jeśli klasa ma więcej niż jedno połączenie punkt, wstawić dodatkowe **CONNECTION_PART** makra między **BEGIN_CONNECTION_MAP** i **END_CONNECTION_MAP** makra.

Na koniec należy dodać wywołanie `EnableConnections` w konstruktorze klasy. Na przykład:

[!code-cpp[NVC_MFCConnectionPoints#3](../mfc/codesnippet/cpp/connection-points_3.cpp)]

Po wstawieniu ten kod swojej `CCmdTarget`-klasy pochodnej udostępnia punkt połączenia dla `ISampleSink` interfejsu. Na poniższym rysunku przedstawiono w tym przykładzie.

![Punkt połączenia z implementowane za pomocą MFC](../mfc/media/vc37lh2.gif "vc37lh2") połączenia punktu implementowane za pomocą MFC

Zazwyczaj punkty połączenia obsługi "multiemisji" — możliwość emisji do wielu ujść podłączone do tego samego interfejsu. Poniższy fragment przykład pokazuje, jak do obsługi multiemisji przez iterację każdy obiekt sink dla punktu połączenia:

[!code-cpp[NVC_MFCConnectionPoints#4](../mfc/codesnippet/cpp/connection-points_4.cpp)]

W tym przykładzie pobiera bieżący zestaw połączeń na `SampleConnPt` punkt połączenia z wywołaniem `CConnectionPoint::GetConnections`. Następnie wykonuje iterację przez połączenia i wywołania `ISampleSink::SinkFunc` dla każdego aktywnego połączenia.

## <a name="see-also"></a>Zobacz też

[MFC COM](../mfc/mfc-com.md)

