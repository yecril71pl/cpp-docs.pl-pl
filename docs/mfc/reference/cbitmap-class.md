---
title: "Cbitmap — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
dev_langs:
- C++
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 22922d29c09ee97a8b2a292953b4bf903ab6649e
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="cbitmap-class"></a>Cbitmap — klasa
Hermetyzuje mapy bitowej interfejsu (GDI) systemu Windows grafiki urządzenia i udostępnia funkcje elementów członkowskich do manipulowania mapy bitowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CBitmap : public CGdiObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBitmap::CBitmap](#cbitmap)|Konstruuje `CBitmap` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBitmap::CreateBitmap](#createbitmap)|Inicjuje obiekt o określonej szerokości, wysokości i wzorca bitowego mapę bitową pamięci zależne od urządzenia.|  
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|Inicjuje obiekt z mapę bitową o szerokości, wysokości i wzorca bitowego (jeśli został określony) podany w **mapy BITOWEJ** struktury.|  
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Inicjuje obiekt z mapą bitową, dzięki czemu jest zgodny z określonym urządzeniem.|  
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Inicjuje obiekt discardable mapą bitową, który jest zgodny z określonym urządzeniem.|  
|[CBitmap::FromHandle](#fromhandle)|Zwraca wskaźnik do `CBitmap` obiektu, gdy uchwyt do systemu Windows `HBITMAP` mapy bitowej.|  
|[CBitmap::GetBitmap](#getbitmap)|Wypełnia **mapy BITOWEJ** struktury z informacjami o mapy bitowej.|  
|[CBitmap::GetBitmapBits](#getbitmapbits)|Kopiuje bity Podana mapa bitowa do określonego bufora.|  
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Zwraca szerokość i wysokość mapy bitowej. Szerokość i wysokość uznaje się, że wcześniej zostały ustawione [SetBitmapDimension](#setbitmapdimension) funkcję elementu członkowskiego.|  
|[CBitmap::LoadBitmap](#loadbitmap)|Inicjuje obiekt przez ładowanie zasobów o nazwie mapy bitowej z plik wykonywalny aplikacji i dołączania mapy bitowej do obiektu.|  
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Ładuje mapę bitową, a następnie mapuje kolory do bieżącego kolorów systemu.|  
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Inicjuje obiekt przez ładowanie wstępnie zdefiniowanych mapy bitowej systemu Windows i dołączanie mapy bitowej do obiektu.|  
|[CBitmap::SetBitmapBits](#setbitmapbits)|Ustawia wartości bitowe określonej usługi bits mapy bitowej.|  
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Przypisuje mapę bitową w jednostkach milimetra 0,1 szerokości i wysokości.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HBITMAP CBitmap::operator](#operator_hbitmap)|Zwraca dojście Windows dołączona do `CBitmap` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby użyć `CBitmap` obiektów, konstruowania obiektu dołączenia dojścia mapy bitowej do jednego z funkcji Członkowskich inicjowania i następnie wywołać elementu członkowskiego obiektu funkcji.  
  
 Aby uzyskać więcej informacji na temat używania obiektów graficznych, takich jak `CBitmap`, zobacz [obiektów grafiki](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBitmap`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cbitmap"></a>CBitmap::CBitmap  
 Konstruuje `CBitmap` obiektu.  
  
```  
CBitmap();
```  
  
### <a name="remarks"></a>Uwagi  
 Wynikowy obiekt musi zostać zainicjowany z jednej z funkcji inicjowania elementu członkowskiego.  
  
##  <a name="createbitmap"></a>CBitmap::CreateBitmap  
 Inicjuje określonej szerokości, wysokości i wzorca bitowego mapę bitową pamięci zależne od urządzenia.  
  
```  
BOOL CreateBitmap(
    int nWidth,  
    int nHeight,  
    UINT nPlanes,  
    UINT nBitcount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>Parametry  
 `nWidth`  
 Określa szerokość (w pikselach) mapy bitowej.  
  
 `nHeight`  
 Określa wysokość mapy bitowej (w pikselach).  
  
 `nPlanes`  
 Określa liczbę płaszczyzn kolorów w mapie bitowej.  
  
 `nBitcount`  
 Określa liczbę kolorów bitów na piksel wyświetlania.  
  
 `lpBits`  
 Punkty na tablicę bajtów, które zawiera wartości bitowe początkowej mapy bitowej. Jeśli jest **NULL**, pozostanie nowej mapy bitowej niezainicjowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Dla mapy bitowej kolor albo `nPlanes` lub `nBitcount` parametru powinna być równa 1. Jeśli oba te parametry są ustawione na 1, `CreateBitmap` tworzy monochromatyczny mapy bitowej.  
  
 Mimo że mapy bitowej nie można wybrać bezpośrednio do wyświetlania na urządzeniach, można go ustawić jako bieżący mapy bitowej "pamięci urządzenia kontekstu" przy użyciu [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) i skopiowane do żadnego kontekstu zgodne urządzenie za pomocą [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) funkcji.  
  
 Po zakończeniu pracy z `CBitmap` obiekt utworzony przez `CreateBitmap` funkcji, najpierw wybierz mapy bitowej poza kontekstem urządzenia, a następnie usuń `CBitmap` obiektu.  
  
 Aby uzyskać więcej informacji, zobacz opis **bmBits** w **mapy BITOWEJ** struktury. [Mapy BITOWEJ](../../mfc/reference/bitmap-structure.md) struktury została opisana w sekcji [CBitmap::CreateBitmapIndirect](#createbitmapindirect) funkcję elementu członkowskiego.  
  
##  <a name="createbitmapindirect"></a>CBitmap::CreateBitmapIndirect  
 Inicjuje mapę bitową szerokości, wysokości i wzorca bitowego (jeśli został określony) podany w strukturze wskazywana przez `lpBitmap`.  
  
```  
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBitmap`  
 Wskazuje [mapy BITOWEJ](../../mfc/reference/bitmap-structure.md) struktury, który zawiera informacje o mapy bitowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Mimo że mapy bitowej nie można wybrać bezpośrednio do wyświetlania na urządzeniach, można go ustawić jako bieżący mapy bitowej dla kontekstu urządzenia pamięci za pomocą [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) i skopiowane do żadnego kontekstu zgodne urządzenie za pomocą [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) lub [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) funkcji. ( [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt) funkcji można kopiować mapy bitowej dla bieżącego pędzla bezpośrednio do kontekstu urządzenia wyświetlania.)  
  
 Jeśli **mapy BITOWEJ** wskazywanej przez `lpBitmap` parametru zostały wypełnione przy użyciu `GetObject` funkcji, nie są określone bity mapy bitowej i mapy bitowej jest zainicjowany. Aby zainicjować mapy bitowej, aplikację można użyć funkcji takich jak [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) lub [SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) do skopiowania bity mapy bitowej identyfikowane przez pierwszy parametr `CGdiObject::GetObject` do mapy bitowej utworzone przez `CreateBitmapIndirect`.  
  
 Po zakończeniu pracy z `CBitmap` utworzone za pomocą obiektu `CreateBitmapIndirect` funkcji, najpierw wybierz mapy bitowej poza kontekstem urządzenia, a następnie usuń `CBitmap` obiektu.  
  
##  <a name="createcompatiblebitmap"></a>CBitmap::CreateCompatibleBitmap  
 Inicjuje mapy bitowej, która jest zgodna z urządzenia określonego przez `pDC`.  
  
```  
BOOL CreateCompatibleBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Określa kontekst urządzenia.  
  
 `nWidth`  
 Określa szerokość (w pikselach) mapy bitowej.  
  
 `nHeight`  
 Określa wysokość mapy bitowej (w pikselach).  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Mapa bitowa ma taką samą liczbę płaszczyzn kolorów lub ten sam format bitów na piksel jako kontekst określonego urządzenia. Można wybrać jako bieżący mapy bitowej dla dowolnego urządzenia pamięci, który jest zgodny z określonym przez `pDC`.  
  
 Jeśli `pDC` jest kontekstu urządzenia pamięci mapy bitowej zwrócił ma tego samego formatu co mapy bitowej aktualnie wybranego w tym kontekście urządzenia. "Kontekstu urządzenia pamięci" to blok pamięci, który reprezentuje obszar wyświetlania. Może służyć do przygotowania obrazów w pamięci przed skopiowaniem ich do powierzchni wyświetlany zgodne urządzenie.  
  
 Po utworzeniu kontekstu urządzenia pamięci GDI automatycznie wybiera monochromatyczny standardowych mapy bitowej dla niego.  
  
 Ponieważ kolor kontekstu urządzenia pamięci może mieć kolor lub monochromatyczny map bitowych wybrane, format mapy bitowej zwrócony przez `CreateCompatibleBitmap` funkcja nie zawsze jest taka sama; jednak zawsze jest w formacie zgodne mapy bitowej dla kontekstu urządzenia nonmemory Format urządzenia.  
  
 Po zakończeniu pracy z `CBitmap` utworzone za pomocą obiektu `CreateCompatibleBitmap` funkcji, najpierw wybierz mapy bitowej poza kontekstem urządzenia, a następnie usuń `CBitmap` obiektu.  
  
##  <a name="creatediscardablebitmap"></a>CBitmap::CreateDiscardableBitmap  
 Inicjuje discardable mapy bitowej zgodnego z kontekstu urządzenia identyfikowane przez `pDC`.  
  
```  
BOOL CreateDiscardableBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Określa kontekst urządzenia.  
  
 `nWidth`  
 Określa szerokość (w bitach) mapy bitowej.  
  
 `nHeight`  
 Określa wysokość (w bitach) mapy bitowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Mapa bitowa ma taką samą liczbę płaszczyzn kolorów lub ten sam format bitów na piksel jako kontekst określonego urządzenia. Jako bieżący mapy bitowej dla urządzenie pamięci, który jest zgodny z określonym przez aplikację można wybrać tej mapy bitowej `pDC`.  
  
 Systemu Windows można odrzucić utworzony przez tę funkcję tylko wtedy, gdy aplikacja nie została wybrana go w kontekście wyświetlania mapy bitowej. Jeśli Windows odrzuca mapy bitowej, gdy nie jest zaznaczone i próbuje, wybierz aplikację później [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) funkcja zwróci **NULL**.  
  
 Po zakończeniu pracy z `CBitmap` utworzone za pomocą obiektu `CreateDiscardableBitmap` funkcji, najpierw wybierz mapy bitowej poza kontekstem urządzenia, a następnie usuń `CBitmap` obiektu.  
  
##  <a name="fromhandle"></a>CBitmap::FromHandle  
 Zwraca wskaźnik do `CBitmap` obiektu, gdy uchwyt do mapy bitowej GDI systemu Windows.  
  
```  
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `hBitmap`  
 Określa mapę bitową GDI systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CBitmap` obiektu w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CBitmap` obiekt nie jest już dołączony do uchwytu, tymczasowej `CBitmap` obiekt jest tworzony i dołączyć. To tymczasowe `CBitmap` obiekt jest prawidłowy tylko do momentu przy następnym aplikacja ma czas bezczynności w pętli jego zdarzeń, w czasu grafiki wszystkie tymczasowe obiekty zostaną usunięte. Innymi słowy to jest, że tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu jedno okno.  
  
##  <a name="getbitmap"></a>CBitmap::GetBitmap  
 Pobiera właściwości obrazu dołączone mapy bitowej.  
  
```  
int GetBitmap(BITMAP* pBitMap);
```  
  
### <a name="parameters"></a>Parametry  
 `pBitMap`  
 Wskaźnik do [struktury mapy BITOWEJ](../../mfc/reference/bitmap-structure.md) struktury, która odbierze właściwości obrazu. Ten parametr nie może być `NULL`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli metoda zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getbitmapbits"></a>CBitmap::GetBitmapBits  
 Kopiuje wzorca bitowego mapy bitowej dołączone do określonego bufora.  
  
```  
DWORD GetBitmapBits(
    DWORD dwCount,  
    LPVOID lpBits) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dwCount`  
 Liczba bajtów do skopiowania do buforu.  
  
 `lpBits`  
 Wskaźnik do buforu, który będzie otrzymywał mapy bitowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba bajtów kopiowania do buforu, jeśli metoda zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CBitmap::GetBitmap](#getbitmap) ustalenie wymagany rozmiar buforu.  
  
##  <a name="getbitmapdimension"></a>CBitmap::GetBitmapDimension  
 Zwraca szerokość i wysokość mapy bitowej.  
  
```  
CSize GetBitmapDimension() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość i wysokość mapy bitowej, mierzona w jednostkach milimetra 0,1. Wysokość jest **cy** członkiem `CSize` obiektu i szerokości znajduje się w **cx** elementu członkowskiego. Jeśli wysokość i szerokość bitmapy nie zostały ustawione za pomocą `SetBitmapDimension`, jest zwracana wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Szerokość i wysokość uznaje się, że wcześniej zostały ustawione za pomocą [SetBitmapDimension](#setbitmapdimension) funkcję elementu członkowskiego.  
  
##  <a name="loadbitmap"></a>CBitmap::LoadBitmap  
 Ładuje zasobu mapy bitowej o nazwie `lpszResourceName` lub identyfikowany przez numer identyfikacyjny w `nIDResource` z pliku wykonywalnego aplikacji.  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszResourceName`  
 Wskazuje zerem ciągu zawierającego nazwę zasobu mapy bitowej.  
  
 `nIDResource`  
 Określa identyfikator zasobu zasobu mapy bitowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Załadować mapy bitowej jest dołączony do `CBitmap` obiektu.  
  
 Jeśli mapy bitowej zidentyfikowana na podstawie `lpszResourceName` nie istnieje lub jeśli jest za mało pamięci, aby załadować mapy bitowej, funkcja zwraca wartość 0.  
  
 Można użyć [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funkcji, aby usunąć mapy bitowej załadowanych przez `LoadBitmap` funkcji, lub `CBitmap` destruktora spowoduje usunięcie obiektu dla Ciebie.  
  
> [!CAUTION]
>  Przed usunięciem obiektu, upewnij się, że nie jest zaznaczone do kontekstu urządzenia.  
  
 Następujące map bitowych zostały dodane do systemu Windows w wersji 3.1 lub nowszy:  
  
 **OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI**  
  
 Te mapy bitowe nie znajdują się w sterowniki urządzeń dla wersji systemu Windows 3.0 i wcześniejszych. Pełną listę mapy bitowe i wyświetlanie ich wyglądu zobacz zestaw Windows SDK.  
  
##  <a name="loadmappedbitmap"></a>CBitmap::LoadMappedBitmap  
 Wywołanie tej funkcji Członkowskich załadować mapy bitowej i mapowania kolorów do bieżącego kolorów systemu.  
  
```  
BOOL LoadMappedBitmap(
    UINT nIDBitmap,  
    UINT nFlags = 0,  
    LPCOLORMAP lpColorMap = NULL,  
    int nMapSize = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDBitmap`  
 Identyfikator zasobu mapy bitowej.  
  
 `nFlags`  
 Flaga mapy bitowej. Może być równa zero lub **CMB_MASKED**.  
  
 `lpColorMap`  
 Wskaźnik do **COLORMAP** strukturę, która zawiera informacje kolor potrzebne do mapowania map bitowych. Jeśli ten parametr ma **NULL**, funkcja używa domyślnej kolorów mapy.  
  
 *nMapSize*  
 Liczba kolorów mapy wskazywana przez `lpColorMap`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `LoadMappedBitmap` przypisze kolory zazwyczaj używany w przycisku symboli.  
  
 Informacji o tworzeniu zamapowanych mapy bitowej, zobacz opis funkcji Windows [CreateMappedBitmap](http://go.microsoft.com/fwlink/p/?linkid=230562) i [COLORMAP](http://msdn.microsoft.com/library/windows/desktop/bb760448) struktury w zestawie Windows SDK.  
  
##  <a name="loadoembitmap"></a>CBitmap::LoadOEMBitmap  
 Ładuje mapę bitową wstępnie zdefiniowanych używane przez system Windows.  
  
```  
BOOL LoadOEMBitmap(UINT nIDBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDBitmap`  
 Numer identyfikacyjny wstępnie zdefiniowanych mapy bitowej systemu Windows. Poniżej przedstawiono możliwe wartości z systemu WINDOWS. H:  
  
|||  
|-|-|  
|**OBM_BTNCORNERS**|**OBM_OLD_RESTORE**|  
|**OBM_BTSIZE**|**OBM_OLD_RGARROW**|  
|**OBM_CHECK**|**OBM_OLD_UPARROW**|  
|**OBM_CHECKBOXES**|**OBM_OLD_ZOOM**|  
|**OBM_CLOSE**|**OBM_REDUCE**|  
|**OBM_COMBO**|**OBM_REDUCED**|  
|**OBM_DNARROW**|**OBM_RESTORE**|  
|**OBM_DNARROWD**|**OBM_RESTORED**|  
|**OBM_DNARROWI**|**OBM_RGARROW**|  
|**OBM_LFARROW**|**OBM_RGARROWD**|  
|**OBM_LFARROWD**|**OBM_RGARROWI**|  
|**OBM_LFARROWI**|**OBM_SIZE**|  
|**OBM_MNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_CLOSE**|**OBM_UPARROWD**|  
|**OBM_OLD_DNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_LFARROW**|**OBM_ZOOM**|  
|**OBM_OLD_REDUCE**|**OBM_ZOOMD**|  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Bitmap o nazwach zaczynających **OBM_OLD** reprezentują map bitowych używanych przez wersje systemu Windows przed 3.0.  
  
 Należy pamiętać, że stała **OEMRESOURCE** muszą być zdefiniowane przed tym systemu WINDOWS. H, aby można było użyć dowolnego z **OBM_** stałe.  
  
##  <a name="operator_hbitmap"></a>HBITMAP CBitmap::operator  
 Użyj tego operatora, aby uzyskać dojście Windows GDI dołączonych `CBitmap` obiektu.  
  
```  
operator HBITMAP() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli się powiedzie, uchwyt do obiektu Windows GDI reprezentowany przez `CBitmap` obiektu; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator jest operatora rzutowania obsługuje bezpośredniego użycia `HBITMAP` obiektu.  
  
 Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz [obiektów grafiki](http://msdn.microsoft.com/library/windows/desktop/dd144962) w zestawie Windows SDK.  
  
##  <a name="setbitmapbits"></a>CBitmap::SetBitmapBits  
 Ustawia bity mapy bitowej wartości bitowe przez `lpBits`.  
  
```  
DWORD SetBitmapBits(
    DWORD dwCount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCount`  
 Określa liczbę bajtów wskazywana przez `lpBits`.  
  
 `lpBits`  
 Wskazuje **BAJTÓW** tablica, która zawiera wartości pikseli, który ma zostać skopiowany na `CBitmap` obiektu. Aby mapy bitowej można było poprawnie renderować obraz należy sformatować wartości odpowiadają wartości głębokość wysokość i szerokość kolorów, które zostały określone podczas tworzenia wystąpienia cbitmap —. Aby uzyskać więcej informacji, zobacz [CBitmap::CreateBitmap](#createbitmap).  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba bajtów używanych podczas ustawiania bitowa; 0, jeśli funkcja nie powiedzie się.  
  
##  <a name="setbitmapdimension"></a>CBitmap::SetBitmapDimension  
 Przypisuje mapę bitową w jednostkach milimetra 0,1 szerokości i wysokości.  
  
```  
CSize SetBitmapDimension(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `nWidth`  
 Określa szerokość mapy bitowej (w jednostkach 0,1 milimetra).  
  
 `nHeight`  
 Określa wysokość mapy bitowej (w jednostkach 0,1 milimetra).  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzednie wymiary mapy bitowej. Wysokość jest **cy** zmiennej członkowskiej z `CSize` obiektu i szerokości jest **cx** zmiennej członkowskiej.  
  
### <a name="remarks"></a>Uwagi  
 Interfejs GDI nie używa tych wartości, z wyjątkiem przypadków, aby zwrócić je po uruchomieniu [GetBitmapDimension](#getbitmapdimension) funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MDI](../../visual-cpp-samples.md)   
 [Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)

