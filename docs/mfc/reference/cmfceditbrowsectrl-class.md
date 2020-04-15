---
title: Klasa CMFCEditBrowseCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFileBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFolderBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::GetMode
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnAfterUpdate
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnBrowse
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnChangeLayout
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnDrawBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnIllegalFileName
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::SetBrowseButtonImage
helpviewer_keywords:
- CMFCEditBrowseCtrl [MFC], EnableBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFileBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFolderBrowseButton
- CMFCEditBrowseCtrl [MFC], GetMode
- CMFCEditBrowseCtrl [MFC], OnAfterUpdate
- CMFCEditBrowseCtrl [MFC], OnBrowse
- CMFCEditBrowseCtrl [MFC], OnChangeLayout
- CMFCEditBrowseCtrl [MFC], OnDrawBrowseButton
- CMFCEditBrowseCtrl [MFC], OnIllegalFileName
- CMFCEditBrowseCtrl [MFC], SetBrowseButtonImage
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
ms.openlocfilehash: 6c611297353f82e4ec90365cbe33db763d9c9838
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367537"
---
# <a name="cmfceditbrowsectrl-class"></a>Klasa CMFCEditBrowseCtrl

Klasa `CMFCEditBrowseCtrl` obsługuje kontrolkę przeglądania edycji, która jest edytowalnym polem tekstowym, które opcjonalnie zawiera przycisk przeglądania. Gdy użytkownik kliknie przycisk przeglądania, formant wykonuje akcję niestandardową lub wyświetla standardowe okno dialogowe zawierające przeglądarkę plików lub przeglądarkę folderów.

## <a name="syntax"></a>Składnia

