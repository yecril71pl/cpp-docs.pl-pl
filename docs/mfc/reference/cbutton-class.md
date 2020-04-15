---
title: Klasa CButton
ms.date: 11/04/2016
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
ms.openlocfilehash: 05ad60855cd03115cf88ab2b51e56e6a26822035
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352445"
---
# <a name="cbutton-class"></a>Klasa CButton

Udostępnia funkcje formantów przycisków systemu Windows.

## <a name="syntax"></a>Składnia

```
class CButton : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CButton::CButton](#cbutton)|Konstruuje `CButton` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CButton::Tworzenie](#create)|Tworzy kontrolka przycisku Windows `CButton` i dołącza go do obiektu.|
|[CButton::DrawItem](#drawitem)|Zastąd, aby narysować obiekt rysowany przez `CButton` właściciela.|
|[CButton::GetBitmap](#getbitmap)|Pobiera uchwyt mapy bitowej ustawionej wcześniej za pomocą [SetBitmap](#setbitmap).|
|[CButton::GetButtonStyle](#getbuttonstyle)|Pobiera informacje o stylu sterowania przyciskami.|
|[CButton::GetCheck](#getcheck)|Pobiera stan sprawdzania formantu przycisku.|
|[CButton::GetCursor](#getcursor)|Pobiera uchwyt obrazu kursora wcześniej ustawionego za pomocą [setcursor](#setcursor).|
|[CButton::GetIcon](#geticon)|Pobiera uchwyt ikony ustawionej wcześniej za pomocą [SetIcon](#seticon).|
|[CButton::GetIdealSize](#getidealsize)|Pobiera idealny rozmiar formantu przycisku.|
|[CButton::GetImageList](#getimagelist)|Pobiera listę obrazów formantu przycisku.|
|[CButton::GetNote](#getnote)|Pobiera składnik notatki bieżącego kontrolki łącza polecenia.|
|[CButton::GetNoteLength](#getnotelength)|Pobiera długość tekstu notatki dla bieżącego formantu łącza polecenia.|
|[CButton::GetSplitglyph](#getsplitglyph)|Pobiera glif skojarzony z bieżącą kontrolą przycisku podziału.|
|[CButton::GetSplitImageList](#getsplitimagelist)|Pobiera listę obrazów dla bieżącego sterowania przyciskiem podziału.|
|[CButton::GetSplitInfo](#getsplitinfo)|Pobiera informacje definiujące bieżącą kontrolki przycisku podziału.|
|[CButton::GetSplitSize](#getsplitsize)|Pobiera prostokąt ograniczający składnika rozwijanego bieżącego formantu przycisku podziału.|
|[CButton::GetSplitStyle](#getsplitstyle)|Pobiera style przycisków podziału, które definiują bieżącą kontrolę przycisku podziału.|
|[CButton::GetState](#getstate)|Pobiera stan wyboru, stan podświetlenia i stan fokusu formantu przycisku.|
|[CButton::GetTextMargin](#gettextmargin)|Pobiera margines tekstu formantu przycisku.|
|[CButton::SetBitmap](#setbitmap)|Określa mapę bitową, która ma być wyświetlana na przycisku.|
|[CButton::SetButtonStyle](#setbuttonstyle)|Zmienia styl przycisku.|
|[CButton::SetCheck](#setcheck)|Ustawia stan wyboru formantu przycisku.|
|[CButton::SetCursor](#setcursor)|Określa obraz kursora, który ma być wyświetlany na przycisku.|
|[CButton::SetDropDownState](#setdropdownstate)|Ustawia stan listy rozwijanej bieżącej kontroli przycisku podziału.|
|[CButton::SetIcon](#seticon)|Określa ikonę, która ma być wyświetlana na przycisku.|
|[CButton::SetImageList](#setimagelist)|Ustawia listę obrazów formantu przycisku.|
|[CButton::SetNote](#setnote)|Ustawia notatkę na bieżącym formancie łącza polecenia.|
|[CButton::SetSplitglyph](#setsplitglyph)|Kojarzy określony glif z bieżącą kontrolą przycisku podziału.|
|[CButton::SetSplitImageList](#setsplitimagelist)|Kojarzy listę obrazów z bieżącym formantem przycisku podziału.|
|[CButton::SetSplitInfo](#setsplitinfo)|Określa informacje definiujące bieżącą kontrolę przycisku podziału.|
|[CButton::SetSplitSize](#setsplitsize)|Ustawia prostokąt ograniczający składnika rozwijanego bieżącego przycisku podziału.|
|[CButton::SetSplitStyle](#setsplitstyle)|Ustawia styl bieżącego sterowania przyciskiem podziału.|
|[CButton::SetState](#setstate)|Ustawia stan podświetlania formantu przycisku.|
|[CButton::SetTextMargin](#settextmargin)|Ustawia margines tekstu formantu przycisku.|

## <a name="remarks"></a>Uwagi

Kontrolka przycisku to małe, prostokątne okno podrzędne, które można klikać i wyłączać. Przyciski mogą być używane samodzielnie lub w grupach i mogą być oznaczone etykietą lub wyświetlane bez tekstu. Przycisk zazwyczaj zmienia wygląd, gdy użytkownik kliknie go.

Typowe przyciski to pole wyboru, przycisk radiowy i przycisk. Obiekt `CButton` może stać się dowolnym z nich, zgodnie ze [stylem przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles) określonym podczas jego inicjowania przez funkcję [Utwórz](#create) element członkowski.

Ponadto [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) klasy pochodzące `CButton` z obsługuje tworzenie formanty przycisku oznaczone obrazami bitmapy zamiast tekstu. Może `CBitmapButton` mieć oddzielne mapy bitowe dla przycisku w górę, w dół, skoncentrowane i wyłączone stany.

Formant przycisku można utworzyć z szablonu okna dialogowego lub bezpośrednio w kodzie. W obu przypadkach najpierw wywołać konstruktora `CButton` do konstruowania `CButton` obiektu; następnie wywołaj funkcję elementu członkowskiego, `Create` aby utworzyć `CButton` kontrolka przycisku systemu Windows i dołączyć go do obiektu.

Budowa może być procesem jednoetapowym w `CButton`klasie wywodzącej się z . Napisz konstruktora dla klasy `Create` pochodnej i wywołać z wewnątrz konstruktora.

Jeśli chcesz obsługiwać wiadomości powiadomień systemu Windows wysyłane przez formant przycisku do jego nadrzędnego (zwykle klasy pochodzące z [CDialog](../../mfc/reference/cdialog-class.md)), dodaj wpis mapy wiadomości i funkcję elementu członkowskiego obsługi wiadomości do klasy nadrzędnej dla każdej wiadomości.

Każdy wpis mapy wiadomości ma następującą formę:

**On\_**_Powiadomienie_ _(id_, _memberFxn_ **)** **(**

gdzie *identyfikator* określa identyfikator okna podrzędnego formantu wysyłającego powiadomienie, a *memberFxn* jest nazwą funkcji nadrzędnego elementu członkowskiego, którą napisano w celu obsługi powiadomienia.

Prototyp funkcji rodzica jest następujący:

`afx_msg void memberFxn();`

Potencjalne wpisy mapy wiadomości są następujące:

|Wpis mapy|Wysłane do rodzica, gdy...|
|---------------|----------------------------|
|ON_BN_CLICKED|Użytkownik klika przycisk.|
|ON_BN_DOUBLECLICKED|Użytkownik dwukrotnie klika przycisk.|

Jeśli obiekt `CButton` zostanie utworzony z zasobu okna dialogowego, `CButton` obiekt zostanie automatycznie zniszczony po zamknięciu okna dialogowego przez użytkownika.

Jeśli utworzysz `CButton` obiekt w oknie, może być konieczne jego zniszczenie. Jeśli `CButton` obiekt zostanie utworzony na stercie przy użyciu **nowej** funkcji, należy wywołać **delete** na obiekcie, aby go zniszczyć, gdy użytkownik zamknie kontrolkę przycisku systemu Windows. Jeśli obiekt `CButton` zostanie utworzony na stosie lub zostanie osadzony w obiekcie nadrzędnego okna dialogowego, zostanie on automatycznie zniszczony.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cbuttoncbutton"></a><a name="cbutton"></a>CButton::CButton

Konstruuje `CButton` obiekt.

```
CButton();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

