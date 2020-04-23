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
ms.openlocfilehash: 79f52d275d360cf8447b8977b8196ea5f95eacd8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752284"
---
# <a name="ctaskdialog-class"></a>Klasa CTaskDialog

Wyskakujące okno dialogowe, które działa jak okno komunikatu, ale może wyświetlać dodatkowe informacje użytkownikowi. Obejmuje `CTaskDialog` również funkcje zbierania informacji od użytkownika.

## <a name="syntax"></a>Składnia

```
class CTaskDialog : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[CTaskDialog::CTaskDialog](#ctaskdialog)|Konstruuje `CTaskDialog` obiekt.|

### <a name="methods"></a>Metody

|||
|-|-|
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|Dodaje kontrolkę przycisku polecenia do pliku `CTaskDialog`.|
|[CTaskDialog::AddRadioButton](#addradiobutton)|Dodaje przycisk radiowy `CTaskDialog`do pliku .|
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|Klika formant przycisku polecenia lub wspólny przycisk programowo.|
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Automatycznie klika przycisk radiowy.|
|[CTaskDialog::DoModal](#domodal)|Wyświetla `CTaskDialog`plik .|
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Pobiera liczbę dostępnych wspólnych przycisków.|
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Konwertuje standardowy przycisk Systemu Windows na `CTaskDialog` typ przycisku wspólnego skojarzonego z klasą.|
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|Konwertuje jeden z typowych typów `CTaskDialog` przycisków skojarzonych z klasą na standardowy przycisk systemu Windows.|
|[CTaskDialog::GetOptions](#getoptions)|Zwraca flagi opcji `CTaskDialog`dla tego .|
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|Zwraca kontrolka wybranego przycisku polecenia.|
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Zwraca wybrany przycisk radiowy.|
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Pobiera stan pola wyboru weryfikacji.|
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|Określa, czy jest włączony formant przycisku polecenia, czy wspólny.|
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|Określa, czy przycisk radiowy jest włączony.|
|[CTaskDialog::IsSupported](#issupported)|Określa, czy komputer, na który `CTaskDialog`jest uruchomiona aplikacja, obsługuje plik .|
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Dodaje formanty przycisku polecenia przy użyciu danych z tabeli ciągów.|
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|Dodaje przyciski radiowe przy użyciu danych z tabeli ciągów.|
|[CTaskDialog::NavigateTo](#navigateto)|Przenosi fokus `CTaskDialog`do innego .|
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|Struktura wywołuje tę metodę, gdy użytkownik kliknie kontrolkę przycisku polecenia.|
|[CTaskDialog::OnCreate](#oncreate)|Struktura wywołuje tę metodę po `CTaskDialog`tym, jak tworzy .|
|[CTaskDialog::OnDestroy](#ondestroy)|Struktura wywołuje tę metodę bezpośrednio przed `CTaskDialog`zniszczeniem .|
|[CTaskDialog::OnRozwińButtonClick](#onexpandbuttonclick)|Struktura wywołuje tę metodę, gdy użytkownik kliknie przycisk rozszerzenia.|
|[CTaskDialog::OnHelp](#onhelp)|Struktura wywołuje tę metodę, gdy użytkownik żąda pomocy.|
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|Struktura wywołuje tę metodę, gdy użytkownik kliknie hiperłącze.|
|[CTaskDialog::OnInit](#oninit)|Struktura wywołuje tę metodę, `CTaskDialog` gdy jest inicjowany.|
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|Struktura wywołuje tę metodę, gdy użytkownik przenosi fokus w odniesieniu do formantów na `CTaskDialog`.|
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|Struktura wywołuje tę metodę, gdy użytkownik wybiera kontrolkę przycisku radiowego.|
|[CTaskDialog::OnTimer](#ontimer)|Struktura wywołuje tę metodę, gdy czasomierz wygasa.|
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|Struktura wywołuje tę metodę, gdy użytkownik kliknie pole wyboru weryfikacji.|
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|Usuwa wszystkie kontrolki `CTaskDialog`poleceń z pliku .|
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|Usuwa wszystkie przyciski radiowe z pliku `CTaskDialog`.|
|[CTaskDialog::SetCommandControlOptions](#setcommandcontroloptions)|Aktualizuje kontrolkę `CTaskDialog`przycisku polecenia na pliku .|
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|Aktualizuje podzbiór typowych przycisków, które mają być włączone i wymagają elewacji funkcji Kontrola konta użytkownika.|
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|Dodaje typowe przyciski do pliku `CTaskDialog`.|
|[CTaskDialog::SetContent](#setcontent)|Aktualizuje zawartość `CTaskDialog`pliku .|
|[CTaskDialog::SetDefaultCommandControl](#setdefaultcommandcontrol)|Określa domyślny kontrolka przycisku polecenia.|
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|Określa domyślny przycisk opcji.|
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|Dostosowuje szerokość pliku `CTaskDialog`.|
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|Aktualizuje obszar rozbudowy pliku `CTaskDialog`.|
|[CTaskDialog::SetFooterIcon](#setfootericon)|Aktualizuje ikonę stopki dla pliku `CTaskDialog`.|
|[CTaskDialog::SetFooterText](#setfootertext)|Aktualizuje tekst na stopce `CTaskDialog`pliku .|
|[CTaskDialog::SetMainIcon](#setmainicon)|Aktualizuje główną `CTaskDialog`ikonę pliku .|
|[CTaskDialog::SetMainInstruction](#setmaininstruction)|Aktualizuje główną `CTaskDialog`instrukcję .|
|[CTaskDialog::SetOptions](#setoptions)|Konfiguruje opcje `CTaskDialog`dla pliku .|
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Konfiguruje pasek ramki zaznaczenia dla `CTaskDialog` i dodaje go do okna dialogowego.|
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|Dostosowuje położenie paska postępu.|
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|Dostosowuje zakres paska postępu.|
|[CTaskDialog::SetProgressBarState](#setprogressbarstate)|Ustawia stan paska postępu i wyświetla `CTaskDialog`go na pliku .|
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Włącza lub wyłącza przycisk radiowy.|
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|Ustawia sprawdzony stan pola wyboru weryfikacji.|
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Ustawia tekst po prawej stronie pola wyboru weryfikacji.|
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|Ustawia tytuł pliku `CTaskDialog`.|
|[CTaskDialog::ShowDialog](#showdialog)|Tworzy i `CTaskDialog`wyświetla plik .|
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|Struktura wywołuje to w odpowiedzi na różne komunikaty systemu Windows.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|`m_aButtons`|Tablica przycisków poleceń `CTaskDialog`steruje przyciskiem .|
|`m_aRadioButtons`|Tablica elementów sterujących `CTaskDialog`przyciskiem opcji dla pliku .|
|`m_bVerified`|`TRUE`wskazuje, że pole wyboru weryfikacji jest zaznaczone; `FALSE` oznacza, że tak nie jest.|
|`m_footerIcon`|Ikona w stopce `CTaskDialog`pliku .|
|`m_hWnd`|Uchwyt do okna dla `CTaskDialog`.|
|`m_mainIcon`|Główna ikona `CTaskDialog`pliku .|
|`m_nButtonDisabled`|Maska wskazująca, które z typowych przycisków są wyłączone.|
|`m_nButtonElevation`|Maska wskazująca, który z typowych przycisków wymaga podniesienia funkcji Kontrola konta użytkownika.|
|`m_nButtonId`|Identyfikator wybranego przycisku polecenia.|
|`m_nCommonButton`|Maska wskazująca, które typowe przyciski `CTaskDialog`są wyświetlane na pliku .|
|`m_nDefaultCommandControl`|Identyfikator formantu przycisku polecenia, który `CTaskDialog` jest wybrany podczas wyświetlania.|
|`m_nDefaultRadioButton`|Identyfikator kontrolki przycisku radiowego, `CTaskDialog` który jest wybrany podczas wyświetlania.|
|`m_nFlags`|Maska wskazująca opcje dla `CTaskDialog`pliku .|
|`m_nProgressPos`|Bieżąca pozycja paska postępu.  Ta wartość musi `m_nProgressRangeMin` `m_nProgressRangeMax`być między i .|
|`m_nProgressRangeMax`|Maksymalna wartość paska postępu.|
|`m_nProgressRangeMin`|Minimalna wartość paska postępu.|
|`m_nProgressState`|Stan paska postępu. Aby uzyskać więcej informacji, zobacz [CTaskDialog::SetProgressBarState](#setprogressbarstate).|
|`m_nRadioId`|Identyfikator wybranego przycisku radiowego.|
|`m_nWidth`|Szerokość `CTaskDialog` w pikselach.|
|`m_strCollapse`|Ciąg wyświetlany `CTaskDialog` po prawej stronie pola rozszerzeń, gdy rozwinięte informacje są ukryte.|
|`m_strContent`|Ciąg zawartości pliku `CTaskDialog`.|
|`m_strExpand`|Ciąg wyświetlany `CTaskDialog` po prawej stronie pola rozszerzeń, gdy wyświetlane są rozwinięte informacje.|
|`m_strFooter`|Stopka `CTaskDialog`.|
|`m_strInformation`|Rozszerzone informacje `CTaskDialog`dla .|
|`m_strMainInstruction`|Główną instrukcją `CTaskDialog`.|
|`m_strTitle`|Tytuł . `CTaskDialog`|
|`m_strVerification`|Ciąg wyświetlany `CTaskDialog` po prawej stronie pola wyboru weryfikacji.|

## <a name="remarks"></a>Uwagi

Klasa `CTaskDialog` zastępuje standardowe okno komunikatu systemu Windows i ma dodatkowe funkcje, takie jak nowe formanty do zbierania informacji od użytkownika. Ta klasa znajduje się w bibliotece MFC w programie Visual Studio 2010 i nowszych. Jest `CTaskDialog` dostępny począwszy od systemu Windows Vista. Starsze wersje systemu Windows `CTaskDialog` nie mogą wyświetlać obiektu. Służy `CTaskDialog::IsSupported` do określania w czasie wykonywania, czy bieżący użytkownik może wyświetlić okno dialogowe zadania. Standardowe okno komunikatu systemu Windows jest nadal obsługiwane.

Jest `CTaskDialog` dostępna tylko podczas tworzenia aplikacji przy użyciu biblioteki Unicode.

Ma `CTaskDialog` dwa różne konstruktory. Jeden konstruktor umożliwia określenie dwóch przycisków poleceń i maksymalnie sześciu zwykłych formantów przycisków. Po utworzeniu `CTaskDialog`pliku . Drugi konstruktor nie obsługuje żadnych przycisków poleceń, ale można dodać nieograniczoną liczbę zwykłych formantów przycisków. Aby uzyskać więcej informacji na temat konstruktorów, zobacz [CTaskDialog::CTaskDialog](#ctaskdialog).

Na poniższej ilustracji przedstawiono przykład, `CTaskDialog` aby zilustrować lokalizację niektórych formantów.

![Przykład CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "Przykład CTaskDialog") <br/>
Próbka CTaskDialog

## <a name="requirements"></a>Wymagania

**Minimalny wymagany system operacyjny:** Windows Vista

**Nagłówek:** afxtaskdialog.h

## <a name="ctaskdialogaddcommandcontrol"></a><a name="addcommandcontrol"></a>CTaskDialog::AddCommandControl

Dodaje nowy kontrolka `CTaskDialog`przycisku polecenia do pliku .

```cpp
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parametry

