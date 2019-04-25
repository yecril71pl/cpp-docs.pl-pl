---
title: Klasy formantów OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
ms.openlocfilehash: 86470c3e3e66d6aee2ce532570cea096641d2c1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186091"
---
# <a name="ole-control-classes"></a>Klasy formantów OLE

Są to klasy podstawowej, używane podczas zapisywania formantów OLE. `COleControlModule` Przypomina klasy modułu sterowania OLE [CWinApp](../mfc/reference/cwinapp-class.md) klasy w aplikacji. Każdy moduł stanowi wdrożenie co najmniej jedną kontrolkę OLE; Te kontrolki są reprezentowane przez `COleControl` obiektów. Te kontrolki komunikować się z ich kontenerów za pomocą `CConnectionPoint` obiektów.

`CPictureHolder` i `CFontHolder` klasy hermetyzacji interfejsów COM, obrazów i czcionek, podczas gdy `COlePropertyPage` i `CPropExchange` klasy pomóc w zaimplementowaniu trwałości właściwości kontrolki i strony właściwości.

[COleControlModule](../mfc/reference/colecontrolmodule-class.md)<br/>
Zastępuje `CWinApp` klasy dla modułu sterowania OLE. Pochodzi od `COleControlModule` klasa do tworzenia obiekt modułu sterowania OLE. Dostarcza funkcji elementów członkowskich dla inicjowania modułu kontrolki OLE.

[COleControl](../mfc/reference/colecontrol-class.md)<br/>
Pochodzi od `COleControl` klasa do tworzenia kontrolkę OLE. Pochodną `CWnd`, ta klasa dziedziczy wszystkie funkcje programu Windows obiekt window, a także dodatkowe funkcje specyficzne dla OLE, takich jak inicjowanie zdarzeń i możliwość obsługi metod i właściwości.

[CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)<br/>
`CConnectionPoint` Klasa definiuje specjalny rodzaj interfejsu używanego do komunikacji z innymi obiektami OLE, o nazwie punktu połączenia. Punkt połączenia implementuje interfejsu wychodzącego, która jest w stanie inicjowania działania na inne obiekty, takie jak wyzwalanie zdarzeń i powiadomień o zmianie.

[CPictureHolder](../mfc/reference/cpictureholder-class.md)<br/>
Hermetyzuje funkcjonalność obiektu obrazu Windows i `IPicture` COM interfejsu; używany do implementowania właściwości obrazów niestandardowych formantów OLE.

[CFontHolder](../mfc/reference/cfontholder-class.md)<br/>
Hermetyzuje funkcjonalność obiektu czcionki Windows i `IFont` COM interfejsu; używany do implementowania właściwości czcionki zasobów kontrolkę OLE.

[COlePropertyPage](../mfc/reference/colepropertypage-class.md)<br/>
Wyświetla właściwości OLE control w interfejsie graficznym, zbliżonym do okna dialogowego.

[CPropExchange](../mfc/reference/cpropexchange-class.md)<br/>
Obsługuje właściwość trwałość wdrożenia formantów OLE. Odpowiednikiem [CDataExchange](../mfc/reference/cdataexchange-class.md) dla okien dialogowych.

[CMonikerFile](../mfc/reference/cmonikerfile-class.md)<br/>
Krótka nazwa lub reprezentację ciągu znaków, który może zgłaszać do krótka i wiąże go synchronicznie strumień, dla którego przydomek jest nazwą.

[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)<br/>
Działa podobnie jak `CMonikerFile`; jednak powiąże moniker asynchronicznie strumień, dla którego przydomek jest nazwą.

[CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)<br/>
Implementuje OLE kontrolować właściwość, która może być ładowana asynchronicznie.

[CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)<br/>
Implementuje OLE konntrolki przeniesionej asynchronicznie i buforowanej w pliku pamięci.

[COleCmdUI](../mfc/reference/colecmdui-class.md)<br/>
Zezwala na aktywnego dokumentu w celu odbierania poleceń, które pochodzą z jego kontenerem interfejsu użytkownika (na przykład nowy plik, Otwórz, drukowania i tak dalej) i umożliwia kontenera w celu odbierania poleceń, które pochodzą z interfejsu użytkownika w aktywnym dokumencie.

[COleSafeArray](../mfc/reference/colesafearray-class.md)<br/>
Sprawdza w przypadku tablic dowolnego typu i wymiar.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../mfc/class-library-overview.md)
