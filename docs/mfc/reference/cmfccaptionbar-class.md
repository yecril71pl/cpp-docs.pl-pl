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
ms.openlocfilehash: c42b1ccb51a3c290e0887717d900543b8d5b277a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752629"
---
# <a name="cmfccaptionbar-class"></a>Klasa CMFCCaptionBar

Obiekt `CMFCCaptionBar` to pasek sterowania, na który można wyświetlić trzy elementy: przycisk, etykietę tekstową i mapę bitową. Może wyświetlać tylko jeden element każdego typu naraz. Każdy element można wyrównać do lewej lub prawej krawędzi formantu lub do środka. Do górnej i dolnej krawędzi paska podpisu można również zastosować styl płaski lub 3D.

## <a name="syntax"></a>Składnia

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCCaptionBar::Tworzenie](#create)|Tworzy formant paska podpisu `CMFCCaptionBar` i dołącza go do obiektu.|
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Wskazuje, czy można dynamicznie wstawiać inne okienko między pasem podpisu a ramką nadrzędną. (Zastępuje [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCCaptionBar::EnableButton](#enablebutton)|Włącza lub wyłącza przycisk na pasku podpisów.|
|[CMFCCaptionBar::GetAlignment](#getalignment)|Zwraca wyrównanie określonego elementu.|
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|Zwraca rozmiar obramowania paska podpisu.|
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|Pobiera prostokąt ograniczający przycisku na pasku podpisu.|
|[CMFCCaptionBar::GetMargin](#getmargin)|Zwraca odległość między krawędzią elementów paska podpisu a krawędzią formantu paska podpisu.|
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|Określa, czy pasek podpisu znajduje się w trybie paska komunikatów.|
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|Usuwa obraz mapy bitowej z paska podpisu.|
|[CMFCCaptionBar::UsuńButton](#removebutton)|Usuwa przycisk z paska podpisu.|
|[CMFCCaptionBar::RemoveIcon](#removeicon)|Usuwa ikonę z paska podpisu.|
|[CMFCCaptionBar::Usuń Tekst](#removetext)|Usuwa etykietę tekstową z paska podpisu.|
|[CMFCCaptionBar::SetBitmap](#setbitmap)|Ustawia obraz bitmapowy dla paska podpisu.|
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|Ustawia rozmiar obramowania paska podpisu.|
|[CMFCCaptionBar::Przycisk seta](#setbutton)|Ustawia przycisk paska podpisu.|
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|Określa, czy przycisk pozostaje naciśnięty.|
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|Ustawia etykietkę narzędzia dla przycisku.|
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|Ustawia styl obramowania paska podpisu.|
|[CMFCCaptionBar::SetIcon](#seticon)|Ustawia ikonę paska podpisu.|
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|Ustawia etykietkę narzędzia dla paska podpisu.|
|[CMFCCaptionBar::SetMargin](#setmargin)|Ustawia odległość między krawędzią elementu paska podpisu a krawędzią formantu paska podpisu.|
|[CMFCCaptionBar::SetText](#settext)|Ustawia etykietę tekstową dla paska podpisu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|Wywoływana przez strukturę, aby wypełnić tło paska podpisu.|
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|Wywoływana przez ramy, aby narysować obramowanie paska podpisu.|
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|Wywoływane przez strukturę, aby narysować przycisk paska podpisu.|
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|Wywoływane przez strukturę, aby narysować obraz paska podpisu.|
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|Wywoływane przez strukturę, aby narysować tekst paska podpisu.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|Kolor tła paska podpisu.|
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|Kolor obramowania paska podpisu.|
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|Kolor tekstu paska podpisu.|

## <a name="remarks"></a>Uwagi

Aby utworzyć pasek podpisu, wykonaj następujące czynności:

1. Konstruuj `CMFCCaptionBar` obiekt. Zazwyczaj należy dodać pasek podpisu do klasy okna ramki.

1. Wywołanie [CMFCCaptionBar::Create](#create) metody, aby utworzyć formant `CMFCCaptionBar` paska podpisu i dołączyć go do obiektu.

1. Wywołanie [CMFCCaptionBar::SetButton](#setbutton), [CMFCCaptionBar::SetText](#settext), [CMFCCaptionBar::SetIcon](#seticon)i [CMFCCaptionBar::SetBitmap,](#setbitmap) aby ustawić elementy paska podpisu.

Po ustawieniu elementu przycisku należy przypisać identyfikator polecenia do przycisku. Gdy użytkownik kliknie przycisk, pasek podpisu kieruje WM_COMMAND wiadomości, które mają ten identyfikator, do nadrzędnego okna ramki.

Pasek podpisów może również działać w trybie paska komunikatów, który emuluje pasek komunikatów wyświetlany w aplikacjach pakietu Microsoft Office 2007. W trybie paska komunikatów na pasku podpisów jest wyświetlana mapa bitowa, komunikat i przycisk (który zazwyczaj otwiera okno dialogowe). Do mapy bitowej można przypisać etykietkę narzędzia.

Aby włączyć tryb paska komunikatów, zadzwoń do [CMFCCaptionBar::Create](#create) i ustaw czwarty parametr (bIsMessageBarMode) na TRUE.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCCaptionBar` używać różnych metod w klasie. W przykładzie pokazano, jak utworzyć kontrolkę paska podpisu, ustawić obramowanie 3D paska podpisu, ustawić odległość, w pikselach, między krawędzią elementów paska podpisu a krawędzią formantu paska podpisu, ustawić przycisk paska podpisu, ustawić etykietę narzędzia przycisku, ustawić etykietę tekstową dla paska podpisu, ustawić obraz bitmapowy dla paska podpisu i ustaw etykietkę narzędzia obrazu na pasku podpisu. Ten fragment kodu jest częścią [przykładu demo pakietu MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[Cmfccaptionbar](../../mfc/reference/cmfccaptionbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcaptionbar.h

## <a name="cmfccaptionbarcreate"></a><a name="create"></a>CMFCCaptionBar::Tworzenie

Tworzy formant paska podpisu `CMFCCaptionBar` i dołącza go do obiektu.

```
BOOL Create(
    DWORD dwStyle,
    CWnd* pParentWnd,
    UINT uID,
    int nHeight=-1,
    BOOL bIsMessageBarMode=FALSE);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Logiczna kombinacja stylów paska podpisu.

*pParentWnd*<br/>
Okno nadrzędne formantu paska podpisu.

*Uid*<br/>
Identyfikator formantu paska podpisu.

*nFeksja*<br/>
Wysokość w pikselach formantu paska podpisu. Jeśli jest to -1, wysokość jest obliczana zgodnie z wysokością ikony, tekstem i przyciskiem wyświetlanym przez formant paska podpisu.

*bIsMessageBarMode*<br/>
PRAWDA, jeśli pasek podpisu znajduje się w trybie paska komunikatów; FAŁSZ inaczej.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli formant paska podpisu został utworzony pomyślnie; FAŁSZ inaczej.

### <a name="remarks"></a>Uwagi

Konstruowanie `CMFCCaptionBar` obiektu w dwóch krokach. Najpierw wywołać konstruktora, a `Create` następnie wywołać metodę, która tworzy `CMFCCaptionBar` formant systemu Windows i dołącza go do obiektu.

## <a name="cmfccaptionbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCCaptionBar::DoesAllowDynInsertBefore

Wskazuje, czy można dynamicznie wstawiać inne okienko między pasem podpisu a ramką nadrzędną.

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość FAŁSZ, chyba że zostanie zastąpiona.

### <a name="remarks"></a>Uwagi

## <a name="cmfccaptionbarenablebutton"></a><a name="enablebutton"></a>CMFCCaptionBar::EnableButton

Włącza lub wyłącza przycisk na pasku podpisów.

```cpp
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] PRAWDA, aby włączyć przycisk, FALSE, aby wyłączyć przycisk.

## <a name="cmfccaptionbargetalignment"></a><a name="getalignment"></a>CMFCCaptionBar::GetAlignment

Zwraca wyrównanie określonego elementu.

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
[w] Element paska podpisu, dla którego ma być pobierana wyrównanie.

### <a name="return-value"></a>Wartość zwracana

Wyrównanie elementu, takiego jak przycisk, mapa bitowa, tekst lub ikona.

### <a name="remarks"></a>Uwagi

Wyrównanie elementu może być jedną z następujących wartości:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbargetbordersize"></a><a name="getbordersize"></a>CMFCCaptionBar::GetBorderSize

Zwraca rozmiar obramowania paska podpisu.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar obramowania w pikselach.

## <a name="cmfccaptionbargetbuttonrect"></a><a name="getbuttonrect"></a>CMFCCaptionBar::GetButtonRect

Pobiera prostokąt ograniczający przycisku na pasku podpisu.

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt, `CRect` który zawiera współrzędne prostokąta ograniczającego przycisku na pasku podpisu.

## <a name="cmfccaptionbargetmargin"></a><a name="getmargin"></a>CMFCCaptionBar::GetMargin

Zwraca odległość między krawędzią elementów paska podpisu a krawędzią formantu paska podpisu.

```
int GetMargin() const;
```

### <a name="return-value"></a>Wartość zwracana

Odległość w pikselach między krawędzią elementów paska podpisu a krawędzią formantu paska podpisu.

## <a name="cmfccaptionbarismessagebarmode"></a><a name="ismessagebarmode"></a>CMFCCaptionBar::IsMessageBarMode

Określa, czy pasek podpisu znajduje się w trybie paska komunikatów.

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli pasek podpisu znajduje się w trybie paska komunikatów; FAŁSZ inaczej.

### <a name="remarks"></a>Uwagi

W trybie paska komunikatów na pasku podpisów wyświetlany jest obraz z etykietką narzędzia, tekstem wiadomości i przyciskiem.

## <a name="cmfccaptionbarm_clrbarbackground"></a><a name="m_clrbarbackground"></a>CMFCCaptionBar::m_clrBarBackground

Kolor tła paska podpisu.

```
COLORREF m_clrBarBackground
```

## <a name="cmfccaptionbarm_clrbarborder"></a><a name="m_clrbarborder"></a>CMFCCaptionBar::m_clrBarBorder

Kolor obramowania paska podpisu.

```
COLORREF m_clrBarBorder
```

## <a name="cmfccaptionbarm_clrbartext"></a><a name="m_clrbartext"></a>CMFCCaptionBar::m_clrBarText

Kolor tekstu paska podpisu.

```
COLORREF m_clrBarText
```

## <a name="cmfccaptionbarondrawbackground"></a><a name="ondrawbackground"></a>CMFCCaptionBar::OnDrawBackground

Wywoływana przez strukturę, aby wypełnić tło paska podpisu.

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia paska podpisu.

*Rect*<br/>
[w] Prostokąt ograniczający do wypełnienia.

### <a name="remarks"></a>Uwagi

Metoda `OnDrawBackground` jest wywoływana, gdy tło paska podpisu ma zostać wypełnione. Domyślna implementacja wypełnia tło przy użyciu [CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground) kolor.

Zastąpi tę `CMFCCaptionBar` metodę w klasie pochodnej, aby dostosować wygląd paska podpisu.

## <a name="cmfccaptionbarondrawborder"></a><a name="ondrawborder"></a>CMFCCaptionBar::OnDrawBorder

Wywoływana przez ramy, aby narysować obramowanie paska podpisu.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Kontekst urządzenia, który jest używany do wyświetlania obramowań.

*Rect*<br/>
[w] Prostokąt ograniczający.

### <a name="remarks"></a>Uwagi

Domyślnie obramowania mają styl płaski.

Zastąpi tę `CMFCCaptionBar` metodę w klasie pochodnej, aby dostosować wygląd obramowań paska podpisu.

## <a name="cmfccaptionbarondrawbutton"></a><a name="ondrawbutton"></a>CMFCCaptionBar::OnDrawButton

Wywoływane przez strukturę, aby narysować przycisk paska podpisu.

```
virtual void OnDrawButton(
    CDC* pDC,
    CRect rect,
    const CString& strButton,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia, który jest używany do wyświetlania przycisku.

*Rect*<br/>
[w] Prostokąt ograniczający przycisku.

*strButton (przycisk strButton)*<br/>
[w] Etykieta tekstowa przycisku.

*bWłach*<br/>
[w] PRAWDA, jeśli przycisk jest włączony; FAŁSZ inaczej.

### <a name="remarks"></a>Uwagi

Zastąp tę `CMFCCaptionBar` metodę w klasie pochodnej, aby dostosować wygląd przycisku paska podpisu.

## <a name="cmfccaptionbarondrawimage"></a><a name="ondrawimage"></a>CMFCCaptionBar::OnDrawImage

Wywoływane przez strukturę, aby narysować obraz paska podpisu.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia, który jest używany do wyświetlania obrazu.

*Rect*<br/>
[w] Określa prostokąt ograniczający obrazu.

### <a name="remarks"></a>Uwagi

Zastąpić tę `CMFCCaptionBar` metodę w klasie pochodnej, aby dostosować wygląd obrazu.

## <a name="cmfccaptionbarondrawtext"></a><a name="ondrawtext"></a>CMFCCaptionBar::OnDrawText

Wywoływane przez strukturę, aby narysować tekst paska podpisu.

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia, który jest używany do wyświetlania przycisku.

*Rect*<br/>
[w] Prostokąt obwiedniowy tekstu.

*strText (tekst)*<br/>
[w] Ciąg tekstowy do wyświetlenia.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wyświetla `CDC::DrawText` tekst przy użyciu i [CMFCCaptionBar::m_clrBarText](#m_clrbartext) kolor.

Zastąpić tę `CMFCCaptionBar` metodę w klasie pochodnej, aby dostosować wygląd tekstu paska podpisu.

## <a name="cmfccaptionbarremovebitmap"></a><a name="removebitmap"></a>CMFCCaptionBar::RemoveBitmap

Usuwa obraz mapy bitowej z paska podpisu.

```cpp
void RemoveBitmap();
```

## <a name="cmfccaptionbarremovebutton"></a><a name="removebutton"></a>CMFCCaptionBar::UsuńButton

Usuwa przycisk z paska podpisu.

```cpp
void RemoveButton();
```

### <a name="remarks"></a>Uwagi

Układ elementów paska podpisu jest dostosowywany automatycznie.

## <a name="cmfccaptionbarremoveicon"></a><a name="removeicon"></a>CMFCCaptionBar::RemoveIcon

Usuwa ikonę z paska podpisu.

```cpp
void RemoveIcon();
```

## <a name="cmfccaptionbarremovetext"></a><a name="removetext"></a>CMFCCaptionBar::Usuń Tekst

Usuwa etykietę tekstową z paska podpisu.

```cpp
void RemoveText();
```

## <a name="cmfccaptionbarsetbitmap"></a><a name="setbitmap"></a>CMFCCaptionBar::SetBitmap

Ustawia obraz bitmapowy dla paska podpisu.

```cpp
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

*hBitmapa*<br/>
[w] Uchwyt do mapy bitowej, aby ustawić.

*clrPrzezroczysty*<br/>
[w] Wartość RGB określająca przezroczysty kolor mapy bitowej.

*bStieczka*<br/>
[w] Jeśli true, mapa bitowa jest rozciągnięta, jeśli nie pasuje do prostokąta ograniczającego obraz. W przeciwnym razie mapa bitowa nie jest rozciągnięta.

*bmpWserwość*<br/>
[w] Wyrównanie mapy bitowej.

### <a name="remarks"></a>Uwagi

Ta metoda służy do ustawiania mapy bitowej na pasku podpisu.

Poprzednia mapa bitowa jest niszczony automatycznie. Jeśli na pasku podpisu jest wyświetlana ikona, ponieważ nazwano metodę [CMFCCaptionBar::SetIcon,](#seticon) mapa bitowa nie będzie wyświetlana, chyba że usuniesz ikonę, wywołując [CMFCCaptionBar::RemoveIcon](#removeicon).

Mapa bitowa jest wyrównana zgodnie z parametrem *bmpAlignment.*  Ten parametr może być `BarElementAlignment` jedną z następujących wartości:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetbordersize"></a><a name="setbordersize"></a>CMFCCaptionBar::SetBorderSize

Ustawia rozmiar obramowania paska podpisu.

```cpp
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize (rozmiar)*<br/>
[w] Nowy rozmiar obramowania paska podpisu w pikselach.

## <a name="cmfccaptionbarsetbutton"></a><a name="setbutton"></a>CMFCCaptionBar::Przycisk seta

Ustawia przycisk paska podpisu.

```cpp
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
Etykieta polecenia przycisku.

*uiCmdUI*<br/>
Identyfikator polecenia przycisku.

*btnAlignmnet*<br/>
Wyrównanie przycisku.

*bHasDropDownArrow*<br/>
PRAWDA, jeśli przycisk wyświetla strzałkę rozwijaną, w przeciwnym razie wartość FAŁSZUj.

## <a name="cmfccaptionbarsetbuttonpressed"></a><a name="setbuttonpressed"></a>CMFCCaptionBar::SetButtonPressed

Określa, czy przycisk pozostaje naciśnięty.

```cpp
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>Parametry

*bZdniałe*<br/>
PRAWDA, jeśli przycisk zachowuje stan naciśnięcia, FALSE w przeciwnym razie.

## <a name="cmfccaptionbarsetbuttontooltip"></a><a name="setbuttontooltip"></a>CMFCCaptionBar::SetButtonToolTip

Ustawia etykietkę narzędzia dla przycisku.

```cpp
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Parametry

*lpszToolTip*<br/>
[w] Podpis etykietki narzędzia.

*lpszDescription*<br/>
[w] Opis etykietki narzędzia.

## <a name="cmfccaptionbarsetflatborder"></a><a name="setflatborder"></a>CMFCCaptionBar::SetFlatBorder

Ustawia styl obramowania paska podpisu.

```cpp
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Parametry

*bFlat (ur.*<br/>
[w] PRAWDA, jeśli obramowanie paska podpisu jest płaskie. FAŁSZ, jeśli obramowanie jest 3D.

## <a name="cmfccaptionbarseticon"></a><a name="seticon"></a>CMFCCaptionBar::SetIcon

Ustawia ikonę paska podpisu.

```cpp
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parametry

*hIcon (własówce)*<br/>
[w] Uchwyt do ikony, aby ustawić.

*iconZdyspodań ws.*<br/>
[w] Wyrównanie ikony.

### <a name="remarks"></a>Uwagi

Paski podpisów mogą wyświetlać ikony lub mapy bitowe. Zobacz [CMFCCaptionBar::SetBitmap,](#setbitmap) aby dowiedzieć się, jak wyświetlić mapę bitową. Jeśli ustawisz zarówno ikonę, jak i mapę bitową, ikona jest zawsze wyświetlana. Wywołanie [CMFCCaptionBar::RemoveIcon](#removeicon) usunąć ikonę z paska podpisu.

Ikona jest wyrównana zgodnie z *parametrem iconAlignment.* Może to być jedna `BarElementAlignment` z następujących wartości:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetimagetooltip"></a><a name="setimagetooltip"></a>CMFCCaptionBar::SetImageToolTip

Ustawia etykietkę narzędzia obrazu na pasku podpisu.

```cpp
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Parametry

*lpszToolTip*<br/>
[w] Tekst etykietki narzędzia.

*lpszDescription*<br/>
[w] Opis etykietki narzędzia.

## <a name="cmfccaptionbarsetmargin"></a><a name="setmargin"></a>CMFCCaptionBar::SetMargin

Ustawia odległość między krawędzią elementu paska podpisu a krawędzią formantu paska podpisu.

```cpp
void SetMargin(int nMargin);
```

### <a name="parameters"></a>Parametry

*nMargin (właso)*<br/>
[w] Odległość w pikselach między krawędzią elementów paska podpisu a krawędzią formantu paska podpisu.

## <a name="cmfccaptionbarsettext"></a><a name="settext"></a>CMFCCaptionBar::SetText

Ustawia etykietę tekstową dla paska podpisu.

```cpp
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parametry

*strText (tekst)*<br/>
[w] Ciąg tekstowy do skonfigurowania.

*Textalignment*<br/>
[w] Wyrównanie tekstu.

### <a name="remarks"></a>Uwagi

Etykieta tekstowa jest wyrównana zgodnie z parametrem *textAlignment.* Może to być jedna `BarElementAlignment` z następujących wartości:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
