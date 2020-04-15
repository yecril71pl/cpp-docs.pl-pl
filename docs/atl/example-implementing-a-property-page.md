---
title: Implementowanie strony właściwości (ATL)
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
ms.openlocfilehash: 0b2448e66e3b86e3295cd4b318a268a113f6058b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319577"
---
# <a name="example-implementing-a-property-page"></a>Przykład: Implementowanie strony właściwości

::: moniker range="vs-2019"

Kreator strony właściwości ATL nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

W tym przykładzie pokazano, jak utworzyć stronę właściwości, która wyświetla (i pozwala na zmianę) właściwości interfejsu [Klasy dokumentów.](../mfc/document-classes.md)

Przykład jest oparty na [przykładzie ATLPages](../overview/visual-cpp-samples.md).

Aby wykonać ten przykład, należy:

- [Dodawanie klasy strony właściwości ATL](#vcconusing_the_atl_object_wizard) za pomocą okna dialogowego Dodawanie klasy i Kreatora strony właściwości ATL.

- [Edytuj zasób okna dialogowego,](#vcconediting_the_dialog_resource) dodając nowe `Document` formanty dla interesujących właściwości interfejsu.

- [Dodaj programy obsługi wiadomości,](#vcconadding_message_handlers) aby informować witrynę strony właściwości o zmianach wprowadzonych przez użytkownika.

- Dodaj `#import` kilka instrukcji i typedef w sekcji [Sprzątanie.](#vcconhousekeeping)

- [Zastąp IPropertyPageImpl::SetObjects,](#vcconoverriding_ipropertypageimpl_setobjects) aby sprawdzić poprawność obiektów przekazywanych do strony właściwości.

- [Zastąp IPropertyPageImpl::Aktywuj,](#vcconoverriding_ipropertypageimpl_activate) aby zainicjować interfejs strony właściwości.

- [Zastąp IPropertyPageImpl::Zastosuj,](#vcconoverride_ipropertypageimpl_apply) aby zaktualizować obiekt o najnowsze wartości właściwości.

- [Wyświetl stronę właściwości,](#vccontesting_the_property_page) tworząc prosty obiekt pomocniczy.

- [Utwórz makro,](#vcconcreating_a_macro) które przetestuje stronę właściwości.

## <a name="adding-the-atl-property-page-class"></a><a name="vcconusing_the_atl_object_wizard"></a>Dodawanie klasy strony właściwości ATL

Najpierw utwórz nowy projekt ATL dla `ATLPages7`serwera DLL o nazwie . Teraz użyj [Kreatora strony właściwości ATL,](../atl/reference/atl-property-page-wizard.md) aby wygenerować stronę właściwości. Nadaj stronie właściwości **krótką nazwę** **właściwości DocProperties,** a następnie przełącz się na stronę **Ciągi,** aby ustawić elementy specyficzne dla strony właściwości, jak pokazano w poniższej tabeli.

|Element|Wartość|
|----------|-----------|
|Tytuł|Dokument tekstowy|
|Ciąg doc|Właściwości dokumentu tekstowego VCUE|
|Helpfile|*\<puste>*|

Wartości ustawione na tej stronie kreatora zostaną zwrócone do kontenera `IPropertyPage::GetPageInfo`strony właściwości podczas wywołania . Co się dzieje z ciągami po tym jest zależna od kontenera, ale zazwyczaj będą one używane do identyfikowania strony do użytkownika. Tytuł zwykle pojawia się na karcie nad stroną, a ciąg dok może być wyświetlany na pasku stanu lub etykietce narzędzia (chociaż standardowa ramka właściwości w ogóle nie używa tego ciągu).

> [!NOTE]
> Ciągi, które można ustawić w tym miejscu są przechowywane jako zasoby ciągów w projekcie przez kreatora. Można łatwo edytować te ciągi za pomocą edytora zasobów, jeśli trzeba zmienić te informacje po wygenerowaniu kodu strony.

Kliknij **przycisk OK,** aby kreator wygenerował stronę właściwości.

## <a name="editing-the-dialog-resource"></a><a name="vcconediting_the_dialog_resource"></a>Edytowanie zasobu okna dialogowego

Teraz, gdy strona właściwości została wygenerowana, musisz dodać kilka formantów do zasobu okna dialogowego reprezentującego stronę. Dodaj pole edycji, statyczny formant tekstowy i pole wyboru i ustaw ich identyfikatory, jak pokazano poniżej:

![Edytowanie zasobu okna dialogowego](../atl/media/ppgresourcelabeled.gif "Edytowanie zasobu okna dialogowego")

Te formanty będą używane do wyświetlania nazwy pliku dokumentu i jego stanu tylko do odczytu.

> [!NOTE]
> Zasób okna dialogowego nie zawiera ramki ani przycisków poleceń ani nie ma wyglądu z kartami, który mógł się spodziewać. Te funkcje są dostarczane przez ramkę strony właściwości, taką jak utworzona przez wywołanie [OleCreatePropertyFrame](/windows/win32/api/olectl/nf-olectl-olecreatepropertyframe).

## <a name="adding-message-handlers"></a><a name="vcconadding_message_handlers"></a>Dodawanie programów obsługi wiadomości

Za pomocą formantów można dodać programy obsługi wiadomości, aby zaktualizować stan brudnej strony, gdy zmieni się wartość jednego z formantów:

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

Ten kod odpowiada na zmiany wprowadzone w formancie edycji lub polu wyboru, wywołując [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty), który informuje witrynę strony, że strona została zmieniona. Zazwyczaj witryna strony będzie reagować, włączając lub wyłączając przycisk **Zastosuj** w ramce strony właściwości.

> [!NOTE]
> Na stronach własnych właściwości może być konieczne śledzenie dokładnie, które właściwości zostały zmienione przez użytkownika, dzięki czemu można uniknąć aktualizowania właściwości, które nie zostały zmienione. W tym przykładzie implementuje ten kod, śledząc oryginalne wartości właściwości i porównując je z bieżącymi wartościami z interfejsu użytkownika, gdy nadszedł czas, aby zastosować zmiany.

## <a name="housekeeping"></a><a name="vcconhousekeeping"></a>Sprzątanie

Teraz dodaj kilka `#import` instrukcji do DocProperties.h tak, że `Document` kompilator wie o interfejsie:

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

Musisz również odwołać się `IPropertyPageImpl` do klasy podstawowej; dodaj do `CDocProperties` klasy następujące **typedef:**

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

## <a name="overriding-ipropertypageimplsetobjects"></a><a name="vcconoverriding_ipropertypageimpl_setobjects"></a>Zastępowanie IPropertyPageImpl::SetObjects

Pierwszą `IPropertyPageImpl` metodą, którą należy zastąpić, jest [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects). W tym miejscu dodasz kod, aby sprawdzić, czy tylko `Document` jeden obiekt został przekazany i czy obsługuje interfejs, którego oczekujesz:

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
> Warto obsługiwać tylko jeden obiekt dla tej strony, ponieważ użytkownik może ustawić nazwę pliku obiektu — tylko jeden plik może istnieć w dowolnej lokalizacji.

## <a name="overriding-ipropertypageimplactivate"></a><a name="vcconoverriding_ipropertypageimpl_activate"></a>Zastępowanie IPropertyPageImpl::Aktywuj

Następnym krokiem jest zainicjowanie strony właściwości z wartościami właściwości obiektu źródłowego podczas pierwszego tworzenia strony.

W takim przypadku należy dodać następujące elementy członkowskie do klasy, ponieważ będziesz również używać początkowych wartości właściwości do porównania, gdy użytkownicy strony zastosują swoje zmiany:

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

Implementacja klasy podstawowej [Activate](../atl/reference/ipropertypageimpl-class.md#activate) metoda jest odpowiedzialny za tworzenie okna dialogowego i jego formantów, dzięki czemu można zastąpić tę metodę i dodać własne inicjowanie po wywołaniu klasy podstawowej:

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

Ten kod używa metod COM `Document` interfejsu, aby uzyskać właściwości, które Cię interesują. Następnie używa otoki interfejsu API Win32 dostarczone przez [CDialogImpl](../atl/reference/cdialogimpl-class.md) i jego klas podstawowych do wyświetlania wartości właściwości do użytkownika.

## <a name="overriding-ipropertypageimplapply"></a><a name="vcconoverride_ipropertypageimpl_apply"></a>Zastępowanie IPropertyPageImpl::Zastosuj

Gdy użytkownicy chcą zastosować swoje zmiany do obiektów, witryna strony właściwości wywoła [Apply](../atl/reference/ipropertypageimpl-class.md#apply) metody. Jest to miejsce, aby wykonać odwrotną część kodu w `Activate` — podczas gdy `Activate` wziął wartości z `Apply` obiektu i wypchnął je do formantów na stronie właściwości, pobiera wartości z formantów na stronie właściwości i wypycha je do obiektu.

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
> Sprawdzanie [przed m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) na początku tej implementacji jest sprawdzanie wstępne, aby `Apply` uniknąć niepotrzebnych aktualizacji obiektów, jeśli jest wywoływana więcej niż jeden raz. Istnieją również kontrole dla każdej z wartości właściwości, aby upewnić `Document`się, że tylko zmiany powodują wywołanie metody do .

> [!NOTE]
> `Document`udostępnia `FullName` jako właściwość tylko do odczytu. Aby zaktualizować nazwę pliku dokumentu na podstawie zmian wprowadzonych na stronie `Save` właściwości, należy użyć metody zapisywania pliku o innej nazwie. W związku z tym kod na stronie właściwości nie musi ograniczać się do uzyskiwania lub ustawiania właściwości.

## <a name="displaying-the-property-page"></a><a name="vccontesting_the_property_page"></a>Wyświetlanie strony właściwości

Aby wyświetlić tę stronę, należy utworzyć prosty obiekt pomocniczy. Obiekt pomocnika zapewni metodę, która upraszcza `OleCreatePropertyFrame` interfejs API do wyświetlania pojedynczej strony połączonej z pojedynczym obiektem. Ten pomocnik zostanie zaprojektowany tak, aby mógł być używany z języka Visual Basic.

Użyj [okna dialogowego Dodawanie klasy](../ide/add-class-dialog-box.md) i [Kreatora obiektów prostych ATL,](../atl/reference/atl-simple-object-wizard.md) aby wygenerować nową klasę i użyć `Helper` jej jako krótkiej nazwy. Po utworzeniu dodaj metodę, jak pokazano w poniższej tabeli.

|Element|Wartość|
|----------|-----------|
|Nazwa metody|`ShowPage`|
|Parametry|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

Parametr *bstrCaption* to podpis, który ma być wyświetlany jako tytuł okna dialogowego. Parametr *bstrID* jest ciągiem reprezentującym identyfikator CLSID lub progid strony właściwości do wyświetlenia. Parametr *pUnk* będzie `IUnknown` wskaźnikiem obiektu, którego właściwości zostaną skonfigurowane przez stronę właściwości.

Zaimplementuj metodę, jak pokazano poniżej:

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

## <a name="creating-a-macro"></a><a name="vcconcreating_a_macro"></a>Tworzenie makra

Po utworzeniu projektu można przetestować stronę właściwości i obiekt pomocniczy przy użyciu prostego makra, które można utworzyć i uruchomić w środowisku programistycznym programistycznemu. To makro utworzy obiekt pomocniczy, `ShowPage` a następnie wywoła jego metodę przy użyciu progid strony właściwości **DocProperties** i `IUnknown` wskaźnik dokumentu aktualnie aktywny w edytorze programu Visual Studio. Kod potrzebny do tego makra jest pokazany poniżej:

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

Po uruchomieniu tego makra zostanie wyświetlona strona właściwości z nazwą pliku i stanem tylko do odczytu aktualnie aktywnego dokumentu tekstowego. Stan tylko do odczytu dokumentu odzwierciedla tylko możliwość zapisu do dokumentu w środowisku programistycznym; nie ma to wpływu na atrybut tylko do odczytu pliku na dysku.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Strony właściwości](../atl/atl-com-property-pages.md)<br/>
[Przykład ATLPages](../overview/visual-cpp-samples.md)
