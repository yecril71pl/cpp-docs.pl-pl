---
title: Omówienie formantu edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: 9ef696bc348dfb18b797b487224b97261020e11c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366869"
---
# <a name="overview-of-the-rich-edit-control"></a>Omówienie formantu edycji wzbogaconej

> [!IMPORTANT]
> Jeśli używasz formantu edycji bogatej w oknie dialogowym (niezależnie od tego, czy aplikacja jest oparta na SDI, MDI, czy w oknie dialogowym), należy wywołać [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) raz przed wyświetleniem okna dialogowego. Typowe miejsce do wywołania tej funkcji `InitInstance` znajduje się w funkcji członka programu. Nie trzeba wywoływać go za każdym razem, gdy wyświetlasz okno dialogowe, tylko za pierwszym razem. Nie musisz dzwonić, `AfxInitRichEdit` jeśli pracujesz z `CRichEditView`.

Zaawansowane kontrolki edycji[(CRichEditCtrl)](../mfc/reference/cricheditctrl-class.md)zapewniają interfejs programowania do formatowania tekstu. Jednak aplikacja musi implementować wszystkie składniki interfejsu użytkownika niezbędne do udostępnienia użytkownikowi operacji formatowania. Oznacza to, że formant edycji rich obsługuje zmianę atrybutów znaków lub akapitów zaznaczonego tekstu. Niektóre przykłady atrybutów znaków to pogrubienie, kursywa, rodzina czcionek i rozmiar punktów. Przykłady atrybutów akapitu obejmują wyrównanie, marginesy i tabulatory. Jednak to do Ciebie, aby zapewnić interfejs użytkownika, czy jest to przyciski paska narzędzi, elementy menu lub okno dialogowe znak formatu. Istnieją również funkcje do wykonywania zapytań o formant edycji bogatej dla atrybutów bieżącego zaznaczenia. Te funkcje służą do wyświetlania bieżących ustawień atrybutów, na przykład ustawiania znacznika wyboru w interfejsie użytkownika polecenia, jeśli zaznaczenie ma atrybut formatowania pogrubienia.

Aby uzyskać więcej informacji na temat formatowania znaków i akapitów, zobacz [Formatowanie znaków](../mfc/character-formatting-in-rich-edit-controls.md) i [formatowanie akapitu](../mfc/paragraph-formatting-in-rich-edit-controls.md) w dalszej części tego tematu.

Zaawansowane formanty edycji obsługują prawie wszystkie operacje i komunikaty powiadomień używane z wielowierszowymi formantami edycji. W związku z tym aplikacje, które już używają formantów edycji można łatwo zmienić, aby używać formantów edycji bogatej. Dodatkowe komunikaty i powiadomienia umożliwiają aplikacjom dostęp do funkcji unikatowych dla formantów edycji. Aby uzyskać informacje na temat kontrolek edycji, zobacz [CEdit](../mfc/reference/cedit-class.md).

Aby uzyskać więcej informacji na temat powiadomień, zobacz [Powiadomienia z zaawansowanego formantu edycji](../mfc/notifications-from-a-rich-edit-control.md) w dalszej części tego tematu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
