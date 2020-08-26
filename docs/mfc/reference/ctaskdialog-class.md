---
title: Klasa obiektu CTaskDialog
ms.date: 11/19/2018
f1_keywords:
- CTaskDialog
- AFXTASKDIALOG/CTaskDialog
- AFXTASKDIALOG/CTaskDialog::CTaskDialog
- AFXTASKDIALOG/CTaskDialog::AddCommandControl
- AFXTASKDIALOG/CTaskDialog::AddRadioButton
- AFXTASKDIALOG/CTaskDialog::ClickCommandControl
- AFXTASKDIALOG/CTaskDialog::ClickRadioButton
- AFXTASKDIALOG/CTaskDialog::DoModal
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonCount
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonFlag
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonId
- AFXTASKDIALOG/CTaskDialog::GetOptions
- AFXTASKDIALOG/CTaskDialog::GetSelectedCommandControlID
- AFXTASKDIALOG/CTaskDialog::GetSelectedRadioButtonID
- AFXTASKDIALOG/CTaskDialog::GetVerificationCheckboxState
- AFXTASKDIALOG/CTaskDialog::IsCommandControlEnabled
- AFXTASKDIALOG/CTaskDialog::IsRadioButtonEnabled
- AFXTASKDIALOG/CTaskDialog::IsSupported
- AFXTASKDIALOG/CTaskDialog::LoadCommandControls
- AFXTASKDIALOG/CTaskDialog::LoadRadioButtons
- AFXTASKDIALOG/CTaskDialog::NavigateTo
- AFXTASKDIALOG/CTaskDialog::OnCommandControlClick
- AFXTASKDIALOG/CTaskDialog::OnCreate
- AFXTASKDIALOG/CTaskDialog::OnDestroy
- AFXTASKDIALOG/CTaskDialog::OnExpandButtonClick
- AFXTASKDIALOG/CTaskDialog::OnHelp
- AFXTASKDIALOG/CTaskDialog::OnHyperlinkClick
- AFXTASKDIALOG/CTaskDialog::OnInit
- AFXTASKDIALOG/CTaskDialog::OnNavigatePage
- AFXTASKDIALOG/CTaskDialog::OnRadioButtonClick
- AFXTASKDIALOG/CTaskDialog::OnTimer
- AFXTASKDIALOG/CTaskDialog::OnVerificationCheckboxClick
- AFXTASKDIALOG/CTaskDialog::RemoveAllCommandControls
- AFXTASKDIALOG/CTaskDialog::RemoveAllRadioButtons
- AFXTASKDIALOG/CTaskDialog::SetCommandControlOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtons
- AFXTASKDIALOG/CTaskDialog::SetContent
- AFXTASKDIALOG/CTaskDialog::SetDefaultCommandControl
- AFXTASKDIALOG/CTaskDialog::SetDefaultRadioButton
- AFXTASKDIALOG/CTaskDialog::SetDialogWidth
- AFXTASKDIALOG/CTaskDialog::SetExpansionArea
- AFXTASKDIALOG/CTaskDialog::SetFooterIcon
- AFXTASKDIALOG/CTaskDialog::SetFooterText
- AFXTASKDIALOG/CTaskDialog::SetMainIcon
- AFXTASKDIALOG/CTaskDialog::SetMainInstruction
- AFXTASKDIALOG/CTaskDialog::SetOptions
- AFXTASKDIALOG/CTaskDialog::SetProgressBarMarquee
- AFXTASKDIALOG/CTaskDialog::SetProgressBarPosition
- AFXTASKDIALOG/CTaskDialog::SetProgressBarRange
- AFXTASKDIALOG/CTaskDialog::SetProgressBarState
- AFXTASKDIALOG/CTaskDialog::SetRadioButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckbox
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckboxText
- AFXTASKDIALOG/CTaskDialog::SetWindowTitle
- AFXTASKDIALOG/CTaskDialog::ShowDialog
- AFXTASKDIALOG/CTaskDialog::TaskDialogCallback
helpviewer_keywords:
- CTaskDialog [MFC], CTaskDialog
- CTaskDialog [MFC], AddCommandControl
- CTaskDialog [MFC], AddRadioButton
- CTaskDialog [MFC], ClickCommandControl
- CTaskDialog [MFC], ClickRadioButton
- CTaskDialog [MFC], DoModal
- CTaskDialog [MFC], GetCommonButtonCount
- CTaskDialog [MFC], GetCommonButtonFlag
- CTaskDialog [MFC], GetCommonButtonId
- CTaskDialog [MFC], GetOptions
- CTaskDialog [MFC], GetSelectedCommandControlID
- CTaskDialog [MFC], GetSelectedRadioButtonID
- CTaskDialog [MFC], GetVerificationCheckboxState
- CTaskDialog [MFC], IsCommandControlEnabled
- CTaskDialog [MFC], IsRadioButtonEnabled
- CTaskDialog [MFC], IsSupported
- CTaskDialog [MFC], LoadCommandControls
- CTaskDialog [MFC], LoadRadioButtons
- CTaskDialog [MFC], NavigateTo
- CTaskDialog [MFC], OnCommandControlClick
- CTaskDialog [MFC], OnCreate
- CTaskDialog [MFC], OnDestroy
- CTaskDialog [MFC], OnExpandButtonClick
- CTaskDialog [MFC], OnHelp
- CTaskDialog [MFC], OnHyperlinkClick
- CTaskDialog [MFC], OnInit
- CTaskDialog [MFC], OnNavigatePage
- CTaskDialog [MFC], OnRadioButtonClick
- CTaskDialog [MFC], OnTimer
- CTaskDialog [MFC], OnVerificationCheckboxClick
- CTaskDialog [MFC], RemoveAllCommandControls
- CTaskDialog [MFC], RemoveAllRadioButtons
- CTaskDialog [MFC], SetCommandControlOptions
- CTaskDialog [MFC], SetCommonButtonOptions
- CTaskDialog [MFC], SetCommonButtons
- CTaskDialog [MFC], SetContent
- CTaskDialog [MFC], SetDefaultCommandControl
- CTaskDialog [MFC], SetDefaultRadioButton
- CTaskDialog [MFC], SetDialogWidth
- CTaskDialog [MFC], SetExpansionArea
- CTaskDialog [MFC], SetFooterIcon
- CTaskDialog [MFC], SetFooterText
- CTaskDialog [MFC], SetMainIcon
- CTaskDialog [MFC], SetMainInstruction
- CTaskDialog [MFC], SetOptions
- CTaskDialog [MFC], SetProgressBarMarquee
- CTaskDialog [MFC], SetProgressBarPosition
- CTaskDialog [MFC], SetProgressBarRange
- CTaskDialog [MFC], SetProgressBarState
- CTaskDialog [MFC], SetRadioButtonOptions
- CTaskDialog [MFC], SetVerificationCheckbox
- CTaskDialog [MFC], SetVerificationCheckboxText
- CTaskDialog [MFC], SetWindowTitle
- CTaskDialog [MFC], ShowDialog
- CTaskDialog [MFC], TaskDialogCallback
ms.assetid: 1991ec98-ae56-4483-958b-233809c8c559
ms.openlocfilehash: 3fd67eed7e80a2e594710df8ae8bc6fd13f0e96c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837674"
---
# <a name="ctaskdialog-class"></a>Klasa obiektu CTaskDialog

Wyskakujące okno dialogowe, które działa jak okno komunikatu, ale może wyświetlić dodatkowe informacje dla użytkownika. `CTaskDialog`Obejmuje również funkcje zbierania informacji od użytkownika.

## <a name="syntax"></a>Składnia

