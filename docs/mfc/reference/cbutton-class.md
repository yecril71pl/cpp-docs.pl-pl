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
ms.openlocfilehash: 669bdb18e378c4dc39bdc6d51ca1ebe7f93fa839
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507427"
---
# <a name="cbutton-class"></a>Klasa CButton

Oferuje funkcje kontrolek przycisku systemu Windows.

## <a name="syntax"></a>Składnia

```
class CButton : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CButton:: CButton](#cbutton)|Konstruuje `CButton` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CButton:: Create](#create)|Tworzy formant przycisku systemu Windows i dołącza go do `CButton` obiektu.|
|[CButton::D rawItem](#drawitem)|Przesłoń, aby narysować obiekt `CButton` rysowany przez właściciela.|
|[CButton:: getmap](#getbitmap)|Pobiera uchwyt mapy bitowej poprzednio ustawiony za pomocą [Setmap bitowych](#setbitmap).|
|[CButton:: getbutton](#getbuttonstyle)|Pobiera informacje o stylu kontrolki przycisku.|
|[CButton:: getcheck](#getcheck)|Pobiera stan zaznaczenia kontrolki Button.|
|[CButton:: GetCursor](#getcursor)|Pobiera uchwyt obrazu kursora wcześniej ustawionego za pomocą elementu [SetCursor](#setcursor).|
|[CButton::GetIcon](#geticon)|Pobiera uchwyt ikony wcześniej ustawionej za pomocą [SetIcon](#seticon).|
|[CButton::GetIdealSize](#getidealsize)|Pobiera idealny rozmiar kontrolki przycisku.|
|[CButton:: GetImageList](#getimagelist)|Pobiera listę obrazów kontrolki przycisku.|
|[CButton:: getnote](#getnote)|Pobiera składnik uwagi bieżącej kontrolki linku polecenia.|
|[CButton:: GetNoteLength](#getnotelength)|Pobiera długość tekstu komentarza dla bieżącej kontrolki łącza polecenia.|
|[CButton:: GetSplitGlyph](#getsplitglyph)|Pobiera glif skojarzony z bieżącą kontrolką przycisku podziału.|
|[CButton:: GetSplitImageList](#getsplitimagelist)|Pobiera listę obrazów dla kontrolki bieżącego przycisku podziału.|
|[CButton:: GetSplitInfo](#getsplitinfo)|Pobiera informacje definiujące bieżącą kontrolkę przycisku podziału.|
|[CButton:: GetSplitSize](#getsplitsize)|Pobiera prostokąt ograniczenia składnika listy rozwijanej bieżącego formantu przycisku podziału.|
|[CButton:: getsplit](#getsplitstyle)|Pobiera style przycisku podziału definiujące bieżącą kontrolkę przycisku podziału.|
|[CButton:: GetState](#getstate)|Pobiera stan zaznaczenia, wyróżnij stan i fokus kontrolki przycisku.|
|[CButton:: GetTextMargin](#gettextmargin)|Pobiera margines tekstu kontrolki przycisku.|
|[CButton:: setmap](#setbitmap)|Określa mapę bitową, która będzie wyświetlana na przycisku.|
|[CButton::SetButtonStyle](#setbuttonstyle)|Zmienia styl przycisku.|
|[CButton::SetCheck](#setcheck)|Ustawia stan zaznaczenia kontrolki przycisku.|
|[CButton:: SetCursor](#setcursor)|Określa obraz kursora, który będzie wyświetlany na przycisku.|
|[CButton:: SetDropDownState](#setdropdownstate)|Ustawia stan listy rozwijanej bieżącego formantu przycisku podziału.|
|[CButton::SetIcon](#seticon)|Określa ikonę, która będzie wyświetlana na przycisku.|
|[CButton:: SetImageList](#setimagelist)|Ustawia listę obrazów kontrolki przycisku.|
|[CButton:: SetNote](#setnote)|Ustawia uwagę na bieżącą kontrolkę linku polecenia.|
|[CButton:: SetSplitGlyph](#setsplitglyph)|Kojarzy określony glif z bieżącą kontrolką przycisku podziału.|
|[CButton:: SetSplitImageList](#setsplitimagelist)|Kojarzy listę obrazów z bieżącym formantem przycisku podziału.|
|[CButton::SetSplitInfo](#setsplitinfo)|Określa informacje definiujące bieżącą kontrolkę przycisku podziału.|
|[CButton::SetSplitSize](#setsplitsize)|Ustawia prostokąt ograniczenia składnika listy rozwijanej bieżącego formantu przycisku podziału.|
|[CButton::SetSplitStyle](#setsplitstyle)|Ustawia styl bieżącej kontrolki przycisku podziału.|
|[CButton:: setstate](#setstate)|Ustawia stan wyróżniania kontrolki przycisku.|
|[CButton:: SetTextMargin](#settextmargin)|Ustawia margines tekstu kontrolki przycisku.|

## <a name="remarks"></a>Uwagi

Formant Button jest małym prostokątnym oknem podrzędnym, które można kliknąć i wyłączyć. Przyciski mogą być używane samodzielnie lub w grupach i mogą być oznaczone etykietami lub wyświetlane bez tekstu. Przycisk zazwyczaj zmienia wygląd, gdy użytkownik go klika.

Typowymi przyciskami są pola wyboru, przycisk radiowy i przyciski. Obiekt może być dowolnym z tych elementów, zgodnie z stylem [przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles) określonym podczas inicjowania przez funkcję tworzenia elementu członkowskiego. [](#create) `CButton`

Ponadto Klasa [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) , która pochodzi od `CButton` , obsługuje tworzenie kontrolek przycisków oznaczonych obrazami mapy bitowej zamiast tekstu. `CBitmapButton` Może mieć oddzielne mapy bitowe dla stanów up, w dół, skoncentrowanych i wyłączonych przycisku.

Kontrolkę przycisku można utworzyć z poziomu szablonu okna dialogowego lub bezpośrednio w kodzie. W obu przypadkach najpierw `CButton` Wywołaj konstruktora w celu `CButton` skonstruowania `Create` obiektu, a następnie wywołaj funkcję członkowską, aby utworzyć kontrolkę przycisk `CButton` systemu Windows i dołączyć ją do obiektu.

Konstrukcja może być procesem jednoetapowym klasy pochodzącej od `CButton`. Napisz konstruktora dla klasy pochodnej i Wywołaj `Create` z konstruktora.

Jeśli chcesz obsługiwać komunikaty powiadomień systemu Windows wysyłane przez kontrolkę przycisku do jego elementu nadrzędnego (zwykle klasy pochodzącej od [CDialog](../../mfc/reference/cdialog-class.md)), Dodaj do klasy nadrzędnej wpis mapy komunikatów i funkcję członkowską obsługi komunikatów dla każdego komunikatu.

Każdy wpis mapy komunikatów przyjmuje następującą formę:

**On\_** _Notification_ **(** _ID_, _memberFxn_ **)**

gdzie *ID* określa identyfikator okna podrzędnego kontrolki wysyłającej powiadomienie, a *memberFxn* jest nazwą nadrzędnej funkcji składowej, która została zapisywana w celu obsługi powiadomienia.

Prototyp funkcji elementu nadrzędnego jest następujący:

`afx_msg void memberFxn();`

Potencjalne wpisy mapy komunikatów są następujące:

|Wpis mapy|Wysyłany do elementu nadrzędnego, gdy...|
|---------------|----------------------------|
|ON_BN_CLICKED|Użytkownik klika przycisk.|
|ON_BN_DOUBLECLICKED|Użytkownik klika dwukrotnie przycisk.|

Jeśli utworzysz `CButton` obiekt z zasobu okna dialogowego `CButton` , obiekt zostanie automatycznie zniszczony, gdy użytkownik zamknie okno dialogowe.

Jeśli utworzysz `CButton` obiekt w oknie, może być konieczne jego zniszczenie. Jeśli `CButton` obiekt jest tworzony na stercie przy użyciu **nowej** funkcji, należy wywołać metodę **delete** dla obiektu, aby zniszczyć go, gdy użytkownik zamknie formant przycisku systemu Windows. Jeśli `CButton` obiekt zostanie utworzony na stosie lub osadzony w obiekcie okna dialogowego nadrzędnym, zostanie zniszczony automatycznie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="cbutton"></a>CButton:: CButton

Konstruuje `CButton` obiekt.

```
CButton();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

