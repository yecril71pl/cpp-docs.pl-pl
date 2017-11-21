---
title: "Implementacja strony właściwości (ALT) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 04f2871af749091e97ec1731650f998739995781
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="example-implementing-a-property-page"></a>Przykład: Implementacja strony właściwości
W tym przykładzie pokazano, jak zbudować stronę właściwości, która wyświetla (i umożliwia zmianę) właściwości [klasy dokumentów](../mfc/document-classes.md) interfejsu.  
  
 Przykład jest oparty na [próbki ATLPages](../visual-cpp-samples.md).  
  
 Aby ukończyć w tym przykładzie, obejmują:  
  
- [Dodawanie klasy strony właściwości ATL](#vcconusing_the_atl_object_wizard) za pomocą okna dialogowego Dodawanie klasy i Kreator strony właściwości ATL.  
  
- [Edytowanie zasobu okna dialogowego](#vcconediting_the_dialog_resource) przez dodanie nowych kontrolek interesujące właściwości **dokumentu** interfejsu.  
  
- [Dodawanie obsługi komunikatów](#vcconadding_message_handlers) do zachowania lokacji strony właściwości o zmiany wprowadzone przez użytkownika.  
  
-   Dodaj raporty `#import` instrukcje i jako element typedef w [celów](#vcconhousekeeping) sekcji.  
  
- [Zastąpienie IPropertyPageImpl::SetObjects](#vcconoverriding_ipropertypageimpl_setobjects) do sprawdzania poprawności obiektów przekazywany do strony właściwości.  
  
- [Zastąpienie IPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate) zainicjować stronę właściwości interfejsu.  
  
- [Zastąpienie IPropertyPageImpl::Apply](#vcconoverride_ipropertypageimpl_apply) można zaktualizować obiektu o najnowszych wartości właściwości.  
  
- [Wyświetl stronę właściwości](#vccontesting_the_property_page) przez utworzenie obiektu pomocnika proste.  
  
- [Tworzenie makra](#vcconcreating_a_macro) który Testuj stronę właściwości.  
  
##  <a name="vcconusing_the_atl_object_wizard"></a>Dodawanie klasy strony właściwości ATL  
 Najpierw utwórz nowy projekt ATL DLL serwera o nazwie `ATLPages7`. Teraz używać [Kreator strony właściwości ATL](../atl/reference/atl-property-page-wizard.md) do generowania strony właściwości. Nadaj stronę właściwości **krótką nazwę** z **DocProperties** następnie przełącz się do **ciągów** można ustawić właściwości strony dotyczące elementów, jak pokazano w poniższej tabeli.  
  
|Element|Wartość|  
|----------|-----------|  
|Tytuł|TextDocument|  
|Ciąg dokumentu|Właściwości TextDocument VCUE|  
|HelpFile|*\<Puste >*|  
  
 Wartości, które można ustawić na tej stronie kreatora zostanie zwrócony do kontenera strony właściwości, gdy wywołuje **IPropertyPage::GetPageInfo**. Co się dzieje na ciągi po zależy kontenera, ale zazwyczaj one będzie służyć do identyfikowania ze strony użytkownika. Tytuł zwykle pojawiają się na karcie powyżej strony i Doc String może być wyświetlany w pasku stanu lub etykietka narzędzia, (mimo że ramka standardowe właściwości nie są używane te parametry na wszystkich).  
  
> [!NOTE]
>  Ciągi, które można ustawić w tym miejscu są przechowywane jako zasoby ciągów w projekcie przez kreatora. Można łatwo edytować te ciągi za pomocą edytora zasobów, jeśli chcesz zmienić te informacje po wygenerowaniu kodu strony.  
  
 Kliknij przycisk **OK** aby Kreator generowania strony właściwości.  
  
##  <a name="vcconediting_the_dialog_resource"></a>Edytowanie zasobu okna dialogowego  
 Teraz, gdy został wygenerowany strony właściwości, należy dodać kilka formantów do zasobu okna dialogowego reprezentujący stronę. Dodaj pole edycji, kontrolę tekst statyczny oraz pole wyboru i ustawić ich identyfikatorów, jak pokazano poniżej:  
  
 ![Zasób okna dialogowego Edytowanie](../atl/media/ppgresourcelabeled.gif "ppgresourcelabeled")  
  
 Formanty będzie używany do wyświetlania nazwa pliku dokumentu i jego stan tylko do odczytu.  
  
> [!NOTE]
>  Zasób okna dialogowego nie zawiera przyciski poleceń lub ramki, ani nie ma wygląd z kartami, który może mieć miały. Funkcje te są dostarczane przez ramki strony właściwości, takie jak utworzyć przez wywołanie [OleCreatePropertyFrame](http://msdn.microsoft.com/library/windows/desktop/ms678437).  
  
##  <a name="vcconadding_message_handlers"></a>Dodawanie programów obsługi wiadomości  
 Kontroli w miejscu można dodać obsługi komunikatów, aby zaktualizować zanieczyszczeniu stan strony po zmianie wartości każdej kontrolki:  
  
 [!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]  
  
 Ten kod odpowiada zmiany wprowadzone do kontrolki edycji lub pole wyboru, wywołując [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty), które informują witryny strony, strony o zmianie. Zwykle lokacji strony będzie odpowiadać przez włączenie lub wyłączenie **Zastosuj** przycisk w ramce strony właściwości.  
  
> [!NOTE]
>  Własne stronach właściwości może być konieczne do śledzenia dokładnie właściwości, które zostały zmienione przez użytkownika tak, aby uniknąć aktualizowanie właściwości, które nie zostały zmienione. W tym przykładzie implementuje ten kod przez rejestrowanie informacji o oryginalnej wartości właściwości oraz porównanie ich z bieżących wartości z interfejsu użytkownika, gdy nadejdzie czas, aby zastosować zmiany.  
  
##  <a name="vcconhousekeeping"></a>Celów  
 Teraz dodaj kilka `#import` instrukcje DocProperties.h tak, że kompilator zna **dokumentu** interfejsu:  
  
 [!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]  
  
 Należy również dotyczą `IPropertyPageImpl` klasa podstawowa; Dodaj następujące `typedef` do **CDocProperties** klasy:  
  
 [!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]  
  
##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a>Zastępowanie IPropertyPageImpl::SetObjects  
 Pierwszy `IPropertyPageImpl` metody, której należy zastąpić [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects). Będzie w tym miejscu Dodaj kod, aby sprawdzić, czy tylko jeden obiekt został przekazany, i czy obsługuje **dokumentu** interfejs, który jest oczekiwany:  
  
 [!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]  
  
> [!NOTE]
>  Warto obsługuje tylko jeden obiekt na tej stronie, ponieważ umożliwi użytkownikowi określenie nazwy pliku obiektu — może istnieć tylko jeden plik, w jednym miejscu.  
  
##  <a name="vcconoverriding_ipropertypageimpl_activate"></a>Zastępowanie IPropertyPageImpl::Activate  
 Następnym krokiem jest zainicjować stronę właściwości z wartościami właściwości obiektu podstawowego po pierwszym utworzeniu strony.  
  
 W takim przypadku należy dodać następujące elementy członkowskie do klasy, ponieważ będą także używać początkowe wartości właściwości do porównania, gdy użytkownicy strony ich zmiany:  
  
 [!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]  
  
 Implementacja klasy podstawowej [Aktywuj](../atl/reference/ipropertypageimpl-class.md#activate) metoda jest odpowiedzialna za tworzenie okna dialogowego i jego formantów, aby można było przesłonić tę metodę i dodać własne inicjowanie po wywołaniu metody klasy podstawowej:  
  
 [!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]  
  
 Ten kod używa metody COM **dokumentu** interfejsu można pobrać właściwości, które Cię interesują. Następnie używa otoki Win32 API dostarczonych przez [cdialogimpl —](../atl/reference/cdialogimpl-class.md) i jej klas podstawowych, aby wyświetlić wartości właściwości dla użytkownika.  
  
##  <a name="vcconoverride_ipropertypageimpl_apply"></a>Zastępowanie IPropertyPageImpl::Apply  
 Kiedy użytkownik chce zastosować zmiany ich do obiektów, lokacja strony właściwości wywoła [Zastosuj](../atl/reference/ipropertypageimpl-class.md#apply) metody. Jest to miejsce na wykonanie kodu w odwrotnej **Aktywuj** — należy **Aktywuj** trwało wartości z obiektu i ich przypisany do kontrolki na stronie właściwości **Zastosuj** pobiera wartości z kontrolki na stronie właściwości i umieszcza je w obiekcie.  
  
 [!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]  
  
> [!NOTE]
>  Sprawdzanie względem [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) na początku tej implementacji jest początkowej wyboru, aby uniknąć niepotrzebnych aktualizacje obiektów, jeśli **Zastosuj** jest wywoływana więcej niż raz. Dostępne są także kontroli w odniesieniu do każdego z wartości właściwości, aby upewnić się, że tylko zmiany spowoduje wywołanie metody **dokumentu**.  
  
> [!NOTE]
> **Dokument** przedstawia **imię i nazwisko** jako właściwość tylko do odczytu. Aby zaktualizować nazwa pliku dokumentu na podstawie zmian wprowadzonych na stronie właściwości, należy użyć **zapisać** metodę, aby zapisać plik pod inną nazwą. W związku z tym nie ma kodu na stronie właściwości ograniczyć się do pobierania lub ustawiania właściwości.  
  
##  <a name="vccontesting_the_property_page"></a>Strona właściwości  
 Aby wyświetlić tę stronę, należy utworzyć obiekt pomocnika proste. Obiekt pomocnika zapewnia metodę, która upraszcza **OleCreatePropertyFrame** interfejsu API do wyświetlania pojedynczej strony podłączone do pojedynczego obiektu. Tego pomocnika projektowania, aby mogą być używane z języka Visual Basic.  
  
 Użyj [okno dialogowe Dodaj klasę](../ide/add-class-dialog-box.md) i [Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md) nową klasę do generowania i użytkowania `Helper` krótką nazwę. Po utworzeniu, Dodaj metodę, jak pokazano w poniższej tabeli.  
  
|Element|Wartość|  
|----------|-----------|  
|Nazwa metody|`ShowPage`|  
|Parametry|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|  
  
 `bstrCaption` Parametr ma podpis, który ma być wyświetlana jako tytuł okna dialogowego. `bstrID` Parametr jest ciąg reprezentujący CLSID lub ProgID strony właściwości, aby wyświetlić. `pUnk` Parametr zostanie `IUnknown` wskaźnika obiektu, którego właściwości zostaną skonfigurowane przez stronę właściwości.  
  
 Zaimplementuj metodę, jak pokazano poniżej:  
  
 [!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]  
  
##  <a name="vcconcreating_a_macro"></a>Tworzenie makra  
 Gdy projekt został utworzony, można sprawdzić stronę właściwości i obiekt pomocnika za pomocą prostego makra, które można tworzyć i uruchamiać w środowisku projektowym Visual Studio. To makro utworzy pomocnika obiekt, a następnie wywołaj jego **ShowPage** metodę przy użyciu identyfikatora ProgID **DocProperties** stronę właściwości i **IUnknown** wskaźnik dokumentu aktualnie aktywne w edytorze programu Visual Studio. Poniżej pokazano kod, który należy do tego makra:  
  
```  
Imports EnvDTE  
Imports System.Diagnostics  
 
Public Module AtlPages  
 
    Public Sub Test()  
    Dim Helper  
    Helper = CreateObject("ATLPages7.Helper.1")  
 
    On Error Resume Next  
    Helper.ShowPage(_ 
    ActiveDocument.Name,
    _ 
 "ATLPages7Lib.DocumentProperties.1",
    _ 
    DTE.ActiveDocument _)  
    End Sub  
 
End Module  
```  
  
 Po uruchomieniu tego makra, będą wyświetlane strony właściwości wyświetlane nazwy pliku i stanu tylko do odczytu dokumentu tekstowego obecnie aktywne. Stanu tylko do odczytu dokumentu przedstawiają tylko dane możliwość zapisu w dokumencie w środowisku programistycznym; nie wpływa na atrybut tylko do odczytu pliku na dysku.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości](../atl/atl-com-property-pages.md)   
 [Przykładowe ATLPages](../visual-cpp-samples.md)

