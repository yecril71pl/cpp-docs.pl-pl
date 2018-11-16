---
title: Dodawanie obsługi zdarzeń
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.eventhandler.overview
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
- event handler wizard [C++]
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
ms.openlocfilehash: 8e6b2511b00b7f949718e5b0d9fd793ac53d0d8b
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694520"
---
# <a name="add-an-event-handler"></a>Dodawanie obsługi zdarzeń

W edytorze zasobów, możesz dodać nowy program obsługi zdarzeń lub edycji istniejącego programu obsługi zdarzeń, dla okna dialogowego pole kontrolkę za pomocą [Kreator obsługi zdarzeń](#event-handler-wizard).

Zdarzenie można dodać do klasy wdrożenie przy użyciu okno dialogowe [okno właściwości](/visualstudio/ide/reference/properties-window). Aby dodać zdarzenie do klasy innej niż klasa okno dialogowe, należy użyć Kreator obsługi zdarzeń.

**Aby dodać program obsługi zdarzeń do formantu pola w oknie dialogowym:**

1. Kliknij dwukrotnie zasobu okna dialogowego pole w [widok zasobów](../windows/resource-view-window.md) można otworzyć zasobu okna dialogowego pole, który zawiera formant w [Edytor okien dialogowych](../windows/dialog-editor.md).

1. Kliknij prawym przyciskiem myszy formant, dla którego chcesz obsłużyć zdarzenie powiadomienia.

1. W menu skrótów wybierz **dodać program obsługi zdarzeń** do wyświetlenia Kreator obsługi zdarzeń.

1. Wybierz zdarzenie w **typ komunikatu** pole, aby dodać do klasy wybrane w **listy klas** pole.

1. Zaakceptuj nazwę domyślną w **Nazwa procedury obsługi funkcji** pole lub podaj wybraną nazwę.

1. Wybierz **dodawania i edytowania** Dodaj program obsługi zdarzeń do projektu i Otwórz Edytor tekstu na nową funkcję, aby Dodaj kod procedury obsługi zdarzeń właściwe.

   Jeśli typ wybranego komunikatu ma już program obsługi zdarzeń dla wybranej klasy **dodawania i edytowania** jest niedostępny, a **edytowania kodu** jest dostępna. Wybierz **edytowania kodu** można otworzyć edytora tekstu w istniejącej funkcji.

Alternatywnie można dodać procedury obsługi zdarzeń z [okno właściwości](/visualstudio/ide/reference/properties-window). Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi zdarzeń dla formantów okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md).

## <a name="in-this-section"></a>W tej sekcji

- [Kreator obsługi zdarzeń](#event-handler-wizard)

## <a name="event-handler-wizard"></a>Kreator obsługi zdarzeń

Ten kreator dodaje program obsługi zdarzeń dla formantu pola okna dialogowego do klasy wybranych przez użytkownika. Po dodaniu programu obsługi zdarzeń z [okno właściwości](/visualstudio/ide/reference/properties-window), można go dodać tylko do klasy, która implementuje okno dialogowe. Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi zdarzeń dla formantów okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md).

- **Nazwa polecenia**

  Identyfikuje zaznaczonego formantu, do którego jest dodawany program obsługi zdarzeń. To pole jest niedostępne.

- **Typ komunikatu**

  Wyświetla listę bieżącej obsługi komunikatów możliwe dla zaznaczonej kontrolki.

- **Nazwa procedury obsługi — funkcja**

  Wyświetla nazwę funkcji, który jest dodawany do obsługi zdarzeń. Nazwa domyślna jest oparta na typ komunikatu i polecenia dołączony przez `On`. Na przykład dla przycisku o nazwie `IDC_BUTTON1`, typ komunikatu `BN_CLICKED` Wyświetla nazwę procedury obsługi funkcji `OnBnClickedButton1`.

- **Lista klas**

  Wyświetla dostępne klasy, do których można dodać program obsługi zdarzeń. Klasa wybranego okna dialogowego jest wyświetlany w kolorze czerwonym.

- **Opis procedury obsługi**

  Zawiera opis elementu zaznaczonego w **typ komunikatu** pole. To pole jest niedostępne.

- **Dodawanie i edytowanie**

  Dodaje program obsługi komunikatów do wybranej klasy lub obiektu. Otwiera również nową funkcję w edytorze tekstu, dzięki czemu można dodać kod procedury obsługi powiadamiania kontrolki.

- **Edytowanie kodu**

  Zostanie otwarty Edytor tekstów, aby wybrane istniejącą funkcję, dzięki czemu można dodawać lub edytować kod procedury obsługi powiadamiania kontrolki.
