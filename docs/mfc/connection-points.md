---
title: Punkty połączenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IConnectionPoint
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56686fe4ea2920f9365b84ec3064df4be95f4a3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="connection-points"></a>Punkty połączenia
W tym artykule wyjaśniono, jak wdrożyć punkty połączenia (wcześniej znane jako punkty połączenia OLE) przy użyciu klas MFC `CCmdTarget` i `CConnectionPoint`.  
  
 W przeszłości składnik modelu COM. zdefiniowane mechanizm ogólne (**IUnknown::QueryInterface**) który dozwolone obiektów do wdrożenia i ujawniać funkcjonalność w interfejsach. Odpowiedni mechanizm, który dozwolone obiektu możliwość wywołania określonych interfejsów nie został zdefiniowany. Oznacza to, COM zdefiniowane przychodzącymi wskaźników do obiektów zostały obsłużone (wskaźniki do tego obiektu interfejsów), ale nie ma jawnego modelu dla wychodzących interfejsów (wskaźniki obiekt zawiera interfejsy inne obiekty). COM ma teraz modelu o nazwie punktów połączenia, która obsługuje tę funkcję.  
  
 Połączenie ma dwie części: obiekt wywołujący interfejs o nazwie źródła, a obiekt implementujący interfejs, wywołuje obiekt sink. Punkt połączenia jest interfejs udostępniany przez źródło. W przypadku wystawianego punktu połączenia, źródłem umożliwia wychwytywanie do ustanawiania połączeń do samego siebie (źródło). Przez połączenie punktu mechanizmu ( **IConnectionPoint** interface), wskaźnika interfejsu zbiornika została przekazana do obiektu źródłowego. This, wskaźnik zapewnia źródłowej z dostępem do implementacji obiektu sink zestawu funkcji Członkowskich. Na przykład uruchomienie zaimplementowana przez obiekt sink zdarzenia, źródła można wywołać odpowiedniej metody implementacji obiektu sink. Na poniższym rysunku pokazano połączenie punktu właśnie opisem.  
  
 ![Zaimplementowany punkt połączenia](../mfc/media/vc37lh1.gif "vc37lh1")  
Wdrożony punkt połączenia  
  
 MFC implementuje tego modelu w [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md) i [CCmdTarget](../mfc/reference/ccmdtarget-class.md) klasy. Klasy wyprowadzone z **CConnectionPoint** zaimplementować **IConnectionPoint** interfejs używany do udostępnienia punkty połączenia do innych obiektów. Klasy wyprowadzone z `CCmdTarget` zaimplementować **IConnectionPointContainer** interfejs, który można wyliczyć wszystkich punktów połączenia dostępny obiekt lub znaleźć określonego punktu połączenia.  
  
 Dla każdego punktu połączenia zaimplementowana w klasie należy zadeklarować części połączenia, który implementuje punkt połączenia. W przypadku zastosowania co najmniej jednego punktu połączenia, musi również deklarować mapy pojedynczego połączenia w klasie. Mapy połączeń znajduje się tabela punkty połączenia jest obsługiwana przez kontrolkę ActiveX.  
  
 W poniższych przykładach pokazano mapy prostego połączenia i jedno połączenie punkt. Pierwszym przykładzie deklaruje mapy połączenia i punktu; drugi przykład implementuje mapy i punktu. Należy pamiętać, że `CMyClass` musi być `CCmdTarget`-klasy. W pierwszym przykładzie kod jest wstawiany w deklaracji klasy, w obszarze **chronione** sekcji:  
  
 [!code-cpp[NVC_MFCConnectionPoints#1](../mfc/codesnippet/cpp/connection-points_1.h)]  
  
 `BEGIN_CONNECTION_PART` i **end_connection_part —** makra zadeklarować klasy osadzone, `XSampleConnPt` (pochodną `CConnectionPoint`), że implementuje tego konkretnego połączenia punktu. Jeśli chcesz przesłonić `CConnectionPoint` funkcji Członkowskich lub dodać funkcje Członkowskie własny, Zadeklaruj je między tych dwóch makr. Na przykład `CONNECTION_IID` zastępuje makro `CConnectionPoint::GetIID` funkcji członkowskiej umieszczone między tych dwóch makr.  
  
 W drugim przykładzie kodu jest wstawiany formantu implementacji (plik .cpp). Ten kod implementuje Mapa połączenia, która zawiera punkt połączenia, `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../mfc/codesnippet/cpp/connection-points_2.cpp)]  
  
 Jeśli klasa ma więcej niż jedno połączenie punkt, Wstaw dodatkowe `CONNECTION_PART` makra między `BEGIN_CONNECTION_MAP` i `END_CONNECTION_MAP` makra.  
  
 Na koniec należy dodać wywołanie `EnableConnections` w Konstruktorze tej klasy. Na przykład:  
  
 [!code-cpp[NVC_MFCConnectionPoints#3](../mfc/codesnippet/cpp/connection-points_3.cpp)]  
  
 Po wstawieniu ten kod z `CCmdTarget`-klasy pochodnej udostępnia punkt połączenia dla **ISampleSink** interfejsu. Na poniższym rysunku przedstawiono w tym przykładzie.  
  
 ![Punkt połączenia implementowane za pomocą MFC](../mfc/media/vc37lh2.gif "vc37lh2")  
Punkt połączenia zaimplementowany z MFC  
  
 Zazwyczaj punkty połączenia obsługi "multiemisji" — możliwość emisji do wielu wychwytywanie podłączone do tego samego interfejsu. Poniższy fragment przykładzie pokazano, jak do obsługi multiemisji przez iteracja każdego zbiornika w punkcie połączenia:  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../mfc/codesnippet/cpp/connection-points_4.cpp)]  
  
 W tym przykładzie pobierana bieżącego zestawu połączeń na `SampleConnPt` punkt połączenia z wywołaniem do `CConnectionPoint::GetConnections`. Następnie wykonuje iterację za pośrednictwem połączenia i wywołania **ISampleSink::SinkFunc** dla każdego aktywnego połączenia.  
  
## <a name="see-also"></a>Zobacz też  
 [MFC COM](../mfc/mfc-com.md)

