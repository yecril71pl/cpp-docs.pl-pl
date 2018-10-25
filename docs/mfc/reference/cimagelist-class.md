---
title: Klasa CImageList | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ca52f7a5940de3caa87f81ddf07625ab751927c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054539"
---
# <a name="cimagelist-class"></a>Cimagelist — klasa

Oferuje funkcje formantu Windows typowej listy obrazów.

## <a name="syntax"></a>Składnia

```
class CImageList : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CImageList::CImageList](#cimagelist)|Konstruuje `CImageList` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CImageList::Add](#add)|Dodaje obraz lub obrazów do listy obrazów.|
|[CImageList::Attach](#attach)|Dołącza listy obrazów do `CImageList` obiektu.|
|[CImageList::BeginDrag](#begindrag)|Rozpoczyna się, przeciągając obrazu.|
|[CImageList::Copy](#copy)|Kopiuje obraz w obrębie `CImageList` obiektu.|
|[CImageList::Create](#create)|Inicjuje listy obrazów i dołącza je do `CImageList` obiektu.|
|[CImageList::DeleteImageList](#deleteimagelist)|Usuwa listy obrazów.|
|[CImageList::DeleteTempMap](#deletetempmap)|Wywoływane przez [CWinApp](../../mfc/reference/cwinapp-class.md) obsługi czasu bezczynności można usunąć wszystkie tymczasowe `CImageList` obiekt utworzony przez `FromHandle`.|
|[CImageList::Detach](#detach)|Odłącza obiekt listy obrazów z `CImageList` obiektu i zwraca uchwyt do listy obrazów.|
|[CImageList::DragEnter](#dragenter)|Blokuje aktualizacji w czasie trwania operacji przeciągania, a następnie wyświetli przeciągnij obraz na określonej pozycji.|
|[CImageList::DragLeave](#dragleave)|Odblokowuje okna i ukrywa przeciągnij obraz, dzięki czemu można zaktualizować okna.|
|[CImageList::DragMove](#dragmove)|Przenosi obraz, który jest przeciągany podczas operacji przeciągania i upuszczania.|
|[CImageList::DragShowNolock](#dragshownolock)|Pokazuje lub ukrywa przeciągnij obraz podczas operacji przeciągania, bez blokowania okna.|
|[CImageList::Draw](#draw)|Rysuje obraz, który jest przeciągany podczas operacji przeciągania i upuszczania.|
|[CImageList::DrawEx](#drawex)|Rysuje element listy obrazów w kontekście określonego urządzenia. Funkcja używa określony styl rysowania i przejścia obrazu przy użyciu określonego koloru.|
|[CImageList::DrawIndirect](#drawindirect)|Rysuje obraz z listy obrazów.|
|[CImageList::EndDrag](#enddrag)|Kończy operację przeciągania.|
|[CImageList::ExtractIcon](#extracticon)|Tworzy ikonę na podstawie obrazu i maska w listy obrazów.|
|[CImageList::FromHandle](#fromhandle)|Zwraca wskaźnik do `CImageList` obiektu, kiedy podane dojście do listy obrazów. Jeśli `CImageList` obiektu nie jest dołączony do uchwyt tymczasowego `CImageList` obiekt zostanie utworzony i dołączony.|
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|Zwraca wskaźnik do `CImageList` obiektu, kiedy podane dojście do listy obrazów. Jeśli `CImageList` obiektu nie jest dołączony do uchwytu, jest zwracana wartość NULL.|
|[CImageList::GetBkColor](#getbkcolor)|Pobiera bieżący kolor tła dla listy obrazów.|
|[CImageList::GetDragImage](#getdragimage)|Pobiera listę tymczasowe obrazu który jest używany do przeciągania.|
|[CImageList::GetImageCount](#getimagecount)|Pobiera liczbę obrazów w listy obrazów.|
|[CImageList::GetImageInfo](#getimageinfo)|Pobiera informacje o obrazie.|
|[CImageList::GetSafeHandle](#getsafehandle)|Pobiera `m_hImageList`.|
|[CImageList::Read](#read)|Odczytuje listy obrazów z archiwum.|
|[CImageList::Remove](#remove)|Usuwa obraz z listy obrazów.|
|[CImageList::Replace](#replace)|Zamienia obrazu na liście obrazu nowego obrazu.|
|[CImageList::SetBkColor](#setbkcolor)|Ustawia kolor tła dla listy obrazów.|
|[CImageList::SetDragCursorImage](#setdragcursorimage)|Tworzy nowy obraz przeciągania.|
|[CImageList::SetImageCount](#setimagecount)|Resetuje liczbę obrazów w listy obrazów.|
|[CImageList::SetOverlayImage](#setoverlayimage)|Dodaje liczony od zera indeks obrazu do listy obrazów do użycia jako nakładka maski.|
|[CImageList::Write](#write)|Zapisuje listy obrazów do archiwum.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CImageList::operator HIMAGELIST](#operator_himagelist)|Zwraca HIMAGELIST dołączone do `CImageList`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CImageList::m_hImageList](#m_himagelist)|Dojście, zawierających listy obrazów dołączonych do tego obiektu.|

## <a name="remarks"></a>Uwagi

"Lista obrazów" to kolekcja obrazów o tym samym rozmiarze, z których każdy może być przywoływane przez jego liczony od zera indeks. Listy obrazów są używane do efektywnego zarządzania dużymi zestawami ikony lub mapy bitowej. Wszystkie obrazy w listy obrazów znajdują się w jednej, szeroki mapy bitowej w formacie urządzenia ekranu. Listy obrazów może również obejmować monochromatycznych map bitowych, zawierający maski używany do rysowania obrazów w sposób niewidoczny dla użytkownika (styl ikony). Programowania interfejsu API aplikacji Win32 firmy Microsoft zawiera obraz lista funkcji, które umożliwiają rysowanie obrazów, tworzenie i zniszcz list obrazów, dodawania i usuwania obrazów, Zastąp obrazów, scalanie obrazów oraz przeciągnąć obrazy.

Ta kontrolka (i w związku z tym `CImageList` klasy) jest dostępna tylko dla programów uruchomionych w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.

Aby uzyskać więcej informacji na temat korzystania z `CImageList`, zobacz [kontrolki](../../mfc/controls-mfc.md) i [korzystanie z CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

##  <a name="add"></a>  CImageList::Add

Wywołaj tę funkcję, aby dodać jeden lub więcej obrazów lub ikonę do listy obrazów.

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
Wskaźnik do mapy bitowej zawierającego obraz lub obrazy. Liczba obrazów jest wnioskowany z szerokość mapy bitowej.

*pbmMask*<br/>
Wskaźnik do mapy bitowej zawierającą maskę. Jeśli żadna maska jest używany z listy obrazów, ten parametr jest ignorowany.

*crMask*<br/>
Kolor używany do generowania maski. Każdego piksela tego koloru w podanej mapie bitowej jest zmieniana na czarny i odpowiadający mu bit maski jest ustawiony na jedną.

*hIcon*<br/>
Uchwyt ikony, która zawiera mapę bitową i maska dla nowego obrazu.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks pierwszego nowy obraz w przypadku powodzenia; w przeciwnym razie - 1.

### <a name="remarks"></a>Uwagi

Odpowiedzialność za zwalniając uchwyt ikony, gdy są z nią zrobić.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

##  <a name="attach"></a>  CImageList::Attach

Wywołaj tę funkcję, aby dołączyć do listy obrazów `CImageList` obiektu.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hImageList*<br/>
Dojście do obiektu listy obrazów.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli załącznik powiodła się. w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

##  <a name="begindrag"></a>  CImageList::BeginDrag

Wywołaj tę funkcję, aby rozpocząć, przeciągania obrazu.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parametry

*Nokreślono*<br/>
Liczony od zera indeks obrazu do przeciągania.

*ptHotSpot*<br/>
Współrzędne początkową przeciągania (zazwyczaj pozycja kursora). Współrzędne są względne wobec lewym górnym rogu obrazu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja tworzy listę tymczasowe obrazu, która jest używana do przeciągania. Obraz, który stanowi połączenie określonego obrazu i jego maskę bieżący kursor. W odpowiedzi na kolejnych komunikatów WM_MOUSEMOVE, można przenieść przeciągnij obraz przy użyciu `DragMove` funkcja elementu członkowskiego. Aby zakończyć operacji przeciągania, można użyć `EndDrag` funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

##  <a name="cimagelist"></a>  CImageList::CImageList

Konstruuje `CImageList` obiektu.

```
CImageList();
```

##  <a name="copy"></a>  CImageList::Copy

Ta funkcja elementu członkowskiego implementuje zachowanie funkcji Win32 [ImageList_Copy](/windows/desktop/api/commctrl/nf-commctrl-imagelist_copy), zgodnie z opisem w zestawie Windows SDK.

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
Liczony od zera indeks obrazu, który ma być używany jako docelowy operacji kopiowania.

*Kod*<br/>
Liczony od zera indeks obrazu, który ma być używany jako źródło kopiowania.

*uFlags*<br/>
Wartość flagi bitowe, który określa typ operacji kopiowania, które ma zostać wykonane. Ten parametr może być jedną z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|ILCF_MOVE|Obraz źródłowy jest kopiowany do indeksu obrazu docelowego. Ta operacja powoduje wielu wystąpień danego obrazu. ILCF_MOVE jest ustawieniem domyślnym.|
|ILCF_SWAP|Obraz źródłowy i docelowy wymiany położenie listy obrazów.|

*pSrc*<br/>
Wskaźnik do `CImageList` obiekt, który jest elementem docelowym operacji kopiowania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

##  <a name="create"></a>  CImageList::Create

Inicjuje listy obrazów i dołącza je do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu.

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
Wymiary każdego obrazu w pikselach.

*CY*<br/>
Wymiary każdego obrazu w pikselach.

*nFlags*<br/>
Określa typ listy obrazów do utworzenia. Ten parametr może być kombinacją następujących wartości, ale może zawierać tylko jeden z `ILC_COLOR` wartości.

|Wartość|Znaczenie|
|-----------|-------------|
|ILC_COLOR|Użyj zachowania domyślnego, jeśli nie określono żadnego innymi ILC_COLOR * flag. Zazwyczaj wartość domyślna to ILC_COLOR4; Jednak w przypadku starszych sterowniki wyświetlacza, wartość domyślna jest ILC_COLORDDB.|
|ILC_COLOR4|Sekcja 4-bitowy (16 kolorów) map bitowych niezależnych od urządzenia (DIB) jako mapy bitowej dla listy obrazów.|
|ILC_COLOR8|Użyj sekcji DIB 8-bitowych. Kolory używane w tabeli kolorów są takich samych kolorów jako palety półtonów.|
|ILC_COLOR16|Użyj 16-bitowych (32/64 KB kolorów) DIB sekcji.|
|ILC_COLOR24|Użyj sekcji DIB 24-bitowego.|
|ILC_COLOR32|Użyj sekcji DIB 32-bitowych.|
|ILC_COLORDDB|Użyj mapy bitowej zależnej od urządzenia.|
|ILC_MASK|Używa maski. Lista obrazów zawiera dwa mapy bitowe, w jednym z nich jest monochromatycznych map bitowych maskowania. Jeśli ta wartość nie jest uwzględniona, listy obrazów zawiera tylko jeden mapy bitowej. Zobacz [rysowanie obrazów z listy obrazów](../../mfc/drawing-images-from-an-image-list.md) dodatkowe informacje na temat obrazów maskowanego.|

*nInitial*<br/>
Liczba obrazów, które początkowo zawiera listy obrazów.

*nGrow*<br/>
Liczba obrazów za pomocą których listy obrazów może być zwiększana, gdy system musi zmienić rozmiar na liście, aby zwolnić miejsce dla nowych obrazów. Tego parametru reprezentuje liczbę nowych obrazów, które mogą zawierać listy obrazów o zmienionym rozmiarze.

*nBitmapID*<br/>
Identyfikatory zasobów mapy bitowej ma zostać skojarzony z listy obrazów.

*crMask*<br/>
Kolor używany do generowania maski. Każdego piksela ten kolor Podana mapa bitowa jest zmieniana na czarny, a odpowiadający mu bit maski jest ustawiony na jedną.

*lpszBitmapID*<br/>
Ciąg zawierający identyfikatory obrazów.

*imagelist1*<br/>
Odwołanie do `CImageList` obiektu.

*nImage1*<br/>
Indeks pierwszego istniejącego obrazu.

*imagelist2*<br/>
Odwołanie do `CImageList` obiektu.

*nImage2*<br/>
Indeks drugiego istniejącego obrazu.

*DX*<br/>
Przesunięcie osi x, drugi obrazu w stosunku do pierwszego obrazu w pikselach.

*dy*<br/>
Przesunięcie osi y o drugi obraz w stosunku do pierwszego obrazu w pikselach.

*pImageList*<br/>
Wskaźnik do `CImageList` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CImageList` w dwóch krokach. Po pierwsze wywołanie konstruktora, a następnie wywołać `Create`, który tworzy listy obrazów i dołącza go do `CImageList` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

