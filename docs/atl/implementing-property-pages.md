---
title: Implementowanie stron właściwości
ms.date: 11/04/2016
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
ms.openlocfilehash: 6544f5ddf0b81fdec893308bb10e0c19cea73005
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499452"
---
# <a name="implementing-property-pages"></a>Implementowanie stron właściwości

::: moniker range="vs-2019"

Kreator strony właściwości ATL nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Strony właściwości to obiekty COM implementujące `IPropertyPage` interfejs lub `IPropertyPage2` . ATL zapewnia obsługę implementowania stron właściwości za pomocą [Kreatora strony właściwości ATL](../atl/reference/atl-property-page-wizard.md) w [oknie dialogowym Dodaj klasę](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box).

Aby utworzyć stronę właściwości przy użyciu biblioteki ATL:

- Utwórz lub Otwórz projekt serwera biblioteki dołączanej dynamicznie (DLL) ATL.

- Otwórz okno [dialogowe Dodawanie klasy](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) i wybierz opcję **Strona właściwości ATL**.

- Upewnij się, że strona właściwości jest komórką Apartment (ponieważ ma interfejs użytkownika).

- Ustaw tytuł, opis (doc String) i plik pomocy, który ma zostać skojarzony ze stroną.

- Dodaj formanty do wygenerowanego zasobu okna dialogowego, aby pełnić rolę interfejsu użytkownika strony właściwości.

- Odpowiedz na zmiany w interfejsie użytkownika strony, aby przeprowadzić walidację, zaktualizować witrynę strony lub zaktualizować obiekty skojarzone ze stroną. W szczególności należy wywołać metodę [IPropertyPageImpl:: SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) , gdy użytkownik wprowadza zmiany na stronie właściwości.

- Opcjonalnie Przesłoń `IPropertyPageImpl` metody, korzystając z poniższych wskazówek.

   |IPropertyPageImpl, Metoda|Przesłoń, gdy chcesz...|Uwagi|
   |------------------------------|----------------------------------|-----------|
   |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|Wykonaj podstawowe testy Sanity na liczbę obiektów, które są przesyłane do strony, oraz obsługiwane przez nich interfejsy.|Wykonaj własny kod przed wywołaniem implementacji klasy bazowej. Jeśli ustawione obiekty nie są zgodne z oczekiwaniami, należy wykonać wywołanie najszybciej, jak to możliwe.|
   |[Zdezaktywować](../atl/reference/ipropertypageimpl-class.md#activate)|Zainicjuj interfejs użytkownika strony (na przykład ustaw kontrolki okna dialogowego z bieżącymi wartościami właściwości z obiektów, twórz formanty dynamicznie lub wykonuj inne inicjalizacje).|Wywołaj implementację klasy bazowej przed kodem, aby Klasa bazowa mogła utworzyć okno dialogowe i wszystkie formanty przed próbą ich aktualizacji.|
   |[Zastosuj](../atl/reference/ipropertypageimpl-class.md#apply)|Sprawdź poprawność ustawień właściwości i zaktualizuj obiekty.|Nie ma potrzeby wywoływania implementacji klasy podstawowej, ponieważ nie ma nic więcej od śledzenia wywołania.|
   |[Dezaktywuj](../atl/reference/ipropertypageimpl-class.md#deactivate)|Wyczyść elementy związane z oknem.|Implementacja klasy bazowej niszczy okno dialogowe reprezentujące stronę właściwości. Aby wyczyścić przed zniszczeniem okna dialogowego, należy dodać kod przed wywołaniem klasy bazowej.|

Aby zapoznać się z przykładową implementacją strony właściwości, zobacz [przykład: implementowanie strony właściwości](../atl/example-implementing-a-property-page.md).

> [!NOTE]
> Jeśli chcesz hostować kontrolki ActiveX na stronie właściwości, musisz zmienić sposób wyprowadzania klasy generowanej przez kreatora. Zastąp **CDialogImpl \<CYourClass> ** z **CAxDialogImpl \<CYourClass> ** na liście klas bazowych.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Strony właściwości](../atl/atl-com-property-pages.md)<br/>
[Przykład ATLPages](../overview/visual-cpp-samples.md)
