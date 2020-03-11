---
title: Klasa korzystanie CImageList
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
ms.openlocfilehash: 1555209ce0f1c2caacbfb4b01107775db948d230
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890710"
---
# <a name="cimagelist-class"></a>Klasa korzystanie CImageList

Oferuje funkcje formantu Common Image list systemu Windows.

## <a name="syntax"></a>Składnia

```
class CImageList : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Korzystanie CImageList:: Korzystanie CImageList](#cimagelist)|Konstruuje obiekt `CImageList`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Korzystanie CImageList:: Add](#add)|Dodaje obraz lub obrazy do listy obrazów.|
|[Korzystanie CImageList:: Attach](#attach)|Dołącza listę obrazów do obiektu `CImageList`.|
|[Korzystanie CImageList:: BeginDrag](#begindrag)|Rozpoczyna przeciąganie obrazu.|
|[Korzystanie CImageList:: Copy](#copy)|Kopiuje obraz w ramach obiektu `CImageList`.|
|[Korzystanie CImageList:: Create](#create)|Inicjuje listę obrazów i dołącza ją do obiektu `CImageList`.|
|[Korzystanie CImageList::D eleteImageList](#deleteimagelist)|Usuwa listę obrazów.|
|[Korzystanie CImageList::D eleteTempMap](#deletetempmap)|Wywoływane przez [CWinApp](../../mfc/reference/cwinapp-class.md) procedurę obsługi bezczynności w celu usunięcia dowolnego tymczasowego obiektu `CImageList` utworzonego przez `FromHandle`.|
|[Korzystanie CImageList::D etach](#detach)|Odłącza obiekt listy obrazów z obiektu `CImageList` i zwraca dojście do listy obrazów.|
|[Korzystanie CImageList::D ragEnter](#dragenter)|Blokuje aktualizacje w trakcie operacji przeciągania i wyświetla obraz przeciągnij na określonej pozycji.|
|[Korzystanie CImageList::D ragLeave](#dragleave)|Odblokowuje okno i ukrywa obraz przeciągnij, aby można było zaktualizować okno.|
|[Korzystanie CImageList::D ragMove](#dragmove)|Przenosi obraz, który jest przeciągany podczas operacji przeciągania i upuszczania.|
|[Korzystanie CImageList::D ragShowNolock](#dragshownolock)|Pokazuje lub ukrywa obraz przeciągany podczas operacji przeciągania bez blokowania okna.|
|[Korzystanie CImageList::D RAW](#draw)|Rysuje obraz, który jest przeciągany podczas operacji przeciągania i upuszczania.|
|[Korzystanie CImageList::D rawEx](#drawex)|Rysuje element listy obrazów w określonym kontekście urządzenia. Funkcja używa określonego stylu rysowania i miesza obraz z określonym kolorem.|
|[Korzystanie CImageList::D rawIndirect](#drawindirect)|Rysuje obraz z listy obrazów.|
|[Korzystanie CImageList:: EndDrag](#enddrag)|Zamyka operację przeciągania.|
|[Korzystanie CImageList:: ExtractIcon](#extracticon)|Tworzy ikonę na podstawie obrazu i maski na liście obrazów.|
|[Korzystanie CImageList:: FromHandle](#fromhandle)|Zwraca wskaźnik do obiektu `CImageList`, gdy ma dojść do listy obrazów. Jeśli obiekt `CImageList` nie jest dołączony do dojścia, zostanie utworzony i dołączony tymczasowy obiekt `CImageList`.|
|[Korzystanie CImageList:: FromHandlePermanent](#fromhandlepermanent)|Zwraca wskaźnik do obiektu `CImageList`, gdy ma dojść do listy obrazów. Jeśli obiekt `CImageList` nie jest dołączony do dojścia, zwracana jest wartość NULL.|
|[Korzystanie CImageList:: GetBkColor](#getbkcolor)|Pobiera bieżący kolor tła listy obrazów.|
|[Korzystanie CImageList:: GetDragImage](#getdragimage)|Pobiera listę obrazów tymczasowych, która jest używana do przeciągania.|
|[Korzystanie CImageList:: GetImageCount](#getimagecount)|Pobiera liczbę obrazów z listy obrazów.|
|[Korzystanie CImageList:: GetImageInfo](#getimageinfo)|Pobiera informacje o obrazie.|
|[Korzystanie CImageList:: GetSafeHandle](#getsafehandle)|Pobiera klasę `m_hImageList`.|
|[Korzystanie CImageList:: Read](#read)|Odczytuje listę obrazów z archiwum.|
|[Korzystanie CImageList:: Remove](#remove)|Usuwa obraz z listy obrazów.|
|[Korzystanie CImageList:: Replace](#replace)|Zamienia obraz na liście obrazów na nowy obraz.|
|[Korzystanie CImageList:: SetBkColor](#setbkcolor)|Ustawia kolor tła listy obrazów.|
|[Korzystanie CImageList:: SetDragCursorImage](#setdragcursorimage)|Tworzy nowy obraz przeciągania.|
|[Korzystanie CImageList:: SetImageCount](#setimagecount)|Resetuje liczbę obrazów na liście obrazów.|
|[Korzystanie CImageList:: SetOverlayImage](#setoverlayimage)|Dodaje indeks obrazu (liczony od zera) do listy obrazów, które mają być używane jako maski nakładania.|
|[Korzystanie CImageList:: Write](#write)|Zapisuje listę obrazów w archiwum.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Korzystanie CImageList:: operator HIMAGELIST](#operator_himagelist)|Zwraca HIMAGELIST dołączony do `CImageList`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[Korzystanie CImageList:: m_hImageList](#m_himagelist)|Dojście zawierające listę obrazów dołączoną do tego obiektu.|

## <a name="remarks"></a>Uwagi

"Lista obrazów" jest kolekcją obrazów o takim samym rozmiarze, z których każdy może być określony przez swój indeks (liczony od zera). Listy obrazów służą do wydajnego zarządzania dużymi zestawami ikon lub map bitowych. Wszystkie obrazy na liście obrazów są zawarte w jednej, szerokiej mapie bitowej w formacie urządzenia ekranowego. Lista obrazów może również zawierać mapę bitową monochromatyczny, która zawiera maski używane do rysowania obrazów w sposób przezroczysty (styl ikon). Interfejs programowania aplikacji (API) systemu Microsoft Win32 udostępnia funkcje listy obrazów, które umożliwiają rysowanie obrazów, tworzenie i niszczenie list obrazów, Dodawanie i usuwanie obrazów, zastępowanie obrazów, scalanie obrazów i przeciąganie obrazów.

Ten formant (i w związku z tym Klasa `CImageList`) jest dostępny tylko dla programów uruchomionych w systemach Windows 95/98 i Windows NT w wersji 3,51 lub nowszej.

Aby uzyskać więcej informacji na temat używania `CImageList`, zobacz [Controls](../../mfc/controls-mfc.md) and [using korzystanie CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

##  <a name="add"></a>Korzystanie CImageList:: Add

Wywołaj tę funkcję, aby dodać do listy obrazów co najmniej jeden obraz lub ikonę.

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

*pbmImage*<br/>
Wskaźnik do mapy bitowej zawierającej obraz lub obrazy. Liczba obrazów jest wywnioskowana na podstawie szerokości mapy bitowej.

*pbmMask*<br/>
Wskaźnik do mapy bitowej zawierającej maskę. Jeśli na liście obrazów nie jest używana żadna maska, ten parametr jest ignorowany.

*crMask*<br/>
Kolor używany do generowania maski. Każdy piksel tego koloru w danej mapie bitowej jest zmieniany na czarny, a odpowiedni bit w masce jest ustawiony na jeden.

*hIcon*<br/>
Uchwyt ikony zawierającej mapę bitową i maskę dla nowego obrazu.

### <a name="return-value"></a>Wartość zwracana

Indeksowanie pierwszego nowego obrazu (liczony od zera); w przeciwnym razie-1.

### <a name="remarks"></a>Uwagi

Użytkownik jest odpowiedzialny za zwolnienie uchwytu ikony po jego zakończeniu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

##  <a name="attach"></a>Korzystanie CImageList:: Attach

Wywołaj tę funkcję, aby dołączyć listę obrazów do obiektu `CImageList`.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hImageList*<br/>
Uchwyt do obiektu listy obrazów.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli załącznik zakończył się pomyślnie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

##  <a name="begindrag"></a>Korzystanie CImageList:: BeginDrag

Wywołaj tę funkcję, aby rozpocząć przeciąganie obrazu.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parametry

*Nokreślono*<br/>
Indeks obrazu, który ma być przeciągany od zera.

*ptHotSpot*<br/>
Współrzędne początkowej pozycji przeciągania (zazwyczaj położenie kursora). Współrzędne są względne w lewym górnym rogu obrazu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja tworzy listę obrazów tymczasowych, która jest używana do przeciągania. Obraz łączy określony obraz i jego maskę z bieżącym kursorem. W odpowiedzi na kolejne WM_MOUSEMOVE komunikaty można przenieść obraz przeciągany przy użyciu funkcji elementu członkowskiego `DragMove`. Aby zakończyć operację przeciągania, można użyć funkcji składowej `EndDrag`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

##  <a name="cimagelist"></a>Korzystanie CImageList:: Korzystanie CImageList

Konstruuje obiekt `CImageList`.

```
CImageList();
```

##  <a name="copy"></a>Korzystanie CImageList:: Copy

Ta funkcja członkowska implementuje zachowanie funkcji Win32 [ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy), zgodnie z opisem w Windows SDK.

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

*iDst*<br/>
Indeks (liczony od zera) obrazu, który ma być używany jako miejsce docelowe operacji kopiowania.

*iSrc*<br/>
Indeks (liczony od zera) obrazu, który ma być używany jako źródło operacji kopiowania.

*uFlags*<br/>
Wartość flagi bitowej, która określa typ operacji kopiowania, która ma zostać wykonana. Ten parametr może mieć jedną z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|ILCF_MOVE|Obraz źródłowy jest kopiowany do indeksu obrazu docelowego. Ta operacja powoduje wystąpienie wielu wystąpień danego obrazu. ILCF_MOVE jest wartością domyślną.|
|ILCF_SWAP|Obrazy źródłowe i docelowe są wymieniane na liście obrazów.|

*pSrc*<br/>
Wskaźnik do obiektu `CImageList`, który jest obiektem docelowym operacji kopiowania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

##  <a name="create"></a>Korzystanie CImageList:: Create

Inicjuje listę obrazów i dołącza ją do obiektu [Korzystanie CImageList](../../mfc/reference/cimagelist-class.md) .

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

*CX*<br/>
Wymiary każdego obrazu (w pikselach).

*cy*<br/>
Wymiary każdego obrazu (w pikselach).

*nFlags*<br/>
Określa typ listy obrazów do utworzenia. Ten parametr może być kombinacją następujących wartości, ale może zawierać tylko jedną z wartości `ILC_COLOR`.

|Wartość|Znaczenie|
|-----------|-------------|
|ILC_COLOR|Użyj zachowania domyślnego, jeśli nie określono żadnego z innych ILC_COLOR * flagi. Zazwyczaj wartość domyślna to ILC_COLOR4; Jednak w przypadku starszych sterowników wyświetlania wartością domyślną jest ILC_COLORDDB.|
|ILC_COLOR4|Użyj 4-bitowej (16-kolorów) niezależnej od urządzenia mapy bitowej (DIB) jako mapy bitowej dla listy obrazów.|
|ILC_COLOR8|Użyj 8-bitowej sekcji DIB. Kolory używane dla tabeli Color są takie same jak kolory palety półtonów.|
|ILC_COLOR16|Użyj 16-bitowej (32/64-bitowego koloru) DIB sekcji.|
|ILC_COLOR24|Użyj 24-bitowej sekcji DIB.|
|ILC_COLOR32|Użyj 32-bitowej DIB sekcji.|
|ILC_COLORDDB|Użyj mapy bitowej zależnej od urządzenia.|
|ILC_MASK|Używa maski. Lista obrazów zawiera dwie mapy bitowe, z których jedna to mapa bitowa monochromatyczny używana jako maska. Jeśli ta wartość nie jest uwzględniona, lista obrazów będzie zawierać tylko jedną mapę bitową. Zobacz [Rysowanie obrazów z listy obrazów,](../../mfc/drawing-images-from-an-image-list.md) Aby uzyskać dodatkowe informacje na temat zamaskowanych obrazów.|

*nInitial*<br/>
Liczba obrazów, które początkowo zawiera lista obrazów.

*nGrow*<br/>
Liczba obrazów, za pomocą których lista obrazów może się rozwijać, gdy system musi zmienić rozmiar listy, aby zwolnić miejsce na nowe obrazy. Ten parametr reprezentuje liczbę nowych obrazów, które może zawierać lista obrazów o zmienionym rozmiarze.

*nBitmapID*<br/>
Identyfikatory zasobów mapy bitowej, które mają być skojarzone z listą obrazów.

*crMask*<br/>
Kolor używany do generowania maski. Każdy piksel tego koloru w określonej mapie bitowej jest zmieniany na czarny, a odpowiedni bit w masce jest ustawiony na jeden.

*lpszBitmapID*<br/>
Ciąg zawierający identyfikatory zasobów obrazów.

*imagelist1*<br/>
Odwołanie do obiektu `CImageList`.

*nImage1*<br/>
Indeks pierwszego istniejącego obrazu.

*imagelist2*<br/>
Odwołanie do obiektu `CImageList`.

*nImage2*<br/>
Indeks drugiego istniejącego obrazu.

*DX*<br/>
Przesunięcie osi x drugiego obrazu w relacji do pierwszego obrazu (w pikselach).

*dy*<br/>
Przesunięcie osi y drugiego obrazu w relacji do pierwszego obrazu (w pikselach).

*pImageList*<br/>
Wskaźnik do obiektu `CImageList`.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Należy skonstruować `CImageList` w dwóch krokach. Najpierw Wywołaj konstruktora, a następnie Wywołaj `Create`, który tworzy listę obrazów i dołącza go do obiektu `CImageList`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

##  <a name="deleteimagelist"></a>Korzystanie CImageList::D eleteImageList

Wywołaj tę funkcję, aby usunąć listę obrazów.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

##  <a name="deletetempmap"></a>Korzystanie CImageList::D eleteTempMap

Wywoływana automatycznie przez `CWinApp` procedury obsługi czasu bezczynności, `DeleteTempMap` usuwa wszystkie tymczasowe obiekty `CImageList` utworzone przez [FromHandle](#fromhandle), ale nie niszczy żadnych dojść (`hImageList`) tymczasowo skojarzonych z obiektami `ImageList`.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

##  <a name="detach"></a>Korzystanie CImageList::D etach

Wywołaj tę funkcję, aby odłączyć obiekt listy obrazów od obiektu `CImageList`.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do obiektu listy obrazów.

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca uchwyt do obiektu listy obrazów.

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CImageList:: Attach](#attach).

##  <a name="dragenter"></a>Korzystanie CImageList::D ragEnter

Podczas operacji przeciągania program blokuje aktualizacje okna określonego przez *pWndLock* i wyświetla obraz przeciągnij na pozycji określonej przez *punkt*.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWndLock*<br/>
Wskaźnik do okna, które jest właścicielem obrazu przeciągania.

*moment*<br/>
Położenie, w którym ma być wyświetlany obraz przeciągania. Współrzędne są względem górnego lewego rogu okna (a nie obszaru klienckiego).

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Współrzędne są względne w lewym górnym rogu okna, dlatego należy zrekompensować szerokości elementów okna, takich jak obramowanie, pasek tytułu i pasek menu, podczas określania współrzędnych.

Jeśli *pWndLock* ma wartość null, ta funkcja rysuje obraz w kontekście wyświetlania skojarzonym z oknem pulpitu, a współrzędne są względne w lewym górnym rogu ekranu.

Ta funkcja blokuje wszystkie pozostałe aktualizacje danego okna podczas operacji przeciągania. Jeśli musisz wykonać dowolny rysunek podczas operacji przeciągania, na przykład podświetlić obiekt docelowy operacji przeciągania i upuszczania, możesz tymczasowo ukryć przeciągany obraz przy użyciu funkcji [Korzystanie CImageList::D ragleave](#dragleave) .

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CImageList:: BeginDrag](#begindrag).

##  <a name="dragleave"></a>Korzystanie CImageList::D ragLeave

Umożliwia odblokowanie okna określonego przez *pWndLock* i ukrycie obrazu przeciągania, co umożliwia zaktualizowanie okna.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>Parametry

*pWndLock*<br/>
Wskaźnik do okna, które jest właścicielem obrazu przeciągania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CImageList:: endDrag](#enddrag).

##  <a name="dragmove"></a>Korzystanie CImageList::D ragMove

Wywołaj tę funkcję, aby przenieść obraz, który jest przeciągany podczas operacji przeciągania i upuszczania.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Parametry

*zmiennoprzecinkow*<br/>
Nowa pozycja przeciągania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana w odpowiedzi na komunikat WM_MOUSEMOVE. Aby rozpocząć operację przeciągania, użyj funkcji składowej `BeginDrag`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

##  <a name="dragshownolock"></a>Korzystanie CImageList::D ragShowNolock

Pokazuje lub ukrywa obraz przeciągany podczas operacji przeciągania bez blokowania okna.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Określa, czy obraz przeciągnięcia ma być pokazywany.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja [Korzystanie CImageList::D ragenter](#dragenter) blokuje wszystkie aktualizacje okna podczas operacji przeciągania. Ta funkcja nie blokuje jednak okna.

##  <a name="draw"></a>Korzystanie CImageList::D RAW

Wywołaj tę funkcję, aby narysować obraz, który jest przeciągany podczas operacji przeciągania i upuszczania.

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
Wskaźnik do kontekstu urządzenia docelowego.

*Nokreślono*<br/>
Indeks obrazu, który ma być rysowany od zera.

*zmiennoprzecinkow*<br/>
Lokalizacja do rysowania w określonym kontekście urządzenia.

*nStyle*<br/>
Flaga określająca styl rysowania. Może to być co najmniej jedna z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|Rysuje obraz, mieszając 25 procent z kolorem wyróżnienia systemu. Ta wartość nie działa, jeśli lista obrazów nie zawiera maski.|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|Rysuje obraz, mieszając 50 procent z kolorem wyróżnienia systemu. Ta wartość nie działa, jeśli lista obrazów nie zawiera maski.|
|ILD_MASK|Rysuje maskę.|
|ILD_NORMAL|Rysuje obraz przy użyciu koloru tła listy obrazów. Jeśli kolor tła jest wartością CLR_NONE, obraz jest rysowany w sposób przezroczysty przy użyciu maski.|
|ILD_TRANSPARENT|Rysuje obraz w sposób przezroczysty przy użyciu maski, niezależnie od koloru tła.|

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CImageList:: SetOverlayImage](#setoverlayimage).

##  <a name="drawex"></a>Korzystanie CImageList::D rawEx

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

*Domeny*<br/>
Wskaźnik do kontekstu urządzenia docelowego.

*Nokreślono*<br/>
Indeks obrazu, który ma być rysowany od zera.

*zmiennoprzecinkow*<br/>
Lokalizacja do rysowania w określonym kontekście urządzenia.

*sz*<br/>
Rozmiar części obrazu do rysowania względem lewego górnego rogu obrazu. Zobacz *DX* i *dy* w [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) w Windows SDK.

*clrBk*<br/>
Kolor tła obrazu. Zobacz *rgbBk* w [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) w Windows SDK.

*clrFg*<br/>
Kolor pierwszego planu obrazu. Zobacz *rgbFg* w [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) w Windows SDK.

*nStyle*<br/>
Flaga określająca styl rysowania. Zobacz *fStyle* w [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja używa określonego stylu rysowania i miesza obraz z określonym kolorem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

##  <a name="drawindirect"></a>Korzystanie CImageList::D rawIndirect

Wywołaj tę funkcję elementu członkowskiego, aby narysować obraz z listy obrazów.

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
Wskaźnik do struktury [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) , który zawiera informacje o operacji rysowania.

*Domeny*<br/>
Wskaźnik do kontekstu urządzenia docelowego. Ten obiekt [przechwytywania](../../mfc/reference/cdc-class.md) zmian należy usunąć po zakończeniu pracy z nim.

*Nokreślono*<br/>
Indeks (liczony od zera) obrazu do narysowania.

*zmiennoprzecinkow*<br/>
Struktura [punktu](/previous-versions/dd162805\(v=vs.85\)) zawierającego współrzędne x i y, w których zostanie narysowany obraz.

*sz*<br/>
Struktura [rozmiaru](/windows/win32/api/windef/ns-windef-size) wskazująca rozmiar obrazu do narysowania.

*ptOrigin*<br/>
Struktura [punktu](/previous-versions/dd162805\(v=vs.85\)) zawierającego współrzędne x i y określające górny lewy róg operacji rysowania w odniesieniu do samego obrazu. Piksele obrazu, które znajdują się po lewej stronie współrzędnej x i powyżej współrzędnej y nie są rysowane.

*fStyle*<br/>
Flaga określania stylu rysowania i, opcjonalnie, obrazu nakładki. Zapoznaj się z sekcją uwagi, aby uzyskać informacje na temat obrazu nakładki. Domyślna implementacja MFC, ILD_NORMAL, rysuje obraz przy użyciu koloru tła listy obrazów. Jeśli kolor tła jest wartością CLR_NONE, obraz jest rysowany w sposób przezroczysty przy użyciu maski.

Inne możliwe style są opisane poniżej elementu członkowskiego *fStyle* struktury [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) .

*dwRop*<br/>
Wartość określająca kod operacji rastrowej. Te kody definiują sposób łączenia danych koloru dla prostokąta źródłowego z danymi koloru dla prostokąta docelowego w celu uzyskania końcowego koloru. Domyślna implementacja MFC, SRCCOPY, kopiuje prostokąt źródłowy bezpośrednio do prostokąta docelowego. Ten parametr jest ignorowany, jeśli parametr *fStyle* nie zawiera flagi ILD_ROP.

Inne możliwe wartości są opisane poniżej elementu członkowskiego *dwRop* struktury [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) .

*rgbBack*<br/>
Kolor tła obrazu, domyślnie CLR_DEFAULT. Ten parametr może być zdefiniowaną przez aplikację wartością RGB lub jedną z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|CLR_DEFAULT|Domyślny kolor tła. Obraz jest rysowany przy użyciu koloru tła listy obrazu.|
|CLR_NONE|Brak koloru tła. Obraz jest rysowany jako przezroczysty.|

*rgbFore*<br/>
Kolor pierwszego planu obrazu, domyślnie CLR_DEFAULT. Ten parametr może być zdefiniowaną przez aplikację wartością RGB lub jedną z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|CLR_DEFAULT|Domyślny kolor pierwszego planu. Obraz jest rysowany przy użyciu koloru wyróżnienia systemu jako koloru pierwszego planu.|
|CLR_NONE|Brak koloru mieszania. Obraz jest mieszany z kolorem kontekstu urządzenia docelowego.|

Ten parametr jest używany tylko wtedy, gdy *fStyle* zawiera flagę ILD_BLEND25 lub ILD_BLEND50.

*fState*<br/>
Flaga określająca stan rysowania. Ten element członkowski może zawierać co najmniej jedną flagę stanu listy obrazu.

*Ramka*<br/>
Wpływa na zachowanie funkcji nasycenia i efektów mieszania alfa.

Gdy jest używany z ILS_SATURATE, ten element członkowski przechowuje wartość dodaną do każdego koloru składnika RGB tryplet dla każdego piksela w ikonie.

Gdy jest używany z ILS_APLHA, ten element członkowski przechowuje wartość kanału alfa. Wartość ta może wynosić od 0 do 255, z 0 jest całkowicie przezroczyste i 255 jest całkowicie nieprzezroczysty.

*crEffect*<br/>
Wartość [COLORREF](/windows/win32/gdi/colorref) używana dla efektów blask i cień.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli obraz został pomyślnie narysowany; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj pierwszej wersji, jeśli chcesz samodzielnie wypełnić strukturę Win32. Użyj drugiej wersji, jeśli chcesz korzystać z jednego lub większej liczby domyślnych argumentów MFC lub uniknąć zarządzania strukturą.

Obraz nakładki jest obrazem, który jest rysowany na początku obrazu podstawowego, określonym w tej funkcji elementu członkowskiego przez parametr *nokreślono* . Narysuj maskę nakładki przy użyciu funkcji [rysowania](#draw) elementu członkowskiego z jednym indeksem maski nakładki określonej przy użyciu makra [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

##  <a name="enddrag"></a>Korzystanie CImageList:: EndDrag

Wywołaj tę funkcję, aby zakończyć operację przeciągania.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Uwagi

Aby rozpocząć operację przeciągania, użyj funkcji składowej `BeginDrag`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

##  <a name="extracticon"></a>Korzystanie CImageList:: ExtractIcon

Wywołaj tę funkcję, aby utworzyć ikonę opartą na obrazie i pokrewnej masce na liście obrazów.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Parametry

*Nokreślono*<br/>
Indeks obrazu liczony od zera.

### <a name="return-value"></a>Wartość zwracana

Uchwyt ikony, jeśli się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ta metoda opiera się na zachowaniu makra [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) , aby utworzyć ikonę. Aby uzyskać więcej informacji na temat tworzenia i czyszczenia ikon, zapoznaj się z makrem [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

##  <a name="fromhandle"></a>Korzystanie CImageList:: FromHandle

Zwraca wskaźnik do obiektu `CImageList`, gdy ma dojść do listy obrazów.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hImageList*<br/>
Określa listę obrazów.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu `CImageList`, jeśli się to powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CImageList` nie jest jeszcze dołączona do dojścia, zostaje utworzony i dołączony tymczasowy obiekt `CImageList`. Ten tymczasowy `CImageList` obiektu jest prawidłowy tylko do następnego czasu bezczynności aplikacji w pętli zdarzeń, w którym wszystkie obiekty tymczasowe są usuwane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

