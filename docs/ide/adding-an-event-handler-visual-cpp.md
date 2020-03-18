---
title: Dodawanie procedury obsługi zdarzeń
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
- event handler wizard [C++]
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
ms.openlocfilehash: 0d852991c29281a7ecf912bd3d764d9916ef10f7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447509"
---
# <a name="add-an-event-handler"></a>Dodawanie procedury obsługi zdarzeń

Z edytora zasobów można dodać nowy program obsługi zdarzeń lub edytować istniejący program obsługi zdarzeń dla formantu okna dialogowego przy użyciu [Kreatora obsługi zdarzeń](#event-handler-wizard).

Można dodać zdarzenie do klasy implementującej okno dialogowe przy użyciu [okno właściwości](/visualstudio/ide/reference/properties-window). Aby dodać zdarzenie do klasy innej niż Klasa okna dialogowego, użyj Kreatora obsługi zdarzeń.

**Aby dodać program obsługi zdarzeń do kontrolki okna dialogowego:**

1. Kliknij dwukrotnie zasób okna dialogowego w [Widok zasobów](../windows/how-to-create-a-resource-script-file.md#create-resources) , aby otworzyć zasób okna dialogowego, który zawiera kontrolkę w [edytorze okien dialogowych](../windows/dialog-editor.md).

1. Kliknij prawym przyciskiem myszy kontrolkę, dla której chcesz obsłużyć zdarzenie powiadamiania.

1. W menu skrótów wybierz polecenie **Dodaj program obsługi zdarzeń** , aby wyświetlić Kreatora obsługi zdarzeń.

1. Wybierz zdarzenie w polu **typ komunikatu** , aby dodać do klasy wybranej w polu **listy klas** .

1. Zaakceptuj nazwę domyślną w polu **nazwa procedury obsługi funkcji** lub podaj wybraną nazwę.

1. Wybierz pozycję **Dodaj i edytuj** , aby dodać obsługę zdarzeń do projektu i Otwórz Edytor tekstów w nowej funkcji, aby dodać odpowiedni kod procedury obsługi zdarzeń.

   Jeśli wybrany typ komunikatu ma już procedurę obsługi zdarzeń dla wybranej klasy, **Dodawanie i edytowanie** jest niedostępne, a **Edycja kodu** jest dostępna. Wybierz pozycję **Edytuj kod** , aby otworzyć Edytor tekstu w istniejącej funkcji.

Można też dodać procedury obsługi zdarzeń z [okno właściwości](/visualstudio/ide/reference/properties-window). Aby uzyskać więcej informacji, zobacz [Dodawanie programów obsługi zdarzeń dla kontrolek okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md).

## <a name="in-this-section"></a>W tej sekcji

- [Kreator obsługi zdarzeń](#event-handler-wizard)

## <a name="event-handler-wizard"></a>Kreator obsługi zdarzeń

Ten Kreator dodaje procedurę obsługi zdarzeń dla kontrolki okna dialogowego do wybranej klasy. Jeśli dodasz procedurę obsługi zdarzeń z [okno właściwości](/visualstudio/ide/reference/properties-window), możesz dodać ją tylko do klasy, która implementuje okno dialogowe. Aby uzyskać więcej informacji, zobacz [Dodawanie programów obsługi zdarzeń dla kontrolek okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md).

- **Nazwa polecenia**

  Identyfikuje wybraną kontrolkę, dla której dodano procedurę obsługi zdarzeń. To pole jest niedostępne.

- **Typ komunikatu**

  Wyświetla listę bieżących możliwych programów obsługi komunikatów dla wybranej kontrolki.

- **Nazwa procedury obsługi funkcji**

  Wyświetla nazwę funkcji dodanej do obsłużenia zdarzenia. Nazwa jest domyślnie oparta na typie komunikatu i poleceniu, poprzedzone przez `On`. Na przykład dla przycisku o nazwie `IDC_BUTTON1`, typ komunikatu `BN_CLICKED` wyświetla nazwę procedury obsługi funkcji `OnBnClickedButton1`.

- **Lista klas**

  Wyświetla dostępne klasy, do których można dodać program obsługi zdarzeń. Klasa wybranego okna dialogowego jest wyświetlana na czerwono.

- **Opis procedury obsługi**

  Zawiera opis elementu wybranego w polu **typ komunikatu** . To pole jest niedostępne.

- **Dodawanie i edytowanie**

  Dodaje procedurę obsługi komunikatów do wybranej klasy lub obiektu. Otwiera również Edytor tekstu do nowej funkcji, aby można było dodać kod procedury obsługi dla powiadomienia o kontroli.

- **Edytuj kod**

  Otwiera edytor tekstu do wybranej istniejącej funkcji, aby można było dodać lub edytować kod procedury obsługi powiadomień.
