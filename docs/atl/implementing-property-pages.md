---
title: Implementacja strony właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1db6ca4ea374cd76d5b0e1df8e6c0cd03474fdf2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="implementing-property-pages"></a>Implementacja strony właściwości
Strony właściwości są obiektów COM, które implementują `IPropertyPage` lub **IPropertyPage2** interfejsu. ATL zapewnia obsługę implementacja strony właściwości za pośrednictwem [Kreator strony właściwości ATL](../atl/reference/atl-property-page-wizard.md) w [okno dialogowe Dodaj klasę](../ide/add-class-dialog-box.md).  
  
 Aby utworzyć za pomocą biblioteki ATL strony właściwości:  
  
-   Utwórz lub Otwórz projekt ATL DLL biblioteki DLL serwera.  
  
-   Otwórz [okno dialogowe Dodaj klasę](../ide/add-class-dialog-box.md) i wybierz **stronę właściwości ATL**.  
  
-   Upewnij się, że strony właściwości jest apartamentu wątku (ponieważ ma ona interfejsu użytkownika).  
  
-   Ustaw tytuł, opis (Doc String) i plik pomocy ma zostać skojarzony z Twojej strony.  
  
-   Dodawanie formantów do zasobu okna dialogowego wygenerowane jako interfejsu użytkownika strony właściwości.  
  
-   Odpowiedz na zmiany w interfejsie użytkownika strony do sprawdzania poprawności, zaktualizować lokacji strony lub obiekty skojarzone z Twojej strony. W szczególności wywołać [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) gdy użytkownik zmienia się na stronie właściwości.  
  
-   Opcjonalnie zastąpić `IPropertyPageImpl` metod, korzystając z poniższych wskazówek.  
  
    |IPropertyPageImpl — metoda|Zastąp, jeśli chcesz...|Uwagi|  
    |------------------------------|----------------------------------|-----------|  
    |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|Wykonywać podstawowe wykonuje testów liczbę przekazywany do strony swojego i interfejsów, które obsługują obiektów.|Wykonanie własnego kodu przed wywołaniem klasy podstawowej implementacji. Jeśli ustawiany obiekty nie spełniają oczekiwań, należy jak najszybciej nie wywołania.|  
    |[Aktywuj](../atl/reference/ipropertypageimpl-class.md#activate)|Inicjowanie ze strony interfejsu użytkownika (na przykład ustawienie formantów okna dialogowego z bieżącej wartości właściwości z obiektów, dynamiczne tworzenie formantów lub wykonywania innych operacji inicjowania).|Wywołanie implementacji klasy podstawowej przed kodu tak, aby klasa podstawowa ma możliwość tworzenia okna dialogowego i wszystkie formanty, przed podjęciem próby ich aktualizacji.|  
    |[Zastosuj](../atl/reference/ipropertypageimpl-class.md#apply)|Sprawdź poprawność ustawień właściwości i zaktualizować obiektów.|Nie istnieje potrzeba do wywołania implementacji klasy podstawowej, ponieważ go nie są wykonywane poza śledzenia wywołania.|  
    |[Dezaktywowanie](../atl/reference/ipropertypageimpl-class.md#deactivate)|Wyczyść elementy związane z okna.|Implementacja klasy podstawowej niszczy okno dialogowe reprezentujący stronę właściwości. Jeśli musisz wyczyścić przed okno dialogowe, należy dodać kodu przed wywołaniem klasy podstawowej.|  
  
 Przykładem implementacji strony właściwości, można wyświetlić [przykład: implementacja strony właściwości](../atl/example-implementing-a-property-page.md).  
  
> [!NOTE]
>  Jeśli chcesz kontrolki ActiveX hosta na stronie właściwości, należy zmienić pochodnym klasy generowane przez kreatora. Zastąp **cdialogimpl —\<CYourClass >** z **CAxDialogImpl\<CYourClass >** na liście klas podstawowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości](../atl/atl-com-property-pages.md)   
 [Przykładowe ATLPages](../visual-cpp-samples.md)

