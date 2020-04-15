---
title: Klasa CPropertyPage
ms.date: 11/04/2016
f1_keywords:
- CPropertyPage
- AFXDLGS/CPropertyPage
- AFXDLGS/CPropertyPage::CPropertyPage
- AFXDLGS/CPropertyPage::CancelToClose
- AFXDLGS/CPropertyPage::Construct
- AFXDLGS/CPropertyPage::GetPSP
- AFXDLGS/CPropertyPage::OnApply
- AFXDLGS/CPropertyPage::OnCancel
- AFXDLGS/CPropertyPage::OnKillActive
- AFXDLGS/CPropertyPage::OnOK
- AFXDLGS/CPropertyPage::OnQueryCancel
- AFXDLGS/CPropertyPage::OnReset
- AFXDLGS/CPropertyPage::OnSetActive
- AFXDLGS/CPropertyPage::OnWizardBack
- AFXDLGS/CPropertyPage::OnWizardFinish
- AFXDLGS/CPropertyPage::OnWizardNext
- AFXDLGS/CPropertyPage::QuerySiblings
- AFXDLGS/CPropertyPage::SetModified
- AFXDLGS/CPropertyPage::m_psp
helpviewer_keywords:
- CPropertyPage [MFC], CPropertyPage
- CPropertyPage [MFC], CancelToClose
- CPropertyPage [MFC], Construct
- CPropertyPage [MFC], GetPSP
- CPropertyPage [MFC], OnApply
- CPropertyPage [MFC], OnCancel
- CPropertyPage [MFC], OnKillActive
- CPropertyPage [MFC], OnOK
- CPropertyPage [MFC], OnQueryCancel
- CPropertyPage [MFC], OnReset
- CPropertyPage [MFC], OnSetActive
- CPropertyPage [MFC], OnWizardBack
- CPropertyPage [MFC], OnWizardFinish
- CPropertyPage [MFC], OnWizardNext
- CPropertyPage [MFC], QuerySiblings
- CPropertyPage [MFC], SetModified
- CPropertyPage [MFC], m_psp
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
ms.openlocfilehash: 816948ea17f674c3cd693331502df33cce62610c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364001"
---
# <a name="cpropertypage-class"></a>Klasa CPropertyPage

Reprezentuje poszczególne strony arkusza właściwości, inaczej nazywane okno dialogowe karty.

## <a name="syntax"></a>Składnia

