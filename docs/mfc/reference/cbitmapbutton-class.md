---
title: Klasa CBitmapButton
ms.date: 11/04/2016
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
ms.openlocfilehash: df21591dec1da5861125d7e9480fb9345aaad061
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752950"
---
# <a name="cbitmapbutton-class"></a>Klasa CBitmapButton

Tworzy formanty przycisku oznaczone obrazami bitmapowym zamiast tekstu.

## <a name="syntax"></a>Składnia

```
class CBitmapButton : public CButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|Konstruuje `CBitmapButton` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmapButton::Autoload](#autoload)|Kojarzy przycisk w oknie dialogowym z `CBitmapButton` obiektem klasy, ładuje mapy bitowe według nazwy i rozmiaruje przycisk, aby pasował do mapy bitowej.|
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|Inicjuje obiekt, ładując co najmniej jeden nazwany materiał bitmapowy z pliku zasobów aplikacji i dołączając mapy bitowe do obiektu.|
|[CBitmapButton::SizeToContent](#sizetocontent)|Rozmiary przycisku, aby pomieścić bitmapę.|

## <a name="remarks"></a>Uwagi

`CBitmapButton`obiekty zawierają maksymalnie cztery mapy bitowe, które zawierają obrazy dla różnych stanów, które przycisk może przyjąć: w górę (lub normalnie), w dół (lub zaznaczone), skoncentrowane i wyłączone. Wymagana jest tylko pierwsza mapa bitowa; pozostałe są opcjonalne.

Obrazy przycisków bitmapowych zawierają obramowanie wokół obrazu, a także sam obraz. Obramowanie zazwyczaj odgrywa rolę w wyświetlaniu stanu przycisku. Na przykład mapa bitowa dla stanu skupiona jest zwykle podobna do mapy dla stanu w górę, ale z wstawką prostokąta przerywanego od obramowania lub grubą linią ciągłą na obramowania. Mapa bitowa dla stanu wyłączonego zwykle przypomina ten dla stanu w górę, ale ma mniejszy kontrast (np. wygaszony lub wyszarzony wybór menu).

Te mapy bitowe mogą mieć dowolny rozmiar, ale wszystkie są traktowane tak, jakby były tego samego rozmiaru co mapa bitowa dla stanu up.

Różne aplikacje wymagają różnych kombinacji obrazów bitmapowych:

|W górę|W dół|Ustawiono fokus|Disabled (Wyłączony)|Aplikacja|
|--------|----------|-------------|--------------|-----------------|
|×||||Bitmapy|
|×|×|||Przycisk bez stylu WS_TABSTOP|
|×|×|×|×|Przycisk Dialogowy ze wszystkimi stanami|
|×|×|×||Przycisk Dialogowy ze stylem WS_TABSTOP|

Podczas tworzenia formantu przycisku mapy bitowej ustaw styl BS_OWNERDRAW, aby określić, że przycisk jest rysowany przez właściciela. Powoduje to, że system Windows wysyła komunikaty WM_MEASUREITEM i WM_DRAWITEM dla przycisku; framework obsługuje te komunikaty i zarządza wygląd przycisku dla Ciebie.

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>Aby utworzyć kontrolkę przycisku mapy bitowej w obszarze klienta okna

1. Utwórz od jednego do czterech obrazów bitmapowych dla przycisku.

1. Skonstruuj [CBitmapButton](#cbitmapbutton) obiektu.

1. Wywołanie funkcji [Utwórz,](../../mfc/reference/cbutton-class.md#create) aby utworzyć kontrolka przycisku Systemu Windows i dołączyć go do `CBitmapButton` obiektu.

1. Wywołanie funkcji elementu członkowskiego [LoadBitmaps,](#loadbitmaps) aby załadować zasoby mapy bitowej po skonstruowaniu przycisku mapy bitowej.

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>Aby dołączyć kontrolkę przycisku mapy bitowej do okna dialogowego

1. Utwórz od jednego do czterech obrazów bitmapowych dla przycisku.

1. Utwórz szablon okna dialogowego z przyciskiem rysowania właściciela umieszczonym w miejscu, w którym ma się odwładniać. Rozmiar przycisku w szablonie nie ma znaczenia.

1. Ustaw podpis przycisku na wartość typu "MYIMAGE" i zdefiniuj symbol przycisku, taki jak IDC_MYIMAGE.

1. W skrypcie zasobów aplikacji podaj każdemu z obrazów utworzonych dla przycisku identyfikator utworzony przez dołączenie jednej z liter "U", "D", "F" lub "X" (dla góry, w dół, skoncentrowany i wyłączony) do ciągu używanego dla podpisu przycisku w kroku 3. Na przykład w przypadku przycisku "MYIMAGE" identyfikatory to " MYIMAGEU", " MYIMAGED", " MYIMAGEF" i " MYIMAGEX". Identyfikator map bitowych **należy** określić w cudzysłowie. W przeciwnym razie edytor zasobów przypisze całkowitą do zasobu, a MFC zakończy się niepowodzeniem podczas ładowania obrazu.

1. W klasie okna dialogowego aplikacji `CDialog`(pochodzące `CBitmapButton` z ), dodać obiekt elementu członkowskiego.

1. W `CDialog` procedurze [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) obiektu wywołaj funkcję [AutoLoad](#autoload) `CBitmapButton` obiektu, używając jako parametrów identyfikatora `CDialog` formantu przycisku i obiektu **ten** wskaźnik.

Jeśli chcesz obsługiwać wiadomości powiadomień systemu Windows, takie jak BN_CLICKED, wysyłane przez kontrolkę przycisku `CDialog`mapy bitowej do jego elementu nadrzędnego (zwykle klasy pochodnej), dodaj do obiektu `CDialog`pochodnego wpis mapy wiadomości i funkcję elementu członkowskiego obsługi wiadomości dla każdej wiadomości. Powiadomienia wysyłane przez `CBitmapButton` obiekt są takie same jak te wysyłane przez [CButton](../../mfc/reference/cbutton-class.md) obiektu.

Klasa [CToolBar](../../mfc/reference/ctoolbar-class.md) przyjmuje inne podejście do przycisków mapy bitowej.

Aby uzyskać `CBitmapButton`więcej informacji na temat , zobacz [Formanty](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cbutton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="cbitmapbuttonautoload"></a><a name="autoload"></a>CBitmapButton::Autoload

Kojarzy przycisk w oknie dialogowym z `CBitmapButton` obiektem klasy, ładuje mapy bitowe według nazwy i rozmiaruje przycisk, aby pasował do mapy bitowej.

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identyfikator sterowania przycisku.

*pRoczysz*<br/>
Wskaźnik do obiektu, który jest właścicielem przycisku.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Za `AutoLoad` pomocą tej funkcji można zainicjować przycisk rysowania właściciela w oknie dialogowym jako przycisk mapy bitowej. Instrukcje dotyczące korzystania z tej funkcji `CBitmapButton` znajdują się w uwagach dla klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

## <a name="cbitmapbuttoncbitmapbutton"></a><a name="cbitmapbutton"></a>CBitmapButton::CBitmapButton

Tworzy obiekt `CBitmapButton`.

```
CBitmapButton();
```

### <a name="remarks"></a>Uwagi

Po utworzeniu obiektu `CBitmapButton` C++ wywołaj [CButton::Create,](../../mfc/reference/cbutton-class.md#create) aby utworzyć kontrolka przycisku systemu Windows i dołączyć go do `CBitmapButton` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

## <a name="cbitmapbuttonloadbitmaps"></a><a name="loadbitmaps"></a>CBitmapButton::LoadBitmaps

Tej funkcji należy użyć, jeśli chcesz załadować obrazy bitmapowe identyfikowane przez ich `AutoLoad` nazwy zasobów lub numery identyfikacyjne lub gdy nie można użyć tej funkcji, ponieważ na przykład tworzysz przycisk mapy bitowej, który nie jest częścią okna dialogowego.

```
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,
    LPCTSTR lpszBitmapResourceSel = NULL,
    LPCTSTR lpszBitmapResourceFocus = NULL,
    LPCTSTR lpszBitmapResourceDisabled = NULL);