*nCommandControlID (Identyfikator kontrolera)*<br/>
[w] Numer identyfikacyjny sterowania sterowaniem poleceniem.

*strCaption (strCaption)*<br/>
[w] Ciąg, który `CTaskDialog` wyświetla użytkownikowi. Ten ciąg służy do wyjaśniania celu polecenia.

*bWłach*<br/>
[w] Parametr logiczny wskazujący, czy nowy przycisk jest włączony czy wyłączony.

*bWymaganieWychanie*<br/>
[w] Parametr logiczny, który wskazuje, czy polecenie wymaga podniesienia uprawnień.

### <a name="remarks"></a>Uwagi

Może `CTaskDialog Class` wyświetlać nieograniczoną liczbę elementów sterujących przyciskami poleceń. Jeśli jednak `CTaskDialog` zostanie wyświetlony dowolny przycisk polecenia, może wyświetlić maksymalnie sześć przycisków. Jeśli `CTaskDialog` a nie ma elementów sterujących przyciskiem polecenia, może wyświetlać nieograniczoną liczbę przycisków.

Gdy użytkownik wybierze kontrolkę `CTaskDialog` przycisku polecenia, zamyka. Jeśli aplikacja wyświetla okno dialogowe przy użyciu [CTaskDialog::DoModal](#domodal), `DoModal` zwraca *nCommandControlID* wybranego przycisku polecenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogaddradiobutton"></a><a name="addradiobutton"></a>CTaskDialog::AddRadioButton

Dodaje przycisk radiowy `CTaskDialog`do pliku .

```cpp
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parametry

*nRadioButtonid*<br/>
[w] Numer identyfikacyjny przycisku radiowego.

*strCaption (strCaption)*<br/>
[w] Ciąg wyświetlany `CTaskDialog` obok przycisku opcji.

*bWłach*<br/>
[w] Parametr logiczny wskazujący, czy przycisk radiowy jest włączony.

### <a name="remarks"></a>Uwagi

Przyciski radiowe [dla CTaskDialog Klasy](../../mfc/reference/ctaskdialog-class.md) umożliwiają zbieranie informacji od użytkownika. Użyj funkcji [CTaskDialog::GetSelectedRadioButtonID,](#getselectedradiobuttonid) aby określić, który przycisk opcji jest zaznaczony.

Nie `CTaskDialog` wymaga, aby parametry *nRadioButtonID* były unikatowe dla każdego przycisku radiowego. Jednak może wystąpić nieoczekiwane zachowanie, jeśli nie używasz odrębnego identyfikatora dla każdego przycisku radiowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogclickcommandcontrol"></a><a name="clickcommandcontrol"></a>CTaskDialog::ClickCommandControl

Klika formant przycisku polecenia lub wspólny przycisk programowo.

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>Parametry

*nCommandControlID (Identyfikator kontrolera)*<br/>
[w] Identyfikator polecenia formantu do kliknięcia.

### <a name="remarks"></a>Uwagi

Ta metoda generuje komunikat systemu Windows TDM_CLICK_BUTTON.

## <a name="ctaskdialogclickradiobutton"></a><a name="clickradiobutton"></a>CTaskDialog::ClickRadioButton

Automatycznie klika przycisk radiowy.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parametry

*nRadioButtonid*<br/>
[w] Identyfikator przycisku radiowego do kliknięcia.

### <a name="remarks"></a>Uwagi

Ta metoda generuje komunikat systemu Windows TDM_CLICK_RADIO_BUTTON.

## <a name="ctaskdialogctaskdialog"></a><a name="ctaskdialog"></a>CTaskDialog::CTaskDialog

Tworzy wystąpienie [klasy CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

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

*strContent (podtrzymuje)*<br/>
[w] Ciąg do użycia dla zawartości `CTaskDialog`pliku .

*strMainInstrukcja*<br/>
[w] Główną instrukcją `CTaskDialog`.

*strTitle (napis)*<br/>
[w] Tytuł . `CTaskDialog`

*nKłamiony*<br/>
[w] Maska wspólnych przycisków, aby `CTaskDialog`dodać do pliku .

*nTaskDialogOptions*<br/>
[w] Zestaw opcji do użycia `CTaskDialog`dla pliku .

*strFooter (ul.*<br/>
[w] Ciąg do użycia jako stopka.

*nIDCommandControlsFirst*<br/>
[w] Identyfikator ciągu pierwszego polecenia.

*nIDCommandControlsLast*<br/>
[w] Identyfikator ciągu ostatniego polecenia.

### <a name="remarks"></a>Uwagi

Istnieją dwa sposoby, które `CTaskDialog` można dodać do aplikacji. Pierwszym sposobem jest użycie jednego z konstruktorów do utworzenia `CTaskDialog` i wyświetlenia go za pomocą [CTaskDialog::DoModal](#domodal). Drugim sposobem jest użycie funkcji statycznej [CTaskDialog::ShowDialog](#showdialog), która `CTaskDialog` umożliwia wyświetlanie bez `CTaskDialog` jawnego tworzenia obiektu.

Drugi konstruktor tworzy formanty przycisku polecenia przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów zawiera kilka ciągów o skojarzonych identyfikatorach ciągów. Ta metoda dodaje kontrolkę przycisku polecenia dla każdego prawidłowego wpisu w tabeli ciągów między *nIDCommandControlsFirst* i *nCommandControlsLast*, włącznie. Dla tych formantów przycisku polecenia ciąg w tabeli ciągów jest podpis formantu i identyfikator ciągu jest identyfikator formantu.

Zobacz [CTaskDialog::SetOptions](#setoptions) listę prawidłowych opcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogdomodal"></a><a name="domodal"></a>CTaskDialog::DoModal

Pokazuje `CTaskDialog` i sprawia, że modalne.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parametry

*hRoszt*<br/>
[w] Okno nadrzędne `CTaskDialog`dla pliku .

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita odpowiadająca wyborowi dokonanemu przez użytkownika.

### <a name="remarks"></a>Uwagi

Wyświetla to wystąpienie [CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Następnie aplikacja czeka na zamknięcie okna dialogowego przez użytkownika.

Zamyka `CTaskDialog` się, gdy użytkownik wybierze wspólny przycisk, kontrolkę `CTaskDialog`łącza poleceń lub zamknie plik . Zwracana wartość jest identyfikatorem wskazującym, w jaki sposób użytkownik zamknął okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetcommonbuttoncount"></a><a name="getcommonbuttoncount"></a>CTaskDialog::GetCommonButtonCount

Pobiera liczbę typowych przycisków.

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba dostępnych wspólnych przycisków.

### <a name="remarks"></a>Uwagi

Typowe przyciski są domyślne przyciski, które można podać [do CTaskDialog::CTaskDialog](#ctaskdialog). [Klasa CTaskDialog](../../mfc/reference/ctaskdialog-class.md) wyświetla przyciski wzdłuż dolnej części okna dialogowego.

Wyliczona lista przycisków znajduje się w pliku CommCtrl.h.

## <a name="ctaskdialoggetcommonbuttonflag"></a><a name="getcommonbuttonflag"></a>CTaskDialog::GetCommonButtonFlag

Konwertuje standardowy przycisk Systemu Windows na typ przycisku wspólnego skojarzonego z [klasą CTaskDialog](../../mfc/reference/ctaskdialog-class.md).

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>Parametry

*nButtonId (PrzyciskId)*<br/>
[w] Standardowa wartość przycisku Systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Wartość odpowiedniego `CTaskDialog` wspólnego przycisku. Jeśli nie ma odpowiedniego wspólnego przycisku, ta metoda zwraca wartość 0.

## <a name="ctaskdialoggetcommonbuttonid"></a><a name="getcommonbuttonid"></a>CTaskDialog::GetCommonButtonId

Konwertuje jeden z typowych typów przycisków skojarzonych z [klasą CTaskDialog](../../mfc/reference/ctaskdialog-class.md) na standardowy przycisk Systemu Windows.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>Parametry

*żużel*<br/>
[w] Typ przycisku typowe skojarzone z klasą. `CTaskDialog`

### <a name="return-value"></a>Wartość zwracana

Wartość odpowiedniego standardowego przycisku Windows. Jeśli nie ma odpowiedniego przycisku systemu Windows, metoda zwraca wartość 0.

## <a name="ctaskdialoggetoptions"></a><a name="getoptions"></a>CTaskDialog::GetOptions

Zwraca flagi opcji `CTaskDialog`dla tego .

```
int GetOptions() const;
```

### <a name="return-value"></a>Wartość zwracana

Flagi dla `CTaskDialog`.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat opcji dostępnych dla [klasy CTaskDialog](../../mfc/reference/ctaskdialog-class.md), zobacz [CTaskDialog::SetOptions](#setoptions).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetselectedcommandcontrolid"></a><a name="getselectedcommandcontrolid"></a>CTaskDialog::GetSelectedCommandControlID

Zwraca kontrolka wybranego przycisku polecenia.

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator aktualnie wybranego przycisku polecenia.

### <a name="remarks"></a>Uwagi

Nie trzeba używać tej metody, aby pobrać identyfikator przycisku polecenia, który użytkownik wybrał. Ten identyfikator jest zwracany przez [CTaskDialog::DoModal](#domodal) lub [CTaskDialog::ShowDialog](#showdialog).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialoggetselectedradiobuttonid"></a><a name="getselectedradiobuttonid"></a>CTaskDialog::GetSelectedRadioButtonID

Zwraca wybrany przycisk radiowy.

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator wybranego przycisku radiowego.

### <a name="remarks"></a>Uwagi

Tej metody można użyć po zamknięciu okna dialogowego przez użytkownika w celu pobrania wybranego przycisku opcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialoggetverificationcheckboxstate"></a><a name="getverificationcheckboxstate"></a>CTaskDialog::GetVerificationCheckboxState

Pobiera stan pola wyboru weryfikacji.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zaznaczone jest pole wyboru, FALSE, jeśli nie jest.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogiscommandcontrolenabled"></a><a name="iscommandcontrolenabled"></a>CTaskDialog::IsCommandControlEnabled

Określa, czy jest włączony przycisk polecenia, czy przycisk.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>Parametry

*nCommandControlID (Identyfikator kontrolera)*<br/>
[w] Identyfikator sterowania przyciskiem polecenia lub przycisku do przetestowania.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli formant jest włączony, FALSE, jeśli nie jest.

### <a name="remarks"></a>Uwagi

Za pomocą tej metody można określić dostępność zarówno formanty `CTaskDialog` przycisku polecenia, jak i typowe przyciski klasy*.

Jeśli *nCommandControlID* nie jest prawidłowym identyfikatorem `CTaskDialog` dla wspólnego przycisku lub formantu przycisku polecenia, ta metoda zgłasza wyjątek.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogisradiobuttonenabled"></a><a name="isradiobuttonenabled"></a>CTaskDialog::IsRadioButtonEnabled

Określa, czy przycisk radiowy jest włączony.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parametry

*nRadioButtonid*<br/>
[w] Identyfikator przycisku radiowego do przetestowania.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przycisk radiowy jest włączony, FALSE, jeśli nie jest.

### <a name="remarks"></a>Uwagi

Jeśli *nRadioButtonID* nie jest prawidłowym identyfikatorem przycisku radiowego, ta metoda zgłasza wyjątek.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogissupported"></a><a name="issupported"></a>CTaskDialog::IsSupported

Określa, czy komputer, na który `CTaskDialog`jest uruchomiona aplikacja, obsługuje plik .

```
static BOOL IsSupported();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli komputer `CTaskDialog`obsługuje ; FAŁSZ inaczej.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do określenia w czasie wykonywania, czy `CTaskDialog` komputer, który jest uruchomiony aplikacji obsługuje klasy. Jeśli komputer nie obsługuje `CTaskDialog`, należy podać inną metodę przekazywania informacji do użytkownika. Aplikacja ugo zostanie upaść, `CTaskDialog` jeśli spróbuje użyć `CTaskDialog` na komputerze, który nie obsługuje klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogloadcommandcontrols"></a><a name="loadcommandcontrols"></a>CTaskDialog::LoadCommandControls

Dodaje formanty przycisku polecenia przy użyciu danych z tabeli ciągów.

```cpp
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>Parametry

*nIDCommandControlsFirst*<br/>
[w] Identyfikator ciągu pierwszego polecenia.

*nIDCommandControlsLast*<br/>
[w] Identyfikator ciągu ostatniego polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy formanty przycisku polecenia przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów zawiera kilka ciągów o skojarzonych identyfikatorach ciągów. Nowe formanty przycisku polecenia dodane przy użyciu tej metody użyć ciągu dla podpisu formantu i identyfikatora ciągu dla identyfikatora formantu. Zakres wybranych ciągów jest dostarczany przez *nIDCommandControlsFirst* i *nCommandControlsLast*, włącznie. Jeśli istnieje pusty wpis w zakresie, metoda nie dodaje formantu przycisku polecenia dla tego wpisu.

Domyślnie nowe kontrolki przycisków poleceń są włączone i nie wymagają podniesienia uprawnień.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogloadradiobuttons"></a><a name="loadradiobuttons"></a>CTaskDialog::LoadRadioButtons

Dodaje kontrolki przycisku opcji przy użyciu danych z tabeli ciągów.

```cpp
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>Parametry

*nIDRadioButtonsPierwsz*<br/>
[w] Identyfikator ciągu pierwszego przycisku radiowego.

*nIDRadioButtonsLast*<br/>
[w] Identyfikator ciągu ostatniego przycisku radiowego.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy przyciski radiowe przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów zawiera kilka ciągów o skojarzonych identyfikatorach ciągów. Nowe przyciski radiowe dodane przy użyciu tej metody używają ciągu dla podpisu przycisku radiowego i identyfikatora ciągu dla identyfikatora przycisku radiowego. Zakres wybranych ciągów jest dostarczany przez *nIDRadioButtonsFirst* i *nRadioButtonsLast*, włącznie. Jeśli istnieje pusty wpis w zakresie, metoda nie dodaje przycisku radiowego dla tego wpisu.

Domyślnie nowe przyciski radiowe są włączone.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialognavigateto"></a><a name="navigateto"></a>CTaskDialog::NavigateTo

Przenosi fokus `CTaskDialog`do innego .

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>Parametry

*oTaskDialog*<br/>
[w] Ten, `CTaskDialog` który otrzymuje fokus.

### <a name="remarks"></a>Uwagi

Ta metoda ukrywa `CTaskDialog` prąd, gdy wyświetla *oTaskDialog*. *OTaskDialog* jest wyświetlany w tym samym `CTaskDialog`miejscu co bieżący .

## <a name="ctaskdialogoncommandcontrolclick"></a><a name="oncommandcontrolclick"></a>CTaskDialog::OnCommandControlClick

Struktura wywołuje tę metodę, gdy użytkownik kliknie kontrolkę przycisku polecenia.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>Parametry

*nCommandControlID (Identyfikator kontrolera)*<br/>
[w] Identyfikator formantu przycisku polecenia wybrany przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogoncreate"></a><a name="oncreate"></a>CTaskDialog::OnCreate

Struktura wywołuje tę metodę po `CTaskDialog`tym, jak tworzy .

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogondestroy"></a><a name="ondestroy"></a>CTaskDialog::OnDestroy

Struktura wywołuje tę metodę bezpośrednio przed `CTaskDialog`zniszczeniem .

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogonexpandbuttonclick"></a><a name="onexpandbuttonclick"></a>CTaskDialog::OnRozwińButtonClick

Struktura wywołuje tę metodę, gdy użytkownik kliknie przycisk rozszerzenia.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>Parametry

*bRozwiń*<br/>
[w] Wartość niezerowa wskazuje, że wyświetlane są dodatkowe informacje; 0 oznacza, że dodatkowe informacje są ukryte.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogonhelp"></a><a name="onhelp"></a>CTaskDialog::OnHelp

Struktura wywołuje tę metodę, gdy użytkownik żąda pomocy.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogonhyperlinkclick"></a><a name="onhyperlinkclick"></a>CTaskDialog::OnHyperlinkClick

Struktura wywołuje tę metodę, gdy użytkownik kliknie hiperłącze.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>Parametry

*strHref (strHref)*<br/>
[w] Ciąg reprezentujący hiperłącze.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) przed zwraca S_OK.