```
class CPropertyPage : public CDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Strona CProperty::CPropertyPage](#cpropertypage)|Konstruuje `CPropertyPage` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPropertyPage::CancelToToZło](#canceltoclose)|Zmienia przycisk OK, aby odczytać Przycisk Zamknij, i wyłącza przycisk Anuluj po nieodwracalnej zmianie na stronie arkusza właściwości modalnych.|
|[CPropertyPage::Konstrukcja](#construct)|Konstruuje `CPropertyPage` obiekt. Użyj, `Construct` jeśli chcesz określić parametry w czasie wykonywania lub jeśli używasz tablic.|
|[Strona CProperty::GetPSP](#getpsp)|Pobiera strukturę Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) skojarzoną z obiektem. `CPropertyPage`|
|[CPropertyPage::OnApply](#onapply)|Wywoływana przez strukturę po kliknięciu przycisku Zastosuj teraz.|
|[CPropertyPage::OnCancel](#oncancel)|Wywoływane przez strukturę po kliknięciu przycisku Anuluj.|
|[CPropertyPage::OnKillActive](#onkillactive)|Wywoływana przez strukturę, gdy bieżąca strona nie jest już aktywną stroną. Tutaj wykonaj sprawdzanie poprawności danych.|
|[CPropertyPage::OnOK](#onok)|Wywoływane przez strukturę po kliknięciu przycisku OK, Zastosuj teraz lub Zamknij.|
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Wywoływane przez strukturę po kliknięciu przycisku Anuluj i przed anulowaniem miało miejsce.|
|[CPropertyPage::OnReset](#onreset)|Wywoływane przez strukturę po kliknięciu przycisku Anuluj.|
|[CPropertyPage::OnSetActive](#onsetactive)|Wywoływana przez strukturę, gdy strona jest aktywna strona.|
|[Strona CProperty::OnWizardBack](#onwizardback)|Wywoływane przez strukturę po kliknięciu przycisku Wstecz podczas korzystania z arkusza właściwości typu kreatora.|
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Wywoływane przez strukturę po kliknięciu przycisku Zakończ podczas korzystania z arkusza właściwości typu kreatora.|
|[CPropertyPage::OnWizardNext](#onwizardnext)|Wywoływane przez strukturę po kliknięciu przycisku Dalej podczas korzystania z arkusza właściwości typu kreatora.|
|[CPropertyPage::QuerySiblings](#querysiblings)|Przekazuje wiadomość do każdej strony arkusza właściwości.|
|[CPropertyPage::SetModified](#setmodified)|Zadzwoń, aby aktywować lub dezaktywować przycisk Zastosuj teraz.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPropertyPage::m_psp](#m_psp)|Struktura Windows [PROPSHEETPAGE.](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) Zapewnia dostęp do podstawowych parametrów strony właściwości.|

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku standardowych okien `CPropertyPage` dialogowych, klasy pochodzić z dla każdej strony w arkuszu właściwości. Aby `CPropertyPage`użyć obiektów pochodnych, należy najpierw utworzyć obiekt [CPropertySheet,](../../mfc/reference/cpropertysheet-class.md) a następnie utworzyć obiekt dla każdej strony, która znajduje się w arkuszu właściwości. Wywołanie [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) dla każdej strony w arkuszu, a następnie wyświetlić arkusz właściwości, wywołując [CPropertySheet::DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) dla arkusza właściwości modalnej lub [CPropertySheet::Create](../../mfc/reference/cpropertysheet-class.md#create) dla arkusza właściwości bez trybu.

Można utworzyć typ okna dialogowego karty o nazwie kreator, który składa się z arkusza właściwości z sekwencją stron właściwości, które prowadzą użytkownika przez kroki operacji, takie jak konfigurowanie urządzenia lub tworzenie biuletynu. W oknie dialogowym karty typu kreatora strony właściwości nie mają kart, a jednocześnie jest widoczna tylko jedna strona właściwości. Ponadto zamiast przycisków OK i Zastosuj teraz, okno dialogowe typu kreatora ma przycisk Wstecz, przycisk Dalej lub Zakończ i przycisk Anuluj.

Aby uzyskać więcej informacji na temat ustanawiania arkusza właściwości jako kreatora, zobacz [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Aby uzyskać więcej `CPropertyPage` informacji na temat używania obiektów, zobacz artykuł [Arkusze właściwości i strony właściwości](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

## <a name="cpropertypagecanceltoclose"></a><a name="canceltoclose"></a>CPropertyPage::CancelToToZło

Wywołanie tej funkcji po nieodwracalnej zmiany zostały wprowadzone do danych na stronie arkusza właściwości modalnych.

```
void CancelToClose();
```

### <a name="remarks"></a>Uwagi

Ta funkcja zmieni przycisk OK, aby zamknąć i wyłączyć przycisk Anuluj. Ta zmiana ostrzega użytkownika, że zmiana jest trwała i modyfikacje nie mogą zostać anulowane.

Funkcja `CancelToClose` elementu członkowskiego nie robi nic w arkuszu właściwości bez trybu, ponieważ arkusz właściwości bez trybu nie ma domyślnie przycisku Anuluj.

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertyPage::QuerySiblings](#querysiblings).

## <a name="cpropertypageconstruct"></a><a name="construct"></a>CPropertyPage::Konstrukcja

Wywołanie tej funkcji `CPropertyPage` elementu członkowskiego do konstruowania obiektu.

```
void Construct(
    UINT nIDTemplate,
    UINT nIDCaption = 0);

void Construct(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption = 0);

void Construct(
    UINT nIDTemplate,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0);

void Construct(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0);
```

### <a name="parameters"></a>Parametry

*nIDTemplate*<br/>
Identyfikator szablonu używanego dla tej strony.

*nIDCaption (nIDCaption)*<br/>
Identyfikator nazwy, która ma zostać umieszczona na karcie dla tej strony. Jeśli 0, nazwa zostanie pobrana z szablonu okna dialogowego dla tej strony.

*lpszTemplateName*<br/>
Zawiera ciąg zakończony zerem, który jest nazwą zasobu szablonu.

*nIDHeaderTitle (Napis nagłówka)*<br/>
Identyfikator nazwy, która ma zostać umieszczona w lokalizacji tytułu nagłówka strony właściwości. Domyślnie 0.

*nIDHeaderSubTitle*<br/>
Identyfikator nazwy, która ma zostać umieszczona w lokalizacji napisów nagłówka strony właściwości. Domyślnie 0.

### <a name="remarks"></a>Uwagi

Obiekt jest wyświetlany po spełnieniu wszystkich następujących warunków:

- Strona została dodana do arkusza właściwości przy użyciu [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- Wywołano funkcję [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) lub [Create](../../mfc/reference/cpropertysheet-class.md#create) arkusza właściwości.

- Użytkownik wybrał tę stronę (z kartami).

Wywołanie, `Construct` jeśli jeden z innych konstruktorów klasy nie został wywołany. Funkcja `Construct` elementu członkowskiego jest elastyczna, ponieważ można pozostawić instrukcję parametru pustą, a następnie określić wiele parametrów i konstrukcji w dowolnym punkcie kodu.

Należy użyć `Construct` podczas pracy z tablicami i `Construct` należy wywołać dla każdego członka tablicy, tak aby elementy członkowskie danych są przypisane prawidłowe wartości.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

## <a name="cpropertypagecpropertypage"></a><a name="cpropertypage"></a>Strona CProperty::CPropertyPage

Konstruuje `CPropertyPage` obiekt.

```
CPropertyPage();

