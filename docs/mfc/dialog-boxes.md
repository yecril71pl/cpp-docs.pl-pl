---
title: Okna dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f26f5cad47815c25602eba836a482e6f6cecc85d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424940"
---
# <a name="dialog-boxes"></a>Okna dialogowe

Aplikacje dla Windows często komunikują się z użytkownikiem za pośrednictwem okna dialogowe. Klasa [CDialog](../mfc/reference/cdialog-class.md) udostępnia interfejs dla zarządzania okien dialogowych, Edytor okien dialogowych Visual C++ ułatwia projektowanie okien dialogowych i tworzenie ich zasobów szablonu okna dialogowego i kreatorów kodu upraszcza proces inicjowania i Sprawdzanie poprawności formantów w oknie dialogowym i zbierania wartości wprowadzonej przez użytkownika.

Okna dialogowe zawierają formantów, w tym:

- Typowe kontrolki Windows takich jak edytować pola, przyciski, pola listy, pola kombi, kontrolki drzewa, kontrolki listy i wskaźniki postępu.

- Kontrolki ActiveX.

- Formanty rysowane przez właściciela: formanty, które są odpowiedzialne za narysowanie w oknie dialogowym.

Większość okna dialogowe są modalne, która wymaga od użytkownika zamknąć okno dialogowe przed rozpoczęciem korzystania z innych części programu. Jednak jest możliwe tworzenie niemodalnych okien dialogowych, które umożliwiają użytkownikom pracę z innymi oknami, gdy jest otwarte okno dialogowe. Biblioteka MFC obsługuje oba rodzaje okno dialogowe z klasą `CDialog`. Formanty są uporządkowane i zarządzane przy użyciu zasobu szablonu okna dialogowego, utworzony za pomocą [Edytor okien dialogowych](../windows/dialog-editor.md).

[Arkusze właściwości](../mfc/property-sheets-mfc.md), znany także jako karcie okna dialogowe, są okna dialogowe, zawierające "strony" formantów distinct okno dialogowe. Każda strona ma folder plików "kartę" u góry. Po kliknięciu karty zapewnia tej strony na początku okna dialogowego.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Przykład: wyświetlanie okna dialogowego za pomocą polecenia menu](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)

- [Składniki okna dialogowego w strukturze](../mfc/dialog-box-components-in-the-framework.md)

- [Modalne i Niemodalne okna dialogowe](../mfc/modal-and-modeless-dialog-boxes.md)

- [Arkusze właściwości i strony właściwości](../mfc/property-sheets-and-property-pages-mfc.md) w oknie dialogowym

- [Tworzenie zasobu okna dialogowego](../mfc/creating-the-dialog-resource.md)

- [Tworzenie klasy okien dialogowych za pomocą kreatorów kodu](../mfc/creating-a-dialog-class-with-code-wizards.md)

- [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

- [Wymiana danych okna dialogowego (DDX) i sprawdzania poprawności (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Bezpieczny dostęp do formantów w oknie dialogowym](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Mapowanie komunikatów Windows na klasę](../mfc/mapping-windows-messages-to-your-class.md)

- [Powszechnie zastępowane funkcje składowe](../mfc/commonly-overridden-member-functions.md)

- [Powszechnie dodawane funkcje składowe](../mfc/commonly-added-member-functions.md)

- [Klasy wspólnych okien dialogowych](../mfc/common-dialog-classes.md)

- [Okna dialogowe w OLE](../mfc/dialog-boxes-in-ole.md)

- Tworzenie aplikacji interfejsu użytkownika, którego to okno dialogowe: zobacz [CMNCTRL1](../visual-cpp-samples.md) lub [CMNCTRL2](../visual-cpp-samples.md) przykładowe programy. Kreator aplikacji udostępnia również tej opcji.

- [Przykłady](../mfc/dialog-sample-list.md)

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
