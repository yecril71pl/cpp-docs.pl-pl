---
title: Klasa CTaskDialog
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
ms.openlocfilehash: 04c8a60f546700be8eeb2ec8a948e0ea321d12f8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265018"
---
# <a name="ctaskdialog-class"></a>Klasa CTaskDialog

Wyskakujące okno dialogowe, które funkcje jak okno komunikatu, ale można wyświetlić dodatkowe informacje do użytkownika. `CTaskDialog` Obejmuje również funkcję do zbierania informacji od użytkownika.

## <a name="syntax"></a>Składnia

```
class CTaskDialog : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[CTaskDialog::CTaskDialog](#ctaskdialog)|Konstruuje `CTaskDialog` obiektu.|

### <a name="methods"></a>Metody

|||
|-|-|
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|Dodaje formant przycisku polecenia, aby `CTaskDialog`.|
|[CTaskDialog::AddRadioButton](#addradiobutton)|Dodaje przycisk radiowy, aby `CTaskDialog`.|
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|Programowe klika formant przycisku polecenia lub wspólnej przycisku.|
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Programowe klika przycisk radiowy.|
|[CTaskDialog::DoModal](#domodal)|Wyświetla `CTaskDialog`.|
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Pobiera liczbę dostępnych wspólnej przycisków.|
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Konwertuje standardowego przycisku Windows wspólny typ przycisku skojarzone z `CTaskDialog` klasy.|
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|Konwertuje jeden z najczęściej popełnianymi typami przycisk skojarzone z `CTaskDialog` klasy do standardowego przycisku Windows.|
|[CTaskDialog::GetOptions](#getoptions)|Zwraca wartość flagi opcji dla tego `CTaskDialog`.|
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|Zwraca kontrolkę przycisku wybranego polecenia.|
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Zwraca wartość wybranego przycisku radiowego.|
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Pobiera stan weryfikacji pola wyboru.|
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|Określa, czy formant przycisku polecenia lub wspólnej przycisk jest włączony.|
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|Określa, czy włączono przycisku radiowego.|
|[CTaskDialog::IsSupported](#issupported)|Określa, czy komputer, na którym działa aplikacja obsługuje `CTaskDialog`.|
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Dodaje kontrolek przycisku polecenia, używając danych z tablicy ciągów.|
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|Dodaje przycisków radiowych przy użyciu danych z tablicy ciągów.|
|[CTaskDialog::NavigateTo](#navigateto)|Przenosi fokus do innego `CTaskDialog`.|
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|Struktura wywołuje tę metodę, gdy użytkownik kliknie kontrolkę przycisku polecenia.|
|[CTaskDialog::OnCreate](#oncreate)|Struktura wywołuje tę metodę, po utworzeniu `CTaskDialog`.|
|[CTaskDialog::OnDestroy](#ondestroy)|Struktura wywołuje tę metodę, natychmiast przed niszczy `CTaskDialog`.|
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|Struktura wywołuje tę metodę, gdy użytkownik kliknie przycisk rozszerzenia.|
|[CTaskDialog::OnHelp](#onhelp)|Struktura wywołuje tę metodę, gdy użytkownik zażąda pomocy.|
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|Struktura wywołuje tę metodę, gdy użytkownik kliknie hiperlink.|
|[CTaskDialog::OnInit](#oninit)|Struktura wywołuje tę metodę podczas `CTaskDialog` został zainicjowany.|
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|Platforma wywołuje tę metodę, gdy użytkownik przenosi fokus w odniesieniu do kontrolki `CTaskDialog`.|
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|Struktura wywołuje tę metodę, gdy użytkownik wybierze kontrolkę przycisku radiowego.|
|[CTaskDialog::OnTimer](#ontimer)|Struktura wywołuje tę metodę, po upływie okresu działania czasomierza.|
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|Struktura wywołuje tę metodę, gdy użytkownik kliknie pole weryfikacji.|
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|Usuwa wszystkie formanty poleceń z `CTaskDialog`.|
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|Usuwa wszystkie przyciski radiowe z `CTaskDialog`.|
|[CTaskDialog::SetCommandControlOptions](#setcommandcontroloptions)|Aktualizuje formant przycisku polecenia na `CTaskDialog`.|
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|Aktualizuje podzbioru typowych przycisków można włączyć i wymaga podniesienia uprawnień funkcji kontroli konta użytkownika.|
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|Dodaje typowe przycisków, aby `CTaskDialog`.|
|[CTaskDialog::SetContent](#setcontent)|Aktualizuje zawartość `CTaskDialog`.|
|[CTaskDialog::SetDefaultCommandControl](#setdefaultcommandcontrol)|Określa domyślny formant przycisku polecenia.|
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|Określa domyślny przycisk radiowy.|
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|Dostosowuje szerokość `CTaskDialog`.|
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|Aktualizuje obszar rozszerzenia `CTaskDialog`.|
|[CTaskDialog::SetFooterIcon](#setfootericon)|Aktualizuje ikonę stopki `CTaskDialog`.|
|[CTaskDialog::SetFooterText](#setfootertext)|Aktualizuje tekst w stopce `CTaskDialog`.|
|[CTaskDialog::SetMainIcon](#setmainicon)|Aktualizuje ikony głównej o `CTaskDialog`.|
|[CTaskDialog::SetMainInstruction](#setmaininstruction)|Aktualizuje głównego instrukcja `CTaskDialog`.|
|[CTaskDialog::SetOptions](#setoptions)|Konfiguruje opcje `CTaskDialog`.|
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Konfiguruje pasek neon `CTaskDialog` i dodaje go do okna dialogowego.|
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|Ustawia położenie paska postępu.|
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|Dopasowuje zakresu pasek postępu.|
|[CTaskDialog::SetProgressBarState](#setprogressbarstate)|Ustawia stan pasek postępu i wyświetla go na `CTaskDialog`.|
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Włącza lub wyłącza przycisk radiowy.|
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|Ustawia stan zaznaczenia pola wyboru weryfikacji.|
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Ustawia tekst po prawej stronie pola wyboru weryfikacji.|
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|Ustawia tytuł elementu `CTaskDialog`.|
|[CTaskDialog::ShowDialog](#showdialog)|Tworzy i wyświetla `CTaskDialog`.|
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|Struktura ta jest nazywana w odpowiedzi na różne komunikaty Windows.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|`m_aButtons`|Tablica kontrolki przycisku polecenia `CTaskDialog`.|
|`m_aRadioButtons`|Tablica kontrolek przycisków radiowych do `CTaskDialog`.|
|`m_bVerified`|`TRUE` Wskazuje, że zaznaczono pole wyboru weryfikacji; `FALSE` wskazuje nie jest.|
|`m_footerIcon`|Ikony w stopce `CTaskDialog`.|
|`m_hWnd`|Dojście do okna `CTaskDialog`.|
|`m_mainIcon`|Ikona główna dla `CTaskDialog`.|
|`m_nButtonDisabled`|Maskę, która wskazuje, które wspólnej przyciski są wyłączone.|
|`m_nButtonElevation`|Maskę, która wskazuje, które wspólnej przyciski wymaga podniesienia uprawnień funkcji kontroli konta użytkownika.|
|`m_nButtonId`|Identyfikator kontrolki przycisku wybranego polecenia.|
|`m_nCommonButton`|Maska, wskazującą, które wspólnej przyciski są wyświetlane na `CTaskDialog`.|
|`m_nDefaultCommandControl`|Identyfikator przycisku polecenia kontrolować, czy wybrano podczas `CTaskDialog` jest wyświetlana.|
|`m_nDefaultRadioButton`|Identyfikator przycisku radiowego kontrolować, czy wybrano podczas `CTaskDialog` jest wyświetlana.|
|`m_nFlags`|Maska, który wskazuje opcje `CTaskDialog`.|
|`m_nProgressPos`|Bieżące położenie paska postępu.  Ta wartość musi należeć do zakresu od `m_nProgressRangeMin` i `m_nProgressRangeMax`.|
|`m_nProgressRangeMax`|Maksymalna wartość pasek postępu.|
|`m_nProgressRangeMin`|Wartość minimalna pasek postępu.|
|`m_nProgressState`|Stan pasek postępu. Aby uzyskać więcej informacji, zobacz [CTaskDialog::SetProgressBarState](#setprogressbarstate).|
|`m_nRadioId`|Identyfikator kontrolki przycisku radiowego wybrane.|
|`m_nWidth`|Szerokość `CTaskDialog` w pikselach.|
|`m_strCollapse`|Ciąg `CTaskDialog` Wyświetla z prawej strony pola rozszerzeń, gdy jest ukryty rozszerzone informacje.|
|`m_strContent`|Ciąg tekstowy zawartości obiektu `CTaskDialog`.|
|`m_strExpand`|Ciąg `CTaskDialog` wyświetla się po prawej stronie pola rozszerzenia, gdy rozwinięte informacje są wyświetlane.|
|`m_strFooter`|Stopkę `CTaskDialog`.|
|`m_strInformation`|Rozszerzone informacje dla `CTaskDialog`.|
|`m_strMainInstruction`|Instrukcja głównego `CTaskDialog`.|
|`m_strTitle`|Tytuł `CTaskDialog`.|
|`m_strVerification`|Ciąg, `CTaskDialog` wyświetlane po prawej stronie pola wyboru weryfikacji.|

## <a name="remarks"></a>Uwagi

`CTaskDialog` Klasy zastępuje standardowe okno komunikatu Windows i zawiera dodatkowe funkcje, takie jak nowe formanty do zbierania informacji od użytkownika. Ta klasa znajduje się w bibliotece MFC w programie Visual Studio 2010 i nowszych wersjach. `CTaskDialog` Jest dostępna, począwszy od Windows Vista. Nie można wyświetlić w starszych wersjach Windows `CTaskDialog` obiektu. Użyj `CTaskDialog::IsSupported` do określenia w czasie wykonywania, czy bieżący użytkownik mógł wyświetlić okno dialogowe zadania. Standardowe okno komunikatu Windows nadal jest obsługiwany.

`CTaskDialog` Jest dostępna, tylko gdy kompilujesz aplikację przy użyciu biblioteki Unicode.

`CTaskDialog` Ma dwa różne konstruktory. Jeden konstruktor można określić dwa przyciski poleceń i maksymalnie sześciu formanty przycisków regularne. Można dodać więcej przycisków poleceń po utworzeniu `CTaskDialog`. Drugi Konstruktor nie obsługuje żadnych przycisków poleceń, ale można dodać nieograniczoną liczbę zwykły przycisk kontrolek. Aby uzyskać więcej informacji na temat konstruktory zobacz [CTaskDialog::CTaskDialog](#ctaskdialog).

Na poniższej ilustracji przedstawiono przykład `CTaskDialog` aby zilustrować lokalizacji niektóre formanty.

![Przykładem obiektu CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "przykład CTaskDialog") <br/>
Przykładowe CTaskDialog

## <a name="requirements"></a>Wymagania

**Minimalny wymagany system operacyjny:** Windows Vista

**Nagłówek:** afxtaskdialog.h

##  <a name="addcommandcontrol"></a>  CTaskDialog::AddCommandControl

Dodaje nowy formant przycisku polecenia do `CTaskDialog`.

```
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
[in] Numer identyfikacyjny polecenia kontroli.

