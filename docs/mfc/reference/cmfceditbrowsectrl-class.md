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
ms.openlocfilehash: db99c5e72e84bb359184f4c62594fcddff7d8ff6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505352"
---
# <a name="cmfceditbrowsectrl-class"></a>Klasa CMFCEditBrowseCtrl

`CMFCEditBrowseCtrl` Klasa obsługuje kontrolkę Edytuj przeglądanie, która jest edytowalnym polem tekstowym, które opcjonalnie zawiera przycisk przeglądania. Gdy użytkownik kliknie przycisk Przeglądaj, formant wykonuje akcję niestandardową lub wyświetla standardowe okno dialogowe zawierające przeglądarkę plików lub przeglądarkę folderów.

## <a name="syntax"></a>Składnia

```
class CMFCEditBrowseCtrl : public CEdit
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|Konstruktor domyślny.|
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|Włącza lub wyłącza (ukrywa) przycisk przeglądania.|
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Włącza przycisk Przeglądaj i umieszcza kontrolkę Edycja przeglądania w trybie *przeglądania plików* .|
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Włącza przycisk Przeglądaj i umieszcza kontrolkę Edytuj przeglądanie w trybie *przeglądania folderów* .|
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Zwraca bieżący tryb przeglądania.|
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|Wywoływane przez platformę po zaktualizowaniu kontrolki edycji przeglądania z wynikiem akcji przeglądania.|
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk Przeglądaj.|
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Odświeża bieżącą kontrolkę przeglądania edycji.|
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|Wywoływane przez platformę, by narysować przycisk przeglądania.|
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|Wywoływane przez platformę, gdy w kontrolce edycji wprowadzono niedozwoloną nazwę pliku.|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Tłumaczy komunikaty okna przed ich wysłaniem do funkcji systemu Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Aby uzyskać informacje o składni i więcej informacji, zobacz [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Ustawia niestandardowy obraz przycisku przeglądania.|

## <a name="remarks"></a>Uwagi

Użyj kontrolki edycji edytowanie, aby wybrać nazwę pliku lub folderu. Opcjonalnie można użyć kontrolki, aby wykonać akcję niestandardową, na przykład w celu wyświetlenia okna dialogowego. Możesz wyświetlić lub nie wyświetlić przycisku Przeglądaj i można zastosować na przycisku etykietę niestandardową lub obraz.

*Tryb przeglądania* kontrolki Edytuj przeglądanie decyduje o tym, czy ma być wyświetlany przycisk Przeglądaj, oraz jaka akcja występuje po kliknięciu przycisku. Aby uzyskać więcej informacji, zobacz [](#getmode) Metoda GetMode.

`CMFCEditBrowseCtrl` Klasa obsługuje następujące tryby.

- **Tryb niestandardowy**

   Akcja niestandardowa jest wykonywana, gdy użytkownik kliknie przycisk Przeglądaj. Na przykład można wyświetlić okno dialogowe specyficzne dla aplikacji.

- **tryb pliku**

   Standardowe okno dialogowe wyboru pliku jest wyświetlane, gdy użytkownik kliknie przycisk Przeglądaj.

- **Tryb folderu**

   Standardowe okno dialogowe wyboru folderów jest wyświetlane, gdy użytkownik kliknie przycisk Przeglądaj.

## <a name="how-to-specify-an-edit-browse-control"></a>Instrukcje: Określanie kontrolki przeglądania edycji

Wykonaj następujące kroki, aby dołączyć kontrolkę przeglądania edycji w swojej aplikacji:

1. Jeśli chcesz zaimplementować niestandardowy tryb przeglądania, Utwórz własną klasę z `CMFCEditBrowseCtrl` klasy, a następnie Zastąp metodę [CMFCEditBrowseCtrl:: OnBrowse](#onbrowse) . W zastąpionej metodzie należy wykonać niestandardową akcję przeglądania i zaktualizować kontrolkę Edytuj przeglądanie z wynikiem.

1. `CMFCEditBrowseCtrl` Osadź obiekt lub pochodny formant przeglądania edycji w obiekcie okna nadrzędnego.

1. Jeśli używasz **kreatora klas** do utworzenia okna dialogowego, Dodaj kontrolkę edycji ( `CEdit`) do formularza okna dialogowego. Ponadto Dodaj zmienną, aby uzyskać dostęp do kontrolki w pliku nagłówkowym. W pliku nagłówkowym Zmień typ zmiennej z `CEdit` na. `CMFCEditBrowseCtrl` Kontrolka edycji zostanie utworzona automatycznie. Jeśli nie używasz **kreatora klas**, Dodaj `CMFCEditBrowseCtrl` zmienną do pliku nagłówkowego, `Create` a następnie Wywołaj metodę.

1. Jeśli dodasz kontrolkę edycji przeglądania do okna dialogowego, użyj narzędzia **ClassWizard** , aby skonfigurować wymianę danych.

1. Wywołaj metodę [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton)lub [EnableBrowseButton](#enablebrowsebutton) , aby ustawić tryb przeglądania i wyświetlić przycisk przeglądania. Wywołaj [](#getmode) metodę GetMode, aby uzyskać bieżący tryb przeglądania.

1. Aby zapewnić niestandardowy obraz przycisku Przeglądaj, wywołaj metodę [SetBrowseButtonImage](#setbrowsebuttonimage) lub Zastąp metodę [OnDrawBrowseButton](#ondrawbrowsebutton) .

1. Aby usunąć przycisk przeglądania z kontrolki Edytuj przeglądanie, wywołaj metodę [EnableBrowseButton](#enablebrowsebutton) z parametrem *bEnable* ustawionym na wartość false.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia dwóch metod w `CMFCEditBrowseCtrl` klasie: `EnableFolderBrowseButton` i `EnableFileBrowseButton`. Ten przykład jest częścią [nowych kontrolek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxeditbrowsectrl. h

##  <a name="enablebrowsebutton"></a>CMFCEditBrowseCtrl::EnableBrowseButton

Wyświetla lub nie wyświetla przycisku Przeglądaj w bieżącej kontrolce przeglądania edycji.

```
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Wartość TRUE, aby wyświetlić przycisk przeglądania; Wartość FALSE, aby wyświetlić przycisk Przeglądaj. Wartość domyślna to TRUE.