## <a name="cbuttoncreate"></a><a name="create"></a>CButton::Tworzenie

Tworzy kontrolka przycisku Windows `CButton` i dołącza go do obiektu.

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszCaption (własnowie)*<br/>
Określa tekst formantu przycisku.

*Dwstyle*<br/>
Określa styl formantu przycisku. Zastosuj dowolną kombinację [stylów przycisków](../../mfc/reference/styles-used-by-mfc.md#button-styles) do przycisku.

*Rect*<br/>
Określa rozmiar i położenie formantu przycisku. Może to być `CRect` obiekt lub `RECT` struktura.

*pParentWnd*<br/>
Określa okno nadrzędne formantu przycisku, `CDialog`zwykle . Nie może być null.

*Nid*<br/>
Określa identyfikator formantu przycisku.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CButton` obiektu w dwóch krokach. Najpierw wywołaj konstruktora, a następnie wywołaj `Create`, który `CButton` tworzy kontrolka przycisku systemu Windows i dołącza go do obiektu.

Jeśli podany jest styl WS_VISIBLE, system Windows wysyła przycisk kontrolki wszystkich komunikatów wymaganych do aktywacji i wyświetlenia przycisku.

Zastosuj następujące [style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki przycisków:

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_GROUP Do grupowanie formantów

- WS_TABSTOP Aby uwzględnić przycisk w kolejności tabulacji

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

## <a name="cbuttondrawitem"></a><a name="drawitem"></a>CButton::DrawItem

Wywoływana przez strukturę, gdy zmienił się wizualny aspekt przycisku rysowanego przez właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Długi wskaźnik do struktury [DRAWITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-drawitemstruct) Struktura zawiera informacje o elemencie, który ma zostać narysowany i o typie wymaganego rysunku.

### <a name="remarks"></a>Uwagi

Przycisk rysowany przez właściciela ma zestaw stylu BS_OWNERDRAW. Zastąpokaj tę funkcję elementu członkowskiego, aby zaimplementować rysunek dla obiektu rysowanego przez `CButton` właściciela. Aplikacja powinna przywrócić wszystkie obiekty interfejsu urządzenia graficznego (GDI) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem funkcji elementu członkowskiego.

Zobacz także wartości stylu [BS_.](../../mfc/reference/styles-used-by-mfc.md#button-styles)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

## <a name="cbuttongetbitmap"></a><a name="getbitmap"></a>CButton::GetBitmap

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać uchwyt mapy bitowej, wcześniej ustawiona z [SetBitmap](#setbitmap), który jest skojarzony z przyciskiem.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do mapy bitowej. NULL, jeśli wcześniej nie określono mapy bitowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttongetbuttonstyle"></a><a name="getbuttonstyle"></a>CButton::GetButtonStyle

Pobiera informacje o stylu sterowania przyciskami.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca style przycisków `CButton` dla tego obiektu. Ta funkcja zwraca tylko [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) wartości stylu, a nie żadnego z innych stylów okna.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttongetcheck"></a><a name="getcheck"></a>CButton::GetCheck

Pobiera stan wyboru przycisku opcji lub pola wyboru.

```
int GetCheck() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość zwracana z formantu przycisku utworzonego za pomocą stylu BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON lub BS_3STATE jest jedną z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|BST_UNCHECKED|Stan przycisku jest niezaznaczony.|
|BST_CHECKED|Stan przycisku jest sprawdzany.|
|BST_INDETERMINATE|Stan przycisku jest nieokreślony (dotyczy tylko wtedy, gdy przycisk ma styl BS_3STATE lub BS_AUTO3STATE).|

Jeśli przycisk ma inny styl, zwracana wartość jest BST_UNCHECKED.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttongetcursor"></a><a name="getcursor"></a>CButton::GetCursor

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać uchwyt kursora, wcześniej ustawione z [SetCursor](#setcursor), który jest skojarzony z przyciskiem.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do obrazu kursora. NULL, jeśli nie określono wcześniej kursora.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttongeticon"></a><a name="geticon"></a>CButton::GetIcon

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać uchwyt ikony, wcześniej ustawione z [SetIcon](#seticon), który jest skojarzony z przyciskiem.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do ikony. NULL, jeśli żadna ikona nie jest wcześniej określona.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttongetidealsize"></a><a name="getidealsize"></a>CButton::GetIdealSize

Pobiera idealny rozmiar dla sterowania przyciskami.

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>Parametry

*psize (psize)*<br/>
Wskaźnik do bieżącego rozmiaru przycisku.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego emuluje funkcjonalność komunikatu BCM_GETIDEALSIZE, zgodnie z opisem w sekcji [Przyciski](/windows/win32/controls/buttons) w programie Windows SDK.

## <a name="cbuttongetimagelist"></a><a name="getimagelist"></a>CButton::GetImageList

Wywołanie tej metody, aby uzyskać listę obrazów z kontrolki przycisku.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parametry

*pbuttonImagelist*<br/>
Wskaźnik do listy obrazów `CButton` obiektu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego emuluje funkcjonalność komunikatu BCM_GETIMAGELIST, zgodnie z opisem w sekcji [Przyciski](/windows/win32/controls/buttons) w programie Windows SDK.

## <a name="cbuttongetnote"></a><a name="getnote"></a>CButton::GetNote

Pobiera tekst notatki skojarzony z bieżącym kontrolką łącza polecenia.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*lpszNote (uwaga)*|[na zewnątrz] Wskaźnik do buforu, który wywołujący jest odpowiedzialny za przydzielanie i przydzielanie. Jeśli zwracaną wartością jest PRAWDA, bufor zawiera tekst notatki skojarzony z bieżącym kontrolką łącza polecenia; w przeciwnym razie bufor pozostaje niezmieniony.|
|*cchNote (uwaga)*|[w, na zewnątrz] Wskaźnik do niepodpisanej zmiennej całkowitej.<br /><br /> Gdy ta metoda jest wywoływana, zmienna zawiera rozmiar buforu określony przez *parametr lpszNote.*<br /><br /> Gdy ta metoda zwraca, jeśli zwracana wartość jest TRUE, zmienna zawiera rozmiar notatki skojarzonej z bieżącym formantem łącza polecenia. Jeśli zwracana wartość jest FAŁSZ, zmienna zawiera rozmiar buforu wymagany do umieszczenia notatki.|

### <a name="return-value"></a>Wartość zwracana

W pierwszym przeciążeniu [CString](../../atl-mfc-shared/using-cstring.md) obiektu, który zawiera tekst notatki skojarzone z bieżącego sterowania łączem polecenia.

— lub —

W drugim przeciążeniu TRUE, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko w przypadku formantów, których styl przycisku jest BS_COMMANDLINK lub BS_DEFCOMMANDLINK.

Ta metoda wysyła komunikat [BCM_GETNOTE,](/windows/win32/Controls/bcm-getnote) który jest opisany w windows SDK.

## <a name="cbuttongetnotelength"></a><a name="getnotelength"></a>CButton::GetNoteLength

Pobiera długość tekstu notatki dla bieżącego formantu łącza polecenia.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość tekstu notatki w 16-bitowych znakach Unicode dla bieżącego kontrolki łącza polecenia.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko w przypadku formantów, których styl przycisku jest BS_COMMANDLINK lub BS_DEFCOMMANDLINK.

Ta metoda wysyła komunikat [BCM_GETNOTELENGTH,](/windows/win32/Controls/bcm-getnotelength) który jest opisany w windows SDK.

## <a name="cbuttongetsplitglyph"></a><a name="getsplitglyph"></a>CButton::GetSplitglyph

Pobiera glif skojarzony z bieżącą kontrolą przycisku podziału.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Wartość zwracana

Znak glifów skojarzony z bieżącą kontrolą przycisku podziału.

### <a name="remarks"></a>Uwagi

Glif jest fizyczną reprezentacją znaku w określonej czcionce. Na przykład formant podziału przycisku może być ozdobiony glifem znaku wyboru Unicode (U + 2713).

Tej metody należy używać tylko w przypadku formantów, których styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Ta metoda inicjuje `mask` element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z flagą BCSIF_GLYPH, a następnie wysyła tę strukturę w komunikacie [BCM_GETSPLITINFO,](/windows/win32/Controls/bcm-getsplitinfo) który jest opisany w windows SDK. Po powrocie funkcji wiadomości ta metoda pobiera glif z elementu `himlGlyph` członkowskiego struktury.

## <a name="cbuttongetsplitimagelist"></a><a name="getsplitimagelist"></a>CButton::GetSplitImageList

Pobiera [listę obrazów](../../mfc/reference/cimagelist-class.md) dla bieżącego sterowania przyciskiem podziału.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CImageList.](../../mfc/reference/cimagelist-class.md)

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko w przypadku formantów, których styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Ta metoda inicjuje `mask` element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z flagą BCSIF_IMAGE, a następnie wysyła tę strukturę w komunikacie [BCM_GETSPLITINFO,](/windows/win32/Controls/bcm-getsplitinfo) który jest opisany w windows SDK. Po powrocie funkcji wiadomości ta metoda pobiera `himlGlyph` listę obrazów z elementu członkowskiego struktury.

## <a name="cbuttongetsplitinfo"></a><a name="getsplitinfo"></a>CButton::GetSplitInfo

Pobiera parametry, które określają, jak system Windows rysuje bieżącą kontrolki przycisku podziału.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Pinfo*|[na zewnątrz] Wskaźnik do [struktury BUTTON_SPLITINFO,](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) która odbiera informacje o bieżącej kontroli przycisku podziału. Wywołujący jest odpowiedzialny za przydzielanie struktury.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko w przypadku formantów, których styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Ta metoda wysyła [komunikat BCM_GETSPLITINFO,](/windows/win32/Controls/bcm-getsplitinfo) który jest opisany w windows SDK.

## <a name="cbuttongetsplitsize"></a><a name="getsplitsize"></a>CButton::GetSplitSize

Pobiera prostokąt ograniczający składnika rozwijanego bieżącego formantu przycisku podziału.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pSize (rozmiar)*|[na zewnątrz] Wskaźnik do [size](/windows/win32/api/windef/ns-windef-size) struktury, która odbiera opis prostokąta.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko w przypadku formantów, których styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Po rozwinięciu formantu przycisku podziału można wyświetlić składnik rozwijany, taki jak formant listy lub kontrolka pagera. Ta metoda pobiera prostokąt ograniczający, który zawiera składnik rozwijany.

Ta metoda inicjuje `mask` element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z flagą BCSIF_SIZE, a następnie wysyła tę strukturę w [komunikacie BCM_GETSPLITINFO,](/windows/win32/Controls/bcm-getsplitinfo) który jest opisany w windows SDK. Gdy funkcja message zwraca, ta metoda pobiera prostokąt ograniczający z elementu `size` członkowskiego struktury.

## <a name="cbuttongetsplitstyle"></a><a name="getsplitstyle"></a>CButton::GetSplitStyle

Pobiera style przycisków podziału, które definiują bieżącą kontrolę przycisku podziału.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Bitowa kombinacja stylów przycisków podziału. Aby uzyskać więcej `uSplitStyle` informacji, zobacz element członkowski [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko w przypadku formantów, których styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Style przycisków podziału określają wyrównanie, współczynnik proporcji i format graficzny, za pomocą którego system Windows rysuje ikonę przycisku podziału.

Ta metoda inicjuje `mask` element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z flagą BCSIF_STYLE, a następnie wysyła tę strukturę w komunikacie [BCM_GETSPLITINFO,](/windows/win32/Controls/bcm-getsplitinfo) który jest opisany w windows SDK. Po powrocie funkcji wiadomości ta metoda pobiera style `uSplitStyle` przycisków podziału z elementu członkowskiego struktury.

## <a name="cbuttongetstate"></a><a name="getstate"></a>CButton::GetState

Pobiera stan formantu przycisku.

```
UINT GetState() const;
```

### <a name="return-value"></a>Wartość zwracana

Pole bitowe zawierające kombinację wartości wskazujących bieżący stan formantu przycisku. W poniższej tabeli wymieniono możliwe wartości.

|Stan przycisku|Wartość|Opis|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|Stan początkowy.|
|BST_CHECKED|0x0001|Kontrolka przycisku jest zaznaczona.|
|BST_INDETERMINATE|0x0002|Stan jest nieokreślony (możliwe tylko wtedy, gdy formant przycisku ma trzy stany).|
|BST_PUSHED|0x0004|Kontrolka przycisku zostanie naciśnięta.|
|BST_FOCUS|0x0008|Kontrolka przycisku ma fokus.|

### <a name="remarks"></a>Uwagi

Kontrolka przycisku w stylu przycisku BS_3STATE lub BS_AUTO3STATE tworzy pole wyboru o stanie trzecim o nazwie stan nieokreślony. Stan nieokreślony wskazuje, że pole wyboru nie jest zaznaczone ani nie zaznaczone.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttongettextmargin"></a><a name="gettextmargin"></a>CButton::GetTextMargin

Wywołanie tej metody, aby `CButton` uzyskać margines tekstu obiektu.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parametry

*pmargin (pmargin)*<br/>
Wskaźnik do marginesu tekstu `CButton` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca margines tekstu.

### <a name="remarks"></a>Uwagi

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego emuluje funkcjonalność komunikatu BCM_GETTEXTMARGIN, zgodnie z opisem w sekcji [Przyciski](/windows/win32/controls/buttons) w programie Windows SDK.

## <a name="cbuttonsetbitmap"></a><a name="setbitmap"></a>CButton::SetBitmap

Wywołanie tej funkcji elementu członkowskiego, aby skojarzyć nową mapę bitową z przyciskiem.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmapa*<br/>
Uchwyt mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Uchwyt mapy bitowej wcześniej skojarzonej z przyciskiem.

### <a name="remarks"></a>Uwagi

Mapa bitowa zostanie automatycznie umieszczona na ścianie przycisku, domyślnie wyśrodkowany. Jeśli mapa bitowa jest zbyt duża dla przycisku, zostanie przycięta po obu stronach. Można wybrać inne opcje wyrównania, w tym następujące:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

W przeciwieństwie do [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), który używa `SetBitmap` czterech bitmap na przycisk, używa tylko jednej mapy bitowej na przycisk. Po naciśnięciu przycisku mapa bitowa jest przesuwana w dół i w prawo.

Użytkownik jest odpowiedzialny za zwolnienie mapy bitowej po zakończeniu pracy z nią.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttonsetbuttonstyle"></a><a name="setbuttonstyle"></a>CButton::SetButtonStyle

Zmienia styl przycisku.

```
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*styl nStyle*<br/>
Określa [styl przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*bRedraw*<br/>
Określa, czy przycisk ma zostać ponownie narysowany. Wartość niezerowa ponownie rysuje przycisk. Wartość 0 nie powoduje ponownego rysowania przycisku. Przycisk jest domyślnie ponownie rysowany.

### <a name="remarks"></a>Uwagi

Użyj `GetButtonStyle` funkcji elementu członkowskiego, aby pobrać styl przycisku. Słowo niskiego rzędu stylu przycisku Complete jest stylem specyficznym dla przycisku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttonsetcheck"></a><a name="setcheck"></a>CButton::SetCheck

Ustawia lub resetuje stan wyboru przycisku opcji lub pola wyboru.

```
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parametry

*nSprawda*<br/>
Określa stan sprawdzania. Ten parametr może być jedną z następujących czynności:

|Wartość|Znaczenie|
|-----------|-------------|
|BST_UNCHECKED|Ustaw stan przycisku na niezaznaczone.|
|BST_CHECKED|Ustaw stan przycisku tak, aby był zaznaczony.|
|BST_INDETERMINATE|Ustaw stan przycisku na nieokreślony. Tej wartości można użyć tylko wtedy, gdy przycisk ma styl BS_3STATE lub BS_AUTO3STATE.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego nie ma wpływu na przycisk.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttonsetcursor"></a><a name="setcursor"></a>CButton::SetCursor

Wywołanie tej funkcji elementu członkowskiego, aby skojarzyć nowy kursor z przyciskiem.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parametry

*hCursor (własno)-do*<br/>
Uchwyt kursora.

### <a name="return-value"></a>Wartość zwracana

Uchwyt kursora wcześniej skojarzony z przyciskiem.

### <a name="remarks"></a>Uwagi

Kursor zostanie automatycznie umieszczony na ścianie przycisku, domyślnie wyśrodkowany. Jeśli kursor jest zbyt duży dla przycisku, zostanie przycięty po obu stronach. Można wybrać inne opcje wyrównania, w tym następujące:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

W przeciwieństwie do [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), który używa `SetCursor` czterech bitmap na przycisk, używa tylko jednego kursora na przycisk. Po naciśnięciu przycisku kursor wydaje się przesuwać w dół i w prawo.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttonsetdropdownstate"></a><a name="setdropdownstate"></a>CButton::SetDropDownState

Ustawia stan listy rozwijanej bieżącej kontroli przycisku podziału.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*fDropDown (Dół)*|[w] TRUE, aby ustawić stan BST_DROPDOWNPUSHED; w przeciwnym razie FALSE.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Formant przycisku podziału ma styl BS_SPLITBUTTON lub BS_DEFSPLITBUTTON i składa się z przycisku i strzałki rozwijanej po prawej stronie. Aby uzyskać więcej informacji, zobacz [Style przycisków](/windows/win32/Controls/button-styles). Zwykle stan listy rozwijanej jest ustawiany, gdy użytkownik kliknie strzałkę listy rozwijanej. Ta metoda służy do programowego ustawiania stanu rozwijanego formantu. Strzałka rozwijana jest rysowana w cieniach, aby wskazać stan.

Ta metoda wysyła komunikat [BCM_SETDROPDOWNSTATE,](/windows/win32/Controls/bcm-setdropdownstate) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje *zmienną, m_splitButton*, która jest używana do programowego dostępu do formantu przycisku podziału. Ta zmienna jest używana w poniższym przykładzie.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia stan kontroli przycisku podziału, aby wskazać, że strzałka rozwijana jest wciśnięty.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

## <a name="cbuttonsetelevationrequired"></a><a name="setelevationrequired"></a>CButton::Wymagany setelevation

Ustawia stan bieżącego formantu przycisku na `elevation required`, który jest niezbędny do wyświetlania przez formant podwyższonej liczby ikon zabezpieczeń.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*fUchocz wymagane*|[w] TRUE, `elevation required` aby ustawić stan; w przeciwnym razie FALSE.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli kontrolka łącza przycisku lub polecenia wymaga uprawnień podwyższonych zabezpieczeń do wykonania akcji, ustaw formant na `elevation required` stan. Następnie system Windows wyświetla ikonę osłony kontroli konta użytkownika (UAC) na formancie. Aby uzyskać więcej informacji, zobacz "Kontrola konta użytkownika" w [MSDN](https://go.microsoft.com/fwlink/p/?linkid=18507).

Ta metoda wysyła komunikat [BCM_SETSHIELD,](/windows/win32/Controls/bcm-setshield) który jest opisany w windows SDK.

## <a name="cbuttonseticon"></a><a name="seticon"></a>CButton::SetIcon

Wywołanie tej funkcji elementu członkowskiego, aby skojarzyć nową ikonę z przyciskiem.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parametry

*hIcon (własówce)*<br/>
Uchwyt ikony.

### <a name="return-value"></a>Wartość zwracana

Uchwyt ikony uprzednio skojarzonej z przyciskiem.

### <a name="remarks"></a>Uwagi

Ikona zostanie automatycznie umieszczona na ścianie przycisku, domyślnie wyśrodkowany. Jeśli ikona jest zbyt duża dla przycisku, zostanie przycięta po obu stronach. Można wybrać inne opcje wyrównania, w tym następujące:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

W przeciwieństwie do [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), który używa `SetIcon` czterech bitmap na przycisk, używa tylko jednej ikony na przycisk. Po naciśnięciu przycisku ikona jest przesuwana w dół i w prawo.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttonsetimagelist"></a><a name="setimagelist"></a>CButton::SetImageList

Wywołanie tej metody, aby `CButton` ustawić listę obrazów obiektu.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parametry

*pbuttonImagelist*<br/>
Wskaźnik do nowej listy obrazów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego emuluje funkcjonalność komunikatu BCM_SETIMAGELIST, zgodnie z opisem w sekcji [Przyciski](/windows/win32/controls/buttons) w programie Windows SDK.

## <a name="cbuttonsetnote"></a><a name="setnote"></a>CButton::SetNote

Ustawia tekst notatki dla bieżącego kontrolki łącza polecenia.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*lpszNote (uwaga)*|[w] Wskaźnik do ciągu Unicode, który jest ustawiony jako tekst notatki dla formantu łącza polecenia.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko w przypadku formantów, których styl przycisku jest BS_COMMANDLINK lub BS_DEFCOMMANDLINK.

Ta metoda wysyła komunikat [BCM_SETNOTE,](/windows/win32/Controls/bcm-setnote) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje *zmienną, m_cmdLink*, która jest używana do programowego dostępu do formantu łącza polecenia. Ta zmienna jest używana w poniższym przykładzie.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia tekst notatki dla formantu łącza polecenia.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

## <a name="cbuttonsetsplitglyph"></a><a name="setsplitglyph"></a>CButton::SetSplitglyph

Kojarzy określony glif z bieżącą kontrolą przycisku podziału.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*chGlyph (chGlyph)*|[w] Znak określający glif do użycia jako strzałkę rozwijaną przycisku podziału.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko z formantami, które mają styl przycisku BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Glif jest fizyczną reprezentacją znaku w określonej czcionce. Parametr *chGlyph* nie jest używany jako glif, ale zamiast tego jest używany do wybierania glifów z zestawu glifów zdefiniowanych przez system. Domyślny glif strzałki rozwijanej jest określony przez znak "6" i przypomina znak Unicode BLACK DOWN-POINTING TRIANGLE (U+25BC).

Ta `mask` metoda inicjuje element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z flagą `himlGlyph` BCSIF_GLYPH i element członkowski z *parametrem chGlyph,* a następnie wysyła tę strukturę w komunikacie [BCM_GETSPLITINFO,](/windows/win32/Controls/bcm-getsplitinfo) który jest opisany w programie Windows SDK.

## <a name="cbuttonsetsplitimagelist"></a><a name="setsplitimagelist"></a>CButton::SetSplitImageList

Kojarzy [listę obrazów](../../mfc/reference/cimagelist-class.md) z bieżącym formantem przycisku podziału.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Lista pSplitImage*|[w] Wskaźnik do [obiektu CImageList,](../../mfc/reference/cimagelist-class.md) aby przypisać do bieżącego sterowania przyciskiem podziału.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko w przypadku formantów, których styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Ta metoda inicjuje `mask` element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z flagą `himlGlyph` BCSIF_IMAGE i element członkowski z parametrem *pSplitImageList,* a następnie wysyła tę strukturę w komunikacie [BCM_GETSPLITINFO,](/windows/win32/Controls/bcm-getsplitinfo) który jest opisany w programie Windows SDK.

## <a name="cbuttonsetsplitinfo"></a><a name="setsplitinfo"></a>CButton::SetSplitInfo

Określa parametry określające sposób, w jaki system Windows rysuje bieżącą kontrolę przycisku podziału.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Pinfo*|[w] Wskaźnik do [struktury BUTTON_SPLITINFO,](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) która definiuje bieżącą kontrolkę przycisku podziału.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko w przypadku formantów, których styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Ta metoda wysyła komunikat [BCM_SETSPLITINFO,](/windows/win32/Controls/bcm-setsplitinfo) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_splitButton`zmienną , która jest używana do programowego dostępu do formantu przycisku podziału.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu zmienia glif, który jest używany dla strzałki listy rozwijanej przycisku podziału. W przykładzie zastępuje glif trójkąta skierowanego w górę domyślny glif trójkąta skierowanego w dół. Glif, który jest wyświetlany zależy od znaku, `himlGlyph` który `BUTTON_SPLITINFO` można określić w człówka struktury. Glif trójkąta skierowanego w dół jest określony przez znak "6", a glif trójkąta wskazującego w górę jest określony przez znak "5". Dla porównania, zobacz metodę wygody, [CButton::SetSplitGlyph](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

## <a name="cbuttonsetsplitsize"></a><a name="setsplitsize"></a>CButton::SetSplitSize

Ustawia prostokąt ograniczający składnika rozwijanego bieżącego przycisku podziału.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pSize (rozmiar)*|[w] Wskaźnik do [struktury SIZE,](/windows/win32/api/windef/ns-windef-size) która opisuje prostokąt ograniczający.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko w przypadku formantów, których styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Po rozwinięciu formantu przycisku podziału można wyświetlić składnik rozwijany, taki jak formant listy lub kontrolka pagera. Ta metoda określa rozmiar prostokąta ograniczającego, który zawiera składnik rozwijany.

Ta `mask` metoda inicjuje element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z flagą `size` BCSIF_SIZE i element członkowski z *parametrem pSize,* a następnie wysyła tę strukturę w komunikacie [BCM_GETSPLITINFO,](/windows/win32/Controls/bcm-getsplitinfo) który jest opisany w programie Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_splitButton`zmienną , która jest używana do programowego dostępu do formantu przycisku podziału. Ta zmienna jest używana w poniższym przykładzie.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu podwaja rozmiar strzałki rozwijanej przycisku podziału.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

## <a name="cbuttonsetsplitstyle"></a><a name="setsplitstyle"></a>CButton::SetSplitStyle

Ustawia styl bieżącego sterowania przyciskiem podziału.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*uSplitStyle*|[w] Bitowa kombinacja stylów przycisków podziału. Aby uzyskać więcej `uSplitStyle` informacji, zobacz element członkowski [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko w przypadku formantów, których styl przycisku jest BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Style przycisków podziału określają wyrównanie, współczynnik proporcji i format graficzny, za pomocą którego system Windows rysuje ikonę przycisku podziału. Aby uzyskać więcej `uSplitStyle` informacji, zobacz element członkowski [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury.

Ta metoda inicjuje `mask` element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z flagą `uSplitStyle` BCSIF_STYLE i element członkowski z parametrem *uSplitStyle,* a następnie wysyła tę strukturę w komunikacie [BCM_GETSPLITINFO,](/windows/win32/Controls/bcm-getsplitinfo) który jest opisany w usłudze Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_splitButton`zmienną , która jest używana do programowego dostępu do formantu przycisku podziału.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia styl strzałki listy rozwijanej przycisku podziału. Styl BCSS_ALIGNLEFT wyświetla strzałkę po lewej stronie przycisku, a styl BCSS_STRETCH zachowuje proporcje strzałki rozwijanej po zmienić rozmiar przycisku.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

## <a name="cbuttonsetstate"></a><a name="setstate"></a>CButton::SetState

Określa, czy formant przycisku jest wyróżniony, czy nie.

```
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Parametry

*bWyświetlenie*<br/>
Określa, czy przycisk ma być podświetlony. Wartość niezerowa podświetla przycisk; wartość 0 usuwa wszelkie podświetlenia.

### <a name="remarks"></a>Uwagi

Podświetlanie wpływa na zewnętrzną część kontrolki przycisku. Nie ma to wpływu na stan wyboru przycisku radiowego lub pola wyboru.

Kontrolka przycisku jest automatycznie podświetlany, gdy użytkownik kliknie i przytrzymuje lewy przycisk myszy. Podświetlenie zostanie usunięte, gdy użytkownik zwolni przycisk myszy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttonsettextmargin"></a><a name="settextmargin"></a>CButton::SetTextMargin

Wywołanie tej metody, aby `CButton` ustawić margines tekstu obiektu.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parametry

*pmargin (pmargin)*<br/>
Wskaźnik do nowego marginesu tekstu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego emuluje funkcjonalność komunikatu BCM_SETTEXTMARGIN, zgodnie z opisem w sekcji [Przyciski](/windows/win32/controls/buttons) w programie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Klasa CScrollBar](../../mfc/reference/cscrollbar-class.md)<br/>
[Klasa CStatic](../../mfc/reference/cstatic-class.md)<br/>
[Klasa CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
