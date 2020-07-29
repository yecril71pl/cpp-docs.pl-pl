---
title: Punkty połączenia
ms.date: 11/19/2018
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
ms.openlocfilehash: c14d8247be2abdf828b88e728bd930691ec6571f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214155"
---
# <a name="connection-points"></a>Punkty połączenia

W tym artykule wyjaśniono, jak zaimplementować punkty połączenia (znane wcześniej jako punkty połączenia OLE) przy użyciu klas MFC `CCmdTarget` i `CConnectionPoint` .

W przeszłości Component Object Model (COM) zdefiniował ogólny mechanizm ( `IUnknown::QueryInterface` *), który zezwala obiektom na implementowanie i Uwidacznianie funkcji w interfejsach. Jednak odpowiedni mechanizm, który zezwala obiektom na ujawnienie ich możliwości wywołania określonych interfejsów, nie został zdefiniowany. Oznacza to, że model COM definiuje sposób obsługi wskaźników przychodzących do obiektów (wskaźników do interfejsów tego obiektu), ale nie miał jawnie modelu dla interfejsów wychodzących (wskaźniki, które obiekt przechowuje do innych interfejsów obiektów). COM ma teraz model o nazwie punkty połączenia, który obsługuje tę funkcję.

Połączenie ma dwie części: obiekt wywołujący interfejs, nazywany źródłem, i obiekt implementujący interfejs, nazywany ujściam. Punkt połączenia jest interfejsem udostępnianym przez źródło. Udostępnienie punktu połączenia umożliwia ujściam nawiązywanie połączeń z samym sobą (Źródło). Za pomocą mechanizmu punktu połączenia ( `IConnectionPoint` interfejsu) wskaźnik do interfejsu ujścia jest przesyłany do obiektu źródłowego. Ten wskaźnik zapewnia źródło z dostępem do implementacji ujścia zestawu funkcji Członkowskich. Na przykład aby uruchomić zdarzenie zaimplementowane przez ujścia, źródło może wywołać odpowiednią metodę implementacji ujścia. Na poniższej ilustracji przedstawiono właśnie opisany punkt połączenia.

![Zaimplementowany punkt połączenia](../mfc/media/vc37lh1.gif "Zaimplementowany punkt połączenia") <br/>
Zaimplementowany punkt połączenia

MFC implementuje ten model w klasach [CConnectionPoint](reference/cconnectionpoint-class.md) i [CCmdTarget](reference/ccmdtarget-class.md) . Klasy pochodzące od `CConnectionPoint` implementacji `IConnectionPoint` interfejsu, używane do udostępniania punktów połączenia do innych obiektów. Klasy pochodzące od `CCmdTarget` implementacji `IConnectionPointContainer` interfejsu, które mogą wyliczyć wszystkie dostępne punkty połączenia obiektu lub znaleźć konkretny punkt połączenia.

Dla każdego punktu połączenia zaimplementowanego w klasie należy zadeklarować część połączenia implementującą punkt połączenia. W przypadku zaimplementowania co najmniej jednego punktu połączenia należy również zadeklarować pojedyncze mapowanie połączenia w klasie. Mapa połączenia to tabela punktów połączenia obsługiwanych przez formant ActiveX.

W poniższych przykładach pokazano prostą mapę połączeń i jeden punkt połączenia. Pierwszy przykład deklaruje mapę połączenia i punkt; Drugi przykład implementuje mapę i punkt. Należy pamiętać, że `CMyClass` musi być `CCmdTarget` klasą pochodną. W pierwszym przykładzie kod jest wstawiany w deklaracji klasy, w **`protected`** sekcji:

[!code-cpp[NVC_MFCConnectionPoints#1](codesnippet/cpp/connection-points_1.h)]

Makra **BEGIN_CONNECTION_PART** i **END_CONNECTION_PART** deklarują klasę osadzoną `XSampleConnPt` (pochodną od `CConnectionPoint` ), która implementuje ten konkretny punkt połączenia. Jeśli chcesz przesłonić dowolne `CConnectionPoint` funkcje Członkowskie lub dodać własne funkcje członkowskie, zadeklaruj te dwa makra. Na przykład `CONNECTION_IID` makro zastępuje `CConnectionPoint::GetIID` funkcję członkowską po umieszczeniu między tymi dwoma makrami.

W drugim przykładzie kod jest wstawiany do pliku implementacji kontrolki (plik. cpp). Ten kod implementuje mapę połączeń, która obejmuje punkt połączenia `SampleConnPt` :

[!code-cpp[NVC_MFCConnectionPoints#2](codesnippet/cpp/connection-points_2.cpp)]

Jeśli klasa ma więcej niż jeden punkt połączenia, Wstaw dodatkowe makra **CONNECTION_PART** między makrami **BEGIN_CONNECTION_MAP** i **END_CONNECTION_MAP** .

Na koniec Dodaj wywołanie do `EnableConnections` w konstruktorze klasy. Na przykład:

[!code-cpp[NVC_MFCConnectionPoints#3](codesnippet/cpp/connection-points_3.cpp)]

Po wstawieniu tego kodu `CCmdTarget` Klasa pochodna uwidacznia punkt połączenia dla `ISampleSink` interfejsu. Poniższy rysunek ilustruje ten przykład.

![Punkt połączenia zaimplementowany przy użyciu MFC](../mfc/media/vc37lh2.gif "Punkt połączenia zaimplementowany przy użyciu MFC") <br/>
Punkt połączenia zaimplementowany z MFC

Zazwyczaj punkty połączenia obsługują "multiemisję" — możliwość emisji do wielu obiektów ujścia podłączonych do tego samego interfejsu. Poniższy przykładowy fragment ilustruje sposób multiemisji poprzez iterację w każdym ujścia w punkcie połączenia:

[!code-cpp[NVC_MFCConnectionPoints#4](codesnippet/cpp/connection-points_4.cpp)]

Ten przykład pobiera bieżący zestaw połączeń w `SampleConnPt` punkcie połączenia z wywołaniem do `CConnectionPoint::GetConnections` . Następnie wykonuje iterację połączeń i wywołań `ISampleSink::SinkFunc` na każdym aktywnym połączeniu.

## <a name="see-also"></a>Zobacz także

[MFC COM](mfc-com.md)
