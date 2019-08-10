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
ms.openlocfilehash: f9116306fd2bd6145096b055025bd4dd2075b0c1
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916879"
---
# <a name="cpropertypage-class"></a>Klasa CPropertyPage

Reprezentuje pojedyncze strony arkusza właściwości, w przeciwnym razie znane jako karta okna dialogowego.

## <a name="syntax"></a>Składnia

```
class CPropertyPage : public CDialog
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPropertyPage::CPropertyPage](#cpropertypage)|Konstruuje `CPropertyPage` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPropertyPage::CancelToClose](#canceltoclose)|Zmienia przycisk OK na Odczytaj i wyłącza przycisk Anuluj po nieodwracalnej zmianie na stronie modalnego arkusza właściwości.|
|[CPropertyPage:: konstrukcja](#construct)|Konstruuje `CPropertyPage` obiekt. Użyj `Construct` , jeśli chcesz określić parametry w czasie wykonywania lub w przypadku korzystania z tablic.|
|[CPropertyPage::GetPSP](#getpsp)|Pobiera strukturę [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v2) systemu Windows skojarzoną z `CPropertyPage` obiektem.|
|[CPropertyPage:: OnApply](#onapply)|Wywoływane przez platformę, gdy kliknięto przycisk Zastosuj teraz.|
|[CPropertyPage:: OnCancel](#oncancel)|Wywoływane przez platformę, gdy kliknięto przycisk Anuluj.|
|[CPropertyPage::OnKillActive](#onkillactive)|Wywoływane przez platformę, gdy bieżąca strona nie jest już aktywną stroną. Tutaj należy wykonać walidację danych.|
|[CPropertyPage:: OnOK —](#onok)|Wywoływane przez platformę, gdy kliknięto przycisk OK, Zastosuj teraz lub Zamknij.|
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Wywoływane przez platformę, gdy kliknięto przycisk Anuluj, a przed zakończeniem.|
|[CPropertyPage:: onreset](#onreset)|Wywoływane przez platformę, gdy kliknięto przycisk Anuluj.|
|[CPropertyPage::OnSetActive](#onsetactive)|Wywoływane przez platformę, gdy strona jest stroną aktywną.|
|[CPropertyPage::OnWizardBack](#onwizardback)|Wywoływane przez platformę, gdy kliknięto przycisk Wstecz podczas korzystania z arkusza właściwości typu Kreator.|
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Wywoływane przez platformę, gdy kliknięto przycisk Zakończ podczas korzystania z arkusza właściwości typu Kreator.|
|[CPropertyPage::OnWizardNext](#onwizardnext)|Wywoływane przez platformę po kliknięciu przycisku Dalej podczas korzystania z arkusza właściwości typu Kreator.|
|[CPropertyPage::QuerySiblings](#querysiblings)|Przekazuje komunikat do każdej strony arkusza właściwości.|
|[CPropertyPage::SetModified](#setmodified)|Wywołaj, aby uaktywnić lub dezaktywować przycisk Zastosuj teraz.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPropertyPage::m_psp](#m_psp)|Struktura [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v2) systemu Windows. Zapewnia dostęp do podstawowych parametrów strony właściwości.|

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku standardowych okien dialogowych, Klasa `CPropertyPage` jest pochodną dla każdej strony w arkuszu właściwości. Aby użyć `CPropertyPage`obiektów pochodnych, najpierw Utwórz obiekt [CPropertySheet](../../mfc/reference/cpropertysheet-class.md) , a następnie Utwórz obiekt dla każdej strony, która znajduje się w arkuszu właściwości. Wywołaj [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) dla każdej strony w arkuszu, a następnie Wyświetl arkusz właściwości, wywołując [CPropertySheet::D omodal](../../mfc/reference/cpropertysheet-class.md#domodal) dla modalnego arkusza właściwości lub [CPropertySheet:: Create](../../mfc/reference/cpropertysheet-class.md#create) dla niemodalnego arkusza właściwości.

Można utworzyć typ okna dialogowego o nazwie Kreator, który składa się z arkusza właściwości z sekwencją stron właściwości, które prowadzą użytkownika przez kroki operacji, takie jak Konfigurowanie urządzenia lub tworzenie biuletynu. W oknie dialogowym karta typ Kreatora strony właściwości nie mają kart i widoczna jest tylko jedna strona właściwości jednocześnie. Ponadto, zamiast mieć przyciski OK i Zastosuj teraz, okno dialogowe karty typ kreatora ma przycisk Wstecz, przycisk Dalej lub Zakończ, a następnie przycisk Anuluj.

Aby uzyskać więcej informacji na temat tworzenia arkusza właściwości jako kreatora, zobacz [CPropertySheet::](../../mfc/reference/cpropertysheet-class.md#setwizardmode)SetWizardMode. Aby uzyskać więcej informacji na `CPropertyPage` temat używania obiektów, zobacz [arkusze właściwości artykułu i strony właściwości](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs. h

##  <a name="canceltoclose"></a>CPropertyPage::CancelToClose

Wywołaj tę funkcję po wprowadzeniu nieodwracalnej zmiany danych na stronie modalnego arkusza właściwości.

```
void CancelToClose();
```

### <a name="remarks"></a>Uwagi

Ta funkcja zmieni przycisk OK, aby zamknąć i wyłączyć przycisk Anuluj. Ta zmiana ostrzega użytkownika o tym, że zmiana jest trwała, a modyfikacje nie mogą być anulowane.

Funkcja `CancelToClose` członkowska nie ma żadnego niemodalnego arkusza właściwości, ponieważ niemodalny arkusz właściwości domyślnie nie ma przycisku Anuluj.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPropertyPage:: QuerySiblings](#querysiblings).

##  <a name="construct"></a>CPropertyPage:: konstrukcja

Wywołaj tę funkcję elementu członkowskiego `CPropertyPage` , aby skonstruować obiekt.

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
Identyfikator szablonu używany na tej stronie.

*nIDCaption*<br/>
Identyfikator nazwy do umieszczenia na karcie na tej stronie. Jeśli wartość jest równa 0, nazwa zostanie pobrana z szablonu okna dialogowego dla tej strony.

*lpszTemplateName*<br/>
Zawiera ciąg zakończony znakiem null, który jest nazwą zasobu szablonu.

*nIDHeaderTitle*<br/>
Identyfikator nazwy, która ma zostać umieszczona w lokalizacji tytułu nagłówka strony właściwości. Domyślnie 0.

*nIDHeaderSubTitle*<br/>
Identyfikator nazwy, która ma zostać umieszczona w lokalizacji podtytuł nagłówka strony właściwości. Domyślnie 0.

### <a name="remarks"></a>Uwagi

Obiekt jest wyświetlany po spełnieniu wszystkich następujących warunków:

- Strona została dodana do arkusza właściwości przy użyciu [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- Funkcja [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) lub [Create](../../mfc/reference/cpropertysheet-class.md#create) arkusza właściwości została wywołana.

- Użytkownik zaznaczył Tę stronę (z kartami).

Wywołanie `Construct` , jeśli jeden z konstruktorów klas nie został wywołany. Funkcja `Construct` członkowska jest elastyczna, ponieważ można pozostawić instrukcję parametryczną pustą, a następnie określić wiele parametrów i skonstruować w dowolnym momencie w kodzie.

Należy używać `Construct` podczas pracy z tablicami i należy wywołać `Construct` dla każdego elementu członkowskiego tablicy, tak aby elementy członkowskie danych przypisały odpowiednie wartości.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

##  <a name="cpropertypage"></a>CPropertyPage::CPropertyPage

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
Identyfikator szablonu używany na tej stronie.

*nIDCaption*<br/>
Identyfikator nazwy do umieszczenia na karcie na tej stronie. Jeśli wartość jest równa 0, nazwa zostanie pobrana z szablonu okna dialogowego dla tej strony.

*dwSize*<br/>
*lpszTemplateName* Wskazuje ciąg zawierający nazwę szablonu dla tej strony. Nie może mieć wartości NULL.

*nIDHeaderTitle*<br/>
Identyfikator nazwy, która ma zostać umieszczona w lokalizacji tytułu nagłówka strony właściwości.

*nIDHeaderSubTitle*<br/>
Identyfikator nazwy, która ma zostać umieszczona w lokalizacji podtytuł nagłówka strony właściwości.

### <a name="remarks"></a>Uwagi

Obiekt jest wyświetlany po spełnieniu wszystkich następujących warunków:

- Strona została dodana do arkusza właściwości przy użyciu [CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- Funkcja [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) lub [Create](../../mfc/reference/cpropertysheet-class.md#create) arkusza właściwości została wywołana.

- Użytkownik zaznaczył Tę stronę (z kartami).

Jeśli masz wiele parametrów (na przykład jeśli używasz tablicy), użyj [CPropertySheet:: konstrukcja](../../mfc/reference/cpropertysheet-class.md#construct) zamiast `CPropertyPage`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

##  <a name="getpsp"></a>CPropertyPage::GetPSP

Pobiera strukturę [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v2) systemu Windows skojarzoną z `CPropertyPage` obiektem.

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `PROPSHEETPAGE` struktury.

##  <a name="m_psp"></a>CPropertyPage::m_psp

`m_psp`jest strukturą, której członkowie przechowują cechy [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v2).

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Uwagi

Użyj tej struktury, aby zainicjować wygląd strony właściwości po jej skonstruowaniu.

Aby uzyskać więcej informacji na temat tej struktury, łącznie z listą jej elementów `PROPSHEETPAGE` Członkowskich, zobacz w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

##  <a name="onapply"></a>CPropertyPage:: OnApply

Ta funkcja członkowska jest wywoływana przez platformę, gdy użytkownik wybierze przycisk OK lub Zastosuj teraz.

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli zmiany są akceptowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Gdy struktura wywołuje tę funkcję, zmiany wprowadzone na wszystkich stronach właściwości w arkuszu właściwości są akceptowane, arkusz właściwości zachowuje fokus i `OnApply` zwraca wartość true (wartość 1). Zanim `OnApply` będzie można wywołać przez platformę, należy wywołać polecenie [SetModified](#setmodified) i ustawić dla jego parametru wartość true. Spowoduje to aktywowanie przycisku Zastosuj teraz, gdy tylko użytkownik dokona zmiany na stronie właściwości.

Przesłoń tę funkcję elementu członkowskiego, aby określić akcję podejmowaną przez program, gdy użytkownik kliknie przycisk Zastosuj teraz. Podczas zastępowania funkcja powinna zwrócić wartość TRUE, aby akceptować zmiany i FAŁSZ, aby zapobiec wprowadzeniu zmian.

Domyślna implementacja `OnApply` wywołań `OnOK`.

Aby uzyskać więcej informacji na temat komunikatów powiadomień wysyłanych, gdy użytkownik naciśnie przycisk Zastosuj teraz lub OK w arkuszu właściwości, zobacz [PSN_APPLY](/windows/desktop/Controls/psn-apply) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPropertyPage:: OnOK —](#onok).

##  <a name="oncancel"></a>CPropertyPage:: OnCancel

Ta funkcja członkowska jest wywoływana przez platformę, gdy zostanie wybrany przycisk Anuluj.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby wykonać akcje przycisków anulowania. Wartością domyślną jest Negacja wszelkich wprowadzonych zmian.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

##  <a name="onkillactive"></a>CPropertyPage::OnKillActive

Ta funkcja członkowska jest wywoływana przez platformę, gdy strona nie jest już aktywną stroną.

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli dane zostały pomyślnie zaktualizowane, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby wykonywać specjalne zadania sprawdzania poprawności danych.

Domyślna implementacja tej funkcji składowej kopiuje ustawienia z kontrolek na stronie właściwości do zmiennych składowych strony właściwości. Jeśli dane nie zostały pomyślnie zaktualizowane z powodu błędu sprawdzania poprawności danych okna dialogowego (DDV), Strona zachowa fokus.

Po pomyślnym powrocie funkcji elementu członkowskiego platforma wywoła funkcję [OnOK —](#onok) strony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

##  <a name="onok"></a>CPropertyPage:: OnOK —

Ta funkcja członkowska jest wywoływana przez platformę, gdy użytkownik wybierze przycisk OK lub Zastosuj teraz, bezpośrednio po wywołaniu platformy [OnKillActive](#onkillactive).

```
virtual void OnOK();
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze przycisk OK lub Zastosuj teraz, struktura odbiera powiadomienie [PSN_APPLY](/windows/desktop/Controls/psn-apply) ze strony właściwości. Wywołanie `OnOK` nie zostanie wykonane, jeśli wywołasz [CPropertySheet::P ressbutton](../../mfc/reference/cpropertysheet-class.md#pressbutton) , ponieważ strona właściwości nie wyśle powiadomienia w tym przypadku.

Przesłoń tę funkcję elementu członkowskiego, aby zaimplementować dodatkowe zachowanie specyficzne dla aktualnie aktywnej strony, gdy użytkownik odrzuci cały arkusz właściwości.

Domyślna implementacja tej funkcji elementu członkowskiego oznacza stronę jako "czysty", aby odzwierciedlić, że dane zostały zaktualizowane w `OnKillActive` funkcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

##  <a name="onquerycancel"></a>CPropertyPage::OnQueryCancel

Ta funkcja członkowska jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Anuluj i przed wykonaniem akcji anulowania.

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość FALSE, aby zapobiec operacji anulowania lub wartości TRUE, aby zezwolić na to.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby określić akcję podejmowaną przez program, gdy użytkownik kliknie przycisk Anuluj.

Domyślna implementacja `OnQueryCancel` zwraca wartość true.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

##  <a name="onreset"></a>CPropertyPage:: onreset

Ta funkcja członkowska jest wywoływana przez platformę, gdy użytkownik wybierze przycisk Anuluj.

```
virtual void OnReset();
```

### <a name="remarks"></a>Uwagi

Gdy struktura wywołuje tę funkcję, zmiany we wszystkich stronach właściwości, które zostały wprowadzone przez użytkownika przed wybraniem przycisku Zastosuj teraz, są odrzucane, a arkusz właściwości zachowuje fokus.

Przesłoń tę funkcję elementu członkowskiego, aby określić akcję podejmowaną przez program, gdy użytkownik kliknie przycisk Anuluj.

Domyślna implementacja programu `OnReset` nic nie robi.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPropertyPage:: OnCancel](#oncancel).

##  <a name="onsetactive"></a>CPropertyPage::OnSetActive

Ta funkcja członkowska jest wywoływana przez platformę, gdy strona zostanie wybrana przez użytkownika i zostanie uaktywniona.

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli strona została pomyślnie ustawiona jako aktywna; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby wykonywać zadania po aktywowaniu strony. Przesłonięcie tej funkcji składowej zwykle wywołuje domyślną wersję po aktualizacji składowych danych, aby umożliwić jej aktualizację kontrolek strony przy użyciu nowych danych.

Domyślna implementacja powoduje utworzenie okna dla strony, jeśli nie została wcześniej utworzona, i spowoduje, że staje się ona aktywną stroną.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPropertySheet:: SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).