*szLabel*<br/>
Etykieta wyświetlana na przycisku przeglądania. Wartość domyślna to " **...** ".

### <a name="remarks"></a>Uwagi

Jeśli parametr *bEnable* ma wartość true, należy zaimplementować akcję niestandardową do wykonania po kliknięciu przycisku przeglądania. Aby zaimplementować akcję niestandardową, należy utworzyć klasę z `CMFCEditBrowseCtrl` klasy, a następnie zastąpić metodę OnBrowse. [](#onbrowse)

Jeśli parametr *bEnable* ma wartość true, tryb przeglądania kontrolki to `BrowseMode_Default`; w przeciwnym razie tryb przeglądania to. `BrowseMode_None` Aby uzyskać więcej informacji na temat trybów przeglądania, [](#getmode) Zobacz GetMode Metoda.

##  <a name="enablefilebrowsebutton"></a>CMFCEditBrowseCtrl::EnableFileBrowseButton

Wyświetla przycisk Przeglądaj w bieżącej kontrolce edycji przeglądania i umieszcza formant w trybie *przeglądania plików* .

```
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>Parametry

*lpszDefExt*<br/>
Określa domyślne rozszerzenie nazwy pliku, które jest używane w oknie dialogowym Wybór pliku. Wartość domyślna to NULL.

*lpszFilter*<br/>
Określa domyślny ciąg filtru, który jest używany w oknie dialogowym Wybór pliku. Wartość domyślna to NULL.

*flagiDW*<br/>
Flagi okna dialogowego. Wartość domyślna to kombinacja bitowa (lub) OFN_HIDEREADONLY i OFN_OVERWRITEPROMPT.

### <a name="remarks"></a>Uwagi

Gdy kontrolka edycji jest w trybie przeglądania plików, a użytkownik kliknie przycisk Przeglądaj, w oknie dialogowym Wybór pliku standardowego zostanie wyświetlone okno dialogowe.

Pełną listę dostępnych flag można znaleźć w temacie [OPENFILENAME Structure](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

##  <a name="enablefolderbrowsebutton"></a>CMFCEditBrowseCtrl::EnableFolderBrowseButton

Wyświetla przycisk Przeglądaj w bieżącej kontrolce edycji przeglądania i umieszcza formant w trybie *przeglądania folderów* .

```
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>Uwagi

Gdy kontrolka Edytuj przeglądanie jest w trybie przeglądania folderów, a użytkownik kliknie przycisk Przeglądaj, w oknie dialogowym wybór folderu standardowego zostanie wyświetlone okno dialogowe.

##  <a name="getmode"></a>CMFCEditBrowseCtrl:: GetMode

Pobiera tryb przeglądania bieżącego formantu przeglądania edycji.

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości wyliczenia, która określa bieżący tryb kontrolki edycji przeglądania. Tryb przeglądania Określa, czy struktura ma wyświetlać przycisk Przeglądaj i jakie akcje występuje po kliknięciu tego przycisku przez użytkownika.

Poniższa tabela zawiera listę możliwych zwracanych wartości.

|Wartość|Opis|
|-----------|-----------------|
|`BrowseMode_Default`|**Tryb niestandardowy**. Jest wykonywana akcja zdefiniowana przez programistę.|
|`BrowseMode_File`|**tryb pliku**. Zostanie wyświetlone okno dialogowe standardowa przeglądarka plików.|
|`BrowseMode_Folder`|**Tryb folderu**. Zostanie wyświetlone okno dialogowe standardowa przeglądarka folderów.|
|`BrowseMode_None`|Przycisk przeglądania nie jest wyświetlany.|

### <a name="remarks"></a>Uwagi

Domyślnie `CMFCEditBrowseCtrl` obiekt jest zainicjowany do `BrowseMode_None` trybu. Zmodyfikuj tryb przeglądania przy użyciu metod [CMFCEditBrowseCtrl:: EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl:: EnableFileBrowseButton](#enablefilebrowsebutton)i [CMFCEditBrowseCtrl:: EnableFolderBrowseButton](#enablefolderbrowsebutton) .

##  <a name="onafterupdate"></a>CMFCEditBrowseCtrl::OnAfterUpdate

Wywoływane przez platformę po zaktualizowaniu kontrolki edycji przeglądania z wynikiem akcji przeglądania.

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby zaimplementować akcję niestandardową.

##  <a name="onbrowse"></a>CMFCEditBrowseCtrl:: OnBrowse

Wywoływane przez platformę, gdy użytkownik kliknie przycisk Przeglądaj w kontrolce Edycja przeglądania.

```
virtual void OnBrowse();
```

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby wykonać kod niestandardowy, gdy użytkownik kliknie przycisk Przeglądaj w kontrolce Edycja. Utwórz własną klasę z `CMFCEditBrowseCtrl` klasy i Zastąp jej `OnBrowse` metodę. W tej metodzie Zaimplementuj niestandardową akcję przeglądania i opcjonalnie zaktualizuj pole tekstowe kontrolki Edytuj przeglądanie. W aplikacji użyj metody [EnableBrowseButton](#enablebrowsebutton) , aby ustawić kontrolkę Edytuj przeglądanie w trybie *przeglądania niestandardowego* .

##  <a name="onchangelayout"></a>CMFCEditBrowseCtrl::OnChangeLayout

Odświeża bieżącą kontrolkę przeglądania edycji.

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy tryb przeglądania kontrolki edycji edytuje zmiany. Aby uzyskać więcej informacji, zobacz [CMFCEditBrowseCtrl:: GetMode](#getmode).

##  <a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl::OnDrawBrowseButton

Wywoływane przez platformę, aby narysować przycisk przeglądania w kontrolce Edycja przeglądania.

```
virtual void OnDrawBrowseButton(
    CDC* pDC,
    CRect rect,
    BOOL bIsButtonPressed,
    BOOL bIsButtonHot);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do kontekstu urządzenia.

*Cinania*<br/>
Prostokąt ograniczający przycisk przeglądania.

*bIsButtonPressed*<br/>
Ma wartość TRUE, jeśli przycisk jest wciśnięty; w przeciwnym razie FALSE.

*bIsButtonHot*<br/>
Ma wartość TRUE, jeśli przycisk jest wyróżniony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję w klasie pochodnej, aby dostosować wygląd przycisku przeglądania.

##  <a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl::SetBrowseButtonImage

Ustawia obraz niestandardowy na przycisku przeglądania kontrolki edytowanie.

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

*hIcon*<br/>
Uchwyt ikony.

*hBitmap*<br/>
Uchwyt mapy bitowej.

*uiBmpResId*<br/>
Identyfikator zasobu mapy bitowej.

*bAutoDestroy*<br/>
TRUE, aby usunąć określoną ikonę lub mapę bitową, gdy ta metoda zostanie zakończona; w przeciwnym razie FALSE. Wartość domyślna to TRUE.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby zastosować obraz niestandardowy do przycisku przeglądania. Domyślnie struktura uzyskuje standardowy obraz, gdy kontrolka edycji jest w trybie przeglądania *plików* lub *folderów* .

##  <a name="onillegalfilename"></a>CMFCEditBrowseCtrl::OnIllegalFileName

Wywoływane przez platformę, gdy w kontrolce edycji wprowadzono niedozwoloną nazwę pliku.

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>Parametry

*strFileName*<br/>
Określa niedozwoloną nazwę pliku.

### <a name="return-value"></a>Wartość zwracana

Jeśli nazwa pliku nie może zostać przeniesiona do okna dialogowego pliku, powinna zostać zwrócona wartość FALSE. W takim przypadku fokus jest ustawiany z powrotem do kontrolki edycji, a użytkownik powinien kontynuować edytowanie. Domyślna implementacja Wyświetla okno komunikatu informującego użytkownika o niedozwolonej nazwie pliku i zwraca wartość FALSE. Można zastąpić tę metodę, poprawić nazwę pliku i zwrócić wartość TRUE w celu dalszej obróbki.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