Zastąpi tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogoninit"></a><a name="oninit"></a>CTaskDialog::OnInit

Struktura wywołuje tę metodę, `CTaskDialog` gdy jest inicjowany.

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogonnavigatepage"></a><a name="onnavigatepage"></a>CTaskDialog::OnNavigatePage

Struktura wywołuje tę metodę w odpowiedzi na [CTaskDialog::NavigateTo](#navigateto) metody.

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogonradiobuttonclick"></a><a name="onradiobuttonclick"></a>CTaskDialog::OnRadioButtonClick

Struktura wywołuje tę metodę, gdy użytkownik wybiera kontrolkę przycisku radiowego.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>Parametry

*nRadioButtonid*<br/>
[w] Identyfikator kontrolki przycisku radiowego, który użytkownik kliknął.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogontimer"></a><a name="ontimer"></a>CTaskDialog::OnTimer

Struktura wywołuje tę metodę, gdy czasomierz wygasa.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>Parametry

*lCzas*<br/>
[w] Czas w milisekundach `CTaskDialog` od momentu utworzenia lub zresetowania czasomierza.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogonverificationcheckboxclick"></a><a name="onverificationcheckboxclick"></a>CTaskDialog::OnVerificationCheckboxClick

Struktura wywołuje tę metodę, gdy użytkownik kliknie pole wyboru weryfikacji.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>Parametry

*bSprawiona*<br/>
[w] PRAWDA wskazuje, że pole wyboru weryfikacji jest zaznaczone; FALSE oznacza, że nie jest.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca S_OK.

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby zaimplementować zachowanie niestandardowe.

## <a name="ctaskdialogremoveallcommandcontrols"></a><a name="removeallcommandcontrols"></a>CTaskDialog::RemoveAllCommandControls

Usuwa wszystkie kontrolki przycisku polecenia z pliku `CTaskDialog`.

```cpp
void RemoveAllCommandControls();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogremoveallradiobuttons"></a><a name="removeallradiobuttons"></a>CTaskDialog::RemoveAllRadioButtons

Usuwa wszystkie przyciski radiowe z pliku `CTaskDialog`.

```cpp
void RemoveAllRadioButtons();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetcommandcontroloptions"></a><a name="setcommandcontroloptions"></a>CTaskDialog::SetCommandControlOptions

Aktualizuje kontrolkę `CTaskDialog`przycisku polecenia na pliku .

```cpp
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parametry

*nCommandControlID (Identyfikator kontrolera)*<br/>
[w] Identyfikator formantu polecenia do aktualizacji.

*bWłach*<br/>
[w] Parametr logiczny wskazujący, czy określony kontrolka przycisku polecenia jest włączona czy wyłączona.

*bWymaganieWychanie*<br/>
[w] Parametr logiczny, który wskazuje, czy określony przycisk polecenia wymaga podniesienia uprawnień.

### <a name="remarks"></a>Uwagi

Ta metoda służy do zmiany, czy formant przycisku polecenia jest włączony `CTaskDialog` lub wymaga podniesienia po dodaniu do klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetcommonbuttonoptions"></a><a name="setcommonbuttonoptions"></a>CTaskDialog::SetCommonButtonOptions

Aktualizuje podzbiór typowych przycisków, które mają być włączone i wymagać elewacji funkcji Kontrola konta użytkownika.

```cpp
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parametry

*nDisabledButtonMask*<br/>
[w] Maska dla typowych przycisków, aby wyłączyć.

*nElevationButtonMask*<br/>
[w] Maska dla typowych przycisków, które wymagają podniesienia.

### <a name="remarks"></a>Uwagi

Wspólne przyciski można ustawić w wystąpieniu [klasy CTaskDialog](../../mfc/reference/ctaskdialog-class.md) przy użyciu konstruktora [CTaskDialog::CTaskDialog](#ctaskdialog) i metody [CTaskDialog::SetCommonButtons](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions`nie obsługuje dodawania nowych wspólnych przycisków.

Jeśli ta metoda jest używana do wyłączania lub podnoszenia `CTaskDialog`poziomu wspólnego przycisku, który nie jest dostępny dla tego, ta metoda zgłasza wyjątek przy użyciu makra [ENSURE.](diagnostic-services.md#ensure)

Ta metoda włącza dowolny przycisk, `CTaskDialog` który jest dostępny dla, ale nie jest w *nDisabledButtonMask*, nawet jeśli został wcześniej wyłączony. Ta metoda traktuje elewację w podobny sposób: rejestruje typowe przyciski jako nie wymagające podniesienia, jeśli wspólny przycisk jest dostępny, ale nie jest zawarty w *nElevationButtonMask*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcommonbuttons"></a><a name="setcommonbuttons"></a>CTaskDialog::SetCommonButtons

Dodaje typowe przyciski do pliku `CTaskDialog`.

```cpp
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parametry

*nButtonMask (Maska dobuttonów)*<br/>
[w] Maska przycisków, aby `CTaskDialog`dodać do .

*nDisabledButtonMask*<br/>
[w] Maska przycisków do wyłączenia.

*nElevationButtonMask*<br/>
[w] Maska przycisków, które wymagają elewacji.

### <a name="remarks"></a>Uwagi

Nie można wywołać tej metody po utworzeniu okna wyświetlania dla tego wystąpienia `CTaskDialog` klasy. Jeśli to zrobisz, ta metoda zgłasza wyjątek.

Przyciski oznaczone przez *nButtonMask* zastępują wszystkie typowe przyciski wcześniej dodane do pliku `CTaskDialog`. Dostępne są tylko przyciski wskazane w *nButtonMask.*

Jeśli *ani nDisabledButtonMask,* albo *nElevationButtonMask* zawierają przycisk, który nie znajduje się w *nButtonMask,* ta metoda zgłasza wyjątek przy użyciu makra [ENSURE.](diagnostic-services.md#ensure)

Domyślnie wszystkie typowe przyciski są włączone i nie wymagają podniesienia uprawnień.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcontent"></a><a name="setcontent"></a>CTaskDialog::SetContent

Aktualizuje zawartość `CTaskDialog`pliku .

```cpp
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>Parametry

*strContent (podtrzymuje)*<br/>
[w] Ciąg do wyświetlenia użytkownikowi.

### <a name="remarks"></a>Uwagi

Zawartość `CTaskDialog` klasy jest tekst, który jest wyświetlany użytkownikowi w sekcji głównej okna dialogowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetdefaultcommandcontrol"></a><a name="setdefaultcommandcontrol"></a>CTaskDialog::SetDefaultCommandControl

Określa domyślny kontrolka przycisku polecenia.

```cpp
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>Parametry

*nCommandControlID (Identyfikator kontrolera)*<br/>
[w] Identyfikator formantu przycisku polecenia ma być wartością domyślną.

### <a name="remarks"></a>Uwagi

Domyślny przycisk polecenia to formant wybrany, gdy `CTaskDialog` jest wyświetlany po raz pierwszy użytkownikowi.

Ta metoda zgłasza wyjątek, jeśli nie można znaleźć formantu przycisku polecenia określonego przez *nCommandControlID*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetdefaultradiobutton"></a><a name="setdefaultradiobutton"></a>CTaskDialog::SetDefaultRadioButton

Określa domyślny przycisk opcji.

```cpp
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>Parametry

*nRadioButtonid*<br/>
[w] Identyfikator przycisku radiowego ma być domyślny.

### <a name="remarks"></a>Uwagi

Domyślny przycisk opcji to przycisk wybrany, gdy `CTaskDialog` jest wyświetlany po raz pierwszy użytkownikowi.

Ta metoda zgłasza wyjątek, jeśli nie można znaleźć przycisku opcji określonego przez *nRadioButtonID*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetdialogwidth"></a><a name="setdialogwidth"></a>CTaskDialog::SetDialogWidth

Dostosowuje szerokość pliku `CTaskDialog`.

```cpp
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>Parametry

*nWidth (ww.*<br/>
[w] Szerokość okna dialogowego w pikselach.

### <a name="remarks"></a>Uwagi

Parametr *nWidth* musi być większy lub równy 0. W przeciwnym razie ta metoda zgłasza wyjątek.

Jeśli *nWidth* jest ustawiona na 0, ta metoda ustawia okno dialogowe na domyślny rozmiar.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetexpansionarea"></a><a name="setexpansionarea"></a>CTaskDialog::SetExpansionArea

Aktualizuje obszar rozbudowy pliku `CTaskDialog`.

```cpp
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>Parametry

*strRozwińInformacja*<br/>
[w] Ciąg wyświetlany `CTaskDialog` w głównej części okna dialogowego, gdy użytkownik kliknie przycisk rozszerzenia.

*strCollapsedLabel (Ul.*<br/>
[w] Ciąg wyświetlany `CTaskDialog` obok przycisku rozszerzeń po zwinięciu rozwiniętego obszaru.

*strRozwińLabel*<br/>
[w] Ciąg wyświetlany `CTaskDialog` obok przycisku rozszerzeń po wyświetleniu rozwiniętego obszaru.

### <a name="remarks"></a>Uwagi

Obszar rozwiarzeń `CTaskDialog` klasy umożliwia dostarczenie dodatkowych informacji do użytkownika. Obszar rozwiarzeń znajduje się `CTaskDialog`w głównej części , znajdującej się bezpośrednio pod tytułem i ciągiem zawartości.

Gdy `CTaskDialog` jest wyświetlany po raz pierwszy, nie pokazuje `strCollapsedLabel` rozwiniętych informacji i umieszcza obok przycisku rozszerzenia. Gdy użytkownik kliknie przycisk `CTaskDialog` rozszerzenia, wyświetla *strExpandedInformation* i zmienia etykietę na *strExpandedLabel*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootericon"></a><a name="setfootericon"></a>CTaskDialog::SetFooterIcon

Aktualizuje ikonę stopki pliku `CTaskDialog`.

```cpp
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>Parametry

*hFooterIcon (Właśc.*<br/>
[w] Nowa ikona `CTaskDialog`pliku .

*lpszFooterIcon*<br/>
[w] Nowa ikona `CTaskDialog`pliku .

### <a name="remarks"></a>Uwagi

Ikona stopki jest wyświetlana na spodzie [klasy CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Może mieć skojarzony tekst stopki. Tekst stopki można zmienić za pomocą [CTaskDialog::SetFooterText](#setfootertext).

Ta metoda zgłasza wyjątek z makra [ENSURE,](diagnostic-services.md#ensure) jeśli `CTaskDialog` jest wyświetlany lub parametr wejściowy jest NULL.

A `CTaskDialog` może akceptować tylko ikonę `HICON` stopki lub `LPCWSTR` jako ikonę stopki. Jest to konfigurowane przez ustawienie opcji TDF_USE_HICON_FOOTER w konstruktorze lub [CTaskDialog::SetOptions](#setoptions). Domyślnie `CTaskDialog` jest skonfigurowany do `LPCWSTR` używania jako typ wejściowy dla ikony stopki. Ta metoda generuje wyjątek, jeśli spróbujesz ustawić ikonę przy użyciu nieodpowiedniego typu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootertext"></a><a name="setfootertext"></a>CTaskDialog::SetFooterText

Aktualizuje tekst na stopce `CTaskDialog`pliku .

```cpp
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>Parametry

*strFooterTekst*<br/>
[w] Nowy tekst stopki.

### <a name="remarks"></a>Uwagi

Obok tekstu stopki na spodzie przycisku `CTaskDialog`. Ikonę stopki można zmienić za pomocą [CTaskDialog::SetFooterIcon](#setfootericon).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmainicon"></a><a name="setmainicon"></a>CTaskDialog::SetMainIcon

Aktualizuje główną `CTaskDialog`ikonę pliku .

```cpp
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>Parametry

*hMainIcon (Właz n./ Wł.*<br/>
[w] Nowa ikona.

*lpszMainIcon (lpszMainIcon)*<br/>
[w] Nowa ikona.

### <a name="remarks"></a>Uwagi

Ta metoda zgłasza wyjątek z makra [ENSURE,](diagnostic-services.md#ensure) jeśli `CTaskDialog` jest wyświetlany lub parametr wejściowy jest NULL.

A `CTaskDialog` może zaakceptować tylko `HICON` ikonę główną lub `LPCWSTR` jako ikonę główną. Można to skonfigurować, ustawiając opcję TDF_USE_HICON_MAIN w konstruktorze lub w [CTaskDialog::SetOptions](#setoptions) metody. Domyślnie `CTaskDialog` jest skonfigurowany do `LPCWSTR` używania jako typ wejściowy dla ikony głównej. Ta metoda generuje wyjątek, jeśli spróbujesz ustawić ikonę przy użyciu nieodpowiedniego typu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmaininstruction"></a><a name="setmaininstruction"></a>CTaskDialog::SetMainInstruction

Aktualizuje główną `CTaskDialog`instrukcję .

```cpp
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>Parametry

*strInstrukcje*<br/>
[w] Nowa instrukcja główna.

### <a name="remarks"></a>Uwagi

Główną instrukcją `CTaskDialog` klasy jest tekst wyświetlany użytkownikowi dużą czcionką pogrubioną. Znajduje się w oknie dialogowym pod paskiem tytułu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetoptions"></a><a name="setoptions"></a>CTaskDialog::SetOptions

Konfiguruje opcje `CTaskDialog`dla pliku .

```cpp
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>Parametry

*nOptionPlag*<br/>
[w] Zestaw flag do użycia `CTaskDialog`dla pliku .

### <a name="remarks"></a>Uwagi

Ta metoda czyści wszystkie bieżące opcje dla . `CTaskDialog` Aby zachować bieżące opcje, należy pobrać je najpierw z [CTaskDialog::GetOptions](#getoptions) i połączyć je z opcjami, które chcesz ustawić.

W poniższej tabeli wymieniono wszystkie prawidłowe opcje.

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|Włącza hiperłącza `CTaskDialog`w pliku .|
|TDF_USE_HICON_MAIN|Konfiguruje `CTaskDialog` do `HICON` używania a dla głównej ikony. Alternatywą jest użycie `LPCWSTR`.|
|TDF_USE_HICON_FOOTER|Konfiguruje `CTaskDialog` do `HICON` używania ikony stopki. Alternatywą jest użycie `LPCWSTR`.|
|TDF_ALLOW_DIALOG_CANCELLATION|Umożliwia użytkownikowi zamknięcie `CTaskDialog` za pomocą klawiatury lub za pomocą ikony w prawym górnym rogu okna dialogowego, nawet jeśli przycisk **Anuluj** nie jest włączony. Jeśli ta flaga nie jest ustawiona, a przycisk **Anuluj** nie jest włączony, użytkownik nie może zamknąć okna dialogowego za pomocą klawiszy Alt+F4, klawisza Escape lub przycisku zamknięcia paska tytułu.|
|TDF_USE_COMMAND_LINKS|Konfiguruje `CTaskDialog` do używania formantów przycisku polecenia.|
|TDF_USE_COMMAND_LINKS_NO_ICON|Konfiguruje `CTaskDialog` formantów przycisku polecenia bez wyświetlania ikony obok formantu. TDF_USE_COMMAND_LINKS zastępuje TDF_USE_COMMAND_LINKS_NO_ICON.|
|TDF_EXPAND_FOOTER_AREA|Wskazuje, że obszar rozwiarzeń jest aktualnie rozwinięty.|
|TDF_EXPANDED_BY_DEFAULT|Określa, czy obszar rozwiarzeń jest domyślnie rozwinięty.|
|TDF_VERIFICATION_FLAG_CHECKED|Wskazuje, że pole wyboru weryfikacji jest aktualnie zaznaczone.|
|TDF_SHOW_PROGRESS_BAR|Konfiguruje, `CTaskDialog` aby wyświetlić pasek postępu.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|Konfiguruje pasek postępu jako pasek postępu ramki zaznaczenia. Jeśli ta opcja zostanie włączona, należy ustawić TDF_SHOW_PROGRESS_BAR, aby mieć oczekiwane zachowanie.|
|TDF_CALLBACK_TIMER|Wskazuje, że `CTaskDialog` interwał wywołania zwrotnego jest ustawiony na około 200 milisekund.|
|TDF_POSITION_RELATIVE_TO_WINDOW|Konfiguruje `CTaskDialog` do wyśrodkowanych względem okna nadrzędnego. Jeśli ta flaga nie `CTaskDialog` jest włączona, jest wyśrodkowany względem monitora.|
|TDF_RTL_LAYOUT|Konfiguruje `CTaskDialog` dla układu odczytu od prawej do lewej.|
|TDF_NO_DEFAULT_RADIO_BUTTON|Wskazuje, że po wyświetleniu `CTaskDialog` nie wybrano żadnego przycisku opcji.|
|TDF_CAN_BE_MINIMIZED|Umożliwia użytkownikowi zminimalizowanie pliku `CTaskDialog`. Aby obsługiwać tę `CTaskDialog` opcję, nie może być modalny. MFC nie obsługuje tej opcji, ponieważ MFC `CTaskDialog`nie obsługuje trybless .|

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetprogressbarmarquee"></a><a name="setprogressbarmarquee"></a>CTaskDialog::SetProgressBarMarquee

Konfiguruje pasek ramki zaznaczenia dla `CTaskDialog` i dodaje go do okna dialogowego.

```cpp
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>Parametry

*bWłach*<br/>
[w] TRUE, aby włączyć pasek ramki zaznaczenia; FALSE, aby wyłączyć pasek ramki `CTaskDialog`zaznaczenia i usunąć go z pliku .

*nMarqueeSpeed*<br/>
[w] Liczba całkowita wskazująca szybkość paska ramki zaznaczenia.

### <a name="remarks"></a>Uwagi

Pasek ramki zaznaczenia pojawi się `CTaskDialog` pod głównym tekstem klasy.

Użyj *nMarqueeSpeed,* aby ustawić prędkość paska ramki zaznaczenia; większe wartości wskazują na wolniejsze prędkości. Wartość 0 dla *nMarqueeSpeed* sprawia, że pasek ramki zaznaczenia porusza się z domyślną prędkością dla systemu Windows.

Ta metoda zgłasza wyjątek z makra [ENSURE,](diagnostic-services.md#ensure) jeśli *nMarqueeSpeed* jest mniejsza niż 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarposition"></a><a name="setprogressbarposition"></a>CTaskDialog::SetProgressBarPosition

Dostosowuje położenie paska postępu.

```cpp
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parametry

*nProgressPos*<br/>
[w] Pozycja paska postępu.

### <a name="remarks"></a>Uwagi

Ta metoda zgłasza wyjątek z [upewnij](diagnostic-services.md#ensure) makro if *nProgressPos* nie znajduje się w zakresie paska postępu. Zakres paska postępu można zmienić za pomocą [CTaskDialog::SetProgressBarRange](#setprogressbarrange).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarrange"></a><a name="setprogressbarrange"></a>CTaskDialog::SetProgressBarRange

Dostosowuje zakres paska postępu.

```cpp
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parametry

*nRangeMin (nRangeMin)*<br/>
[w] Dolna granica paska postępu.

*nRangeMax (Polski)*<br/>
[w] Górna granica paska postępu.

### <a name="remarks"></a>Uwagi

Położenie paska postępu jest względem *nRangeMin* i *nRangeMax*. Na przykład jeśli *nRangeMin* jest 50 i *nRangeMax* jest 100, pozycja 75 jest w połowie drogi przez pasek postępu. Użyj [CTaskDialog::SetProgressBarPosition,](#setprogressbarposition) aby ustawić położenie paska postępu.

Aby wyświetlić pasek postępu, należy włączyć opcję TDF_SHOW_PROGRESS_BAR i nie należy włączać TDF_SHOW_MARQUEE_PROGRESS_BAR. Ta metoda automatycznie ustawia TDF_SHOW_PROGRESS_BAR i czyści TDF_SHOW_MARQUEE_PROGRESS_BAR. Użyj [CTaskDialog::SetOptions](#setoptions) ręcznie zmienić opcje dla tego wystąpienia [CTaskDialog Klasy](../../mfc/reference/ctaskdialog-class.md).

Ta metoda zgłasza wyjątek z makra [ENSURE,](diagnostic-services.md#ensure) jeśli *nRangeMin* jest nie mniejsza niż *nRangeMax*. Ta metoda zgłasza również wyjątek, jeśli `CTaskDialog` jest już wyświetlany i ma pasek postępu ramki zaznaczenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarstate"></a><a name="setprogressbarstate"></a>CTaskDialog::SetProgressBarState

Ustawia stan paska postępu i wyświetla `CTaskDialog`go na pliku .

```cpp
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>Parametry

*nPaństwo*<br/>
[w] Stan paska postępu. Zobacz uwagi sekcji dla możliwych wartości.

### <a name="remarks"></a>Uwagi

Ta metoda zgłasza wyjątek z hasłem [ENSURE,](diagnostic-services.md#ensure) jeśli `CTaskDialog` jest już wyświetlany i ma pasek postępu ramki zaznaczenia.

W poniższej tabeli wymieniono możliwe wartości dla *nState*. We wszystkich tych przypadkach pasek postępu wypełni się zwykłym kolorem, aż osiągnie wyznaczoną pozycję zatrzymania. W tym momencie zmieni kolor na podstawie stanu.

|||
|-|-|
|PBST_NORMAL|Po wypełnieniu `CTaskDialog` paska postępu nie zmienia koloru paska. Domyślnie zwykły kolor jest zielony.|
|PBST_ERROR|Po wypełnieniu paska `CTaskDialog` postępu kolor paska zmienia kolor błędu. Domyślnie jest to czerwony.|
|PBST_PAUSED|Po wypełnieniu paska `CTaskDialog` postępu kolor paska zmienia kolor na wstrzymany kolor. Domyślnie jest to żółty.|

Można ustawić, gdzie zatrzymuje się pasek postępu za pomocą [CTaskDialog::SetProgressBarPosition](#setprogressbarposition).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetradiobuttonoptions"></a><a name="setradiobuttonoptions"></a>CTaskDialog::SetRadioButtonOptions

Włącza lub wyłącza przycisk radiowy.

```cpp
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*nRadioButtonid*<br/>
[w] Identyfikator sterowania przyciskiem radiowym.

*bWłach*<br/>
[w] PRAWDA, aby włączyć przycisk radiowy; FALSE, aby wyłączyć przycisk radiowy.

### <a name="remarks"></a>Uwagi

Ta metoda zgłasza wyjątek z makra [ENSURE,](diagnostic-services.md#ensure) jeśli *nRadioButtonID* nie jest prawidłowym identyfikatorem przycisku radiowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetverificationcheckbox"></a><a name="setverificationcheckbox"></a>CTaskDialog::SetVerificationCheckbox

Ustawia sprawdzony stan pola wyboru weryfikacji.

```cpp
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>Parametry

*bSprawiona*<br/>
[w] PRAWDA, aby pole wyboru weryfikacji `CTaskDialog` było zaznaczone po wyświetleniu; FAŁSZ, aby pole wyboru weryfikacji `CTaskDialog` nie zostało zaznaczone po wyświetleniu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetverificationcheckboxtext"></a><a name="setverificationcheckboxtext"></a>CTaskDialog::SetVerificationCheckboxText

Ustawia tekst wyświetlany po prawej stronie pola wyboru weryfikacji.

```cpp
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>Parametry

*strVerificationTekt*<br/>
[w] Tekst wyświetlany przez tę metodę obok pola wyboru weryfikacji.

### <a name="remarks"></a>Uwagi

Ta metoda zgłasza wyjątek z [upewnij](diagnostic-services.md#ensure) makro, `CTaskDialog` jeśli to wystąpienie klasy jest już wyświetlany.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetwindowtitle"></a><a name="setwindowtitle"></a>CTaskDialog::SetWindowTitle

Ustawia tytuł pliku `CTaskDialog`.

```cpp
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>Parametry

*strWindowTitle (Tytuł StrWindow)*<br/>
[w] Nowy tytuł dla `CTaskDialog`.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogshowdialog"></a><a name="showdialog"></a>CTaskDialog::ShowDialog

Tworzy i `CTaskDialog`wyświetla plik .

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

*strContent (podtrzymuje)*<br/>
[w] Ciąg do użycia dla zawartości `CTaskDialog`pliku .

*strMainInstrukcja*<br/>
[w] Główną instrukcją `CTaskDialog`.

*strTitle (napis)*<br/>
[w] Tytuł . `CTaskDialog`

*nIDCommandControlsFirst*<br/>
[w] Identyfikator ciągu pierwszego polecenia.

*nIDCommandControlsLast*<br/>
[w] Identyfikator ciągu ostatniego polecenia.

*nKłamiony*<br/>
[w] Maska przycisków, aby `CTaskDialog`dodać do .

*nTaskDialogOptions*<br/>
[w] Zestaw opcji do użycia `CTaskDialog`dla pliku .

*strFooter (ul.*<br/>
[w] Ciąg do użycia jako stopka.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita odpowiadająca wyborowi dokonanemu przez użytkownika.

### <a name="remarks"></a>Uwagi

Ta metoda statyczna umożliwia utworzenie wystąpienia `CTaskDialog` klasy bez jawnego `CTaskDialog` tworzenia obiektu w kodzie. Ponieważ nie `CTaskDialog` ma obiektu, nie można wywołać żadnych innych `CTaskDialog` metod, `CTaskDialog` jeśli używasz tej metody, aby pokazać użytkownikowi.

Ta metoda tworzy formanty przycisku polecenia przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów zawiera kilka ciągów o skojarzonych identyfikatorach ciągów. Ta metoda dodaje kontrolkę przycisku polecenia dla każdego prawidłowego wpisu w tabeli ciągów między *nIDCommandControlsFirst* i *nCommandControlsLast*, włącznie. Dla tych formantów przycisku polecenia ciąg w tabeli ciągów jest podpis formantu i identyfikator ciągu jest identyfikator formantu.

Zobacz [CTaskDialog::SetOptions](#setoptions) listę prawidłowych opcji.

Zamyka `CTaskDialog` się, gdy użytkownik wybierze wspólny przycisk, kontrolkę `CTaskDialog`łącza poleceń lub zamknie plik . Zwracana wartość jest identyfikatorem wskazującym, w jaki sposób użytkownik zamknął okno dialogowe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogtaskdialogcallback"></a><a name="taskdialogcallback"></a>CTaskDialog::TaskDialogCallback

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

*Hwnd*<br/>
[w] Uchwyt do `m_hWnd` struktury dla `CTaskDialog`.

*uNotyfikowanie*<br/>
[w] Kod powiadomienia określający wygenerowany komunikat.

*Wparam*<br/>
[w] Więcej informacji o wiadomości.

*Lparam*<br/>
[w] Więcej informacji o wiadomości.

*dwRefData*<br/>
[w] Wskaźnik do `CTaskDialog` obiektu, który dotyczy wiadomości wywołania zwrotnego.

### <a name="return-value"></a>Wartość zwracana

Zależy od konkretnego kodu powiadomienia. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Domyślna implementacja `TaskDialogCallback` obsługuje określony komunikat, a następnie wywołuje odpowiednią metodę On [klasy CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Na przykład w odpowiedzi na komunikat TDN_BUTTON_CLICKED, `TaskDialogCallback` wywołuje [CTaskDialog::OnCommandControlClick](#oncommandcontrolclick).

Wartości dla *wParam* i *lParam* zależą od określonego wygenerowanego komunikatu. Jest możliwe dla jednej lub obu tych wartości, które mają być puste. W poniższej tabeli wymieniono domyślne powiadomienia, które są obsługiwane i jakie reprezentują wartości *wParam* i *lParam.* Jeśli zastąpisz tę metodę w klasie pochodnej, należy zaimplementować kod wywołania zwrotnego dla każdej wiadomości w poniższej tabeli.

|Komunikat z powiadomieniem|*wParam* Wartość|*lParam* Wartość|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|Nie używany.|Nie używany.|
|TDN_NAVIGATED|Nie używany.|Nie używany.|
|TDN_BUTTON_CLICKED|Identyfikator sterowania przyciskiem polecenia.|Nie używany.|
|TDN_HYPERLINK_CLICKED|Nie używany.|Struktura [LPCWSTR](/windows/win32/WinProg/windows-data-types) zawierająca łącze.|
|TDN_TIMER|Czas w milisekundach `CTaskDialog` od momentu utworzenia lub zresetowania czasomierza.|Nie używany.|
|TDN_DESTROYED|Nie używany.|Nie używany.|
|TDN_RADIO_BUTTON_CLICKED|Identyfikator przycisku radiowego.|Nie używany.|
|TDN_DIALOG_CONSTRUCTED|Nie używany.|Nie używany.|
|TDN_VERIFICATION_CLICKED|1, jeśli pole wyboru jest zaznaczone, 0, jeśli nie jest.|Nie używany.|
|TDN_HELP|Nie używany.|Nie używany.|
|TDN_EXPANDO_BUTTON_CLICKED|0, jeśli obszar ekspansji jest zwinięty; niezerowy, jeśli wyświetlany jest tekst rozszerzenia.|Nie używany.|

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Wskazówki: dodawanie obiektu CTaskDialog do aplikacji](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
