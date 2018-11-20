---
title: Implementowanie strony właściwości (ATL)
ms.date: 11/19/2018
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
ms.openlocfilehash: a76a0f49e8b0ec7458b781785cd5030d2c523f0b
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176474"
---
# <a name="example-implementing-a-property-page"></a>Przykład: Implementowanie strony właściwości

W tym przykładzie pokazano, jak strona właściwości, która wyświetla (i pozwala na zmianę) właściwości budowania [klasy dokumentów](../mfc/document-classes.md) interfejsu.

Przykład jest oparty na [przykładowe ATLPages](../visual-cpp-samples.md).

Aby ukończyć w tym przykładzie, wykonasz następujące czynności:

- [Dodawanie klasy strony właściwości ATL](#vcconusing_the_atl_object_wizard) przy użyciu okna dialogowego Dodaj klasę i Kreator strony właściwości ATL.

- [Edytowanie zasobu okna dialogowego](#vcconediting_the_dialog_resource) przez dodanie nowych kontrolek, interesujące właściwości `Document` interfejsu.

- [Dodawanie obsługi komunikatów](#vcconadding_message_handlers) zapewnienie lokacji strony właściwości poinformowany o zmiany wprowadzone przez użytkownika.

- Dodaj `#import` oświadczeń i typedef w [celów](#vcconhousekeeping) sekcji.

- [Zastąp IPropertyPageImpl::SetObjects](#vcconoverriding_ipropertypageimpl_setobjects) do sprawdzania poprawności obiektów przekazywany do strony właściwości.

- [Zastąp IPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate) zainicjować interfejsu na stronie właściwości.

- [Zastąp IPropertyPageImpl::Apply](#vcconoverride_ipropertypageimpl_apply) aktualizacji obiektu za pomocą najnowszej wartości właściwości.

- [Wyświetl stronę właściwości](#vccontesting_the_property_page) przez utworzenie obiektu pomocnika proste.

- [Tworzenie makra](#vcconcreating_a_macro) przetestujesz, na stronie właściwości.

##  <a name="vcconusing_the_atl_object_wizard"></a> Dodawanie klasy strony właściwości ATL

Najpierw utwórz nowy projekt ATL DLL serwera o nazwie `ATLPages7`. Teraz za pomocą [Kreator strony właściwości ATL](../atl/reference/atl-property-page-wizard.md) do generowania strony właściwości. Nadaj na stronie właściwości **krótką nazwę** z **DocProperties** następnie przełącz się do **ciągi** strony, aby ustawić właściwości strony specyficzne dla elementów, jak pokazano w poniższej tabeli.

|Element|Wartość|
|----------|-----------|
|Tytuł|TextDocument|
|Ciąg dokumentu|VCUE textdocument — właściwości|
|HelpFile —|*\<pusty >*|

Wartości, które można ustawić na tej stronie kreatora zostanie przywrócony do kontener strony właściwości, gdy wywołuje `IPropertyPage::GetPageInfo`. Co się stanie do ciągów, po zależy w kontenerze, ale zazwyczaj są będzie służyć do identyfikowania strony do użytkownika. Tytuł pojawi się zwykle w karcie powyżej strony i ciąg dokumentu może być wyświetlany w pasku stanu lub etykietki narzędzia (mimo że ramka właściwości standardowe nie korzysta z tego ciągu w ogóle).

> [!NOTE]
>  Ciągi, które można ustawić w tym miejscu są przechowywane jako zasoby w postaci ciągów w projekcie przez kreatora. Można łatwo edytować tych ciągów za pomocą edytora zasobów, jeśli zajdzie potrzeba zmiany te informacje po wygenerowaniu kodu dla strony.

Kliknij przycisk **OK** aby Kreator Generuj stronę właściwości.

##  <a name="vcconediting_the_dialog_resource"></a> Edytowanie zasobu okna dialogowego

Teraz, gdy Twoja strona właściwości został wygenerowany, należy dodać kilka formantów do okna dialogowego reprezentujący stronę sieci. Dodaj pole edycji, formant statyczny tekst i pola wyboru i ustaw ich identyfikatory, jak pokazano poniżej:

![Edytowanie zasobu okna dialogowego](../atl/media/ppgresourcelabeled.gif "edycji zasobu okna dialogowego")

Te kontrolki będzie służyć do wyświetlania nazwa pliku dokumentu oraz jego statusu tylko do odczytu.

> [!NOTE]
>  Zasobu okna dialogowego nie zawiera ramki lub polecenia przycisków, ani nie ma wygląd z kartami, oczekiwany przez Ciebie może mieć. Te funkcje są udostępniane przez ramka strony właściwości, takiego jak utworzonych przez wywoływanie [OleCreatePropertyFrame](/windows/desktop/api/olectl/nf-olectl-olecreatepropertyframe).

##  <a name="vcconadding_message_handlers"></a> Dodawanie programów obsługi wiadomości

Za pomocą kontrolek w miejscu można dodać procedury obsługi komunikatów do aktualizowania stanu zanieczyszczone strony, po zmianie wartości albo kontrolki:

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

Ten kod reaguje na zmiany wprowadzone do kontrolki edycji lub okienka do zaznaczenia, wywołując [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty), która informuje witryny strony, który zmienił się strony. Zazwyczaj witryna strony będzie odpowiadać przez włączenie lub wyłączenie **Zastosuj** przycisk na ramce strony właściwości.

> [!NOTE]
>  Na własnych stronach właściwości może być konieczne do śledzenia dokładnie właściwości, które zostały zmienione przez użytkownika tak, aby uniknąć, aktualizowanie właściwości, które nie zostały zmienione. W tym przykładzie implementuje ten kod, rejestrowanie informacji o oryginalnej wartości właściwości i porównywanie ich bieżącymi wartościami w interfejsie użytkownika, gdy nadejdzie czas, aby zastosować zmiany.

##  <a name="vcconhousekeeping"></a> Celów

Teraz dodaj kilka `#import` instrukcje DocProperties.h tak, aby kompilator wie o `Document` interfejsu:

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

Należy także odwoływać się do `IPropertyPageImpl` klasy bazowej; Dodaj następujący kod **typedef** do `CDocProperties` klasy:

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a> Zastępowanie IPropertyPageImpl::SetObjects

Pierwszy `IPropertyPageImpl` jest metoda, który trzeba zastąpić [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects). W tym miejscu należy dodać kod, aby sprawdzić, czy jeden obiekt został przekazany i że obsługuje ona `Document` interfejs, który jest oczekiwany:

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
>  Dobrym pomysłem będzie obsługuje tylko jeden obiekt na tej stronie, ponieważ pozwoli użytkownikowi na ustawianie nazwę pliku obiektu — tylko jeden plik może znajdować się w dowolnym miejscu jeden.

##  <a name="vcconoverriding_ipropertypageimpl_activate"></a> Zastępowanie IPropertyPageImpl::Activate

Następnym krokiem jest do zainicjowania strony właściwości z wartościami właściwości obiektu bazowego, przy pierwszym utworzeniu strony.

W takim przypadku należy dodać następujące elementy członkowskie do klasy, ponieważ skorzystasz także początkowe wartości właściwości dla porównania użytkownicy strony zastosowanie zmian:

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

Implementacja klasy bazowej [Aktywuj](../atl/reference/ipropertypageimpl-class.md#activate) metoda jest odpowiedzialna za tworzenie okna dialogowego i jego formantów, aby można było przesłonić tę metodę i dodaj własne inicjowanie po wywołaniu klasy bazowej:

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

Ten kod używa metody COM `Document` interfejsu można pobrać właściwości, które interesują Cię. Następnie używa otoki Win32 API dostarczonych przez [CDialogImpl](../atl/reference/cdialogimpl-class.md) i jej klasy bazowe, aby wyświetlić wartości właściwości dla użytkownika.

##  <a name="vcconoverride_ipropertypageimpl_apply"></a> Zastępowanie IPropertyPageImpl::Apply

Gdy użytkownik chce zastosować zmiany do obiektów, wywoła lokacji strony właściwości [Zastosuj](../atl/reference/ipropertypageimpl-class.md#apply) metody. Jest to miejsce, w odwrotnej kolejności kodu w `Activate` — dlatego `Activate` trwało wartości z obiektu i wypchnięcie ich do formantów na stronie właściwości `Apply` przyjmuje wartości od formantów na stronie właściwości, a następnie wypycha je do obiekt.

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
>  Sprawdzenie [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) na początku tej implementacji jest początkowa wyboru, aby uniknąć niepotrzebnych aktualizacje obiektów, jeśli `Apply` jest wywoływana więcej niż jeden raz. Dostępne są także kontroli w odniesieniu do każdego z wartości właściwości, aby upewnić się, że tylko zmiany powodują wywołanie metody `Document`.

> [!NOTE]
> `Document` udostępnia `FullName` jako właściwość tylko do odczytu. Aby zaktualizować nazwę pliku dokument, w oparciu o zmiany wprowadzone na stronie właściwości, trzeba użyć `Save` metodę, aby zapisać plik pod inną nazwą. W efekcie kod na stronie właściwości nie trzeba ograniczać się do pobrań lub ustawień właściwości.

##  <a name="vccontesting_the_property_page"></a> Wyświetlanie strony właściwości

Można wyświetlić tej strony, należy utworzyć obiekt pomocnika proste. Obiekt pomocnika zapewnia metodę, która upraszcza `OleCreatePropertyFrame` interfejsu API do wyświetlania pojedynczej strony podłączony do pojedynczego obiektu. Tego pomocnika projektowania, aby mogą być używane z Visual Basic.

Użyj [okno dialogowe Dodaj klasę](../ide/add-class-dialog-box.md) i [proste Kreator obiektu ATL](../atl/reference/atl-simple-object-wizard.md) nową klasę do generowania i użytkowania `Helper` jako jego krótką nazwę. Po utworzeniu Dodaj metody, jak pokazano w poniższej tabeli.

|Element|Wartość|
|----------|-----------|
|Nazwa metody|`ShowPage`|
|Parametry|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

*BstrCaption* parametr jest podpis, który ma być wyświetlana jako tytuł okna dialogowego. *BstrID* parametru jest ciąg reprezentujący CLSID lub ProgID strony właściwości, aby wyświetlić. *PUnk* parametr będzie `IUnknown` wskaźnika obiektu, którego właściwości, które zostaną skonfigurowane przez stronę właściwości.

Implementuje metody, jak pokazano poniżej:

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

##  <a name="vcconcreating_a_macro"></a> Tworzenie makra

Po utworzeniu projektu można sprawdzić na stronie właściwości i obiekt pomocnika za pomocą prostego makro, które można tworzyć i uruchamiać w środowisku programowania Visual Studio. To makro utworzy obiekt pomocnika obiektu, a następnie wywołaj jej `ShowPage` metody przy użyciu identyfikatora ProgID **DocProperties** stronę właściwości i `IUnknown` wskaźnika dokumentu, które są aktualnie aktywne w edytorze programu Visual Studio. Poniżej przedstawiono kod, czego potrzebujesz do tego makra:

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

Po uruchomieniu tego makra, zostanie wyświetlona strona właściwości, przedstawiający nazwę pliku i status tylko do odczytu dokumentu tekstowego aktualnie aktywny. Stanu tylko do odczytu dokumentu przedstawiają tylko możliwość zapisu do dokumentu w środowisku programistycznym; nie wpływa na atrybut tylko do odczytu pliku na dysku.

## <a name="see-also"></a>Zobacz też

[Strony właściwości](../atl/atl-com-property-pages.md)<br/>
[Przykładowe ATLPages](../visual-cpp-samples.md)