BOOL LoadBitmaps(
    UINT nIDBitmapResource,
    UINT nIDBitmapResourceSel = 0,
    UINT nIDBitmapResourceFocus = 0,
    UINT nIDBitmapResourceDisabled = 0);
```

### <a name="parameters"></a>Parametry

*lpszBitmapResource*<br/>
Wskazuje ciąg zakończony z wartością null, który zawiera nazwę mapy bitowej dla stanu normalnego lub "w górę" przycisku mapy bitowej. Wymagany.

*lpszBitmapResourceSel*<br/>
Wskazuje ciąg zakończony z wartością null, który zawiera nazwę mapy bitowej dla wybranego lub "w dół" stanu przycisku mapy bitowej. Może być null.

*lpszBitmapResourceFocus*<br/>
Wskazuje ciąg zakończony z wartością null, który zawiera nazwę mapy bitowej dla stanu skupiona przycisku mapy bitowej. Może być null.

*lpszBitmapResourceDisabled*<br/>
Wskazuje ciąg zakończony z wartością null, który zawiera nazwę mapy bitowej dla stanu wyłączonego przycisku mapy bitowej. Może być null.

*nIDBitmapResource*<br/>
Określa numer identyfikatora zasobu mapy bitowej dla stanu normalnego lub "w górę" przycisku mapy bitowej. Wymagany.

*nIDBitmapResourceSel*<br/>
Określa numer identyfikatora zasobu mapy bitowej dla wybranego lub "w dół" stanu przycisku mapy bitowej. Może być 0.

*nIDBitmapResourceFocus*<br/>
Określa numer identyfikatora zasobu mapy bitowej dla stanu skupiona przycisku mapy bitowej. Może być 0.

*nIDBitmapResourceDisabled*<br/>
Określa numer identyfikatora zasobu mapy bitowej dla stanu wyłączonego przycisku mapy bitowej. Może być 0.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

## <a name="cbitmapbuttonsizetocontent"></a><a name="sizetocontent"></a>CBitmapButton::SizeToContent

Wywołanie tej funkcji, aby zmienić rozmiar przycisku mapy bitowej do rozmiaru mapy bitowej.

```cpp
void SizeToContent();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[Klasa CButton](../../mfc/reference/cbutton-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