*strCaption*<br/>
[in] Ciąg, `CTaskDialog` wyświetla dla użytkownika. Użyj tych parametrów, aby wyjaśnić, cel polecenia.

*bWłączony*<br/>
[in] Parametrów logiczny, który wskazuje, czy nowy przycisk jest włączony.

*bRequiresElevation*<br/>
[in] Parametrów logiczny, który wskazuje, czy polecenie wymaga podniesienia uprawnień.

### <a name="remarks"></a>Uwagi

`CTaskDialog Class` Można wyświetlić nieograniczoną liczbę kontrolek przycisku polecenia. Jednak jeśli `CTaskDialog` kontroluje dowolnego przycisku polecenia wyświetla, można wyświetlić, maksymalnie sześć przycisków. Jeśli `CTaskDialog` ma Brak kontrolek przycisku polecenia, można wyświetlić, nieograniczoną liczbę przycisków.

Gdy użytkownik wybierze kontrolkę przycisku polecenia `CTaskDialog` zostanie zamknięty. Jeśli aplikacja zostanie wyświetlone okno dialogowe, za pomocą [CTaskDialog::DoModal](#domodal), `DoModal` zwraca *nCommandControlID* formantu przycisku wybranego polecenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="addradiobutton"></a>  CTaskDialog::AddRadioButton

Dodaje przycisk radiowy, aby `CTaskDialog`.

```
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[in] Numer identyfikacyjny przycisku radiowego.

*strCaption*<br/>
[in] Ciąg, `CTaskDialog` wyświetlany obok przycisku radiowego.

*bWłączony*<br/>
[in] Parametr logiczny, który wskazuje, czy włączono przycisku radiowego.

### <a name="remarks"></a>Uwagi

Przyciski radiowe dla [klasa CTaskDialog](../../mfc/reference/ctaskdialog-class.md) umożliwiają zbieranie informacji od użytkownika. Użyj funkcji [CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid) ustalenie, który przycisk radiowy zostanie wybrany.

`CTaskDialog` Nie wymaga *nRadioButtonID* parametry są unikatowe dla każdego przycisku radiowego. Jeśli nie używasz unikatowych identyfikator dla każdego przycisku radiowego może jednak wystąpić nieoczekiwane zachowanie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="clickcommandcontrol"></a>  CTaskDialog::ClickCommandControl

Programowe klika formant przycisku polecenia lub wspólnej przycisku.

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
[in] Identyfikator polecenia formantu do kliknięcia.

### <a name="remarks"></a>Uwagi

Ta metoda generuje komunikat TDM_CLICK_BUTTON systemu windows.

##  <a name="clickradiobutton"></a>  CTaskDialog::ClickRadioButton

Programowe klika przycisk radiowy.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[in] Identyfikator przycisku radiowego, kliknij przycisk.

### <a name="remarks"></a>Uwagi

Ta metoda generuje komunikat TDM_CLICK_RADIO_BUTTON systemu windows.

##  <a name="ctaskdialog"></a>  CTaskDialog::CTaskDialog

Tworzy wystąpienie [klasa CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

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
[in] Ciąg używany dla zawartości `CTaskDialog`.

*strMainInstruction*<br/>
[in] Instrukcja głównego `CTaskDialog`.

*strTitle*<br/>
[in] Tytuł `CTaskDialog`.

*nCommonButtons*<br/>
[in] Maska wspólnej przycisków, aby dodać do `CTaskDialog`.

*nTaskDialogOptions*<br/>
[in] Zestaw opcji dla `CTaskDialog`.

*strFooter*<br/>
[in] Ciąg do użycia jako stopki.

*nIDCommandControlsFirst*<br/>
[in] Identyfikator ciągu pierwszego polecenia.

*nIDCommandControlsLast*<br/>
[in] Identyfikator ciągu ostatnie polecenie.

### <a name="remarks"></a>Uwagi

Istnieją dwa sposoby, które można dodać `CTaskDialog` do aplikacji. Pierwszym sposobem jest użycie jednego z konstruktorów do tworzenia `CTaskDialog` i wyświetl ją przy użyciu [CTaskDialog::DoModal](#domodal). Drugim sposobem jest użycie funkcji statycznej [CTaskDialog::ShowDialog](#showdialog), która pozwala na wyświetlanie `CTaskDialog` bez konieczności jawnego tworzenia `CTaskDialog` obiektu.

Drugi Konstruktor tworzy kontrolek przycisku polecenia przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów ma kilka ciągów przy użyciu parametrów skojarzonych identyfikatorów. Metoda ta umożliwia dodanie polecenia kontrolki przycisku dla każdego prawidłowego wpisu w tabeli ciągów między *nIDCommandControlsFirst* i *nCommandControlsLast*włącznie. Te kontrolki przycisku polecenia parametry w tabeli ciągów jest podpis formantu i identyfikator ciągu jest identyfikatorem formantu.

Zobacz [CTaskDialog::SetOptions](#setoptions) listę prawidłowych opcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="domodal"></a>  CTaskDialog::DoModal

Pokazuje `CTaskDialog` i sprawia, że modalne.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parametry

*hParent*<br/>
[in] W oknie nadrzędnym `CTaskDialog`.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która odnosi się do wybranej przez użytkownika.

### <a name="remarks"></a>Uwagi

Wyświetla tego wystąpienia [CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Następnie aplikacja oczekuje na użytkownika zamknąć okno dialogowe.

`CTaskDialog` Zamyka się, gdy użytkownik wybierze przycisk wspólnej formant łącza polecenie lub zamknie `CTaskDialog`. Wartość zwracana jest identyfikator, który wskazuje, jak użytkownik zamknięte okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getcommonbuttoncount"></a>  CTaskDialog::GetCommonButtonCount

Pobiera liczbę wspólnych przycisków.

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba wspólnych przycisków dostępnych.

### <a name="remarks"></a>Uwagi

Typowe przyciski są przyciski domyślny, który możesz udostępnić [CTaskDialog::CTaskDialog](#ctaskdialog). [Klasa CTaskDialog](../../mfc/reference/ctaskdialog-class.md) Wyświetla przyciski wzdłuż dolnej części okna dialogowego.

Na liście wyliczany przyciski znajduje się w CommCtrl.h.

##  <a name="getcommonbuttonflag"></a>  CTaskDialog::GetCommonButtonFlag

Konwertuje standardowego przycisku Windows wspólny typ przycisku skojarzone z [klasa CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>Parametry

*nButtonId*<br/>
[in] Standardowa wartość przycisku Windows.

### <a name="return-value"></a>Wartość zwracana

Wartość odpowiadającego `CTaskDialog` typowych przycisku. Jeśli nie ma odpowiednich wspólnych przycisku, ta metoda zwraca wartość 0.

##  <a name="getcommonbuttonid"></a>  CTaskDialog::GetCommonButtonId

Konwertuje jeden z najczęściej popełnianymi typami przycisk skojarzone z [klasa CTaskDialog](../../mfc/reference/ctaskdialog-class.md) do standardowego przycisku Windows.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>Parametry

*nFlag*<br/>
[in] Skojarzony typ wspólny przycisk `CTaskDialog` klasy.

### <a name="return-value"></a>Wartość zwracana

Wartość odpowiedniego standardowego przycisku Windows. Jeśli nie ma odpowiedniego Windows przycisku, metoda zwraca wartość 0.

##  <a name="getoptions"></a>  CTaskDialog::GetOptions

Zwraca wartość flagi opcji dla tego `CTaskDialog`.

```
int GetOptions() const;
```

### <a name="return-value"></a>Wartość zwracana

Flagi dla `CTaskDialog`.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat dostępnych opcji [klasa CTaskDialog](../../mfc/reference/ctaskdialog-class.md), zobacz [CTaskDialog::SetOptions](#setoptions).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getselectedcommandcontrolid"></a>  CTaskDialog::GetSelectedCommandControlID

Zwraca kontrolkę przycisku wybranego polecenia.

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia zaznaczony formant przycisku.

### <a name="remarks"></a>Uwagi

Nie masz do używania tej metody, aby pobrać identyfikator przycisku polecenia, który użytkownik zaznaczył. Ten identyfikator jest zwracany przez [CTaskDialog::DoModal](#domodal) lub [CTaskDialog::ShowDialog](#showdialog).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="getselectedradiobuttonid"></a>  CTaskDialog::GetSelectedRadioButtonID

Zwraca wartość wybranego przycisku radiowego.

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator wybranego przycisku radiowego.

### <a name="remarks"></a>Uwagi

Można użyć tej metody, po użytkownik zamknie okno dialogowe, które można pobrać wybranego przycisku radiowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="getverificationcheckboxstate"></a>  CTaskDialog::GetVerificationCheckboxState

Pobiera stan weryfikacji pola wyboru.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pole wyboru jest zaznaczone, wartość FALSE, jeśli nie jest.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="iscommandcontrolenabled"></a>  CTaskDialog::IsCommandControlEnabled

Określa, czy formant przycisku polecenia lub przycisk jest włączony.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
[in] Identyfikator kontrolki przycisku polecenia lub przycisku do testowania.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli kontrolka jest włączona, FALSE, jeśli nie jest.

### <a name="remarks"></a>Uwagi

Ta metoda służy do określenia dostępności zarówno kontrolek przycisku polecenia i wspólne przyciski `CTaskDialog` klasy *.

Jeśli *nCommandControlID* pojawia się nie jest prawidłowym identyfikatorem dla dowolnego często `CTaskDialog` przycisku lub kontrolki przycisku polecenia, ta metoda zgłasza wyjątek.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="isradiobuttonenabled"></a>  CTaskDialog::IsRadioButtonEnabled

Określa, czy włączono przycisku radiowego.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[in] Identyfikator przycisku radiowego do testowania.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli przycisku radiowego jest włączone, wartość FALSE, jeśli nie jest.

### <a name="remarks"></a>Uwagi

Jeśli *nRadioButtonID* nie jest prawidłowym identyfikatorem dla przycisku radiowego, ta metoda zgłasza wyjątek.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="issupported"></a>  CTaskDialog::IsSupported

Określa, czy komputer, na którym działa aplikacja obsługuje `CTaskDialog`.

```
static BOOL IsSupported();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli komputer obsługuje `CTaskDialog`; Wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do określenia w czasie wykonywania, czy komputer, na którym działa aplikacja obsługuje `CTaskDialog` klasy. Jeśli komputer nie obsługuje `CTaskDialog`, należy podać inną metodą przekazywania informacji do użytkownika. Twoja aplikacja ulegnie awarii, jeśli próbuje użyć `CTaskDialog` na komputerze, który nie obsługuje `CTaskDialog` klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="loadcommandcontrols"></a>  CTaskDialog::LoadCommandControls

Dodaje kontrolek przycisku polecenia, używając danych z tablicy ciągów.

```
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>Parametry

*nIDCommandControlsFirst*<br/>
[in] Identyfikator ciągu pierwszego polecenia.

*nIDCommandControlsLast*<br/>
[in] Identyfikator ciągu ostatnie polecenie.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy kontrolek przycisku polecenia przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów ma kilka ciągów przy użyciu parametrów skojarzonych identyfikatorów. Nowe kontrolki przycisku polecenia dodane za pomocą tej metody należy użyć ciągu formantu podpisu i identyfikator ciągu Identyfikator kontrolki. Zakres wybrane parametry są dostarczane przez *nIDCommandControlsFirst* i *nCommandControlsLast*włącznie. Jeśli zakres jest pusty wpis, metoda nie dodaje formant przycisku polecenia dla tego wpisu.

Domyślnie nowe kontrolki przycisku polecenia są włączone i nie wymagają podniesionych uprawnień.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="loadradiobuttons"></a>  CTaskDialog::LoadRadioButtons

Dodaje kontrolek przycisków radiowych przy użyciu danych z tablicy ciągów.

```
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>Parametry

*nIDRadioButtonsFirst*<br/>
[in] Identyfikator ciągu pierwszego przycisku radiowego.

*nIDRadioButtonsLast*<br/>
[in] Identyfikator ciągu ostatnich przycisku radiowego.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy przyciski radiowe przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów ma kilka ciągów przy użyciu parametrów skojarzonych identyfikatorów. Nowe przyciski radiowe dodane za pomocą tej metody należy użyć ciągu napis na przycisku radiowego i identyfikator ciągu dla identyfikatora przycisk radiowy. Zakres wybrane parametry są dostarczane przez *nIDRadioButtonsFirst* i *nRadioButtonsLast*włącznie. Jeśli zakres jest pusty wpis, metoda nie powoduje dodania przycisku radiowego dla tego wpisu.

Domyślnie nowe przyciski radiowe są włączone.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="navigateto"></a>  CTaskDialog::NavigateTo

Przenosi fokus do innego `CTaskDialog`.

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>Parametry

*oTaskDialog*<br/>
[in] `CTaskDialog` , Która otrzymuje fokus.

### <a name="remarks"></a>Uwagi

Ta metoda powoduje ukrycie bieżącego `CTaskDialog` po Wyświetla *oTaskDialog*. *OTaskDialog* jest wyświetlany w tej samej lokalizacji co bieżący `CTaskDialog`.

##  <a name="oncommandcontrolclick"></a>  CTaskDialog::OnCommandControlClick

Struktura wywołuje tę metodę, gdy użytkownik kliknie kontrolkę przycisku polecenia.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
[in] Identyfikator kontrolki przycisku polecenia, który użytkownik zaznaczył.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, aby implementować niestandardowe zachowanie.

##  <a name="oncreate"></a>  CTaskDialog::OnCreate

Struktura wywołuje tę metodę, po utworzeniu `CTaskDialog`.

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, aby implementować niestandardowe zachowanie.

##  <a name="ondestroy"></a>  CTaskDialog::OnDestroy

Struktura wywołuje tę metodę, natychmiast przed niszczy `CTaskDialog`.

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, aby implementować niestandardowe zachowanie.

##  <a name="onexpandbuttonclick"></a>  CTaskDialog::OnExpandButtonClick

Struktura wywołuje tę metodę, gdy użytkownik kliknie przycisk rozszerzenia.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>Parametry

*bExpanded*<br/>
[in] Wartość różną od zera wartość wskazuje, że dodatkowe informacje są wyświetlane; 0 wskazuje, że dodatkowe informacje są ukrywane.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, aby implementować niestandardowe zachowanie.

##  <a name="onhelp"></a>  CTaskDialog::OnHelp

Struktura wywołuje tę metodę, gdy użytkownik zażąda pomocy.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, aby implementować niestandardowe zachowanie.

##  <a name="onhyperlinkclick"></a>  CTaskDialog::OnHyperlinkClick

Struktura wywołuje tę metodę, gdy użytkownik kliknie hiperlink.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>Parametry

*strHref*<br/>
[in] Ciąg, który reprezentuje hiperlink.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea) przed zwróceniem S_OK.

