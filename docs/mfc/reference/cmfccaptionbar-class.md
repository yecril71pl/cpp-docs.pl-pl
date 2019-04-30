---
title: Klasa CMFCCaptionBar
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
ms.openlocfilehash: c6385cb6bd3eec3ce5fefe0475d771c774777820
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403844"
---
# <a name="cmfccaptionbar-class"></a>Klasa CMFCCaptionBar

A `CMFCCaptionBar` obiekt jest pasek sterowania, który może wyświetlać trzy elementy: przycisk, etykietę tekstową i mapę bitową. Umożliwia wyświetlanie tylko jednego elementu każdego typu w danym momencie. Możesz wyrównać każdy element do lewej lub prawej krawędzi formantu lub do środka. Można również zastosować płaski lub 3-wymiarowy styl do górnej i dolnej krawędzi pasek podpisu.

## <a name="syntax"></a>Składnia

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCCaptionBar::Create](#create)|Tworzy kontrolkę paska podpisu i dołącza je do `CMFCCaptionBar` obiektu.|
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Wskazuje, czy innego okienka można dynamicznie wstawione między pasek podpisu i jej nadrzędnej ramki. (Przesłania [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCCaptionBar::EnableButton](#enablebutton)|Włącza lub wyłącza przycisk na pasku podpisu.|
|[CMFCCaptionBar::GetAlignment](#getalignment)|Zwraca wyrównanie określony element.|
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|Zwraca rozmiar obramowania paska podpisu.|
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|Pobiera prostokąt otaczający przycisk na pasku podpisu.|
|[CMFCCaptionBar::GetMargin](#getmargin)|Zwraca odległość między krawędzi elementów paska podpisu krawędzią formantu paska podpisu.|
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|Określa, czy pasek podpisu jest w trybie pasek komunikatów.|
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|Usuwa obraz mapy bitowej z pasek podpisu.|
|[CMFCCaptionBar::RemoveButton](#removebutton)|Usuwa przycisk na pasku podpisu.|
|[CMFCCaptionBar::RemoveIcon](#removeicon)|Usuwa ikonę na pasku podpisu.|
|[CMFCCaptionBar::RemoveText](#removetext)|Usuwa etykietę tekstową z pasek podpisu.|
|[CMFCCaptionBar::SetBitmap](#setbitmap)|Ustawia obraz mapy bitowej dla pasek podpisu.|
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|Ustawia rozmiar obramowania paska podpisu.|
|[CMFCCaptionBar::SetButton](#setbutton)|Ustawia przycisk na pasku podpisu.|
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|Określa, czy przycisk pozostaje po naciśnięciu.|
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|Ustawia etykietkę narzędzia dla przycisku.|
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|Ustawia styl obramowania paska podpisu.|
|[CMFCCaptionBar::SetIcon](#seticon)|Ustawia ikonę pasek podpisu.|
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|Ustawia etykietkę narzędzia dla obrazu pasek podpisu.|
|[CMFCCaptionBar::SetMargin](#setmargin)|Ustawia odległość między krawędzią elementu pasek podpisu krawędzią formantu paska podpisu.|
|[CMFCCaptionBar::SetText](#settext)|Określa tekst etykiety dla pasek podpisu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|Metoda wywoływana przez platformę, by wypełnienia tła paska podpisu.|
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|Metoda wywoływana przez platformę, by narysować obramowanie pasek podpisu.|
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|Metoda wywoływana przez platformę, by narysować przycisk paska podpisu.|
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|Metoda wywoływana przez platformę, by narysować obraz paska podpisu.|
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|Metoda wywoływana przez platformę, by narysować tekst pasek podpisu.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|Kolor tła paska podpisu.|
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|Kolor obramowania paska podpisu.|
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|Kolor tekstu pasek podpisu.|

## <a name="remarks"></a>Uwagi

Aby utworzyć pasek podpisu, wykonaj następujące kroki:

1. Konstruowania `CMFCCaptionBar` obiektu. Zazwyczaj należy dodać pasek podpisu na klasę okna ramowego.

1. Wywołaj [CMFCCaptionBar::Create](#create) metodę, aby utworzyć kontrolkę paska podpisu i dołączyć go do `CMFCCaptionBar` obiektu.

1. Wywołaj [CMFCCaptionBar::SetButton](#setbutton), [CMFCCaptionBar::SetText](#settext), [CMFCCaptionBar::SetIcon](#seticon), i [CMFCCaptionBar::SetBitmap](#setbitmap)można ustawić elementów paska podpisu.

Po ustawieniu button element, należy przypisać identyfikator polecenia do przycisku. Gdy użytkownik kliknie przycisk, pasek podpisu kieruje wm_command — komunikaty, które mają ten identyfikator do nadrzędnej ramki okna.

Pasek podpisu mogą również działać w trybie pasek wiadomości, która emuluje pasek komunikatów, która pojawia się w aplikacjach pakietu Office 2007. W trybie pasek komunikatów pasek podpisu Wyświetla mapę bitową, wiadomości i przycisk umożliwiający (zwykle powoduje otwarcie okna dialogowego.) Etykietka narzędzia można przypisać do mapy bitowej.

Aby włączyć tryb pasek komunikatów, należy wywołać [CMFCCaptionBar::Create](#create) i ustaw czwarty parametr (bIsMessageBarMode) na wartość TRUE.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCCaptionBar` klasy. W przykładzie pokazano, jak utworzyć formant paska podpisu, ustawianie obramowanie 3D paska podpisu, określ odległość w pikselach, między krawędzi podpis paska elementy krawędzią formantu paska podpisu, skonfigurować przycisk na pasku podpisu , ustawić etykietkę narzędzia dla przycisku, Ustaw tekst etykiety dla pasek podpisu, Ustaw obraz mapy bitowej dla pasek podpisu i ustawić etykietkę narzędzia dla obrazu w pasek podpisu. Ten fragment kodu jest częścią [próbka MS Office 2007 Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcaptionbar.h

##  <a name="create"></a>  CMFCCaptionBar::Create

Tworzy kontrolkę paska podpisu i dołącza je do `CMFCCaptionBar` obiektu.

```
BOOL Create(
    DWORD dwStyle,
    CWnd* pParentWnd,
    UINT uID,
    int nHeight=-1,
    BOOL bIsMessageBarMode=FALSE);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Logiczne OR kombinacja Style paska podpisu.

*pParentWnd*<br/>
Okno nadrzędne kontrolki paska podpisu.

*uID*<br/>
Identyfikator formantu paska podpisu.

*nHeight*<br/>
Wysokość w pikselach formantu paska podpisu. Jeśli jest to wartość -1, wysokość jest obliczana wysokość ikony, tekst i przycisk, który wyświetla kontrolkę paska podpisu.

*bIsMessageBarMode*<br/>
Wartość TRUE, jeśli pasek podpisu jest w trybie pasek wiadomości; Wartość FALSE w przeciwnym razie.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli formantu paska podpisu został utworzony pomyślnie; Wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Konstruowanie `CMFCCaptionBar` obiektu w dwóch krokach. Pierwsze wywołanie konstruktora, a następnie wywołać `Create` metody, która tworzy formant Windows i dołącza je do `CMFCCaptionBar` obiektu.

##  <a name="doesallowdyninsertbefore"></a>  CMFCCaptionBar::DoesAllowDynInsertBefore

Wskazuje, czy innego okienka można dynamicznie wstawione między pasek podpisu i jej nadrzędnej ramki.

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość FALSE, jeśli zastąpiona.

### <a name="remarks"></a>Uwagi

##  <a name="enablebutton"></a>  CMFCCaptionBar::EnableButton

Włącza lub wyłącza przycisk na pasku podpisu.

```
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Wartość TRUE powoduje włączenie przycisku wartości FALSE spowoduje wyłączenie przycisku.

##  <a name="getalignment"></a>  CMFCCaptionBar::GetAlignment

Zwraca wyrównanie określony element.

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>Parametry

*elem*<br/>
[in] Element paska podpisu dla której mają zostać pobrane wyrównania.

### <a name="return-value"></a>Wartość zwracana

Wyrównanie elementu, takiego jak przycisk, mapy bitowej, tekst lub ikony.

### <a name="remarks"></a>Uwagi

Wyrównanie elementu może być jednym z następujących wartości:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="getbordersize"></a>  CMFCCaptionBar::GetBorderSize

Zwraca rozmiar obramowania paska podpisu.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar w pikselach, obramowania.

##  <a name="getbuttonrect"></a>  CMFCCaptionBar::GetButtonRect

Pobiera prostokąt otaczający przycisk na pasku podpisu.

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>Wartość zwracana

A `CRect` obiekt, który zawiera współrzędne prostokąt otaczający przycisk na pasku podpisu.

##  <a name="getmargin"></a>  CMFCCaptionBar::GetMargin

Zwraca odległość między krawędzi elementów paska podpisu krawędzią formantu paska podpisu.

```
int GetMargin() const;
```

### <a name="return-value"></a>Wartość zwracana

Odległość w pikselach, między krawędzi elementów paska podpisu krawędzią formantu paska podpisu.

##  <a name="ismessagebarmode"></a>  CMFCCaptionBar::IsMessageBarMode

Określa, czy pasek podpisu jest w trybie pasek komunikatów.

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pasek podpisu jest w trybie pasek wiadomości; Wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

W trybie pasek komunikatów pasek podpisu Wyświetla obraz z etykietki narzędzia, tekst komunikatu i przycisku.

##  <a name="m_clrbarbackground"></a>  CMFCCaptionBar::m_clrBarBackground

Kolor tła paska podpisu.

```
COLORREF m_clrBarBackground
```

##  <a name="m_clrbarborder"></a>  CMFCCaptionBar::m_clrBarBorder

Kolor obramowania paska podpisu.

```
COLORREF m_clrBarBorder
```

##  <a name="m_clrbartext"></a>  CMFCCaptionBar::m_clrBarText

Kolor tekstu pasek podpisu.

```
COLORREF m_clrBarText
```

##  <a name="ondrawbackground"></a>  CMFCCaptionBar::OnDrawBackground

Metoda wywoływana przez platformę, by wypełnienia tła paska podpisu.

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia paska podpisu.

*Rect*<br/>
[in] Prostokąt otaczający do wypełnienia.

### <a name="remarks"></a>Uwagi

`OnDrawBackground` Metoda jest wywoływana, gdy tło paska podpis ma być wypełnione. Domyślna implementacja wypełnienia tła przy użyciu [CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground) kolorów.

Należy przesłonić tę metodę w `CMFCCaptionBar` klasy, aby dostosować wygląd paska podpisu.

##  <a name="ondrawborder"></a>  CMFCCaptionBar::OnDrawBorder

Metoda wywoływana przez platformę, by narysować obramowanie pasek podpisu.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Kontekst urządzenia, która jest używana do wyświetlania obramowania.

*Rect*<br/>
[in] Prostokąt otaczający.

### <a name="remarks"></a>Uwagi

Domyślnie obramowanie mają płaski.

Należy przesłonić tę metodę w `CMFCCaptionBar` klasy, aby dostosować wygląd obramowania paska podpisu.

##  <a name="ondrawbutton"></a>  CMFCCaptionBar::OnDrawButton

Metoda wywoływana przez platformę, by narysować przycisk paska podpisu.

```
virtual void OnDrawButton(
    CDC* pDC,
    CRect rect,
    const CString& strButton,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia, które służy do wyświetlania przycisku.

*Rect*<br/>
[in] Prostokąt otaczający przycisku.

*strButton*<br/>
[in] Etykieta tekstowa przycisku.

*bWłączony*<br/>
[in] Wartość TRUE, jeśli ten przycisk jest włączony; Wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w `CMFCCaptionBar` klasy do dostosowywania wyglądu przycisku paska podpisu.

##  <a name="ondrawimage"></a>  CMFCCaptionBar::OnDrawImage

Metoda wywoływana przez platformę, by narysować obraz paska podpisu.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia, które służy do wyświetlania obrazu.

*Rect*<br/>
[in] Określa prostokąt otaczający obrazu.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w `CMFCCaptionBar` klasy, aby dostosować wygląd obrazu.

##  <a name="ondrawtext"></a>  CMFCCaptionBar::OnDrawText

Metoda wywoływana przez platformę, by narysować tekst pasek podpisu.

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia, które służy do wyświetlania przycisku.

*Rect*<br/>
[in] Prostokąt otaczający tekstu.

*strText*<br/>
[in] Ciąg tekstowy do wyświetlenia.

### <a name="remarks"></a>Uwagi

Domyślna implementacja służy do wyświetlania tekstu przy użyciu `CDC::DrawText` i [CMFCCaptionBar::m_clrBarText](#m_clrbartext) kolorów.

Należy przesłonić tę metodę w `CMFCCaptionBar` klasy, aby dostosować wygląd tekstu pasek podpisu.

##  <a name="removebitmap"></a>  CMFCCaptionBar::RemoveBitmap

Usuwa obraz mapy bitowej z pasek podpisu.

```
void RemoveBitmap();
```

##  <a name="removebutton"></a>  CMFCCaptionBar::RemoveButton

Usuwa przycisk na pasku podpisu.

```
void RemoveButton();
```

### <a name="remarks"></a>Uwagi

Układ elementów paska podpisu zostaną automatycznie dopasowane.

##  <a name="removeicon"></a>  CMFCCaptionBar::RemoveIcon

Usuwa ikonę na pasku podpisu.

```
void RemoveIcon();
```

##  <a name="removetext"></a>  CMFCCaptionBar::RemoveText

Usuwa etykietę tekstową z pasek podpisu.

```
void RemoveText();
```

##  <a name="setbitmap"></a>  CMFCCaptionBar::SetBitmap

Ustawia obraz mapy bitowej dla pasek podpisu.

```
void SetBitmap(
    HBITMAP hBitmap,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

void SetBitmap(
    UINT uiBmpResID,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
[in] Dojście do mapy bitowej do ustawienia.

*clrTransparent*<br/>
[in] Wartości RGB, który określa przezroczysty kolor mapy bitowej.

*bStretch*<br/>
[in] W przypadku opcji TRUE mapy bitowej jest rozciągany tak, jeśli nie mieści się w obrazie prostokąt ograniczający. W przeciwnym razie nie jest rozciągana mapy bitowej.

*bmpAlignment*<br/>
[in] Wyrównanie mapy bitowej.

### <a name="remarks"></a>Uwagi

Użyj tej metody można ustawić mapy bitowej na pasku podpisu.

Poprzednie mapy bitowej jest niszczony, automatycznie. Jeśli pasek podpisu Wyświetla ikony, ponieważ wywołana [CMFCCaptionBar::SetIcon](#seticon) metody, mapa bitowa nie będą wyświetlane, chyba że usuniesz ikonę przez wywołanie metody [CMFCCaptionBar::RemoveIcon](#removeicon).

Mapa bitowa jest wyrównany zgodnie z określonym *bmpAlignment* parametru.  Ten parametr może być jedną z następujących `BarElementAlignment` wartości:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="setbordersize"></a>  CMFCCaptionBar::SetBorderSize

Ustawia rozmiar obramowania paska podpisu.

```
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
[in] Nowy rozmiar w pikselach, obramowania paska podpisu.

##  <a name="setbutton"></a>  CMFCCaptionBar::SetButton

Ustawia przycisk na pasku podpisu.

```
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
Etykieta polecenia przycisku.

*uiCmdUI*<br/>
Identyfikator przycisku polecenia.

*btnAlignmnet*<br/>
Wyrównanie przycisku.

*bHasDropDownArrow*<br/>
Wartość TRUE, jeśli przycisk powoduje wyświetlenie strzałkę listy rozwijanej, wartość FALSE w przeciwnym razie.

##  <a name="setbuttonpressed"></a>  CMFCCaptionBar::SetButtonPressed

Określa, czy przycisk pozostaje po naciśnięciu.

```
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>Parametry

*bPresed*<br/>
Wartość TRUE, jeśli przycisk śledzi stan naciśnięcia, wartość FALSE w przeciwnym razie.

##  <a name="setbuttontooltip"></a>  CMFCCaptionBar::SetButtonToolTip

Ustawia etykietkę narzędzia dla przycisku.

```
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Parametry

*lpszToolTip*<br/>
[in] W etykiecie.

*lpszDescription*<br/>
[in] Opis etykietki narzędzia.

##  <a name="setflatborder"></a>  CMFCCaptionBar::SetFlatBorder

Ustawia styl obramowania paska podpisu.

```
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Parametry

*bFlat*<br/>
[in] Wartość TRUE, jeśli obramowania paska podpisu jest płaska. Wartość FALSE, jeśli obramowanie 3D.

##  <a name="seticon"></a>  CMFCCaptionBar::SetIcon

Ustawia ikonę pasek podpisu.

```
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parametry

*hIcon*<br/>
[in] Dojście do ikony, aby ustawić.

*iconAlignment*<br/>
[in] Wyrównanie ikony.

### <a name="remarks"></a>Uwagi

Paski podpis może wyświetlać ikony lub mapy bitowej. Zobacz [CMFCCaptionBar::SetBitmap](#setbitmap) Aby dowiedzieć się, jak wyświetlać mapę bitową. Jeśli ustawisz zarówno ikony, jak i mapy bitowej, jest zawsze wyświetlana jako ikona. Wywołaj [CMFCCaptionBar::RemoveIcon](#removeicon) usuwanie ikony paska podpisu.

Ikona jest wyrównany zgodnie z opisem w *iconAlignment* parametru. Może to być jedna z następujących `BarElementAlignment` wartości:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="setimagetooltip"></a>  CMFCCaptionBar::SetImageToolTip

Ustawia etykietkę narzędzia dla obrazu w pasek podpisu.

```
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Parametry

*lpszToolTip*<br/>
[in] Tekst etykietki narzędzia.

*lpszDescription*<br/>
[in] Opis etykietki narzędzia.

##  <a name="setmargin"></a>  CMFCCaptionBar::SetMargin

Ustawia odległość między krawędzią elementu pasek podpisu krawędzią formantu paska podpisu.

```
void SetMargin(int nMargin);
```

### <a name="parameters"></a>Parametry

*nMargin*<br/>
[in] Odległość w pikselach, między krawędzi elementów paska podpisu krawędzią formantu paska podpisu.

##  <a name="settext"></a>  CMFCCaptionBar::SetText

Określa tekst etykiety dla pasek podpisu.

```
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parametry

*strText*<br/>
[in] Ciąg tekstowy, który można ustawić.

*TextAlignment to*<br/>
[in] Wyrównanie tekstu.

### <a name="remarks"></a>Uwagi

Etykieta tekstowa jest wyrównany zgodnie z określonym *TextAlignment to* parametru. Może to być jedna z następujących `BarElementAlignment` wartości:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
