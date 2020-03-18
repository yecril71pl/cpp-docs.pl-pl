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
ms.openlocfilehash: 47c28520d592c4bd49ab6cb40edbb2f5ddf59846
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447651"
---
# <a name="ole-control-classes"></a>Klasy formantów OLE

Są to klasy podstawowe używane podczas pisania formantów OLE. Klasa `COleControlModule` w module kontrolki OLE jest taka sama jak Klasa [CWinApp](../mfc/reference/cwinapp-class.md) w aplikacji. Każdy moduł implementuje co najmniej jedną kontrolkę OLE; te kontrolki są reprezentowane przez obiekty `COleControl`. Te Kontrolki komunikują się ze swoimi kontenerami za pomocą obiektów `CConnectionPoint`.

Klasy `CPictureHolder` i `CFontHolder` hermetyzują interfejsy COM dla obrazów i czcionek, natomiast klasy `COlePropertyPage` i `CPropExchange` pomagają zaimplementować strony właściwości i trwałość właściwości dla kontrolki.

[COleControlModule](../mfc/reference/colecontrolmodule-class.md)<br/>
Zastępuje klasę `CWinApp` dla modułu kontrolki OLE. Dziedzicz z klasy `COleControlModule`, aby utworzyć obiekt modułu kontrolki OLE. Udostępnia funkcje członkowskie do inicjowania modułu kontrolki OLE.

[COleControl](../mfc/reference/colecontrol-class.md)<br/>
Dziedzicz z klasy `COleControl`, aby utworzyć kontrolkę OLE. Pochodny od `CWnd`, Klasa dziedziczy wszystkie funkcje obiektu okna systemu Windows oraz dodatkowe funkcje specyficzne dla OLE, takie jak Wyzwalanie zdarzeń i możliwość obsługi metod i właściwości.

[CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)<br/>
Klasa `CConnectionPoint` definiuje specjalny typ interfejsu używany do komunikowania się z innymi obiektami OLE o nazwie punkt połączenia. Punkt połączenia implementuje interfejs wychodzący, który może inicjować akcje na innych obiektach, takich jak Wyzwalanie zdarzeń i powiadomienia o zmianach.

[CPictureHolder](../mfc/reference/cpictureholder-class.md)<br/>
Hermetyzuje funkcjonalność obiektu obrazu systemu Windows i interfejsu `IPicture` COM; służy do implementowania właściwości Custom obrazu formantu OLE.

[CFontHolder](../mfc/reference/cfontholder-class.md)<br/>
Hermetyzuje funkcjonalność obiektu czcionki systemu Windows i interfejsu `IFont` COM; służy do implementowania właściwości podstawowe czcionki formantu OLE.

[COlePropertyPage](../mfc/reference/colepropertypage-class.md)<br/>
Wyświetla właściwości kontrolki OLE w interfejsie graficznym podobnym do okna dialogowego.

[CPropExchange](../mfc/reference/cpropexchange-class.md)<br/>
Obsługuje implementację trwałości właściwości dla kontrolek OLE. Analogiczne do [CDataExchange](../mfc/reference/cdataexchange-class.md) dla okien dialogowych.

[CMonikerFile](../mfc/reference/cmonikerfile-class.md)<br/>
Przyjmuje moniker lub reprezentację w postaci ciągu, którą może umieścić w monikerze, i powiąże ją synchronicznie ze strumieniem, dla którego moniker jest nazwą.

[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)<br/>
Działa podobnie do `CMonikerFile`; jednak powiązanie monikera asynchronicznie ze strumieniem, dla którego moniker jest nazwą.

[CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)<br/>
Implementuje właściwość kontrolki OLE, która może zostać załadowana asynchronicznie.

[CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)<br/>
Implementuje właściwość kontrolki OLE przetransferowaną asynchronicznie i buforowaną w pliku pamięci.

[COleCmdUI](../mfc/reference/colecmdui-class.md)<br/>
Umożliwia aktywnemu dokumentowi otrzymywanie poleceń, które pochodzą z interfejsu użytkownika kontenera (takich jak FileNew, Otwórz, Drukuj itd.), i umożliwia kontenerowi otrzymywanie poleceń, które pochodzą z interfejsu użytkownika aktywnego dokumentu.

[COleSafeArray](../mfc/reference/colesafearray-class.md)<br/>
Współpracuje z tablicami dowolnego typu i wymiaru.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
