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
ms.openlocfilehash: 1c5d73897f7028768476c82824f8c0b6d530aea2
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742908"
---
# <a name="cmfcdynamiclayout-class"></a>Klasa CMFCDynamicLayout

Określa sposób przenoszenia i zmiany rozmiaru kontrolek w oknie, gdy użytkownik zmienia rozmiar okna.

## <a name="syntax"></a>Składnia

```
class CMFCDynamicLayout : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCDynamicLayout::CMFCDynamicLayout`|Konstruuje `CMFCDynamicLayout` obiekt.|
|`CMFCDynamicLayout::~CMFCDynamicLayout`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDynamicLayout:: AddItem](#additem)|Dodaje okno podrzędne, zazwyczaj kontrolkę, do listy okien, które są kontrolowane przez Menedżera układu dynamicznego.|
|[CMFCDynamicLayout:: Dopasuj](#adjust)|Dodaje okno podrzędne, zazwyczaj kontrolkę, do listy okien, które są kontrolowane przez Menedżera układu dynamicznego.|
|[CMFCDynamicLayout:: Create](#create)|Zapisuje i sprawdza poprawność okna hosta.|
|[CMFCDynamicLayout:: GetHostWnd](#gethostwnd)|Zwraca wskaźnik do okna hosta.|
|[CMFCDynamicLayout:: GetMinSize](#getminsize)|Zwraca rozmiar okna, poniżej którego układ nie jest dostosowany.|
|[CMFCDynamicLayout:: GetWindowRect](#getwindowrect)|Pobiera prostokąt dla bieżącego obszaru klienta okna.|
|[CMFCDynamicLayout:: HasItem](#hasitem)|Sprawdza, czy formant podrzędny został dodany do układu dynamicznego.|
|[CMFCDynamicLayout:: IsEmpty](#isempty)|Sprawdza, czy układ dynamiczny nie ma dodanych podrzędnych okien.|
|[CMFCDynamicLayout:: LoadResource](#loadresource)|Odczytuje układ dynamiczny z AFX_DIALOG_LAYOUT zasobu, a następnie stosuje układ do okna hosta.|
|statyczny [CMFCDynamicLayout:: MoveHorizontal](#movehorizontal)|Pobiera wartość [MoveSettings](#movesettings_structure) , która definiuje, jak dużo kontrolki podrzędnej jest przenoszona w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.|
|statyczny [CMFCDynamicLayout:: MoveHorizontalAndVertical](#movehorizontalandvertical)|Pobiera wartość [MoveSettings](#movesettings_structure) , która definiuje, jak dużo kontrolki podrzędnej jest przenoszona w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.|
|statyczny [CMFCDynamicLayout:: MoveNone](#movenone)|Pobiera wartość [MoveSettings](#movesettings_structure) , która reprezentuje brak ruchu, pionowo lub poziomo dla formantu podrzędnego.|
|statyczny [CMFCDynamicLayout:: MoveVertical](#movevertical)|Pobiera wartość [MoveSettings](#movesettings_structure) , która definiuje, jak dużo kontrolki podrzędnej jest przenoszona w pionie, gdy użytkownik zmienia rozmiar okna hostingu.|
|[CMFCDynamicLayout:: SetMinSize](#setminsize)|Ustawia rozmiar okna, poniżej którego układ nie jest dostosowywany.|
|statyczny [CMFCDynamicLayout:: SizeHorizontal](#sizehorizontal)|Pobiera wartość [SizeSettings —](#sizesettings_structure) , która określa, ile czasu formant podrzędny jest zmieniany w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.|
|statyczny [CMFCDynamicLayout:: SizeHorizontalAndVertical](#sizehorizontalandvertical)|Pobiera wartość [SizeSettings —](#sizesettings_structure) , która określa, ile czasu formant podrzędny jest zmieniany w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.|
|statyczny [CMFCDynamicLayout:: SizeNone](#sizenone)|Pobiera wartość [SizeSettings —](#sizesettings_structure) , która reprezentuje brak zmian w rozmiarze dla formantu podrzędnego.|
|statyczny [CMFCDynamicLayout:: SizeVertical](#sizevertical)|Pobiera wartość [SizeSettings —](#sizesettings_structure) , która definiuje, jak dużo kontrolki podrzędnej jest zmieniana w pionie, gdy użytkownik zmienia rozmiar okna hostingu.|

## <a name="nested-types"></a>Zagnieżdżone typy

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDynamicLayout:: MoveSettings, struktura](#movesettings_structure)|Hermetyzuje przenoszenie danych dla kontrolek w układzie dynamicznym.|
|[CMFCDynamicLayout:: SizeSettings —, struktura](#sizesettings_structure)|Hermetyzuje zmiany rozmiaru dla kontrolek w układzie dynamicznym.|

## <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxlayout. h

## <a name="cmfcdynamiclayoutadditem"></a><a name="additem"></a> CMFCDynamicLayout:: AddItem

Dodaje okno podrzędne, zazwyczaj kontrolkę, do listy okien, które są kontrolowane przez Menedżera układu dynamicznego.

```
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
Uchwyt do okna do dodania.

*nID*<br/>
Identyfikator formantu podrzędnego do dodania.

*moveSettings*<br/>
Struktura opisująca, jak zmienia się rozmiar okna.

*SizeSettings —*<br/>
Struktura opisująca sposób zmiany rozmiaru kontrolki w miarę zmieniania rozmiaru okna.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli element został pomyślnie dodany; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Położenie i rozmiar kontrolki podrzędnej jest zmieniany dynamicznie w przypadku zmiany rozmiaru okna hostowania.

## <a name="cmfcdynamiclayoutadjust"></a><a name="adjust"></a> CMFCDynamicLayout:: Dopasuj

Dodaje okno podrzędne, zazwyczaj kontrolkę, do listy okien, które są kontrolowane przez Menedżera układu dynamicznego.

```cpp
void Adjust();
```

### <a name="remarks"></a>Uwagi

Położenie i rozmiar kontrolki podrzędnej jest zmieniany dynamicznie w przypadku zmiany rozmiaru okna hostowania.

## <a name="cmfcdynamiclayoutcreate"></a><a name="create"></a> CMFCDynamicLayout:: Create

Zapisuje i sprawdza poprawność okna hosta.

```
BOOL Create(CWnd* pHostWnd);
```

### <a name="parameters"></a>Parametry

*pHostWnd*<br/>
Wskaźnik do okna hosta.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli tworzenie powiodło się; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutgethostwnd"></a><a name="gethostwnd"></a> CMFCDynamicLayout:: GetHostWnd

Zwraca wskaźnik do okna hosta.

```
CWnd* GetHostWnd();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna hosta.

### <a name="remarks"></a>Uwagi

Domyślnie wszystkie pozycje formantu podrzędnego obliczone ponownie względem tego okna.

## <a name="cmfcdynamiclayoutgetminsize"></a><a name="getminsize"></a> CMFCDynamicLayout:: GetMinSize

Zwraca rozmiar okna, poniżej którego układ nie jest dostosowany.

```
CSize GetMinSize();
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar okna, poniżej którego układ nie został dostosowany.

### <a name="remarks"></a>Uwagi

Położenie i rozmiar kontrolki podrzędnej jest zmieniany dynamicznie w przypadku zmiany rozmiaru okna hostowania, ale istnieje minimalny rozmiar, poniżej którego układ nie jest dostosowywany. Użytkownik może zmienić rozmiar okna na mniejszy, ale części okna są następnie ukryte z widoku.

## <a name="cmfcdynamiclayoutgetwindowrect"></a><a name="getwindowrect"></a> CMFCDynamicLayout:: GetWindowRect

Pobiera prostokąt dla bieżącego obszaru klienta okna.

```cpp
void GetHostWndRect(CRect& rect,);
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
Po powrocie funkcji ten parametr zawiera prostokąt ograniczenia obszaru układu. Jest to parametr out; wartość wejściowa jest zastępowana.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayouthasitem"></a><a name="hasitem"></a> CMFCDynamicLayout:: HasItem

Sprawdza, czy formant podrzędny został dodany do układu dynamicznego.

```
BOOL HasItem(HWND hwnd);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
Uchwyt okna dla kontrolki.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli układ ma już ten element; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutisempty"></a><a name="isempty"></a> CMFCDynamicLayout:: IsEmpty

Sprawdza, czy układ dynamiczny nie ma dodanych podrzędnych okien.

```
BOOL IsEmpty();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli układ nie zawiera elementów; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutloadresource"></a><a name="loadresource"></a> CMFCDynamicLayout:: LoadResource

Odczytuje układ dynamiczny z AFX_DIALOG_LAYOUT zasobu, a następnie stosuje układ do okna hosta.

```
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);
```

### <a name="parameters"></a>Parametry

*pHostWnd*<br/>
Wskaźnik do okna hosta.

*lpResource*<br/>
Wskaźnik do buforu zawierającego zasób AFX_DIALOG_LAYOUT.

*dwSize*<br/>
Rozmiar buforu w bajtach.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli zasób jest ładowany i stosowany do okna hosta; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutmovehorizontal"></a><a name="movehorizontal"></a> CMFCDynamicLayout:: MoveHorizontal

Pobiera wartość [MoveSettings](#movesettings_structure) , która definiuje, jak dużo kontrolki podrzędnej jest przenoszona w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.

```
static MoveSettings MoveHorizontal(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Definiuje jako wartość procentową, o ile formant podrzędny jest przenoszony w poziomie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

Wartość [MoveSettings](#movesettings_structure) , która hermetyzuje żądany współczynnik przenoszenia.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutmovehorizontalandvertical"></a><a name="movehorizontalandvertical"></a> CMFCDynamicLayout:: MoveHorizontalAndVertical

Pobiera wartość [MoveSettings](#movesettings_structure) , która definiuje, jak dużo kontrolki podrzędnej jest przenoszona w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.

```
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parametry

*nXRatio*<br/>
Definiuje jako wartość procentową, o ile formant podrzędny jest przenoszony w poziomie, gdy użytkownik zmienia rozmiar okna hosta.

*nYRatio*<br/>
Definiuje jako wartość procentową, o ile formant podrzędny jest przenoszony w pionie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

Wartość [MoveSettings](#movesettings_structure) , która hermetyzuje żądany współczynnik przenoszenia.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutmovenone"></a><a name="movenone"></a> CMFCDynamicLayout:: MoveNone

Pobiera wartość [MoveSettings](#movesettings_structure) , która reprezentuje brak ruchu, pionowo lub poziomo dla formantu podrzędnego.

```
static MoveSettings MoveNone();
```

### <a name="return-value"></a>Wartość zwracana

Wartość [MoveSettings](#movesettings_structure) , która naprawia zastosowanej kontrolki, tak aby nie była przenoszona, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutmovesettings-structure"></a><a name="movesettings_structure"></a> CMFCDynamicLayout:: MoveSettings, struktura

Hermetyzuje przenoszenie danych dla kontrolek w układzie dynamicznym.

```
struct CMFCDynamicLayout::MoveSettings;
```

### <a name="remarks"></a>Uwagi

Jest to Klasa zagnieżdżona wewnątrz `CMFCDynamicLayout` .

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout:: MoveSettings:: ispoziome

Sprawdź, czy Przenieś dane określają przechodzenie w poziomie różny od zera.

```
BOOL IsHorizontal() const
```

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli `MoveSettings` obiekt Określa niezerowe przesunięcie w poziomie.

## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout:: MoveSettings:: IsNone

Sprawdź, czy przeniesienie danych nie określa przenoszenia.

```
BOOL IsNone() const
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli `MoveSettings` obiekt nie określa przenoszenia.

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout:: MoveSettings:: ispionowy

Sprawdź, czy Przenieś dane określają niezerowe przesunięcie w pionie.

```
BOOL IsVertical() const
```

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli `MoveSettings` obiekt Określa niezerowe przesunięcie w pionie.

## <a name="cmfcdynamiclayoutmovevertical"></a><a name="movevertical"></a> CMFCDynamicLayout:: MoveVertical

Pobiera wartość [MoveSettings](#movesettings_structure) , która definiuje, jak dużo kontrolki podrzędnej jest przenoszona w pionie, gdy użytkownik zmienia rozmiar okna hostingu.

```
static MoveSettings MoveVertical(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Definiuje jako wartość procentową, o ile formant podrzędny jest przenoszony w pionie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

Wartość [MoveSettings](#movesettings_structure) , która hermetyzuje żądany współczynnik przenoszenia.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutsetminsize"></a><a name="setminsize"></a> CMFCDynamicLayout:: SetMinSize

Ustawia rozmiar okna, poniżej którego układ nie jest dostosowywany.

```cpp
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
Żądany rozmiar, poniżej którego układ nie został dostosowany.

### <a name="remarks"></a>Uwagi

Położenie i rozmiar kontrolki podrzędnej jest zmieniany dynamicznie w przypadku zmiany rozmiaru okna hostowania, ale istnieje minimalny rozmiar, poniżej którego układ nie jest dostosowywany. Użytkownik może zmienić rozmiar okna na mniejszy, ale części okna są następnie ukryte z widoku.

## <a name="cmfcdynamiclayoutsizehorizontal"></a><a name="sizehorizontal"></a> CMFCDynamicLayout:: SizeHorizontal

Pobiera wartość [SizeSettings —](#sizesettings_structure) , która określa, ile czasu formant podrzędny jest zmieniany w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.

```
static SizeSettings SizeHorizontal(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Definiuje jako wartość procentową rozmiaru formantu podrzędnego w poziomie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

Wartość [SizeSettings —](#sizesettings_structure) , która hermetyzuje żądany Współczynnik rozmiaru.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutsizehorizontalandvertical"></a><a name="sizehorizontalandvertical"></a> CMFCDynamicLayout:: SizeHorizontalAndVertical

Pobiera wartość [SizeSettings —](#sizesettings_structure) , która określa, ile czasu formant podrzędny jest zmieniany w poziomie, gdy użytkownik zmienia rozmiar okna hostingu.

```
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Parametry

*nXRatio*<br/>
Definiuje jako wartość procentową rozmiaru formantu podrzędnego w poziomie, gdy użytkownik zmienia rozmiar okna hosta.

*nYRatio*<br/>
Definiuje jako wartość procentową zmiany rozmiaru formantu podrzędnego w pionie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

Wartość [SizeSettings —](#sizesettings_structure) , która hermetyzuje żądany Współczynnik rozmiaru.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutsizenone"></a><a name="sizenone"></a> CMFCDynamicLayout:: SizeNone

Pobiera wartość [SizeSettings —](#sizesettings_structure) , która reprezentuje brak zmian w rozmiarze dla formantu podrzędnego.

```
static SizeSettings SizeNone();
```

### <a name="return-value"></a>Wartość zwracana

Wartość [SizeSettings —](#sizesettings_structure) , która naprawia formant w określonym rozmiarze, dzięki czemu nie zmienia rozmiaru okna hosta.

### <a name="remarks"></a>Uwagi

## <a name="cmfcdynamiclayoutsizesettings-structure"></a><a name="sizesettings_structure"></a> CMFCDynamicLayout:: SizeSettings —, struktura

Hermetyzuje zmiany rozmiaru dla kontrolek w układzie dynamicznym.

```
struct CMFCDynamicLayout::SizeSettings;
```

### <a name="remarks"></a>Uwagi

Jest to Klasa zagnieżdżona wewnątrz `CMFCDynamicLayout` .

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout:: SizeSettings —:: ispoziome

Sprawdza, czy dane zmiany rozmiaru określają niezerową zmianę rozmiaru w poziomie.

```
BOOL IsHorizontal() const
```

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli `SizeSettings` obiekt Określa niezerową zmianę w poziomie.

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout:: SizeSettings —:: IsNone

Sprawdza, czy dane zmiany rozmiaru nie określają zmiany rozmiaru.

```
BOOL IsNone() const
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli `SizeSettings` obiekt nie określa zmiany rozmiarów.

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout:: SizeSettings —:: ispionowy

Sprawdza, czy dane zmiany rozmiaru określają niezerową zmianę rozmiaru w pionie.

```
BOOL IsVertical() const
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli `SizeSettings` obiekt Określa niezerową zmianę rozmiarów w pionie.

## <a name="cmfcdynamiclayoutsizevertical"></a><a name="sizevertical"></a> CMFCDynamicLayout:: SizeVertical

Pobiera wartość [SizeSettings —](#sizesettings_structure) , która definiuje, jak dużo kontrolki podrzędnej jest zmieniana w pionie, gdy użytkownik zmienia rozmiar okna hostingu.

```
static SizeSettings SizeVertical(int nRatio);
```

### <a name="parameters"></a>Parametry

*nRatio*<br/>
Definiuje jako wartość procentową zmiany rozmiaru formantu podrzędnego w pionie, gdy użytkownik zmienia rozmiar okna hosta.

### <a name="return-value"></a>Wartość zwracana

Wartość [SizeSettings —](#sizesettings_structure) , która hermetyzuje żądany Współczynnik rozmiaru.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