explicit CPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

explicit CPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

CPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

CPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));
```

### <a name="parameters"></a>Parametry

*nIDTemplate*<br/>
Identyfikator szablonu używanego dla tej strony.

*nIDCaption (nIDCaption)*<br/>
Identyfikator nazwy, która ma zostać umieszczona na karcie dla tej strony. Jeśli 0, nazwa zostanie pobrana z szablonu okna dialogowego dla tej strony.

*dwSize (rozmiar)*<br/>
*lpszTemplateName* Wskazuje ciąg zawierający nazwę szablonu dla tej strony. Nie może być null.

*nIDHeaderTitle (Napis nagłówka)*<br/>
Identyfikator nazwy, która ma zostać umieszczona w lokalizacji tytułu nagłówka strony właściwości.

*nIDHeaderSubTitle*<br/>
Identyfikator nazwy, która ma zostać umieszczona w lokalizacji napisów nagłówka strony właściwości.

### <a name="remarks"></a>Uwagi

Obiekt jest wyświetlany po spełnieniu wszystkich następujących warunków:

- Strona została dodana do arkusza właściwości przy użyciu [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- Wywołano funkcję [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) lub [Create](../../mfc/reference/cpropertysheet-class.md#create) arkusza właściwości.

- Użytkownik wybrał tę stronę (z kartami).

Jeśli masz wiele parametrów (na przykład, jeśli używasz [tablicy), użyj CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct) zamiast `CPropertyPage`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

## <a name="cpropertypagegetpsp"></a><a name="getpsp"></a>Strona CProperty::GetPSP

Pobiera strukturę Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) skojarzoną z obiektem. `CPropertyPage`

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `PROPSHEETPAGE` struktury.

## <a name="cpropertypagem_psp"></a><a name="m_psp"></a>CPropertyPage::m_psp

`m_psp`jest strukturą, której członkowie przechowują cechy [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2).

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Uwagi

Ta struktura służy do inicjowania wyglądu strony właściwości po jej skonstruowaniu.

Aby uzyskać więcej informacji na temat tej struktury, w tym listę jej członków, zobacz `PROPSHEETPAGE` w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

## <a name="cpropertypageonapply"></a><a name="onapply"></a>CPropertyPage::OnApply

Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik wybierze przycisk OK lub Zastosuj teraz.

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli zmiany są akceptowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Gdy framework wywołuje tę funkcję, zmiany wprowadzone na wszystkich stronach właściwości w arkuszu właściwości `OnApply` są akceptowane, arkusz właściwości zachowuje fokus i zwraca wartość TRUE (wartość 1). Zanim `OnApply` może być wywołana przez strukturę, musisz mieć [wywołane SetModified](#setmodified) i ustawić jego parametr true. Spowoduje to aktywowanie przycisku Zastosuj teraz, gdy tylko użytkownik zmieni się na stronie właściwości.

Zastąp tę funkcję elementu członkowskiego, aby określić, jakie działania wykonuje program, gdy użytkownik kliknie przycisk Zastosuj teraz. Podczas zastępowania funkcja powinna zwracać wartość PRAWDA, aby zaakceptować zmiany i fałsz, aby zapobiec wprowadzaniu zmian.

Domyślna implementacja `OnOK`wywołań `OnApply` .

Aby uzyskać więcej informacji o wiadomościach powiadomień wysyłanych, gdy użytkownik naciśnie przycisk Zastosuj teraz lub OK w arkuszu właściwości, zobacz [PSN_APPLY](/windows/win32/Controls/psn-apply) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertyPage::OnOK](#onok).

## <a name="cpropertypageoncancel"></a><a name="oncancel"></a>CPropertyPage::OnCancel

Ta funkcja elementu członkowskiego jest wywoływana przez platformę po wybraniu przycisku Anuluj.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję elementu członkowskiego, aby wykonać akcje przycisku Anuluj. Wartość domyślna neguje wszelkie zmiany, które zostały wprowadzone.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

## <a name="cpropertypageonkillactive"></a><a name="onkillactive"></a>CPropertyPage::OnKillActive

Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy strona nie jest już aktywną stroną.

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli dane zostały pomyślnie zaktualizowane, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zastąpojąć tę funkcję elementu członkowskiego do wykonywania zadań sprawdzania poprawności danych specjalnych.

Domyślna implementacja tej funkcji elementu członkowskiego kopiuje ustawienia z formantów na stronie właściwości do zmiennych członkowskich strony właściwości. Jeśli dane nie zostały pomyślnie zaktualizowane z powodu błędu sprawdzania poprawności danych okna dialogowego (DDV), strona zachowuje fokus.

Po pomyślnym powrocie tej funkcji elementu członkowskiego, ramach wywoła page's [OnOK](#onok) funkcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

## <a name="cpropertypageonok"></a><a name="onok"></a>CPropertyPage::OnOK

Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik wybierze przycisk OK lub Zastosuj teraz, natychmiast po wywołaniu przez platformę [OnKillActive](#onkillactive).

```
virtual void OnOK();
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze przycisk OK lub Zastosuj teraz, struktura odbiera powiadomienie [PSN_APPLY](/windows/win32/Controls/psn-apply) ze strony właściwości. Wywołanie `OnOK` nie zostanie wykonane, jeśli wywołasz [CPropertySheet::PressButton,](../../mfc/reference/cpropertysheet-class.md#pressbutton) ponieważ strona właściwości nie wysyła powiadomienia w takim przypadku.

Zastąpokaj tę funkcję elementu członkowskiego, aby zaimplementować dodatkowe zachowanie specyficzne dla aktualnie aktywnej strony, gdy użytkownik odrzuci cały arkusz właściwości.

Domyślna implementacja tej funkcji elementu członkowskiego oznacza stronę jako "czystą", aby odzwierciedlić, że dane zostały zaktualizowane w `OnKillActive` funkcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

## <a name="cpropertypageonquerycancel"></a><a name="onquerycancel"></a>CPropertyPage::OnQueryCancel

Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Anuluj i przed anuluj akcję.

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość FALSE, aby zapobiec operacji anulowania lub true, aby na to zezwolić.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję elementu członkowskiego, aby określić akcję, która zostanie wykonaniu przez program, gdy użytkownik kliknie przycisk Anuluj.

Domyślna implementacja `OnQueryCancel` zwraca wartość TRUE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

## <a name="cpropertypageonreset"></a><a name="onreset"></a>CPropertyPage::OnReset

Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik wybierze przycisk Anuluj.

```
virtual void OnReset();
```

### <a name="remarks"></a>Uwagi

Gdy framework wywołuje tę funkcję, zmiany na wszystkich stronach właściwości, które zostały wprowadzone przez użytkownika wcześniej wybierając przycisk Zastosuj teraz są odrzucane, a arkusz właściwości zachowuje fokus.

Zastąp tę funkcję elementu członkowskiego, aby określić, jakie działania program wykonuje, gdy użytkownik kliknie przycisk Anuluj.

Domyślna implementacja `OnReset` nic nie robi.

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertyPage::OnCancel](#oncancel).

## <a name="cpropertypageonsetactive"></a><a name="onsetactive"></a>CPropertyPage::OnSetActive

Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy strona jest wybierana przez użytkownika i staje się aktywną stroną.

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli strona została pomyślnie ustawiona jako aktywna; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zastąpojąć tę funkcję elementu członkowskiego do wykonywania zadań, gdy strona jest aktywowana. Zastąpienie tej funkcji elementu członkowskiego zazwyczaj wywoła wersję domyślną po zaktualizowaniu elementów członkowskich danych, aby umożliwić jej zaktualizowanie formantów strony za pomocą nowych danych.

Domyślna implementacja tworzy okno dla strony, jeśli nie została wcześniej utworzona, i sprawia, że jest aktywną stroną.

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).