```
class CTaskDialog : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|Nazwa|Opis|
|-|-|
|[Obiektu CTaskDialog:: obiektu CTaskDialog](#ctaskdialog)|Konstruuje `CTaskDialog` obiekt.|

### <a name="methods"></a>Metody

|Nazwa|Opis|
|-|-|
|[Obiektu CTaskDialog:: AddCommandControl](#addcommandcontrol)|Dodaje kontrolkę przycisk polecenia do `CTaskDialog` .|
|[Obiektu CTaskDialog:: AddRadioButton](#addradiobutton)|Dodaje przycisk radiowy do `CTaskDialog` .|
|[Obiektu CTaskDialog:: ClickCommandControl](#clickcommandcontrol)|Program programowo klika kontrolkę przycisk polecenia lub typowy przycisk.|
|[Obiektu CTaskDialog:: ClickRadioButton](#clickradiobutton)|Program programowo klika przycisk radiowy.|
|[Obiektu CTaskDialog::D oModal](#domodal)|Wyświetla `CTaskDialog` .|
|[Obiektu CTaskDialog:: GetCommonButtonCount](#getcommonbuttoncount)|Pobiera liczbę dostępnych wspólnych przycisków.|
|[Obiektu CTaskDialog:: GetCommonButtonFlag](#getcommonbuttonflag)|Konwertuje standardowy przycisk systemu Windows na wspólny typ przycisku skojarzony z `CTaskDialog` klasą.|
|[Obiektu CTaskDialog:: GetCommonButtonId](#getcommonbuttonid)|Konwertuje jeden ze wspólnych typów przycisków skojarzonych z `CTaskDialog` klasą na standardowy przycisk systemu Windows.|
|[Obiektu CTaskDialog:: GetOptions](#getoptions)|Zwraca flagi opcji dla tego elementu `CTaskDialog` .|
|[Obiektu CTaskDialog:: GetSelectedCommandControlID](#getselectedcommandcontrolid)|Zwraca wybraną kontrolkę przycisk polecenia.|
|[Obiektu CTaskDialog:: GetSelectedRadioButtonID](#getselectedradiobuttonid)|Zwraca wybrany przycisk radiowy.|
|[Obiektu CTaskDialog:: GetVerificationCheckboxState](#getverificationcheckboxstate)|Pobiera stan pola wyboru weryfikacji.|
|[Obiektu CTaskDialog:: IsCommandControlEnabled](#iscommandcontrolenabled)|Określa, czy kontrolka przycisku polecenia lub typowy przycisk jest włączony.|
|[Obiektu CTaskDialog:: IsRadioButtonEnabled](#isradiobuttonenabled)|Określa, czy przycisk radiowy jest włączony.|
|[Obiektu CTaskDialog:: issupportd](#issupported)|Określa, czy komputer, na którym działa aplikacja, obsługuje program `CTaskDialog` .|
|[Obiektu CTaskDialog:: LoadCommandControls](#loadcommandcontrols)|Dodaje kontrolki przycisku polecenia przy użyciu danych z tabeli ciągów.|
|[Obiektu CTaskDialog:: LoadRadioButtons](#loadradiobuttons)|Dodaje przyciski radiowe przy użyciu danych z tabeli ciągów.|
|[Obiektu CTaskDialog:: typu NavigateTo](#navigateto)|Przenosi fokus do innego `CTaskDialog` .|
|[Obiektu CTaskDialog:: OnCommandControlClick](#oncommandcontrolclick)|Struktura wywołuje tę metodę, gdy użytkownik kliknie kontrolkę przycisk polecenia.|
|[Obiektu CTaskDialog:: OnCreate](#oncreate)|Struktura wywołuje tę metodę po utworzeniu `CTaskDialog` .|
|[Obiektu CTaskDialog:: OnDestroy](#ondestroy)|Struktura wywołuje tę metodę natychmiast przed zniszczeniem `CTaskDialog` .|
|[Obiektu CTaskDialog:: OnExpandButtonClick](#onexpandbuttonclick)|Struktura wywołuje tę metodę, gdy użytkownik kliknie przycisk rozwinięcia.|
|[Obiektu CTaskDialog:: OnHelp](#onhelp)|Struktura wywołuje tę metodę, gdy użytkownik zażąda pomocy.|
|[Obiektu CTaskDialog:: OnHyperlinkClick](#onhyperlinkclick)|Struktura wywołuje tę metodę, gdy użytkownik kliknie hiperłącze.|
|[Obiektu CTaskDialog:: OnInit](#oninit)|Struktura wywołuje tę metodę, gdy `CTaskDialog` zostanie zainicjowany.|
|[Obiektu CTaskDialog:: OnNavigatePage](#onnavigatepage)|Struktura wywołuje tę metodę, gdy użytkownik przesuwa fokus w odniesieniu do kontrolek w `CTaskDialog` .|
|[Obiektu CTaskDialog:: OnRadioButtonClick](#onradiobuttonclick)|Struktura wywołuje tę metodę, gdy użytkownik wybierze kontrolkę przycisk radiowy.|
|[Obiektu CTaskDialog:: ontimeer](#ontimer)|Struktura wywołuje tę metodę po wygaśnięciu czasomierza.|
|[Obiektu CTaskDialog:: OnVerificationCheckboxClick](#onverificationcheckboxclick)|Struktura wywołuje tę metodę, gdy użytkownik kliknie pole wyboru weryfikacja.|
|[Obiektu CTaskDialog:: RemoveAllCommandControls](#removeallcommandcontrols)|Usuwa wszystkie formanty poleceń z `CTaskDialog` .|
|[Obiektu CTaskDialog:: RemoveAllRadioButtons](#removeallradiobuttons)|Usuwa wszystkie przyciski radiowe z `CTaskDialog` .|
|[Obiektu CTaskDialog:: SetCommandControlOptions](#setcommandcontroloptions)|Aktualizuje kontrolkę przycisk polecenia na `CTaskDialog` .|
|[Obiektu CTaskDialog:: SetCommonButtonOptions](#setcommonbuttonoptions)|Aktualizuje podzestaw wspólnych przycisków do włączenia i wymaga podniesienia uprawnień funkcji kontroli konta użytkownika.|
|[Obiektu CTaskDialog:: SetCommonButtons](#setcommonbuttons)|Dodaje typowe przyciski do `CTaskDialog` .|
|[Obiektu CTaskDialog:: SetContent](#setcontent)|Aktualizuje zawartość `CTaskDialog` .|
|[Obiektu CTaskDialog:: SetDefaultCommandControl](#setdefaultcommandcontrol)|Określa domyślną kontrolkę przycisk polecenia.|
|[Obiektu CTaskDialog:: SetDefaultRadioButton](#setdefaultradiobutton)|Określa domyślny przycisk radiowy.|
|[Obiektu CTaskDialog:: SetDialogWidth](#setdialogwidth)|Dostosowuje szerokość `CTaskDialog` .|
|[Obiektu CTaskDialog:: SetExpansionArea](#setexpansionarea)|Aktualizuje obszar rozwinięcia `CTaskDialog` .|
|[Obiektu CTaskDialog:: SetFooterIcon](#setfootericon)|Aktualizuje ikonę stopki dla `CTaskDialog` .|
|[Obiektu CTaskDialog:: SetFooterText](#setfootertext)|Aktualizuje tekst w stopce `CTaskDialog` .|
|[Obiektu CTaskDialog:: SetMainIcon](#setmainicon)|Aktualizuje główną ikonę `CTaskDialog` .|
|[Obiektu CTaskDialog:: SetMainInstruction](#setmaininstruction)|Aktualizuje główną instrukcję `CTaskDialog` .|
|[Obiektu CTaskDialog:: Set— opcje](#setoptions)|Konfiguruje opcje dla `CTaskDialog` .|
|[Obiektu CTaskDialog:: SetProgressBarMarquee](#setprogressbarmarquee)|Konfiguruje pasek Neon dla `CTaskDialog` i dodaje go do okna dialogowego.|
|[Obiektu CTaskDialog:: SetProgressBarPosition](#setprogressbarposition)|Dostosowuje położenie paska postępu.|
|[Obiektu CTaskDialog:: SetProgressBarRange](#setprogressbarrange)|Dostosowuje zakres paska postępu.|
|[Obiektu CTaskDialog:: SetProgressBarState](#setprogressbarstate)|Ustawia stan paska postępu i wyświetla go w `CTaskDialog` .|
|[Obiektu CTaskDialog:: SetRadioButtonOptions](#setradiobuttonoptions)|Włącza lub wyłącza przycisk radiowy.|
|[Obiektu CTaskDialog:: SetVerificationCheckbox](#setverificationcheckbox)|Ustawia stan zaznaczenia pola wyboru weryfikacji.|
|[Obiektu CTaskDialog:: SetVerificationCheckboxText](#setverificationcheckboxtext)|Ustawia tekst po prawej stronie pola wyboru weryfikacji.|
|[Obiektu CTaskDialog:: SetWindowTitle](#setwindowtitle)|Ustawia tytuł elementu `CTaskDialog` .|
|[Obiektu CTaskDialog:: ShowDialog](#showdialog)|Tworzy i wyświetla `CTaskDialog` .|
|[Obiektu CTaskDialog:: TaskDialogCallback](#taskdialogcallback)|Struktura wywołuje ten element w odpowiedzi na różne komunikaty systemu Windows.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|-|-|
|`m_aButtons`|Tablica kontrolek przycisków poleceń dla `CTaskDialog` .|
|`m_aRadioButtons`|Tablica kontrolek przycisków radiowych `CTaskDialog` .|
|`m_bVerified`|`TRUE` wskazuje, że pole wyboru weryfikacji jest zaznaczone; `FALSE` wskazuje, że nie jest.|
|`m_footerIcon`|Ikona w stopce `CTaskDialog` .|
|`m_hWnd`|Uchwyt okna dla `CTaskDialog` .|
|`m_mainIcon`|Ikona główna `CTaskDialog` .|
|`m_nButtonDisabled`|Maska wskazująca, które z typowych przycisków są wyłączone.|
|`m_nButtonElevation`|Maska wskazująca, które ze wspólnych przycisków wymagają podniesienia uprawnień funkcji Kontrola konta użytkownika.|
|`m_nButtonId`|Identyfikator wybranego formantu przycisku polecenia.|
|`m_nCommonButton`|Maska wskazująca, które typowe przyciski są wyświetlane w `CTaskDialog` .|
|`m_nDefaultCommandControl`|Identyfikator kontrolki przycisku polecenia, która jest wybierana podczas `CTaskDialog` wyświetlania.|
|`m_nDefaultRadioButton`|Identyfikator kontrolki przycisku radiowego, która jest wybierana podczas `CTaskDialog` wyświetlania.|
|`m_nFlags`|Maska wskazująca opcje `CTaskDialog` .|
|`m_nProgressPos`|Bieżąca pozycja paska postępu.  Ta wartość musi należeć `m_nProgressRangeMin` do zakresu od do `m_nProgressRangeMax` .|
|`m_nProgressRangeMax`|Maksymalna wartość paska postępu.|
|`m_nProgressRangeMin`|Minimalna wartość paska postępu.|
|`m_nProgressState`|Stan paska postępu. Aby uzyskać więcej informacji, zobacz [obiektu CTaskDialog:: SetProgressBarState](#setprogressbarstate).|
|`m_nRadioId`|Identyfikator wybranej kontrolki przycisku radiowego.|
|`m_nWidth`|Szerokość `CTaskDialog` w pikselach.|
|`m_strCollapse`|Ciąg wyświetlany po `CTaskDialog` prawej stronie pola rozwijanego, gdy rozwinięte informacje są ukryte.|
|`m_strContent`|Ciąg zawartości `CTaskDialog` .|
|`m_strExpand`|Ciąg wyświetlany po `CTaskDialog` prawej stronie pola rozwijanego, gdy wyświetlane są rozwinięte informacje.|
|`m_strFooter`|Stopka `CTaskDialog` .|
|`m_strInformation`|Rozwinięte informacje dla `CTaskDialog` .|
|`m_strMainInstruction`|Główna instrukcja `CTaskDialog` .|
|`m_strTitle`|Tytuł `CTaskDialog` .|
|`m_strVerification`|Ciąg `CTaskDialog` wyświetlany po prawej stronie pola wyboru weryfikacji.|

## <a name="remarks"></a>Uwagi

`CTaskDialog`Klasa zastępuje standardowe okno komunikatu systemu Windows i ma dodatkowe funkcje, takie jak nowe kontrolki, aby zebrać informacje od użytkownika. Ta klasa znajduje się w bibliotece MFC w programie Visual Studio 2010 i nowszych. `CTaskDialog`Jest dostępny od systemu Windows Vista. W starszych wersjach systemu Windows nie można wyświetlić `CTaskDialog` obiektu. Użyj `CTaskDialog::IsSupported` , aby określić w czasie wykonywania, czy bieżący użytkownik może wyświetlić okno dialogowe zadania. Standardowe okno komunikatu systemu Windows jest nadal obsługiwane.

`CTaskDialog`Jest dostępny tylko w przypadku kompilowania aplikacji przy użyciu biblioteki Unicode.

`CTaskDialog`Ma dwa różne konstruktory. Jeden konstruktor pozwala określić dwa przyciski poleceń i maksymalnie sześć kontrolek zwykłych przycisków. Można dodać więcej przycisków poleceń po utworzeniu `CTaskDialog` . Drugi Konstruktor nie obsługuje żadnych przycisków poleceń, ale można dodać nieograniczoną liczbę kontrolek zwykłych przycisków. Aby uzyskać więcej informacji na temat konstruktorów, zobacz [obiektu CTaskDialog:: obiektu CTaskDialog](#ctaskdialog).

Na poniższej ilustracji przedstawiono przykład `CTaskDialog` ilustrujący lokalizację niektórych kontrolek.

![Przykład obiektu CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "Przykład obiektu CTaskDialog") <br/>
Przykład obiektu CTaskDialog

## <a name="requirements"></a>Wymagania

**Minimalny wymagany system operacyjny:** System Windows Vista

**Nagłówek:** afxtaskdialog. h

## <a name="ctaskdialogaddcommandcontrol"></a><a name="addcommandcontrol"></a> Obiektu CTaskDialog:: AddCommandControl

Dodaje nową kontrolkę przycisk polecenia do `CTaskDialog` .

```cpp
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
podczas Numer identyfikacyjny kontrolki polecenia.