##  <a name="fromhandlepermanent"></a>Korzystanie CImageList:: FromHandlePermanent

Zwraca wskaźnik do obiektu `CImageList`, gdy ma dojść do listy obrazów.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hImageList*<br/>
Określa listę obrazów.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu `CImageList`, jeśli się to powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli obiekt `CImageList` nie jest dołączony do dojścia, zwracana jest wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

##  <a name="getbkcolor"></a>Korzystanie CImageList:: GetBkColor

Wywołaj tę funkcję, aby pobrać bieżący kolor tła dla listy obrazów.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość koloru RGB koloru tła obiektu `CImageList`.

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CImageList:: SetBkColor](#setbkcolor).

##  <a name="getdragimage"></a>Korzystanie CImageList:: GetDragImage

Pobiera listę obrazów tymczasowych, która jest używana do przeciągania.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Parametry

*lpPoint*<br/>
Adres struktury [punktu](/previous-versions/dd162805\(v=vs.85\)) , który odbiera bieżącą pozycję przeciągania.

*lpPointHotSpot*<br/>
Adres struktury `POINT`, która odbiera przesunięcie obrazu przeciągania względem pozycji przeciągania.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, wskaźnik do listy obrazów tymczasowych, który jest używany do przeciągania; w przeciwnym razie wartość NULL.

##  <a name="getimagecount"></a>Korzystanie CImageList:: GetImageCount

Wywołaj tę funkcję, aby pobrać liczbę obrazów z listy obrazów.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba obrazów.

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CImageList:: ExtractIcon](#extracticon).

##  <a name="getimageinfo"></a>Korzystanie CImageList:: GetImageInfo

Wywołaj tę funkcję, aby pobrać informacje o obrazie.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>Parametry

*Nokreślono*<br/>
Indeks obrazu liczony od zera.

*pImageInfo*<br/>
Wskaźnik do struktury [IMAGEINFO](/windows/win32/api/commctrl/ns-commctrl-imageinfo) , która otrzymuje informacje o obrazie. Informacje w tej strukturze mogą służyć do bezpośredniego manipulowania mapami bitowymi obrazu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Struktura `IMAGEINFO` zawiera informacje o obrazie na liście obrazów.

##  <a name="getsafehandle"></a>Korzystanie CImageList:: GetSafeHandle

Wywołaj tę funkcję, aby pobrać element członkowski danych `m_hImageList`.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do listy dołączonych obrazów; w przeciwnym razie wartość NULL, jeśli żaden obiekt nie jest dołączony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

##  <a name="m_himagelist"></a>Korzystanie CImageList:: m_hImageList

Dojście do listy obrazów dołączone do tego obiektu.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Uwagi

Element członkowski danych `m_hImageList` jest publiczną zmienną typu HIMAGELIST.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

##  <a name="operator_himagelist"></a>Korzystanie CImageList:: operator HIMAGELIST

Użyj tego operatora, aby uzyskać dołączone dojście obiektu `CImageList`.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, dojście do listy obrazów reprezentowane przez obiekt `CImageList`; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatorem rzutowania, który obsługuje bezpośrednie użycie obiektu HIMAGELIST.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

##  <a name="read"></a>Korzystanie CImageList:: Read

Wywołaj tę funkcję, aby odczytać listę obrazów z archiwum.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Parametry

*pArchive*<br/>
Wskaźnik do obiektu `CArchive`, z którego ma zostać odczytana lista obrazów.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

##  <a name="remove"></a>Korzystanie CImageList:: Remove

Wywołaj tę funkcję, aby usunąć obraz z obiektu listy obrazów.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>Parametry

*Nokreślono*<br/>
Indeks (liczony od zera) obrazu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wszystkie elementy po *nokreślono* teraz przechodzą w dół o jedno miejsce. Na przykład, jeśli lista obrazów zawiera dwa elementy, usunięcie pierwszego elementu spowoduje, że pozostały element zostanie teraz w pierwszej pozycji. *nokreślono*= 0 dla elementu w pierwszej pozycji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

##  <a name="replace"></a>Korzystanie CImageList:: Replace

Wywołaj tę funkcję, aby zastąpić obraz na liście obrazów nowym obrazem.

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

*Nokreślono*<br/>
Indeks obrazu, który ma zostać zastąpiony od zera.

*pbmImage*<br/>
Wskaźnik do mapy bitowej zawierającej obraz.

*pbmMask*<br/>
Wskaźnik do mapy bitowej zawierającej maskę. Jeśli na liście obrazów nie jest używana żadna maska, ten parametr jest ignorowany.

*hIcon*<br/>
Uchwyt do ikony zawierającej mapę bitową i maskę dla nowego obrazu.

### <a name="return-value"></a>Wartość zwracana

Zwracanie wersji BOOL zwraca wartość różną od zera, jeśli pomyślne; w przeciwnym razie 0.

Wersja zwracająca wartość **int** zwraca indeks (liczony od zera) obrazu, jeśli to się powiedzie; w przeciwnym razie-1.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego po wywołaniu [SetImageCount](#setimagecount) , aby przypisać nowe, prawidłowe obrazy do numerów indeksu obrazu zastępczego.

### <a name="example"></a>Przykład

  Zobacz przykład dla [Korzystanie CImageList:: SetImageCount](#setimagecount).

##  <a name="setbkcolor"></a>Korzystanie CImageList:: SetBkColor

Wywołaj tę funkcję, aby ustawić kolor tła dla listy obrazów.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parametry

*znaki*<br/>
Kolor tła do ustawienia. Może być CLR_NONE. W takim przypadku obrazy są rysowane w sposób przezroczysty przy użyciu maski.

### <a name="return-value"></a>Wartość zwracana

Poprzedni kolor tła w przypadku powodzenia; w przeciwnym razie CLR_NONE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

##  <a name="setdragcursorimage"></a>Korzystanie CImageList:: SetDragCursorImage

Tworzy nowy obraz przeciągany przez połączenie danego obrazu (zwykle obrazu kursora myszy) z bieżącym obrazem przeciągania.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parametry

*nDrag*<br/>
Indeks nowego obrazu, który ma być połączony z obrazem przeciągania.

*ptHotSpot*<br/>
Położenie punktu aktywnego w nowym obrazie.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ponieważ funkcje przeciągania używają nowego obrazu podczas operacji przeciągania, należy użyć funkcji [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) systemu Windows, aby ukryć rzeczywisty wskaźnik myszy po wywołaniu `CImageList::SetDragCursorImage`. W przeciwnym razie system może wydawać dwa kursory myszy na czas trwania operacji przeciągania.

##  <a name="setimagecount"></a>Korzystanie CImageList:: SetImageCount

Wywołaj tę funkcję elementu członkowskiego, aby zresetować liczbę obrazów w obiekcie `CImageList`.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Parametry

*uNewCount*<br/>
Wartość określająca nową łączną liczbę obrazów z listy obrazów.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Jeśli wywołasz tę funkcję elementu członkowskiego, aby zwiększyć liczbę obrazów na liście obrazów, wywołaj polecenie [Zamień](#replace) dla każdego dodatkowego obrazu, aby przypisać nowe indeksy do prawidłowych obrazów. Jeśli przypisanie indeksów do prawidłowych obrazów nie powiedzie się, operacje rysowania, które tworzą nowe obrazy, będą nieprzewidywalne.

Zmniejszenie rozmiaru listy obrazów przy użyciu tej funkcji spowoduje zwolnienie obciętych obrazów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

##  <a name="setoverlayimage"></a>Korzystanie CImageList:: SetOverlayImage

Wywołaj tę funkcję, aby dodać indeks obrazu (liczony od zera) do listy obrazów, które mają być używane jako maski nakładania.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Parametry

*Nokreślono*<br/>
Indeks (liczony od zera) obrazu, który ma być używany jako maska nakładki.

*nOverlay*<br/>
Indeks pojedynczej maski nakładania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Do listy można dodać maksymalnie cztery indeksy.

Maska nakładki to obraz rysowany w sposób przezroczysty na innym obrazie. Narysuj maskę nakładki na obrazie, używając funkcji [Korzystanie CImageList::D RAW](#draw) członkowskiej z indeksem jednokrotnym dla maski nakładki określonej przy użyciu makra INDEXTOOVERLAYMASK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

##  <a name="write"></a>Korzystanie CImageList:: Write

Wywołaj tę funkcję, aby napisać obiekt listy obrazów do archiwum.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Parametry

*pArchive*<br/>
Wskaźnik do obiektu `CArchive`, w którym ma być przechowywana lista obrazów.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)<br/>
[Klasa CTabCtrl](../../mfc/reference/ctabctrl-class.md)
