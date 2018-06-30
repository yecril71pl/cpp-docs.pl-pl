---
title: Klasa obiektu CTaskDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2971293a61a662b789506bbc32923089097f962d
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123217"
---
# <a name="ctaskdialog-class"></a>Klasa obiektu CTaskDialog
Okno podręczne okno dialogowe, które działa jak okno komunikatu, ale można wyświetlić dodatkowe informacje dla użytkownika. `CTaskDialog` Zawiera także funkcje do zbierania informacji przez użytkownika.  
  
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
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|Dodaje kontrolkę przycisku polecenia, aby `CTaskDialog`.|  
|[CTaskDialog::AddRadioButton](#addradiobutton)|Dodaje przycisk radiowy, aby `CTaskDialog`.|  
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|Klika formant przycisku polecenia lub przycisku wspólnej programowo.|  
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Kliknięcie przycisku radiowego programowo.|  
|[CTaskDialog::DoModal](#domodal)|Wyświetla `CTaskDialog`.|  
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Pobiera liczbę dostępnych wspólnej przycisków.|  
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Konwertuje standard przycisku systemu Windows do wspólnego typu przycisk skojarzone z `CTaskDialog` klasy.|  
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|Konwertuje jednego z typowych przycisku skojarzonego z `CTaskDialog` klasy standardowe przycisku systemu Windows.|  
|[CTaskDialog::GetOptions](#getoptions)|Zwraca flagi opcji dla tego `CTaskDialog`.|  
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|Zwraca formantu przycisku wybranego polecenia.|  
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Zwraca wartość wybranego przycisku radiowego.|  
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Pobiera stan weryfikacji pola wyboru.|  
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|Określa, czy formant przycisku polecenia lub przycisku wspólnej jest włączone.|  
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|Określa, czy przycisk radiowy jest włączone.|  
|[CTaskDialog::IsSupported](#issupported)|Określa, czy komputer, na którym działa aplikacja obsługuje `CTaskDialog`.|  
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Dodaje kontrolek przycisku polecenia przy użyciu danych z tabeli ciągów.|  
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|Dodaje przycisków radiowych przy użyciu danych z tabeli ciągów.|  
|[CTaskDialog::NavigateTo](#navigateto)|Przenosi fokus `CTaskDialog`.|  
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|Platformę wywołuje tę metodę, gdy użytkownik kliknie kontrolkę przycisku polecenia.|  
|[CTaskDialog::OnCreate](#oncreate)|Struktura wywołuje tę metodę po utworzeniu `CTaskDialog`.|  
|[CTaskDialog::OnDestroy](#ondestroy)|Struktura wywołuje tę metodę, bezpośrednio przed niszczy `CTaskDialog`.|  
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|Struktura wywołuje tę metodę, gdy użytkownik kliknie przycisk rozszerzenia.|  
|[CTaskDialog::OnHelp](#onhelp)|Struktura wywołuje tę metodę, gdy użytkownik zażąda pomocy.|  
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|Struktura wywołuje tę metodę, gdy użytkownik klika hiperłącze.|  
|[CTaskDialog::OnInit](#oninit)|Struktura wywołuje tę metodę po `CTaskDialog` został zainicjowany.|  
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|Platformę wywołuje tę metodę, gdy użytkownik przenosi fokus w odniesieniu do kontrolki `CTaskDialog`.|  
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|Struktura wywołuje tę metodę, gdy użytkownik wybierze kontrolkę przycisku radiowego.|  
|[CTaskDialog::OnTimer](#ontimer)|Struktura wywołuje tę metodę, po wygaśnięciu czasomierza.|  
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|Platformę wywołuje tę metodę, gdy użytkownik kliknie pole wyboru weryfikacji.|  
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|Usuwa wszystkie formanty poleceń z `CTaskDialog`.|  
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|Usuwa wszystkie przyciski radiowe z `CTaskDialog`.|  
|[CTaskDialog::SetCommandControlOptions](#setcommandcontroloptions)|Aktualizuje kontrolkę przycisku polecenia na `CTaskDialog`.|  
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|Aktualizuje podzbiór wspólnej przycisków można włączyć i wymaga podniesienia uprawnień funkcji kontroli konta użytkownika.|  
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|Dodaje typowe przycisków `CTaskDialog`.|  
|[CTaskDialog::SetContent](#setcontent)|Aktualizuje zawartość `CTaskDialog`.|  
|[CTaskDialog::SetDefaultCommandControl](#setdefaultcommandcontrol)|Określa domyślny formantu przycisku polecenia.|  
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|Określa domyślny przycisk radiowy.|  
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|Dostosowuje szerokość `CTaskDialog`.|  
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|Aktualizuje obszaru rozszerzenia `CTaskDialog`.|  
|[CTaskDialog::SetFooterIcon](#setfootericon)|Aktualizuje ikonę stopki `CTaskDialog`.|  
|[CTaskDialog::SetFooterText](#setfootertext)|Aktualizuje tekst w stopce `CTaskDialog`.|  
|[CTaskDialog::SetMainIcon](#setmainicon)|Aktualizuje głównego ikonę `CTaskDialog`.|  
|[CTaskDialog::SetMainInstruction](#setmaininstruction)|Aktualizuje głównego instrukcja `CTaskDialog`.|  
|[CTaskDialog::SetOptions](#setoptions)|Służy do konfigurowania opcji dla `CTaskDialog`.|  
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Konfiguruje pasek ustawiony na marquee `CTaskDialog` i dodaje go do okna dialogowego.|  
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|Ustawia położenie paska postępu.|  
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|Można dostosować zakres pasek postępu.|  
|[CTaskDialog::SetProgressBarState](#setprogressbarstate)|Ustawia stan paska postępu i wyświetla je na `CTaskDialog`.|  
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Włącza lub wyłącza przycisk radiowy.|  
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|Ustawia stan zaznaczenia pola wyboru weryfikacji.|  
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Ustawia tekst po prawej stronie pola wyboru weryfikacji.|  
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|Ustawia tytuł `CTaskDialog`.|  
|[CTaskDialog::ShowDialog](#showdialog)|Tworzy i wyświetla `CTaskDialog`.|  
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|Struktura wywołuje to w odpowiedzi na różnych komunikatów systemu Windows.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|`m_aButtons`|Tablica kontrolki przycisku polecenia `CTaskDialog`.|  
|`m_aRadioButtons`|Tablica kontrolki przycisku radiowego `CTaskDialog`.|  
|`m_bVerified`|`TRUE` Wskazuje, że zaznaczono pole wyboru weryfikacji; `FALSE` wskazuje nie jest.|  
|`m_footerIcon`|Ikona w stopce `CTaskDialog`.|  
|`m_hWnd`|Dojście do okna `CTaskDialog`.|  
|`m_mainIcon`|Ikona głównego `CTaskDialog`.|  
|`m_nButtonDisabled`|Maska, która wskazuje, które wspólnej przycisków są wyłączone.|  
|`m_nButtonElevation`|Maska, która wskazuje, które wspólnej przycisków wymaga podniesienia uprawnień funkcji kontroli konta użytkownika.|  
|`m_nButtonId`|Identyfikator formantu przycisku wybranego polecenia.|  
|`m_nCommonButton`|Maska, która wskazuje, które wspólnej przyciski są wyświetlane na `CTaskDialog`.|  
|`m_nDefaultCommandControl`|Kontrolowanie identyfikator przycisku polecenia, który wybrano podczas `CTaskDialog` jest wyświetlany.|  
|`m_nDefaultRadioButton`|Sterowanie identyfikator przycisku radiowego, który wybrano podczas `CTaskDialog` jest wyświetlany.|  
|`m_nFlags`|Maska, która wskazuje opcje `CTaskDialog`.|  
|`m_nProgressPos`|Bieżąca pozycja paska postępu.  Ta wartość musi należeć do zakresu od `m_nProgressRangeMin` i `m_nProgressRangeMax`.|  
|`m_nProgressRangeMax`|Maksymalna wartość pasek postępu.|  
|`m_nProgressRangeMin`|Minimalna wartość pasek postępu.|  
|`m_nProgressState`|Stan pasek postępu. Aby uzyskać więcej informacji, zobacz [CTaskDialog::SetProgressBarState](#setprogressbarstate).|  
|`m_nRadioId`|Identyfikator formantu przycisku radiowego wybrane.|  
|`m_nWidth`|Szerokość `CTaskDialog` w pikselach.|  
|`m_strCollapse`|Ciąg `CTaskDialog` wyświetlana z prawej strony pola rozszerzenia gdy rozszerzone informacje jest ukryty.|  
|`m_strContent`|Zawartość ciągu z `CTaskDialog`.|  
|`m_strExpand`|Ciąg `CTaskDialog` wyświetlana z prawej strony pola rozszerzeń po wyświetleniu rozszerzone informacje.|  
|`m_strFooter`|Stopki `CTaskDialog`.|  
|`m_strInformation`|Rozszerzone informacje dla `CTaskDialog`.|  
|`m_strMainInstruction`|Instrukcja głównego `CTaskDialog`.|  
|`m_strTitle`|Tytuł `CTaskDialog`.|  
|`m_strVerification`|Ciąg który `CTaskDialog` wyświetlana z prawej strony pola wyboru weryfikacji.|  
  
## <a name="remarks"></a>Uwagi  
 `CTaskDialog` Klasy zastępuje standardowe pole komunikatów systemu Windows i ma dodatkowe funkcje, takie jak nowe kontrolki, aby zebrać informacje od użytkownika. Ta klasa jest w bibliotece MFC w [!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)]. `CTaskDialog` Jest dostępna, począwszy od systemu Windows Vista. Wcześniejsze wersje systemu Windows nie może wyświetlić `CTaskDialog` obiektu. Użyj `CTaskDialog::IsSupported` można określić w czasie wykonywania, czy bieżący użytkownik może wyświetlić okno dialogowe zadania. Standardowe pole komunikatów systemu Windows nadal jest obsługiwany w [!INCLUDE[vs_dev10_long](../../build/includes/vs_dev10_long_md.md)].  
  
 `CTaskDialog` Jest dostępna tylko po utworzeniu aplikacji przy użyciu biblioteki Unicode.  
  
 `CTaskDialog` Ma dwa różne konstruktory. Jeden konstruktor umożliwia określenie przyciski poleceń dwóch i maksymalnie sześć kontrolki przycisku regularne. Można dodać więcej przycisków poleceń po utworzeniu `CTaskDialog`. Drugi Konstruktor nie obsługuje żadnych przyciski poleceń, ale można dodać nieograniczoną liczbę kontrolki przycisku regularne. Aby uzyskać więcej informacji na temat konstruktorów, zobacz [CTaskDialog::CTaskDialog](#ctaskdialog).  
  
 Na poniższej ilustracji przedstawiono przykład `CTaskDialog` aby zilustrować niektóre formanty lokalizację.  
  
 ![Przykład obiektu CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "ctaskdialogsample")  
Przykładowe obiektu CTaskDialog  
  
## <a name="requirements"></a>Wymagania  
 **Minimalny wymagany system operacyjny:** systemu Windows Vista  
  
 **Nagłówek:** afxtaskdialog.h  
  
##  <a name="addcommandcontrol"></a>  CTaskDialog::AddCommandControl  
 Dodaje nową kontrolkę przycisku polecenia do `CTaskDialog`.  
  
```  
void AddCommandControl(
    int nCommandControlID,  
    const CString& strCaption,  
    BOOL bEnabled = TRUE,  
    BOOL bRequiresElevation = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nCommandControlID*  
 Numer identyfikacyjny polecenia kontroli.  
  
 [in] *strCaption*  
 Ciąg który `CTaskDialog` wyświetla dla użytkownika. Użyj tych parametrów do wyjaśnienia celu polecenia.  
  
 [in] *bWłączony*  
 Parametrów typu Boolean wskazującą, czy przycisk Nowy jest włączona lub wyłączona.  
  
 [in] *bRequiresElevation*  
 Parametrów typu Boolean wskazującą, czy polecenie wymaga podniesienia uprawnień.  
  
### <a name="remarks"></a>Uwagi  
 `CTaskDialog Class` Można wyświetlić nieograniczoną liczbę kontrolek przycisku polecenia. Jednak jeśli `CTaskDialog` Wyświetla dowolnego przycisku polecenia formanty, można wyświetlać maksymalnie sześć przycisków. Jeśli `CTaskDialog` ma żadne formanty przycisku polecenia, można wyświetlić nieograniczoną liczbę przycisków.  
  
 Gdy użytkownik wybierze kontrolkę przycisku polecenia `CTaskDialog` zostanie zamknięte. Jeśli aplikacja zostanie wyświetlone okno dialogowe, za pomocą [CTaskDialog::DoModal](#domodal), `DoModal` zwraca *nCommandControlID* kontrolki przycisku wybranego polecenia.  
  
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
 [in] *nRadioButtonID*  
 Numer identyfikacyjny przycisku radiowego.  
  
 [in] *strCaption*  
 Ciąg który `CTaskDialog` wyświetla obok przycisku radiowego.  
  
 [in] *bWłączony*  
 Parametrów typu Boolean wskazującą, czy przycisk radiowy jest włączone.  
  
### <a name="remarks"></a>Uwagi  
 Przyciski radiowe dla [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) umożliwiają zebranie informacji z użytkownika. Użyj funkcji [CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid) do określenia, które przycisk radiowy zostanie wybrany.  
  
 `CTaskDialog` Nie wymaga, aby *nRadioButtonID* parametry są unikatowe dla każdego przycisku radiowego. Jeśli nie używasz identyfikator różne dla każdego przycisku radiowego może jednak wystąpić nieoczekiwane zachowanie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="clickcommandcontrol"></a>  CTaskDialog::ClickCommandControl  
 Klika formant przycisku polecenia lub przycisku wspólnej programowo.  
  
```  
protected:  
void ClickCommandControl(int nCommandControlID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nCommandControlID*  
 Identyfikator polecenia formantu do kliknięcia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda generuje komunikat TDM_CLICK_BUTTON systemu windows.  
  
##  <a name="clickradiobutton"></a>  CTaskDialog::ClickRadioButton  
 Kliknięcie przycisku radiowego programowo.  
  
```  
protected:  
void ClickRadioButton(int nRadioButtonID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nRadioButtonID*  
 Identyfikator kliknij przycisk radiowy.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda generuje komunikat TDM_CLICK_RADIO_BUTTON systemu windows.  
  
##  <a name="ctaskdialog"></a>  CTaskDialog::CTaskDialog  
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
 [in] *strContent*  
 Ciąg używany dla zawartości `CTaskDialog`.  
  
 [in] *strMainInstruction*  
 Instrukcja głównego `CTaskDialog`.  
  
 [in] *strTitle*  
 Tytuł `CTaskDialog`.  
  
 [in] *nCommonButtons*  
 Maska wspólnej przycisków, aby dodać do `CTaskDialog`.  
  
 [in] *nTaskDialogOptions*  
 Zestaw opcji dla `CTaskDialog`.  
  
 [in] *strFooter*  
 Ciąg, który ma być używana jako stopki.  
  
 [in] *nIDCommandControlsFirst*  
 Identyfikator ciągu pierwszego polecenia.  
  
 [in] *nIDCommandControlsLast*  
 Identyfikator ciągu ostatnie polecenie.  
  
### <a name="remarks"></a>Uwagi  
 Istnieją dwa sposoby, które można dodać `CTaskDialog` do aplikacji. Pierwszym sposobem jest użycie jednego z konstruktorów utworzyć `CTaskDialog` i wyświetl ją przy użyciu [CTaskDialog::DoModal](#domodal). Drugim sposobem jest użycie statycznej funkcji [CTaskDialog::ShowDialog](#showdialog), co umożliwia wyświetlanie `CTaskDialog` bez jawnego tworzenia `CTaskDialog` obiektu.  
  
 Drugi Konstruktor tworzy kontrolek przycisku polecenia przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów ma kilka ciągów z ciągiem skojarzonych identyfikatorów. Ta metoda dodaje kontrolkę przycisku polecenia dla każdej prawidłowy wpis w tabeli ciągów między *nIDCommandControlsFirst* i *nCommandControlsLast*włącznie. W przypadku tych kontrolek przycisku polecenia ciąg w tabeli ciągów jest podpis formantu i identyfikator ciągu jest identyfikatorem formantu.  
  
 Zobacz [CTaskDialog::SetOptions](#setoptions) listę prawidłowych opcji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="domodal"></a>  CTaskDialog::DoModal  
 Pokazuje `CTaskDialog` i ułatwia modalne.  
  
```  
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```  
  
### <a name="parameters"></a>Parametry  
 [in] *hParent*  
 Okno nadrzędne dla `CTaskDialog`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba całkowita, która odpowiada wybór dokonany przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Wyświetla to wystąpienie [obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Następnie aplikacja oczekuje na użytkownika zamknąć okno dialogowe.  
  
 `CTaskDialog` Zamyka, gdy użytkownik zaznaczy wspólnej przycisk formantu łącze polecenia lub zamyka `CTaskDialog`. Wartość zwracana jest identyfikator, który wskazuje, jak zostanie zamknięte okno dialogowe.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="getcommonbuttoncount"></a>  CTaskDialog::GetCommonButtonCount  
 Pobiera liczbę typowych przycisków.  
  
```  
int GetCommonButtonCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wspólnych przyciski.  
  
### <a name="remarks"></a>Uwagi  
 Typowe przyciski są domyślnych przycisków, które zapewniają do [CTaskDialog::CTaskDialog](#ctaskdialog). [Klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) Wyświetla przyciski wzdłuż dolnej części okna dialogowego.  
  
 Wyliczany Lista przycisków znajduje się w CommCtrl.h.  
  
##  <a name="getcommonbuttonflag"></a>  CTaskDialog::GetCommonButtonFlag  
 Konwertuje standard przycisku systemu Windows do wspólnego typu przycisk skojarzone z [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md).  
  
```  
int GetCommonButtonFlag(int nButtonId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nButtonId*  
 Standardowa wartość przycisku systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość odpowiadającego `CTaskDialog` wspólnej przycisku. Jeśli nie jest odpowiedni dostępny przycisk wspólne, ta metoda zwraca wartość 0.  
  
##  <a name="getcommonbuttonid"></a>  CTaskDialog::GetCommonButtonId  
 Konwertuje jednego z typowych przycisku skojarzonego z [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) do standardowego przycisku systemu Windows.  
  
```  
int GetCommonButtonId(int nFlag);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nFlag*  
 Wspólny typ przycisku skojarzonego z `CTaskDialog` klasy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość odpowiedni przycisk standardowych systemu Windows. Jeśli nie jest dostępny odpowiedni przycisk systemu Windows, metoda zwraca wartość 0.  
  
##  <a name="getoptions"></a>  CTaskDialog::GetOptions  
 Zwraca flagi opcji dla tego `CTaskDialog`.  
  
```  
int GetOptions() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Flag `CTaskDialog`.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat dostępnych opcji [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md), zobacz [CTaskDialog::SetOptions](#setoptions).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="getselectedcommandcontrolid"></a>  CTaskDialog::GetSelectedCommandControlID  
 Zwraca formantu przycisku wybranego polecenia.  
  
```  
int GetSelectedCommandControlID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator formantu przycisku aktualnie wybranego polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Nie masz do używania tej metody można pobrać Identyfikatora przycisku polecenia, który użytkownik wybrał. Ten identyfikator jest zwracany przez jeden [CTaskDialog::DoModal](#domodal) lub [CTaskDialog::ShowDialog](#showdialog).  
  
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
 Można użyć tej metody, po użytkownik zamyka okno dialogowe, aby pobrać wybranego przycisku radiowego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="getverificationcheckboxstate"></a>  CTaskDialog::GetVerificationCheckboxState  
 Pobiera stan weryfikacji pola wyboru.  
  
```  
BOOL GetVerificationCheckboxState() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pole wyboru jest zaznaczone, FALSE, jeśli nie jest.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]  
  
##  <a name="iscommandcontrolenabled"></a>  CTaskDialog::IsCommandControlEnabled  
 Określa, czy formant przycisku polecenia lub przycisku jest włączone.  
  
```  
BOOL IsCommandControlEnabled(int nCommandControlID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nCommandControlID*  
 Identyfikator formantu przycisku polecenia lub przycisku do testowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli formant jest włączony, FALSE, jeśli nie jest.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda służy do określenia dostępności zarówno kontrolki przycisku polecenia i przyciski typowych `CTaskDialog` klasy *.  
  
 Jeśli *nCommandControlID* jest prawidłowym identyfikatorem w obu wspólnego `CTaskDialog` przycisku lub kontrolkę przycisku polecenia, ta metoda zgłasza wyjątek.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="isradiobuttonenabled"></a>  CTaskDialog::IsRadioButtonEnabled  
 Określa, czy przycisk radiowy jest włączone.  
  
```  
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nRadioButtonID*  
 Identyfikator przycisku radiowego do testowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk radiowy jest włączone, wartość FALSE, jeśli nie jest.  
  
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
 Wartość TRUE, jeśli komputer obsługuje `CTaskDialog`; Wartość FALSE w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do określenia w czasie wykonywania, jeśli komputera, na którym jest uruchomiona aplikacja obsługuje `CTaskDialog` klasy. Jeśli komputer nie obsługuje `CTaskDialog`, należy wybrać inną metodę komunikacji informacji do użytkownika. Aplikacja ulegnie awarii, jeśli klient próbuje użyć `CTaskDialog` na komputerze, który nie obsługuje `CTaskDialog` klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]  
  
##  <a name="loadcommandcontrols"></a>  CTaskDialog::LoadCommandControls  
 Dodaje kontrolek przycisku polecenia przy użyciu danych z tabeli ciągów.  
  
```  
void LoadCommandControls(
    int nIDCommandControlsFirst,  
    int nIDCommandControlsLast);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nIDCommandControlsFirst*  
 Identyfikator ciągu pierwszego polecenia.  
  
 [in] *nIDCommandControlsLast*  
 Identyfikator ciągu ostatnie polecenie.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda tworzy kontrolek przycisku polecenia przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów ma kilka ciągów z ciągiem skojarzonych identyfikatorów. Nowe kontrolki przycisku polecenia dodane za pomocą tej metody należy użyć ciągu formantu podpisu i identyfikator ciągu dla identyfikatora formantu. Zakres wybrane parametry są dostarczane przez *nIDCommandControlsFirst* i *nCommandControlsLast*włącznie. Jeśli jest pusty wpis w zakresie, metoda nie dodaje kontrolkę przycisku polecenia dla tego wpisu.  
  
 Domyślnie nowe kontrolki przycisku polecenia są włączone i nie wymaga podwyższonego poziomu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="loadradiobuttons"></a>  CTaskDialog::LoadRadioButtons  
 Dodaje kontrolek przycisków radiowych przy użyciu danych z tabeli ciągów.  
  
```  
void LoadRadioButtons(
    int nIDRadioButtonsFirst,  
    int nIDRadioButtonsLast);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nIDRadioButtonsFirst*  
 Identyfikator ciągu pierwszego przycisku radiowego.  
  
 [in] *nIDRadioButtonsLast*  
 Identyfikator ciągu ostatnich przycisku radiowego.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda tworzy przycisków radiowych przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów ma kilka ciągów z ciągiem skojarzonych identyfikatorów. Nowe przyciski radiowe dodane za pomocą tej metody należy użyć ciągu dla przycisku radiowego i identyfikator ciągu dla identyfikatora przycisk radiowy. Zakres wybrane parametry są dostarczane przez *nIDRadioButtonsFirst* i *nRadioButtonsLast*włącznie. Jeśli jest pusty wpis w zakresie, metoda nie dodaje przycisku radiowego dla tego wpisu.  
  
 Nowe przyciski radiowe są domyślnie włączone.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="navigateto"></a>  CTaskDialog::NavigateTo  
 Przenosi fokus `CTaskDialog`.  
  
```  
protected:  
void NavigateTo(CTaskDialog& oTaskDialog) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *oTaskDialog*  
 `CTaskDialog` Który otrzymuje fokus.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda powoduje ukrycie bieżącego `CTaskDialog` po Wyświetla *oTaskDialog*. *OTaskDialog* jest wyświetlany w tej samej lokalizacji co bieżący `CTaskDialog`.  
  
##  <a name="oncommandcontrolclick"></a>  CTaskDialog::OnCommandControlClick  
 Platformę wywołuje tę metodę, gdy użytkownik kliknie kontrolkę przycisku polecenia.  
  
```  
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nCommandControlID*  
 Identyfikator formantu przycisku polecenia, którą użytkownik wybrał.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej do zaimplementowania niestandardowego zachowania.  
  
##  <a name="oncreate"></a>  CTaskDialog::OnCreate  
 Struktura wywołuje tę metodę po utworzeniu `CTaskDialog`.  
  
```  
virtual HRESULT OnCreate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej do zaimplementowania niestandardowego zachowania.  
  
##  <a name="ondestroy"></a>  CTaskDialog::OnDestroy  
 Struktura wywołuje tę metodę, bezpośrednio przed niszczy `CTaskDialog`.  
  
```  
virtual HRESULT OnDestroy();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej do zaimplementowania niestandardowego zachowania.  
  
##  <a name="onexpandbuttonclick"></a>  CTaskDialog::OnExpandButtonClick  
 Struktura wywołuje tę metodę, gdy użytkownik kliknie przycisk rozszerzenia.  
  
```  
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bExpanded*  
 Wartość niezerowa wskazuje, że dodatkowe informacje są wyświetlane; 0 wskazuje, że dodatkowe informacje są ukrywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej do zaimplementowania niestandardowego zachowania.  
  
##  <a name="onhelp"></a>  CTaskDialog::OnHelp  
 Struktura wywołuje tę metodę, gdy użytkownik zażąda pomocy.  
  
```  
virtual HRESULT OnHelp();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej do zaimplementowania niestandardowego zachowania.  
  
##  <a name="onhyperlinkclick"></a>  CTaskDialog::OnHyperlinkClick  
 Struktura wywołuje tę metodę, gdy użytkownik klika hiperłącze.  
  
```  
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *strHref*  
 Ciąg reprezentujący hiperłącze.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153) przed zwraca wartość S_OK.  
  
 Zastępuje tę metodę w klasie pochodnej do zaimplementowania niestandardowego zachowania.  
  
##  <a name="oninit"></a>  CTaskDialog::OnInit  
 Struktura wywołuje tę metodę po `CTaskDialog` został zainicjowany.  
  
```  
virtual HRESULT OnInit();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej do zaimplementowania niestandardowego zachowania.  
  
##  <a name="onnavigatepage"></a>  CTaskDialog::OnNavigatePage  
 Struktura wywołuje tę metodę w odpowiedzi na [CTaskDialog::NavigateTo](#navigateto) metody.  
  
```  
virtual HRESULT OnNavigatePage();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej do zaimplementowania niestandardowego zachowania.  
  
##  <a name="onradiobuttonclick"></a>  CTaskDialog::OnRadioButtonClick  
 Struktura wywołuje tę metodę, gdy użytkownik wybierze kontrolkę przycisku radiowego.  
  
```  
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nRadioButtonID*  
 Identyfikator formantu przycisku radiowego, który użytkownik kliknął.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej do zaimplementowania niestandardowego zachowania.  
  
##  <a name="ontimer"></a>  CTaskDialog::OnTimer  
 Struktura wywołuje tę metodę, po wygaśnięciu czasomierza.  
  
```  
virtual HRESULT OnTimer(long lTime);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lTime*  
 Czas w milisekundach od `CTaskDialog` został utworzony lub został zresetowany przez czasomierz.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej do zaimplementowania niestandardowego zachowania.  
  
##  <a name="onverificationcheckboxclick"></a>  CTaskDialog::OnVerificationCheckboxClick  
 Platformę wywołuje tę metodę, gdy użytkownik kliknie pole wyboru weryfikacji.  
  
```  
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bChecked*  
 Wartość TRUE wskazuje, że zaznaczone jest pole wyboru weryfikacji; Wartość FALSE wskazuje, że nie jest.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej do zaimplementowania niestandardowego zachowania.  
  
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
 Aktualizuje kontrolkę przycisku polecenia na `CTaskDialog`.  
  
```  
void SetCommandControlOptions(
    int nCommandControlID,  
    BOOL bEnabled,  
    BOOL bRequiresElevation = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nCommandControlID*  
 Identyfikator formantu polecenia do zaktualizowania.  
  
 [in] *bWłączony*  
 Parametrów typu Boolean wskazującą, czy kontrolka przycisku określone polecenie jest włączona lub wyłączona.  
  
 [in] *bRequiresElevation*  
 Parametrów typu Boolean wskazującą, czy określone polecenie formantu przycisku wymaga podniesienia uprawnień.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia określenie, czy formant przycisku polecenia jest włączona lub wymaga podniesienia uprawnień, po dodaniu do `CTaskDialog` klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="setcommonbuttonoptions"></a>  CTaskDialog::SetCommonButtonOptions  
 Aktualizuje podzbiór wspólnej przycisków można włączyć i wymaga podniesienia uprawnień funkcji kontroli konta użytkownika.  
  
```  
void SetCommonButtonOptions(
    int nDisabledButtonMask,  
    int nElevationButtonMask = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nDisabledButtonMask*  
 Maska wspólnej przycisków wyłączyć.  
  
 [in] *nElevationButtonMask*  
 Maska wspólnej przycisków, które wymagają podniesionych uprawnień.  
  
### <a name="remarks"></a>Uwagi  
 Można ustawić wspólne przycisków dostępnych na wystąpienie [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) przy użyciu konstruktora [CTaskDialog::CTaskDialog](#ctaskdialog) , a także metoda [CTaskDialog::SetCommonButtons ](#setcommonbuttons). `CTaskDialog::SetCommonButtonOptions` nie obsługuje dodawania nowych wspólnej przycisków.  
  
 Jeśli używasz tej metody do wyłączenia lub podniesienie poziomu wspólnego przycisku, który nie jest dostępna dla tego `CTaskDialog`, ta metoda zgłasza wyjątek przy użyciu [upewnij się, że](diagnostic-services.md#ensure) makra.  
  
 Ta metoda umożliwia obsługę dowolnego przycisku, który jest dostępny do `CTaskDialog` , ale nie ma na liście *nDisabledButtonMask*, nawet jeśli wcześniej była wyłączona. Ta metoda traktuje podniesienia uprawnień w podobny sposób: rejestruje wspólnej przyciski jako niewymagające podniesienia uprawnień, jeśli wspólnej przycisk jest dostępny, ale nie jest zawarty w *nElevationButtonMask*.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]  
  
##  <a name="setcommonbuttons"></a>  CTaskDialog::SetCommonButtons  
 Dodaje typowe przycisków `CTaskDialog`.  
  
```  
void SetCommonButtons(
    int nButtonMask,  
    int nDisabledButtonMask = 0,  
    int nElevationButtonMask = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nButtonMask*  
 Maska przycisków, aby dodać do `CTaskDialog`.  
  
 [in] *nDisabledButtonMask*  
 Maska przycisków, aby wyłączyć.  
  
 [in] *nElevationButtonMask*  
 Maska przycisków, które wymagają podniesionych uprawnień.  
  
### <a name="remarks"></a>Uwagi  
 Nie można wywołać tej metody po okna dla tego wystąpienia `CTaskDialog` utworzyć klasy. Jeśli to zrobisz, ta metoda zgłasza wyjątek.  
  
 Przyciski wskazywanym przez *nButtonMask* zastąpić wszystkie wspólne przyciski wcześniej dodane do `CTaskDialog`. Wskazane tylko przyciski *nButtonMask* są dostępne.  
  
 Jeśli dowolny *nDisabledButtonMask* lub *nElevationButtonMask* zawiera przycisk, który nie znajduje się w *nButtonMask*, ta metoda zgłasza wyjątek przy użyciu [Upewnij się, że](diagnostic-services.md#ensure) makra.  
  
 Domyślnie wszystkie wspólne przyciski są włączone i nie wymaga podwyższonego poziomu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]  
  
##  <a name="setcontent"></a>  CTaskDialog::SetContent  
 Aktualizuje zawartość `CTaskDialog`.  
  
```  
void SetContent(const CString& strContent);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *strContent*  
 Ciąg wyświetlany użytkownikowi.  
  
### <a name="remarks"></a>Uwagi  
 Zawartość `CTaskDialog` klasy jest tekst, który jest wyświetlany użytkownikowi w sekcji głównej okna dialogowego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setdefaultcommandcontrol"></a>  CTaskDialog::SetDefaultCommandControl  
 Określa domyślny formantu przycisku polecenia.  
  
```  
void SetDefaultCommandControl(int nCommandControlID);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nCommandControlID*  
 Identyfikator formantu przycisku polecenia domyślne.  
  
### <a name="remarks"></a>Uwagi  
 Kontrolka przycisku polecenia domyślny jest formant, który jest zaznaczone, gdy `CTaskDialog` jest najpierw wyświetlany użytkownikowi.  
  
 Ta metoda zgłasza wyjątek, jeśli nie można odnaleźć formantu przycisku polecenia, określony przez *nCommandControlID*.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]  
  
##  <a name="setdefaultradiobutton"></a>  CTaskDialog::SetDefaultRadioButton  
 Określa domyślny przycisk radiowy.  
  
```  
void SetDefaultRadioButton(int nRadioButtonID);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nRadioButtonID*  
 Identyfikator przycisku radiowego jako domyślny.  
  
### <a name="remarks"></a>Uwagi  
 Przycisk radiowy domyślny jest przycisku, który jest zaznaczone, gdy `CTaskDialog` jest najpierw wyświetlany użytkownikowi.  
  
 Ta metoda zgłasza wyjątek, jeśli nie można odnaleźć określonego przez przycisk radiowy *nRadioButtonID*.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="setdialogwidth"></a>  CTaskDialog::SetDialogWidth  
 Dostosowuje szerokość `CTaskDialog`.  
  
```  
void SetDialogWidth(int nWidth = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nWidth*  
 Szerokość okna dialogowego w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Parametr *nWidth* musi być większa lub równa 0. W przeciwnym razie ta metoda zgłasza wyjątek.  
  
 Jeśli *nWidth* jest ustawiona na 0, to Ustawia metodę dialogowym domyślny rozmiar.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setexpansionarea"></a>  CTaskDialog::SetExpansionArea  
 Aktualizuje obszaru rozszerzenia `CTaskDialog`.  
  
```  
void SetExpansionArea(
    const CString& strExpandedInformation,  
    const CString& strCollapsedLabel = _T(""),  
    const CString& strExpandedLabel = _T(""));
```  
  
### <a name="parameters"></a>Parametry  
 [in] *strExpandedInformation*  
 Ciąg który `CTaskDialog` wyświetla w głównej części okna dialogowego, gdy użytkownik kliknie przycisk rozszerzenia.  
  
 [in] *strCollapsedLabel*  
 Ciąg który `CTaskDialog` wyświetla obok przycisku rozszerzeń po zwinięciu rozwinięte obszaru.  
  
 [in] *strExpandedLabel*  
 Ciąg który `CTaskDialog` wyświetlany obok przycisku rozszerzeń, gdy obszar rozszerzonej jest wyświetlany.  
  
### <a name="remarks"></a>Uwagi  
 Obszar rozszerzenia `CTaskDialog` klasa umożliwia podanie dodatkowych informacji do użytkownika. Obszar rozszerzenia jest w głównej części `CTaskDialog`, który znajduje się bezpośrednio pod ciąg tytuł i zawartości.  
  
 Gdy `CTaskDialog` najpierw jest wyświetlane, jego rozszerzone informacje nie są wyświetlane, jak i umieszcza `strCollapsedLabel` obok przycisku rozszerzenia. Gdy użytkownik kliknie przycisk rozszerzenia `CTaskDialog` Wyświetla *strExpandedInformation* i zmiany etykiety do *strExpandedLabel*.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setfootericon"></a>  CTaskDialog::SetFooterIcon  
 Aktualizuje ikonę stopki `CTaskDialog`.  
  
```  
void SetFooterIcon(HICON hFooterIcon);  
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *hFooterIcon*  
 Ikona nowego `CTaskDialog`.  
  
 [in] *lpszFooterIcon*  
 Ikona nowego `CTaskDialog`.  
  
### <a name="remarks"></a>Uwagi  
 Ikona stopka jest wyświetlana w dolnej części [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Można ją skojarzyć tekst stopki. Możesz zmienić tekst stopki z [CTaskDialog::SetFooterText](#setfootertext).  
  
 Ta metoda zgłasza wyjątek z [upewnij się, że](diagnostic-services.md#ensure) makro Jeśli `CTaskDialog` wyświetleniem lub parametr wejściowy ma wartość NULL.  
  
 A `CTaskDialog` może akceptować tylko `HICON` lub `LPCWSTR` jako ikonę stopki. Te ustawienia zostaną skonfigurowane przez ustawienie opcji TDF_USE_HICON_FOOTER w konstruktorze lub [CTaskDialog::SetOptions](#setoptions). Domyślnie `CTaskDialog` jest skonfigurowana do używania `LPCWSTR` jako typ danych wejściowych dla ikony stopki. Ta metoda generuje wyjątek, Jeśli spróbujesz ustawić ikonę przy użyciu typu nieodpowiednie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setfootertext"></a>  CTaskDialog::SetFooterText  
 Aktualizuje tekst w stopce `CTaskDialog`.  
  
```  
void SetFooterText(const CString& strFooterText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *strFooterText*  
 Nowy tekst stopki.  
  
### <a name="remarks"></a>Uwagi  
 Ikona stopki widoczna obok tekstu stopki w dolnej części `CTaskDialog`. Możesz zmienić ikonę stopki z [CTaskDialog::SetFooterIcon](#setfootericon).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setmainicon"></a>  CTaskDialog::SetMainIcon  
 Aktualizuje głównego ikonę `CTaskDialog`.  
  
```  
void SetMainIcon(HICON hMainIcon);  
void SetMainIcon(LPCWSTR lpszMainIcon);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *hMainIcon*  
 Ikona nowego.  
  
 [in] *lpszMainIcon*  
 Ikona nowego.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zgłasza wyjątek z [upewnij się, że](diagnostic-services.md#ensure) makro Jeśli `CTaskDialog` wyświetleniem lub parametr wejściowy ma wartość NULL.  
  
 A `CTaskDialog` może akceptować tylko `HICON` lub `LPCWSTR` jako ikonę głównego. Można to skonfigurować przez ustawienie opcji TDF_USE_HICON_MAIN w konstruktorze lub w [CTaskDialog::SetOptions](#setoptions) metody. Domyślnie `CTaskDialog` jest skonfigurowana do używania `LPCWSTR` jako typ danych wejściowych dla ikony głównego. Ta metoda generuje wyjątek, Jeśli spróbujesz ustawić ikonę przy użyciu typu nieodpowiednie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setmaininstruction"></a>  CTaskDialog::SetMainInstruction  
 Aktualizuje głównego instrukcja `CTaskDialog`.  
  
```  
void SetMainInstruction(const CString& strInstructions);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *strInstructions*  
 Nowe instrukcji głównego.  
  
### <a name="remarks"></a>Uwagi  
 Instrukcja głównego `CTaskDialog` klasy jest tekst wyświetlany użytkownikowi w dużych pogrubioną czcionką. Znajduje się w oknie dialogowym poniżej paska tytułu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setoptions"></a>  CTaskDialog::SetOptions  
 Służy do konfigurowania opcji dla `CTaskDialog`.  
  
```  
void SetOptions(int nOptionFlag);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nOptionFlag*  
 Zbiór flagi do użycia na potrzeby `CTaskDialog`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa wszystkie bieżące opcje dla `CTaskDialog`. Aby zachować bieżące opcje, należy pobrać je najpierw z [CTaskDialog::GetOptions](#getoptions) i połączyć je z opcjami, które chcesz ustawić.  
  
 Poniższa tabela zawiera listę prawidłowych opcji.  
  
 TDF_ENABLE_HYPERLINKS  
 Włącza hiperłącza w `CTaskDialog`.  
  
 TDF_USE_HICON_MAIN  
 Konfiguruje `CTaskDialog` do używania `HICON` głównego ikony. Alternatywą jest użycie `LPCWSTR`.  
  
 TDF_USE_HICON_FOOTER  
 Konfiguruje `CTaskDialog` do używania `HICON` ikony stopki. Alternatywą jest użycie `LPCWSTR`.  
  
 TDF_ALLOW_DIALOG_CANCELLATION  
 Umożliwia zamknięcie `CTaskDialog` za pomocą klawiatury lub za pomocą ikony w prawym górnym rogu okna dialogowego, nawet wtedy, gdy **anulować** przycisk nie jest włączona. Jeśli ta flaga nie jest ustawiona i **anulować** przycisk nie jest włączona, użytkownik nie może zamknąć okno dialogowe za pomocą Alt + F4, klawisz Escape, lub przycisk Zamknij pasek tytułu.  
  
 TDF_USE_COMMAND_LINKS  
 Konfiguruje `CTaskDialog` użycie kontroli przycisk polecenia.  
  
 TDF_USE_COMMAND_LINKS_NO_ICON  
 Konfiguruje `CTaskDialog` użycie kontroli przycisku polecenia bez wyświetlania ikona obok kontrolki. TDF_USE_COMMAND_LINKS zastępuje TDF_USE_COMMAND_LINKS_NO_ICON.  
  
 TDF_EXPAND_FOOTER_AREA  
 Wskazuje, że obszar rozszerzenia obecnie jest rozwinięta.  
  
 TDF_EXPANDED_BY_DEFAULT  
 Określa, czy obszar rozszerzenia jest rozwinięta domyślnie.  
  
 TDF_VERIFICATION_FLAG_CHECKED  
 Wskazuje, że aktualnie zaznaczone jest pole wyboru weryfikacji.  
  
 TDF_SHOW_PROGRESS_BAR  
 Konfiguruje `CTaskDialog` do wyświetlany pasek postępu.  
  
 TDF_SHOW_MARQUEE_PROGRESS_BAR  
 Konfiguruje paska postępu jest ustawiony na marquee pasek postępu. Jeśli ta opcja jest włączona, należy ustawić TDF_SHOW_PROGRESS_BAR mają oczekiwane zachowanie.  
  
 TDF_CALLBACK_TIMER  
 Oznacza to, że `CTaskDialog` wywołania zwrotnego interwał wynosi około 200 ms.  
  
 TDF_POSITION_RELATIVE_TO_WINDOW  
 Konfiguruje `CTaskDialog` do wyśrodkowany względem okno nadrzędne. Jeśli ta flaga nie jest włączona, `CTaskDialog` jest wyśrodkowywany względem monitora.  
  
 TDF_RTL_LAYOUT  
 Konfiguruje `CTaskDialog` układu czytania od prawej do lewej.  
  
 TDF_NO_DEFAULT_RADIO_BUTTON  
 Wskazuje, że nie jest zaznaczona opcja podczas `CTaskDialog` pojawi się.  
  
 TDF_CAN_BE_MINIMIZED  
 Umożliwia użytkownikowi zminimalizować `CTaskDialog`. Do obsługi tej opcji `CTaskDialog` nie może być modalne. MFC nie obsługuje tej opcji, ponieważ MFC nie obsługuje niemodalny `CTaskDialog`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]  
  
##  <a name="setprogressbarmarquee"></a>  CTaskDialog::SetProgressBarMarquee  
 Konfiguruje pasek ustawiony na marquee `CTaskDialog` i dodaje go do okna dialogowego.  
  
```  
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,  
    int nMarqueeSpeed = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bWłączony*  
 Wartość TRUE, aby włączyć paskiem ustawiony na marquee. Wartość FAŁSZ, aby wyłączyć pasek ustawiony na marquee i usunąć go z `CTaskDialog`.  
  
 [in] *nMarqueeSpeed*  
 Liczba całkowita, która określa szybkość pasek ustawiony na marquee.  
  
### <a name="remarks"></a>Uwagi  
 Zostanie wyświetlony pasek ustawiony na marquee poniżej główny tekst `CTaskDialog` klasy.  
  
 Użyj *nMarqueeSpeed* można ustawić szybkości paskiem ustawiony na marquee; wartości większe wskazują niższej szybkości. Wartość 0 dla *nMarqueeSpeed* pasek ustawiony na marquee Przenieś szybkością domyślne dla systemu Windows staje się.  
  
 Ta metoda zgłasza wyjątek z [upewnij się, że](diagnostic-services.md#ensure) makro Jeśli *nMarqueeSpeed* jest mniejszy niż 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setprogressbarposition"></a>  CTaskDialog::SetProgressBarPosition  
 Ustawia położenie paska postępu.  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nProgressPos*  
 Pozycja paska postępu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zgłasza wyjątek z [upewnij się, że](diagnostic-services.md#ensure) makro Jeśli *nProgressPos* nie znajduje się w zakresie pasek postępu. Możesz zmienić zakres paska postępu z [CTaskDialog::SetProgressBarRange](#setprogressbarrange).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setprogressbarrange"></a>  CTaskDialog::SetProgressBarRange  
 Można dostosować zakres pasek postępu.  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nRangeMin*  
 Dolna granica pasek postępu.  
  
 [in] *nRangeMax*  
 Górna granica pasek postępu.  
  
### <a name="remarks"></a>Uwagi  
 Pozycja paska postępu jest względem *nRangeMin* i *nRangeMax*. Na przykład jeśli *nRangeMin* wynosi 50 i *nRangeMax* wynosi 100, pozycji 75 jest w połowie między pasek postępu. Użyj [CTaskDialog::SetProgressBarPosition](#setprogressbarposition) można ustawić pozycja paska postępu.  
  
 Aby wyświetlić pasek postępu, opcję TDF_SHOW_PROGRESS_BAR musi być włączona i TDF_SHOW_MARQUEE_PROGRESS_BAR nie mogą być włączone. Ta metoda automatycznie ustawia TDF_SHOW_PROGRESS_BAR i czyści TDF_SHOW_MARQUEE_PROGRESS_BAR. Użyj [CTaskDialog::SetOptions](#setoptions) ręcznie zmienić opcje dla tego wystąpienia [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md).  
  
 Ta metoda zgłasza wyjątek z [upewnij się, że](diagnostic-services.md#ensure) makro Jeśli *nRangeMin* jest nie mniejszy niż *nRangeMax*. Ta metoda również zgłasza wyjątek, jeśli `CTaskDialog` jest już wyświetlany i ma ustawiony na marquee pasek postępu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]  
  
##  <a name="setprogressbarstate"></a>  CTaskDialog::SetProgressBarState  
 Ustawia stan paska postępu i wyświetla je na `CTaskDialog`.  
  
```  
void SetProgressBarState(int nState = PBST_NORMAL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nInformacje*  
 Stan pasek postępu. W sekcji uwag możliwych wartości.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zgłasza wyjątek z [upewnij się, że](diagnostic-services.md#ensure) makro Jeśli `CTaskDialog` jest już wyświetlany i ma ustawiony na marquee pasek postępu.  
  
 W poniższej tabeli przedstawiono możliwe wartości *nInformacje*. W takich przypadkach pasek postępu będzie Wypełnianie kolorem regularne, dopóki nie osiągnie pozycji wyznaczonych stop. W tym momencie zmieni kolor na podstawie stanu.  
  
 PBST_NORMAL  
 Po postęp pasek się wypełni, `CTaskDialog` nie zmienia kolor paska. Domyślnie regularne kolor jest zielony.  
  
 PBST_ERROR  
 Po postęp pasek się wypełni, `CTaskDialog` kolor paska zmienia kolor błędu. Domyślnie jest to czerwony.  
  
 PBST_PAUSED  
 Po postęp pasek się wypełni, `CTaskDialog` zmienia kolor paska koloru wstrzymana. Domyślnie jest żółty.  
  
 Można ustawić, gdy zatrzyma się paska postępu [CTaskDialog::SetProgressBarPosition](#setprogressbarposition).  
  
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
 [in] *nRadioButtonID*  
 Identyfikator formantu przycisku radiowego.  
  
 [in] *bWłączony*  
 Wartość TRUE powoduje włączenie przycisku radiowego; Wartość FALSE, aby wyłączyć przycisk radiowy.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zgłasza wyjątek z [upewnij się, że](diagnostic-services.md#ensure) makro Jeśli *nRadioButtonID* nie jest prawidłowy identyfikator przycisku radiowego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]  
  
##  <a name="setverificationcheckbox"></a>  CTaskDialog::SetVerificationCheckbox  
 Ustawia stan zaznaczenia pola wyboru weryfikacji.  
  
```  
void SetVerificationCheckbox(BOOL bChecked);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bChecked*  
 Wartość true w pole wyboru weryfikacji wybrano kiedy `CTaskDialog` wyświetleniem; Wartość FALSE, aby zaznaczyć pole wyboru weryfikacji niezaznaczoną, kiedy `CTaskDialog` jest wyświetlany.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]  
  
##  <a name="setverificationcheckboxtext"></a>  CTaskDialog::SetVerificationCheckboxText  
 Ustawia tekst, który jest wyświetlany po prawej stronie pola wyboru weryfikacji.  
  
```  
void SetVerificationCheckboxText(CString& strVerificationText);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *strVerificationText*  
 Tekst, ta metoda jest wyświetlany obok pola wyboru weryfikacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zgłasza wyjątek z [upewnij się, że](diagnostic-services.md#ensure) makro, jeśli to wystąpienie `CTaskDialog` klasa jest już wyświetlany.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]  
  
##  <a name="setwindowtitle"></a>  CTaskDialog::SetWindowTitle  
 Ustawia tytuł `CTaskDialog`.  
  
```  
void SetWindowTitle(CString& strWindowTitle);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *strWindowTitle*  
 Nowy tytuł `CTaskDialog`.  
  
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
 [in] *strContent*  
 Ciąg używany dla zawartości `CTaskDialog`.  
  
 [in] *strMainInstruction*  
 Instrukcja głównego `CTaskDialog`.  
  
 [in] *strTitle*  
 Tytuł `CTaskDialog`.  
  
 [in] *nIDCommandControlsFirst*  
 Identyfikator ciągu pierwszego polecenia.  
  
 [in] *nIDCommandControlsLast*  
 Identyfikator ciągu ostatnie polecenie.  
  
 [in] *nCommonButtons*  
 Maska przycisków, aby dodać do `CTaskDialog`.  
  
 [in] *nTaskDialogOptions*  
 Zestaw opcji dla `CTaskDialog`.  
  
 [in] *strFooter*  
 Ciąg, który ma być używana jako stopki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba całkowita, która odpowiada wybór dokonany przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda statyczna umożliwia utworzenie wystąpienia `CTaskDialog` klasy bez jawnego tworzenia `CTaskDialog` obiektu w kodzie. Ponieważ nie istnieje żadne `CTaskDialog` obiekt i wszystkie inne metody nie można wywołać `CTaskDialog` użycie tej metody do wyświetlenia `CTaskDialog` dla użytkownika.  
  
 Ta metoda tworzy kontrolek przycisku polecenia przy użyciu danych z pliku zasobów aplikacji. Tabela ciągów w pliku zasobów ma kilka ciągów z ciągiem skojarzonych identyfikatorów. Ta metoda dodaje kontrolkę przycisku polecenia dla każdej prawidłowy wpis w tabeli ciągów między *nIDCommandControlsFirst* i *nCommandControlsLast*włącznie. W przypadku tych kontrolek przycisku polecenia ciąg w tabeli ciągów jest podpis formantu i identyfikator ciągu jest identyfikatorem formantu.  
  
 Zobacz [CTaskDialog::SetOptions](#setoptions) listę prawidłowych opcji.  
  
 `CTaskDialog` Zamyka, gdy użytkownik zaznaczy wspólnej przycisk formantu łącze polecenia lub zamyka `CTaskDialog`. Wartość zwracana jest identyfikator, który wskazuje, jak zostanie zamknięte okno dialogowe.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]  
  
##  <a name="taskdialogcallback"></a>  CTaskDialog::TaskDialogCallback  
 Struktura wywołuje tę metodę w odpowiedzi na różnych komunikatów systemu Windows.  
  
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
 [in] *hwnd*  
 Dojście do `m_hWnd` struktury `CTaskDialog`.  
  
 [in] *uNotification*  
 Kod powiadomienia, który określa wygenerowany komunikat.  
  
 [in] *wParam*  
 Więcej informacji na temat wiadomości.  
  
 [in] *lParam*  
 Więcej informacji na temat wiadomości.  
  
 [in] *dwRefData*  
 Wskaźnik do `CTaskDialog` obiekt, który dotyczy komunikat wywołania zwrotnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zależy od kodu określonych powiadomień. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja `TaskDialogCallback` obsługuje komunikat, a następnie wywołuje odpowiedni sposób [klasy obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md). Na przykład w odpowiedzi na komunikat TDN_BUTTON_CLICKED `TaskDialogCallback` wywołania [CTaskDialog::OnCommandControlClick](#oncommandcontrolclick).  
  
 Wartości *wParam* i *lParam* zależą od określonego komunikatu wygenerowany. Istnieje możliwość jedną lub obie te wartości muszą być puste. W poniższej tabeli przedstawiono domyślne powiadomienia, które są obsługiwane i wartości *wParam* i *lParam* reprezentują. Należy przesłonić tę metodę w klasie pochodnej, należy zaimplementować kod wywołania zwrotnego dla każdego komunikatu w tabeli poniżej.  
  
|Komunikat z powiadomieniem|*wParam* wartości|*lParam* wartości|  
|--------------------------|--------------------|--------------------|  
|TDN_CREATED|Nie używany.|Nie używany.|  
|TDN_NAVIGATED|Nie używany.|Nie używany.|  
|TDN_BUTTON_CLICKED|Przycisk polecenia kontroli identyfikatora.|Nie używany.|  
|TDN_HYPERLINK_CLICKED|Nie używany.|A [LPCWSTR](http://msdn.microsoft.com/library/windows/desktop/aa383751) struktury, która zawiera łącze.|  
|TDN_TIMER|Czas w milisekundach od `CTaskDialog` został utworzony lub został zresetowany przez czasomierz.|Nie używany.|  
|TDN_DESTROYED|Nie używany.|Nie używany.|  
|TDN_RADIO_BUTTON_CLICKED|Identyfikator przycisku radiowego.|Nie używany.|  
|TDN_DIALOG_CONSTRUCTED|Nie używany.|Nie używany.|  
|TDN_VERIFICATION_CLICKED|1, jeśli pole wyboru jest zaznaczone, 0, jeśli nie jest.|Nie używany.|  
|TDN_HELP|Nie używany.|Nie używany.|  
|TDN_EXPANDO_BUTTON_CLICKED|0, jeśli obszar rozszerzenia jest zwinięty; różna od zera, jeśli jest wyświetlany tekst rozszerzenia.|Nie używany.|  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Przewodnik: dodawanie obiektu CTaskDialog do aplikacji](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)



