---
title: Cbrush — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
dev_langs:
- C++
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39c5167c81d6c44fa62f9bff87c6c04f73f9f6d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cbrush-class"></a>Cbrush — klasa
Hermetyzuje pędzla interfejsu (GDI) systemu Windows grafiki urządzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CBrush : public CGdiObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBrush::CBrush](#cbrush)|Konstruuje `CBrush` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Inicjuje pędzla o stylu, kolor i wzorcem określonym w [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) struktury.|  
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Inicjuje pędzla ze wzorcem określonym przez map bitowych niezależnych od urządzenia (DIB).|  
|[CBrush::CreateHatchBrush](#createhatchbrush)|Inicjuje pędzla z określonym wzorcem kreskowane i kolor.|  
|[CBrush::CreatePatternBrush](#createpatternbrush)|Inicjuje pędzla ze wzorcem określonym przez mapy bitowej.|  
|[CBrush::CreateSolidBrush](#createsolidbrush)|Inicjuje z określonym pełny kolor pędzla.|  
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Tworzy pędzla, który jest domyślny kolor systemu.|  
|[CBrush::FromHandle](#fromhandle)|Zwraca wskaźnik do `CBrush` obiektu, gdy uchwyt do systemu Windows `HBRUSH` obiektu.|  
|[CBrush::GetLogBrush](#getlogbrush)|Pobiera [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) struktury.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HBRUSH CBrush::operator](#operator_hbrush)|Zwraca dojście Windows dołączona do `CBrush` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Umożliwia `CBrush` obiektów, utworzyć `CBrush` obiektu i przekaż go do dowolnego `CDC` funkcji członkowskiej, która wymaga pędzla.  
  
 Pędzle może być stałe, wyklutych lub deseń.  
  
 Aby uzyskać więcej informacji na temat `CBrush`, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBrush`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cbrush"></a>  CBrush::CBrush  
 Konstruuje `CBrush` obiektu.  
  
```  
CBrush(); 
CBrush(COLORREF crColor); 
CBrush(int nIndex, COLORREF crColor); 
explicit CBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `crColor`  
 Określa kolor pędzla jako kolor RGB. Jeśli jest wyklutych pędzla, ten parametr określa kolor kreskowaniu.  
  
 `nIndex`  
 Określa styl kreskowania pędzla. Może być jeden z następujących wartości:  
  
- `HS_BDIAGONAL` Dół kreskowania (od lewej do prawej), na 45 stopni  
  
- `HS_CROSS` Kreskowany poziome i pionowe  
  
- `HS_DIAGCROSS` Kreskowanie 45 stopni  
  
- `HS_FDIAGONAL` Górę kreskowania (od lewej do prawej), na 45 stopni  
  
- `HS_HORIZONTAL` Poziomy kreskowania  
  
- `HS_VERTICAL` Pionowy kreskowania  
  
 `pBitmap`  
 Wskazuje `CBitmap` obiekt, który określa mapę bitową, z którym rysują pędzla.  
  
### <a name="remarks"></a>Uwagi  
 `CBrush` ma cztery przeciążone konstruktory. Tworzy niezainicjowany konstruktora bez argumentów `CBrush` obiekt, który musi zostać zainicjowany przed jego użyciem.  
  
 Jeśli używasz konstruktora bez argumentów musi inicjować powstałe w ten sposób `CBrush` obiekt z [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush), lub [CreateDIBPatternBrush](#createdibpatternbrush). Jeśli używany jest jeden z konstruktorów, która przyjmuje argumenty, następnie żadne dodatkowe inicjowania jest konieczne. Konstruktorów z argumentami może zgłosić wyjątek, jeśli występują błędy, gdy zawsze powiedzie konstruktora bez argumentów.  
  
 Konstruktor za pomocą jednej [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parametru konstruuje pędzla jednolitym kolorem określony. Kolor określa wartości RGB i mogą być zbudowane z `RGB` makra w systemie WINDOWS. H.  
  
 Konstruktor z dwoma parametrami tworzy kreskowania pędzla. `nIndex` Parametr określa indeks kreskowanym wzorca. `crColor` Parametr określa kolor.  
  
 Konstruktora z `CBitmap` parametru konstruuje deseniem pędzla. Parametr identyfikuje mapy bitowej. Mapy bitowej jest zakłada się, że zostały utworzone przy użyciu [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), lub [ CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). Minimalny rozmiar mapy bitowej do użycia w deseń wypełnienia jest 8 x pikseli 8.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]  
  
##  <a name="createbrushindirect"></a>  CBrush::CreateBrushIndirect  
 Inicjuje pędzla o stylu, kolor i wzorcem określonym w [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) struktury.  
  
```  
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```  
  
### <a name="parameters"></a>Parametry  
 *lpLogBrush*  
 Wskazuje [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) struktury, który zawiera informacje o pędzla.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Następnie można wybrać pędzla jako bieżący pędzel dla dowolnego kontekstu urządzenia.  
  
 Pędzel utworzone przy użyciu map bitowych (1 płaszczyzny, 1 bity na piksel) w skali odcieni szarości jest rysowane przy użyciu bieżących kolorów tła i tekstu. Bieżący kolor tekstu będzie rysowany pikseli reprezentowany przez bit równa 0. Pikseli reprezentowany przez bit, ustaw wartość 1, zostanie narysowany bieżący kolor tła.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]  
  
##  <a name="createdibpatternbrush"></a>  CBrush::CreateDIBPatternBrush  
 Inicjuje pędzla ze wzorcem określonym przez map bitowych niezależnych od urządzenia (DIB).  
  
```  
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,  
    UINT nUsage);

 
BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,  
    UINT nUsage);
```  
  
### <a name="parameters"></a>Parametry  
 *hPackedDIB*  
 Określa obiekt pamięci globalnej zawierający spakowane map bitowych niezależnych od urządzenia (DIB).  
  
 *nUsage*  
 Określa, czy **[bmiColors]** pola [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) struktury danych (część "spakowane DIB") zawiera jawne wartości RGB lub wskaźników do aktualnie zrealizowanych logiczną paletę. Parametr musi mieć jedną z następujących wartości:  
  
- **DIB_PAL_COLORS** tabeli kolorów składa się z 16-bitowe indeksy tablicy.  
  
- **DIB_RGB_COLORS** tabeli kolorów zawiera wartości RGB literałów.  
  
 *lpPackedDIB*  
 Wskazuje spakowana DIB, składające się z `BITMAPINFO` struktury poprzedzającą tablicę bajtów Definiowanie pikseli mapy bitowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Następnie można wybrać pędzel dla dowolnego kontekstu urządzenia, który obsługuje rastrowych.  
  
 Dwie wersje różnią się w sposób obsługi DIB:  
  
-   W pierwszej wersji, można uzyskać dojścia do DIB wywołujesz systemu Windows **działanie funkcji GlobalAlloc** funkcji można przydzielić bloku pamięci globalnej i następnie wypełnienie pamięci spakowana DIB.  
  
-   W drugiej wersji nie jest konieczne do wywołania **działanie funkcji GlobalAlloc** można przydzielić pamięci dla spakowanych DIB.  
  
 Spakowana DIB składa się z `BITMAPINFO` struktury danych bezpośrednio po nim tablicę bajtów, który definiuje pikseli mapy bitowej. Mapy bitowe używane jako wzorce wypełnienia powinna być 8 x pikseli 8. Jeśli mapy bitowej jest większy, system Windows tworzy deseń wypełnienia przy użyciu tylko usługi bits odpowiadający pierwsze 8 wierszy i kolumn 8 pikseli w lewym górnym rogu mapy bitowej.  
  
 Kiedy aplikacja wybierze pędzla DIB dwóch kolorów do kontekstu urządzenia monochromatyczny, Windows ignoruje kolory określone w DIB i zamiast tego Wyświetla pędzla wzorzec przy użyciu bieżącego kolory tła i tekstu kontekst urządzenia. Pikseli mapowane na pierwszy kolor DIB (przy przesunięciu 0 w tabeli kolorów DIB) są wyświetlane przy użyciu kolor tekstu. Pikseli mapowane na drugi kolor (od przesunięcia 1 w tabeli kolorów) są wyświetlane przy użyciu kolor tła.  
  
 Aby dowiedzieć się, jak przy użyciu następujących funkcji systemu Windows zobacz zestaw Windows SDK:  
  
- [CreateDIBPatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183492) (Ta funkcja jest udostępniany tylko dla zgodności z aplikacjami napisane dla systemu Windows w wersjach starszych niż 3.0; użyj **CreateDIBPatternBrushPt** funkcji.)  
  
- [CreateDIBPatternBrushPt](http://msdn.microsoft.com/library/windows/desktop/dd183493) (tej funkcji należy używać aplikacji Win32).  
  
- [Działanie funkcji GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]  
  
##  <a name="createhatchbrush"></a>  CBrush::CreateHatchBrush  
 Inicjuje pędzla z określonym wzorcem kreskowane i kolor.  
  
```  
BOOL CreateHatchBrush(
    int nIndex,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa styl kreskowania pędzla. Może być jeden z następujących wartości:  
  
- `HS_BDIAGONAL` Dół kreskowania (od lewej do prawej), na 45 stopni  
  
- `HS_CROSS` Kreskowany poziome i pionowe  
  
- `HS_DIAGCROSS` Kreskowanie 45 stopni  
  
- `HS_FDIAGONAL` Górę kreskowania (od lewej do prawej), na 45 stopni  
  
- `HS_HORIZONTAL` Poziomy kreskowania  
  
- `HS_VERTICAL` Pionowy kreskowania  
  
 `crColor`  
 Określa kolor pędzla jako kolor RGB (kolor kreskowaniu). Zobacz [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) w zestawie SDK systemu Windows, aby uzyskać więcej informacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Następnie można wybrać pędzla jako bieżący pędzel dla dowolnego kontekstu urządzenia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]  
  
##  <a name="createpatternbrush"></a>  CBrush::CreatePatternBrush  
 Inicjuje pędzla ze wzorcem określonym przez mapy bitowej.  
  
```  
BOOL CreatePatternBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `pBitmap`  
 Identyfikuje mapy bitowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Następnie można wybrać pędzel dla dowolnego kontekstu urządzenia, który obsługuje rastrowych. Mapa bitowa identyfikowane przez `pBitmap` jest zwykle inicjowana przy użyciu [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), lub [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) funkcji.  
  
 Mapy bitowe używane jako wzorce wypełnienia powinna być 8 x pikseli 8. W przypadku większych mapy bitowej systemu Windows będzie używana tylko bity odpowiadający pierwsze 8 wiersze i kolumny pikseli w lewym górnym rogu mapy bitowej.  
  
 Pędzla mogą zostać usunięte bez wpływu na skojarzone mapy bitowej. Oznacza to, że mapy bitowej można utworzyć dowolną liczbę pędzle wzorca.  
  
 Pędzel utworzone za pomocą monochromatyczny mapy bitowej (płaszczyzna koloru 1, 1 bity na piksel) jest rysowane przy użyciu bieżących kolorów tła i tekstu. Pikseli reprezentowany przez bit równa 0 są pobierane z bieżący kolor tekstu. Pikseli reprezentowany przez bit, ustaw wartość 1, są rysowane bieżący kolor tła.  
  
 Aby uzyskać informacje o korzystaniu z [CreatePatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183508), systemu Windows funkcji, zobacz zestaw Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]  
  
##  <a name="createsolidbrush"></a>  CBrush::CreateSolidBrush  
 Inicjuje pędzla jednolitym kolorem określony.  
  
```  
BOOL CreateSolidBrush(COLORREF crColor);
```  
  
### <a name="parameters"></a>Parametry  
 `crColor`  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) struktury, która określa kolor pędzla. Kolor określa wartości RGB i mogą być zbudowane z `RGB` makra w systemie WINDOWS. H.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Następnie można wybrać pędzla jako bieżący pędzel dla dowolnego kontekstu urządzenia.  
  
 Kiedy aplikacja zakończy pędzla utworzone przez `CreateSolidBrush`, należy wybrać pędzla poza kontekst urządzenia.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CBrush::CBrush](#cbrush).  
  
##  <a name="createsyscolorbrush"></a>  CBrush::CreateSysColorBrush  
 Inicjuje kolor pędzla.  
  
```  
BOOL CreateSysColorBrush(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Określa indeks koloru. Ta wartość odpowiada kolor używany do rysowania jeden z elementów 21 okna. Zobacz [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) w zestawie SDK systemu Windows, aby uzyskać listę wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Następnie można wybrać pędzla jako bieżący pędzel dla dowolnego kontekstu urządzenia.  
  
 Kiedy aplikacja zakończy pędzla utworzone przez `CreateSysColorBrush`, należy wybrać pędzla poza kontekst urządzenia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]  
  
##  <a name="fromhandle"></a>  CBrush::FromHandle  
 Zwraca wskaźnik do `CBrush` obiektu, gdy uchwyt do systemu Windows [HBRUSH](#operator_hbrush) obiektu.  
  
```  
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```  
  
### <a name="parameters"></a>Parametry  
 `hBrush`  
 `HANDLE` Aby pędzla GDI systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CBrush` obiektu w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CBrush` obiekt nie jest już dołączony do uchwytu, tymczasowej `CBrush` obiekt jest tworzony i dołączyć. To tymczasowe `CBrush` obiekt jest prawidłowy tylko do następnego wznowienia aplikacja ma czas bezczynności w jego pętli zdarzenia. W tej chwili wszystkich tymczasowych obiektów graficznych są usuwane. Innymi słowy tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu jedno okno.  
  
 Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz [obiektów grafiki](http://msdn.microsoft.com/library/windows/desktop/dd144962) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CBrush::CBrush](#cbrush).  
  
##  <a name="getlogbrush"></a>  CBrush::GetLogBrush  
 Wywołanie tej funkcji Członkowskich pobrać `LOGBRUSH` struktury.  
  
```  
int GetLogBrush(LOGBRUSH* pLogBrush);
```  
  
### <a name="parameters"></a>Parametry  
 `pLogBrush`  
 Wskazuje [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) struktury, który zawiera informacje o pędzla.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, a `pLogBrush` nieprawidłowy wskaźnik, wartość zwracana jest liczba bajtów przechowywanych w buforze.  
  
 Jeśli funkcja zakończy się powodzeniem, a `pLogBrush` jest **NULL**, jest zwracana wartość liczbę bajtów wymaganą do przechowywania informacji o funkcji będzie przechowywać w buforze.  
  
 Jeśli funkcja nie powiedzie się, zwracana wartość to 0.  
  
### <a name="remarks"></a>Uwagi  
 `LOGBRUSH` Struktury definiuje styl, kolor i wzoru pędzla.  
  
 Na przykład wywołać `GetLogBrush` odpowiadające konkretny kolor lub deseń mapy bitowej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]  
  
##  <a name="operator_hbrush"></a>  HBRUSH CBrush::operator  
 Użyj tego operatora, aby uzyskać dojście Windows GDI dołączonych `CBrush` obiektu.  
  
```  
operator HBRUSH() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli się powiedzie, uchwyt do obiektu Windows GDI reprezentowany przez `CBrush` obiektu; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator jest operatora rzutowania obsługuje bezpośredniego użycia `HBRUSH` obiektu.  
  
 Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz [obiektów grafiki](http://msdn.microsoft.com/library/windows/desktop/dd144962) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC PROPDLG](../../visual-cpp-samples.md)   
 [Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cbitmap — klasa](../../mfc/reference/cbitmap-class.md)   
 [Klasa CDC](../../mfc/reference/cdc-class.md)
