---
title: Implementowanie stron właściwości
ms.date: 11/04/2016
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
ms.openlocfilehash: 8999f6469e420fa86cb1267675f10dc173d45ff0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776254"
---
# <a name="implementing-property-pages"></a>Implementowanie stron właściwości

Strony właściwości są obiektów COM, które implementują `IPropertyPage` lub `IPropertyPage2` interfejsu. ATL zapewnia obsługę implementowania strony właściwości, za pośrednictwem [Kreator strony właściwości ATL](../atl/reference/atl-property-page-wizard.md) w [okno dialogowe Dodaj klasę](../ide/add-class-dialog-box.md).

Aby utworzyć stronę właściwości przy użyciu biblioteki ATL:

- Utwórz lub Otwórz projekt serwera ATL dołączana dynamicznie biblioteka (DLL).

- Otwórz [okno dialogowe Dodaj klasę](../ide/add-class-dialog-box.md) i wybierz **strony właściwości ATL**.

- Upewnij się, że strona właściwości jest typu apartment Threading (ponieważ ma on interfejsu użytkownika).

- Ustaw tytuł, opis (Doc String) i plik pomocy do skojarzenia z Twojej strony.

- Dodawanie formantów do okna dialogowego wygenerowanego pełnić rolę interfejsu użytkownika strony właściwości.

- Odpowiadanie na zmiany w interfejsie użytkownika strony do przeprowadzenia weryfikacji, zaktualizuj lokację strony lub zaktualizować obiekty skojarzone z Twojej strony. W szczególności należy wywołać [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) po użytkownik wprowadza zmiany do strony właściwości.

- Opcjonalnie zastąpić `IPropertyPageImpl` metod, korzystając z poniższych wskazówek.

   |Metoda IPropertyPageImpl|Zastąp, jeśli chcesz...|Uwagi|
   |------------------------------|----------------------------------|-----------|
   |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|Wykonaj podstawowe wykonuje testów liczbę obiektów, które były przekazywane do strony swojego i interfejsy, które obsługują.|Wykonaj swój kod przed wywołaniem implementacji klasy podstawowej. Jeśli obiekty ustawiania nie odpowiada Twoim oczekiwaniom, wywołanie powinno nie tak szybko, jak to możliwe.|
   |[Aktywuj](../atl/reference/ipropertypageimpl-class.md#activate)|Zainicjuj na stronie interfejsu użytkownika (na przykład ustawić formanty okna dialogowego za pomocą bieżące wartości właściwości z obiektów, dynamicznie utworzyć formanty lub wykonać inne inicjalizacje).|Wywołania implementacji klasy podstawowej zanim kod tak, aby klasa bazowa ma możliwość tworzenia okna dialogowego i wszystkich kontrolek, przed podjęciem próby je zaktualizować.|
   |[Zastosuj](../atl/reference/ipropertypageimpl-class.md#apply)|Sprawdź poprawność ustawień właściwości i zaktualizować obiektów.|Nie ma potrzeby wywoływały implementację klasy podstawowej, ponieważ nie robi nic, oprócz śledzenia wywołania.|
   |[Dezaktywuj](../atl/reference/ipropertypageimpl-class.md#deactivate)|Wyczyść elementy związane z okna.|Implementacja klasy bazowej niszczy okno dialogowe reprezentujący stronę właściwości. Jeśli musisz wyczyścić przed jest niszczony, okno dialogowe, należy dodać kod przed wywołaniem klasy bazowej.|

Przykładem implementacji strony właściwości, można zobaczyć [przykładu: Implementowanie strony właściwości](../atl/example-implementing-a-property-page.md).

> [!NOTE]
> Chcąc formantów ActiveX hosta na stronie właściwości, należy zmienić pochodnym klasy generowane przez kreatora. Zastąp **CDialogImpl\<CYourClass >** z **CAxDialogImpl\<CYourClass >** na liście klas bazowych.

## <a name="see-also"></a>Zobacz także

[Strony właściwości](../atl/atl-com-property-pages.md)<br/>
[Przykładowe ATLPages](../overview/visual-cpp-samples.md)
