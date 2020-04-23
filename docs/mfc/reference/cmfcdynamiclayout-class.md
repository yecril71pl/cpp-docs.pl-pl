---
title: Klasa CMFCDynamicLayout
ms.date: 08/29/2019
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
ms.openlocfilehash: 77dd3a84a0c76b92495bb062eeb83ff013933087
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752385"
---
# <a name="cmfcdynamiclayout-class"></a>Klasa CMFCDynamicLayout

Określa sposób przenoszenia i rozmiaru formantów w oknie, gdy użytkownik zmienić rozmiar okna.

## <a name="syntax"></a>Składnia

```
class CMFCDynamicLayout : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCDynamicLayout::CMFCDynamicLayout`|Konstruuje `CMFCDynamicLayout` obiekt.|
|`CMFCDynamicLayout::~CMFCDynamicLayout`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDynamicLayout::AddItem](#additem)|Dodaje okno podrzędne, zazwyczaj formant, do listy okien, które są kontrolowane przez menedżera układu dynamicznego.|
|[CMFCDynamicLayout::Dopasuj](#adjust)|Dodaje okno podrzędne, zazwyczaj formant, do listy okien, które są kontrolowane przez menedżera układu dynamicznego.|
|[CMFCDynamicLayout::Tworzenie](#create)|Przechowuje i sprawdza poprawność okna hosta.|
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|Zwraca wskaźnik do okna hosta.|
|[CMFCDynamicLayout::GetMinSize](#getminsize)|Zwraca rozmiar okna, poniżej którego układ nie jest dostosowany.|
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|Pobiera prostokąt dla bieżącego obszaru klienta okna.|
|[CMFCDynamicLayout::HasItem](#hasitem)|Sprawdza, czy formant podrzędny został dodany do układu dynamicznego.|
|[CMFCDynamicLayout::IsEmpty](#isempty)|Sprawdza, czy układ dynamiczny nie ma okien podrzędnych.|
|[CMFCDynamicLayout::LoadResource](#loadresource)|Odczytuje układ dynamiczny z AFX_DIALOG_LAYOUT zasobu, a następnie stosuje układ do okna hosta.|
|statyczne [CMFCDynamicLayout::MoveHorizontal](#movehorizontal)|Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile formant podrzędny jest przenoszony w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.|
|statyczne [CMFCDynamicLayout::MoveHorizontalAndVertical](#movehorizontalandvertical)|Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile formant podrzędny jest przenoszony w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.|
|statyczny [CMFCDynamicLayout::MoveNone](#movenone)|Pobiera [MoveSettings](#movesettings_structure) wartość, która reprezentuje nie ruchu, pionowe lub poziome, dla formantu podrzędnego.|
|statyczne [CMFCDynamicLayout::MoveVertical](#movevertical)|Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile formant podrzędny jest przenoszony w pionie, gdy użytkownik zmienia rozmiar okna hostingu.|
|[CMFCDynamicLayout::SetMinSize](#setminsize)|Ustawia rozmiar okna, poniżej którego układ nie jest dostosowywany.|
|statyczne [CMFCDynamicLayout::SizeHorizontal](#sizehorizontal)|Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, jak bardzo formant podrzędny jest zmieniany w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.|
|statyczne [CMFCDynamicLayout::SizeHorizontalAndVertical](#sizehorizontalandvertical)|Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, jak bardzo formant podrzędny jest zmieniany w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.|
|statyczne [CMFCDynamicLayout::SizeNone](#sizenone)|Pobiera [SizeSettings](#sizesettings_structure) wartość, która reprezentuje nie zmiany rozmiaru formantu podrzędnego.|
|statyczne [CMFCDynamicLayout::SizeVertical](#sizevertical)|Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, jak bardzo formant podrzędny jest zmieniany w pionie, gdy użytkownik zmienia rozmiar okna hostingu.|

## <a name="nested-types"></a>Zagnieżdżone typy

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDynamicLayout::MoveSettings Struktura](#movesettings_structure)|Hermetyzuje przenoszenie danych dla formantów w układzie dynamicznym.|
|[CMFCDynamicLayout::Struktura rozmiarówstawienia](#sizesettings_structure)|Hermetyzuje dane zmiany rozmiaru dla formantów w układzie dynamicznym.|

## <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxlayout.h

## <a name="cmfcdynamiclayoutadditem"></a><a name="additem"></a>CMFCDynamicLayout::AddItem

Dodaje okno podrzędne, zazwyczaj formant, do listy okien, które są kontrolowane przez menedżera układu dynamicznego.

```
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Uchwyt do okna, aby dodać.

*Nid*<br/>
Identyfikator formantu podrzędnego do dodania.

*moveSettings*<br/>
Struktura, która opisuje, jak formant powinien być przenoszony w miarę zmiany rozmiaru okna.

*rozmiaryStawienia*<br/>
Struktura, która opisuje, jak formant powinien być zmieniany w miarę zmiany rozmiaru okna.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli element został dodany pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Położenie i rozmiar formantu podrzędnego jest zmieniana dynamicznie, gdy zmieniana jest zmiana rozmiaru okna hostingu.

## <a name="cmfcdynamiclayoutadjust"></a><a name="adjust"></a>CMFCDynamicLayout::Dopasuj

Dodaje okno podrzędne, zazwyczaj formant, do listy okien, które są kontrolowane przez menedżera układu dynamicznego.

```cpp
void Adjust();
```

### <a name="remarks"></a>Uwagi

Położenie i rozmiar formantu podrzędnego jest zmieniana dynamicznie, gdy zmieniana jest zmiana rozmiaru okna hostingu.

## <a name="cmfcdynamiclayoutcreate"></a><a name="create"></a>CMFCDynamicLayout::Tworzenie

Przechowuje i sprawdza poprawność okna hosta.

```
BOOL Create(CWnd* pHostWnd);
```

### <a name="parameters"></a>Parametry

*pHostWnd (pHostWnd)*<br/>
Wskaźnik do okna hosta.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli utworzenie zakończyło się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutgethostwnd"></a><a name="gethostwnd"></a>CMFCDynamicLayout::GetHostWnd

Zwraca wskaźnik do okna hosta.

```
CWnd* GetHostWnd();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna hosta.

### <a name="remarks"></a>Uwagi

Domyślnie wszystkie pozycje kontroli podrzędnej przeliczane względem tego okna.

## <a name="cmfcdynamiclayoutgetminsize"></a><a name="getminsize"></a>CMFCDynamicLayout::GetMinSize

Zwraca rozmiar okna, poniżej którego układ nie jest dostosowany.

```
CSize GetMinSize();
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar okna, poniżej którego układ nie jest dostosowany.

### <a name="remarks"></a>Uwagi

Położenie i rozmiar formantu podrzędnego jest zmieniana dynamicznie, gdy zmieniana jest zmiana rozmiaru okna hostingu, ale istnieje minimalny rozmiar, poniżej którego układ nie jest dostosowywany. Użytkownik może zmienić rozmiar okna na mniejszy rozmiar, ale części okna są następnie ukryte przed widokiem.

## <a name="cmfcdynamiclayoutgetwindowrect"></a><a name="getwindowrect"></a>CMFCDynamicLayout::GetWindowRect

Pobiera prostokąt dla bieżącego obszaru klienta okna.

```cpp
void GetHostWndRect(CRect& rect,);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Po powrocie funkcji ten parametr zawiera prostokąt ograniczający obszaru układu. Jest to parametr out; wartość wejściowa zostanie zastąpiona.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayouthasitem"></a><a name="hasitem"></a>CMFCDynamicLayout::HasItem

Sprawdza, czy formant podrzędny został dodany do układu dynamicznego.

```
BOOL HasItem(HWND hwnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Uchwyt okna dla formantu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli układ ma już ten element; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutisempty"></a><a name="isempty"></a>CMFCDynamicLayout::IsEmpty

Sprawdza, czy układ dynamiczny nie ma okien podrzędnych.

```
BOOL IsEmpty();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli układ nie ma elementów; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutloadresource"></a><a name="loadresource"></a>CMFCDynamicLayout::LoadResource

Odczytuje układ dynamiczny z AFX_DIALOG_LAYOUT zasobu, a następnie stosuje układ do okna hosta.

```
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);
```

### <a name="parameters"></a>Parametry

*pHostWnd (pHostWnd)*<br/>
Wskaźnik do okna hosta.

*lpResource*<br/>
Wskaźnik do buforu, który zawiera AFX_DIALOG_LAYOUT zasobu.

*dwSize (rozmiar)*<br/>
Rozmiar buforu w bajtach.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zasób jest załadowany i zastosowany do okna hosta; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutmovehorizontal"></a><a name="movehorizontal"></a>CMFCDynamicLayout::MoveHorizontal

Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile formant podrzędny jest przenoszony w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.

```
static MoveSettings MoveHorizontal(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio (nRatio)*<br/>
Definiuje jako procent, jak daleko formant podrzędny jest przenoszony w poziomie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

[MoveSettings](#movesettings_structure) wartość, która hermetyzuje żądany współczynnik przenoszenia.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutmovehorizontalandvertical"></a><a name="movehorizontalandvertical"></a>CMFCDynamicLayout::MoveHorizontalAndVertical

Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile formant podrzędny jest przenoszony w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.

```
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parametry

*nXRatio ( nXRatio )*<br/>
Definiuje jako procent, jak daleko formant podrzędny jest przenoszony w poziomie, gdy użytkownik zmienia rozmiar okna hosta.

*nYRatio*<br/>
Definiuje jako procent, jak daleko formant podrzędny jest przenoszony w pionie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

[MoveSettings](#movesettings_structure) wartość, która hermetyzuje żądany współczynnik przenoszenia.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutmovenone"></a><a name="movenone"></a>CMFCDynamicLayout::MoveNone

Pobiera [MoveSettings](#movesettings_structure) wartość, która reprezentuje nie ruchu, pionowe lub poziome, dla formantu podrzędnego.

```
static MoveSettings MoveNone();
```

### <a name="return-value"></a>Wartość zwracana

[MoveSettings](#movesettings_structure) wartość, która rozwiązuje formant w miejscu, tak aby nie przenieść jako użytkownik zmienia rozmiar okna hosta.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutmovesettings-structure"></a><a name="movesettings_structure"></a>CMFCDynamicLayout::MoveSettings Struktura

Hermetyzuje przenoszenie danych dla formantów w układzie dynamicznym.

```
struct CMFCDynamicLayout::MoveSettings;
```

### <a name="remarks"></a>Uwagi

Jest to klasa zagnieżdżona wewnątrz `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout::MoveSettings::IsHorizontal

Sprawdź, czy dane przenoszenia określają niezerowy ruch poziomy.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Wartość zwracana

PRAWDA, `MoveSettings` jeśli obiekt określa niezerowy ruch poziomy.

## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout::MoveSettings::IsNone

Sprawdź, czy dane przenoszenia nie określają żadnego ruchu.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Wartość zwracana

PRAWDA, `MoveSettings` jeśli obiekt nie określa żadnego ruchu.

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout::MoveSettings::IsVertical

Sprawdź, czy dane przenoszenia określają niezerowy ruch pionowy.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Wartość zwracana

PRAWDA, `MoveSettings` jeśli obiekt określa niezerowy ruch pionowy.

## <a name="cmfcdynamiclayoutmovevertical"></a><a name="movevertical"></a>CMFCDynamicLayout::MoveVertical

Pobiera [MoveSettings](#movesettings_structure) wartość, która definiuje, ile formant podrzędny jest przenoszony w pionie, gdy użytkownik zmienia rozmiar okna hostingu.

```
static MoveSettings MoveVertical(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio (nRatio)*<br/>
Definiuje jako procent, jak daleko formant podrzędny jest przenoszony w pionie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

[MoveSettings](#movesettings_structure) wartość, która hermetyzuje żądany współczynnik przenoszenia.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutsetminsize"></a><a name="setminsize"></a>CMFCDynamicLayout::SetMinSize

Ustawia rozmiar okna, poniżej którego układ nie jest dostosowywany.

```cpp
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Żądany rozmiar, poniżej którego układ nie jest regulowany.

### <a name="remarks"></a>Uwagi

Położenie i rozmiar formantu podrzędnego jest zmieniana dynamicznie, gdy zmieniana jest zmiana rozmiaru okna hostingu, ale istnieje minimalny rozmiar, poniżej którego układ nie jest dostosowywany. Użytkownik może zmienić rozmiar okna na mniejszy rozmiar, ale części okna są następnie ukryte przed widokiem.

## <a name="cmfcdynamiclayoutsizehorizontal"></a><a name="sizehorizontal"></a>CMFCDynamicLayout::SizeHorizontal

Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, jak bardzo formant podrzędny jest zmieniany w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.

```
static SizeSettings SizeHorizontal(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio (nRatio)*<br/>
Definiuje jako procent, jak daleko formant podrzędny jest zmieniany w poziomie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

A [SizeSettings](#sizesettings_structure) wartość, która hermetyzuje żądany współczynnik rozmiaru.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutsizehorizontalandvertical"></a><a name="sizehorizontalandvertical"></a>CMFCDynamicLayout::SizeHorizontalAndVertical

Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, jak bardzo formant podrzędny jest zmieniany w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.

```
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parametry

*nXRatio ( nXRatio )*<br/>
Definiuje jako procent, jak daleko formant podrzędny jest zmieniany w poziomie, gdy użytkownik zmienia rozmiar okna hosta.

*nYRatio*<br/>
Definiuje jako procent, jak daleko formant podrzędny jest zmieniany w pionie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

A [SizeSettings](#sizesettings_structure) wartość, która hermetyzuje żądany współczynnik rozmiaru.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutsizenone"></a><a name="sizenone"></a>CMFCDynamicLayout::SizeNone

Pobiera [SizeSettings](#sizesettings_structure) wartość, która reprezentuje nie zmiany rozmiaru formantu podrzędnego.

```
static SizeSettings SizeNone();
```

### <a name="return-value"></a>Wartość zwracana

A [SizeSettings](#sizesettings_structure) wartość, która rozwiązuje formant w określonym rozmiarze, tak aby nie zmieniał rozmiaru, jak użytkownik zmienia rozmiar okna hosta.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutsizesettings-structure"></a><a name="sizesettings_structure"></a>CMFCDynamicLayout::Struktura rozmiarówstawienia

Hermetyzuje dane zmiany rozmiaru dla formantów w układzie dynamicznym.

```
struct CMFCDynamicLayout::SizeSettings;
```

### <a name="remarks"></a>Uwagi

Jest to klasa zagnieżdżona wewnątrz `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout::SizeSettings::IsHorizontal

Sprawdza, czy dane zmiany rozmiaru określa niezerowej zmiany rozmiaru w poziomie.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Wartość zwracana

PRAWDA, `SizeSettings` jeśli obiekt określa niezerową zmiany rozmiaru poziomego.

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout::SizeSettings::IsNone

Sprawdza, czy dane o rozmiarze zmiany określa nie zmiany rozmiaru.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Wartość zwracana

PRAWDA, `SizeSettings` jeśli obiekt nie określa zmiany rozmiaru.

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout::SizeSettings::IsVertical

Sprawdza, czy dane zmiany rozmiaru określa niezerowej zmiany rozmiaru w pionie.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Wartość zwracana

PRAWDA, `SizeSettings` jeśli obiekt określa niezerową zmiany rozmiaru w pionie.

## <a name="cmfcdynamiclayoutsizevertical"></a><a name="sizevertical"></a>CMFCDynamicLayout::SizeVertical

Pobiera [SizeSettings](#sizesettings_structure) wartość, która definiuje, jak bardzo formant podrzędny jest zmieniany w pionie, gdy użytkownik zmienia rozmiar okna hostingu.

```
static SizeSettings SizeVertical(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio (nRatio)*<br/>
Definiuje jako procent, jak daleko formant podrzędny jest zmieniany w pionie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

A [SizeSettings](#sizesettings_structure) wartość, która hermetyzuje żądany współczynnik rozmiaru.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