*strCaption*<br/>
podczas Ciąg `CTaskDialog` wyświetlany użytkownikowi. Użyj tego ciągu, aby wyjaśnić przeznaczenie polecenia.

*bEnabled*<br/>
podczas Parametr logiczny, który wskazuje, czy przycisk Nowy jest włączony, czy wyłączony.

*bRequiresElevation*<br/>
podczas Parametr logiczny, który wskazuje, czy polecenie wymaga podniesienia uprawnień.

### <a name="remarks"></a>Uwagi

`CTaskDialog Class`Może wyświetlać nieograniczoną liczbę kontrolek przycisków poleceń. Jeśli jednak w `CTaskDialog` formancie zostanie wyświetlony dowolny przycisk polecenia, będzie można wyświetlić maksymalnie sześć przycisków. Jeśli `CTaskDialog` nie ma kontrolek przycisk polecenia, może wyświetlić nieograniczoną liczbę przycisków.

Gdy użytkownik wybierze kontrolkę przycisk polecenia, zostanie `CTaskDialog` ZAMKNIĘTA. Jeśli aplikacja wyświetli okno dialogowe przy użyciu [obiektu CTaskDialog::D omodal](#domodal), `DoModal` zwraca *nCommandControlID* zaznaczonej kontrolki przycisk polecenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogaddradiobutton"></a><a name="addradiobutton"></a> Obiektu CTaskDialog:: AddRadioButton

Dodaje przycisk radiowy do `CTaskDialog` .

```cpp
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
podczas Numer identyfikacyjny przycisku radiowego.

*strCaption*<br/>
podczas Ciąg `CTaskDialog` wyświetlany obok przycisku radiowego.

*bEnabled*<br/>
podczas Parametr logiczny, który wskazuje, czy przycisk radiowy jest włączony.

### <a name="remarks"></a>Uwagi

Przyciski radiowe dla [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) umożliwiają zbieranie informacji od użytkownika. Użyj funkcji [obiektu CTaskDialog:: GetSelectedRadioButtonID](#getselectedradiobuttonid) , aby określić, który przycisk radiowy jest wybrany.

Nie `CTaskDialog` wymaga, aby parametry *nRadioButtonID* były unikatowe dla każdego przycisku radiowego. Jednak może wystąpić nieoczekiwane zachowanie, jeśli nie zostanie użyty unikatowy identyfikator dla każdego przycisku radiowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogclickcommandcontrol"></a><a name="clickcommandcontrol"></a> Obiektu CTaskDialog:: ClickCommandControl

Program programowo klika kontrolkę przycisk polecenia lub typowy przycisk.

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
podczas Identyfikator polecenia kontrolki do kliknięcia.

### <a name="remarks"></a>Uwagi

Ta metoda generuje TDM_CLICK_BUTTON komunikatów systemu Windows.

## <a name="ctaskdialogclickradiobutton"></a><a name="clickradiobutton"></a> Obiektu CTaskDialog:: ClickRadioButton

Program programowo klika przycisk radiowy.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
podczas Identyfikator przycisku radiowego, który ma zostać kliknięty.

### <a name="remarks"></a>Uwagi

Ta metoda generuje TDM_CLICK_RADIO_BUTTON komunikatów systemu Windows.

## <a name="ctaskdialogctaskdialog"></a><a name="ctaskdialog"></a> Obiektu CTaskDialog:: obiektu CTaskDialog

Tworzy wystąpienie [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

```
CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nCommonButtons = TDCBF_OK_BUTTON | TDCBF_CANCEL_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));

CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>Parametry

