---
title: Używanie arkuszy właściwości w aplikacji
ms.date: 11/04/2016
helpviewer_keywords:
- dialog templates [MFC], property sheets
- dialog resources
- property pages [MFC], property sheets
- DoModal method property sheets
- AddPage method [MFC]
- property sheets, about property sheets
- Create method [MFC], property sheets
- CPropertyPage class [MFC], styles
ms.assetid: 240654d4-152b-4e3f-af7b-44234339206e
ms.openlocfilehash: 4fd68f57db082ab0b0da0e8248e0be239c63c99a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773219"
---
# <a name="using-property-sheets-in-your-application"></a>Używanie arkuszy właściwości w aplikacji

Aby korzystać z arkusza właściwości w aplikacji, wykonaj następujące czynności:

1. Tworzenie zasobu okna dialogowego szablon dla każdej strony właściwości. Należy pamiętać, który może być przełączanie użytkowników z jednej strony do innego, więc układ każdej strony możliwie jak spójnie.

   Szablony okna dialogowego na wszystkich stronach nie trzeba mieć taki sam rozmiar. Środowisko wykorzystuje rozmiar największego strony, aby określić, ile miejsca do przydzielenia w arkuszu właściwości dla stron właściwości.

   Podczas tworzenia zasobu szablonu okna dialogowego strony właściwości, należy określić następujące style w arkuszu właściwości okna dialogowego właściwości:

   - Ustaw **podpis** edytować pola na **ogólne** strony w tekście, które mają być wyświetlane na karcie tej strony.

   - Ustaw **styl** pola listy na **style** stronie **podrzędnych**.

   - Ustaw **obramowania** pola listy na **style** stronie **uproszczonym**.

   - Upewnij się, że **Titlebar** pole wyboru na **style** została zaznaczona strona.

   - Upewnij się, że **wyłączone** pole wyboru na **więcej stylów** została zaznaczona strona.

1. Tworzenie [CPropertyPage](../mfc/reference/cpropertypage-class.md)— odpowiadający każdego szablonu okna dialogowego strony właściwości klasy pochodnej. Zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md). Wybierz `CPropertyPage` jako klasa bazowa.

1. Utwórz element członkowski zmienne do przechowywania wartości dla tej strony właściwości. Proces dodawania zmiennych składowych do strony właściwości jest dokładnie taka sama jak dodawanie zmiennych składowych do okna dialogowego, ponieważ wyspecjalizowane okno dialogowe strony właściwości. Aby uzyskać więcej informacji, zobacz [Definiowanie zmiennych Członkowskich dla formantów okna dialogowego](../windows/defining-member-variables-for-dialog-controls.md).

1. Konstruowania [CPropertySheet](../mfc/reference/cpropertysheet-class.md) obiektu w kodzie źródłowym. Zazwyczaj konstruowania `CPropertySheet` obiekt programu obsługi dla polecenia, które wyświetla arkusz właściwości. Ten obiekt reprezentuje arkusza właściwości całego. Jeśli tworzysz modalny arkusz właściwości z [DoModal](../mfc/reference/cpropertysheet-class.md#domodal) funkcji w ramach dostarcza trzy przyciski poleceń domyślnie: Dobrze Anuluj i zastosować. Szablon tworzy przyciski nie poleceń dla niemodalne arkusze właściwości są tworzone za pomocą [Utwórz](../mfc/reference/cpropertysheet-class.md#create) funkcji. Nie należy wyprowadzić klasę z `CPropertySheet` chyba że chcesz dodać inne formanty (na przykład okno podglądu) lub wyświetlić niemodalnego arkusza właściwości. Ten krok jest konieczny do niemodalne arkusze właściwości, ponieważ nie zawierają żadnych kontrolkami domyślnymi, które mogłyby zostać użyte, aby zamknąć arkusza właściwości.

1. Dla każdej strony, które mają zostać dodane do arkusza właściwości należy wykonać następujące czynności:

   - Utworzyć jeden obiekt dla każdego `CPropertyPage`-klasy, który został utworzony we wcześniejszej części tego procesu.

   - Wywołaj [CPropertySheet::AddPage](../mfc/reference/cpropertysheet-class.md#addpage) dla każdej strony.

   Zazwyczaj obiekt, który tworzy `CPropertySheet` wzrasta, powstaje `CPropertyPage` obiektów w tym kroku. Jednak w przypadku zaimplementowania `CPropertySheet`-klasy, można osadzić `CPropertyPage` obiekty w `CPropertySheet` obiektu, a następnie wywołać `AddPage` dla każdej strony z `CPropertySheet`— Konstruktor klasy pochodnej. `AddPage` dodaje `CPropertyPage` do listy stron w arkuszu właściwości obiektu, ale nie powoduje utworzenia okno dla tej strony. W związku z tym, nie jest konieczne czekać do momentu utworzenia okna arkusza właściwości, aby wywołać `AddPage`; może wywołać `AddPage` z arkusza właściwości konstruktora.

   Domyślnie jeśli arkusz właściwości ma więcej kart niż mieści się w jednym wierszu arkusza właściwości karty będą umieszczane w wielu wierszach. Aby wyłączyć umieszczanie na stosie, należy wywołać [CPropertySheet::EnableStackedTabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs) z parametrem ustawionym **FALSE**. Należy wywołać `EnableStackedTabs` po utworzeniu arkusza właściwości.

1. Wywołaj [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal) lub [Utwórz](../mfc/reference/cpropertysheet-class.md#create) do wyświetlenia arkusza właściwości. Wywołaj `DoModal` Utwórz arkusz właściwości jako modalne okno dialogowe. Wywołaj **Utwórz** utworzyć arkusz właściwości jako niemodalnego okna dialogowego.

1. Wymiana danych pomiędzy właściciela arkusza właściwości i strony właściwości. Wyjaśnienie jest zawarte w artykule [wymiana danych](../mfc/exchanging-data.md).

Na przykład jak używać arkuszy właściwości, zobacz próbki MFC-ogólne [PROPDLG](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz także

[Arkusze właściwości](../mfc/property-sheets-mfc.md)
