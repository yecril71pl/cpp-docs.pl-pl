---
title: Klasa CMFCDynamicLayout
ms.date: 11/04/2016
f1_keywords:
- CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout::AddItem
- AFXLAYOUT/CMFCDynamicLayout::Adjust
- AFXLAYOUT/CMFCDynamicLayout::Create
- AFXLAYOUT/CMFCDynamicLayout::GetHostWnd
- AFXLAYOUT/CMFCDynamicLayout::GetMinSize
- AFXLAYOUT/CMFCDynamicLayout::GetWindowRect
- AFXLAYOUT/CMFCDynamicLayout::HasItem
- AFXLAYOUT/CMFCDynamicLayout::IsEmpty
- AFXLAYOUT/CMFCDynamicLayout::LoadResource
- AFXLAYOUT/CMFCDynamicLayout::SetMinSize
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
ms.openlocfilehash: da512b5e05f3d5ff0229cc44a0a8268148a43f82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640638"
---
# <a name="cmfcdynamiclayout-class"></a>Klasa CMFCDynamicLayout

Określa, jak przenieść i zmiany rozmiaru, ponieważ użytkownik zmienia rozmiar okna kontrolki w oknie.

## <a name="syntax"></a>Składnia

```
class CMFCDynamicLayout : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCDynamicLayout::CMFCDynamicLayout`|Konstruuje `CMFCDynamicLayout` obiektu.|
|`CMFCDynamicLayout::~CMFCDynamicLayout`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDynamicLayout::AddItem](#additem)|Dodaje okno podrzędne, zwykle kontrolkę, do listy systemu windows, które są kontrolowane przez Menedżera układ dynamiczny.|
|[CMFCDynamicLayout::Adjust](#adjust)|Dodaje okno podrzędne, zwykle kontrolkę, do listy systemu windows, które są kontrolowane przez Menedżera układ dynamiczny.|
|[CMFCDynamicLayout::Create](#create)|Przechowuje i weryfikuje okno hosta.|
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|Zwraca wskaźnik do okna hosta.|
|[CMFCDynamicLayout::GetMinSize](#getminsize)|Zwraca rozmiar okna, poniżej której układu nie jest uwzględniany.|
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|Pobiera prostokąt dla bieżącego obszaru klienckiego okna.|
|[CMFCDynamicLayout::HasItem](#hasitem)|Sprawdza, jeśli kontrolka podrzędna została dodana do układ dynamiczny.|
|[CMFCDynamicLayout::IsEmpty](#isempty)|Sprawdza, czy układ dynamiczny ma nie okien podrzędnych dodane.|
|[CMFCDynamicLayout::LoadResource](#loadresource)|Odczytuje układ dynamiczny z zasobu AFX_DIALOG_LAYOUT, a następnie stosuje układ okna hosta.|
|statyczne [CMFCDynamicLayout::MoveHorizontal](#movehorizontal)|Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile kontrolka podrzędna zostanie przesunięta w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.|
|statyczne [CMFCDynamicLayout::MoveHorizontalAndVertical](#movehorizontalandvertical)|Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile kontrolka podrzędna zostanie przesunięta w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.|
|statyczne [CMFCDynamicLayout::MoveNone](#movenone)|Pobiera [MoveSettings](#movesettings_structure) wartość, która reprezentuje nie ruchu pionowych lub poziomych, kontrolki podrzędne.|
|statyczne [CMFCDynamicLayout::MoveVertical](#movevertical)|Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile kontrolka podrzędna zostanie przesunięta w pionie, gdy użytkownik zmienia rozmiar okna obsługi.|
|[CMFCDynamicLayout::SetMinSize](#setminsize)|Ustawia rozmiar okna, poniżej której układu nie jest uwzględniany.|
|statyczne [CMFCDynamicLayout::SizeHorizontal](#sizehorizontal)|Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, ile kontrolki podrzędnej zmiany rozmiaru w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.|
|statyczne [CMFCDynamicLayout::SizeHorizontalAndVertical](#sizehorizontalandvertical)|Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, ile kontrolki podrzędnej zmiany rozmiaru w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.|
|statyczne [CMFCDynamicLayout::SizeNone](#sizenone)|Pobiera [SizeSettings](#sizesettings_structure) wartość, która reprezentuje nie zmieni się rozmiar kontrolki podrzędnej.|
|statyczne [CMFCDynamicLayout::SizeVertical](#sizevertical)|Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, ile kontrolki podrzędnej zmiany rozmiaru w pionie, gdy użytkownik zmienia rozmiar okna obsługi.|

## <a name="nested-types"></a>Zagnieżdżone typy

|Nazwa|Opis|
|----------|-----------------|
|[Struktura CMFCDynamicLayout::MoveSettings](#movesettings_structure)|Hermetyzuje przenoszenia danych dla formantów w układ dynamiczny.|
|[Cmfcdynamiclayout::sizesettings — struktura](#sizesettings_structure)|Hermetyzuje dane zmiany rozmiaru formantów w układ dynamiczny.|

## <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxlayout.h

##  <a name="additem"></a>  CMFCDynamicLayout::AddItem

Dodaje okno podrzędne, zwykle kontrolkę, do listy systemu windows, które są kontrolowane przez Menedżera układ dynamiczny.

```
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```

### <a name="parameters"></a>Parametry

*hwnd*<br/>
Dojście do okna, aby dodać.

*nID*<br/>
Identyfikator kontrolki podrzędnej do dodania.

*moveSettings*<br/>
Struktura, która w tym artykule opisano, jak kontrolka zostanie przeniesiona zgodnie ze zmianami wielkości okna.

*sizeSettings*<br/>
Struktura, która w tym artykule opisano, jak można zmienić formant w zgodnie ze zmianami wielkości okna.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli element został dodany pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Położenie i rozmiar kontrolki podrzędnej jest zmieniany dynamicznie przy zmianie rozmiaru okna hostowania.

##  <a name="adjust"></a>  CMFCDynamicLayout::Adjust

Dodaje okno podrzędne, zwykle kontrolkę, do listy systemu windows, które są kontrolowane przez Menedżera układ dynamiczny.

```
void Adjust();
```

### <a name="remarks"></a>Uwagi

Położenie i rozmiar kontrolki podrzędnej jest zmieniany dynamicznie przy zmianie rozmiaru okna hostowania.

##  <a name="create"></a>  CMFCDynamicLayout::Create

Przechowuje i weryfikuje okno hosta.

```
BOOL Create(CWnd* pHostWnd);
```

### <a name="parameters"></a>Parametry

*pHostWnd*<br/>
Wskaźnik do okna hosta.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli tworzenie powiodło się; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="gethostwnd"></a>  CMFCDynamicLayout::GetHostWnd

Zwraca wskaźnik do okna hosta.

```
CWnd* GetHostWnd();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna hosta.

### <a name="remarks"></a>Uwagi

Domyślnie wszystkie pozycje kontrolki podrzędne ponownie obliczone względem tego okna.

##  <a name="getminsize"></a>  CMFCDynamicLayout::GetMinSize

Zwraca rozmiar okna, poniżej której układu nie jest uwzględniany.

```
CSize GetMinSize();
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar okna, poniżej której układu nie jest uwzględniany.

### <a name="remarks"></a>Uwagi

Położenie i rozmiar kontrolki podrzędnej jest zmieniany dynamicznie, gdy zmianie rozmiaru okna hostowania, ale ma minimalnego rozmiaru, poniżej której układ nie jest uwzględniany. Użytkownika można zmienić rozmiar okna na mniejszy, ale części okna są ukryte w widoku.

##  <a name="getwindowrect"></a>  CMFCDynamicLayout::GetWindowRect

Pobiera prostokąt dla bieżącego obszaru klienckiego okna.

```
void GetHostWndRect(CRect& rect,);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Po powrocie funkcji, ten parametr zawiera prostokąt otaczający obszaru układu. To jest parametrem wyjściowym; wartość wejściowa jest zastępowany.

### <a name="remarks"></a>Uwagi

##  <a name="hasitem"></a>  CMFCDynamicLayout::HasItem

Sprawdza, jeśli kontrolka podrzędna została dodana do układ dynamiczny.

```
BOOL HasItem(HWND hwnd);
```

### <a name="parameters"></a>Parametry

*hwnd*<br/>
Uchwyt okna dla formantu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli układu ma już ten element; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="isempty"></a>  CMFCDynamicLayout::IsEmpty

Sprawdza, czy układ dynamiczny ma nie okien podrzędnych dodane.

```
BOOL IsEmpty();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli układu nie ma żadnych elementów; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="loadresource"></a>  CMFCDynamicLayout::LoadResource

Odczytuje układ dynamiczny z zasobu AFX_DIALOG_LAYOUT, a następnie stosuje układ okna hosta.

```
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);
```

### <a name="parameters"></a>Parametry

*pHostWnd*<br/>
Wskaźnik do okna hosta.

*lpResource*<br/>
Wskaźnik do buforu, który zawiera zasób AFX_DIALOG_LAYOUT.

*niezerowego*<br/>
Rozmiar buforu w bajtach.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zasób jest ładowany i stosowane na oknie hosta. w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="movehorizontal"></a>  CMFCDynamicLayout::MoveHorizontal

Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile kontrolka podrzędna zostanie przesunięta w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.

```
static MoveSettings MoveHorizontal(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Określa w procentach, jak daleko kontrolka podrzędna zostanie przesunięta w poziomie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

A [MoveSettings](#movesettings_structure) wartość, która hermetyzuje żądany Przesuń wskaźnik.

### <a name="remarks"></a>Uwagi

##  <a name="movehorizontalandvertical"></a>  CMFCDynamicLayout::MoveHorizontalAndVertical

Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile kontrolka podrzędna zostanie przesunięta w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.

```
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parametry

*nXRatio*<br/>
Określa w procentach, jak daleko kontrolka podrzędna zostanie przesunięta w poziomie, gdy użytkownik zmienia rozmiar okna hosta.

*nYRatio*<br/>
Określa w procentach, jak daleko kontrolka podrzędna zostanie przesunięta w pionie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

A [MoveSettings](#movesettings_structure) wartość, która hermetyzuje żądany Przesuń wskaźnik.

### <a name="remarks"></a>Uwagi

##  <a name="movenone"></a>  CMFCDynamicLayout::MoveNone

Pobiera [MoveSettings](#movesettings_structure) wartość, która reprezentuje nie ruchu pionowych lub poziomych, kontrolki podrzędne.

```
static MoveSettings MoveNone();
```

### <a name="return-value"></a>Wartość zwracana

A [MoveSettings](#movesettings_structure) wartość, która rozwiązuje kontrolki w miejscu, tak aby nie powoduje przeniesienia, ponieważ użytkownik zmienia rozmiar okna hosta.

### <a name="remarks"></a>Uwagi

##  <a name="movesettings_structure"></a>  Struktura CMFCDynamicLayout::MoveSettings

Hermetyzuje przenoszenia danych dla formantów w układ dynamiczny.

```
struct CMFCDynamicLayout::MoveSettings;
```

### <a name="remarks"></a>Uwagi

Jest to klasa zagnieżdżona wewnątrz `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout::MoveSettings::IsHorizontal

Sprawdź, jeśli przenoszenie danych określa wartość różną od zera przenoszenia poziomej.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli `MoveSettings` obiektu określa wartość różną od zera przeniesienie poziomej.

## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout::MoveSettings::IsNone

Sprawdź, jeśli przenoszenie danych określa nie przepływu.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli `MoveSettings` obiektu określa nie przepływu.

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout::MoveSettings::IsVertical

  Sprawdź, jeśli przenoszenie danych określa wartość różną od zera przenoszenia pionowy.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli `MoveSettings` obiektu określa wartość różną od zera przenoszenia pionowy.

##  <a name="movevertical"></a>  CMFCDynamicLayout::MoveVertical

Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile kontrolka podrzędna zostanie przesunięta w pionie, gdy użytkownik zmienia rozmiar okna obsługi.

```
static MoveSettings MoveVertical(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Określa w procentach, jak daleko kontrolka podrzędna zostanie przesunięta w pionie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

A [MoveSettings](#movesettings_structure) wartość, która hermetyzuje żądany Przesuń wskaźnik.

### <a name="remarks"></a>Uwagi

##  <a name="setminsize"></a>  CMFCDynamicLayout::SetMinSize

Ustawia rozmiar okna, poniżej której układu nie jest uwzględniany.

```
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Żądany rozmiar, poniżej której układu nie jest uwzględniany.

### <a name="remarks"></a>Uwagi

Położenie i rozmiar kontrolki podrzędnej jest zmieniany dynamicznie, gdy zmianie rozmiaru okna hostowania, ale ma minimalnego rozmiaru, poniżej której układ nie jest uwzględniany. Użytkownika można zmienić rozmiar okna na mniejszy, ale części okna są ukryte w widoku.

##  <a name="sizehorizontal"></a>  CMFCDynamicLayout::SizeHorizontal

Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, ile kontrolki podrzędnej zmiany rozmiaru w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.

```
static SizeSettings SizeHorizontal(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Określa w procentach, jak daleko kontrolka podrzędna zmiany rozmiaru w poziomie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

A [SizeSettings](#sizesettings_structure) wartość, która hermetyzuje współczynnik żądanego rozmiaru.

### <a name="remarks"></a>Uwagi

##  <a name="sizehorizontalandvertical"></a>  CMFCDynamicLayout::SizeHorizontalAndVertical

Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, ile kontrolki podrzędnej zmiany rozmiaru w poziomie, gdy użytkownik zmienia rozmiar okna obsługi.

```
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parametry

*nXRatio*<br/>
Określa w procentach, jak daleko kontrolka podrzędna zmiany rozmiaru w poziomie, gdy użytkownik zmienia rozmiar okna hosta.

*nYRatio*<br/>
Określa w procentach, jak daleko kontrolka podrzędna zmiany rozmiaru w pionie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

A [SizeSettings](#sizesettings_structure) wartość, która hermetyzuje współczynnik żądanego rozmiaru.

### <a name="remarks"></a>Uwagi

##  <a name="sizenone"></a>  CMFCDynamicLayout::SizeNone

Pobiera [SizeSettings](#sizesettings_structure) wartość, która reprezentuje nie zmieni się rozmiar kontrolki podrzędnej.

```
static SizeSettings SizeNone();
```

### <a name="return-value"></a>Wartość zwracana

A [SizeSettings](#sizesettings_structure) wartość, która rozwiązuje formantu o rozmiarze tak, aby nie zmienia rozmiar jako użytkownik zmienia rozmiar okna hosta.

### <a name="remarks"></a>Uwagi

##  <a name="sizesettings_structure"></a>  Cmfcdynamiclayout::sizesettings — struktura

Hermetyzuje dane zmiany rozmiaru formantów w układ dynamiczny.

```
struct CMFCDynamicLayout::SizeSettings;
```

### <a name="remarks"></a>Uwagi

Jest to klasa zagnieżdżona wewnątrz `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout::SizeSettings::IsHorizontal

Sprawdza, czy dane zmiany rozmiaru określa wartość różną od zera poziomy zmiany rozmiaru.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli `SizeSettings` obiekt określa wartość różną od zera poziomy zmiany rozmiaru.

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout::SizeSettings::IsNone

Sprawdza, czy dane zmiany rozmiaru określa bez zmiany rozmiaru.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli `SizeSettings` obiekt określa bez zmiany rozmiaru.

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout::SizeSettings::IsVertical

Sprawdza, czy dane zmiany rozmiaru określa wartość różną od zera pionowy zmiany rozmiaru.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli `SizeSettings` obiekt określa wartość różną od zera pionowy zmiany rozmiaru.

##  <a name="sizevertical"></a>  CMFCDynamicLayout::SizeVertical

Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, ile kontrolki podrzędnej zmiany rozmiaru w pionie, gdy użytkownik zmienia rozmiar okna obsługi.

```
static SizeSettings SizeVertical(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Określa w procentach, jak daleko kontrolka podrzędna zmiany rozmiaru w pionie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

A [SizeSettings](#sizesettings_structure) wartość, która hermetyzuje współczynnik żądanego rozmiaru.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
