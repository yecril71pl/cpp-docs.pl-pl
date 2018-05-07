---
title: Klasa CGdiObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
dev_langs:
- C++
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba88269cf37f41cf8a594745eb2e98a57ccf64ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cgdiobject-class"></a>Klasa CGdiObject
Udostępnia klasę podstawową dla różnych rodzajów grafiki Windows urządzenia interfejsu (GDI) obiektów, takich jak mapy bitowe, regiony pędzle, pióra, palet i czcionek.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CGdiObject : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGdiObject::CGdiObject](#cgdiobject)|Konstruuje `CGdiObject` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGdiObject::Attach](#attach)|Dołącza obiektu GDI systemu Windows w celu `CGdiObject` obiektu.|  
|[CGdiObject::CreateStockObject](#createstockobject)|Pobiera dojścia do wstępnie zdefiniowanych pióra standardowych systemu Windows, Pędzle lub czcionki.|  
|[CGdiObject::DeleteObject](#deleteobject)|Usuwa obiekt Windows GDI dołączony do `CGdiObject` obiekt z pamięci przez zwolnienie wszystkich magazynów systemu skojarzony z obiektem.|  
|[CGdiObject::DeleteTempMap](#deletetempmap)|Usuwa wszystkie tymczasowe `CGdiObject` obiekty utworzone przez `FromHandle`.|  
|[CGdiObject::Detach](#detach)|Odłącza obiekt GDI systemu Windows z `CGdiObject` obiektu i zwraca uchwyt do obiektu GDI systemu Windows.|  
|[CGdiObject::FromHandle](#fromhandle)|Zwraca wskaźnik do `CGdiObject` obiekt na podstawie uchwyt do obiektu GDI systemu Windows.|  
|[CGdiObject::GetObject](#getobject)|Wypełnienia buforu z danymi, które opisano obiektów Windows GDI dołączona do `CGdiObject` obiektu.|  
|[CGdiObject::GetObjectType](#getobjecttype)|Pobiera typ obiektu GDI.|  
|[CGdiObject::GetSafeHandle](#getsafehandle)|Zwraca `m_hObject` chyba że `this` jest `NULL`, w którym to przypadku `NULL` jest zwracany.|  
|[CGdiObject::UnrealizeObject](#unrealizeobject)|Resetuje pochodzenia pędzla lub resetuje logiczną paletę.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGdiObject::operator! =](#operator_neq)|Określa, czy dwa obiekty GDI logicznie nie są takie same.|  
|[CGdiObject::operator ==](#operator_eq_eq)|Określa, czy dwa obiekty GDI są logicznie równe.|  
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|Pobiera `HANDLE` do przyłączonego obiektu GDI systemu Windows.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGdiObject::m_hObject](#m_hobject)|A `HANDLE` zawierający `HBITMAP`, `HPALETTE`, `HRGN`, `HBRUSH`, `HPEN`, lub `HFONT` dołączony do tego obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Nigdy nie twórz `CGdiObject` bezpośrednio. Zamiast tworzenia obiektu z jednej z jej klas pochodnych, takich jak `CPen` lub `CBrush`.  
  
 Aby uzyskać więcej informacji na temat `CGdiObject`, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGdiObject`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="attach"></a>  CGdiObject::Attach  
 Dołącza obiektu GDI systemu Windows w celu `CGdiObject` obiektu.  
  
```  
BOOL Attach(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 A `HANDLE` do obiektów GDI systemu Windows (na przykład `HPEN` lub `HBRUSH`).  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli załącznik zakończy się pomyślnie; w przeciwnym razie 0.  
  
##  <a name="cgdiobject"></a>  CGdiObject::CGdiObject  
 Konstruuje `CGdiObject` obiektu.  
  
```  
CGdiObject();
```  
  
### <a name="remarks"></a>Uwagi  
 Nigdy nie twórz `CGdiObject` bezpośrednio. Zamiast tworzenia obiektu z jednej z jej klas pochodnych, takich jak `CPen` lub **cbrush —**.  
  
##  <a name="createstockobject"></a>  CGdiObject::CreateStockObject  
 Pobiera dojścia do wstępnie zdefiniowanych standardowych pióra GDI systemu Windows, Pędzle lub czcionek i dołącza obiektu GDI `CGdiObject` obiektu.  
  
```  
BOOL CreateStockObject(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określanie typu podstawowego obiektu żądanego stałą. Zobacz parametr *fnObject* dla [GetStockObject](http://msdn.microsoft.com/library/windows/desktop/dd144925) w zestawie Windows SDK opis odpowiednie wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji w jednym z pochodnej klasy, która odpowiada typowi obiektu GDI systemu Windows, takich jak `CPen` standardowych pióra.  
  
##  <a name="deleteobject"></a>  CGdiObject::DeleteObject  
 Usuwa przyłączonego obiektu GDI systemu Windows z pamięci przez zwolnienie wszystkich magazynów systemu skojarzony z obiektem GDI systemu Windows.  
  
```  
BOOL DeleteObject();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiekt GDI został pomyślnie usunięty; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Magazynem skojarzonym z `CGdiObject` obiekt nie ma wpływu na tego wywołania. Aplikacja nie powinny wywoływać `DeleteObject` na `CGdiObject` obiekt, który jest aktualnie wybrany do kontekstu urządzenia.  
  
 Po usunięciu pędzla mapy bitowej skojarzone z pędzel nie zostanie usunięta. Mapa bitowa, należy usunąć niezależnie.  
  
##  <a name="deletetempmap"></a>  CGdiObject::DeleteTempMap  
 Wywoływana automatycznie przez `CWinApp` obsługi czas bezczynności, `DeleteTempMap` usuwa wszystkie tymczasowe `CGdiObject` obiekty utworzone przez `FromHandle`.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>Uwagi  
 `DeleteTempMap` Odłącza obiektów Windows GDI dołączona do tymczasowej `CGdiObject` obiektu przed usunięciem `CGdiObject` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]  
  
##  <a name="detach"></a>  CGdiObject::Detach  
 Odłącza obiekt GDI systemu Windows z `CGdiObject` obiektu i zwraca uchwyt do obiektu GDI systemu Windows.  
  
```  
HGDIOBJ Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `HANDLE` do Windows GDI obiekt odłączyć; w przeciwnym razie **NULL** Jeżeli żaden obiekt GDI nie jest podłączone.  
  
##  <a name="fromhandle"></a>  CGdiObject::FromHandle  
 Zwraca wskaźnik do `CGdiObject` obiekt na podstawie uchwyt do obiektu GDI systemu Windows.  
  
```  
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 A `HANDLE` do obiektów GDI systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CGdiObject` może to być tymczasowych lub trwałych.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CGdiObject` obiekt nie jest już dołączony do obiektu Windows GDI tymczasowej `CGdiObject` obiekt jest tworzony i dołączyć.  
  
 To tymczasowe `CGdiObject` obiektu jest prawidłowa tylko po ponownym aplikacja ma czas bezczynności w pętli jego zdarzeń, które zostaną usunięte wszystkie tymczasowe obiekty graficzne. Innymi słowy to jest, że tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu jedno okno.  
  
##  <a name="getobject"></a>  CGdiObject::GetObject  
 Wstawia buforu danych, który definiuje określony obiekt.  
  
```  
int GetObject(
    int nCount,  
    LPVOID lpObject) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nCount`  
 Określa liczbę bajtów do skopiowania do `lpObject` buforu.  
  
 `lpObject`  
 Wskazuje buforu dostarczone przez użytkownika, który będzie odbierać dane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba bajtów pobrać; w przeciwnym razie 0 Jeśli błąd występuje.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja pobiera struktury danych, którego typ zależy od typu obiektu graficznego, jak to przedstawiono na poniższej liście:  
  
|Obiekt|Typ buforu|  
|------------|-----------------|  
|`CPen`|[LOGPEN](../../mfc/reference/logpen-structure.md)|  
|`CBrush`|[LOGBRUSH](../../mfc/reference/logbrush-structure.md)|  
|`CFont`|[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)|  
|`CBitmap`|[MAPY BITOWEJ](../../mfc/reference/bitmap-structure.md)|  
|`CPalette`|**WORD**|  
|`CRgn`|Nieobsługiwane|  
  
 Jeśli obiekt jest `CBitmap` obiektu `GetObject` zwraca tylko szerokości, wysokości i informacji o formacie kolorów mapy bitowej. Rzeczywiste usługi bits mogą być pobierane przy użyciu [CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).  
  
 Jeśli obiekt jest `CPalette` obiektu `GetObject` pobiera **WORD** określająca liczbę wpisów w palecie. Funkcja nie pobiera [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) struktury, który definiuje palety. Aplikacja może uzyskać informacje na wpisy palety wywołując [CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).  
  
##  <a name="getobjecttype"></a>  CGdiObject::GetObjectType  
 Pobiera typ obiektu GDI.  
  
```  
UINT GetObjectType() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ obiektu, w przypadku powodzenia; w przeciwnym razie 0. Wartość może być jedną z następujących czynności:  
  
- **OBJ_BITMAP** mapy bitowej  
  
- **OBJ_BRUSH** pędzla  
  
- **OBJ_FONT** czcionki  
  
- **OBJ_PAL** palety  
  
- **OBJ_PEN** pióra  
  
- **OBJ_EXTPEN** rozszerzone pióra  
  
- **OBJ_REGION** regionu  
  
- **OBJ_DC** kontekstu urządzenia  
  
- **OBJ_MEMDC** pamięci kontekstu urządzenia  
  
- **OBJ_METAFILE** metaplik  
  
- **OBJ_METADC** metaplik kontekstu urządzenia  
  
- **OBJ_ENHMETAFILE** rozszerzony metaplik  
  
- **OBJ_ENHMETADC** rozszerzony metaplik kontekstu urządzenia  
  
##  <a name="getsafehandle"></a>  CGdiObject::GetSafeHandle  
 Zwraca `m_hObject` chyba że **to** jest **NULL**, w którym to przypadku **NULL** jest zwracany.  
  
```  
HGDIOBJ GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `HANDLE` do przyłączonego obiektu Windows GDI; w przeciwnym razie **NULL** Jeśli obiekt nie jest dołączony.  
  
### <a name="remarks"></a>Uwagi  
 To jest częścią modelu interfejsu dojścia ogólne i jest przydatne, gdy **NULL** jest nieprawidłowa lub specjalne wartość uchwytu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).  
  
##  <a name="m_hobject"></a>  CGdiObject::m_hObject  
 A `HANDLE` zawierający `HBITMAP`, **hrgn —**, `HBRUSH`, `HPEN`, `HPALETTE`, lub **HFONT** dołączony do tego obiektu.  
  
```  
HGDIOBJ m_hObject;  
```  
  
##  <a name="operator_neq"></a>  CGdiObject::operator! =  
 Określa, czy dwa obiekty GDI logicznie nie są takie same.  
  
```  
BOOL operator!=(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `obj`  
 Wskaźnik do istniejącej `CGdiObject`.  
  
### <a name="remarks"></a>Uwagi  
 Określa, czy obiekt GDI po lewej stronie nie jest równa obiektu GDI po prawej stronie.  
  
##  <a name="operator_eq_eq"></a>  CGdiObject::operator ==  
 Określa, czy dwa obiekty GDI są logicznie równe.  
  
```  
BOOL operator==(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `obj`  
 Odwołanie do istniejącej `CGdiObject`.  
  
### <a name="remarks"></a>Uwagi  
 Określa, czy obiekt GDI po lewej stronie jest taki sam, jak obiekt GDI po prawej stronie.  
  
##  <a name="operator_hgdiobj"></a>  CGdiObject::operator HGDIOBJ  
 Pobiera `HANDLE` do przyłączonego obiektu Windows GDI; w przeciwnym razie **NULL** Jeśli obiekt nie jest dołączony.  
  
```  
operator HGDIOBJ() const;  
```  
  
##  <a name="unrealizeobject"></a>  CGdiObject::UnrealizeObject  
 Resetuje pochodzenia pędzla lub resetuje logiczną paletę.  
  
```  
BOOL UnrealizeObject();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `UnrealizeObject` jest funkcji członkowskiej klasy `CGdiObject` klasy, jego powinna być wywoływana tylko na `CBrush` lub `CPalette` obiektów.  
  
 Aby uzyskać `CBrush` obiektów, `UnrealizeObject` instruuje system, aby zresetować pochodzenia danego pędzla przy następnym jest zaznaczony do kontekstu urządzenia. Jeśli obiekt jest `CPalette` obiektu `UnrealizeObject` instruuje system, aby zrealizować palety tak, jakby nie było wcześniej zrealizowany. Przy następnym aplikacja wywołuje [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) funkcji na palecie określony system całkowicie ponownie mapuje logiczną paletę do palety systemu.  
  
 `UnrealizeObject` Funkcja nie powinien być używany z podstawowych obiektów. `UnrealizeObject` Należy wywołać funkcję zawsze, gdy ustawiono nowego źródła pędzla (za pomocą klasy [CDC::SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg) funkcji). `UnrealizeObject` Funkcji, nie można wywoływać dla aktualnie zaznaczonego pędzla lub aktualnie zaznaczonego paletę wszystkich kontekstach wyświetlania.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cbitmap — klasa](../../mfc/reference/cbitmap-class.md)   
 [Cbrush — klasa](../../mfc/reference/cbrush-class.md)   
 [Cfont — klasa](../../mfc/reference/cfont-class.md)   
 [Cpalette — klasa](../../mfc/reference/cpalette-class.md)   
 [Cpen — klasa](../../mfc/reference/cpen-class.md)   
 [Klasa CRgn](../../mfc/reference/crgn-class.md)