##  <a name="onwizardback"></a>CPropertyPage::OnWizardBack

Ta funkcja członkowska jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Wstecz w kreatorze.

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>Wartość zwracana

0, aby automatycznie przejść do następnej strony; -1, aby zapobiec zmienianiu strony. Aby przejść do strony innej niż Następna, zwróć identyfikator okna dialogowego do wyświetlenia.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby określić akcję, którą użytkownik musi wykonać po naciśnięciu przycisku Wstecz.

Aby uzyskać więcej informacji na temat tworzenia arkusza właściwości typu kreatora, zobacz [CPropertySheet::](../../mfc/reference/cpropertysheet-class.md#setwizardmode)SetWizardMode.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

##  <a name="onwizardfinish"></a>CPropertyPage::OnWizardFinish

Ta funkcja członkowska jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Zakończ w kreatorze.

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli arkusz właściwości zostanie zniszczony po zakończeniu pracy Kreatora; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Gdy użytkownik kliknie przycisk **Zakończ** w kreatorze, struktura wywołuje tę funkcję. gdy `OnWizardFinish` zwraca wartość true (wartość różną od zera), arkusz właściwości może zostać zniszczony (ale nie jest faktycznie zniszczony). Wywołaj `DestroyWindow` , aby zniszczyć arkusz właściwości. Nie wywołuj `DestroyWindow` z `OnWizardFinish`; takie działanie spowoduje uszkodzenie sterty lub inne błędy.

Można zastąpić tę funkcję elementu członkowskiego, aby określić akcję, którą użytkownik musi wykonać po naciśnięciu przycisku Zakończ. Podczas zastępowania tej funkcji Zwróć wartość FALSE, aby zapobiec zniszczeniu arkusza właściwości.

Aby uzyskać więcej informacji na temat komunikatów powiadomień wysyłanych po naciśnięciu przycisku Zakończ w arkuszu właściwości kreatora, zobacz [PSN_WIZFINISH](/windows/desktop/Controls/psn-wizfinish) w Windows SDK.

Aby uzyskać więcej informacji na temat tworzenia arkusza właściwości typu kreatora, zobacz [CPropertySheet::](../../mfc/reference/cpropertysheet-class.md#setwizardmode)SetWizardMode.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

##  <a name="onwizardnext"></a>CPropertyPage::OnWizardNext

Ta funkcja członkowska jest wywoływana przez platformę, gdy użytkownik kliknie przycisk Dalej w kreatorze.

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>Wartość zwracana

0, aby automatycznie przejść do następnej strony; -1, aby zapobiec zmienianiu strony. Aby przejść do strony innej niż Następna, zwróć identyfikator okna dialogowego do wyświetlenia.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby określić akcję, którą użytkownik musi wykonać po naciśnięciu przycisku Dalej.

Aby uzyskać więcej informacji na temat tworzenia arkusza właściwości typu kreatora, zobacz [CPropertySheet::](../../mfc/reference/cpropertysheet-class.md#setwizardmode)SetWizardMode.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

##  <a name="querysiblings"></a>CPropertyPage::QuerySiblings

Wywołaj tę funkcję elementu członkowskiego, aby przesłać dalej komunikat do każdej strony w arkuszu właściwości.

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
Określa dodatkowe informacje zależne od komunikatów.

*lParam*<br/>
Określa dodatkowe informacje zależne od wiadomości

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera ze strony w arkuszu właściwości lub 0, jeśli wszystkie strony zwracają wartość 0.

### <a name="remarks"></a>Uwagi

Jeśli strona zwróci wartość różną od zera, arkusz właściwości nie wyśle komunikatu do kolejnych stron.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

##  <a name="setmodified"></a>CPropertyPage:: SetModified

Wywołaj tę funkcję elementu członkowskiego, aby włączyć lub wyłączyć przycisk Zastosuj teraz, w zależności od tego, czy ustawienia na stronie właściwości mają być stosowane do odpowiedniego obiektu zewnętrznego.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parametry

*bChanged*<br/>
Wartość TRUE oznacza, że ustawienia strony właściwości zostały zmodyfikowane od czasu ostatniego zastosowania. Wartość FAŁSZ oznacza, że ustawienia strony właściwości zostały zastosowane lub powinny być ignorowane.

### <a name="remarks"></a>Uwagi

Struktura śledzi, które strony są "zanieczyszczone", czyli strony właściwości, dla których wywołano `SetModified( TRUE )`. Przycisk Zastosuj teraz będzie zawsze włączany w przypadku wywołania `SetModified( TRUE )` jednej ze stron. Przycisk Zastosuj teraz zostanie wyłączony po wywołaniu `SetModified( FALSE )` jednej ze stron, ale tylko wtedy, gdy żadna z pozostałych stron nie jest "zanieczyszczona".

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>Zobacz także

[Przykład CMNCTRL1 MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład CMNCTRL2 MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład PROPDLG MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład SNAPVW MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPropertySheet](../../mfc/reference/cpropertysheet-class.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