```
class CMFCEditBrowseCtrl : public CEdit
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|Domyślny konstruktor.|
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|Włącza lub wyłącza (ukrywa) przycisk przeglądania.|
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Włącza przycisk przeglądania i przełącza kontrolka przeglądania edycji w tryb *przeglądania plików.*|
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Włącza przycisk przeglądania i przełącza kontrolka przeglądania edycji w *trybie przeglądania folderów.*|
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Zwraca bieżący tryb przeglądania.|
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|Wywoływana przez platformę po kontroli przeglądania edycji jest aktualizowana w wyniku akcji przeglądania.|
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|Wywoływane przez strukturę po kliknięciu przez użytkownika przycisku przeglądaj.|
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Ponownie rysuje bieżącą kontrolka przeglądania edycji.|
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|Wywoływane przez strukturę, aby narysować przycisk przeglądania.|
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|Wywoływana przez strukturę, gdy nazwa pliku niezgodna z prawem została wprowadzona w formancie edycji.|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Tłumaczy komunikaty okna, zanim zostaną wysłane do [funkcji TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows. Aby uzyskać informacje dotyczące składni i innych informacji, zobacz [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Ustawia niestandardowy obraz przycisku przeglądania.|

## <a name="remarks"></a>Uwagi

Użyj formantu przeglądania edycji, aby wybrać nazwę pliku lub folderu. Opcjonalnie użyj formantu, aby wykonać akcję niestandardową, taką jak wyświetlanie okna dialogowego. Można wyświetlić lub nie wyświetlić przycisk przeglądania, a na przycisku można zastosować niestandardową etykietę lub obraz.

*Tryb przeglądania* kontrolki przeglądania edycji określa, czy jest wyświetlany przycisk przeglądania i jakie działania występuje po kliknięciu przycisku. Aby uzyskać więcej informacji, zobacz [GetMode](#getmode) metody.

Klasa `CMFCEditBrowseCtrl` obsługuje następujące tryby.

- **tryb niestandardowy**

   Akcja niestandardowa jest wykonywana, gdy użytkownik kliknie przycisk przeglądania. Na przykład można wyświetlić okno dialogowe specyficzne dla aplikacji.

- **tryb pliku**

   Okno dialogowe standardowego wyboru pliku jest wyświetlane, gdy użytkownik kliknie przycisk przeglądania.

- **tryb folderu**

   Okno dialogowe wyboru folderu standardowego jest wyświetlane, gdy użytkownik kliknie przycisk przeglądania.

## <a name="how-to-specify-an-edit-browse-control"></a>Instrukcje: Określanie kontrolki przeglądania edycji

Wykonaj następujące kroki, aby włączyć formant przeglądania edycji w aplikacji:

1. Jeśli chcesz zaimplementować tryb przeglądania niestandardowego, `CMFCEditBrowseCtrl` należy wyprowadzić własną klasę z klasy, a następnie zastąpić [CMFCEditBrowseCtrl::OnBrowse](#onbrowse) metody. W zastąpiona metoda, wykonać akcję przeglądania niestandardowego i zaktualizować formant przeglądania edycji z wynikiem.

1. Osadź `CMFCEditBrowseCtrl` obiekt lub pochodną edycję przeglądaj obiekt kontrolny w obiekcie okna nadrzędnego.

1. Jeśli do utworzenia okna dialogowego użyjesz **Kreatora klas,** dodaj formant edycji ( `CEdit`) do formularza okna dialogowego. Ponadto dodaj zmienną, aby uzyskać dostęp do formantu w pliku nagłówka. W pliku nagłówka zmień typ zmiennej z `CEdit` na `CMFCEditBrowseCtrl`. Kontrolka przeglądania edycji zostanie utworzona automatycznie. Jeśli kreator **klas**nie jest używany, dodaj zmienną `CMFCEditBrowseCtrl` do `Create` pliku nagłówka, a następnie wywołaj jej metodę.

1. Jeśli dodasz kontrolkę przeglądania edycji do okna dialogowego, użyj narzędzia **ClassWizard,** aby skonfigurować wymianę danych.

1. Wywołanie [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton)lub [EnableBrowseButton](#enablebrowsebutton) metody, aby ustawić tryb przeglądania i wyświetlić przycisk przeglądania. Wywołanie [GetMode](#getmode) metody, aby uzyskać bieżący tryb przeglądania.

1. Aby zapewnić niestandardowy obraz dla przycisku przeglądania, wywołaj [Metodę SetBrowseButtonImage](#setbrowsebuttonimage) lub zastąpij metodę [OnDrawBrowseButton.](#ondrawbrowsebutton)

1. Aby usunąć przycisk przeglądania z kontrolki przeglądania edycji, należy wywołać metodę [EnableBrowseButton](#enablebrowsebutton) z *parametrem bEnable ustawionym* na FALSE.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cedit](../../mfc/reference/cedit-class.md)

[Cmfceditbrowsectrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCEditBrowseCtrl` używać `EnableFolderBrowseButton` `EnableFileBrowseButton`dwóch metod w klasie: i . W tym przykładzie jest częścią [new controls próbki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxeditbrowsectrl.h

## <a name="cmfceditbrowsectrlenablebrowsebutton"></a><a name="enablebrowsebutton"></a>CMFCEditBrowseCtrl::EnableBrowseButton

Wyświetla lub nie wyświetla przycisku przeglądania na bieżącym kontrolce przeglądania edycji.

```
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
PRAWDA, aby wyświetlić przycisk przeglądania; FALSE, aby nie wyświetlać przycisku przeglądania. Wartością domyślną jest PRAWDA.

*SzLabel (szLabel)*<br/>
Etykieta wyświetlana na przycisku przeglądania. Wartością domyślną jest " **...**".

### <a name="remarks"></a>Uwagi

Jeśli parametr *bEnable* to TRUE, należy zaimplementować akcję niestandardową do wykonania po kliknięciu przycisku przeglądania. Aby zaimplementować akcję niestandardową, należy wyprowadzić klasę z klasy, `CMFCEditBrowseCtrl` a następnie zastąpić jego [OnBrowse](#onbrowse) metody.

Jeśli *parametrem bEnable* jest PRAWDA, tryb przeglądania `BrowseMode_Default`formantu jest ; w przeciwnym razie tryb `BrowseMode_None`przeglądania jest . Aby uzyskać więcej informacji na temat trybów przeglądania, zobacz [GetMode](#getmode) metody.

## <a name="cmfceditbrowsectrlenablefilebrowsebutton"></a><a name="enablefilebrowsebutton"></a>CMFCEditBrowseCtrl::EnableFileBrowseButton

Wyświetla przycisk przeglądania bieżącej kontrolki przeglądania edycji i przełącza formant w tryb *przeglądania plików.*

```
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>Parametry

*lpszDefext*<br/>
Określa domyślne rozszerzenie nazwy pliku używane w oknie dialogowym wyboru pliku. Wartością domyślną jest NULL.

*lpszFilter*<br/>
Określa domyślny ciąg filtru używany w oknie dialogowym wyboru pliku. Wartością domyślną jest NULL.

*Dwflags*<br/>
Flagi okna dialogowego. Wartością domyślną jest kombinacja bitowa (OR) OFN_HIDEREADONLY i OFN_OVERWRITEPROMPT.

### <a name="remarks"></a>Uwagi

Gdy formant przeglądania edycji jest w trybie przeglądania plików, a użytkownik kliknie przycisk przeglądania, formant wyświetla okno dialogowe wyboru standardowego pliku.

Aby uzyskać pełną listę dostępnych flag, zobacz [OPENFILENAME struktury](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

## <a name="cmfceditbrowsectrlenablefolderbrowsebutton"></a><a name="enablefolderbrowsebutton"></a>CMFCEditBrowseCtrl::EnableFolderBrowseButton

Wyświetla przycisk przeglądania bieżącej kontrolki przeglądania edycji i przełącza formant w tryb *przeglądania folderów.*

```
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>Uwagi

Gdy kontrolka przeglądania edycji jest w trybie przeglądania folderów, a użytkownik kliknie przycisk przeglądania, formant wyświetla okno dialogowe wyboru folderu standardowego.

## <a name="cmfceditbrowsectrlgetmode"></a><a name="getmode"></a>CMFCEditBrowseCtrl::GetMode

Pobiera tryb przeglądania bieżącej kontrolki przeglądania edycji.

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości wyliczenia określająca bieżący tryb kontrolki przeglądania edycji. Tryb przeglądania określa, czy w ramach jest wyświetlany przycisk przeglądania i jakie działania występuje, gdy użytkownik kliknie ten przycisk.

W poniższej tabeli wymieniono możliwe wartości zwracane.

|Wartość|Opis|
|-----------|-----------------|
|`BrowseMode_Default`|**tryb niestandardowy**. Wykonywana jest akcja zdefiniowana przez programistę.|
|`BrowseMode_File`|**w trybie pliku**. Zostanie wyświetlone standardowe okno dialogowe przeglądarki plików.|
|`BrowseMode_Folder`|**tryb folderu**. Zostanie wyświetlone okno dialogowe przeglądarka folderów standardowych.|
|`BrowseMode_None`|Przycisk przeglądania nie jest wyświetlany.|

### <a name="remarks"></a>Uwagi

Domyślnie `CMFCEditBrowseCtrl` obiekt jest inicjowany w `BrowseMode_None` trybie. Zmodyfikuj tryb przeglądania za pomocą [metod CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)i [CMFCEditBrowseCtrl::EnableFolderBrowseButton.](#enablefolderbrowsebutton)

## <a name="cmfceditbrowsectrlonafterupdate"></a><a name="onafterupdate"></a>CMFCEditBrowseCtrl::OnAfterUpdate

Wywoływana przez platformę po kontroli przeglądania edycji jest aktualizowana w wyniku akcji przeglądania.

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby zaimplementować akcję niestandardową.

## <a name="cmfceditbrowsectrlonbrowse"></a><a name="onbrowse"></a>CMFCEditBrowseCtrl::OnBrowse

Wywoływane przez strukturę po kliknięciu przez użytkownika przycisku przeglądania kontrolki przeglądania edycji.

```
virtual void OnBrowse();
```

### <a name="remarks"></a>Uwagi

Ta metoda służy do wykonywania kodu niestandardowego, gdy użytkownik kliknie przycisk przeglądania kontrolki przeglądania edycji. Wywodź własną `CMFCEditBrowseCtrl` klasę z klasy `OnBrowse` i zastąpić jej metody. W tej metodzie zaimplementuj niestandardową akcję przeglądania i opcjonalnie zaktualizuj pole tekstowe formantu przeglądania edycji. W aplikacji użyj [EnableBrowseButton](#enablebrowsebutton) metody, aby umieścić kontrolki przeglądania edycji w *trybie przeglądania niestandardowego.*

## <a name="cmfceditbrowsectrlonchangelayout"></a><a name="onchangelayout"></a>CMFCEditBrowseCtrl::OnChangeLayout

Ponownie rysuje bieżącą kontrolka przeglądania edycji.

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy tryb przeglądania zmiany kontroli przeglądania edycji. Aby uzyskać więcej informacji, zobacz [CMFCEditBrowseCtrl::GetMode](#getmode).

## <a name="cmfceditbrowsectrlondrawbrowsebutton"></a><a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl::OnDrawBrowseButton

Wywoływane przez strukturę, aby narysować przycisk przeglądania na kontrolki przeglądania edycji.

```
virtual void OnDrawBrowseButton(
    CDC* pDC,
    CRect rect,
    BOOL bIsButtonPressed,
    BOOL bIsButtonHot);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia.

*Rect*<br/>
Prostokąt ograniczający przycisku przeglądania.

*bIsButtonPressed (Przycisk)*<br/>
PRAWDA, jeśli przycisk jest naciśnięty; w przeciwnym razie FALSE.

*bIsButtonHot*<br/>
PRAWDA, jeśli przycisk jest wyróżniony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję w klasie pochodnej, aby dostosować wygląd przycisku przeglądania.

## <a name="cmfceditbrowsectrlsetbrowsebuttonimage"></a><a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl::SetBrowseButtonImage

Ustawia obraz niestandardowy na przycisku przeglądania kontrolki przeglądania edycji.

```
void SetBrowseButtonImage(
    HICON hIcon,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(UINT uiBmpResId);
```

### <a name="parameters"></a>Parametry

*hIcon (własówce)*<br/>
Uchwyt ikony.

*hBitmapa*<br/>
Uchwyt mapy bitowej.

*interfejs użytkownika uiBmpResId*<br/>
Identyfikator zasobu mapy bitowej.

*bAutoDestroj*<br/>
TRUE, aby usunąć określoną ikonę lub mapę bitową po zamknięciu tej metody; w przeciwnym razie FALSE. Wartością domyślną jest PRAWDA.

### <a name="remarks"></a>Uwagi

Ta metoda służy do stosowania obrazu niestandardowego do przycisku przeglądania. Domyślnie struktura uzyskuje standardowy obraz, gdy formant przeglądania edycji znajduje się w *trybie przeglądania plików* lub *przeglądania folderów.*

## <a name="cmfceditbrowsectrlonillegalfilename"></a><a name="onillegalfilename"></a>CMFCEditBrowseCtrl::OnIllegalFileName

Wywoływana przez strukturę, gdy nazwa pliku niezgodna z prawem została wprowadzona w formancie edycji.

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>Parametry

*Strfilename*<br/>
Określa niedozwolona nazwa pliku.

### <a name="return-value"></a>Wartość zwracana

Należy zwrócić FAŁSZ, jeśli ta nazwa pliku nie może być przekazana dalej do okna dialogowego pliku. W takim przypadku fokus jest ustawiony z powrotem do kontrolki edycji i użytkownik powinien kontynuować edycję. Domyślna implementacja wyświetla okno komunikatu informujące użytkownika o nielegalnej nazwie pliku i zwraca WARTOŚĆ FAŁSZ. Można zastąpić tę metodę, poprawić nazwę pliku i zwrócić wartość TRUE do dalszego przetwarzania.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
