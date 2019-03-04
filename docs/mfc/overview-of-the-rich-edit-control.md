---
title: Omówienie formantu edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: c45cb638ec860bb803c7de32065606dc3cc176b2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287716"
---
# <a name="overview-of-the-rich-edit-control"></a>Omówienie formantu edycji wzbogaconej

> [!IMPORTANT]
>  Jeśli używasz kontrolki edycji wzbogaconej, w oknie dialogowym (niezależnie od tego, czy aplikacja działa SDI i MDI, lub oparta na oknach dialogowych), należy wywołać [afxinitrichedit —](../mfc/reference/application-information-and-management.md#afxinitrichedit) po przed okno dialogowe zostanie wyświetlone okno. Typowe miejsce, aby wywołać tę funkcję znajduje się w swoim programie `InitInstance` funkcja elementu członkowskiego. Nie musisz wywołać ją za każdym razem, możesz wyświetlić okno dialogowe tylko za pierwszym razem. Nie trzeba wywoływać `AfxInitRichEdit` Jeśli pracujesz z `CRichEditView`.

Formanty edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) zapewnia interfejs programowania dla formatowania tekstu. Jednak aplikacja musi zaimplementować wszelkie niezbędne udostępnić użytkownikowi operacji formatowania składników interfejsu użytkownika. Oznacza to, że sformatowanego obsługuje formant zmiana atrybutów znaków lub zaznaczonego tekstu. Przykłady znaków, atrybuty pogrubienie, kursywa, rodzinę czcionek i rozmiar punktu. Przykładami atrybuty akapitu wyrównanie, marginesy i tabulatora. Jednak jest maksymalnie musisz podać interfejsu użytkownika, czy to przycisków paska narzędzi, elementy menu lub okno dialogowe znaku z formatu. Dostępne są także funkcje do wykonywania zapytań rozwiniętej kontroli edycji w przypadku atrybutów elementów bieżącego zaznaczenia. Korzystania z tych funkcji, aby wyświetlić bieżące ustawienia dla atrybutów, na przykład ustawienie znacznik wyboru na polecenia interfejsu użytkownika, jeśli wybrano formatowania atrybutu znaków pogrubienie.

Aby uzyskać więcej informacji na temat znaków i formatowanie akapitów, zobacz [formatowania znaków](../mfc/character-formatting-in-rich-edit-controls.md) i [formatowanie akapitów](../mfc/paragraph-formatting-in-rich-edit-controls.md) w dalszej części tego tematu.

Tekstu sformatowanego obsługę formantów prawie wszystkie operacje i komunikaty powiadomień używane z formantami edycji wielowierszowe. W związku z tym czy już Użyj kontrolek edycji można łatwo zmienić na używać zaawansowanych aplikacji edycji wzbogaconej. Dodatkowe komunikaty i powiadomienia umożliwiają aplikacjom dostęp do kontrolek edycji unikatowy dla zaawansowanych funkcji. Aby uzyskać informacje o formantach edycji wzbogaconej, zobacz [CEdit](../mfc/reference/cedit-class.md).

Aby uzyskać więcej informacji na temat powiadomień, zobacz [powiadomień w kontrolce edycji wzbogaconej](../mfc/notifications-from-a-rich-edit-control.md) w dalszej części tego tematu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