## <a name="cpropertypageonwizardback"></a><a name="onwizardback"></a>Strona CProperty::OnWizardBack

Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Wstecz w kreatorze.

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>Wartość zwracana

0, aby automatycznie przejść do następnej strony; -1, aby zapobiec zmianie strony. Aby przejść do strony innej niż następna, zwróć identyfikator okna dialogowego, które ma być wyświetlane.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję elementu członkowskiego, aby określić niektóre działania, które użytkownik musi podjąć po naciśnięciu przycisku Wstecz.

Aby uzyskać więcej informacji na temat tworzenia arkusza właściwości typu kreatora, zobacz [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

## <a name="cpropertypageonwizardfinish"></a><a name="onwizardfinish"></a>CPropertyPage::OnWizardFinish

Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Zakończ w kreatorze.

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli arkusz właściwości zostanie zniszczony po zakończeniu pracy kreatora; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Gdy użytkownik kliknie przycisk **Zakończ** w kreatorze, struktura wywołuje tę funkcję; po `OnWizardFinish` zwróceniu wartości TRUE (wartość niezerowa), arkusz właściwości może zostać zniszczony (ale nie jest faktycznie niszczony). Wywołanie, `DestroyWindow` aby zniszczyć arkusz właściwości. Nie `DestroyWindow` dzwonić `OnWizardFinish`z ; spowoduje to uszkodzenie sterty lub inne błędy.

Można zastąpić tę funkcję elementu członkowskiego, aby określić niektóre działania, które użytkownik musi podjąć po naciśnięciu przycisku Zakończ. Podczas zastępowania tej funkcji zwraca wartość FAŁSZ, aby zapobiec zniszczeniu arkusza właściwości.

Aby uzyskać więcej informacji o komunikatach powiadomień wysyłanych po naciśnięciu przez użytkownika przycisku Zakończ w arkuszu właściwości kreatora, zobacz [PSN_WIZFINISH](/windows/win32/Controls/psn-wizfinish) w zestawie Windows SDK.

Aby uzyskać więcej informacji na temat tworzenia arkusza właściwości typu kreatora, zobacz [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

## <a name="cpropertypageonwizardnext"></a><a name="onwizardnext"></a>CPropertyPage::OnWizardNext

Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Dalej w kreatorze.

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>Wartość zwracana

0, aby automatycznie przejść do następnej strony; -1, aby zapobiec zmianie strony. Aby przejść do strony innej niż następna, zwróć identyfikator okna dialogowego, które ma być wyświetlane.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję elementu członkowskiego, aby określić niektóre działania, które użytkownik musi podjąć po naciśnięciu przycisku Dalej.

Aby uzyskać więcej informacji na temat tworzenia arkusza właściwości typu kreatora, zobacz [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

## <a name="cpropertypagequerysiblings"></a><a name="querysiblings"></a>CPropertyPage::QuerySiblings

Wywołanie tej funkcji elementu członkowskiego, aby przesłać dalej wiadomość do każdej strony w arkuszu właściwości.

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Wparam*<br/>
Określa dodatkowe informacje zależne od wiadomości.

*Lparam*<br/>
Określa dodatkowe informacje zależne od wiadomości

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa ze strony w arkuszu właściwości lub 0, jeśli wszystkie strony zwracają wartość 0.

### <a name="remarks"></a>Uwagi

Jeśli strona zwraca wartość niezerową, arkusz właściwości nie wysyła wiadomości do kolejnych stron.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

## <a name="cpropertypagesetmodified"></a><a name="setmodified"></a>CPropertyPage::SetModified

Wywołanie tej funkcji elementu członkowskiego, aby włączyć lub wyłączyć przycisk Zastosuj teraz, w zależności od tego, czy ustawienia na stronie właściwości powinny być stosowane do odpowiedniego obiektu zewnętrznego.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parametry

*bZmienione*<br/>
PRAWDA, aby wskazać, że ustawienia strony właściwości zostały zmodyfikowane od czasu ostatniego ich zastosowania; FALSE, aby wskazać, że ustawienia strony właściwości zostały zastosowane lub powinny zostać zignorowane.

### <a name="remarks"></a>Uwagi

Struktura śledzi, które strony są "brudne", czyli strony właściwości, dla których został `SetModified( TRUE )`wywołany . Przycisk Zastosuj teraz będzie zawsze włączony, `SetModified( TRUE )` jeśli zadzwonisz na jedną ze stron. Przycisk Zastosuj teraz zostanie wyłączony, `SetModified( FALSE )` gdy wywołasz jedną ze stron, ale tylko wtedy, gdy żadna z pozostałych stron nie jest "brudna".

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPropertySheet](../../mfc/reference/cpropertysheet-class.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
