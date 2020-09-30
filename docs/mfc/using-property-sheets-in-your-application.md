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
ms.openlocfilehash: 789764c9af988135219bd710d4f8aec1cda9143a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504644"
---
# <a name="using-property-sheets-in-your-application"></a>Używanie arkuszy właściwości w aplikacji

Aby użyć arkusza właściwości w aplikacji, wykonaj następujące czynności:

1. Utwórz zasób szablonu okna dialogowego dla każdej strony właściwości. Należy pamiętać, że użytkownik może przełączać się między stronami, tak jak to możliwe.

   Szablony okna dialogowego dla wszystkich stron nie muszą mieć tego samego rozmiaru. Struktura używa rozmiaru największej strony, aby określić ilość miejsca do przydzielenia w arkuszu właściwości dla stron właściwości.

   Podczas tworzenia zasobu szablon okna dialogowego dla strony właściwości należy określić następujące style w arkuszu właściwości okna dialogowego Właściwości:

   - W polu Edytuj **podpis** na stronie **Ogólne** Ustaw tekst, który ma być wyświetlany na karcie na tej stronie.

   - Ustaw pole listy **styl** na stronie **Style** na **element podrzędny**.

   - Na stronie **Style** Ustaw pole listy **obramowanie** na wartość **cienkie**.

   - Upewnij się, że pole wyboru **paska tytułu** na stronie **Style** jest zaznaczone.

   - Upewnij się, że pole wyboru **wyłączone** na stronie **więcej stylów** jest zaznaczone.

1. Utwórz klasę pochodną [CPropertyPage](../mfc/reference/cpropertypage-class.md)odpowiadającą każdemu szablonowi okna dialogowego strony właściwości. Zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md). Wybierz `CPropertyPage` jako klasę bazową.

1. Utwórz Zmienne Członkowskie, aby przechowywać wartości dla tej strony właściwości. Proces dodawania zmiennych Członkowskich do strony właściwości jest dokładnie taki sam jak dodanie zmiennych Członkowskich do okna dialogowego, ponieważ strona właściwości jest wyspecjalizowanym oknem dialogowym. Aby uzyskać więcej informacji, zobacz [Definiowanie zmiennych członkowskich dla formantów okna dialogowego](../windows/adding-editing-or-deleting-controls.md).

1. Utwórz obiekt [CPropertySheet](../mfc/reference/cpropertysheet-class.md) w kodzie źródłowym. Zwykle obiekt jest skonstruowany `CPropertySheet` w programie obsługi dla polecenia, które wyświetla arkusz właściwości. Ten obiekt reprezentuje cały arkusz właściwości. Jeśli tworzysz modalny arkusz właściwości przy użyciu funkcji [DoModal](../mfc/reference/cpropertysheet-class.md#domodal) , platforma domyślnie udostępnia trzy przyciski poleceń: OK, Anuluj i Zastosuj. Struktura nie tworzy przycisków poleceń dla niemodalnych arkuszy właściwości utworzonych za pomocą funkcji [Create](../mfc/reference/cpropertysheet-class.md#create) . Nie ma potrzeby wyprowadzania klasy z programu, `CPropertySheet` chyba że chcesz dodać inne kontrolki (takie jak okno podglądu) lub wyświetlić niemodalny arkusz właściwości. Ten krok jest niezbędny dla niemodalnych arkuszy właściwości, ponieważ nie zawierają żadnych formantów domyślnych, których można użyć do zamknięcia arkusza właściwości.

1. Dla każdej strony, która ma zostać dodana do arkusza właściwości, wykonaj następujące czynności:

   - Utwórz jeden obiekt dla każdej `CPropertyPage` klasy pochodnej utworzonej wcześniej w tym procesie.

   - Wywołaj [CPropertySheet:: AddPage](../mfc/reference/cpropertysheet-class.md#addpage) dla każdej strony.

   Zazwyczaj obiekt, który tworzy, `CPropertySheet` tworzy również `CPropertyPage` obiekty w tym kroku. Jednak w przypadku zaimplementowania `CPropertySheet` klasy pochodnej można osadzić `CPropertyPage` obiekty w `CPropertySheet` obiekcie i wywołać `AddPage` dla każdej strony z `CPropertySheet` konstruktora klasy pochodnej. `AddPage` dodaje `CPropertyPage` obiekt do listy stron arkusza właściwości, ale w rzeczywistości nie tworzy okna dla tej strony. W związku z tym nie trzeba czekać do momentu utworzenia okna arkusza właściwości do wywołania `AddPage` ; można wywołać metodę `AddPage` z konstruktora arkusza właściwości.

   Domyślnie jeśli arkusz właściwości zawiera więcej kart, niż mieści się w pojedynczym wierszu arkusza właściwości, karty stosują się do wielu wierszy. Aby wyłączyć funkcję Stacking, wywołaj [CPropertySheet:: EnableStackedTabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs) z parametrem ustawionym na **wartość false**. Należy wywołać `EnableStackedTabs` podczas tworzenia arkusza właściwości.

1. Call [CPropertySheet::D omodal](../mfc/reference/cpropertysheet-class.md#domodal) lub [Create](../mfc/reference/cpropertysheet-class.md#create) , aby wyświetlić arkusz właściwości. Wywołaj, `DoModal` Aby utworzyć arkusz właściwości jako modalne okno dialogowe. Wywołanie **Create** , aby utworzyć arkusz właściwości jako niemodalne okno dialogowe.

1. Wymieniaj dane między stronami właściwości a właścicielem arkusza właściwości. Wyjaśniono to w artykule [wymiana danych](../mfc/exchanging-data.md).

Aby zapoznać się z przykładem korzystania z arkuszy właściwości, zobacz Ogólne przykładowe [PROPDLG](../overview/visual-cpp-samples.md)MFC.

## <a name="see-also"></a>Zobacz też

[Arkusze właściwości](../mfc/property-sheets-mfc.md)