*strContent*<br/>
podczas Ciąg, który ma być używany dla zawartości `CTaskDialog` .

*strMainInstruction*<br/>
podczas Główna instrukcja `CTaskDialog` .

*strTitle*<br/>
podczas Tytuł `CTaskDialog` .

*nCommonButtons*<br/>
podczas Maska typowych przycisków, które mają zostać dodane do `CTaskDialog` .

*nTaskDialogOptions*<br/>
podczas Zestaw opcji do użycia dla `CTaskDialog` .

*strFooter*<br/>
podczas Ciąg, który ma być używany jako stopka.

*nIDCommandControlsFirst*<br/>
podczas Identyfikator ciągu pierwszego polecenia.

*nIDCommandControlsLast*<br/>
podczas Identyfikator ciągu ostatniego polecenia.

### <a name="remarks"></a>Uwagi

Istnieją dwa sposoby dodawania `CTaskDialog` do aplikacji. Pierwszym sposobem jest użycie jednego z konstruktorów w celu utworzenia `CTaskDialog` i wyświetlenia go przy użyciu [obiektu ctaskdialog::D omodal](#domodal). Drugi sposób polega na użyciu funkcji statycznej [obiektu CTaskDialog:: ShowDialog](#showdialog), która umożliwia wyświetlenie `CTaskDialog` bez jawnego tworzenia `CTaskDialog` obiektu.

Drugi Konstruktor tworzy kontrolki przycisk polecenia przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów zawiera kilka ciągów ze skojarzonymi identyfikatorami ciągów. Ta metoda dodaje kontrolkę przycisk polecenia dla każdego prawidłowego wpisu w tabeli ciągów między *nIDCommandControlsFirst* i *nCommandControlsLast*włącznie. Dla tych kontrolek przycisków poleceń ciąg w tabeli ciągów jest podpisem kontrolki, a IDENTYFIKATORem ciągu jest identyfikator formantu.

Aby uzyskać listę prawidłowych opcji, zobacz [obiektu CTaskDialog:: SetOptions](#setoptions) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogdomodal"></a><a name="domodal"></a> Obiektu CTaskDialog::D oModal

Pokazuje `CTaskDialog` i sprawia, że jest modalny.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parametry

*hParent*<br/>
podczas Okno nadrzędne dla `CTaskDialog` .

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która odnosi się do zaznaczenia dokonanego przez użytkownika.

### <a name="remarks"></a>Uwagi

Wyświetla to wystąpienie [obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Aplikacja czeka, aż użytkownik zamknie okno dialogowe.

`CTaskDialog`Zamyka się, gdy użytkownik wybierze wspólny przycisk, formant linku polecenia lub zamknie `CTaskDialog` . Wartość zwracana jest identyfikatorem, który wskazuje, jak użytkownik zamknął okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetcommonbuttoncount"></a><a name="getcommonbuttoncount"></a> Obiektu CTaskDialog:: GetCommonButtonCount

Pobiera liczbę typowych przycisków.

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba dostępnych wspólnych przycisków.

### <a name="remarks"></a>Uwagi

Typowe przyciski są domyślnymi przyciskami dostarczanymi do [obiektu CTaskDialog:: obiektu CTaskDialog](#ctaskdialog). [Klasa obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) Wyświetla przyciski u dołu okna dialogowego.

Lista wyliczonych przycisków jest dostępna w CommCtrl. h.

## <a name="ctaskdialoggetcommonbuttonflag"></a><a name="getcommonbuttonflag"></a> Obiektu CTaskDialog:: GetCommonButtonFlag

Konwertuje standardowy przycisk systemu Windows na wspólny typ przycisku skojarzony z [klasą obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>Parametry

*nButtonId*<br/>
podczas Wartość standardowego przycisku systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wartość odpowiadającego `CTaskDialog` przycisku wspólnego. Jeśli nie ma odpowiedniego przycisku wspólnego, ta metoda zwraca 0.

## <a name="ctaskdialoggetcommonbuttonid"></a><a name="getcommonbuttonid"></a> Obiektu CTaskDialog:: GetCommonButtonId

Konwertuje jeden ze wspólnych typów przycisków skojarzonych z [klasą obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) na standardowy przycisk systemu Windows.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>Parametry

*nFlag*<br/>
podczas Wspólny typ przycisku skojarzony z `CTaskDialog` klasą.

### <a name="return-value"></a>Wartość zwracana

Wartość odpowiadającego standardowego przycisku systemu Windows. Jeśli nie ma odpowiedniego przycisku systemu Windows, metoda zwróci wartość 0.

## <a name="ctaskdialoggetoptions"></a><a name="getoptions"></a> Obiektu CTaskDialog:: GetOptions

Zwraca flagi opcji dla tego elementu `CTaskDialog` .

```
int GetOptions() const;
```

### <a name="return-value"></a>Wartość zwracana

Flagi dla elementu `CTaskDialog` .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat opcji dostępnych dla [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md), zobacz [obiektu CTaskDialog:: SetOptions](#setoptions).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetselectedcommandcontrolid"></a><a name="getselectedcommandcontrolid"></a> Obiektu CTaskDialog:: GetSelectedCommandControlID

Zwraca wybraną kontrolkę przycisk polecenia.

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator aktualnie zaznaczonej kontrolki przycisku polecenia.

### <a name="remarks"></a>Uwagi

Nie trzeba używać tej metody do pobrania identyfikatora przycisku polecenia wybranego przez użytkownika. Ten identyfikator jest zwracany przez jedną z [obiektu CTaskDialog::D omodal](#domodal) lub [obiektu CTaskDialog:: ShowDialog](#showdialog).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialoggetselectedradiobuttonid"></a><a name="getselectedradiobuttonid"></a> Obiektu CTaskDialog:: GetSelectedRadioButtonID

Zwraca wybrany przycisk radiowy.

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator wybranego przycisku radiowego.

### <a name="remarks"></a>Uwagi

Możesz użyć tej metody, gdy użytkownik zamknie okno dialogowe, aby pobrać wybrany przycisk radiowy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialoggetverificationcheckboxstate"></a><a name="getverificationcheckboxstate"></a> Obiektu CTaskDialog:: GetVerificationCheckboxState

Pobiera stan pola wyboru weryfikacji.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli pole wyboru jest zaznaczone, FAŁSZ, jeśli nie jest.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogiscommandcontrolenabled"></a><a name="iscommandcontrolenabled"></a> Obiektu CTaskDialog:: IsCommandControlEnabled

Określa, czy kontrolka przycisku polecenia lub przycisk jest włączony.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
podczas Identyfikator kontrolki przycisku polecenia lub przycisku do przetestowania.

### <a name="return-value"></a>Wartość zwracana

TRUE, Jeśli kontrolka jest włączona, wartość FALSE, jeśli nie jest.

### <a name="remarks"></a>Uwagi

Za pomocą tej metody można określić dostępność obu kontrolek przycisków poleceń i typowych przycisków `CTaskDialog` klasy *.

Jeśli *nCommandControlID* nie jest prawidłowym identyfikatorem dla przycisku wspólnego `CTaskDialog` lub kontrolki przycisku polecenia, ta metoda zgłasza wyjątek.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogisradiobuttonenabled"></a><a name="isradiobuttonenabled"></a> Obiektu CTaskDialog:: IsRadioButtonEnabled

Określa, czy przycisk radiowy jest włączony.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
podczas Identyfikator przycisku radiowego do przetestowania.

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli przycisk radiowy jest włączony, wartość FALSE, jeśli nie jest.

### <a name="remarks"></a>Uwagi

Jeśli *nRadioButtonID* nie jest prawidłowym identyfikatorem przycisku radiowego, ta metoda zgłasza wyjątek.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogissupported"></a><a name="issupported"></a> Obiektu CTaskDialog:: issupportd

Określa, czy komputer, na którym działa aplikacja, obsługuje program `CTaskDialog` .

```
static BOOL IsSupported();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli komputer obsługuje `CTaskDialog` ; W przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji, aby określić w czasie wykonywania, jeśli komputer, na którym działa aplikacja, obsługuje `CTaskDialog` klasę. Jeśli komputer nie obsługuje programu `CTaskDialog` , należy podać inną metodę komunikacji z informacjami dla użytkownika. Aplikacja ulegnie awarii, jeśli podejmie próbę użycia `CTaskDialog` na komputerze, który nie obsługuje `CTaskDialog` klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogloadcommandcontrols"></a><a name="loadcommandcontrols"></a> Obiektu CTaskDialog:: LoadCommandControls

Dodaje kontrolki przycisku polecenia przy użyciu danych z tabeli ciągów.

```cpp
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>Parametry

*nIDCommandControlsFirst*<br/>
podczas Identyfikator ciągu pierwszego polecenia.

*nIDCommandControlsLast*<br/>
podczas Identyfikator ciągu ostatniego polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy formanty przycisków poleceń przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów zawiera kilka ciągów ze skojarzonymi identyfikatorami ciągów. Nowe kontrolki przycisków poleceń dodawane za pomocą tej metody Użyj ciągu dla podpisu kontrolki i identyfikatora ciągu dla identyfikatora formantu. Wybrany zakres ciągów jest dostarczany przez *nIDCommandControlsFirst* i *nCommandControlsLast*włącznie. Jeśli w zakresie istnieje pusty wpis, metoda nie dodaje kontrolki przycisk polecenia dla tego wpisu.

Domyślnie nowe formanty przycisków poleceń są włączone i nie wymagają podniesienia uprawnień.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogloadradiobuttons"></a><a name="loadradiobuttons"></a> Obiektu CTaskDialog:: LoadRadioButtons

Dodaje kontrolki przycisku radiowego za pomocą danych z tabeli ciągów.

```cpp
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>Parametry

*nIDRadioButtonsFirst*<br/>
podczas Identyfikator ciągu pierwszego przycisku radiowego.

*nIDRadioButtonsLast*<br/>
podczas Identyfikator ciągu ostatniego przycisku radiowego.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy przyciski radiowe przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów zawiera kilka ciągów ze skojarzonymi identyfikatorami ciągów. Nowe przyciski radiowe dodane przy użyciu tej metody używają ciągu dla napisu przycisku radiowego i identyfikatora ciągu dla identyfikatora przycisku radiowego. Wybrany zakres ciągów jest dostarczany przez *nIDRadioButtonsFirst* i *nRadioButtonsLast*włącznie. Jeśli w zakresie istnieje pusty wpis, metoda nie dodaje przycisku radiowego dla tego wpisu.

Domyślnie nowe przyciski radiowe są włączone.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialognavigateto"></a><a name="navigateto"></a> Obiektu CTaskDialog:: typu NavigateTo

Przenosi fokus do innego `CTaskDialog` .

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>Parametry

*oTaskDialog*<br/>
podczas , `CTaskDialog` Który odbiera fokus.

### <a name="remarks"></a>Uwagi

Ta metoda ukrywa bieżącą, `CTaskDialog` gdy wyświetla *oTaskDialog*. *OTaskDialog* jest wyświetlany w tej samej lokalizacji co bieżący `CTaskDialog` .

## <a name="ctaskdialogoncommandcontrolclick"></a><a name="oncommandcontrolclick"></a> Obiektu CTaskDialog:: OnCommandControlClick

Struktura wywołuje tę metodę, gdy użytkownik kliknie kontrolkę przycisk polecenia.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
podczas Identyfikator kontrolki przycisku polecenia, która została wybrana przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogoncreate"></a><a name="oncreate"></a> Obiektu CTaskDialog:: OnCreate

Struktura wywołuje tę metodę po utworzeniu `CTaskDialog` .

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogondestroy"></a><a name="ondestroy"></a> Obiektu CTaskDialog:: OnDestroy

Struktura wywołuje tę metodę natychmiast przed zniszczeniem `CTaskDialog` .

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogonexpandbuttonclick"></a><a name="onexpandbuttonclick"></a> Obiektu CTaskDialog:: OnExpandButtonClick

Struktura wywołuje tę metodę, gdy użytkownik kliknie przycisk rozwinięcia.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>Parametry

*bExpanded*<br/>
podczas Wartość różna od zera wskazuje dodatkowe informacje, które są wyświetlane. wartość 0 oznacza ukrycie dodatkowych informacji.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogonhelp"></a><a name="onhelp"></a> Obiektu CTaskDialog:: OnHelp

Struktura wywołuje tę metodę, gdy użytkownik zażąda pomocy.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogonhyperlinkclick"></a><a name="onhyperlinkclick"></a> Obiektu CTaskDialog:: OnHyperlinkClick

Struktura wywołuje tę metodę, gdy użytkownik kliknie hiperłącze.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>Parametry

*strHref*<br/>
podczas Ciąg, który reprezentuje hiperlink.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje interfejs [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) przed zwróceniem S_OK.

Zastąp tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogoninit"></a><a name="oninit"></a> Obiektu CTaskDialog:: OnInit

Struktura wywołuje tę metodę, gdy `CTaskDialog` zostanie zainicjowany.

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogonnavigatepage"></a><a name="onnavigatepage"></a> Obiektu CTaskDialog:: OnNavigatePage

Struktura wywołuje tę metodę w odpowiedzi na metodę [obiektu CTaskDialog:: typu NavigateTo](#navigateto) .

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogonradiobuttonclick"></a><a name="onradiobuttonclick"></a> Obiektu CTaskDialog:: OnRadioButtonClick

Struktura wywołuje tę metodę, gdy użytkownik wybierze kontrolkę przycisk radiowy.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
podczas Identyfikator kontrolki przycisku radiowego klikniętej przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogontimer"></a><a name="ontimer"></a> Obiektu CTaskDialog:: ontimeer

Struktura wywołuje tę metodę po wygaśnięciu czasomierza.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>Parametry

*lTime*<br/>
podczas Czas (w milisekundach) od `CTaskDialog` utworzenia lub czasomierz został zresetowany.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogonverificationcheckboxclick"></a><a name="onverificationcheckboxclick"></a> Obiektu CTaskDialog:: OnVerificationCheckboxClick

Struktura wywołuje tę metodę, gdy użytkownik kliknie pole wyboru weryfikacja.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>Parametry

*bChecked*<br/>
podczas Wartość TRUE oznacza, że zaznaczone jest pole wyboru weryfikacja; Wartość FALSE wskazuje, że nie jest.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogremoveallcommandcontrols"></a><a name="removeallcommandcontrols"></a> Obiektu CTaskDialog:: RemoveAllCommandControls

Usuwa wszystkie formanty przycisków poleceń z `CTaskDialog` .

```cpp
void RemoveAllCommandControls();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogremoveallradiobuttons"></a><a name="removeallradiobuttons"></a> Obiektu CTaskDialog:: RemoveAllRadioButtons

Usuwa wszystkie przyciski radiowe z `CTaskDialog` .

```cpp
void RemoveAllRadioButtons();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetcommandcontroloptions"></a><a name="setcommandcontroloptions"></a> Obiektu CTaskDialog:: SetCommandControlOptions

Aktualizuje kontrolkę przycisk polecenia na `CTaskDialog` .

```cpp
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
podczas Identyfikator kontrolki polecenia do zaktualizowania.

*bEnabled*<br/>
podczas Parametr logiczny, który wskazuje, czy określony formant przycisku polecenia jest włączony lub wyłączony.

*bRequiresElevation*<br/>
podczas Parametr logiczny, który wskazuje, czy określony formant przycisku polecenia wymaga podniesienia uprawnień.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby zmienić, czy kontrolka przycisku polecenia jest włączona, czy wymaga podniesienia uprawnień po dodaniu do `CTaskDialog` klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetcommonbuttonoptions"></a><a name="setcommonbuttonoptions"></a> Obiektu CTaskDialog:: SetCommonButtonOptions

Aktualizuje podzbiór wspólnych przycisków do włączenia i wymaga podniesienia uprawnień funkcji kontroli konta użytkownika.

```cpp
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parametry

*nDisabledButtonMask*<br/>
podczas Maska dla typowych przycisków, które mają zostać wyłączone.

*nElevationButtonMask*<br/>
podczas Maska dla typowych przycisków, które wymagają podniesienia uprawnień.

### <a name="remarks"></a>Uwagi

Można ustawić typowe przyciski dostępne dla wystąpienia [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) , używając konstruktora [obiektu CTaskDialog:: obiektu CTaskDialog](#ctaskdialog) i metody [obiektu CTaskDialog:: SetCommonButtons](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions` nie obsługuje dodawania nowych wspólnych przycisków.

W przypadku użycia tej metody w celu wyłączenia lub podniesienia poziomu wspólnego przycisku, który nie jest dostępny dla tego elementu `CTaskDialog` , ta metoda zgłasza wyjątek za [ENSURE](diagnostic-services.md#ensure) pomocą makra.

Ta metoda włącza dowolny przycisk, który jest dostępny dla programu, `CTaskDialog` ale nie znajduje się w *nDisabledButtonMask*, nawet jeśli został wcześniej wyłączony. Ta metoda traktuje podniesienie uprawnień w podobny sposób: rejestruje typowe przyciski jako niewymagające podniesienia uprawnień, jeśli wspólny przycisk jest dostępny, ale nie jest uwzględniony w *nElevationButtonMask*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcommonbuttons"></a><a name="setcommonbuttons"></a> Obiektu CTaskDialog:: SetCommonButtons

Dodaje typowe przyciski do `CTaskDialog` .

```cpp
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parametry

*nButtonMask*<br/>
podczas Maska przycisków, które mają zostać dodane do `CTaskDialog` .

*nDisabledButtonMask*<br/>
podczas Maska przycisków do wyłączenia.

*nElevationButtonMask*<br/>
podczas Maska przycisków, które wymagają podniesienia uprawnień.

### <a name="remarks"></a>Uwagi

Nie można wywołać tej metody po utworzeniu okna wyświetlania dla tego wystąpienia `CTaskDialog` klasy. Jeśli to zrobisz, ta metoda zgłasza wyjątek.

Przyciski wskazywane przez *nButtonMask* zastępują wszystkie typowe przyciski, które zostały wcześniej dodane do `CTaskDialog` . Dostępne są tylko przyciski wskazane w *nButtonMask* .

Jeśli *nDisabledButtonMask* lub *nElevationButtonMask* zawierają przycisk, którego nie ma w *nButtonMask*, ta metoda zgłasza wyjątek przy użyciu makra [upewniania](diagnostic-services.md#ensure) się.

Domyślnie wszystkie popularne przyciski są włączone i nie wymagają podniesienia uprawnień.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcontent"></a><a name="setcontent"></a> Obiektu CTaskDialog:: SetContent

Aktualizuje zawartość `CTaskDialog` .

```cpp
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>Parametry

*strContent*<br/>
podczas Ciąg, który ma być wyświetlany użytkownikowi.

### <a name="remarks"></a>Uwagi

Zawartość `CTaskDialog` klasy jest tekstem wyświetlanym dla użytkownika w sekcji głównej okna dialogowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetdefaultcommandcontrol"></a><a name="setdefaultcommandcontrol"></a> Obiektu CTaskDialog:: SetDefaultCommandControl

Określa domyślną kontrolkę przycisk polecenia.

```cpp
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
podczas Identyfikator kontrolki przycisku polecenia, która ma być wartością domyślną.

### <a name="remarks"></a>Uwagi

Domyślnym formantem przycisku polecenia jest formant, który jest wybierany podczas `CTaskDialog` pierwszego wyświetlania użytkownikowi.

Ta metoda zgłasza wyjątek, jeśli nie może znaleźć kontrolki przycisku polecenia określonej przez *nCommandControlID*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetdefaultradiobutton"></a><a name="setdefaultradiobutton"></a> Obiektu CTaskDialog:: SetDefaultRadioButton

Określa domyślny przycisk radiowy.

```cpp
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
podczas Identyfikator przycisku radiowego, który ma być wartością domyślną.

### <a name="remarks"></a>Uwagi

Domyślny przycisk radiowy jest przycisk, który jest wybierany podczas `CTaskDialog` pierwszego wyświetlania użytkownikowi.

Ta metoda zgłasza wyjątek, jeśli nie może znaleźć przycisku radiowego określonego przez *nRadioButtonID*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetdialogwidth"></a><a name="setdialogwidth"></a> Obiektu CTaskDialog:: SetDialogWidth

Dostosowuje szerokość `CTaskDialog` .

```cpp
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
podczas Szerokość okna dialogowego (w pikselach).

### <a name="remarks"></a>Uwagi

Parametr *nWidth* musi być większy lub równy 0. W przeciwnym razie ta metoda zgłasza wyjątek.

Jeśli *nWidth* jest ustawiona na 0, ta metoda ustawia domyślny rozmiar okna dialogowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetexpansionarea"></a><a name="setexpansionarea"></a> Obiektu CTaskDialog:: SetExpansionArea

Aktualizuje obszar rozwinięcia `CTaskDialog` .

```cpp
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>Parametry

*strExpandedInformation*<br/>
podczas Ciąg `CTaskDialog` wyświetlany w głównej treści okna dialogowego, gdy użytkownik kliknie przycisk rozwinięcia.

*strCollapsedLabel*<br/>
podczas Ciąg `CTaskDialog` wyświetlany obok przycisku rozwinięcia, gdy rozwinięty obszar jest zwinięty.

*strExpandedLabel*<br/>
podczas Ciąg `CTaskDialog` wyświetlany obok przycisku rozwinięcia po wyświetleniu rozwiniętego obszaru.

### <a name="remarks"></a>Uwagi

Obszar rozszerzania `CTaskDialog` klasy umożliwia użytkownikowi podanie dodatkowych informacji. Obszar rozszerzania znajduje się w głównej części `CTaskDialog` , znajdującej się bezpośrednio pod tytułem i ciągiem zawartości.

Po `CTaskDialog` pierwszym wyświetleniu nie są wyświetlane rozwinięte informacje i umieszczane `strCollapsedLabel` obok przycisku rozwinięcia. Gdy użytkownik kliknie przycisk rozwinięcia, `CTaskDialog` wyświetla *strExpandedInformation* i zmienia etykietę na *strExpandedLabel*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootericon"></a><a name="setfootericon"></a> Obiektu CTaskDialog:: SetFooterIcon

Aktualizuje ikonę stopki `CTaskDialog` .

```cpp
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>Parametry

*hFooterIcon*<br/>
podczas Nowa ikona dla `CTaskDialog` .

*lpszFooterIcon*<br/>
podczas Nowa ikona dla `CTaskDialog` .

### <a name="remarks"></a>Uwagi

Ikona stopki jest wyświetlana u dołu [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Może mieć skojarzoną stopkę tekstu. Tekst stopki można zmienić za pomocą [obiektu CTaskDialog:: SetFooterText](#setfootertext).

Ta metoda zgłasza wyjątek [z makrem](diagnostic-services.md#ensure) , jeśli `CTaskDialog` jest wyświetlana lub parametr wejściowy ma wartość null.

`CTaskDialog`Może akceptować tylko `HICON` ikonę lub `LPCWSTR` jako stopkę. Jest to konfigurowane przez ustawienie opcji TDF_USE_HICON_FOOTER w konstruktorze lub [obiektu CTaskDialog:: SetOptions](#setoptions). Domyślnie program `CTaskDialog` jest skonfigurowany do używania `LPCWSTR` jako typ danych wejściowych dla ikony stopki. Ta metoda generuje wyjątek, jeśli spróbujesz ustawić ikonę przy użyciu niewłaściwego typu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootertext"></a><a name="setfootertext"></a> Obiektu CTaskDialog:: SetFooterText

Aktualizuje tekst w stopce `CTaskDialog` .

```cpp
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>Parametry

*strFooterText*<br/>
podczas Nowy tekst stopki.

### <a name="remarks"></a>Uwagi

Ikona stopki pojawia się obok tekstu stopki w dolnej części okna `CTaskDialog` . Ikonę stopki można zmienić za pomocą [obiektu CTaskDialog:: SetFooterIcon](#setfootericon).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmainicon"></a><a name="setmainicon"></a> Obiektu CTaskDialog:: SetMainIcon

Aktualizuje główną ikonę `CTaskDialog` .

```cpp
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>Parametry

*hMainIcon*<br/>
podczas Nowa ikona.

*lpszMainIcon*<br/>
podczas Nowa ikona.

### <a name="remarks"></a>Uwagi

Ta metoda zgłasza wyjątek [z makrem](diagnostic-services.md#ensure) , jeśli `CTaskDialog` jest wyświetlana lub parametr wejściowy ma wartość null.

`CTaskDialog`Można zaakceptować tylko `HICON` `LPCWSTR` ikonę lub jako główną. Można to skonfigurować przez ustawienie opcji TDF_USE_HICON_MAIN w konstruktorze lub w metodzie [obiektu CTaskDialog:: SetOptions](#setoptions) . Domyślnie program `CTaskDialog` jest skonfigurowany do używania `LPCWSTR` jako typ danych wejściowych dla ikony głównej. Ta metoda generuje wyjątek, jeśli spróbujesz ustawić ikonę przy użyciu niewłaściwego typu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmaininstruction"></a><a name="setmaininstruction"></a> Obiektu CTaskDialog:: SetMainInstruction

Aktualizuje główną instrukcję `CTaskDialog` .

```cpp
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>Parametry

*strInstructions*<br/>
podczas Nowa główna instrukcja.

### <a name="remarks"></a>Uwagi

Główną instrukcją `CTaskDialog` klasy jest tekst wyświetlany użytkownikowi przy użyciu dużej pogrubionej czcionki. Znajduje się w oknie dialogowym pod paskiem tytułu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetoptions"></a><a name="setoptions"></a> Obiektu CTaskDialog:: Set— opcje

Konfiguruje opcje dla `CTaskDialog` .

```cpp
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>Parametry

*nOptionFlag*<br/>
podczas Zestaw flag do użycia dla `CTaskDialog` .

### <a name="remarks"></a>Uwagi

Ta metoda czyści wszystkie bieżące opcje dla `CTaskDialog` . Aby zachować bieżące opcje, należy pobrać je najpierw z [obiektu CTaskDialog:: GetOptions](#getoptions) i połączyć je z opcjami, które chcesz ustawić.

Poniższa tabela zawiera listę wszystkich prawidłowych opcji.

|Nazwa|Opis|
|-|-|
|TDF_ENABLE_HYPERLINKS|Włącza hiperłącza w `CTaskDialog` .|
|TDF_USE_HICON_MAIN|Konfiguruje, `CTaskDialog` Aby używać `HICON` dla głównej ikony. Alternatywą jest użycie elementu `LPCWSTR` .|
|TDF_USE_HICON_FOOTER|Konfiguruje, `CTaskDialog` Aby używać `HICON` dla ikony stopki. Alternatywą jest użycie elementu `LPCWSTR` .|
|TDF_ALLOW_DIALOG_CANCELLATION|Umożliwia użytkownikowi zamknięcie programu przy `CTaskDialog` użyciu klawiatury lub ikony w prawym górnym rogu okna dialogowego, nawet jeśli przycisk **Anuluj** nie jest włączony. Jeśli ta flaga nie jest ustawiona i przycisk **Anuluj** nie jest włączony, użytkownik nie może zamknąć okna dialogowego przy użyciu klawiszy Alt + F4, klawisza ucieczki ani przycisku zamknięcia paska tytułu.|
|TDF_USE_COMMAND_LINKS|Konfiguruje `CTaskDialog` kontrolki przycisków poleceń do użycia.|
|TDF_USE_COMMAND_LINKS_NO_ICON|Konfiguruje `CTaskDialog` kontrolki do używania przycisków poleceń bez wyświetlania ikony obok formantu. TDF_USE_COMMAND_LINKS zastąpień TDF_USE_COMMAND_LINKS_NO_ICON.|
|TDF_EXPAND_FOOTER_AREA|Wskazuje, że obszar rozszerzania jest obecnie rozwinięty.|
|TDF_EXPANDED_BY_DEFAULT|Określa, czy obszar rozszerzania jest domyślnie rozwinięty.|
|TDF_VERIFICATION_FLAG_CHECKED|Wskazuje, że pole wyboru weryfikacja jest aktualnie zaznaczone.|
|TDF_SHOW_PROGRESS_BAR|Konfiguruje `CTaskDialog` Wyświetlanie paska postępu.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|Konfiguruje pasek postępu jako pasek postępu neonu. Jeśli włączysz tę opcję, musisz ustawić TDF_SHOW_PROGRESS_BAR tak, aby miało oczekiwane zachowanie.|
|TDF_CALLBACK_TIMER|Wskazuje, że `CTaskDialog` Interwał wywołania zwrotnego jest ustawiony na około 200 milisekund.|
|TDF_POSITION_RELATIVE_TO_WINDOW|Konfiguruje, `CTaskDialog` aby były wyśrodkowane względem okna nadrzędnego. Jeśli ta flaga nie jest włączona, `CTaskDialog` jest wyśrodkowana względem monitora.|
|TDF_RTL_LAYOUT|Konfiguruje `CTaskDialog` układ do czytania od prawej do lewej.|
|TDF_NO_DEFAULT_RADIO_BUTTON|Wskazuje, że przycisk radiowy nie jest zaznaczony, gdy `CTaskDialog` pojawia się.|
|TDF_CAN_BE_MINIMIZED|Umożliwia użytkownikowi zminimalizowanie `CTaskDialog` . Aby zapewnić obsługę tej opcji, `CTaskDialog` nie może być modalny. MFC nie obsługuje tej opcji, ponieważ MFC nie obsługuje niemodalnych `CTaskDialog` .|

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetprogressbarmarquee"></a><a name="setprogressbarmarquee"></a> Obiektu CTaskDialog:: SetProgressBarMarquee

Konfiguruje pasek Neon dla `CTaskDialog` i dodaje go do okna dialogowego.

```cpp
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>Parametry

*bEnabled*<br/>
podczas PRAWDA, aby włączyć pasek neonu; Wartość FALSE powoduje wyłączenie paska neonu i usunięcie go z `CTaskDialog` .

*nMarqueeSpeed*<br/>
podczas Liczba całkowita wskazująca szybkość paska neonu.

### <a name="remarks"></a>Uwagi

Pasek neonu jest wyświetlany pod głównym tekstem `CTaskDialog` klasy.

Użyj *nMarqueeSpeed* , aby ustawić szybkość paska neonu; większe wartości oznaczają wolną szybkość. Wartość 0 dla *nMarqueeSpeed* sprawia, że pasek neonu przesuwa się przy domyślnej szybkości dla systemu Windows.

Ta metoda zgłasza wyjątek z warunkiem [zagwarantowania](diagnostic-services.md#ensure) , że wartość *nMarqueeSpeed* jest mniejsza od 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarposition"></a><a name="setprogressbarposition"></a> Obiektu CTaskDialog:: SetProgressBarPosition

Dostosowuje położenie paska postępu.

```cpp
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parametry

*nProgressPos*<br/>
podczas Pozycja paska postępu.

### <a name="remarks"></a>Uwagi

Ta metoda zgłasza wyjątek [z makrem](diagnostic-services.md#ensure) "If", jeśli *nProgressPos* nie znajduje się w zakresie paska postępu. Zakres paska postępu można zmienić za pomocą [obiektu CTaskDialog:: SetProgressBarRange](#setprogressbarrange).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarrange"></a><a name="setprogressbarrange"></a> Obiektu CTaskDialog:: SetProgressBarRange

Dostosowuje zakres paska postępu.

```cpp
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parametry

*nRangeMin*<br/>
podczas Dolna granica paska postępu.

*nRangeMax*<br/>
podczas Górna granica paska postępu.

### <a name="remarks"></a>Uwagi

Pozycja paska postępu jest względna w stosunku do *nRangeMin* i *nRangeMax*. Na przykład jeśli *nRangeMin* jest 50 i *nRangeMax* is 100, pozycja 75 jest w połowie na pasku postępu. Użyj [obiektu CTaskDialog:: SetProgressBarPosition](#setprogressbarposition) , aby ustawić pozycję paska postępu.

Aby wyświetlić pasek postępu, opcja TDF_SHOW_PROGRESS_BAR musi być włączona, a TDF_SHOW_MARQUEE_PROGRESS_BAR nie może być włączona. Ta metoda automatycznie ustawia TDF_SHOW_PROGRESS_BAR i czyści TDF_SHOW_MARQUEE_PROGRESS_BAR. Użyj [obiektu CTaskDialog:: SetOptions](#setoptions) , aby ręcznie zmienić opcje dla tego wystąpienia [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

Ta metoda zgłasza wyjątek [z makrem](diagnostic-services.md#ensure) "If", jeśli *nRangeMin* nie jest mniejsza niż *nRangeMax*. Ta metoda zgłasza również wyjątek, jeśli `CTaskDialog` jest już wyświetlany i ma pasek postępu neonu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarstate"></a><a name="setprogressbarstate"></a> Obiektu CTaskDialog:: SetProgressBarState

Ustawia stan paska postępu i wyświetla go w `CTaskDialog` .

```cpp
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>Parametry

*nInformacje*<br/>
podczas Stan paska postępu. Możliwe wartości można znaleźć w sekcji uwagi.

### <a name="remarks"></a>Uwagi

Ta metoda zgłasza wyjątek za pomocą makra [upewnia](diagnostic-services.md#ensure) się, jeśli `CTaskDialog` jest już wyświetlany i ma pasek postępu neonu.

Poniższa tabela zawiera listę możliwych wartości dla *nInformacje*. We wszystkich tych przypadkach pasek postępu będzie wypełniał kolorem regularnym, dopóki nie osiągnie wskazanej pozycji zatrzymania. W tym momencie zmieni kolor na podstawie stanu.

|Nazwa|Opis|
|-|-|
|PBST_NORMAL|Po wypełnieniu paska postępu nie `CTaskDialog` zmienia on koloru paska. Domyślnie normalny kolor jest zielony.|
|PBST_ERROR|Po wypełnieniu paska postępu `CTaskDialog` zmienia kolor paska na kolor błędu. Domyślnie jest to kolor czerwony.|
|PBST_PAUSED|Po wypełnieniu paska postępu `CTaskDialog` zmienia kolor paska na wstrzymany kolor. Domyślnie jest to kolor żółty.|

Można ustawić, gdzie pasek postępu zostanie zatrzymany z [obiektu CTaskDialog:: SetProgressBarPosition](#setprogressbarposition).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetradiobuttonoptions"></a><a name="setradiobuttonoptions"></a> Obiektu CTaskDialog:: SetRadioButtonOptions

Włącza lub wyłącza przycisk radiowy.

```cpp
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
podczas Identyfikator kontrolki przycisku radiowego.

*bEnabled*<br/>
podczas Wartość TRUE powoduje włączenie przycisku radiowego; Wartość FALSE, aby wyłączyć przycisk radiowy.

### <a name="remarks"></a>Uwagi

Ta metoda zgłasza wyjątek z [zagwarantowaniem](diagnostic-services.md#ensure) makro, jeśli *nRadioButtonID* nie jest prawidłowym identyfikatorem przycisku radiowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetverificationcheckbox"></a><a name="setverificationcheckbox"></a> Obiektu CTaskDialog:: SetVerificationCheckbox

Ustawia stan zaznaczenia pola wyboru weryfikacji.

```cpp
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>Parametry

*bChecked*<br/>
podczas Wartość TRUE oznacza, że pole wyboru weryfikacji jest zaznaczone, gdy `CTaskDialog` jest wyświetlany; Jeśli pole wyboru nie jest zaznaczone, gdy jest wyświetlane, wartość FALSE `CTaskDialog` .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetverificationcheckboxtext"></a><a name="setverificationcheckboxtext"></a> Obiektu CTaskDialog:: SetVerificationCheckboxText

Ustawia tekst wyświetlany po prawej stronie pola wyboru weryfikacji.

```cpp
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>Parametry

*strVerificationText*<br/>
podczas Tekst wyświetlany w tej metodzie obok pola wyboru weryfikacji.

### <a name="remarks"></a>Uwagi

Ta metoda zgłasza wyjątek z warunkiem [, że](diagnostic-services.md#ensure) to wystąpienie `CTaskDialog` klasy jest już wyświetlane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetwindowtitle"></a><a name="setwindowtitle"></a> Obiektu CTaskDialog:: SetWindowTitle

Ustawia tytuł elementu `CTaskDialog` .

```cpp
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>Parametry

*strWindowTitle*<br/>
podczas Nowy tytuł dla `CTaskDialog` .

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogshowdialog"></a><a name="showdialog"></a> Obiektu CTaskDialog:: ShowDialog

Tworzy i wyświetla `CTaskDialog` .

```
static INT_PTR ShowDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons = TDCBF_YES_BUTTON | TDCBF_NO_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>Parametry

*strContent*<br/>
podczas Ciąg, który ma być używany dla zawartości `CTaskDialog` .

*strMainInstruction*<br/>
podczas Główna instrukcja `CTaskDialog` .

*strTitle*<br/>
podczas Tytuł `CTaskDialog` .

*nIDCommandControlsFirst*<br/>
podczas Identyfikator ciągu pierwszego polecenia.

*nIDCommandControlsLast*<br/>
podczas Identyfikator ciągu ostatniego polecenia.

*nCommonButtons*<br/>
podczas Maska przycisków, które mają zostać dodane do `CTaskDialog` .

*nTaskDialogOptions*<br/>
podczas Zestaw opcji do użycia dla `CTaskDialog` .

*strFooter*<br/>
podczas Ciąg, który ma być używany jako stopka.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która odnosi się do zaznaczenia dokonanego przez użytkownika.

### <a name="remarks"></a>Uwagi

Ta metoda statyczna umożliwia tworzenie wystąpienia `CTaskDialog` klasy bez jawnego tworzenia `CTaskDialog` obiektu w kodzie. Ponieważ nie ma żadnego `CTaskDialog` obiektu, nie można wywoływać innych metod, `CTaskDialog` Jeśli używasz tej metody do wyświetlania `CTaskDialog` użytkownikowi.

Ta metoda tworzy formanty przycisków poleceń przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów zawiera kilka ciągów ze skojarzonymi identyfikatorami ciągów. Ta metoda dodaje kontrolkę przycisk polecenia dla każdego prawidłowego wpisu w tabeli ciągów między *nIDCommandControlsFirst* i *nCommandControlsLast*włącznie. Dla tych kontrolek przycisków poleceń ciąg w tabeli ciągów jest podpisem kontrolki, a IDENTYFIKATORem ciągu jest identyfikator formantu.

Aby uzyskać listę prawidłowych opcji, zobacz [obiektu CTaskDialog:: SetOptions](#setoptions) .

`CTaskDialog`Zamyka się, gdy użytkownik wybierze wspólny przycisk, formant linku polecenia lub zamknie `CTaskDialog` . Wartość zwracana jest identyfikatorem, który wskazuje, jak użytkownik zamknął okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogtaskdialogcallback"></a><a name="taskdialogcallback"></a> Obiektu CTaskDialog:: TaskDialogCallback

Struktura wywołuje tę metodę w odpowiedzi na różne komunikaty systemu Windows.

```
friend:
HRESULT TaskDialogCallback(
    HWND hWnd,
    UINT uNotification,
    WPARAM wParam,
    LPARAM lParam,
    LONG_PTR dwRefData);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
podczas Dojście do `m_hWnd` struktury `CTaskDialog` .

*uNotification*<br/>
podczas Kod powiadomienia, który określa wygenerowany komunikat.

*wParam*<br/>
podczas Więcej informacji o komunikacie.

*lParam*<br/>
podczas Więcej informacji o komunikacie.

*dwRefData*<br/>
podczas Wskaźnik do `CTaskDialog` obiektu, do którego odnosi się komunikat wywołania zwrotnego.

### <a name="return-value"></a>Wartość zwracana

Zależy od określonego kodu powiadomienia. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Domyślna implementacja programu `TaskDialogCallback` obsługuje określony komunikat, a następnie wywołuje odpowiednią metodę dla [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Na przykład w odpowiedzi na komunikat TDN_BUTTON_CLICKED `TaskDialogCallback` wywołuje [obiektu CTaskDialog:: OnCommandControlClick](#oncommandcontrolclick).

Wartości dla *wParam* i *lParam* zależą od konkretnego wygenerowanego komunikatu. Możliwe jest, aby jedna lub obie te wartości były puste. Poniższa tabela zawiera listę domyślnych powiadomień, które są obsługiwane i co reprezentuje wartości *wParam* i *lParam* . Jeśli zastąpisz tę metodę w klasie pochodnej, należy zaimplementować kod wywołania zwrotnego dla każdego komunikatu w poniższej tabeli.

|Komunikat powiadomienia|*wParam* Wartościami|*lParam* Wartościami|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|Nie używany.|Nie używany.|
|TDN_NAVIGATED|Nie używany.|Nie używany.|
|TDN_BUTTON_CLICKED|Identyfikator kontrolki przycisku polecenia.|Nie używany.|
|TDN_HYPERLINK_CLICKED|Nie używany.|Struktura [LPCWSTR](/windows/win32/WinProg/windows-data-types) , która zawiera link.|
|TDN_TIMER|Czas (w milisekundach) od `CTaskDialog` utworzenia lub czasomierz został zresetowany.|Nie używany.|
|TDN_DESTROYED|Nie używany.|Nie używany.|
|TDN_RADIO_BUTTON_CLICKED|Identyfikator przycisku radiowego.|Nie używany.|
|TDN_DIALOG_CONSTRUCTED|Nie używany.|Nie używany.|
|TDN_VERIFICATION_CLICKED|1 Jeśli pole wyboru jest zaznaczone, 0, jeśli nie jest.|Nie używany.|
|TDN_HELP|Nie używany.|Nie używany.|
|TDN_EXPANDO_BUTTON_CLICKED|0, jeśli obszar rozszerzania jest zwinięty; różne od zera, jeśli wyświetlany jest tekst rozwinięcia.|Nie używany.|

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Przewodnik: Dodawanie obiektu CTaskDialog do aplikacji](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
