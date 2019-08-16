---
title: Implementowanie strony właściwości (ATL)
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
ms.openlocfilehash: 68b4aaef06e40a8ec7b00f9ba744d83ce3388da2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492383"
---
# <a name="example-implementing-a-property-page"></a>Przykład: Implementowanie strony właściwości

::: moniker range="vs-2019"

Kreator strony właściwości ATL nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Ten przykład pokazuje, jak utworzyć stronę właściwości, która wyświetla (i pozwala zmieniać) właściwości interfejsu [klasy dokumentu](../mfc/document-classes.md) .

Przykład jest oparty na przykładu [ATLPages](../overview/visual-cpp-samples.md).

Aby ukończyć ten przykład, można:

- [Dodaj klasę strony właściwości ATL](#vcconusing_the_atl_object_wizard) przy użyciu okna dialogowego Dodaj klasę i Kreatora strony właściwości ATL.

- [Edytuj zasób okna dialogowego](#vcconediting_the_dialog_resource) , dodając nowe kontrolki dla interesujących właściwości `Document` interfejsu.

- [Dodaj programy obsługi komunikatów](#vcconadding_message_handlers) , aby zachować informacje o zmianach wprowadzonych przez użytkownika w witrynie strony właściwości.

- Dodaj instrukcje i element typedef w sekcji [dla gospodarstw domowych.](#vcconhousekeeping) `#import`

- [Przesłoń IPropertyPageImpl::](#vcconoverriding_ipropertypageimpl_setobjects) SetObjects, aby sprawdzić poprawność obiektów, które są przesyłane do strony właściwości.

- [Przesłoń IPropertyPageImpl:: Activate](#vcconoverriding_ipropertypageimpl_activate) , aby zainicjować interfejs strony właściwości.

- [Przesłoń IPropertyPageImpl:: Apply](#vcconoverride_ipropertypageimpl_apply) , aby zaktualizować Obiekt przy użyciu wartości najnowszych właściwości.

- [Wyświetl stronę właściwości](#vccontesting_the_property_page) , tworząc prosty obiekt pomocnika.

- [Utwórz makro](#vcconcreating_a_macro) , które będzie przetestować stronę właściwości.

##  <a name="vcconusing_the_atl_object_wizard"></a>Dodawanie klasy strony właściwości ATL

Najpierw utwórz nowy projekt ATL dla serwera DLL o nazwie `ATLPages7`. Teraz można użyć [Kreatora strony właściwości ATL](../atl/reference/atl-property-page-wizard.md) do wygenerowania strony właściwości. Nadaj stronie właściwości krótką **nazwę** **DocProperties** , a następnie przejdź na stronę **ciągów** , aby ustawić elementy specyficzne dla strony właściwości, jak pokazano w poniższej tabeli.

|Element|Wartość|
|----------|-----------|
|Tytuł|TextDocument|
|Ciąg doc|VCUE właściwości dokumentu|
|HelpFile|*\<puste >*|

Wartości ustawione na tej stronie kreatora zostaną zwrócone do kontenera strony właściwości podczas wywoływania `IPropertyPage::GetPageInfo`. Co się dzieje z ciągami, które są zależne od kontenera, ale zazwyczaj są one używane do identyfikowania strony użytkownika. Tytuł będzie zazwyczaj wyświetlany na karcie nad stroną, a ciąg dokumentu może być wyświetlany na pasku stanu lub w etykietce narzędzia (mimo że standardowa ramka właściwości nie używa tego ciągu w ogóle).

> [!NOTE]
>  Określone w tym miejscu ciągi są przechowywane jako zasoby ciągów w projekcie przez kreatora. Można łatwo edytować te ciągi przy użyciu edytora zasobów, jeśli trzeba zmienić te informacje po wygenerowaniu kodu strony.

Kliknij przycisk **OK** , aby Kreator wygenerował stronę właściwości.

##  <a name="vcconediting_the_dialog_resource"></a>Edytowanie zasobu okna dialogowego

Po wygenerowaniu strony właściwości należy dodać kilka kontrolek do zasobów okna dialogowego reprezentujących Twoją stronę. Dodaj pole edycji, statyczny formant tekstowy i pole wyboru i ustaw ich identyfikatory, jak pokazano poniżej:

![Edytowanie zasobu okna dialogowego](../atl/media/ppgresourcelabeled.gif "Edytowanie zasobu okna dialogowego")

Te kontrolki będą używane do wyświetlania nazwy pliku dokumentu i jego stanu tylko do odczytu.

> [!NOTE]
>  Zasób okna dialogowego nie zawiera ramki lub przycisków poleceń ani nie ma zamierzonych wyszukiwań z kartami. Te funkcje są udostępniane przez ramkę strony właściwości, taką jak ta utworzona przez wywołanie [OleCreatePropertyFrame](/windows/win32/api/olectl/nf-olectl-olecreatepropertyframe).

##  <a name="vcconadding_message_handlers"></a>Dodawanie programów obsługi komunikatów

Przy użyciu kontrolek, można dodać programy obsługi komunikatów, aby zaktualizować stan zanieczyszczony strony po zmianie wartości którejkolwiek z kontrolek:

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

Ten kod reaguje na zmiany wprowadzane do kontrolki edycji lub pola wyboru przez wywołanie [IPropertyPageImpl::](../atl/reference/ipropertypageimpl-class.md#setdirty)SetDirty, który informuje witrynę strony, że strona została zmieniona. Zwykle witryna strony reaguje, włączając lub wyłączając przycisk **Zastosuj** w ramce strony właściwości.

> [!NOTE]
>  Na własnych stronach właściwości może być konieczne dokładne śledzenie właściwości, które zostały zmodyfikowane przez użytkownika, aby można było uniknąć aktualizowania właściwości, które nie zostały zmienione. Ten przykład implementuje ten kod przez śledzenie oryginalnych wartości właściwości i porównywanie ich z bieżącymi wartościami z interfejsu użytkownika, gdy jest czas na zastosowanie zmian.

##  <a name="vcconhousekeeping"></a>Dla gospodarstw domowych

Teraz Dodaj kilka `#import` instrukcji do DocProperties. h, aby kompilator wie `Document` o interfejsie:

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

Należy również zapoznać się z `IPropertyPageImpl` klasą bazową; Dodaj następujący `CDocProperties` element typedef do klasy:

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a>Zastępowanie IPropertyPageImpl:: SetObjects

Pierwszą `IPropertyPageImpl` metodą przesłonięcia jest SetObjects [](../atl/reference/ipropertypageimpl-class.md#setobjects). W tym miejscu dodasz kod do sprawdzenia, czy został przekazano tylko jeden obiekt i że obsługuje `Document` on oczekiwany interfejs:

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
>  Warto na tej stronie obsługiwać tylko jeden obiekt, ponieważ zezwolisz użytkownikowi na ustawienie nazwy pliku dla tego obiektu — w jednej lokalizacji może istnieć tylko jeden plik.

##  <a name="vcconoverriding_ipropertypageimpl_activate"></a>Zastępowanie IPropertyPageImpl:: Activate

Następnym krokiem jest zainicjowanie strony właściwości z wartościami właściwości obiektu źródłowego, gdy strona jest tworzona po raz pierwszy.

W takim przypadku należy dodać następujących członków do klasy, ponieważ będziesz również używać początkowych wartości właściwości do porównania, gdy użytkownicy strony zastosują zmiany:

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

Implementacja klasy bazowej metody [Activate](../atl/reference/ipropertypageimpl-class.md#activate) jest odpowiedzialna za utworzenie okna dialogowego i jego kontrolek, aby można było zastąpić tę metodę i dodać własną inicjalizację po wywołaniu klasy bazowej:

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

Ten kod korzysta z metod `Document` com interfejsu w celu uzyskania interesujących Cię właściwości. Następnie używa otok Win32 API dostarczonych przez [CDialogImpl](../atl/reference/cdialogimpl-class.md) i jej klasy podstawowe do wyświetlania wartości właściwości dla użytkownika.

##  <a name="vcconoverride_ipropertypageimpl_apply"></a>Zastępowanie IPropertyPageImpl:: Apply

Gdy użytkownicy chcą zastosować zmiany do obiektów, witryna strony właściwości wywoła metodę [apply](../atl/reference/ipropertypageimpl-class.md#apply) . Jest to miejsce, w którym należy wykonać odwrotność kodu `Activate` `Activate` — w wyniku których wartości z obiektu zostały wypchnięte do kontrolek na stronie właściwości, `Apply` pobierają wartości z kontrolek na stronie właściwości i wypychają je do Stream.

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
>  Sprawdzenie pod kątem [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) na początku tej implementacji jest początkowym sprawdzeniem, aby uniknąć niepotrzebnych aktualizacji obiektów, `Apply` jeśli jest wywoływana więcej niż raz. Sprawdzane są także dla każdej wartości właściwości, aby upewnić się, że tylko zmiany spowodują wywołanie `Document`metody.

> [!NOTE]
> `Document`uwidacznia `FullName` jako właściwość tylko do odczytu. Aby zaktualizować nazwę pliku dokumentu na podstawie zmian wprowadzonych na stronie właściwości, musisz użyć `Save` metody, aby zapisać plik z inną nazwą. W ten sposób kod na stronie właściwości nie musi ograniczać się do pobierania lub ustawiania właściwości.

##  <a name="vccontesting_the_property_page"></a>Wyświetlanie strony właściwości

Aby wyświetlić tę stronę, należy utworzyć prosty obiekt pomocnika. Obiekt pomocnika będzie dostarczać metodę, która upraszcza `OleCreatePropertyFrame` interfejs API do wyświetlania pojedynczej strony połączonej z pojedynczym obiektem. Ten pomocnik zostanie zaprojektowany w taki sposób, aby można go było używać z Visual Basic.

Za pomocą [okna dialogowego Dodaj klasę](../ide/add-class-dialog-box.md) i [Kreatora prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md) można wygenerować nową klasę i użyć `Helper` jej jako krótkiej nazwy. Po utworzeniu należy dodać metodę, jak pokazano w poniższej tabeli.

|Element|Wartość|
|----------|-----------|
|Nazwa metody|`ShowPage`|
|Parametry|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

Parametr *bstrCaption* jest podpisem, który będzie wyświetlany jako tytuł okna dialogowego. Parametr *bstrID* jest ciągiem REPREZENTUJĄCYM identyfikator CLSID lub ProgID strony właściwości do wyświetlenia. Punkt`IUnknown` jest wskaźnikiem obiektu, którego właściwości zostaną skonfigurowane przez stronę właściwości.

Zaimplementuj metodę, jak pokazano poniżej:

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

##  <a name="vcconcreating_a_macro"></a>Tworzenie makra

Po skompilowaniu projektu można przetestować stronę właściwości i obiekt pomocnika przy użyciu prostego makra, które można utworzyć i uruchomić w środowisku deweloperskim programu Visual Studio. To makro spowoduje utworzenie obiektu pomocnika, a następnie wywołanie `ShowPage` jego metody przy użyciu identyfikatora ProgID strony `IUnknown` właściwości **DocProperties** oraz wskaźnika dokumentu aktualnie aktywnego w edytorze programu Visual Studio. Poniżej przedstawiono kod, który jest wymagany dla tego makra:

```vb
Imports EnvDTE
Imports System.Diagnostics

Public Module AtlPages

Public Sub Test()
    Dim Helper
    Helper = CreateObject("ATLPages7.Helper.1")

    On Error Resume Next
    Helper.ShowPage( ActiveDocument.Name, "ATLPages7Lib.DocumentProperties.1", DTE.ActiveDocument )
End Sub

End Module
```

Po uruchomieniu tego makra zostanie wyświetlona strona właściwości zawierająca informacje o nazwie pliku i stanie tylko do odczytu aktualnie aktywnego dokumentu tekstowego. Stan tylko do odczytu odzwierciedla możliwość zapisu w dokumencie w środowisku programistycznym. nie ma to wpływu na atrybut tylko do odczytu pliku na dysku.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Strony właściwości](../atl/atl-com-property-pages.md)<br/>
[Przykład ATLPages](../overview/visual-cpp-samples.md)
