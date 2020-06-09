---
title: Okna dialogowe
ms.date: 11/04/2016
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
ms.openlocfilehash: da6a2eca7c2366e519b9bf2e809b042dc3ee2e50
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616870"
---
# <a name="dialog-boxes"></a>Okna dialogowe

Aplikacje dla systemu Windows często komunikują się z użytkownikiem przy użyciu okien dialogowych. Klasa [CDialog](reference/cdialog-class.md) udostępnia interfejs do zarządzania oknach dialogowych, Edytor okna dialogowego Visual C++ ułatwia projektowanie okien dialogowych i tworzenie zasobów szablonów okien dialogowych, a kreatory kodu upraszczają proces inicjowania i sprawdzania poprawności kontrolek w oknie dialogowym oraz zbierania wartości wprowadzonych przez użytkownika.

Okna dialogowe zawierają kontrolki, w tym:

- Formanty standardowe systemu Windows, takie jak pola edycji, przyciski, pola listy, pola kombi, kontrolki drzewa, kontrolki listy i wskaźniki postępu.

- Kontrolki ActiveX.

- Kontrolki rysowane przez właściciela: kontrolki, które są odpowiedzialne za Rysowanie w oknie dialogowym.

Większość okien dialogowych jest modalnych, co wymaga od użytkownika zamknięcia okna dialogowego przed użyciem innej części programu. Ale istnieje możliwość tworzenia niemodalnych okien dialogowych, które umożliwiają użytkownikom współpracę z innymi oknami, gdy okno dialogowe jest otwarte. MFC obsługuje oba rodzaje okien dialogowych z klasą `CDialog` . Kontrolki są rozmieszczane i zarządzane przy użyciu zasobu szablonu okna dialogowego utworzonego za pomocą [edytora okien dialogowych](../windows/dialog-editor.md).

[Arkusze właściwości](property-sheets-mfc.md), znane również jako okna dialogowe kart, to okna dialogowe zawierające "strony" różnych kontrolek okna dialogowego. Każda Strona ma folder plików "Tab" u góry. Kliknięcie karty powoduje wyświetlenie tej strony na początku okna dialogowego.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Przykład: wyświetlanie okna dialogowego za pomocą polecenia menu](example-displaying-a-dialog-box-via-a-menu-command.md)

- [Składniki okna dialogowego w strukturze](dialog-box-components-in-the-framework.md)

- [Modalne i Niemodalne okna dialogowe](modal-and-modeless-dialog-boxes.md)

- [Arkusze właściwości i strony właściwości](property-sheets-and-property-pages-mfc.md) w oknie dialogowym

- [Tworzenie zasobu okna dialogowego](creating-the-dialog-resource.md)

- [Tworzenie klasy okien dialogowych za pomocą kreatorów kodu](creating-a-dialog-class-with-code-wizards.md)

- [Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)

- [Wymiana danych okna dialogowego (DDX) i walidacja (DDV)](dialog-data-exchange-and-validation.md)

- [Bezpieczny dostęp do kontrolek w oknie dialogowym](type-safe-access-to-controls-in-a-dialog-box.md)

- [Mapowanie komunikatów systemu Windows do klasy](mapping-windows-messages-to-your-class.md)

- [Powszechnie zastępowane funkcje członkowskie](commonly-overridden-member-functions.md)

- [Powszechnie dodawane funkcje składowe](commonly-added-member-functions.md)

- [Wspólne klasy okien dialogowych](common-dialog-classes.md)

- [Okna dialogowe w OLE](dialog-boxes-in-ole.md)

- Tworzenie aplikacji, której interfejs użytkownika jest oknem dialogowym: zobacz [CMNCTRL1](../overview/visual-cpp-samples.md) lub [CMNCTRL2](../overview/visual-cpp-samples.md) przykładowe programy. Ta opcja jest również dostępna w Kreatorze aplikacji.

- [Samples](dialog-sample-list.md)

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](user-interface-elements-mfc.md)
