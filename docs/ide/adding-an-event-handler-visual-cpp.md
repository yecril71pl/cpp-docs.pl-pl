---
title: Dodawanie obsługi zdarzeń (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
ms.openlocfilehash: d9256fca75b6980d87382bbeb794fa90b89f37c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512444"
---
# <a name="adding-an-event-handler-visual-c"></a>Dodawanie obsługi zdarzeń (Visual C++)

W edytorze zasobów, możesz dodać nowy program obsługi zdarzeń lub edycji istniejącego programu obsługi zdarzeń, dla okna dialogowego pole kontrolkę za pomocą [Kreator obsługi zdarzeń](../ide/event-handler-wizard.md).

Zdarzenie można dodać do klasy wdrożenie przy użyciu okno dialogowe [okno właściwości](/visualstudio/ide/reference/properties-window). Jeśli chcesz dodać zdarzenie do klasy innej niż klasa okno dialogowe, należy użyć Kreator obsługi zdarzeń.

### <a name="to-add-an-event-handler-to-a-dialog-box-control"></a>Aby dodać program obsługi zdarzeń do kontrolka okna dialogowego

1. Kliknij dwukrotnie zasobu okna dialogowego pole w [widok zasobów](../windows/resource-view-window.md) można otworzyć zasobu okna dialogowego pole, który zawiera formant w [Edytor okien dialogowych](../windows/dialog-editor.md).

1. Kliknij prawym przyciskiem myszy formant, dla którego chcesz obsłużyć zdarzenie powiadomienia.

1. W menu skrótów kliknij **dodać program obsługi zdarzeń** do wyświetlenia Kreator obsługi zdarzeń.

1. Wybierz zdarzenie w **typ komunikatu** pole, aby dodać do klasy wybrane w **listy klas** pole.

1. Zaakceptuj nazwę domyślną w **Nazwa procedury obsługi funkcji** pole lub podaj wybraną nazwę.

1. Kliknij przycisk **dodawania i edytowania** Dodaj program obsługi zdarzeń do projektu i Otwórz Edytor tekstu na nową funkcję, aby Dodaj kod procedury obsługi zdarzeń właściwe.

   Jeśli typ wybranego komunikatu ma już program obsługi zdarzeń dla wybranej klasy **dodawania i edytowania** jest niedostępny, a **edytowania kodu** jest dostępna. Kliknij przycisk **edytowania kodu** można otworzyć edytora tekstu w istniejącej funkcji.

Alternatywnie można dodać procedury obsługi zdarzeń z [okno właściwości](/visualstudio/ide/reference/properties-window). Zobacz [Dodawanie obsługi zdarzeń dla formantów okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Dodawanie funkcji za pomocą kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)<br>
[Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)<br>
[Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)<br>
[Handler komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[Nawigacja w strukturze klas](../ide/navigating-the-class-structure-visual-cpp.md)