Należy przesłonić tę metodę w klasie pochodnej, aby implementować niestandardowe zachowanie.

##  <a name="oninit"></a>  CTaskDialog::OnInit

Struktura wywołuje tę metodę podczas `CTaskDialog` został zainicjowany.

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, aby implementować niestandardowe zachowanie.

##  <a name="onnavigatepage"></a>  CTaskDialog::OnNavigatePage

Struktura wywołuje tę metodę w odpowiedzi na [CTaskDialog::NavigateTo](#navigateto) metody.

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, aby implementować niestandardowe zachowanie.

##  <a name="onradiobuttonclick"></a>  CTaskDialog::OnRadioButtonClick

Struktura wywołuje tę metodę, gdy użytkownik wybierze kontrolkę przycisku radiowego.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[in] Identyfikator kontrolki przycisku radiowego, że użytkownik kliknął element.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, aby implementować niestandardowe zachowanie.

##  <a name="ontimer"></a>  CTaskDialog::OnTimer

Struktura wywołuje tę metodę, po upływie okresu działania czasomierza.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>Parametry

*lTime*<br/>
[in] Czas w milisekundach, ponieważ `CTaskDialog` został utworzony lub został zresetowany przez czasomierz.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, aby implementować niestandardowe zachowanie.

##  <a name="onverificationcheckboxclick"></a>  CTaskDialog::OnVerificationCheckboxClick

Struktura wywołuje tę metodę, gdy użytkownik kliknie pole weryfikacji.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>Parametry

*bChecked*<br/>
[in] Wartość TRUE wskazuje, że zaznaczone jest pole wyboru weryfikacji; Wartość FALSE wskazuje, że nie jest.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość S_OK.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, aby implementować niestandardowe zachowanie.

##  <a name="removeallcommandcontrols"></a>  CTaskDialog::RemoveAllCommandControls

Usuwa wszystkich kontrolek przycisku polecenia z `CTaskDialog`.

```
void RemoveAllCommandControls();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="removeallradiobuttons"></a>  CTaskDialog::RemoveAllRadioButtons

Usuwa wszystkie przyciski radiowe z `CTaskDialog`.

```
void RemoveAllRadioButtons();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setcommandcontroloptions"></a>  CTaskDialog::SetCommandControlOptions

Aktualizuje formant przycisku polecenia na `CTaskDialog`.

```
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
[in] Identyfikator formantu polecenia do zaktualizowania.

*bWłączony*<br/>
[in] Parametrów logiczny, który wskazuje, czy formant przycisku określone polecenie jest włączone.

*bRequiresElevation*<br/>
[in] Parametr logiczny, który wskazuje na to, jeśli formant przycisku polecenia wymaga podniesienia uprawnień.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia określenie, czy formant przycisku polecenia jest włączona lub wymaga podniesienia uprawnień, po dodaniu do `CTaskDialog` klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setcommonbuttonoptions"></a>  CTaskDialog::SetCommonButtonOptions

Aktualizuje podzbioru typowych przyciski, można włączyć i wymaga podniesienia uprawnień funkcji kontroli konta użytkownika.

```
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parametry

*nDisabledButtonMask*<br/>
[in] Maska dla typowych przycisków, aby wyłączyć.

*nElevationButtonMask*<br/>
[in] Maska dla typowych przycisków, które wymagają podniesionych uprawnień.

### <a name="remarks"></a>Uwagi

Można ustawić wspólne przyciski dostępne wystąpienia [klasa CTaskDialog](../../mfc/reference/ctaskdialog-class.md) za pomocą konstruktora [CTaskDialog::CTaskDialog](#ctaskdialog) , a także metoda [CTaskDialog::SetCommonButtons ](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions` nie obsługuje dodawania nowe przyciski wspólnej.

Jeśli używasz tej metody do wyłączenia lub podniesienie poziomu wspólnego przycisku, który nie jest dostępna dla tego `CTaskDialog`, ta metoda zgłasza wyjątek, za pomocą [upewnij się, że](diagnostic-services.md#ensure) makra.

Ta metoda umożliwia dowolnego przycisku, który jest dostępny dla `CTaskDialog` , ale nie znajduje się w *nDisabledButtonMask*, nawet jeśli wcześniej była wyłączona. Ta metoda traktuje podniesienia uprawnień w podobny sposób: rejestruje wspólnej przyciski, co nie wymaga podniesienia uprawnień, jeśli wspólnej przycisk jest dostępny, ale nie jest zawarty w *nElevationButtonMask*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcommonbuttons"></a>  CTaskDialog::SetCommonButtons

Dodaje typowe przycisków, aby `CTaskDialog`.

```
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parametry

*nButtonMask*<br/>
[in] Maska przycisków, aby dodać do `CTaskDialog`.

*nDisabledButtonMask*<br/>
[in] Maska przycisków, aby wyłączyć.

*nElevationButtonMask*<br/>
[in] Maska przycisków, które wymagają podniesionych uprawnień.

### <a name="remarks"></a>Uwagi

Nie można wywołać tę metodę po okna dla tego wystąpienia `CTaskDialog` klasa jest tworzona. Jeśli to zrobisz, ta metoda zgłasza wyjątek.

Przyciski wskazywanym przez *nButtonMask* zastępują wszystkie przyciski typowych wcześniej dodane do `CTaskDialog`. Tylko przyciski czcionką *nButtonMask* są dostępne.

Jeśli *nDisabledButtonMask* lub *nElevationButtonMask* zawiera przycisk, który nie znajduje się w *nButtonMask*, ta metoda zgłasza wyjątek, za pomocą [Upewnij się, że](diagnostic-services.md#ensure) makra.

Domyślnie wszystkie typowe przyciski są włączone i nie wymagają podniesionych uprawnień.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcontent"></a>  CTaskDialog::SetContent

Aktualizuje zawartość `CTaskDialog`.

```
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>Parametry

*strContent*<br/>
[in] Ciąg wyświetlany użytkownikowi.

### <a name="remarks"></a>Uwagi

Zawartość `CTaskDialog` klasa jest tekst, który jest wyświetlany użytkownikowi w głównej części okna dialogowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setdefaultcommandcontrol"></a>  CTaskDialog::SetDefaultCommandControl

Określa domyślny formant przycisku polecenia.

```
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>Parametry

*nCommandControlID*<br/>
[in] Identyfikator kontrolki przycisku polecenia jako domyślny.

### <a name="remarks"></a>Uwagi

Domyślny formant przycisku polecenia jest formant który jest zaznaczone, gdy `CTaskDialog` najpierw jest wyświetlany użytkownikowi.

Ta metoda zgłasza wyjątek, jeśli nie można odnaleźć formant przycisku polecenia, które są określone przez *nCommandControlID*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setdefaultradiobutton"></a>  CTaskDialog::SetDefaultRadioButton

Określa domyślny przycisk radiowy.

```
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[in] Identyfikator przycisku radiowego jako domyślny.

### <a name="remarks"></a>Uwagi

Przycisk radiowy domyślny jest przycisk, który jest zaznaczone, gdy `CTaskDialog` najpierw jest wyświetlany użytkownikowi.

Ta metoda zgłasza wyjątek, jeśli nie można odnaleźć przycisku radiowego, określony przez *nRadioButtonID*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setdialogwidth"></a>  CTaskDialog::SetDialogWidth

Dostosowuje szerokość `CTaskDialog`.

```
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
[in] Szerokość okna dialogowego, w pikselach.

### <a name="remarks"></a>Uwagi

Parametr *nWidth* musi być większa lub równa 0. W przeciwnym razie ta metoda zgłasza wyjątek.

Jeśli *nWidth* jest równa 0, tej metody ustawia dialogowego domyślny rozmiar.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setexpansionarea"></a>  CTaskDialog::SetExpansionArea

Aktualizuje obszar rozszerzenia `CTaskDialog`.

```
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>Parametry

*strExpandedInformation*<br/>
[in] Ciąg, `CTaskDialog` wyświetla w głównym oknie dialogowym, gdy użytkownik kliknie przycisk rozszerzenia.

*strCollapsedLabel*<br/>
[in] Ciąg, `CTaskDialog` wyświetlane obok przycisku rozbudowy po zwinięciu rozwinięty obszar.

*strExpandedLabel*<br/>
[in] Ciąg, `CTaskDialog` wyświetlany obok przycisku rozbudowy, gdy rozwinięty obszar jest wyświetlana.

### <a name="remarks"></a>Uwagi

Obszar rozszerzenia `CTaskDialog` klasy umożliwia podanie dodatkowych informacji do użytkownika. W obszarze rozszerzenia znajduje się w głównej części `CTaskDialog`, który znajduje się bezpośrednio pod tytuł i zawartość ciągu.

Gdy `CTaskDialog` następuje wyświetlane, go nie uwzględnia rozszerzone informacje, jak i umieszcza `strCollapsedLabel` obok przycisku rozbudowy. Po kliknięciu przycisku rozbudowy `CTaskDialog` Wyświetla *strExpandedInformation* i zmiany etykiety *strExpandedLabel*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootericon"></a>  CTaskDialog::SetFooterIcon

Aktualizuje ikonę stopki `CTaskDialog`.

```
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>Parametry

*hFooterIcon*<br/>
[in] Nowa ikona dla `CTaskDialog`.

*lpszFooterIcon*<br/>
[in] Nowa ikona dla `CTaskDialog`.

### <a name="remarks"></a>Uwagi

Ikona stopka jest wyświetlana w dolnej części [klasa CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Można ją skojarzyć tekst stopki. Możesz zmienić tekst stopki z [CTaskDialog::SetFooterText](#setfootertext).

Ta metoda wyrzuca wyjątek z [upewnij się, że](diagnostic-services.md#ensure) — makro Jeśli `CTaskDialog` wyświetleniem lub parametr wejściowy jest wartością NULL.

A `CTaskDialog` może akceptować tylko `HICON` lub `LPCWSTR` jako ikona stopki. To ustawienie jest konfigurowane przez ustawienie opcji TDF_USE_HICON_FOOTER w konstruktorze lub [CTaskDialog::SetOptions](#setoptions). Domyślnie `CTaskDialog` jest skonfigurowany do używania `LPCWSTR` jako typ danych wejściowych dla ikony w stopce. Ta metoda generuje wyjątek, Jeśli spróbujesz ustawić ikonę przy użyciu typu nieodpowiednie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootertext"></a>  CTaskDialog::SetFooterText

Aktualizuje tekst w stopce `CTaskDialog`.

```
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>Parametry

*strFooterText*<br/>
[in] Nowy tekst stopki.

### <a name="remarks"></a>Uwagi

Ikony w stopce pojawia się obok tekst stopki w dolnej części `CTaskDialog`. Możesz zmienić ikonę stopki z [CTaskDialog::SetFooterIcon](#setfootericon).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmainicon"></a>  CTaskDialog::SetMainIcon

Aktualizuje ikony głównej o `CTaskDialog`.

```
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>Parametry

*hMainIcon*<br/>
[in] Nowa ikona.

*lpszMainIcon*<br/>
[in] Nowa ikona.

### <a name="remarks"></a>Uwagi

Ta metoda wyrzuca wyjątek z [upewnij się, że](diagnostic-services.md#ensure) — makro Jeśli `CTaskDialog` wyświetleniem lub parametr wejściowy jest wartością NULL.

A `CTaskDialog` może akceptować tylko `HICON` lub `LPCWSTR` jako głównej ikony. Można to skonfigurować przez ustawienie opcji TDF_USE_HICON_MAIN w konstruktorze lub w [CTaskDialog::SetOptions](#setoptions) metody. Domyślnie `CTaskDialog` jest skonfigurowany do używania `LPCWSTR` jako typ danych wejściowych dla głównej ikony. Ta metoda generuje wyjątek, Jeśli spróbujesz ustawić ikonę przy użyciu typu nieodpowiednie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmaininstruction"></a>  CTaskDialog::SetMainInstruction

Aktualizuje głównego instrukcja `CTaskDialog`.

```
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>Parametry

*strInstructions*<br/>
[in] Nowy główny instrukcji.

### <a name="remarks"></a>Uwagi

Instrukcja głównego `CTaskDialog` klasa jest tekst wyświetlany użytkownikowi dużych pogrubioną czcionką. Znajduje się w oknie dialogowym poniżej paska tytułu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setoptions"></a>  CTaskDialog::SetOptions

Konfiguruje opcje `CTaskDialog`.

```
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>Parametry

*nOptionFlag*<br/>
[in] Zestaw flag użytku `CTaskDialog`.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa wszystkie bieżące opcje `CTaskDialog`. Aby zachować bieżące opcje, należy pobrać je najpierw z [CTaskDialog::GetOptions](#getoptions) i połączyć je z opcjami, które chcesz ustawić.

Poniższa tabela zawiera listę wszystkich prawidłowych opcji.

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|Włącza hiperłącza w `CTaskDialog`.|
|TDF_USE_HICON_MAIN|Konfiguruje `CTaskDialog` używać `HICON` dla głównej ikony. Alternatywą jest użycie `LPCWSTR`.|
|TDF_USE_HICON_FOOTER|Konfiguruje `CTaskDialog` używać `HICON` ikony w stopce. Alternatywą jest użycie `LPCWSTR`.|
|TDF_ALLOW_DIALOG_CANCELLATION|Umożliwia użytkownikowi zamknąć `CTaskDialog` za pomocą klawiatury lub przy użyciu ikony w prawym górnym rogu okna dialogowego, nawet wtedy, gdy **anulować** przycisk nie jest włączona. Jeśli ta flaga nie jest ustawiona i **anulować** przycisk nie jest włączona, użytkownik nie może zamknąć okno dialogowe za pomocą klawiszy Alt + F4, klawisz ESC lub przycisk Zamknij na pasku tytułu.|
|TDF_USE_COMMAND_LINKS|Konfiguruje `CTaskDialog` używania kontrolek przycisku polecenia.|
|TDF_USE_COMMAND_LINKS_NO_ICON|Konfiguruje `CTaskDialog` używanie kontrolek przycisku polecenia bez wyświetlanie ikony obok formantu. TDF_USE_COMMAND_LINKS zastępuje TDF_USE_COMMAND_LINKS_NO_ICON.|
|TDF_EXPAND_FOOTER_AREA|Wskazuje, że obecnie podzielonego obszar rozszerzenia.|
|TDF_EXPANDED_BY_DEFAULT|Określa, czy obszar rozszerzenia jest rozwinięta, domyślnie.|
|TDF_VERIFICATION_FLAG_CHECKED|Wskazuje, że pole wyboru weryfikacji jest aktualnie wybrany.|
|TDF_SHOW_PROGRESS_BAR|Konfiguruje `CTaskDialog` ma być wyświetlany pasek postępu.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|Konfiguruje się pasek postępu neon pasek postępu. Jeśli ta opcja jest włączona, należy ustawić TDF_SHOW_PROGRESS_BAR zapewnienie oczekiwanego zachowania.|
|TDF_CALLBACK_TIMER|Oznacza to, że `CTaskDialog` wywołania zwrotnego interwał wynosi około 200 ms.|
|TDF_POSITION_RELATIVE_TO_WINDOW|Konfiguruje `CTaskDialog` do wyśrodkowany względem okna nadrzędnego. Jeśli ta flaga nie jest włączona, `CTaskDialog` jest wyśrodkowywana względem monitora.|
|TDF_RTL_LAYOUT|Konfiguruje `CTaskDialog` układu czytania od prawej do lewej.|
|TDF_NO_DEFAULT_RADIO_BUTTON|Wskazuje, że nie przycisk radiowy zostanie wybrany podczas `CTaskDialog` pojawia się.|
|TDF_CAN_BE_MINIMIZED|Umożliwia użytkownikowi zminimalizować `CTaskDialog`. Do obsługi tej opcji `CTaskDialog` nie może być modalnych. MFC nie obsługuje tej opcji, ponieważ MFC nie obsługuje niemodalne `CTaskDialog`.|

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setprogressbarmarquee"></a>  CTaskDialog::SetProgressBarMarquee

Konfiguruje pasek neon `CTaskDialog` i dodaje go do okna dialogowego.

```
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>Parametry

*bWłączony*<br/>
[in] Wartość TRUE powoduje włączenie paskiem zaznaczenia. Wartość FALSE, aby wyłączyć na pasku neon i usuń go z `CTaskDialog`.

*nMarqueeSpeed*<br/>
[in] Liczba całkowita, która określa szybkość pasek zaznaczenia.

### <a name="remarks"></a>Uwagi

Zostanie wyświetlony pasek zaznaczenia pola poniżej tekstu głównego elementu `CTaskDialog` klasy.

Użyj *nMarqueeSpeed* można ustawić prędkość pasek neon; większe wartości wskazują niższej szybkości. Wartość 0 dla *nMarqueeSpeed* sprawia, że pasek neon przenoszenie z szybkością domyślny dla Windows.

Ta metoda wyrzuca wyjątek z [upewnij się, że](diagnostic-services.md#ensure) — makro Jeśli *nMarqueeSpeed* jest mniejszy niż 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarposition"></a>  CTaskDialog::SetProgressBarPosition

Ustawia położenie paska postępu.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parametry

*nProgressPos*<br/>
[in] Pozycja paska postępu.

### <a name="remarks"></a>Uwagi

Ta metoda wyrzuca wyjątek z [upewnij się, że](diagnostic-services.md#ensure) — makro Jeśli *nProgressPos* nie znajduje się w zakresie pasek postępu. Można zmienić zakres pasek postępu przy użyciu [CTaskDialog::SetProgressBarRange](#setprogressbarrange).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarrange"></a>  CTaskDialog::SetProgressBarRange

Dopasowuje zakresu pasek postępu.

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parametry

*nRangeMin*<br/>
[in] Dolna granica pasek postępu.

*nRangeMax*<br/>
[in] Górna granica pasek postępu.

### <a name="remarks"></a>Uwagi

Pozycja paska postępu jest względem *nRangeMin* i *nRangeMax*. Na przykład jeśli *nRangeMin* wynosi 50 i *nRangeMax* to 100, położenie 75 jest w połowie między pasek postępu. Użyj [CTaskDialog::SetProgressBarPosition](#setprogressbarposition) można ustawić położenie paska postępu.

Aby wyświetlić pasek postępu, opcja, którą TDF_SHOW_PROGRESS_BAR musi być włączona i TDF_SHOW_MARQUEE_PROGRESS_BAR nie mogą być włączone. Ta metoda automatycznie ustawia TDF_SHOW_PROGRESS_BAR i czyści TDF_SHOW_MARQUEE_PROGRESS_BAR. Użyj [CTaskDialog::SetOptions](#setoptions) ręcznie zmienić opcje dla tego wystąpienia [klasa CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

Ta metoda wyrzuca wyjątek z [upewnij się, że](diagnostic-services.md#ensure) — makro Jeśli *nRangeMin* jest nie mniejsza niż *nRangeMax*. Ta metoda również zgłasza wyjątek, jeśli `CTaskDialog` są już wyświetlane i ma neon pasek postępu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarstate"></a>  CTaskDialog::SetProgressBarState

Ustawia stan pasek postępu i wyświetla go na `CTaskDialog`.

```
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>Parametry

*nState*<br/>
[in] Stan pasek postępu. Zobacz sekcję Spostrzeżenia, aby możliwe wartości.

### <a name="remarks"></a>Uwagi

Ta metoda wyrzuca wyjątek z [upewnij się, że](diagnostic-services.md#ensure) — makro Jeśli `CTaskDialog` są już wyświetlane i ma neon pasek postępu.

Poniższa tabela zawiera listę możliwych wartości dla *nInformacje*. W tych przypadkach pasek postępu wypełni kolorem regularne aż do napotkania pozycja wyznaczonym tabulatora. W tym momencie zmieni kolor na podstawie stanu.

|||
|-|-|
|PBST_NORMAL|Po postępu wypełni paska, `CTaskDialog` nie zmienia kolor paska. Domyślnie pasek regularne ma kolor zielony.|
|PBST_ERROR|Po postępu wypełni paska, `CTaskDialog` zmienia kolor paska koloru błędu. Domyślnie jest to czerwone.|
|PBST_PAUSED|Po postępu wypełni paska, `CTaskDialog` zmienia kolor paska koloru wstrzymania. Domyślnie jest to żółty.|

Można ustawić, gdy pasek postępu zatrzymuje się z [CTaskDialog::SetProgressBarPosition](#setprogressbarposition).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setradiobuttonoptions"></a>  CTaskDialog::SetRadioButtonOptions

Włącza lub wyłącza przycisk radiowy.

```
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*nRadioButtonID*<br/>
[in] Identyfikator kontrolki przycisku radiowego.

*bWłączony*<br/>
[in] Wartość TRUE, aby włączyć przycisk radiowy; Wartość FALSE umożliwia wyłączenie przycisku radiowego.

### <a name="remarks"></a>Uwagi

Ta metoda wyrzuca wyjątek z [upewnij się, że](diagnostic-services.md#ensure) — makro Jeśli *nRadioButtonID* nie jest prawidłowym Identyfikatorem dla przycisku radiowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setverificationcheckbox"></a>  CTaskDialog::SetVerificationCheckbox

Ustawia stan zaznaczenia pola wyboru weryfikacji.

```
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>Parametry

*bChecked*<br/>
[in] Wartość true, aby pole wyboru weryfikacji wybrano podczas `CTaskDialog` jest wyświetlana; Wartość FALSE, aby zaznaczyć pole wyboru weryfikacji niezaznaczoną, kiedy `CTaskDialog` jest wyświetlana.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setverificationcheckboxtext"></a>  CTaskDialog::SetVerificationCheckboxText

Ustawia tekst, który jest wyświetlany po prawej stronie pola wyboru weryfikacji.

```
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>Parametry

*strVerificationText*<br/>
[in] Tekst, ta metoda jest wyświetlany obok pola wyboru weryfikacji.

### <a name="remarks"></a>Uwagi

Ta metoda wyrzuca wyjątek z [upewnij się, że](diagnostic-services.md#ensure) — makro, jeśli to wystąpienie `CTaskDialog` klasy są już wyświetlane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setwindowtitle"></a>  CTaskDialog::SetWindowTitle

Ustawia tytuł elementu `CTaskDialog`.

```
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>Parametry

*strWindowTitle*<br/>
[in] Nowy tytuł `CTaskDialog`.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="showdialog"></a>  CTaskDialog::ShowDialog

Tworzy i wyświetla `CTaskDialog`.

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
[in] Ciąg używany dla zawartości `CTaskDialog`.

*strMainInstruction*<br/>
[in] Instrukcja głównego `CTaskDialog`.

*strTitle*<br/>
[in] Tytuł `CTaskDialog`.

*nIDCommandControlsFirst*<br/>
[in] Identyfikator ciągu pierwszego polecenia.

*nIDCommandControlsLast*<br/>
[in] Identyfikator ciągu ostatnie polecenie.

*nCommonButtons*<br/>
[in] Maska przycisków, aby dodać do `CTaskDialog`.

*nTaskDialogOptions*<br/>
[in] Zestaw opcji dla `CTaskDialog`.

*strFooter*<br/>
[in] Ciąg do użycia jako stopki.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która odnosi się do wybranej przez użytkownika.

### <a name="remarks"></a>Uwagi

Ta metoda statyczna umożliwia utworzenie wystąpienia `CTaskDialog` klasy bez jawnego tworzenia `CTaskDialog` obiektu w kodzie. Ponieważ nie istnieje żadne `CTaskDialog` obiektu, nie można wywołać innych metod `CTaskDialog` użycie tej metody do wyświetlenia `CTaskDialog` użytkownikowi.

Ta metoda tworzy kontrolek przycisku polecenia przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów ma kilka ciągów przy użyciu parametrów skojarzonych identyfikatorów. Metoda ta umożliwia dodanie polecenia kontrolki przycisku dla każdego prawidłowego wpisu w tabeli ciągów między *nIDCommandControlsFirst* i *nCommandControlsLast*włącznie. Te kontrolki przycisku polecenia parametry w tabeli ciągów jest podpis formantu i identyfikator ciągu jest identyfikatorem formantu.

Zobacz [CTaskDialog::SetOptions](#setoptions) listę prawidłowych opcji.

`CTaskDialog` Zamyka się, gdy użytkownik wybierze przycisk wspólnej formant łącza polecenie lub zamknie `CTaskDialog`. Wartość zwracana jest identyfikator, który wskazuje, jak użytkownik zamknięte okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="taskdialogcallback"></a>  CTaskDialog::TaskDialogCallback

Struktura wywołuje tę metodę w odpowiedzi na różne komunikaty Windows.

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

*hwnd*<br/>
[in] Dojście do `m_hWnd` struktury dla `CTaskDialog`.

*uNotification*<br/>
[in] Określa komunikat, który wygenerowany kod powiadomień.

*wParam*<br/>
[in] Więcej informacji na temat wiadomości.

*lParam*<br/>
[in] Więcej informacji na temat wiadomości.

*dwRefData*<br/>
[in] Wskaźnik do `CTaskDialog` obiekt, który dotyczy komunikat wywołania zwrotnego.

### <a name="return-value"></a>Wartość zwracana

Zależy od kodu określonych powiadomień. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Domyślna implementacja klasy `TaskDialogCallback` obsługuje szczegółowy komunikat o błędzie, a następnie wywołuje odpowiednią od metody [klasa CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Na przykład w odpowiedzi na komunikat TDN_BUTTON_CLICKED `TaskDialogCallback` wywołania [CTaskDialog::OnCommandControlClick](#oncommandcontrolclick).

Wartości *wParam* i *lParam* są zależne od szczegółowy komunikat o błędzie wygenerowane. Istnieje możliwość dla jednego lub obu tych wartości, być pusta. W poniższej tabeli wymieniono domyślne powiadomienia, które są obsługiwane i jakie wartości *wParam* i *lParam* reprezentują. Jeśli zastąpisz tę metodę w klasie pochodnej, należy zaimplementować kod wywołania zwrotnego dla każdego komunikatu w tabeli poniżej.

|Komunikat z powiadomieniem|*wParam* wartość|*lParam* wartość|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|Nie używany.|Nie używany.|
|TDN_NAVIGATED|Nie używany.|Nie używany.|
|TDN_BUTTON_CLICKED|Przycisk polecenia sterowania identyfikatora.|Nie używany.|
|TDN_HYPERLINK_CLICKED|Nie używany.|A [LPCWSTR](/windows/desktop/WinProg/windows-data-types) strukturę, która zawiera link.|
|TDN_TIMER|Czas w milisekundach, ponieważ `CTaskDialog` został utworzony lub został zresetowany przez czasomierz.|Nie używany.|
|TDN_DESTROYED|Nie używany.|Nie używany.|
|TDN_RADIO_BUTTON_CLICKED|Identyfikator przycisku radiowego|Nie używany.|
|TDN_DIALOG_CONSTRUCTED|Nie używany.|Nie używany.|
|TDN_VERIFICATION_CLICKED|1, jeśli pole wyboru jest zaznaczone, 0, jeśli nie jest.|Nie używany.|
|TDN_HELP|Nie używany.|Nie używany.|
|TDN_EXPANDO_BUTTON_CLICKED|0, jeśli obszar rozszerzenia jest zwinięte; różna od zera, jeśli jest wyświetlany tekst rozszerzenia.|Nie używany.|

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Przewodnik: Dodawanie obiektu CTaskDialog do aplikacji](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
