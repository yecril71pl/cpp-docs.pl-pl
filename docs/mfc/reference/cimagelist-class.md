---
title: "Cimagelist — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 07065470a7dda56650224bc794579a5038c9b643
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cimagelist-class"></a>Cimagelist — klasa
Udostępnia funkcje formantu listy typowych obrazu systemu Windows.  
  
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
|[CImageList::BeginDrag](#begindrag)|Rozpoczyna się przeciąganie obrazu.|  
|[CImageList::Copy](#copy)|Kopiuje obraz wewnątrz `CImageList` obiektu.|  
|[CImageList::Create](#create)|Inicjuje listy obrazów i dołącza go do `CImageList` obiektu.|  
|[CImageList::DeleteImageList](#deleteimagelist)|Usuwa listy obrazów.|  
|[CImageList::DeleteTempMap](#deletetempmap)|Wywoływane przez [CWinApp](../../mfc/reference/cwinapp-class.md) obsługi czas bezczynności, aby usunąć wszystkie tymczasowe `CImageList` obiekt utworzony przez `FromHandle`.|  
|[CImageList::Detach](#detach)|Odłącza obiekt listy obrazów z `CImageList` obiektu i zwraca uchwyt do listy obrazów.|  
|[CImageList::DragEnter](#dragenter)|Blokuje aktualizacji podczas operacji przeciągania i wyświetla obraz przeciągnij na określonej pozycji.|  
|[CImageList::DragLeave](#dragleave)|Odblokowuje okna i ukrywa obrazu przeciągania, dzięki czemu można aktualizować okna.|  
|[CImageList::DragMove](#dragmove)|Przenosi obrazu, który jest przeciągany podczas operacji przeciągania i upuszczania.|  
|[CImageList::DragShowNolock](#dragshownolock)|Pokazuje lub ukrywa obrazu przeciągania podczas operacji przeciągania, bez blokowania okna.|  
|[CImageList::Draw](#draw)|Rysuje obraz, który jest przeciągany podczas operacji przeciągania i upuszczania.|  
|[CImageList::DrawEx](#drawex)|Rysuje obraz elementu listy w kontekście określonego urządzenia. Funkcja używa określony styl rysowania i przejścia obrazu z określonego koloru.|  
|[CImageList::DrawIndirect](#drawindirect)|Rysuje obraz z listy obrazów.|  
|[CImageList::EndDrag](#enddrag)|Kończy operację przeciągania.|  
|[CImageList::ExtractIcon](#extracticon)|Tworzy ikonę na podstawie obrazu i maska w listy obrazów.|  
|[CImageList::FromHandle](#fromhandle)|Zwraca wskaźnik do `CImageList` obiektu, gdy uchwyt do listy obrazów. Jeśli `CImageList` obiekt nie jest dołączony do uchwytu, tymczasowej `CImageList` obiekt jest tworzony i dołączyć.|  
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|Zwraca wskaźnik do `CImageList` obiektu, gdy uchwyt do listy obrazów. Jeśli `CImageList` obiekt nie jest dołączony do uchwytu, **NULL** jest zwracany.|  
|[CImageList::GetBkColor](#getbkcolor)|Pobiera bieżący kolor tła dla listy obrazów.|  
|[CImageList::GetDragImage](#getdragimage)|Pobiera listę tymczasowego obrazu używanego do przeciągania.|  
|[CImageList::GetImageCount](#getimagecount)|Pobiera liczbę obrazów na liście obrazów.|  
|[CImageList::GetImageInfo](#getimageinfo)|Pobiera informacje o pliku obrazu.|  
|[CImageList::GetSafeHandle](#getsafehandle)|Pobiera **m_hImageList**.|  
|[CImageList::Read](#read)|Odczytuje listy obrazów z archiwum.|  
|[CImageList::Remove](#remove)|Usuwa obraz z listy obrazów.|  
|[CImageList::Replace](#replace)|Zastępuje obraz w listy obrazów z nowego obrazu.|  
|[CImageList::SetBkColor](#setbkcolor)|Ustawia kolor tła dla listy obrazów.|  
|[CImageList::SetDragCursorImage](#setdragcursorimage)|Tworzy nowy obraz przeciągania.|  
|[CImageList::SetImageCount](#setimagecount)|Resetuje licznik obrazów w listy obrazów.|  
|[CImageList::SetOverlayImage](#setoverlayimage)|Dodaje liczony od zera indeks obrazu do listy obrazów, które mają być używane jako maski nakładki.|  
|[CImageList::Write](#write)|Zapisuje listy obrazów do archiwum.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CImageList::operator HIMAGELIST](#operator_himagelist)|Zwraca `HIMAGELIST` dołączony do `CImageList`.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CImageList::m_hImageList](#m_himagelist)|Uchwyt zawierających listy obrazów dołączonych do tego obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 "Listy obrazów" jest kolekcją obrazów o tym samym rozmiarze, z których każdy może być przywoływane przez jego liczony od zera indeks. Listy obrazów umożliwiają wydajne zarządzanie dużymi zbiorami ikony lub mapy bitowe. Wszystkie obrazy na liście obrazów znajdują się w jednej, szeroki mapy bitowej w formacie ekranu urządzenia. Listy obrazów mogą również obejmować monochromatyczny mapy bitowej zawierającego maski używany do rysowania obrazów w sposób niewidoczny dla użytkownika (styl ikony). Programowania interfejsu API aplikacji Microsoft Win32 udostępnia funkcje listy obrazów, umożliwiających rysowanie obrazów, tworzenie i zniszczyć listy obrazów, dodawanie i usuwanie obrazów, Zastąp obrazów, scalanie obrazów i przeciągnij obrazów.  
  
 Ten formant (i w związku z tym `CImageList` klasy) jest dostępne tylko dla programów w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Aby uzyskać więcej informacji na temat używania `CImageList`, zobacz [formanty](../../mfc/controls-mfc.md) i [przy użyciu CImageList](../../mfc/using-cimagelist.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CImageList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="add"></a>CImageList::Add  
 Wywołanie tej funkcji, aby dodać jeden lub więcej obrazów lub ikony do listy obrazów.  
  
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
 `pbmImage`  
 Wskaźnik do mapy bitowej zawierającego obraz lub obrazów. Liczba obrazów jest wywnioskowany na podstawie szerokość mapy bitowej.  
  
 `pbmMask`  
 Wskaźnik do mapy bitowej zawierającego maski. Maska nie jest używana z listy obrazów, ten parametr jest ignorowana.  
  
 `crMask`  
 Kolor używany do generowania maski. Każdego piksela tego koloru w danym mapę bitową zostało zmienione na kolor czarny i odpowiadający mu bit maski ma wartość 1.  
  
 `hIcon`  
 Dojście ikonę, która zawiera mapę bitową i maska dla nowego obrazu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks pierwszego nowy obraz w przypadku powodzenia; w przeciwnym razie wartość - 1.  
  
### <a name="remarks"></a>Uwagi  
 Użytkownik jest odpowiedzialny za zwolnienie dojście ikony, gdy wszystko będzie gotowe z nim.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]  
  
##  <a name="attach"></a>CImageList::Attach  
 Wywołanie tej funkcji do dołączenia do listy obrazów `CImageList` obiektu.  
  
```  
BOOL Attach(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `hImageList`  
 Dojście do obiektu listy obrazów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli załącznika zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]  
  
##  <a name="begindrag"></a>CImageList::BeginDrag  
 Wywołanie tej funkcji, aby rozpocząć, przeciągając obrazu.  
  
```  
BOOL BeginDrag(
    int nImage,  
    CPoint ptHotSpot);
```  
  
### <a name="parameters"></a>Parametry  
 `nImage`  
 Liczony od zera indeks obrazu do przeciągnij.  
  
 `ptHotSpot`  
 Współrzędne pozycji początkowej przeciągania (zazwyczaj pozycji kursora). Współrzędne są podawane względem lewym górnym rogu obrazu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja tworzy listę tymczasowego obrazu używanego do przeciągania. Obraz łączy określonego obrazu i jego maskę z bieżący kursor. W odpowiedzi na kolejne `WM_MOUSEMOVE` wiadomości, można przenieść obraz przeciągania przy użyciu `DragMove` funkcji członkowskiej. Aby zakończyć operacji przeciągania, można użyć `EndDrag` funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]  
  
##  <a name="cimagelist"></a>CImageList::CImageList  
 Konstruuje `CImageList` obiektu.  
  
```  
CImageList();
```  
  
##  <a name="copy"></a>CImageList::Copy  
 Ta funkcja członkowska implementuje zachowanie funkcji Win32 [ImageList_Copy](http://msdn.microsoft.com/library/windows/desktop/bb761520), zgodnie z opisem w zestawie Windows SDK.  
  
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
 *iDst*  
 Liczony od zera indeks obrazu, który ma być używany jako docelowy operacji kopiowania.  
  
 `iSrc`  
 Liczony od zera indeks obrazu, który ma być używany jako źródło operacji kopiowania.  
  
 `uFlags`  
 Wartość Flaga bitowa określa rodzaj operacji kopiowania ma zostać wykonane. Ten parametr może mieć jedną z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|`ILCF_MOVE`|Obraz źródłowy jest kopiowana na indeks obrazu docelowego. Ta operacja powoduje wielu wystąpień danego obrazu. `ILCF_MOVE`jest ustawieniem domyślnym.|  
|`ILCF_SWAP`|Obraz źródłowy i docelowy wymiany pozycji w liście obrazu.|  
  
 `pSrc`  
 Wskaźnik do `CImageList` obiektu, który jest miejscem docelowym operacji kopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]  
  
##  <a name="create"></a>CImageList::Create  
 Inicjuje listy obrazów i dołącza go do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu.  
  
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
 `cx`  
 Wymiary każdego obrazu w pikselach.  
  
 `cy`  
 Wymiary każdego obrazu w pikselach.  
  
 `nFlags`  
 Określa typ listy obrazów do utworzenia. Ten parametr może być kombinacją następujące wartości, ale może zawierać tylko jeden z `ILC_COLOR` wartości.  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|`ILC_COLOR`|Używaj domyślnego zachowania, jeśli żadna z innych `ILC_COLOR`* flag jest określona. Wartość domyślna to zazwyczaj `ILC_COLOR4`; ale starsze sterowniki wyświetlania, wartością domyślną jest `ILC_COLORDDB`.|  
|`ILC_COLOR4`|Używanie sekcji map bitowych niezależnych od urządzenia (DIB) (16 kolorów) 4-bitowy jako mapy bitowej dla listy obrazów.|  
|`ILC_COLOR8`|Użyj sekcji DIB 8-bitową. Kolory używane w tabeli kolorów są takich samych kolorów jako półtonów.|  
|`ILC_COLOR16`|Użyj 16-bitowych (32/64 KB kolor) DIB sekcji.|  
|`ILC_COLOR24`|Używanie sekcji DIB 24-bitowego.|  
|`ILC_COLOR32`|Używanie sekcji DIB 32-bitowych.|  
|`ILC_COLORDDB`|Użyj mapy bitowej zależne od urządzenia.|  
|`ILC_MASK`|Używa maski. Listy obrazów zawiera dwa mapy bitowe, z których jeden jest monochromatyczny mapę bitową maskowania. Jeśli ta wartość nie jest uwzględniona, listy obrazów zawiera tylko jeden mapy bitowej. Zobacz [rysowanie obrazów z listy obrazów](../../mfc/drawing-images-from-an-image-list.md) dodatkowe informacje na temat obrazów maskowanego.|  
  
 `nInitial`  
 Liczba obrazów, które początkowo zawiera listy obrazów.  
  
 `nGrow`  
 Liczba obrazów za pomocą których może zwiększyć listy obrazów, podczas których system potrzebuje do zmiany rozmiaru na liście, aby zwolnić miejsce dla nowych obrazów. Tego parametru oznacza liczbę nowych obrazów, może zawierać listę obraz o zmienionym rozmiarze.  
  
 `nBitmapID`  
 Identyfikatory zasobu mapy bitowej ma zostać skojarzony z listy obrazów.  
  
 `crMask`  
 Kolor używany do generowania maski. Podana mapa bitowa tego koloru każdego piksela zostanie zmieniona na kolor czarny i odpowiadający mu bit maski ma wartość 1.  
  
 `lpszBitmapID`  
 Ciąg zawierający identyfikatorów obrazów zasobów.  
  
 `imagelist1`  
 Odwołanie do `CImageList` obiektu.  
  
 `nImage1`  
 Indeks pierwszego istniejącego obrazu.  
  
 `imagelist2`  
 Odwołanie do `CImageList` obiektu.  
  
 `nImage2`  
 Indeks drugi istniejącego obrazu.  
  
 `dx`  
 Przesunięcie osi x drugiego obrazu w stosunku do pierwszego obrazu w pikselach.  
  
 `dy`  
 Przesunięcie osi y drugiego obrazu w stosunku do pierwszego obrazu w pikselach.  
  
 `pImageList`  
 Wskaźnik do `CImageList` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CImageList` w dwóch krokach. Najpierw należy wywołać konstruktora, a następnie wywołać `Create`, która tworzy listy obrazów i dołącza go do `CImageList` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]  
  
##  <a name="deleteimagelist"></a>CImageList::DeleteImageList  
 Wywołanie tej funkcji można usunąć listy obrazów.  
  
```  
BOOL DeleteImageList();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]  
  
##  <a name="deletetempmap"></a>CImageList::DeleteTempMap  
 Wywoływana automatycznie przez `CWinApp` obsługi czas bezczynności, `DeleteTempMap` usuwa wszystkie tymczasowe `CImageList` obiekty utworzone przez [FromHandle](#fromhandle), ale zniszczy dowolnym uchwyty ( `hImageList`) tymczasowo skojarzone z **ImageList** obiektów.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]  
  
##  <a name="detach"></a>CImageList::Detach  
 Wywołanie tej funkcji można odłączyć obiektu listy obrazów z `CImageList` obiektu.  
  
```  
HIMAGELIST Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do obiektu listy obrazów.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja zwraca uchwyt do obiektu listy obrazów.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CImageList::Attach](#attach).  
  
##  <a name="dragenter"></a>CImageList::DragEnter  
 Podczas operacji przeciągania, blokuje aktualizacji do okna, określony przez `pWndLock` i wyświetla obraz przeciągania pozycji określonej przez `point`.  
  
```  
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndLock`  
 Wskaźnik do okna posiadającego obrazu przeciągania.  
  
 `point`  
 Pozycja jaką do wyświetlania obrazu przeciągania. Współrzędne są względem lewym górnym rogu okna (nie obszaru klienckiego).  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Współrzędne są względem oknie w lewym górnym rogu, więc musi kompensacji szerokości okna elementów, takich jak obramowania paska tytułu i paska menu, określając współrzędne.  
  
 Jeśli `pWndLock` jest **NULL**, ta funkcja rysuje obraz w kontekście wyświetlania skojarzony z oknem pulpitu i współrzędne są podawane względem lewym górnym rogu ekranu.  
  
 Ta funkcja umożliwia zablokowanie wszystkie aktualizacje w oknie danego podczas operacji przeciągania. Jeśli trzeba dowolnego rysunku podczas operacji przeciągania, takich jak wyróżnianie obiekt docelowy operacji przeciągania i upuszczania, można ukryć przeciąganego obrazu przy użyciu [CImageList::DragLeave](#dragleave) funkcji.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CImageList::BeginDrag](#begindrag).  
  
##  <a name="dragleave"></a>CImageList::DragLeave  
 Odblokowuje okna, określony przez `pWndLock` i ukrywa obrazu przeciągania, umożliwiając okna do zaktualizowania.  
  
```  
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndLock`  
 Wskaźnik do okna posiadającego obrazu przeciągania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CImageList::EndDrag](#enddrag).  
  
##  <a name="dragmove"></a>CImageList::DragMove  
 Wywołanie tej funkcji, aby przenieść obrazu, który jest przeciągany podczas operacji przeciągania i upuszczania.  
  
```  
static BOOL PASCAL DragMove(CPoint pt);
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 Nowa pozycja przeciągania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zazwyczaj wywoływana w odpowiedzi na `WM_MOUSEMOVE` wiadomości. Aby rozpocząć operacji przeciągania, użyj `BeginDrag` funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]  
  
##  <a name="dragshownolock"></a>CImageList::DragShowNolock  
 Pokazuje lub ukrywa obrazu przeciągania podczas operacji przeciągania, bez blokowania okna.  
  
```  
static BOOL PASCAL DragShowNolock(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 `bShow`  
 Określa, czy ma być wyświetlany obraz przeciągania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 [CImageList::DragEnter](#dragenter) funkcja blokuje wszystkie aktualizacje w oknie podczas operacji przeciągania. Jednak ta funkcja nie blokuje okna.  
  
##  <a name="draw"></a>CImageList::Draw  
 Wywołanie tej funkcji do rysowania obrazu, który jest przeciągany podczas operacji przeciągania i upuszczania.  
  
```  
BOOL Draw(
    CDC* pDC,  
    int nImage,  
    POINT pt,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskaźnik do kontekstu urządzenia docelowego.  
  
 `nImage`  
 Liczony od zera indeks obrazu do rysowania.  
  
 `pt`  
 Lokalizację, w której ma zostać narysowany w kontekście określonego urządzenia.  
  
 `nStyle`  
 Flaga, określając styl rysowania. Może to być co najmniej jeden z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|`ILD_BLEND25`, **ILD_FOCUS**|Rysuje obraz mieszania 25 procent kolorem wyróżnienie systemu. Ta wartość nie ma efektu Jeśli listy obrazów nie zawiera maski.|  
|`ILD_BLEND50`, **ILD_SELECTED**, **ILD_BLEND**|Rysuje obraz mieszania 50 procent kolorem wyróżnienie systemu. Ta wartość nie ma efektu Jeśli listy obrazów nie zawiera maski.|  
|**ILD_MASK**|Rysuje maski.|  
|`ILD_NORMAL`|Rysuje obraz za pomocą kolor tła dla listy obrazów. Jeśli kolor tła jest `CLR_NONE` wartość, obraz jest wybierana w sposób niewidoczny dla użytkownika za pomocą maski.|  
|`ILD_TRANSPARENT`|Rysuje obraz przezroczysty za pomocą maski, niezależnie od koloru tła.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CImageList::SetOverlayImage](#setoverlayimage).  
  
##  <a name="drawex"></a>CImageList::DrawEx  
 Rysuje obraz elementu listy w kontekście określonego urządzenia.  
  
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
 `pDC`  
 Wskaźnik do kontekstu urządzenia docelowego.  
  
 `nImage`  
 Liczony od zera indeks obrazu do rysowania.  
  
 `pt`  
 Lokalizację, w której ma zostać narysowany w kontekście określonego urządzenia.  
  
 `sz`  
 Rozmiar część obrazu do rysowania względem lewego górnego rogu obrazu. Zobacz `dx` i *dy* w [ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) w systemie Windows SDK.  
  
 *clrBk*  
 Kolor tła obrazu. Zobacz *rgbBk* w [ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) w zestawie Windows SDK.  
  
 *clrFg*  
 Kolor pierwszego planu z obrazu. Zobacz *rgbFg* w [ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) w zestawie Windows SDK.  
  
 `nStyle`  
 Flaga, określając styl rysowania. Zobacz *fStyle* w [ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja używa określony styl rysowania i przejścia obrazu z określonego koloru.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]  
  
##  <a name="drawindirect"></a>CImageList::DrawIndirect  
 Wywołanie tej funkcji Członkowskich do rysowania obrazu z listy obrazów.  
  
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
 *pimldp*  
 Wskaźnik do [IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) struktury, która zawiera informacje na temat operacji rysowania.  
  
 `pDC`  
 Wskaźnik do kontekstu urządzenia docelowego. Należy usunąć ten [CDC](../../mfc/reference/cdc-class.md) obiektu, gdy wszystko będzie gotowe z nim.  
  
 `nImage`  
 Liczony od zera indeks obrazu do narysowania.  
  
 `pt`  
 A [punktu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktury zawierającej współrzędne x i y miejsca zostanie rysowania obrazu.  
  
 `sz`  
 A [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) wskazaniem wielkości obraz, który ma być rysowany struktury.  
  
 *ptOrigin*  
 A [punktu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktury zawierającej współrzędne x i y Określanie lewego górnego rogu operacji rysowania względem samego obrazu. Nie są rysowane piksele obrazu, które są w lewo współrzędną x i powyżej współrzędną y.  
  
 `fStyle`  
 Flaga, określając styl rysowania i, opcjonalnie, obrazu nakładki. Zobacz sekcję uwag informacji w obrazie nakładki. Domyślna implementacja MFC `ILD_NORMAL`, Rysuje obraz za pomocą kolor tła dla listy obrazów. Jeśli kolor tła jest `CLR_NONE` wartość, obraz jest wybierana w sposób niewidoczny dla użytkownika za pomocą maski.  
  
 Opisano w innych możliwych stylów **fStyle** członkiem [IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) struktury.  
  
 *dwRop*  
 Wartość określającą kod operacji rastrowych. Te kody zdefiniuj, jak dane kolor prostokąta źródłowego zostanie połączona z danych kolor prostokąta docelowego do osiągnięcia ostateczny kolor. MFC Domyślna implementacja, **SRCCOPY**, kopiuje prostokąta źródłowego bezpośrednio do prostokąta docelowego. Ten parametr jest ignorowana, jeśli `fStyle` nie ma parametru **ILD_ROP** flagi.  
  
 Inne możliwe wartości zostały opisane w obszarze **dwRop** członkiem [IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) struktury.  
  
 *rgbBack*  
 Kolor tła obrazów, domyślnie `CLR_DEFAULT`. Ten parametr może być wartości RGB zdefiniowanym przez aplikację lub jeden z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|`CLR_DEFAULT`|Domyślny kolor tła. Obraz jest rysowane przy użyciu kolor tła listy obrazów.|  
|`CLR_NONE`|Nie kolor tła. Obraz jest rysowany jako przezroczysty.|  
  
 *rgbFore*  
 Obraz kolor pierwszego planu, domyślnie `CLR_DEFAULT`. Ten parametr może być wartości RGB zdefiniowanym przez aplikację lub jeden z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|`CLR_DEFAULT`|Domyślny kolor pierwszego planu. Obraz jest rysowane przy użyciu systemu kolor wyróżnienia jako kolor pierwszego planu.|  
|`CLR_NONE`|Brak koloru mieszania. Obraz jest mieszane kolorem kontekstu urządzenia docelowego.|  
  
 Ten parametr jest używany tylko wtedy, gdy `fStyle` obejmuje `ILD_BLEND25` lub `ILD_BLEND50` flagi.  
  
 *fState*  
 Flaga określający stan rysowania. Ten element członkowski może zawierać jedną lub więcej flag stan listy obrazów.  
  
 *Ramki*  
 Wpływa na działanie efekty saturate i przenikanie alfa.  
  
 W przypadku użycia z **ILS_SATURATE**, ten element członkowski ma wartość, która jest dodawana do każdego składnika kolor Trzykolumnowa RGB dla każdego piksela ikony.  
  
 W przypadku użycia z **ILS_APLHA**, ten użytkownik będzie zawierać wartość dla kanału alfa. Ta wartość może być z zakresu od 0 do 255 0 jest całkowicie niewidoczne, a 255 całkowicie przezroczystości.  
  
 *crEffect*  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) efektów cienia i wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli obraz jest pomyślnie narysowanego; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz samodzielnie wypełnić struktury Win32, należy użyć pierwszej wersji. Druga wersja należy użyć, jeśli chcesz korzystać z co najmniej jeden z argumentów domyślnych MFC lub uniknąć Zarządzanie struktury.  
  
 Nakładka obraz to obraz, który ma zostać narysowana na podstawowy obraz, określona w funkcji członkowskiej przez `nImage` parametru. Rysowanie za pomocą maski nakładki [rysowania](#draw) funkcja członkowska o indeksie na podstawie co określony za pomocą maski nakładki [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) makra.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]  
  
##  <a name="enddrag"></a>CImageList::EndDrag  
 Wywołanie tej funkcji, aby zakończyć operację przeciągania.  
  
```  
static void PASCAL EndDrag();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby rozpocząć operacji przeciągania, użyj `BeginDrag` funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]  
  
##  <a name="extracticon"></a>CImageList::ExtractIcon  
 Wywołanie tej funkcji, aby utworzyć ikonę na podstawie obrazu i jego maskę powiązane w listy obrazów.  
  
```  
HICON ExtractIcon(int nImage);
```  
  
### <a name="parameters"></a>Parametry  
 `nImage`  
 Liczony od zera indeks obrazu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście ikony w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda polega na zachowanie [ImageList_ExtractIcon](http://msdn.microsoft.com/library/windows/desktop/bb761401) makra w celu utworzenia ikony. Zapoznaj się [ImageList_ExtractIcon](http://msdn.microsoft.com/library/windows/desktop/bb761401) makro uzyskać więcej informacji na temat tworzenia ikony oraz podczas oczyszczania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]  
  
##  <a name="fromhandle"></a>CImageList::FromHandle  
 Zwraca wskaźnik do `CImageList` obiektu, gdy uchwyt do listy obrazów.  
  
```  
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `hImageList`  
 Określa listę obrazu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CImageList` obiektu w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CImageList` nie jest już dołączony do uchwytu tymczasowej `CImageList` obiekt jest tworzony i dołączyć. To tymczasowe `CImageList` obiekt jest prawidłowy tylko do momentu przy następnym aplikacja ma czas bezczynności w pętli jego zdarzeń, w tym czasie wszystkie obiekty tymczasowe są usuwane.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]  
  
##  <a name="fromhandlepermanent"></a>CImageList::FromHandlePermanent  
 Zwraca wskaźnik do `CImageList` obiektu, gdy uchwyt do listy obrazów.  
  
```  
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `hImageList`  
 Określa listę obrazu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CImageList` obiektu w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CImageList` obiekt nie jest dołączony do uchwytu, **NULL** jest zwracany.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]  
  
##  <a name="getbkcolor"></a>CImageList::GetBkColor  
 Wywołanie tej funkcji można pobrać bieżący kolor tła dla listy obrazów.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość kolor RGB `CImageList` obiekt kolor tła.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CImageList::SetBkColor](#setbkcolor).  
  
##  <a name="getdragimage"></a>CImageList::GetDragImage  
 Pobiera listę tymczasowego obrazu używanego do przeciągania.  
  
```  
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,  
    LPPOINT lpPointHotSpot);
```  
  
### <a name="parameters"></a>Parametry  
 `lpPoint`  
 Adres [punktu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktury, która odbiera bieżącego przeciągnij pozycji.  
  
 *lpPointHotSpot*  
 Adres **punktu** strukturę, która odbiera przesunięcie obrazu przeciągania położeniu przeciągania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli powodzenia wskaźnik do tymczasowej obrazu listy jest używana do przeciąganie; w przeciwnym razie **NULL**.  
  
##  <a name="getimagecount"></a>CImageList::GetImageCount  
 Wywołanie tej funkcji, aby pobrać liczbę obrazów w listy obrazów.  
  
```  
int GetImageCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba obrazów.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CImageList::ExtractIcon](#extracticon).  
  
##  <a name="getimageinfo"></a>CImageList::GetImageInfo  
 Wywołanie tej funkcji można pobrać informacji o obrazie.  
  
```  
BOOL GetImageInfo(
    int nImage,  
    IMAGEINFO* pImageInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nImage`  
 Liczony od zera indeks obrazu.  
  
 *pImageInfo*  
 Wskaźnik do [IMAGEINFO](http://msdn.microsoft.com/library/windows/desktop/bb761393) struktury, która otrzymuje informacje o obrazie. Informacje przedstawione w tej strukturze można zmieniać bezpośrednio mapy bitowe dla obrazu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `IMAGEINFO` Struktura zawiera informacje o obrazie w listy obrazów.  
  
##  <a name="getsafehandle"></a>CImageList::GetSafeHandle  
 Wywołanie tej funkcji można pobrać **m_hImageList** element członkowski danych.  
  
```  
HIMAGELIST GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do listy obrazów dołączonych; w przeciwnym razie **NULL** Jeśli obiekt nie jest dołączony.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]  
  
##  <a name="m_himagelist"></a>CImageList::m_hImageList  
 Uchwyt listy obrazów dołączonych do tego obiektu.  
  
 **HIMAGELIST m_hImageList;**  
  
### <a name="remarks"></a>Uwagi  
 **M_hImageList** elementu członkowskiego danych jest publiczny zmiennej typu `HIMAGELIST`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]  
  
##  <a name="operator_himagelist"></a>CImageList::operator HIMAGELIST  
 Użyj tego operatora, aby uzyskać dołączone dojście `CImageList` obiektu.  
  
```  
operator HIMAGELIST() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli powodzenia dojścia do listy obrazów reprezentowany przez `CImageList` obiektu; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator jest operatora rzutowania obsługuje bezpośredniego użycia `HIMAGELIST` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]  
  
##  <a name="read"></a>CImageList::Read  
 Wywołanie tej funkcji można odczytać listy obrazów z archiwum.  
  
```  
BOOL Read(CArchive* pArchive);
```  
  
### <a name="parameters"></a>Parametry  
 `pArchive`  
 Wskaźnik do `CArchive` obiektu, z którego listy obrazów jest do odczytu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]  
  
##  <a name="remove"></a>CImageList::Remove  
 Wywołanie tej funkcji można usunąć obrazu z obiektu listy obrazów.  
  
```  
BOOL Remove(int nImage);
```  
  
### <a name="parameters"></a>Parametry  
 `nImage`  
 Liczony od zera indeks obrazu do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie elementy występujące po słowie `nImage` teraz Przenieś w dół o jedną pozycję. Na przykład jeśli listy obrazów zawiera dwa elementy, usunięcie pierwszy element spowoduje, że element pozostałych się teraz na pierwszym miejscu. `nImage`= 0 dla elementu na pierwszym miejscu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]  
  
##  <a name="replace"></a>CImageList::Replace  
 Wywołanie tej funkcji, aby zamienić obrazu w listy obrazów z nowego obrazu.  
  
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
 `nImage`  
 Liczony od zera indeks obrazu do zastąpienia.  
  
 `pbmImage`  
 Wskaźnik do mapy bitowej zawierającego obraz.  
  
 `pbmMask`  
 Wskaźnik do mapy bitowej zawierającego maski. Maska nie jest używana z listy obrazów, ten parametr jest ignorowana.  
  
 `hIcon`  
 Dojście do ikony, która zawiera mapę bitową i maska dla nowego obrazu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wersja zwracanie **BOOL** zwraca różną od zera w przypadku powodzenia; w przeciwnym razie wartość 0.  
  
 Wersja zwracanie `int` zwraca liczony od zera indeks obrazu w przypadku powodzenia; w przeciwnym razie - 1.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji Członkowskich po wywołaniu [SetImageCount](#setimagecount) można przypisać nową, prawidłową obrazów do symbolu zastępczego obrazu numery indeksu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CImageList::SetImageCount](#setimagecount).  
  
##  <a name="setbkcolor"></a>CImageList::SetBkColor  
 Wywołanie tej funkcji, aby ustawić kolor tła dla listy obrazów.  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>Parametry  
 `cr`  
 Kolor tła do ustawienia. Można ją `CLR_NONE`. W takim przypadku obrazy są rysowane niewidocznie za pomocą maski.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzednie kolor tła w przypadku powodzenia; w przeciwnym razie `CLR_NONE`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]  
  
##  <a name="setdragcursorimage"></a>CImageList::SetDragCursorImage  
 Tworzy nowy obraz przeciągania, łącząc danego obrazu (zwykle obraz kursora myszy) z bieżącego obrazu przeciągania.  
  
```  
BOOL SetDragCursorImage(
    int nDrag,  
    CPoint ptHotSpot);
```  
  
### <a name="parameters"></a>Parametry  
 *nDrag*  
 Indeks obrazu do połączenia z obrazem przeciągania.  
  
 `ptHotSpot`  
 Położenie punktu aktywnego w ramach nowego obrazu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ funkcji przeciągania korzystała z nowego obrazu podczas operacji przeciągania, należy używać systemu Windows [wartość](http://msdn.microsoft.com/library/windows/desktop/ms648396) Ukryj wskaźnik myszy rzeczywiste po wywołaniu funkcji `CImageList::SetDragCursorImage`. W przeciwnym razie system może być w dwóch kursory myszy w czasie trwania operacji przeciągania.  
  
##  <a name="setimagecount"></a>CImageList::SetImageCount  
 Wywołanie tej funkcji Członkowskich zresetować liczbę obrazów w `CImageList` obiektu.  
  
```  
BOOL SetImageCount(UINT uNewCount);
```  
  
### <a name="parameters"></a>Parametry  
 *uNewCount*  
 Wartość, określając nowe Liczba obrazów na liście obrazów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji członkowskiej, aby zwiększyć liczbę obrazów na liście obrazów wywoływać [zastąpić](#replace) dla każdego dodatkowego obrazu można przypisać nowe indeksy prawidłowy obrazów. Jeśli nie można przypisać indeksy prawidłowy obrazów, operacje rysowania nowe obrazy będą nieprzewidywalne.  
  
 Jeśli rozmiar listy obrazów za pomocą tej funkcji, są zwalniane skróconą obrazów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]  
  
##  <a name="setoverlayimage"></a>CImageList::SetOverlayImage  
 Wywołanie tej funkcji można dodać do listy obrazów, które mają być używane jako maski nakładki liczony od zera indeks obrazu.  
  
```  
BOOL SetOverlayImage(
    int nImage,  
    int nOverlay);
```  
  
### <a name="parameters"></a>Parametry  
 `nImage`  
 Liczony od zera indeks obrazu do użycia jako maski nakładki.  
  
 *nOverlay*  
 Jeden indeks maski nakładki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Maksymalnie cztery indeksów, które można dodać do listy.  
  
 Maska nakładki jest rysowany jako przezroczysty za pośrednictwem innego obrazu obrazu. Rysuj maski nakładki na obrazie przy użyciu [CImageList::Draw](#draw) funkcja członkowska o indeksie na podstawie co określony za pomocą maski nakładki **INDEXTOOVERLAYMASK** makra.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]  
  
##  <a name="write"></a>CImageList::Write  
 Wywołanie tej funkcji w celu zapisania obiektu listy obrazów do archiwum.  
  
```  
BOOL Write(CArchive* pArchive);
```  
  
### <a name="parameters"></a>Parametry  
 `pArchive`  
 Wskaźnik do `CArchive` obiektu, w którym ma być przechowywany listy obrazów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Clistctrl — klasa](../../mfc/reference/clistctrl-class.md)   
 [Ctabctrl — klasa](../../mfc/reference/ctabctrl-class.md)
