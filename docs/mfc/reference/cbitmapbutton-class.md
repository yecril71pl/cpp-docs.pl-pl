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
ms.openlocfilehash: 45e0214cafb80c3e00a7e888a3170040f46113f1
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58770281"
---
# <a name="cbitmapbutton-class"></a>Klasa CBitmapButton

Tworzy przycisk kontrolek oznaczonych bitowymi obrazów zamiast tekstu mapami.

## <a name="syntax"></a>Składnia

```
class CBitmapButton : public CButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|Konstruuje `CBitmapButton` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmapButton::AutoLoad](#autoload)|Kojarzy przycisk w oknie dialogowym z obiektu `CBitmapButton` klasy, ładuje bitmap(s) według nazwy i rozmiar przycisku, aby dopasować mapę bitową.|
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|Inicjuje obiekt podczas ładowania co najmniej jeden zasób mapy bitowej o nazwie z pliku zasobów aplikacji i dołączanie bitmap do obiektu.|
|[CBitmapButton::SizeToContent](#sizetocontent)|Ustawia rozmiar przycisku aby pomieścić mapy bitowej.|

## <a name="remarks"></a>Uwagi

`CBitmapButton` obiekty zawierają maksymalnie cztery mapy bitowe, co zawierają obrazy w różnych regionach, można założyć, przycisk: górę (lub normalny) dół (lub wybrane) skupia się i wyłączone. Tylko pierwszy mapy bitowej jest wymagana. inne są opcjonalne.

Przycisk mapy bitowej obrazy obejmują obramowanie wokół obrazu, a także sam obraz. Obramowanie zwykle odgrywa rolę w przedstawiający stan przycisku. Na przykład mapa bitowa fokusem stanu zazwyczaj jest podobny do stanu pracy, ale wstawki kreskowane prostokąta, obramowanie lub Gruba linia ciągła na granicy. Mapa bitowa dla wyłączony stanu zwykle podobny do jednego dla się stan, lecz jest niższe kontrast (np. wybór wygaszone lub wygaszone menu).

Te mapy bitowe mogą być dowolnego rozmiaru, ale wszystkie są traktowane tak, jakby były one taki sam rozmiar jak mapy bitowej dla stanu pracy.

Różne aplikacje wymagają różnych kombinacji map bitowych:

|W górę|W dół|Fokus|Wyłączone|Aplikacja|
|--------|----------|-------------|--------------|-----------------|
|×||||Mapy bitowej|
|×|×|||Przycisk bez WS_TABSTOP stylu|
|×|×|×|×|Przycisk okna dialogowego z wszystkie stany|
|×|×|×||Okno dialogowe przycisk ze stylem WS_TABSTOP|

Podczas tworzenia kontrolki mapy bitowej przycisku, ustaw styl BS_OWNERDRAW, aby określić, czy przycisk jest rysowane przez właściciela. Powoduje to Windows wysyłać komunikaty WM_MEASUREITEM i WM_DRAWITEM dla przycisku; struktura obsługuje te komunikaty i zarządza wyglądu przycisku dla Ciebie.

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>Aby utworzyć kontrolkę przycisk mapy bitowej w obszaru klienckiego okna

1. Utwórz jednej do czterech obrazy mapy bitowej dla przycisku.

1. Konstruowania [CBitmapButton](#cbitmapbutton) obiektu.

1. Wywołaj [Utwórz](../../mfc/reference/cbutton-class.md#create) funkcję, aby utworzyć formant przycisku Windows i dołączyć go do `CBitmapButton` obiektu.

1. Wywołaj [LoadBitmaps](#loadbitmaps) funkcja elementu członkowskiego, które można załadować zasobów mapy bitowej, po jest tworzony przycisk mapy bitowej.

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>Aby dołączyć kontrolki przycisku mapy bitowej w oknie dialogowym

1. Utwórz jednej do czterech obrazy mapy bitowej dla przycisku.

1. Tworzenie szablonu okna dialogowego z przyciskiem rysowanym przez właściciela odległości przycisk mapy bitowej. Rozmiar przycisku w szablonie nie ma znaczenia.

1. Ustaw napis na przycisku z wartością, taką jak "MYIMAGE", a następnie zdefiniować symbol dla przycisku, takich jak IDC_MYIMAGE.

1. W skrypcie zasobów aplikacji Nadaj każdej obrazów utworzonych dla przycisku tworzony przez dołączenie jednej litery "U", "D", "F", identyfikator lub "X" (na górę, dół, fokus i wyłączone) na ciąg używany dla podpisu przycisku w kroku 3. Napis na przycisku "MYIMAGE", na przykład identyfikatory będzie "MYIMAGEU", "MYIMAGED", "MYIMAGEF" i "MYIMAGEX." Możesz **musi** . Określ identyfikator usługi map bitowych w cudzysłów. W przeciwnym razie Edytor zasobów przypisze całkowitą zasobu i MFC zakończy się niepowodzeniem podczas ładowania obrazu.

1. W aplikacji klasy okien dialogowych (pochodną `CDialog`), Dodaj `CBitmapButton` elementu członkowskiego obiektu.

1. W `CDialog` obiektu [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) wywołaniu procedury, `CBitmapButton` obiektu [załaduj](#autoload) funkcję, za pomocą jako parametry identyfikator formantu przycisku i `CDialog` obiektu **to** wskaźnika.

Jeśli chcesz obsługiwać komunikaty powiadomień, Windows, takie jak BN_CLICKED, wysyłany przez kontrolkę przycisku mapy bitowej do elementu nadrzędnego (zazwyczaj klasą pochodną `CDialog`), Dodaj do `CDialog`— obiekt pochodne mapy komunikatów wejścia i obsługi wiadomości elementu członkowskiego Funkcja dla każdego komunikatu. Powiadomienia wysyłane przez `CBitmapButton` obiektu są takie same, jak wysyłane przez [CButton](../../mfc/reference/cbutton-class.md) obiektu.

Klasa [CToolBar](../../mfc/reference/ctoolbar-class.md) mają inne podejście do przycisków mapy bitowej.

Aby uzyskać więcej informacji na temat `CBitmapButton`, zobacz [formantów](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

##  <a name="autoload"></a>  CBitmapButton::AutoLoad

Kojarzy przycisk w oknie dialogowym z obiektu `CBitmapButton` klasy, ładuje bitmap(s) według nazwy i rozmiar przycisku, aby dopasować mapę bitową.

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identyfikator formantu przycisku.

*pParent*<br/>
Wskaźnik do obiektu, który jest właścicielem przycisku.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `AutoLoad` funkcji, aby zainicjować przycisk rysowania przez właściciela, w oknie dialogowym jako przycisk mapy bitowej. Instrukcje dotyczące korzystania z tej funkcji znajdują się w uwagi dla `CBitmapButton` klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

##  <a name="cbitmapbutton"></a>  CBitmapButton::CBitmapButton

Tworzy `CBitmapButton` obiektu.

```
CBitmapButton();
```

### <a name="remarks"></a>Uwagi

Po utworzeniu C++ `CBitmapButton` obiektu, wywołaj [CButton::Create](../../mfc/reference/cbutton-class.md#create) do tworzenia kontrolki przycisku Windows i dołącz je do `CBitmapButton` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

##  <a name="loadbitmaps"></a>  CBitmapButton::LoadBitmaps

Użyj tej funkcji załadować obrazy mapy bitowej identyfikowane przez ich nazwy zasobu lub numery identyfikatorów lub jeśli nie możesz używać `AutoLoad` działać, ponieważ na przykład utworzysz przycisk mapy bitowej, który nie jest częścią okno dialogowe.

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
Wskazuje ciąg zakończony wartością null zawierający nazwę mapy bitowej Normalny przycisk mapy bitowej lub "stan up". Wymagana.

*lpszBitmapResourceSel*<br/>
Wskazuje ciąg zakończony zerem, który zawiera nazwę mapy bitowej dla wybranych przycisk mapy bitowej lub "stan działa". Może mieć wartości NULL.

*lpszBitmapResourceFocus*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera nazwę mapy bitowej dla przycisku kontrolki mapy bitowej koncentruje się stan. Może mieć wartości NULL.

*lpszBitmapResourceDisabled*<br/>
Wyłączone punkty ciąg zakończony znakiem null, który zawiera nazwę mapy bitowej dla przycisku kontrolki mapy bitowej. Może mieć wartości NULL.

*nIDBitmapResource*<br/>
Określa identyfikator zasobu zasób mapy bitowej, przycisk mapy bitowej normalny lub "stan up". Wymagana.

*nIDBitmapResourceSel*<br/>
Określa identyfikator zasobu zasób mapy bitowej wybranych przycisk mapy bitowej lub "stan działa". Może mieć wartość 0.

*nIDBitmapResourceFocus*<br/>
Określa identyfikator zasobu zasób mapy bitowej dla stanu wąsko zdefiniowany przycisk mapy bitowej. Może mieć wartość 0.

*nIDBitmapResourceDisabled*<br/>
Określa identyfikator zasobu zasobu mapy bitowej w stanie wyłączenia przycisk mapy bitowej. Może mieć wartość 0.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

##  <a name="sizetocontent"></a>  CBitmapButton::SizeToContent

Wywołaj tę funkcję, aby zmienić rozmiar przycisku mapy bitowej do rozmiaru mapy bitowej.

```
void SizeToContent();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>Zobacz także

[Próbki MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[Klasa CButton](../../mfc/reference/cbutton-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
