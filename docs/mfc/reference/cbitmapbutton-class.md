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
ms.openlocfilehash: 0cf4554f86f4a9275e4d96b3db519fde7fb05b22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231874"
---
# <a name="cbitmapbutton-class"></a>Klasa CBitmapButton

Tworzy kontrolki przycisku z obrazami mapy bitowej zamiast tekstu.

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
|[CBitmapButton:: autoload](#autoload)|Kojarzy przycisk w oknie dialogowym z obiektem `CBitmapButton` klasy, ładuje mapy bitowe według nazwy i dopasowuje przycisk w celu dopasowania do mapy bitowej.|
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|Inicjuje obiekt, ładując jeden lub więcej nazwanych zasobów mapy bitowej z pliku zasobów aplikacji i dołączając mapy bitowe do obiektu.|
|[CBitmapButton::SizeToContent](#sizetocontent)|Dopasowuje przycisk, aby dopasować mapę bitową.|

## <a name="remarks"></a>Uwagi

`CBitmapButton`obiekty zawierają maksymalnie cztery mapy bitowe, które zawierają obrazy dla różnych stanów przycisku może zajmować się: w górę (lub normalny), w dół (lub wybrane), skoncentrowane i wyłączona. Wymagana jest tylko pierwsza Mapa bitowa; inne są opcjonalne.

Obrazy przycisków mapy bitowej obejmują obramowanie wokół obrazu oraz sam obraz. Obramowanie zazwyczaj odtwarza część w pokazywania stanu przycisku. Na przykład mapa bitowa dla stanu skoncentrowanego zwykle jest taka jak dla stanu up, ale z kreskowanym prostokątnym obramowaniem z granicy lub grubej linii kryjącej na granicy. Mapa bitowa dla stanu disabled zwykle jest podobna do tej dla stanu up, ale ma niższy kontrast (na przykład wygaszony lub wyszarzony wybór menu).

Te mapy bitowe mogą mieć rozmiar, ale wszystkie są traktowane tak, jakby były takie same, jak mapa bitowa stanu up.

Różne aplikacje wymagają różnych kombinacji obrazów map bitowych:

|W górę|W dół|Ustawiono fokus|Disabled|Aplikacja|
|--------|----------|-------------|--------------|-----------------|
|×||||Mapy|
|×|×|||Przycisk bez stylu WS_TABSTOP|
|×|×|×|×|Przycisk okna dialogowego ze wszystkimi Stanami|
|×|×|×||Przycisk okna dialogowego z stylem WS_TABSTOP|

Podczas tworzenia kontrolki Bitmap-Button Ustaw styl BS_OWNERDRAW, aby określić, że przycisk jest rysowany przez właściciela. Powoduje to, że system Windows wyśle WM_MEASUREITEM i WM_DRAWITEM komunikatów dla przycisku; Platforma obsługuje te komunikaty i zarządza wyglądem przycisku.

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>Aby utworzyć kontrolkę przycisk mapy bitowej w obszarze klienta okna

1. Utwórz jeden do czterech obrazów mapy bitowej dla przycisku.

1. Utwórz obiekt [CBitmapButton](#cbitmapbutton) .

1. Wywołaj funkcję [Create](../../mfc/reference/cbutton-class.md#create) , aby utworzyć kontrolkę przycisku systemu Windows i dołączyć ją do `CBitmapButton` obiektu.

1. Wywołaj funkcję elementu członkowskiego [LoadBitmaps](#loadbitmaps) w celu załadowania zasobów mapy bitowej po zbudowaniu przycisku mapy bitowej.

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>Aby dołączyć kontrolkę przycisk mapy bitowej w oknie dialogowym

1. Utwórz jeden do czterech obrazów mapy bitowej dla przycisku.

1. Utwórz szablon okna dialogowego z przyciskiem rysowania przez właściciela umieszczonym w miejscu, w którym ma zostać wyświetlony przycisk mapy bitowej. Rozmiar przycisku w szablonie nie ma znaczenia.

1. Ustaw podpis przycisku na wartość taką jak "mój obraz" i zdefiniuj symbol przycisku, takiego jak IDC_MYIMAGE.

1. W skrypcie zasobów aplikacji nadaj każdemu z obrazów utworzonych dla przycisku identyfikator zbudowany przez dołączenie jednej z liter "U", "D", "F," lub "X" (dla elementów up, Down, skoncentrowane i wyłączonych) na ciąg używany dla podpisu przycisku w kroku 3. Na przykład etykieta przycisku "webimage" może mieć identyfikatory "MYIMAGEU", "MYIMAGEF" i "Narzędzie IMAGEX". **Należy** określić identyfikator map bitowych w podwójnych cudzysłowach. W przeciwnym razie Edytor zasobów przypisze liczbę całkowitą do zasobu, a MFC zakończy się niepowodzeniem podczas ładowania obrazu.

1. W klasie okna dialogowego aplikacji (pochodzącej od `CDialog` ) Dodaj `CBitmapButton` obiekt elementu członkowskiego.

1. W `CDialog` procedurze [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) obiektu Wywołaj `CBitmapButton` funkcję [autoładowania](#autoload) obiektu, używając jako parametrów identyfikatora kontrolki przycisku i `CDialog` **`this`** wskaźnika obiektu.

Jeśli chcesz obsługiwać komunikaty powiadomień systemu Windows, takie jak BN_CLICKED, wysyłane przez kontrolkę przycisku mapy bitowej do jej elementu nadrzędnego (zazwyczaj klasy pochodnej `CDialog` ), Dodaj do `CDialog` obiektu pochodnego wpis mapy komunikatów i funkcję elementu członkowskiego obsługi komunikatów dla każdego komunikatu. Powiadomienia wysyłane przez `CBitmapButton` obiekt są takie same jak te wysyłane przez obiekt [CButton](../../mfc/reference/cbutton-class.md) .

Klasa [CToolBar](../../mfc/reference/ctoolbar-class.md) przyjmuje różne podejście do przycisków map bitowych.

Aby uzyskać więcej informacji na temat `CBitmapButton` , zobacz [Controls](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext. h

## <a name="cbitmapbuttonautoload"></a><a name="autoload"></a>CBitmapButton:: autoload

Kojarzy przycisk w oknie dialogowym z obiektem `CBitmapButton` klasy, ładuje mapy bitowe według nazwy i dopasowuje przycisk w celu dopasowania do mapy bitowej.

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator kontrolki przycisku.

*pParent*<br/>
Wskaźnik do obiektu, który jest właścicielem przycisku.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `AutoLoad` funkcji, aby zainicjować przycisk rysowania przez właściciela w oknie dialogowym jako przycisk mapy bitowej. Instrukcje dotyczące korzystania z tej funkcji znajdują się w uwagach dla `CBitmapButton` klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

## <a name="cbitmapbuttoncbitmapbutton"></a><a name="cbitmapbutton"></a>CBitmapButton::CBitmapButton

Tworzy obiekt `CBitmapButton`.

```
CBitmapButton();
```

### <a name="remarks"></a>Uwagi

Po utworzeniu obiektu C++ `CBitmapButton` Wywołaj [CButton:: Create](../../mfc/reference/cbutton-class.md#create) , aby utworzyć kontrolkę przycisku systemu Windows i dołączyć ją do `CBitmapButton` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

## <a name="cbitmapbuttonloadbitmaps"></a><a name="loadbitmaps"></a>CBitmapButton::LoadBitmaps

Użyj tej funkcji, jeśli chcesz ładować obrazy mapy bitowej identyfikowane przez ich nazwy zasobów lub numery IDENTYFIKACYJNe, lub jeśli nie możesz użyć `AutoLoad` funkcji, ponieważ na przykład tworzysz przycisk mapy bitowej, który nie jest częścią okna dialogowego.

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
Wskazuje ciąg zakończony znakiem null, który zawiera nazwę mapy bitowej dla stanu normalnego lub "w górę" przycisku mapy bitowej. Wymagany.

*lpszBitmapResourceSel*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera nazwę mapy bitowej dla wybranego przycisku mapy bitowej lub "Down". Może mieć wartość NULL.

*lpszBitmapResourceFocus*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera nazwę mapy bitowej dla stanu skoncentrowanego przycisku mapy bitowej. Może mieć wartość NULL.

*lpszBitmapResourceDisabled*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera nazwę mapy bitowej dla stanu wyłączenia przycisku mapy bitowej. Może mieć wartość NULL.

*nIDBitmapResource*<br/>
Określa numer identyfikatora zasobu mapy bitowej przycisku "normalny" lub "w górę". Wymagany.

*nIDBitmapResourceSel*<br/>
Określa numer identyfikatora zasobu dla wybranego przycisku mapy bitowej lub stanu "w dół". Może wynosić 0.

*nIDBitmapResourceFocus*<br/>
Określa numer identyfikatora zasobu mapy bitowej dla stanu skoncentrowanego przycisku bitmapy. Może wynosić 0.

*nIDBitmapResourceDisabled*<br/>
Określa numer identyfikatora zasobu mapy bitowej dla stanu wyłączonego przycisku bitmapy. Może wynosić 0.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

## <a name="cbitmapbuttonsizetocontent"></a><a name="sizetocontent"></a>CBitmapButton::SizeToContent

Wywołaj tę funkcję w celu zmiany rozmiaru przycisku mapy bitowej na rozmiar mapy bitowej.

```cpp
void SizeToContent();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>Zobacz także

[Przykład CTRLTEST MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CButton](../../mfc/reference/cbutton-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
