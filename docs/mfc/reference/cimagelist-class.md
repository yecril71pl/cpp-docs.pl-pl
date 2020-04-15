---
title: Klasa CImageList
ms.date: 11/04/2016
f1_keywords:
- CImageList
- AFXCMN/CImageList
- AFXCMN/CImageList::CImageList
- AFXCMN/CImageList::Add
- AFXCMN/CImageList::Attach
- AFXCMN/CImageList::BeginDrag
- AFXCMN/CImageList::Copy
- AFXCMN/CImageList::Create
- AFXCMN/CImageList::DeleteImageList
- AFXCMN/CImageList::DeleteTempMap
- AFXCMN/CImageList::Detach
- AFXCMN/CImageList::DragEnter
- AFXCMN/CImageList::DragLeave
- AFXCMN/CImageList::DragMove
- AFXCMN/CImageList::DragShowNolock
- AFXCMN/CImageList::Draw
- AFXCMN/CImageList::DrawEx
- AFXCMN/CImageList::DrawIndirect
- AFXCMN/CImageList::EndDrag
- AFXCMN/CImageList::ExtractIcon
- AFXCMN/CImageList::FromHandle
- AFXCMN/CImageList::FromHandlePermanent
- AFXCMN/CImageList::GetBkColor
- AFXCMN/CImageList::GetDragImage
- AFXCMN/CImageList::GetImageCount
- AFXCMN/CImageList::GetImageInfo
- AFXCMN/CImageList::GetSafeHandle
- AFXCMN/CImageList::Read
- AFXCMN/CImageList::Remove
- AFXCMN/CImageList::Replace
- AFXCMN/CImageList::SetBkColor
- AFXCMN/CImageList::SetDragCursorImage
- AFXCMN/CImageList::SetImageCount
- AFXCMN/CImageList::SetOverlayImage
- AFXCMN/CImageList::Write
- AFXCMN/CImageList::m_hImageList
helpviewer_keywords:
- CImageList [MFC], CImageList
- CImageList [MFC], Add
- CImageList [MFC], Attach
- CImageList [MFC], BeginDrag
- CImageList [MFC], Copy
- CImageList [MFC], Create
- CImageList [MFC], DeleteImageList
- CImageList [MFC], DeleteTempMap
- CImageList [MFC], Detach
- CImageList [MFC], DragEnter
- CImageList [MFC], DragLeave
- CImageList [MFC], DragMove
- CImageList [MFC], DragShowNolock
- CImageList [MFC], Draw
- CImageList [MFC], DrawEx
- CImageList [MFC], DrawIndirect
- CImageList [MFC], EndDrag
- CImageList [MFC], ExtractIcon
- CImageList [MFC], FromHandle
- CImageList [MFC], FromHandlePermanent
- CImageList [MFC], GetBkColor
- CImageList [MFC], GetDragImage
- CImageList [MFC], GetImageCount
- CImageList [MFC], GetImageInfo
- CImageList [MFC], GetSafeHandle
- CImageList [MFC], Read
- CImageList [MFC], Remove
- CImageList [MFC], Replace
- CImageList [MFC], SetBkColor
- CImageList [MFC], SetDragCursorImage
- CImageList [MFC], SetImageCount
- CImageList [MFC], SetOverlayImage
- CImageList [MFC], Write
- CImageList [MFC], m_hImageList
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
ms.openlocfilehash: eff2d0c1de88ebd9d949ebe197563c87c17e5b05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372449"
---
# <a name="cimagelist-class"></a>Klasa CImageList

Udostępnia funkcje kontrolki wspólnej listy obrazów systemu Windows.

## <a name="syntax"></a>Składnia