##  <a name="deleteimagelist"></a>  CImageList::DeleteImageList

Wywołaj tę funkcję można usunąć listy obrazów.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

##  <a name="deletetempmap"></a>  CImageList::DeleteTempMap

Wywoływana automatycznie przez `CWinApp` obsługi czasu bezczynności `DeleteTempMap` usuwa wszystkie tymczasowe `CImageList` obiekty utworzone przez [FromHandle](#fromhandle), ale nie niszczy wszystkie dojścia ( `hImageList`) tymczasowo skojarzone za pomocą `ImageList` obiektów.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

##  <a name="detach"></a>  CImageList::Detach

Wywołaj tę funkcję można odłączyć obiektu listy obrazów z `CImageList` obiektu.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu listy obrazów.

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca uchwyt do obiektu listy obrazów.

### <a name="example"></a>Przykład

  Zobacz przykład [CImageList::Attach](#attach).

##  <a name="dragenter"></a>  CImageList::DragEnter

Podczas operacji przeciągania, blokuje aktualizacji do okna, określony przez *pWndLock* i wyświetla przeciągnij obraz pozycji określonej przez *punktu*.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWndLock*<br/>
Wskaźnik do okna, który jest właścicielem przeciągnij obraz.

*Punkt*<br/>
Pozycja, od którego należy wyświetlić przeciągnij obraz. Współrzędne są podawane względem lewym górnym rogu okna (nie obszar klienta).

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Współrzędne są względem oknie w lewym górnym rogu, więc należy kompensuje szerokości okna elementów, takich jak obramowania paska tytułu i pasek menu, określając współrzędne.

Jeśli *pWndLock* ma wartość NULL, funkcja rysuje obraz w kontekście wyświetlania skojarzony z oknem pulpitu i współrzędne są podawane względem lewym górnym rogu ekranu.

Ta funkcja umożliwia zablokowanie wszystkich aktualizacji do danego okna podczas operacji przeciągania. Jeśli musisz wykonać dowolnego rysunku podczas operacji przeciągania, takich jak wyróżnianie obiekt docelowy operacji przeciągania i upuszczania, można tymczasowo ukryć przeciąganego obrazu za pomocą [CImageList::DragLeave](#dragleave) funkcji.

### <a name="example"></a>Przykład

  Zobacz przykład [CImageList::BeginDrag](#begindrag).

##  <a name="dragleave"></a>  CImageList::DragLeave

Odblokowuje okna określony przez *pWndLock* i ukrywa przeciągnij obraz, dzięki czemu okna do zaktualizowania.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>Parametry

*pWndLock*<br/>
Wskaźnik do okna, który jest właścicielem przeciągnij obraz.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CImageList::EndDrag](#enddrag).

##  <a name="dragmove"></a>  CImageList::DragMove

Wywołaj tę funkcję, aby przenieść obraz, który jest przeciągany podczas operacji przeciągania i upuszczania.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Parametry

*(czas pacyficzny)*<br/>
Nowa pozycja przeciągania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana w odpowiedzi na wiadomość WM_MOUSEMOVE. Aby rozpocząć operacji przeciągania, należy użyć `BeginDrag` funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

##  <a name="dragshownolock"></a>  CImageList::DragShowNolock

Pokazuje lub ukrywa przeciągnij obraz podczas operacji przeciągania, bez blokowania okna.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Określa, czy przeciągnij obraz ma być wyświetlana.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

[CImageList::DragEnter](#dragenter) funkcja blokuje wszystkie aktualizacje w oknie podczas operacji przeciągania. Ta funkcja nie blokuje jednak okna.

##  <a name="draw"></a>  CImageList::Draw

Wywołaj tę funkcję, aby rysować obraz, który jest przeciągany podczas operacji przeciągania i upuszczania.

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Wskaźnik do kontekstu urządzenia docelowego.

*Nokreślono*<br/>
Liczony od zera indeks obrazu do rysowania.

*(czas pacyficzny)*<br/>
Lokalizację, w której do rysowania w kontekście określonego urządzenia.

*nStyle*<br/>
Flaga określająca styl rysowania. Może być co najmniej jeden z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|Rysuje obraz mieszania 25 procent dzięki kolor wyróżnienia systemu. Ta wartość nie obowiązuje, jeśli listy obrazów nie zawiera maski.|
|ILD_BLEND50 ILD_SELECTED, ILD_BLEND|Rysuje obraz mieszania 50% dzięki kolor wyróżnienia systemu. Ta wartość nie obowiązuje, jeśli listy obrazów nie zawiera maski.|
|ILD_MASK|Rysuje maski.|
|ILD_NORMAL|Rysuje obraz dla listy obrazów za pomocą koloru tła. Jeśli kolor tła jest wartością CLR_NONE, obraz jest rysowana sposób niewidoczny dla użytkownika za pomocą maski.|
|ILD_TRANSPARENT|Rysuje obraz, w sposób niewidoczny dla użytkownika przy użyciu maska, niezależnie od tego, kolor tła.|

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CImageList::SetOverlayImage](#setoverlayimage).

##  <a name="drawex"></a>  CImageList::DrawEx

Rysuje element listy obrazów w kontekście określonego urządzenia.

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

*podstawowego kontrolera domeny*<br/>
Wskaźnik do kontekstu urządzenia docelowego.

*Nokreślono*<br/>
Liczony od zera indeks obrazu do rysowania.

*(czas pacyficzny)*<br/>
Lokalizację, w której do rysowania w kontekście określonego urządzenia.

*Sz*<br/>
Rozmiar część obrazu do rysowania względem lewego górnego rogu obrazu. Zobacz *dx* i *dy* w [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) w zestawie Windows SDK.

*clrBk*<br/>
Kolor tła obrazu. Zobacz *rgbBk* w [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) w zestawie Windows SDK.

*clrFg*<br/>
Kolor pierwszego planu obrazu. Zobacz *rgbFg* w [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) w zestawie Windows SDK.

*nStyle*<br/>
Flaga określająca styl rysowania. Zobacz *fStyle* w [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja używa określony styl rysowania i przejścia obrazu przy użyciu określonego koloru.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

##  <a name="drawindirect"></a>  CImageList::DrawIndirect

Wywołaj tę funkcję elementu członkowskiego, aby rysować obraz z listy obrazów.

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
Wskaźnik do [IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) strukturę, która zawiera informacje na temat operacji rysowania.

*podstawowego kontrolera domeny*<br/>
Wskaźnik do kontekstu urządzenia docelowego. Należy usunąć ten [CDC](../../mfc/reference/cdc-class.md) obiektu, kiedy są z nią zrobić.

*Nokreślono*<br/>
Liczony od zera indeks obrazu do narysowania.

*(czas pacyficzny)*<br/>
A [punktu](https://msdn.microsoft.com/library/windows/desktop/dd162805) struktury zawierającej współrzędnych x i y miejsca będzie rysowania obrazu.

*Sz*<br/>
A [rozmiar](https://msdn.microsoft.com/library/windows/desktop/dd145106) wskazujący rozmiar obraz, który ma być rysowany struktury.

*ptOrigin*<br/>
A [punktu](https://msdn.microsoft.com/library/windows/desktop/dd162805) struktury zawierającej współrzędnych x i y Określanie lewy górny róg operacji rysowania w odniesieniu do samego obrazu. Piksele obrazu, które są po lewej stronie współrzędnej x lub nowszym współrzędną y nie są rysowane.

*fStyle*<br/>
Flaga, określając styl rysowania i, opcjonalnie, obraz nakładki. Zobacz sekcję Spostrzeżenia, aby uzyskać informacje na obrazie nakładki. Domyślna implementacja MFC ILD_NORMAL, Rysuje obraz dla listy obrazów za pomocą koloru tła. Jeśli kolor tła jest wartością CLR_NONE, obraz jest rysowana sposób niewidoczny dla użytkownika za pomocą maski.

Inne możliwe style są opisane w ramach *fStyle* członkiem [IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) struktury.

*dwRop*<br/>
Wartość określająca kod operacji rastrowych. Kody te definiują, jak dane kolor prostokąta źródłowego zostanie połączony z elementem danych kolor prostokąta docelowego osiągnąć ostateczny kolor. Domyślna MFC, implementacja SRCCOPY, kopiuje prostokąta źródłowego bezpośrednio do prostokąta docelowego. Ten parametr jest ignorowany, jeśli *fStyle* parametru nie ma flagi ILD_ROP.

Inne możliwe wartości są opisane w ramach *dwRop* członkiem [IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) struktury.

*rgbBack*<br/>
Obraz kolor tła, domyślnie CLR_DEFAULT. Ten parametr może być wartości RGB zdefiniowanych przez aplikację lub jeden z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|CLR_DEFAULT|Domyślny kolor tła. Obraz jest rysowany przy użyciu koloru tła listy obrazów.|
|CLR_NONE|Brak koloru tła. Obraz jest rysowana w sposób niewidoczny dla użytkownika.|

*rgbFore*<br/>
Kolor pierwszego planu obrazu domyślnie CLR_DEFAULT. Ten parametr może być wartości RGB zdefiniowanych przez aplikację lub jeden z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|CLR_DEFAULT|Domyślny kolor pierwszego planu. Obraz jest rysowany przy użyciu kolor wyróżnienia systemu jako kolor pierwszego planu.|
|CLR_NONE|Brak koloru blend. Obraz jest zmieszana przy użyciu koloru kontekstu urządzenia docelowego.|

Ten parametr jest używany tylko wtedy, gdy *fStyle* obejmuje flagę ILD_BLEND25 lub ILD_BLEND50.

*fState*<br/>
Flaga określająca stan rysowania. Ten element członkowski może zawierać jeden lub więcej flagi stanu listy obrazów.

*Ramka*<br/>
Ma wpływ na zachowanie efekty saturate i używanie mieszania alfa.

W przypadku użycia za pomocą ILS_SATURATE, ten element członkowski przechowuje wartość, która zostanie dodany do każdego składnika koloru trójkę RGB dla każdego piksela ikony.

W przypadku użycia za pomocą ILS_APLHA, ten element członkowski przechowuje wartość kanału alfa. Ta wartość może być z zakresu od 0 do 255 0 jest całkowicie przezroczysty, a 255 całkowicie nieprzezroczysty.

*crEffect*<br/>
A [COLORREF](/windows/desktop/gdi/colorref) wartość używana do efektów i w tle.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pomyślnie narysowaniem obrazu; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Jeśli chcesz wypełnić struktury Win32, samodzielnie, należy użyć pierwszej wersji. Jeśli chcesz skorzystać z co najmniej jeden z argumentów domyślnych MFC lub należy unikać Zarządzanie struktury, należy użyć drugiej wersji.

Obraz nakładki jest obraz, który jest wstawiany dodaną do obrazu podstawowego, określone w tej funkcji elementu członkowskiego przez *Nokreślono* parametru. Rysowanie maski nakładki przy użyciu [Rysowanie](#draw) funkcji składowej z indeksu liczonego od jednego określone za pomocą maski nakładki [INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) — makro.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

##  <a name="enddrag"></a>  CImageList::EndDrag

Wywołaj tę funkcję, aby zakończyć operację przeciągania.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Uwagi

Aby rozpocząć operacji przeciągania, należy użyć `BeginDrag` funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

##  <a name="extracticon"></a>  CImageList::ExtractIcon

Wywołaj tę funkcję, aby utworzyć ikonę na podstawie obrazu i jego maskę powiązane w listy obrazów.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Parametry

*Nokreślono*<br/>
Liczony od zera indeks obrazu.

### <a name="return-value"></a>Wartość zwracana

Uchwyt ikony, jeśli to się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z zachowaniem [ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon) makra w celu utworzenia ikony. Zapoznaj się [ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon) makra, aby uzyskać więcej informacji na ikonę tworzenia i czyszczenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

##  <a name="fromhandle"></a>  CImageList::FromHandle

Zwraca wskaźnik do `CImageList` obiektu, kiedy podane dojście do listy obrazów.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hImageList*<br/>
Określa listę obrazów.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CImageList` obiektu, jeśli operacja się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CImageList` nie jest już dołączony do uchwyt tymczasowego `CImageList` obiekt zostanie utworzony i dołączony. Ten tymczasowy `CImageList` obiekt jest prawidłowy tylko do momentu przy następnym aplikacji ma czas bezczynności, po jego pętlę zdarzeń, które wszystkie obiekty tymczasowe są usuwane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

##  <a name="fromhandlepermanent"></a>  CImageList::FromHandlePermanent

Zwraca wskaźnik do `CImageList` obiektu, kiedy podane dojście do listy obrazów.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hImageList*<br/>
Określa listę obrazów.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CImageList` obiektu, jeśli operacja się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli `CImageList` obiektu nie jest dołączony do uchwytu, jest zwracana wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

##  <a name="getbkcolor"></a>  CImageList::GetBkColor

Wywołaj tę funkcję, aby pobrać bieżący kolor tła dla listy obrazów.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość koloru RGB `CImageList` kolor tła obiektu.

### <a name="example"></a>Przykład

  Zobacz przykład [CImageList::SetBkColor](#setbkcolor).

##  <a name="getdragimage"></a>  CImageList::GetDragImage

Pobiera listę tymczasowe obrazu który jest używany do przeciągania.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Parametry

*lppoint —*<br/>
Adres [punktu](https://msdn.microsoft.com/library/windows/desktop/dd162805) struktury, która odbiera bieżącego przeciągnij pozycji.

*lpPointHotSpot*<br/>
Adres `POINT` strukturę, która odbiera przesunięcie przeciągnij obraz względem pozycji przeciągania.

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja się powiedzie, wskaźnik do tymczasowego obraz listę służy do przeciągania; w przeciwnym razie wartość NULL.

##  <a name="getimagecount"></a>  CImageList::GetImageCount

Wywołaj tę funkcję, aby pobrać liczbę obrazów w listy obrazów.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba obrazów.

### <a name="example"></a>Przykład

  Zobacz przykład [CImageList::ExtractIcon](#extracticon).

##  <a name="getimageinfo"></a>  CImageList::GetImageInfo

Wywołaj tę funkcję, aby pobrać informacje o obrazie.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>Parametry

*Nokreślono*<br/>
Liczony od zera indeks obrazu.

*pImageInfo*<br/>
Wskaźnik do [IMAGEINFO](/windows/desktop/api/commctrl/ns-commctrl-_imageinfo) strukturę, która otrzymuje informacje o obrazie. Informacje przedstawione w tej struktury, można bezpośrednio modyfikować mapy bitowe dla obrazu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`IMAGEINFO` Struktura zawiera informacje o obrazie w listy obrazów.

##  <a name="getsafehandle"></a>  CImageList::GetSafeHandle

Wywołaj tę funkcję, aby pobrać `m_hImageList` element członkowski danych.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do listy dołączonego obrazu w przeciwnym razie wartość NULL, jeśli żaden obiekt nie jest dołączony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

##  <a name="m_himagelist"></a>  CImageList::m_hImageList

Uchwyt listy obrazów dołączonych do tego obiektu.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Uwagi

`m_hImageList` Element członkowski danych jest publiczną zmienną typu HIMAGELIST.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

##  <a name="operator_himagelist"></a>  CImageList::operator HIMAGELIST

Użyj tego operatora, aby uzyskać dojście dołączonych `CImageList` obiektu.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja się powiedzie, dojścia do listy obrazów reprezentowany przez `CImageList` obiektu; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Ten operator jest operatora rzutowania, który obsługuje bezpośredniego użycia obiektu HIMAGELIST.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

##  <a name="read"></a>  CImageList::Read

Wywołaj tę funkcję można odczytać listy obrazów z archiwum.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Parametry

*pArchive*<br/>
Wskaźnik do `CArchive` obiektu, z którego ma być odczytywane listy obrazów.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

##  <a name="remove"></a>  CImageList::Remove

Wywołaj tę funkcję, aby usunąć obraz z obiektu listy obrazów.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>Parametry

*Nokreślono*<br/>
Liczony od zera indeks obrazu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wszystkie elementy występujące *Nokreślono* teraz Przenieś w dół o jedną pozycję. Na przykład jeśli listy obrazów zawiera dwa elementy, usunięcie pierwszy element spowoduje, że element pozostałe które mają być teraz na pierwszym miejscu. *Nokreślono*= 0 dla elementu na pierwszym miejscu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

##  <a name="replace"></a>  CImageList::Replace

Wywołaj tę funkcję, aby zastąpić obraz w listy obrazów za pomocą nowego obrazu.

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
Liczony od zera indeks obrazu do zastąpienia.

*pbmImage*<br/>
Wskaźnik do obrazu mapy bitowej.

*pbmMask*<br/>
Wskaźnik do mapy bitowej zawierającą maskę. Jeśli żadna maska jest używany z listy obrazów, ten parametr jest ignorowany.

*hIcon*<br/>
Dojście do ikony, która zawiera mapę bitową i maska dla nowego obrazu.

### <a name="return-value"></a>Wartość zwracana

Wersji, zwracając wartość logiczna zwraca wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

Wersja zwracanie **int** zwraca liczony od zera indeks obrazu w przypadku powodzenia; w przeciwnym razie - 1.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego po wywołaniu [SetImageCount](#setimagecount) można przypisać nową, prawidłową obrazów do symbolu zastępczego obrazu numery indeksu.

### <a name="example"></a>Przykład

  Zobacz przykład [CImageList::SetImageCount](#setimagecount).

##  <a name="setbkcolor"></a>  CImageList::SetBkColor

Wywołaj tę funkcję, aby ustawić kolor tła dla listy obrazów.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parametry

*CR*<br/>
Kolor tła do ustawienia. Może to być CLR_NONE. W takim przypadku obrazy są rysowane sposób niewidoczny dla użytkownika za pomocą maski.

### <a name="return-value"></a>Wartość zwracana

Poprzedni kolor tła w przypadku powodzenia; w przeciwnym razie CLR_NONE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

##  <a name="setdragcursorimage"></a>  CImageList::SetDragCursorImage

Tworzy nowy obraz przeciągania, łącząc danego obrazu (zazwyczaj obraz kursora myszy) z bieżącego obrazu przeciągania.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parametry

*Nprzeciągnij*<br/>
Indeks nowy obraz, który ma być łączone z przeciągnij obraz.

*ptHotSpot*<br/>
Położenie punktu aktywnego w ramach nowego obrazu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ponieważ funkcje przeciągania korzystała z nowego obrazu w czasie trwania operacji przeciągania, należy używać Windows [wartość](/windows/desktop/api/winuser/nf-winuser-showcursor) funkcję, aby ukryć rzeczywiste kursor po wywołaniu `CImageList::SetDragCursorImage`. W przeciwnym razie system może być w dwóch kursory myszy na czas trwania operacji przeciągania.

##  <a name="setimagecount"></a>  CImageList::SetImageCount

Wywołaj tę funkcję elementu członkowskiego, aby zresetować liczbę obrazów w `CImageList` obiektu.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Parametry

*uNewCount*<br/>
Wartość, określając nowy całkowita liczba obrazów z listy obrazów.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.

### <a name="remarks"></a>Uwagi

Jeśli chcesz wywołać tę funkcję elementu członkowskiego, aby zwiększyć liczbę obrazów z listy obrazów, następnie wywołać [Zastąp](#replace) dla każdego dodatkowego obrazu można przypisać nowe indeksy prawidłowe obrazów. Jeśli nie można przypisać indeksy prawidłowe obrazów, operacji rysowania, które nowe obrazy będą nieprzewidywalne.

Skrócona obrazy są zwalniane, jeśli zmniejszyć rozmiar listy obrazów za pomocą tej funkcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

##  <a name="setoverlayimage"></a>  CImageList::SetOverlayImage

Wywołaj tę funkcję, aby dodać liczony od zera indeks obrazu do listy obrazów do użycia jako nakładka maski.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Parametry

*Nokreślono*<br/>
Liczony od zera indeks obrazu do użycia jako maska nakładki.

*nOverlay*<br/>
Indeksu liczonego od jednego maski nakładki.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Maksymalnie cztery indeksów można dodać do listy.

Maska nakładki jest rysowana w sposób niewidoczny dla użytkownika za pośrednictwem innego obrazu obrazu. Rysowanie maski nakładki na obrazie przy użyciu [CImageList::Draw](#draw) funkcji składowej z indeksu liczonego od jednego określona za pomocą makra INDEXTOOVERLAYMASK maska nakładki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

##  <a name="write"></a>  CImageList::Write

Wywołaj tę funkcję w celu zapisania obiektu listy obrazów do archiwum.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Parametry

*pArchive*<br/>
Wskaźnik do `CArchive` obiekt, w którym ma być przechowywany listy obrazów.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)<br/>
[Klasa CTabCtrl](../../mfc/reference/ctabctrl-class.md)
