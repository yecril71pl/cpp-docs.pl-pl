---
title: 'Kontrolki ActiveX MFC: Używanie powiązania danych w kontrolce ActiveX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 12/09/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1170d312fa6416ba051574022ace21795bf2567f
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535213"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>Kontrolki ActiveX MFC: używanie powiązania danych w kontrolce ActiveX
Jest jednym z zastosowań bardziej zaawansowanych kontrolek ActiveX powiązania danych, co pozwala z właściwością kontrolki, które można powiązać z konkretnym polem w bazie danych. Gdy użytkownik zmodyfikuje danych w tej właściwości powiązanej, formant powiadamia bazy danych i żądaniami zaktualizowania pola rekordu. Baza danych następnie powiadamia użytkownika, formantu powodzenie lub Niepowodzenie żądania.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które wypierają ActiveX zobacz [formantów ActiveX](activex-controls.md).  
  
 W tym artykule opisano strony kontroli zadania. Implementowanie danych wiązaniu interakcji z bazą danych jest obowiązkiem kontener formantu. W jaki sposób zarządzasz interakcji bazy danych w kontenerze wykracza poza zakres tej dokumentacji. Jak przygotować kontroli dla powiązania danych zostało wyjaśnione w dalszej części tego artykułu.  
  
 ![Diagram koncepcyjny danych&#45;formant powiązany z](../mfc/media/vc374v1.gif "vc374v1")  
Diagram pojęciowy kontrolki powiązania danych  
  
 `COleControl` Klasy zapewnia dwie funkcje Członkowskie, wchodzące w łatwy do zaimplementowania powiązanie danych. Pierwsza funkcja [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit), jest używany do zażądania uprawnień do zmiany wartości właściwości. [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged), druga funkcja jest wywoływana po wartość właściwości została zmieniona.  
  
 W tym artykule omówiono następujące tematy:  
  
-   [Tworzenie możliwej do wiązania właściwości standardowych](#vchowcreatingbindablestockproperty)  
  
-   [Tworzenie metody Get/Set możliwej do wiązania](#vchowcreatingbindablegetsetmethod)  
  
##  <a name="vchowcreatingbindablestockproperty"></a> Tworzenie możliwej do wiązania właściwości standardowych  
 Możliwe jest tworzenie powiązanych z danymi właściwości podstawowych, mimo że jest bardziej prawdopodobne, że można [metoda może być powiązana get/set](#vchowcreatingbindablegetsetmethod).  
  
> [!NOTE]
>  Właściwości podstawowe mają `bindable` i `requestedit` atrybuty domyślnie.  
  
#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>Aby dodać właściwości podstawowe możliwej do wiązania za pomocą Kreatora dodawania właściwości  
  
1.  Rozpocznij projekt przy użyciu [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md).  
  
2.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki.  
  
     Spowoduje to otwarcie menu skrótów.  
  
3.  W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj właściwość**.  
  
4.  Wybierz jeden z wpisów z **nazwa właściwości** listy rozwijanej. Na przykład, możesz wybrać **tekstu**.  
  
     Ponieważ **tekstu** jest właściwością podstawowe **możliwej do wiązania** i **requestedit —** atrybuty już są sprawdzane.  
  
5.  Wybierz następujące pola wyboru z **atrybuty IDL** kartę: **displaybind —** i **defaultbind —** można dodawać atrybuty do definicji właściwości w projekcie. Plik IDL. Te atrybuty upewnij kontrolki widoczne dla użytkowników oraz właściwości podstawowych domyślnej właściwości możliwej do wiązania.  
  
 W tym momencie kontroli nad mogą wyświetlać dane ze źródła danych, ale użytkownik nie będzie można zaktualizować pola danych. Jeśli chcesz, aby kontrolka również mieć możliwość aktualizowania danych, zmień `OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) funkcji wyglądać następująco:  
  
 [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
 Można teraz tworzyć projektu, które będą rejestrować się kontrolka. Po wstawieniu kontrolki w oknie dialogowym **pola danych** i **źródła danych** będzie dodawać właściwości i można teraz wybrać źródło danych i pola do wyświetlenia w kontrolce.  
  
##  <a name="vchowcreatingbindablegetsetmethod"></a> Tworzenie metody Get/Set możliwej do wiązania  
 Oprócz danych powiązanych z metodą get/set, można również utworzyć [możliwej do wiązania właściwości podstawowych](#vchowcreatingbindablestockproperty).  
  
> [!NOTE]
>  Ta procedura zakłada, że masz formant ActiveX projektu podklasy kontrolki Windows.  
  
#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>Aby dodać metodę get/set możliwej do wiązania za pomocą Kreatora dodawania właściwości  
  
1.  Załaduj projekt formantu.  
  
2.  Na **ustawienia kontroli** wybierz klasę okna dla formantu, który ma podklasę. Na przykład można do podklasy kontrolki EDYCJI.  
  
3.  Załaduj projekt formantu.  
  
4.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki.  
  
     Spowoduje to otwarcie menu skrótów.  
  
5.  W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj właściwość**.  
  
6.  Wpisz nazwę właściwości w **nazwa właściwości** pola. Użyj `MyProp` w tym przykładzie.  
  
7.  Wybierz typ danych z **typ właściwości** pole listy rozwijanej. Użyj **krótki** w tym przykładzie.  
  
8.  Aby uzyskać **typ implementacji**, kliknij przycisk **metod Get/Set**.  
  
9. Wybierz następujące pola wyboru na karcie Atrybuty IDL: **możliwej do wiązania**, **requestedit —**, **displaybind —**, i **defaultbind —** do dodania atrybuty do definicji właściwości w projekcie. Plik IDL. Te atrybuty upewnij kontrolki widoczne dla użytkowników oraz właściwości podstawowych domyślnej właściwości możliwej do wiązania.  
  
10. Kliknij przycisk **Zakończ**.  
  
11. Modyfikowanie treści `SetMyProp` funkcji tak, aby zawierała następujący kod:  
  
     [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]  
  
12. Parametr przekazany do `BoundPropertyChanged` i `BoundPropertyRequestEdit` functions to identyfikator dispid, właściwości, która jest parametr przekazywany do atrybutu id() dla właściwości w. Plik IDL.  
  
13. Modyfikowanie [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) działać, dlatego zawiera następujący kod:  
  
     [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
14. Modyfikowanie `OnDraw` funkcji tak, aby zawierała następujący kod:  
  
     [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]  
  
15. Do sekcji publicznej pliku nagłówka pliku nagłówkowego klasy kontrolki Dodaj następujące definicje zmiennych składowych (konstruktory):  
  
     [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]  
  
16. Wprowadź następujący wiersz w ostatnim wierszu `DoPropExchange` funkcji:  
  
     [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]  
  
17. Modyfikowanie `OnResetState` funkcji tak, aby zawierała następujący kod:  
  
     [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]  
  
18. Modyfikowanie `GetMyProp` funkcji tak, aby zawierała następujący kod:  
  
     [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]  
  
 Można teraz tworzyć projektu, które będą rejestrować się kontrolka. Po wstawieniu kontrolki w oknie dialogowym **pola danych** i **źródła danych** będzie dodawać właściwości i można teraz wybrać źródło danych i pola do wyświetlenia w kontrolce.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   

