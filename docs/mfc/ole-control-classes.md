---
title: "Klasy formantów OLE | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e61d0ca8ed269557efbd566da1aca160ef669e83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ole-control-classes"></a>Klasy formantów OLE
Są to klasy podstawowej, używanego podczas pisania formantów OLE. `COleControlModule` Przypomina klasy w module formantu OLE [CWinApp](../mfc/reference/cwinapp-class.md) klasy w aplikacji. Każdy moduł implementuje jeden lub kilka formantów OLE; Formanty te są reprezentowane przez `COleControl` obiektów. Formanty komunikować się z ich kontenerów przy użyciu `CConnectionPoint` obiektów.  
  
 `CPictureHolder` i `CFontHolder` klasy Hermetyzuj interfejsów COM dla obrazów i czcionek, gdy `COlePropertyPage` i `CPropExchange` klas ułatwiająca implementację strony właściwości i trwałości właściwości dla formantu.  
  
 [COleControlModule](../mfc/reference/colecontrolmodule-class.md)  
 Zastępuje `CWinApp` klasy dla modułu formantu OLE. Pochodzić od `COleControlModule` klasy umożliwiające tworzenie obiektu modułu formantu. Zapewnia funkcje Członkowskie podczas inicjowania modułu formantu OLE.  
  
 [Colecontrol —](../mfc/reference/colecontrol-class.md)  
 Pochodzić od `COleControl` klasy do opracowywania kontrolkę OLE. Pochodną `CWnd`, ta klasa dziedziczy wszystkie funkcje obiektu okna systemu Windows oraz dodatkowe funkcje specyficzne dla OLE, takich jak inicjowanie zdarzeń i możliwość obsługi metody i właściwości.  
  
 [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)  
 `CConnectionPoint` Klasa definiuje specjalny typ interfejs używany do komunikowania się z innymi obiektami OLE, nazywany też punktem połączenia. Punkt połączenia implementuje interfejs wychodzących, który jest w stanie inicjowania działania na inne obiekty, takie jak wyzwalania zdarzeń i powiadomień o zmianie.  
  
 [CPictureHolder](../mfc/reference/cpictureholder-class.md)  
 Hermetyzuje funkcjonalność obiektu obrazu systemu Windows i `IPicture` COM interfejsu; używane do implementowania niestandardowych właściwości obrazu formantu OLE.  
  
 [CFontHolder](../mfc/reference/cfontholder-class.md)  
 Hermetyzuje funkcjonalność obiektu czcionki systemu Windows i `IFont` COM interfejsu; używaną do zaimplementowania standardowych właściwość czcionki formantu OLE.  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 Wyświetla właściwości OLE control interfejsu graficznego, podobnie do okna dialogowego.  
  
 [CPropExchange](../mfc/reference/cpropexchange-class.md)  
 Obsługuje implementacji trwałości właściwość dla formantów OLE. Odpowiednikiem [cdataexchange —](../mfc/reference/cdataexchange-class.md) dla okien dialogowych.  
  
 [CMonikerFile](../mfc/reference/cmonikerfile-class.md)  
 Pobiera moniker lub reprezentacji w postaci ciągu go do krótkiej nazwy i wiąże go synchronicznie strumienia, dla której krótka nazwa jest nazwą.  
  
 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)  
 Działa podobnie do `CMonikerFile`, ale jest on powiązany moniker asynchronicznie w strumieniu, dla której krótka nazwa jest nazwą.  
  
 [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)  
 Implementuje OLE kontrolować właściwości, które mogą być uruchamiane asynchronicznie.  
  
 [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)  
 Implementuje OLE kontrolować właściwości przesyłane asynchronicznie, a w pliku pamięci podręcznej.  
  
 [COleCmdUI](../mfc/reference/colecmdui-class.md)  
 Umożliwia aktywnego dokumentu do odbierania poleceń, które pochodzą z jego kontenera interfejsu użytkownika (na przykład nowy plik, Otwórz, drukowania i tak dalej) i pozwala kontener służący do odbierania poleceń, które pochodzą z interfejsu użytkownika w aktywnym dokumencie.  
  
 [COleSafeArray](../mfc/reference/colesafearray-class.md)  
 Współpracuje z tablicami dowolnego typu i wymiarów.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

