---
title: Używanie arkuszy właściwości w aplikacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74e63faf5b1cac5e0cb841a28fd59ecee47c9970
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383896"
---
# <a name="using-property-sheets-in-your-application"></a>Używanie arkuszy właściwości w aplikacji
Aby użyć arkusza właściwości w aplikacji, wykonaj następujące kroki:  
  
1.  Tworzenie zasobu okna dialogowego szablonu dla każdej strony właściwości. Należy pamiętać, że użytkownik może można przełączanie z jednej strony do innego, więc każdy układ strony jako spójnie, jak to możliwe.  
  
     Szablony okna dialogowego dla wszystkich stron, nie trzeba mieć taki sam rozmiar. Platformę używa rozmiar największego strony w celu określenia ilości wykorzystanego miejsca można przydzielić w arkuszu właściwości dla strony właściwości.  
  
     Podczas tworzenia zasobu szablonu okna dialogowego strony właściwości, należy określić następujące style w arkuszu właściwości okna dialogowego właściwości:  
  
    -   Ustaw **podpis** pole edycji na **ogólne** strony na tekst ma zostać wyświetlony na karcie tej strony.  
  
    -   Ustaw **styl** pola listy na **style** strony **podrzędnych**.  
  
    -   Ustaw **obramowania** pola listy na **style** strony **uproszczonym**.  
  
    -   Upewnij się, że **Titlebar** pole wyboru na **style** strony jest zaznaczone.  
  
    -   Upewnij się, że **wyłączone** pole wyboru na **więcej stylów** strony jest zaznaczone.  
  
2.  Utwórz [cpropertypage —](../mfc/reference/cpropertypage-class.md)-klasy odpowiadający każdego szablonu okna dialogowego strony właściwości. Zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md). Wybierz `CPropertyPage` jako klasy podstawowej.  
  
3.  Utwórz zmienne do przechowywania wartości dla tej strony właściwości elementu członkowskiego. Proces dodawania zmienne Członkowskie do strony właściwości jest dokładnie taka sama jak dodawanie zmienne Członkowskie do okna dialogowego, ponieważ strona właściwości to specjalne okno dialogowe. Aby uzyskać więcej informacji, zobacz [Definiowanie zmiennych Członkowskich dla formantów okna dialogowego](../windows/defining-member-variables-for-dialog-controls.md).  
  
4.  Utworzyć [cpropertysheet —](../mfc/reference/cpropertysheet-class.md) obiektu w kodzie źródłowym. Zwykle, utworzymy `CPropertySheet` obiekt obsługi dla polecenia, które wyświetla arkusz właściwości. Ten obiekt reprezentuje arkusz właściwości całego. Jeśli utworzysz modalny arkusz właściwości z [DoModal](../mfc/reference/cpropertysheet-class.md#domodal) funkcji, w ramach udostępnia trzy przyciski poleceń domyślnie: OK, Anuluj i Zastosuj. Platformę tworzy nie przyciski poleceń niemodalne arkusze właściwości utworzonych za pomocą [Utwórz](../mfc/reference/cpropertysheet-class.md#create) funkcji. Nie trzeba wyprowadzenia klasy z `CPropertySheet` chyba że chcesz dodać inne formanty (na przykład okno podglądu) albo wyświetlić niemodalnego arkusza właściwości. Ten krok jest niezbędne do niemodalne arkusze właściwości, ponieważ nie zawierają wszystkie formanty domyślne, które można zamknąć arkusz właściwości.  
  
5.  Dla każdej strony, które mają zostać dodane do arkusza właściwości wykonaj następujące czynności:  
  
    -   Utworzyć jeden obiekt dla każdego `CPropertyPage`-klasy, który został utworzony we wcześniejszej części tego procesu.  
  
    -   Wywołanie [CPropertySheet::AddPage](../mfc/reference/cpropertysheet-class.md#addpage) dla każdej strony.  
  
     Zazwyczaj obiekt, który tworzy `CPropertySheet` tworzy także `CPropertyPage` obiektów w tym kroku. Jednak w przypadku zastosowania `CPropertySheet`-klasy, można osadzić `CPropertyPage` obiekty w `CPropertySheet` obiekt i wywołanie `AddPage` dla każdej strony z `CPropertySheet`-konstruktora klasy pochodnej. `AddPage` dodaje `CPropertyPage` do listy stron arkusza właściwości obiektu, ale nie powoduje utworzenia okna dla tej strony. W związku z tym nie jest konieczne tworzenie okna arkusza właściwości do wywołania po upływie `AddPage`; można wywołać `AddPage` z arkusza właściwości konstruktora.  
  
     Domyślnie jeśli w arkuszu właściwości więcej kart niż mieści się w jednym wierszu arkusza właściwości kart będą umieszczane w wielu wierszach. Aby wyłączyć układania, należy wywołać [CPropertySheet::EnableStackedTabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs) z parametrem ustawioną **FALSE**. Należy wywołać `EnableStackedTabs` podczas tworzenia arkusza właściwości.  
  
6.  Wywołanie [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal) lub [Utwórz](../mfc/reference/cpropertysheet-class.md#create) do wyświetlenia arkusza właściwości. Wywołanie `DoModal` utworzyć arkusz właściwości jako modalne okno dialogowe. Wywołanie **Utwórz** utworzyć arkusz właściwości jako niemodalnego okna dialogowego.  
  
7.  Wymiany danych między strony właściwości i właściciel arkusza właściwości. Wyjaśnienie jest zawarte w artykule [wymiana danych](../mfc/exchanging-data.md).  
  
 Na przykład sposobu używania arkuszy właściwości Zobacz przykład ogólne MFC [PROPDLG](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Arkusze właściwości](../mfc/property-sheets-mfc.md)

