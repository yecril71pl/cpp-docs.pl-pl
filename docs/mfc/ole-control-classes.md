---
title: Klasy formantów OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
ms.openlocfilehash: 5aa3899dca5a42cf789dc6dfd4701547495ec618
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617763"
---
# <a name="ole-control-classes"></a>Klasy formantów OLE

Są to klasy podstawowe używane podczas pisania formantów OLE. `COleControlModule`Klasa w module kontrolki OLE jest taka sama jak Klasa [CWinApp](reference/cwinapp-class.md) w aplikacji. Każdy moduł implementuje co najmniej jedną kontrolkę OLE; te kontrolki są reprezentowane przez `COleControl` obiekty. Te Kontrolki komunikują się ze swoimi kontenerami za pomocą `CConnectionPoint` obiektów.

`CPictureHolder`Klasy i `CFontHolder` hermetyzują interfejsy com dla obrazów i czcionek, natomiast `COlePropertyPage` `CPropExchange` klasy i ułatwiają implementowanie stron właściwości i trwałości właściwości dla kontrolki.

[COleControlModule](reference/colecontrolmodule-class.md)<br/>
Zastępuje `CWinApp` klasę modułu kontrolki OLE. Pochodny od `COleControlModule` klasy do opracowania obiektu modułu kontrolki OLE. Udostępnia funkcje członkowskie do inicjowania modułu kontrolki OLE.

[COleControl](reference/colecontrol-class.md)<br/>
Dziedzicz z `COleControl` klasy w celu opracowania formantu OLE. Pochodny od `CWnd` , ta klasa dziedziczy wszystkie funkcje obiektu okna systemu Windows oraz dodatkowe funkcje specyficzne dla OLE, takie jak Wyzwalanie zdarzeń i możliwość obsługi metod i właściwości.

[CConnectionPoint](reference/cconnectionpoint-class.md)<br/>
`CConnectionPoint`Klasa definiuje specjalny typ interfejsu używany do komunikowania się z innymi obiektami OLE, zwanymi punktem połączenia. Punkt połączenia implementuje interfejs wychodzący, który może inicjować akcje na innych obiektach, takich jak Wyzwalanie zdarzeń i powiadomienia o zmianach.

[CPictureHolder](reference/cpictureholder-class.md)<br/>
Hermetyzuje funkcjonalność obiektu obrazu systemu Windows i `IPicture` interfejsu com; służy do implementowania właściwości Custom obrazu kontrolki OLE.

[CFontHolder](reference/cfontholder-class.md)<br/>
Hermetyzuje funkcjonalność obiektu czcionki systemu Windows i `IFont` interfejsu com; służy do implementowania właściwości podstawowe czcionki formantu OLE.

[COlePropertyPage](reference/colepropertypage-class.md)<br/>
Wyświetla właściwości kontrolki OLE w interfejsie graficznym podobnym do okna dialogowego.

[CPropExchange](reference/cpropexchange-class.md)<br/>
Obsługuje implementację trwałości właściwości dla kontrolek OLE. Analogiczne do [CDataExchange](reference/cdataexchange-class.md) dla okien dialogowych.

[CMonikerFile](reference/cmonikerfile-class.md)<br/>
Przyjmuje moniker lub reprezentację w postaci ciągu, którą może umieścić w monikerze, i powiąże ją synchronicznie ze strumieniem, dla którego moniker jest nazwą.

[CAsyncMonikerFile](reference/casyncmonikerfile-class.md)<br/>
Działa podobnie do `CMonikerFile` ; jednak wiąże moniker asynchronicznie ze strumieniem, dla którego moniker jest nazwą.

[CDataPathProperty](reference/cdatapathproperty-class.md)<br/>
Implementuje właściwość kontrolki OLE, która może zostać załadowana asynchronicznie.

[CCachedDataPathProperty](reference/ccacheddatapathproperty-class.md)<br/>
Implementuje właściwość kontrolki OLE przetransferowaną asynchronicznie i buforowaną w pliku pamięci.

[COleCmdUI](reference/colecmdui-class.md)<br/>
Umożliwia aktywnemu dokumentowi otrzymywanie poleceń, które pochodzą z interfejsu użytkownika kontenera (takich jak FileNew, Otwórz, Drukuj itd.), i umożliwia kontenerowi otrzymywanie poleceń, które pochodzą z interfejsu użytkownika aktywnego dokumentu.

[COleSafeArray](reference/colesafearray-class.md)<br/>
Współpracuje z tablicami dowolnego typu i wymiaru.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
