---
title: "Formanty MFC ActiveX: Używanie powiązania danych w formancie ActiveX | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e8416e7a176c00e5fb3067d1c1cfa447445dab54
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>Kontrolki ActiveX MFC: używanie powiązania danych w kontrolce ActiveX
Jest jednym z bardziej zaawansowanych zastosowań kontrolki ActiveX powiązania danych, dzięki czemu właściwości formantu można powiązać z określonego pola w bazie danych. Gdy użytkownik modyfikuje danych w tej właściwości powiązanej, formantu powiadamia bazy danych i żądań, że można zaktualizować pola rekordu. Bazy danych jest następnie powiadamia formantu powodzenie lub Niepowodzenie żądania.  
  
 W tym artykule omówiono po stronie kontrolki zadania. Implementowanie interakcji powiązania danych z bazy danych jest odpowiedzialny za formantu kontenera. Jak zarządzać interakcje bazy danych w sieci kontenera wykracza poza zakres tej dokumentacji. Jak przygotować kontroli dla powiązania danych znajduje się w dalszej części tego artykułu.  
  
 ![Diagram koncepcyjny przedstawiający danych &#45; powiązanej kontrolki](../mfc/media/vc374v1.gif "vc374v1")  
Diagram koncepcyjny formantu powiązanego z danymi  
  
 `COleControl` Klasa udostępnia dwie funkcje Członkowskie składające dane powiązanie łatwy do zaimplementowania. Pierwsza funkcja [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit), jest używany do żądania uprawnień do zmiany wartości właściwości. [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged), druga funkcja jest wywoływana po wartości właściwości została zmieniona.  
  
 W tym artykule omówiono następujące tematy:  
  
-   [Tworzenie powiązania właściwości standardowych](#vchowcreatingbindablestockproperty)  
  
-   [Tworzenie metody powiązania Get/Set](#vchowcreatingbindablegetsetmethod)  
  
##  <a name="vchowcreatingbindablestockproperty"></a>Tworzenie powiązania właściwości standardowych  
 Możliwe jest tworzenie powiązanych z danymi właściwości podstawowych, chociaż jest bardziej prawdopodobne, że można [powiązania get/set, Metoda](#vchowcreatingbindablegetsetmethod).  
  
> [!NOTE]
>  Właściwości podstawowe ma **powiązania** i **requestedit —** atrybuty domyślnie.  
  
#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Aby dodać właściwości standardowych możliwej do wiązania za pomocą Kreatora dodawania właściwości  
  
1.  Rozpocznij projekt za pomocą [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md).  
  
2.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu.  
  
     Spowoduje to otwarcie menu skrótów.  
  
3.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.  
  
4.  Wybierz jeden z wpisów z **nazwa właściwości** listy rozwijanej. Na przykład można wybrać **tekstu**.  
  
     Ponieważ **tekst** jest właściwością standardowych **powiązania** i **requestedit —** atrybuty są już zaznaczone.  
  
5.  Wybierz następujące pola wyboru z **atrybuty IDL** kartę: **displaybind —** i **defaultbind —** dodać atrybuty do definicji właściwości do projektu. Plik IDL. Te atrybuty upewnij formantu widoczne dla użytkowników oraz właściwości standardowych domyślnej właściwości możliwej do wiązania.  
  
 W tym momencie formantu mogą wyświetlać dane ze źródła danych, ale użytkownik nie będzie mógł zaktualizować pola danych. Jeśli chcesz również mieć możliwość aktualizowania danych, zmień formantu `OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) funkcję, która ma wyglądać w następujący sposób:  
  
 [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
 Teraz można utworzyć projektu, który zarejestruje formantu. Po wstawieniu formantu w oknie dialogowym **pola danych** i **źródła danych** zostaną dodane właściwości i można teraz wybrać źródło danych i pola do wyświetlenia w formancie.  
  
##  <a name="vchowcreatingbindablegetsetmethod"></a>Tworzenie metody powiązania Get/Set  
 Oprócz powiązane z danymi pobierania/ustawiania metody, można również utworzyć [można powiązać właściwości standardowych](#vchowcreatingbindablestockproperty).  
  
> [!NOTE]
>  W tej procedurze przyjęto założenie, że masz formantu ActiveX projektu tego podklasy kontrolki okna.  
  
#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Aby dodać metody pobierania/ustawiania możliwej do wiązania za pomocą Kreatora dodawania właściwości  
  
1.  Załaduj projekt z kontroli.  
  
2.  Na **ustawienia kontroli** Wybierz klasy okna dla kontrolki do podklasy. Na przykład można do podklasy kontrolki EDYCJI.  
  
3.  Załaduj projekt z kontroli.  
  
4.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu.  
  
     Spowoduje to otwarcie menu skrótów.  
  
5.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.  
  
6.  Wpisz nazwę właściwości w **nazwa właściwości** pola. Użyj `MyProp` w tym przykładzie.  
  
7.  Wybierz typ danych z **typ właściwości** pole listy rozwijanej. Użyj **krótki** w tym przykładzie.  
  
8.  Aby uzyskać **typ implementacji**, kliknij przycisk **metod Get/Set**.  
  
9. Wybierz następujące pola wyboru na karcie Atrybuty IDL: **powiązania**, **requestedit —**, **displaybind —**, i **defaultbind —** do dodania atrybuty do definicji właściwości do projektu. Plik IDL. Te atrybuty upewnij formantu widoczne dla użytkowników oraz właściwości standardowych domyślnej właściwości możliwej do wiązania.  
  
10. Kliknij przycisk **Zakończ**.  
  
11. Modyfikowanie treści `SetMyProp` funkcjonować tak, aby zawierał następujący kod:  
  
     [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]  
  
12. Parametr przekazany do `BoundPropertyChanged` i `BoundPropertyRequestEdit` funkcji jest identyfikator dispid właściwości, która jest parametr przekazany do atrybutu id() dla właściwości w. Plik IDL.  
  
13. Modyfikowanie [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) funkcjonować tak, aby zawierał następujący kod:  
  
     [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
14. Modyfikowanie `OnDraw` funkcjonować tak, aby zawierał następujący kod:  
  
     [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]  
  
15. Do publicznego sekcji pliku nagłówka pliku nagłówka klasy formantu Dodaj następujące definicje (konstruktorów) dla zmiennych Członkowskich:  
  
     [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]  
  
16. Wprowadzić następujący wiersz w ostatnim wierszu `DoPropExchange` funkcji:  
  
     [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]  
  
17. Modyfikowanie `OnResetState` funkcjonować tak, aby zawierał następujący kod:  
  
     [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]  
  
18. Modyfikowanie `GetMyProp` funkcjonować tak, aby zawierał następujący kod:  
  
     [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]  
  
 Teraz można utworzyć projektu, który zarejestruje formantu. Po wstawieniu formantu w oknie dialogowym **pola danych** i **źródła danych** zostaną dodane właściwości i można teraz wybrać źródło danych i pola do wyświetlenia w formancie.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   