```
class CImageList : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CImageList::CImageList](#cimagelist)|Konstruuje `CImageList` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista CImage::Dodaj](#add)|Dodaje obraz lub obrazy do listy obrazów.|
|[CImageList::Dołącz](#attach)|Dołącza listę obrazów do `CImageList` obiektu.|
|[CImageList::BeginDrag](#begindrag)|Rozpoczyna przeciąganie obrazu.|
|[CImageList::Kopiuj](#copy)|Kopiuje obraz `CImageList` w obiekcie.|
|[CImageList::Tworzenie](#create)|Inicjuje listę obrazów i dołącza `CImageList` ją do obiektu.|
|[CImageList::DeleteImageList](#deleteimagelist)|Usuwa listę obrazów.|
|[CImageList::DeleteTempMap](#deletetempmap)|Wywoływany przez program obsługi [cwinapp](../../mfc/reference/cwinapp-class.md) w czasie `CImageList` bezczynnym, aby usunąć dowolny obiekt tymczasowy utworzony przez `FromHandle`.|
|[CImageList::Detach](#detach)|Odłącza obiekt listy obrazów `CImageList` od obiektu i zwraca uchwyt do listy obrazów.|
|[CImageList::DragEnter](#dragenter)|Blokuje aktualizacje podczas operacji przeciągania i wyświetla obraz przeciągania w określonym położeniu.|
|[CImageList::DragLeave](#dragleave)|Odblokowuje okno i ukrywa obraz przeciągania, dzięki czemu okno może zostać zaktualizowane.|
|[CImageList::DragMove](#dragmove)|Przenosi obraz przeciągany podczas operacji przeciągania i upuszczania.|
|[CImageList::DragShowNolock](#dragshownolock)|Pokazuje lub ukrywa obraz przeciągania podczas operacji przeciągania bez blokowania okna.|
|[CImageList::Draw](#draw)|Rysuje obraz przeciągany podczas operacji przeciągania i upuszczania.|
|[CImageList::DrawEx](#drawex)|Rysuje element listy obrazów w określonym kontekście urządzenia. Funkcja używa określonego stylu rysowania i miesza obraz z określonym kolorem.|
|[CImageList::DrawIndirect](#drawindirect)|Rysuje obraz z listy obrazów.|
|[CImageList::EndDrag](#enddrag)|Kończy operację przeciągania.|
|[CImageList::ExtractIcon](#extracticon)|Tworzy ikonę na podstawie obrazu i maski na liście obrazów.|
|[CImageList::FromHandle](#fromhandle)|Zwraca wskaźnik do `CImageList` obiektu po podaniu dojścia do listy obrazów. Jeśli `CImageList` obiekt nie jest dołączony do uchwytu, tworzony i dołączany jest obiekt tymczasowy. `CImageList`|
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|Zwraca wskaźnik do `CImageList` obiektu po podaniu dojścia do listy obrazów. Jeśli `CImageList` obiekt nie jest dołączony do dojścia, zwracana jest wartość NULL.|
|[CImageList::GetBkColor](#getbkcolor)|Pobiera bieżący kolor tła dla listy obrazów.|
|[Lista CImage::GetDragImage](#getdragimage)|Pobiera tymczasową listę obrazów, która jest używana do przeciągania.|
|[Lista CImage::GetImageCount](#getimagecount)|Pobiera liczbę obrazów na liście obrazów.|
|[Lista CImage::GetImageInfo](#getimageinfo)|Pobiera informacje o obrazie.|
|[CImageList::GetSafeHandle](#getsafehandle)|Pobiera `m_hImageList`plik .|
|[CImageList::Przeczytaj](#read)|Odczytuje listę obrazów z archiwum.|
|[CImageList::Usuń](#remove)|Usuwa obraz z listy obrazów.|
|[CImageList::Zamień](#replace)|Zastępuje obraz na liście obrazów nowym obrazem.|
|[CImageList::SetBkColor](#setbkcolor)|Ustawia kolor tła dla listy obrazów.|
|[CImageList::SetDragCursorImage](#setdragcursorimage)|Tworzy nowy obraz przeciągania.|
|[CImageList::SetImageCount](#setimagecount)|Resetuje liczbę obrazów na liście obrazów.|
|[CImageList::SetOverlayImage](#setoverlayimage)|Dodaje indeks obrazu o zerowym indeksie do listy obrazów, które mają być używane jako maski nakładek.|
|[CImageList::Napisz](#write)|Zapisuje listę obrazów do archiwum.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CImageList::operator HIMAGELIST](#operator_himagelist)|Zwraca himagelisty dołączone `CImageList`do .|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CImageList::m_hImageList](#m_himagelist)|Dojście zawierające listę obrazów dołączoną do tego obiektu.|

## <a name="remarks"></a>Uwagi

"Lista obrazów" to zbiór obrazów o tym samym rozmiarze, z których każdy może być określany przez indeks oparty na wartości zero. Listy obrazów służą do efektywnego zarządzania dużymi zestawami ikon lub map bitowych. Wszystkie obrazy na liście obrazów znajdują się w jednej, szerokiej mapie bitowej w formacie urządzenia ekranowego. Lista obrazów może również zawierać monochromatyczny bitmapa zawierająca maski używane do rysowania obrazów w sposób przezroczysty (styl ikony). Interfejs programowania aplikacji Microsoft Win32 (API) udostępnia funkcje listy obrazów, które umożliwiają rysowanie obrazów, tworzenie i niszczenie list obrazów, dodawanie i usuwanie obrazów, zastępowanie obrazów, scalanie obrazów i przeciąganie obrazów.

Ten formant (i `CImageList` dlatego klasa) jest dostępny tylko dla programów działających w systemach Windows 95/98 i Windows NT w wersji 3.51 lub nowszych.

Aby uzyskać więcej `CImageList`informacji na temat używania , zobacz [Formanty](../../mfc/controls-mfc.md) i [Korzystanie z listy CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="cimagelistadd"></a><a name="add"></a>Lista CImage::Dodaj

Wywołanie tej funkcji, aby dodać jeden lub więcej obrazów lub ikonę do listy obrazów.

```
int Add(
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Add(
    CBitmap* pbmImage,
    COLORREF crMask);

int Add(HICON hIcon);
```

### <a name="parameters"></a>Parametry

*pbmImage (obrazek)*<br/>
Wskaźnik do mapy bitowej zawierającej obraz lub obrazy. Liczba obrazów jest wywnioskowana z szerokości mapy bitowej.

*pbmMask*<br/>
Wskaźnik do mapy bitowej zawierającej maskę. Jeśli z listą obrazów nie jest używana żadna maska, ten parametr jest ignorowany.

*maska cr*<br/>
Kolor używany do generowania maski. Każdy piksel tego koloru na danej mapie bitowej jest zmieniany na czarny, a odpowiedni bit w masce jest ustawiony na jeden.

*hIcon (własówce)*<br/>
Uchwyt ikony zawierającej bitmapę i maskę dla nowego obrazu.

### <a name="return-value"></a>Wartość zwracana

Indeks oparty na wartości zerowej pierwszego nowego obrazu, jeśli zakończy się pomyślnie; w przeciwnym razie - 1.

### <a name="remarks"></a>Uwagi

Jesteś odpowiedzialny za zwolnienie uchwytu ikony, gdy skończysz z nim.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

## <a name="cimagelistattach"></a><a name="attach"></a>CImageList::Dołącz

Wywołanie tej funkcji, aby `CImageList` dołączyć listę obrazów do obiektu.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*lista hImage*<br/>
Dojście do obiektu listy obrazów.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli załącznik zakończył się pomyślnie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

## <a name="cimagelistbegindrag"></a><a name="begindrag"></a>CImageList::BeginDrag

Wywołanie tej funkcji, aby rozpocząć przeciąganie obrazu.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parametry

*nImage (Obraz)*<br/>
Indeks oparty na wartości zerowej obrazu do przeciągania.

*ptHotSpot (polski)*<br/>
Współrzędne początkowej pozycji przeciągania (zazwyczaj położenie kursora). Współrzędne są względem lewego górnego rogu obrazu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja tworzy tymczasową listę obrazów, która jest używana do przeciągania. Obraz łączy określony obraz i jego maskę z bieżącym kursorem. W odpowiedzi na kolejne komunikaty WM_MOUSEMOVE można przenieść `DragMove` obraz przeciągania za pomocą funkcji elementu członkowskiego. Aby zakończyć operację przeciągania, można użyć funkcji elementu `EndDrag` członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

## <a name="cimagelistcimagelist"></a><a name="cimagelist"></a>CImageList::CImageList

Konstruuje `CImageList` obiekt.

```
CImageList();
```

## <a name="cimagelistcopy"></a><a name="copy"></a>CImageList::Kopiuj

Ta funkcja elementu członkowskiego implementuje zachowanie [ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy)funkcji Win32, zgodnie z opisem w programie Windows SDK.

```
BOOL Copy(
    int iDst,
    int iSrc,
    UINT uFlags = ILCF_MOVE);

BOOL Copy(
    int iDst,
    CImageList* pSrc,
    int iSrc,
    UINT uFlags = ILCF_MOVE);
```

### <a name="parameters"></a>Parametry

*iDst ( iDst )*<br/>
Indeks od zera obrazu, który ma być używany jako miejsce docelowe operacji kopiowania.

*iSrc ( iSrc )*<br/>
Indeks od zera obrazu, który ma być używany jako źródło operacji kopiowania.

*żużle uFlags*<br/>
Wartość flagi bitowej określająca typ operacji kopiowania, która ma zostać wykonana. Ten parametr może być jedną z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|ILCF_MOVE|Obraz źródłowy jest kopiowany do indeksu obrazu docelowego. Ta operacja powoduje wiele wystąpień danego obrazu. ILCF_MOVE jest ustawieniem domyślnym.|
|ILCF_SWAP|Obrazy źródłowe i docelowe wymieniają pozycje na liście obrazów.|

*Psrc*<br/>
Wskaźnik do `CImageList` obiektu, który jest obiektem docelowym operacji kopiowania.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

## <a name="cimagelistcreate"></a><a name="create"></a>CImageList::Tworzenie

Inicjuje listę obrazów i dołącza ją do obiektu [CImageList.](../../mfc/reference/cimagelist-class.md)

```
BOOL Create(
    int cx,
    int cy,
    UINT nFlags,
    int nInitial,
    int nGrow);

BOOL Create(
    UINT nBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    LPCTSTR lpszBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    CImageList& imagelist1,
    int nImage1,
    CImageList& imagelist2,
    int nImage2,
    int dx,
    int dy);

BOOL Create(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*Cx*<br/>
Wymiary każdego obrazu w pikselach.

*Cy*<br/>
Wymiary każdego obrazu w pikselach.

*nPłgi*<br/>
Określa typ listy obrazów do utworzenia. Ten parametr może być kombinacją następujących wartości, ale może `ILC_COLOR` zawierać tylko jedną z wartości.

|Wartość|Znaczenie|
|-----------|-------------|
|ILC_COLOR|Użyj zachowania domyślnego, jeśli nie określono żadnej z innych flag ILC_COLOR*. Zazwyczaj wartość domyślna jest ILC_COLOR4; ale w przypadku starszych sterowników wyświetlacza domyślnie jest ILC_COLORDDB.|
|ILC_COLOR4|Użyj 4-bitowej (16-kolorowej) mapy bitowej (DIB) niezależnej od urządzenia jako mapy bitowej listy obrazów.|
|ILC_COLOR8|Użyj 8-bitowej sekcji DIB. Kolory używane dla tabeli kolorów są takie same kolory jak paleta półtonów.|
|ILC_COLOR16|Użyj sekcji DIB 16-bitowej (32/64k color).|
|ILC_COLOR24|Użyj 24-bitowej sekcji DIB.|
|ILC_COLOR32|Użyj 32-bitowej sekcji DIB.|
|ILC_COLORDDB|Użyj mapy bitowej zależnej od urządzenia.|
|ILC_MASK|Używa maski. Lista obrazów zawiera dwie mapy bitowe, z których jedna jest monochromatycznym bitmapą używaną jako maska. Jeśli ta wartość nie jest uwzględniona, lista obrazów zawiera tylko jedną mapę bitową. Aby uzyskać dodatkowe informacje na temat zamaskowanych obrazów, zobacz [Rysowanie obrazów z listy obrazów.](../../mfc/drawing-images-from-an-image-list.md)|

*nInitial (w tym ziw.*<br/>
Liczba obrazów, które początkowo zawiera lista obrazów.

*nGrow ( nGrow )*<br/>
Liczba obrazów, za pomocą których lista obrazów może rosnąć, gdy system musi zmienić rozmiar listy, aby zrobić miejsce dla nowych obrazów. Ten parametr reprezentuje liczbę nowych obrazów, które może zawierać lista obrazów o przeliczonej omioń.

*nBitmapID*<br/>
Identyfikatory zasobów mapy bitowej, która ma być skojarzona z listą obrazów.

*maska cr*<br/>
Kolor używany do generowania maski. Każdy piksel tego koloru w określonej mapie bitowej jest zmieniany na czarny, a odpowiedni bit w masce jest ustawiony na jeden.

*lpszBitmapID*<br/>
Ciąg zawierający identyfikatory zasobów obrazów.

*lista obrazów1*<br/>
Odwołanie do `CImageList` obiektu.

*nImage1*<br/>
Indeks pierwszego istniejącego obrazu.

*lista obrazów2*<br/>
Odwołanie do `CImageList` obiektu.

*nImage2*<br/>
Indeks drugiego istniejącego obrazu.

*Dx*<br/>
Przesunięcie osi x drugiego obrazu w relacji z pierwszym obrazem w pikselach.

*Dy*<br/>
Przesunięcie osi y drugiego obrazu w relacji z pierwszym obrazem w pikselach.

*pImageList (Lista pImage)*<br/>
Wskaźnik do `CImageList` obiektu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruujesz `CImageList` w dwóch krokach. Najpierw wywołaj konstruktora, a następnie wywołaj `Create`, który `CImageList` tworzy listę obrazów i dołącza ją do obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

## <a name="cimagelistdeleteimagelist"></a><a name="deleteimagelist"></a>CImageList::DeleteImageList

Wywołanie tej funkcji, aby usunąć listę obrazów.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

## <a name="cimagelistdeletetempmap"></a><a name="deletetempmap"></a>CImageList::DeleteTempMap

Wywoływane automatycznie `CWinApp` przez program obsługi czasu `DeleteTempMap` bezczynności, `CImageList` usuwa wszystkie obiekty tymczasowe utworzone przez [FromHandle](#fromhandle), ale nie niszczy żadnych uchwytów ( `hImageList`) tymczasowo skojarzonych z `ImageList` obiektami.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

## <a name="cimagelistdetach"></a><a name="detach"></a>CImageList::Detach

Wywołanie tej funkcji, aby odłączyć obiekt listy obrazów od `CImageList` obiektu.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu listy obrazów.

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca dojście do obiektu listy obrazów.

### <a name="example"></a>Przykład

  Zobacz przykład [dla CImageList::Attach](#attach).

## <a name="cimagelistdragenter"></a><a name="dragenter"></a>CImageList::DragEnter

Podczas operacji przeciągania blokuje aktualizacje do okna określonego przez *pWndLock* i wyświetla obraz przeciągania w pozycji określonej przez *punkt*.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWndLock (Blokada pWndLock)*<br/>
Wskaźnik do okna, w które znajduje się obraz przeciągania.

*Punkt*<br/>
Położenie, w którym ma być wyświetlany obraz przeciągania. Współrzędne są względem lewego górnego rogu okna (nie obszaru klienta).

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Współrzędne są względem lewego górnego rogu okna, więc podczas określania współrzędnych należy kompensować szerokości elementów okna, takich jak obramowanie, pasek tytułu i pasek menu.

Jeśli *pWndLock* ma wartość NULL, ta funkcja rysuje obraz w kontekście wyświetlania skojarzonym z oknem pulpitu, a współrzędne są względem lewego górnego rogu ekranu.

Ta funkcja blokuje wszystkie inne aktualizacje do danego okna podczas operacji przeciągania. Jeśli konieczne jest zrobienie dowolnego rysunku podczas operacji przeciągania, na przykład wyróżniania obiektu docelowego operacji przeciągania i upuszczania, można tymczasowo ukryć przeciągany obraz za pomocą funkcji [CImageList::Dleleave.](#dragleave)

### <a name="example"></a>Przykład

  Zobacz przykład [CImageList::BeginDrag](#begindrag).

## <a name="cimagelistdragleave"></a><a name="dragleave"></a>CImageList::DragLeave

Odblokowuje okno określone przez *pWndLock* i ukrywa obraz przeciągania, umożliwiając zaktualizowanie okna.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>Parametry

*pWndLock (Blokada pWndLock)*<br/>
Wskaźnik do okna, w które znajduje się obraz przeciągania.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CImageList::EndDrag](#enddrag).

## <a name="cimagelistdragmove"></a><a name="dragmove"></a>CImageList::DragMove

Wywołanie tej funkcji, aby przenieść obraz, który jest przeciągany podczas operacji przeciągania i upuszczania.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Nowa pozycja przeciągania.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana w odpowiedzi na komunikat WM_MOUSEMOVE. Aby rozpocząć operację przeciągania, należy użyć funkcji elementu `BeginDrag` członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

## <a name="cimagelistdragshownolock"></a><a name="dragshownolock"></a>CImageList::DragShowNolock

Pokazuje lub ukrywa obraz przeciągania podczas operacji przeciągania bez blokowania okna.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bPokaż*<br/>
Określa, czy obraz przeciągania ma być wyświetlany.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

[Funkcja CImageList::DragEnter](#dragenter) blokuje wszystkie aktualizacje okna podczas operacji przeciągania. Ta funkcja nie blokuje jednak okna.

## <a name="cimagelistdraw"></a><a name="draw"></a>CImageList::Draw

Wywołanie tej funkcji, aby narysować obraz, który jest przeciągany podczas operacji przeciągania i upuszczania.

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia docelowego.

*nImage (Obraz)*<br/>
Indeks oparty na wartości zerowej obrazu do rysowania.

*Pt*<br/>
Lokalizacja, w której można rysować w określonym kontekście urządzenia.

*styl nStyle*<br/>
Flaga określająca styl rysunku. Może to być jedna lub więcej z tych wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|Rysuje obraz, mieszając 25 procent z kolorem podświetlenia systemu. Ta wartość nie ma wpływu, jeśli lista obrazów nie zawiera maski.|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|Rysuje obraz, mieszając 50 procent z kolorem podświetlenia systemu. Ta wartość nie ma wpływu, jeśli lista obrazów nie zawiera maski.|
|ILD_MASK|Rysuje maskę.|
|ILD_NORMAL|Rysuje obraz przy użyciu koloru tła dla listy obrazów. Jeśli kolor tła jest wartością CLR_NONE, obraz jest rysowany w sposób przezroczysty za pomocą maski.|
|ILD_TRANSPARENT|Rysuje obraz w sposób przezroczysty za pomocą maski, niezależnie od koloru tła.|

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CImageList::SetOverlayImage](#setoverlayimage).

## <a name="cimagelistdrawex"></a><a name="drawex"></a>CImageList::DrawEx

Rysuje element listy obrazów w określonym kontekście urządzenia.

```
BOOL DrawEx(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    COLORREF clrBk,
    COLORREF clrFg,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia docelowego.

*nImage (Obraz)*<br/>
Indeks oparty na wartości zerowej obrazu do rysowania.

*Pt*<br/>
Lokalizacja, w której można rysować w określonym kontekście urządzenia.

*Sz*<br/>
Rozmiar części obrazu do rysowania względem lewego górnego rogu obrazu. Zobacz *dx* i *dy* w [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) w windows SDK.

*clrBk ( clrBk )*<br/>
Kolor tła obrazu. Zobacz *rgbBk* w [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) w Windows SDK.

*clrFg*<br/>
Kolor obrazu na pierwszym planie. Zobacz *rgbFg* w [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) w Windows SDK.

*styl nStyle*<br/>
Flaga określająca styl rysunku. Zobacz *fStyle* w [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja używa określonego stylu rysowania i miesza obraz z określonym kolorem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

## <a name="cimagelistdrawindirect"></a><a name="drawindirect"></a>CImageList::DrawIndirect

Wywołanie tej funkcji elementu członkowskiego, aby narysować obraz z listy obrazów.

```
BOOL DrawIndirect(IMAGELISTDRAWPARAMS* pimldp);

BOOL DrawIndirect(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    POINT ptOrigin,
    UINT fStyle = ILD_NORMAL,
    DWORD dwRop = SRCCOPY,
    COLORREF rgbBack = CLR_DEFAULT,
    COLORREF rgbFore = CLR_DEFAULT,
    DWORD fState = ILS_NORMAL,
    DWORD Frame = 0,
    COLORREF crEffect = CLR_DEFAULT);
```

### <a name="parameters"></a>Parametry

*pimldp*<br/>
Wskaźnik do struktury [IMAGELISTDRAWPARAMS,](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) który zawiera informacje o operacji rysowania.

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia docelowego. Należy usunąć ten obiekt [CDC,](../../mfc/reference/cdc-class.md) gdy skończysz z nim.

*nImage (Obraz)*<br/>
Indeks od zera obrazu, który ma zostać narysowany.

*Pt*<br/>
Struktura [POINT](/previous-versions/dd162805\(v=vs.85\)) zawierająca współrzędne x i y, w których zostanie narysowany obraz.

*Sz*<br/>
Struktura [SIZE](/windows/win32/api/windef/ns-windef-size) wskazująca rozmiar rysowanego obrazu.

*ptOrigin (polski)*<br/>
Struktura [POINT](/previous-versions/dd162805\(v=vs.85\)) zawierająca współrzędne x i y określające lewy górny róg operacji rysowania w odniesieniu do samego obrazu. Piksele obrazu, które znajdują się po lewej stronie współrzędnej x i powyżej współrzędnej y, nie są rysowane.

*fStyle*<br/>
Flaga określająca styl rysowania i opcjonalnie obraz nakładki. Zobacz sekcję Uwagi, aby uzyskać informacje na temat obrazu nakładki. Domyślna implementacja MFC, ILD_NORMAL, rysuje obraz przy użyciu koloru tła dla listy obrazów. Jeśli kolor tła jest wartością CLR_NONE, obraz jest rysowany w sposób przezroczysty za pomocą maski.

Inne możliwe style są opisane w obszarze *fStyle* element członkowski [imagelistdrawparams](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) struktury.

*dwRop (dwRop)*<br/>
Wartość określająca kod operacji rastrowej. Kody te określają, w jaki sposób dane kolorów prostokąta źródłowego będą łączone z danymi kolorów prostokąta docelowego w celu uzyskania ostatecznego koloru. Domyślna implementacja MFC, SRCCOPY, kopiuje prostokąt źródłowy bezpośrednio do prostokąta docelowego. Ten parametr jest ignorowany, jeśli parametr *fStyle* nie zawiera flagi ILD_ROP.

Inne możliwe wartości są opisane w obszarze *dwRop* element członkowski [imagelistdrawparams](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) struktury.

*rgbBack*<br/>
Kolor tła obrazu, domyślnie CLR_DEFAULT. Ten parametr może być zdefiniowaną przez aplikację wartością RGB lub jedną z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|CLR_DEFAULT|Domyślny kolor tła. Obraz jest rysowany przy użyciu koloru tła listy obrazów.|
|CLR_NONE|Brak koloru tła. Obraz jest rysowany w sposób przezroczysty.|

*rgbFore*<br/>
Kolor pierwszego planu obrazu, domyślnie CLR_DEFAULT. Ten parametr może być zdefiniowaną przez aplikację wartością RGB lub jedną z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|CLR_DEFAULT|Domyślny kolor pierwszego planu. Obraz jest rysowany przy użyciu koloru podświetlenia systemowego jako koloru pierwszego planu.|
|CLR_NONE|Brak koloru mieszanego. Obraz jest mieszany z kolorem kontekstu urządzenia docelowego.|

Ten parametr jest używany tylko wtedy, *gdy fStyle* zawiera flagę ILD_BLEND25 lub ILD_BLEND50.

*fPaństwo*<br/>
Flaga określająca stan rysunku. Ten element członkowski może zawierać co najmniej jedną flagę stanu listy obrazów.

*Klatka*<br/>
Wpływa na zachowanie efektów nasycenia i mieszania alfa.

W przypadku użycia z ILS_SATURATE, ten element członkowski przechowuje wartość dodaną do każdego składnika koloru trójki RGB dla każdego piksela w ikonie.

W przypadku użycia z ILS_APLHA, ten element członkowski przechowuje wartość kanału alfa. Wartość ta może wynosić od 0 do 255, przy czym 0 jest całkowicie przezroczyste, a 255 jest całkowicie nieprzezroczyste.

*efektu crEffect*<br/>
Wartość [COLORREF](/windows/win32/gdi/colorref) używana do efektów blasku i cienia.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obraz został pomyślnie narysowany; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj pierwszej wersji, jeśli chcesz samodzielnie wypełnić strukturę Win32. Użyj drugiej wersji, jeśli chcesz skorzystać z jednego lub więcej domyślnych argumentów MFC lub uniknąć zarządzania strukturą.

Obraz nakładki jest obrazem rysowanym na obrazie podstawowym, określonym w tej funkcji elementu członkowskiego przez parametr *nImage.* Narysuj maskę nakładki za pomocą funkcji [Rysuj](#draw) element członkowski z indeksem opartym na jednej masce nakładki określonym przy użyciu makra [INDEXTOOVERLAYMASK.](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

## <a name="cimagelistenddrag"></a><a name="enddrag"></a>CImageList::EndDrag

Wywołanie tej funkcji, aby zakończyć operację przeciągania.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Uwagi

Aby rozpocząć operację przeciągania, należy użyć funkcji elementu `BeginDrag` członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

## <a name="cimagelistextracticon"></a><a name="extracticon"></a>CImageList::ExtractIcon

Wywołanie tej funkcji, aby utworzyć ikonę na podstawie obrazu i związanej z nim maski na liście obrazów.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Parametry

*nImage (Obraz)*<br/>
Indeks obrazu oparty na wartości zerowej.

### <a name="return-value"></a>Wartość zwracana

Uchwyt ikony, jeśli się powiedzie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ta metoda opiera się na zachowaniu [makra ImageList_ExtractIcon,](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) aby utworzyć ikonę. Więcej informacji na temat tworzenia i oczyszczania ikon można znaleźć w [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) makra.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

## <a name="cimagelistfromhandle"></a><a name="fromhandle"></a>CImageList::FromHandle

Zwraca wskaźnik do `CImageList` obiektu po podaniu dojścia do listy obrazów.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*lista hImage*<br/>
Określa listę obrazów.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CImageList` obiektu, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CImageList` a nie jest jeszcze dołączony do `CImageList` dojścia, obiekt tymczasowy jest tworzony i dołączany. Ten `CImageList` obiekt tymczasowy jest prawidłowy tylko do następnego czasu, gdy aplikacja ma czas bezczynny w pętli zdarzeń, w którym to czasie wszystkie obiekty tymczasowe są usuwane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

## <a name="cimagelistfromhandlepermanent"></a><a name="fromhandlepermanent"></a>CImageList::FromHandlePermanent

Zwraca wskaźnik do `CImageList` obiektu po podaniu dojścia do listy obrazów.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*lista hImage*<br/>
Określa listę obrazów.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CImageList` obiektu, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CImageList` obiekt nie jest dołączony do dojścia, zwracana jest wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

## <a name="cimagelistgetbkcolor"></a><a name="getbkcolor"></a>CImageList::GetBkColor

Wywołanie tej funkcji, aby pobrać bieżący kolor tła dla listy obrazów.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość koloru RGB `CImageList` koloru tła obiektu.

### <a name="example"></a>Przykład

  Zobacz przykład [dla CImageList::SetBkColor](#setbkcolor).

## <a name="cimagelistgetdragimage"></a><a name="getdragimage"></a>Lista CImage::GetDragImage

Pobiera tymczasową listę obrazów, która jest używana do przeciągania.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Parametry

*lpPoint (punkt z punktu widzenia*<br/>
Adres struktury [POINT,](/previous-versions/dd162805\(v=vs.85\)) która odbiera bieżącą pozycję przeciągania.

*lpPointHotSpot*<br/>
Adres `POINT` struktury, która odbiera odsunięcie obrazu przeciągania względem pozycji przeciągania.

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, wskaźnik do tymczasowej listy obrazów, który jest używany do przeciągania; w przeciwnym razie NULL.

## <a name="cimagelistgetimagecount"></a><a name="getimagecount"></a>Lista CImage::GetImageCount

Wywołanie tej funkcji, aby pobrać liczbę obrazów na liście obrazów.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba obrazów.

### <a name="example"></a>Przykład

  Zobacz przykład [dla CImageList::ExtractIcon](#extracticon).

## <a name="cimagelistgetimageinfo"></a><a name="getimageinfo"></a>Lista CImage::GetImageInfo

Wywołanie tej funkcji, aby pobrać informacje o obrazie.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>Parametry

*nImage (Obraz)*<br/>
Indeks obrazu oparty na wartości zerowej.

*pImageInfo*<br/>
Wskaźnik do struktury [IMAGEINFO,](/windows/win32/api/commctrl/ns-commctrl-imageinfo) która odbiera informacje o obrazie. Informacje w tej strukturze mogą służyć do bezpośredniego manipulowania mapami bitowymi obrazu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Struktura `IMAGEINFO` zawiera informacje o obrazie na liście obrazów.

## <a name="cimagelistgetsafehandle"></a><a name="getsafehandle"></a>CImageList::GetSafeHandle

Wywołanie tej funkcji, `m_hImageList` aby pobrać element członkowski danych.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do załączonej listy obrazów; w przeciwnym razie NULL, jeśli żaden obiekt nie jest dołączony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

## <a name="cimagelistm_himagelist"></a><a name="m_himagelist"></a>CImageList::m_hImageList

Uchwyt listy obrazów dołączonych do tego obiektu.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Uwagi

Element `m_hImageList` członkowski danych jest zmienną publiczną typu HIMAGELIST.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

## <a name="cimagelistoperator-himagelist"></a><a name="operator_himagelist"></a>CImageList::operator HIMAGELIST

Ten operator służy do uzyskania dołączonego uchwytu `CImageList` obiektu.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, dojście do `CImageList` listy obrazów reprezentowanych przez obiekt; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatorem odlewniczym, który obsługuje bezpośrednie wykorzystanie obiektu HIMAGELIST.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

## <a name="cimagelistread"></a><a name="read"></a>CImageList::Przeczytaj

Wywołanie tej funkcji, aby odczytać listę obrazów z archiwum.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Parametry

*pArchive (Rodo)*<br/>
Wskaźnik do `CArchive` obiektu, z którego ma być odczytywana lista obrazów.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

## <a name="cimagelistremove"></a><a name="remove"></a>CImageList::Usuń

Wywołanie tej funkcji, aby usunąć obraz z obiektu listy obrazów.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>Parametry

*nImage (Obraz)*<br/>
Indeks oparty na wartości zerowej obrazu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wszystkie elementy następujące *nImage* teraz przenieść w dół o jedną pozycję. Na przykład jeśli lista obrazów zawiera dwa elementy, usunięcie pierwszego elementu spowoduje, że pozostały element będzie teraz na pierwszej pozycji. *nImage*=0 dla towaru na pierwszej pozycji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

## <a name="cimagelistreplace"></a><a name="replace"></a>CImageList::Zamień

Wywołanie tej funkcji, aby zastąpić obraz na liście obrazów nowym obrazem.

```
BOOL Replace(
    int nImage,
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Replace(
    int nImage,
    HICON hIcon);
```

### <a name="parameters"></a>Parametry

*nImage (Obraz)*<br/>
Indeks oparty na wartości zerowej obrazu do zastąpienia.

*pbmImage (obrazek)*<br/>
Wskaźnik do mapy bitowej zawierającej obraz.

*pbmMask*<br/>
Wskaźnik do mapy bitowej zawierającej maskę. Jeśli z listą obrazów nie jest używana żadna maska, ten parametr jest ignorowany.

*hIcon (własówce)*<br/>
Uchwyt do ikony zawierającej bitmapę i maskę dla nowego obrazu.

### <a name="return-value"></a>Wartość zwracana

Wersja zwracająca BOOL zwraca wartość niezerową, jeśli zakończy się pomyślnie; w przeciwnym razie 0.

Wersja zwracająca **int** zwraca indeks oparty na wartości zerowej obrazu, jeśli się powiedzie; w przeciwnym razie - 1.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego po wywołaniu [SetImageCount](#setimagecount) przypisać nowe, prawidłowe obrazy do zastępczych numerów indeksu obrazu.

### <a name="example"></a>Przykład

  Zobacz przykład [dla CImageList::SetImageCount](#setimagecount).

## <a name="cimagelistsetbkcolor"></a><a name="setbkcolor"></a>CImageList::SetBkColor

Wywołanie tej funkcji, aby ustawić kolor tła dla listy obrazów.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parametry

*Cr*<br/>
Kolor tła do skonfigurowania. Można go CLR_NONE. W takim przypadku obrazy są rysowane w sposób przezroczysty za pomocą maski.

### <a name="return-value"></a>Wartość zwracana

Poprzedni kolor tła, jeśli się powiedzie; w przeciwnym razie CLR_NONE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

## <a name="cimagelistsetdragcursorimage"></a><a name="setdragcursorimage"></a>CImageList::SetDragCursorImage

Tworzy nowy obraz przeciągania, łącząc dany obraz (zazwyczaj obraz kursora myszy) z bieżącym obrazem przeciągania.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parametry

*nDrag ( nDrag )*<br/>
Indeks nowego obrazu, który ma być połączony z obrazem przeciągania.

*ptHotSpot (polski)*<br/>
Położenie punktu gorąca w nowym obrazie.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ponieważ funkcje przeciągania używają nowego obrazu podczas operacji przeciągania, należy użyć funkcji [Windows ShowCursor,](/windows/win32/api/winuser/nf-winuser-showcursor) aby ukryć rzeczywisty kursor myszy po wywołaniu `CImageList::SetDragCursorImage`. W przeciwnym razie system może wydawać się mieć dwa kursory myszy na czas trwania operacji przeciągania.

## <a name="cimagelistsetimagecount"></a><a name="setimagecount"></a>CImageList::SetImageCount

Wywołanie tej funkcji elementu członkowskiego, `CImageList` aby zresetować liczbę obrazów w obiekcie.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Parametry

*uNewCount (Liczba nienaliczonych)*<br/>
Wartość określająca nową całkowitą liczbę obrazów na liście obrazów.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Jeśli wywołasz tę funkcję elementu członkowskiego, aby zwiększyć liczbę obrazów na liście obrazów, a następnie [wywołać Zamień](#replace) dla każdego dodatkowego obrazu, aby przypisać nowe indeksy do prawidłowych obrazów. Jeśli nie uda ci się przypisać indeksów do prawidłowych obrazów, operacje rysowania, które tworzą nowe obrazy, będą nieprzewidywalne.

Jeśli zmniejszysz rozmiar listy obrazów za pomocą tej funkcji, obcięty obrazy zostaną zwolnione.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

## <a name="cimagelistsetoverlayimage"></a><a name="setoverlayimage"></a>CImageList::SetOverlayImage

Wywołanie tej funkcji, aby dodać indeks od zera obrazu do listy obrazów, które mają być używane jako maski nakładek.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Parametry

*nImage (Obraz)*<br/>
Indeks obrazu od zera, który ma być używany jako maska nakładki.

*nPrzejazd*<br/>
Indeks nakładki na podstawie jednego.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Do listy można dodać maksymalnie cztery indeksy.

Maska nakładki to obraz narysowany w sposób przezroczysty nad innym obrazem. Narysuj maskę nakładki nad obrazem za pomocą funkcji elementu członkowskiego [CImageList::Draw](#draw) z indeksem opartym na masce nakładki określonym przy użyciu makra INDEXTOOVERLAYMASK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

## <a name="cimagelistwrite"></a><a name="write"></a>CImageList::Napisz

Wywołanie tej funkcji, aby zapisać obiekt listy obrazów do archiwum.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Parametry

*pArchive (Rodo)*<br/>
Wskaźnik do `CArchive` obiektu, w którym ma być przechowywana lista obrazów.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)<br/>
[Klasa CTabCtrl](../../mfc/reference/ctabctrl-class.md)