##  <a name="create"></a>CButton:: Create

Tworzy formant przycisku systemu Windows i dołącza go do `CButton` obiektu.

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszCaption*<br/>
Określa tekst kontrolki przycisku.

*dwStyle*<br/>
Określa styl kontrolki przycisku. Zastosuj dowolną kombinację [stylów przycisków](../../mfc/reference/styles-used-by-mfc.md#button-styles) do przycisku.

*cinania*<br/>
Określa rozmiar i położenie kontrolki przycisku. Może to być `CRect` obiekt `RECT` lub struktura.

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki przycisku, zazwyczaj a `CDialog`. Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki przycisku.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`CButton` Obiekt jest konstruowany w dwóch krokach. Najpierw Wywołaj konstruktora, a następnie Wywołaj `Create`, który tworzy formant przycisku systemu Windows i dołącza go `CButton` do obiektu.

Jeśli określony jest styl WS_VISIBLE, system Windows wysyła wszystkie komunikaty wymagane do aktywacji i wyświetlania przycisku.

Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki Button:

- WS_CHILD zawsze

- WS_VISIBLE zazwyczaj

- WS_DISABLED rzadko

- WS_GROUP do grup kontrolek

- WS_TABSTOP, aby uwzględnić przycisk w kolejności tabulacji

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

##  <a name="drawitem"></a>CButton::D rawItem

Wywoływane przez platformę, gdy wizualny aspekt przycisku rysowanego przez właściciela został zmieniony.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Długi wskaźnik do struktury [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) . Struktura zawiera informacje na temat elementu, który ma być rysowany, i wymagany typ rysunku.

### <a name="remarks"></a>Uwagi

Przycisk rysowany przez właściciela ma ustawiony styl BS_OWNERDRAW. Przesłoń tę funkcję elementu członkowskiego, aby zaimplementować rysowanie dla `CButton` obiektu rysowanego przez właściciela. Aplikacja powinna przywrócić wszystkie obiekty interfejsu GDI (Graphics Device Interface) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem działania elementu członkowskiego.

Zobacz też wartości stylu [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

##  <a name="getbitmap"></a>CButton:: getmap

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać uchwyt mapy bitowej, wcześniej [](#setbitmap)ustawionej za pomocą metody setmap, która jest skojarzona z przyciskiem.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do mapy bitowej. Wartość NULL, jeśli nie określono wcześniej mapy bitowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="getbuttonstyle"></a>CButton:: getbutton

Pobiera informacje o stylu kontrolki przycisku.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca style przycisków dla tego `CButton` obiektu. Ta funkcja zwraca tylko wartości stylu [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) , a nie inne style okna.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="getcheck"></a>CButton:: getcheck

Pobiera stan zaznaczenia przycisku radiowego lub pola wyboru.

```
int GetCheck() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość zwracana z formantu Button utworzonego przy użyciu stylu BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON lub BS_3STATE jest jedną z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|BST_UNCHECKED|Stan przycisku nie jest zaznaczony.|
|BST_CHECKED|Stan przycisku jest zaznaczony.|
|BST_INDETERMINATE|Stan przycisku jest nieokreślony (ma zastosowanie tylko wtedy, gdy przycisk ma styl BS_3STATE lub BS_AUTO3STATE).|

Jeśli przycisk ma inny styl, wartość zwracana to BST_UNCHECKED.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="getcursor"></a>CButton:: GetCursor

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać uchwyt kursora wcześniej ustawiony za [](#setcursor)pomocą elementu SetCursor, który jest skojarzony z przyciskiem.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt obrazu kursora. Wartość NULL, jeśli kursor nie jest wcześniej określony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="geticon"></a>CButton:: GetIcon

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać uchwyt ikony, wcześniej ustawionej za pomocą [SetIcon](#seticon), która jest skojarzona z przyciskiem.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do ikony. Wartość NULL, jeśli nie określono wcześniej ikony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="getidealsize"></a>CButton:: GetIdealSize

Pobiera idealny rozmiar kontrolki przycisku.

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>Parametry

*psize*<br/>
Wskaźnik do bieżącego rozmiaru przycisku.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność komunikatu BCM_GETIDEALSIZE, zgodnie z opisem w sekcji [przyciski](/windows/win32/controls/buttons) Windows SDK.

##  <a name="getimagelist"></a>CButton:: GetImageList

Wywołaj tę metodę, aby pobrać listę obrazów z kontrolki Button.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parametry

*pbuttonImagelist*<br/>
Wskaźnik do listy `CButton` obrazów obiektu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność komunikatu BCM_GETIMAGELIST, zgodnie z opisem w sekcji [przyciski](/windows/win32/controls/buttons) Windows SDK.

##  <a name="getnote"></a>CButton:: getnote

Pobiera tekst notatki skojarzony z bieżącą kontrolką łącza polecenia.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*lpszNote*|określoną Wskaźnik do buforu, którego obiekt wywołujący jest odpowiedzialny za przydzielanie i cofanie przydziału. Jeśli wartość zwracana ma wartość TRUE, bufor zawiera tekst komentarza, który jest skojarzony z bieżącą kontrolką łącza polecenia; w przeciwnym razie bufor nie zmieni się.|
|*cchNote*|[in. out] Wskaźnik do zmiennej niepodpisanej liczby całkowitej.<br /><br /> Gdy ta metoda jest wywoływana, zmienna zawiera rozmiar buforu określony przez parametr *lpszNote* .<br /><br /> Gdy ta metoda zwraca, jeśli wartość zwracana jest TRUE, zmienna zawiera rozmiar notatki skojarzonej z bieżącym formantem łącza polecenia. Jeśli zwracaną wartością jest FALSE, zmienna zawiera rozmiar buforu wymagany do zawierania notatki.|

### <a name="return-value"></a>Wartość zwracana

W pierwszym przeciążeniu obiekt [CString](../../atl-mfc-shared/using-cstring.md) , który zawiera tekst komentarza skojarzony z bieżącą kontrolką łącza polecenia.

—lub—

W drugim przeciążeniu, wartość TRUE, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko z kontrolkami, których styl Button to BS_COMMANDLINK lub BS_DEFCOMMANDLINK.

Ta metoda wysyła komunikat [BCM_GETNOTE](/windows/win32/Controls/bcm-getnote) , który jest opisany w Windows SDK.

##  <a name="getnotelength"></a>CButton:: GetNoteLength

Pobiera długość tekstu komentarza dla bieżącej kontrolki łącza polecenia.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość tekstu notatki (w 16-bitowych znakach Unicode) dla bieżącej kontrolki linku polecenia.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko z kontrolkami, których styl Button to BS_COMMANDLINK lub BS_DEFCOMMANDLINK.

Ta metoda wysyła komunikat [BCM_GETNOTELENGTH](/windows/win32/Controls/bcm-getnotelength) , który jest opisany w Windows SDK.

##  <a name="getsplitglyph"></a>CButton:: GetSplitGlyph

Pobiera glif skojarzony z bieżącą kontrolką przycisku podziału.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Wartość zwracana

Znak glifu skojarzony z bieżącą kontrolką przycisku podziału.

### <a name="remarks"></a>Uwagi

Symbol jest fizyczną reprezentacją znaku w określonej czcionce. Na przykład Kontrolka przycisku podziału może być dekoracyjna przy użyciu symbolu znacznika wyboru Unicode (U + 2713).

Tej metody należy używać tylko z kontrolkami, których styl Button to BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Ta metoda inicjuje `mask` element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z flagą BCSIF_GLYPH, a następnie wysyła tę strukturę w komunikacie [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , który jest opisany w Windows SDK. Gdy funkcja Message zwraca, ta metoda pobiera symbol z `himlGlyph` elementu członkowskiego struktury.

##  <a name="getsplitimagelist"></a>CButton:: GetSplitImageList

Pobiera [listę obrazów](../../mfc/reference/cimagelist-class.md) dla kontrolki bieżącego przycisku podziału.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [Korzystanie CImageList](../../mfc/reference/cimagelist-class.md) .

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko z kontrolkami, których styl Button to BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Ta metoda inicjuje `mask` element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z flagą BCSIF_IMAGE, a następnie wysyła tę strukturę w komunikacie [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , który jest opisany w Windows SDK. Gdy funkcja Message zwraca, ta metoda pobiera listę obrazów ze `himlGlyph` składowej struktury.

##  <a name="getsplitinfo"></a>CButton:: GetSplitInfo

Pobiera parametry, które określają, jak system Windows rysuje bieżącą kontrolkę przycisku podziału.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pInfo*|określoną Wskaźnik do struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) , która otrzymuje informacje o bieżącym formancie przycisku podziału. Obiekt wywołujący jest odpowiedzialny za przydzielanie struktury.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko z kontrolkami, których styl Button to BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Ta metoda wysyła komunikat [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , który jest opisany w Windows SDK.

##  <a name="getsplitsize"></a>CButton:: GetSplitSize

Pobiera prostokąt ograniczenia składnika listy rozwijanej bieżącego formantu przycisku podziału.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pSize*|określoną Wskaźnik do struktury [rozmiaru](/windows/win32/api/windef/ns-windef-size) , która otrzymuje opis prostokąta.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko z kontrolkami, których styl Button to BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Gdy kontrolka przycisku podziału jest rozwinięta, może wyświetlić składnik listy rozwijanej, taki jak kontrolka listy lub kontrolka stronicowania. Ta metoda pobiera prostokąt ograniczający, który zawiera składnik listy rozwijanej.

Ta metoda inicjuje `mask` element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z flagą BCSIF_SIZE, a następnie wysyła tę strukturę w komunikacie [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , który jest opisany w Windows SDK. Gdy funkcja Message zwraca, ta metoda pobiera prostokąt ograniczenia z `size` elementu członkowskiego struktury.

##  <a name="getsplitstyle"></a>CButton:: getsplit

Pobiera style przycisku podziału definiujące bieżącą kontrolkę przycisku podziału.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Bitowa kombinacja stylów przycisku podziału. Aby uzyskać więcej informacji, zobacz `uSplitStyle` element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko z kontrolkami, których styl Button to BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Style przycisku podziału określają wyrównanie, współczynnik proporcji i format graficzny, za pomocą którego system Windows rysuje ikonę przycisku podziału.

Ta metoda inicjuje `mask` element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z flagą BCSIF_STYLE, a następnie wysyła tę strukturę w komunikacie [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , który jest opisany w Windows SDK. Gdy funkcja Message zwraca, ta metoda pobiera style przycisku podziału z `uSplitStyle` elementu członkowskiego struktury.

##  <a name="getstate"></a>CButton:: GetState

Pobiera stan kontrolki przycisku.

```
UINT GetState() const;
```

### <a name="return-value"></a>Wartość zwracana

Pole bitowe, które zawiera kombinację wartości wskazujących bieżący stan kontrolki przycisku. Poniższa tabela zawiera listę możliwych wartości.

|Stan przycisku|Wartość|Opis|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|Stan początkowy.|
|BST_CHECKED|0x0001|Kontrolka przycisku jest zaznaczona.|
|BST_INDETERMINATE|0x0002|Stan jest nieokreślony (możliwe jest tylko, gdy kontrolka przycisku ma trzy Stany).|
|BST_PUSHED|0x0004|Kontrolka przycisku zostanie naciśnięty.|
|BST_FOCUS|0x0008|Kontrolka przycisku ma fokus.|

### <a name="remarks"></a>Uwagi

Kontrolka przycisku ze stylem przycisku BS_3STATE lub BS_AUTO3STATE powoduje utworzenie pola wyboru, które ma trzeci stan o nazwie nieokreślony stan. Nieokreślony stan wskazuje, że pole wyboru nie jest zaznaczone ani niezaznaczone.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="gettextmargin"></a>CButton:: GetTextMargin

Wywołaj tę metodę, aby uzyskać margines `CButton` tekstu obiektu.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parametry

*pmargin*<br/>
Wskaźnik do marginesu `CButton` tekstu obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca margines tekstu.

### <a name="remarks"></a>Uwagi

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność komunikatu BCM_GETTEXTMARGIN, zgodnie z opisem w sekcji [przyciski](/windows/win32/controls/buttons) Windows SDK.

##  <a name="setbitmap"></a>CButton:: setmap

Wywołaj tę funkcję elementu członkowskiego, aby skojarzyć nową mapę bitową z przyciskiem.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Uchwyt mapy bitowej.

### <a name="return-value"></a>Wartość zwracana

Dojście mapy bitowej wcześniej skojarzonej z przyciskiem.

### <a name="remarks"></a>Uwagi

Mapa bitowa zostanie automatycznie umieszczona na stronie przycisku, domyślnie wyśrodkowana. Jeśli mapa bitowa jest zbyt duża dla przycisku, zostanie obcięta po obu stronach. Można wybrać inne opcje wyrównania, w tym następujące:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

W przeciwieństwie do [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), który używa czterech map bitowych na `SetBitmap` przycisk, używa tylko jednej mapy bitowej na przycisku. Po naciśnięciu przycisku Mapa bitowa zostanie przesunięta w dół i w prawo.

Użytkownik jest odpowiedzialny za zwolnienie mapy bitowej po jej zakończeniu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="setbuttonstyle"></a>CButton:: SetButton

Zmienia styl przycisku.

```
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
Określa [styl przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*bRedraw*<br/>
Określa, czy przycisk ma być narysowany ponownie. Wartość różna od zera ponownie narysuje przycisk. Wartość 0 nie powoduje ponownego rysowania przycisku. Przycisk jest ponownie rysowany domyślnie.

### <a name="remarks"></a>Uwagi

Użyj funkcji `GetButtonStyle` członkowskiej, aby pobrać styl przycisku. Word, który ma niski priorytet, jest stylem dla przycisku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="setcheck"></a>CButton:: SetCheck

Ustawia lub resetuje stan zaznaczenia przycisku radiowego lub pola wyboru.

```
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parametry

*nSprawdź*<br/>
Określa stan zaznaczenia. Ten parametr może mieć jedną z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|BST_UNCHECKED|Ustaw stan przycisku na niezaznaczone.|
|BST_CHECKED|Ustaw stan przycisku na zaznaczone.|
|BST_INDETERMINATE|Ustaw stan przycisku na nieokreślony. Ta wartość może być używana tylko wtedy, gdy przycisk ma styl BS_3STATE lub BS_AUTO3STATE.|

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nie ma wpływu na przycisk.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="setcursor"></a>CButton:: SetCursor

Wywołaj tę funkcję elementu członkowskiego, aby skojarzyć nowy kursor z przyciskiem.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parametry

*hCursor*<br/>
Uchwyt kursora.

### <a name="return-value"></a>Wartość zwracana

Uchwyt kursora wcześniej skojarzony z przyciskiem.

### <a name="remarks"></a>Uwagi

Kursor zostanie automatycznie umieszczony na stronie przycisku, domyślnie wyorodkowany. Jeśli kursor jest zbyt duży dla przycisku, zostanie obcięty po obu stronach. Można wybrać inne opcje wyrównania, w tym następujące:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

W przeciwieństwie do [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), który używa czterech map bitowych na `SetCursor` przycisk, używa tylko jednego kursora na przycisku. Gdy przycisk zostanie naciśnięty, kursor zostanie wyświetlony w dół i w prawo.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="setdropdownstate"></a>CButton:: SetDropDownState

Ustawia stan listy rozwijanej bieżącego formantu przycisku podziału.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*fDropDown*|podczas Wartość TRUE powoduje ustawienie stanu BST_DROPDOWNPUSHED; w przeciwnym razie FALSE.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Kontrolka przycisku dzielonego ma styl BS_SPLITBUTTON lub BS_DEFSPLITBUTTON i składa się z przycisku i strzałki listy rozwijanej z prawej strony. Aby uzyskać więcej informacji, zobacz [style przycisków](/windows/win32/Controls/button-styles). Zazwyczaj stan listy rozwijanej jest ustawiany, gdy użytkownik kliknie strzałkę listy rozwijanej. Użyj tej metody, aby programowo ustawić stan listy rozwijanej formantu. Strzałka listy rozwijanej jest rysowana w celu wskazania stanu.

Ta metoda wysyła komunikat [BCM_SETDROPDOWNSTATE](/windows/win32/Controls/bcm-setdropdownstate) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną, *m_splitButton*, która jest używana do programistycznego dostępu do kontrolki przycisku podziału. Ta zmienna jest używana w poniższym przykładzie.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia stan kontrolki przycisku podziału, aby wskazać, że strzałka listy rozwijanej jest wypchnięcia.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

##  <a name="setelevationrequired"></a>CButton:: SetElevationRequired

Ustawia stan bieżącej kontrolki przycisku na `elevation required`, która jest niezbędna, aby formant wyświetlał ikonę zabezpieczeń z podwyższonym poziomem uprawnień.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*fElevationRequired*|podczas Wartość true powoduje `elevation required` ustawienie stanu; w przeciwnym razie, FAŁSZ.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli przycisk lub kontrolka łącza polecenia wymaga podwyższonego poziomu uprawnień zabezpieczeń do wykonania akcji, ustaw kontrolkę `elevation required` na wartość stan. Następnie w systemie Windows zostanie wyświetlona ikona osłona kontroli konta użytkownika (UAC) na kontrolce. Aby uzyskać więcej informacji, zobacz "Kontrola konta użytkownika" w [witrynie MSDN](https://go.microsoft.com/fwlink/p/?linkid=18507).

Ta metoda wysyła komunikat [BCM_SETSHIELD](/windows/win32/Controls/bcm-setshield) , który jest opisany w Windows SDK.

##  <a name="seticon"></a>CButton:: SetIcon

Wywołaj tę funkcję elementu członkowskiego, aby skojarzyć nową ikonę z przyciskiem.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parametry

*hIcon*<br/>
Uchwyt ikony.

### <a name="return-value"></a>Wartość zwracana

Uchwyt ikony, która została wcześniej skojarzona z przyciskiem.

### <a name="remarks"></a>Uwagi

Ikona zostanie automatycznie umieszczona na stronie przycisku, domyślnie wyśrodkowana. Jeśli ikona jest za duża dla przycisku, zostanie obcięta po obu stronach. Można wybrać inne opcje wyrównania, w tym następujące:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

W przeciwieństwie do [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), która używa czterech map bitowych na `SetIcon` przycisk, używa tylko jednej ikony na przycisku. Po naciśnięciu przycisku zostanie wyświetlona ikona przesunięcia w dół i w prawo.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="setimagelist"></a>CButton:: SetImageList

Wywołaj tę metodę, aby ustawić listę `CButton` obrazów obiektu.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parametry

*pbuttonImagelist*<br/>
Wskaźnik do nowej listy obrazów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność komunikatu BCM_SETIMAGELIST, zgodnie z opisem w sekcji [przyciski](/windows/win32/controls/buttons) Windows SDK.

##  <a name="setnote"></a>CButton:: SetNote

Ustawia tekst notatki dla bieżącej kontrolki łącza polecenia.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*lpszNote*|podczas Wskaźnik na ciąg Unicode, który jest ustawiany jako tekst komentarza dla kontrolki łącza polecenia.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko z kontrolkami, których styl Button to BS_COMMANDLINK lub BS_DEFCOMMANDLINK.

Ta metoda wysyła komunikat [BCM_SETNOTE](/windows/win32/Controls/bcm-setnote) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną, *m_cmdLink*, która jest używana do programistycznego dostępu do formantu łącza polecenia. Ta zmienna jest używana w poniższym przykładzie.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia tekst notatki dla kontrolki łącza polecenia.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

##  <a name="setsplitglyph"></a>CButton:: SetSplitGlyph

Kojarzy określony glif z bieżącą kontrolką przycisku podziału.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*chGlyph*|podczas Znak określający symbol, który ma być używany jako przycisk podziału strzałki rozwijanej.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko z kontrolkami, które mają styl Button BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Symbol jest fizyczną reprezentacją znaku w określonej czcionce. Parametr *chGlyph* nie jest używany jako symbol, ale zamiast tego jest używany do wybierania symbolu z zestawu symboli zdefiniowanych przez system. Domyślny symbol strzałki listy rozwijanej jest określany przez znak "6" i przypomina czarny znak w dół w dół (U + 25BC).

Ta metoda inicjuje `mask` składową struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z `himlGlyph` flagą BCSIF_GLYPH i składową z parametrem *chGlyph* , a następnie wysyła tę strukturę w wiadomości [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) jest to opisane w Windows SDK.

##  <a name="setsplitimagelist"></a>CButton:: SetSplitImageList

Kojarzy [listę obrazów](../../mfc/reference/cimagelist-class.md) z bieżącym formantem przycisku podziału.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pSplitImageList*|podczas Wskaźnik do obiektu [Korzystanie CImageList](../../mfc/reference/cimagelist-class.md) , który ma zostać przypisany do bieżącej kontrolki przycisku podziału.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko z kontrolkami, których styl Button to BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Ta metoda inicjuje `mask` składową struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z `himlGlyph` flagą BCSIF_IMAGE i składową z parametrem *pSplitImageList* , a następnie wysyła tę strukturę w [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) komunikat opisany w Windows SDK.

##  <a name="setsplitinfo"></a>CButton:: SetSplitInfo

Określa parametry, które określają, jak system Windows rysuje bieżącą kontrolkę przycisku podziału.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pInfo*|podczas Wskaźnik do struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) , która definiuje bieżącą kontrolkę przycisku podziału.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko z kontrolkami, których styl Button to BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Ta metoda wysyła komunikat [BCM_SETSPLITINFO](/windows/win32/Controls/bcm-setsplitinfo) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną, `m_splitButton`, która jest używana do programistycznego dostępu do kontrolki przycisku podziału.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu zmienia symbol, który jest używany dla przycisku podziału strzałki rozwijanej. W przykładzie zastępują glify trójkątne w górę dla domyślnego glifu trójkąta wskazującego w dół. Wyświetlany symbol zależy od znaku określonego w `himlGlyph` elemencie członkowskim `BUTTON_SPLITINFO` struktury. Glif z trójkątem wskazującym w dół jest określany przez znak "6", a glif z trójkątem wskazującym w górę jest określany przez znak "5". Aby uzyskać porównanie, zobacz wygodną metodę [CButton:: SetSplitGlyph](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

##  <a name="setsplitsize"></a>CButton:: SetSplitSize

Ustawia prostokąt ograniczenia składnika listy rozwijanej bieżącego formantu przycisku podziału.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pSize*|podczas Wskaźnik na strukturę [rozmiaru](/windows/win32/api/windef/ns-windef-size) opisującą prostokąt ograniczający.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko z kontrolkami, których styl Button to BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Gdy kontrolka przycisku podziału jest rozwinięta, może wyświetlić składnik listy rozwijanej, taki jak kontrolka listy lub kontrolka stronicowania. Ta metoda określa rozmiar prostokąta granicznego, który zawiera składnik listy rozwijanej.

Ta metoda inicjuje `mask` składową struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z `size` flagą BCSIF_SIZE i składową z parametrem *psize* , a następnie wysyła tę strukturę w komunikacie [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , który został opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną, `m_splitButton`, która jest używana do programistycznego dostępu do kontrolki przycisku podziału. Ta zmienna jest używana w poniższym przykładzie.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu podwaja rozmiar rozwijanej strzałki przycisku podziału.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

##  <a name="setsplitstyle"></a>CButton:: setsplit

Ustawia styl bieżącej kontrolki przycisku podziału.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*uSplitStyle*|podczas Bitowa kombinacja stylów przycisku podziału. Aby uzyskać więcej informacji, zobacz `uSplitStyle` element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko z kontrolkami, których styl Button to BS_SPLITBUTTON lub BS_DEFSPLITBUTTON.

Style przycisku podziału określają wyrównanie, współczynnik proporcji i format graficzny, za pomocą którego system Windows rysuje ikonę przycisku podziału. Aby uzyskać więcej informacji, zobacz `uSplitStyle` element członkowski struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .

Ta metoda inicjuje `mask` składową struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) z `uSplitStyle` flagą BCSIF_STYLE i składową z parametrem *uSplitStyle* , a następnie wysyła tę strukturę w [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) komunikat opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną, `m_splitButton`, która jest używana do programistycznego dostępu do kontrolki przycisku podziału.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia styl strzałki rozwijanej przycisku podziału. Styl BCSS_ALIGNLEFT wyświetla strzałkę po lewej stronie przycisku, a styl BCSS_STRETCH zachowuje proporcje strzałki listy rozwijanej po zmianie rozmiaru przycisku.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

##  <a name="setstate"></a>CButton:: setstate

Określa, czy kontrolka przycisku jest wyróżniona, czy nie.

```
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Parametry

*bHighlight*<br/>
Określa, czy przycisk ma być wyróżniony. Wartość niezerowa powoduje wyróżnienie przycisku; wartość 0 usuwa wszystkie wyróżnienia.

### <a name="remarks"></a>Uwagi

Wyróżnianie ma wpływ na zewnętrzną kontrolkę Button. Nie ma ono wpływu na stan zaznaczenia przycisku radiowego lub pola wyboru.

Kontrolka przycisku jest automatycznie podświetlana, gdy użytkownik kliknie i zatrzyma lewy przycisk myszy. Wyróżnienie zostanie usunięte, gdy użytkownik zwolni przycisk myszy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="settextmargin"></a>CButton:: SetTextMargin

Wywołaj tę metodę, aby ustawić margines `CButton` tekstu obiektu.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parametry

*pmargin*<br/>
Wskaźnik do nowego marginesu tekstu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność komunikatu BCM_SETTEXTMARGIN, zgodnie z opisem w sekcji [przyciski](/windows/win32/controls/buttons) Windows SDK.

## <a name="see-also"></a>Zobacz także

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
