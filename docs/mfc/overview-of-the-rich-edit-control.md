---
title: Omówienie formantu edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: b99a5c6faaae4679b6aef67f240febbfb0f596e8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617713"
---
# <a name="overview-of-the-rich-edit-control"></a>Omówienie formantu edycji wzbogaconej

> [!IMPORTANT]
> Jeśli używasz kontrolki edycji wzbogaconej w oknie dialogowym (bez względu na to, czy aplikacja jest oparta na interfejsie SDI, MDI czy w oknie dialogowym), musisz wywołać [AfxInitRichEdit](reference/application-information-and-management.md#afxinitrichedit) raz przed wyświetleniem okna dialogowego. Typowym miejscem do wywołania tej funkcji jest `InitInstance` funkcja członkowska programu. Nie trzeba go wywoływać za każdym razem, gdy wyświetlasz okno dialogowe, tylko po raz pierwszy. Nie jest konieczne wywoływanie, `AfxInitRichEdit` Jeśli pracujesz z usługą `CRichEditView` .

Formanty edycji wzbogaconej ([CRichEditCtrl](reference/cricheditctrl-class.md)) zapewniają interfejs programowania do formatowania tekstu. Jednak aplikacja musi zaimplementować wszelkie składniki interfejsu użytkownika niezbędne do udostępnienia użytkownikowi operacji formatowania. Oznacza to, że formant edycji wzbogaconej obsługuje zmianę atrybutów znaków lub akapitu zaznaczonego tekstu. Przykłady atrybutów znaków to pogrubienie, kursywa, Rodzina czcionek i rozmiar punktu. Przykłady atrybutów akapitu obejmują wyrównanie, marginesy i tabulatory. Można jednak zapewnić interfejs użytkownika, czy są to przyciski paska narzędzi, elementy menu czy okno dialogowe znak formatowania. Istnieją również funkcje do wykonywania zapytań dotyczących kontrolki edycji wzbogaconej dotyczącej atrybutów bieżącego zaznaczenia. Użyj tych funkcji, aby wyświetlić bieżące ustawienia dla atrybutów, na przykład ustawienie znacznika wyboru w interfejsie użytkownika poleceń, jeśli zaznaczenie ma atrybut formatowania pogrubiony znak.

Aby uzyskać więcej informacji na temat formatowania znaków i akapitów, zobacz [Formatowanie znaków](character-formatting-in-rich-edit-controls.md) i [Formatowanie akapitu](paragraph-formatting-in-rich-edit-controls.md) w dalszej części tego tematu.

Kontrolki edycji wzbogaconej obsługują niemal wszystkie operacje i komunikaty powiadomień używane w wielowierszowych formantach edycji. W ten sposób aplikacje, które już używają kontrolek edycji, można łatwo zmienić, aby użyć kontrolek edycji wzbogaconej. Dodatkowe komunikaty i powiadomienia umożliwiają aplikacjom dostęp do funkcji unikatowych dla kontrolek edycji wzbogaconej. Aby uzyskać informacje o kontrolkach edycji, zobacz [CEdit](reference/cedit-class.md).

Aby uzyskać więcej informacji na temat powiadomień, zobacz [powiadomienia z kontrolki edycji wzbogaconej](notifications-from-a-rich-edit-control.md) w dalszej części tego tematu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](using-cricheditctrl.md)<br/>
[Formanty](controls-mfc.md)
