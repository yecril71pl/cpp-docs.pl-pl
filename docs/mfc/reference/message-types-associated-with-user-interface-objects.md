---
title: Typy komunikatów związane z obiektami interfejsu użytkownika
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.uiobject.msgs
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
ms.openlocfilehash: 37638d12c65986d40e7df9f0fbfdef4b8207e418
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66741573"
---
# <a name="message-types-associated-with-user-interface-objects"></a>Typy komunikatów związane z obiektami interfejsu użytkownika

W poniższej tabeli przedstawiono typy obiektów, z którymi pracujesz, a typy komunikatów związane z nimi.

### <a name="user-interface-objects-and-associated-messages"></a>Obiekty interfejsu użytkownika i skojarzone wiadomości

|Identyfikator obiektu:|Komunikaty|
|---------------|--------------|
|Nazwa klasy, reprezentujący do okna nadrzędnego|Komunikaty Windows odpowiednimi [CWnd](../../mfc/reference/cwnd-class.md)-klasy pochodnej: okno dialogowe, okna, okno podrzędne, okno podrzędne MDI lub okno ramek najwyższego poziomu.|
|Identyfikator menu lub klawiszy skrótów|— Komunikat polecenia (wykonuje funkcję program).<br />-UPDATE_COMMAND_UI komunikat (dynamicznie aktualizuje element menu).|
|Identyfikator formantu|Komunikaty powiadomień dotyczących kontrolki dla typu wybranej kontrolki.|

## <a name="see-also"></a>Zobacz także

[Mapowanie komunikatów do funkcji](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnych](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Handler komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Nawigacja w strukturze klas](../../ide/navigate-code-cpp.md)
