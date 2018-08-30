---
title: Klasa CPen | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
dev_langs:
- C++
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60fb1c219068cc0c59f908688ea5c471946458ad
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204144"
---
# <a name="cpen-class"></a>Cpen — klasa
Hermetyzuje pióro Windows grafiki urządzenia interface (GDI).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPen : public CGdiObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPen::CPen](#cpen)|Konstruuje `CPen` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPen::CreatePen](#createpen)|Tworzy logiczną pióra kosmetycznych lub geometryczne przy użyciu stylu określonego, szerokość i atrybuty pędzla i dołącza go do `CPen` obiektu.|  
|[CPen::CreatePenIndirect](#createpenindirect)|Tworzy pióra przy użyciu stylu, szerokość i kolor w [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen) struktury i dołącza go do `CPen` obiektu.|  
|[CPen::FromHandle](#fromhandle)|Zwraca wskaźnik do `CPen` obiektu, gdy hpen — Windows.|  
|[CPen::GetExtLogPen](#getextlogpen)|Pobiera [EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen) struktury.|  
|[CPen::GetLogPen](#getlogpen)|Pobiera [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen) struktury.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPen::operator hpen —](#operator_hpen)|Zwraca uchwyt Windows dołączonych do `CPen` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat korzystania z `CPen`, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPen`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cpen"></a>  CPen::CPen  
 Konstruuje `CPen` obiektu.  
  
```  
CPen();

 
CPen(
    int nPenStyle,  
    int nWidth,  
    COLORREF crColor);

 
CPen(
    int nPenStyle,  
    int nWidth,  
    const LOGBRUSH* pLogBrush,  
    int nStyleCount = 0,  
    const DWORD* lpStyle = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nPenStyle*  
 Określa styl pióra. Ten parametr w pierwszej wersji Konstruktor może być jedną z następujących wartości:  
  
- PS_SOLID tworzy pełny pióra.  
  
- PS_DASH tworzy kreskowane pióra. Prawidłowe tylko wtedy, gdy szerokość pióra jednostek 1 lub mniej, w urządzeniu.  
  
- PS_DOT tworzy kropkowana pióra. Prawidłowe tylko wtedy, gdy szerokość pióra jednostek 1 lub mniej, w urządzeniu.  
  
- Tworzy PS_DASHDOT pióra ze zmieniającymi się kreski oraz kropki. Prawidłowe tylko wtedy, gdy szerokość pióra jednostek 1 lub mniej, w urządzeniu.  
  
- Tworzy PS_DASHDOTDOT a pióra ze zmieniającymi się łączniki i kropki double. Prawidłowe tylko wtedy, gdy szerokość pióra jednostek 1 lub mniej, w urządzeniu.  
  
- PS_NULL tworzy pióra o wartości null.  
  
- PS_INSIDEFRAME tworzy produkowane przez Pióro, który rysuje wewnątrz ramki kształty zamknięte przez Windows GDI dane wyjściowe funkcji, które określają prostokąt otaczający (na przykład `Ellipse`, `Rectangle`, `RoundRect`, `Pie`i `Chord`funkcji elementów członkowskich). Gdy ten styl jest używany z Windows GDI dane wyjściowe funkcji, które nie określaj prostokąt otaczający (na przykład `LineTo` składowa), obszaru rysowania pióra nie jest ograniczone przez ramkę.  
  
 Druga wersja `CPen` Konstruktor określa kombinację typu, stylu, zakończenie i atrybuty sprzężenia. Wartości z każdej kategorii powinny być one łączone przy użyciu bitowego operatora OR (&#124;). Typ pióra może być jedną z następujących wartości:  
  
- PS_GEOMETRIC tworzy geometrycznych pióra.  
  
- PS_COSMETIC tworzy kosmetycznych pióra.  
  
     Druga wersja `CPen` Konstruktor dodaje następujące style pióra *nPenStyle*:  
  
- PS_ALTERNATE tworzy pióra, która ustawia co drugi piksel. (Ten styl jest tylko w przypadku kosmetycznych pióra).  
  
- Tworzy PS_USERSTYLE pióra, który używa tablicy stylu podane przez użytkownika.  
  
     Zakończenie końca może być jednym z następujących wartości:  
  
- PS_ENDCAP_ROUND zakończenia są Rundy.  
  
- PS_ENDCAP_SQUARE zakończenia są kwadratowe.  
  
- PS_ENDCAP_FLAT zakończenia są prostego.  
  
     Sprzężenia może być jednym z następujących wartości:  
  
- Dołącza PS_JOIN_BEVEL są ukośne.  
  
- Dołącza PS_JOIN_MITER są połączenia znajdujących się w bieżącym określonym przez [SetMiterLimit](/windows/desktop/api/wingdi/nf-wingdi-setmiterlimit) funkcji. Jeśli sprzężenia przekracza ten limit, jest ukośne.  
  
- Dołącza PS_JOIN_ROUND są Rundy.  
  
 *nWidth*  
 Określa grubość pióra.  
  
-   Pierwsza wersja konstruktora Jeśli ta wartość wynosi 0, szerokość w jednostkach urządzenia jest zawsze 1 piksela, niezależnie od tego trybu mapowania.  
  
-   Dla drugiego wersja konstruktora Jeśli *nPenStyle* jest PS_GEOMETRIC, szerokość znajduje się w jednostkach logicznych. Jeśli *nPenStyle* jest PS_COSMETIC, szerokość musi być równa 1.  
  
 *crColor*  
 Zawiera kolor RGB pióra.  
  
 *pLogBrush*  
 Wskazuje `LOGBRUSH` struktury. Jeśli *nPenStyle* jest PS_COSMETIC, *lbColor* członkiem `LOGBRUSH` struktury Określa kolor pióra i *lbStyle* członkiem `LOGBRUSH` Struktura musi być równa BS_SOLID. Jeśli *nPenStyle* jest PS_GEOMETRIC, wszystkie elementy Członkowskie może służyć do określania atrybutów pędzla pióra.  
  
 *nStyleCount*  
 Określa długość w jednostkach bitowego *lpStyle* tablicy. Ta wartość musi być zero, jeśli *nPenStyle* nie jest PS_USERSTYLE.  
  
 *lpStyle*  
 Wskazuje na tablicę wartości bitowego. Pierwsza wartość określa długość kreski pierwszy w stylu zdefiniowanych przez użytkownika, druga wartość Określa pierwszą przestrzeń i tak dalej. This, wskaźnik musi mieć wartość NULL, jeśli *nPenStyle* nie jest PS_USERSTYLE.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli korzystasz z konstruktora bez argumentów, należy zainicjować wynikowy `CPen` obiekt z `CreatePen`, `CreatePenIndirect`, lub `CreateStockObject` funkcji elementów członkowskich.  
  
 Jeśli korzystasz z konstruktora, który przyjmuje argumenty, nie dalsze inicjowania jest konieczne. Konstruktor z argumentami może zgłosić wyjątek, jeśli zostaną napotkane błędy, gdy konstruktor bez argumentów zawsze powiedzie się.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]  
  
##  <a name="createpen"></a>  CPen::CreatePen  
 Tworzy logiczną pióra kosmetycznych lub geometryczne przy użyciu stylu określonego, szerokość i atrybuty pędzla i dołącza go do `CPen` obiektu.  
  
```  
BOOL CreatePen(
    int nPenStyle,  
    int nWidth,  
    COLORREF crColor);

 
BOOL CreatePen(
    int nPenStyle,  
    int nWidth,  
    const LOGBRUSH* pLogBrush,  
    int nStyleCount = 0,  
    const DWORD* lpStyle = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nPenStyle*  
 Określa styl pióra. Aby uzyskać listę możliwych wartości, zobacz *nPenStyle* parametru w [CPen](#cpen) konstruktora.  
  
 *nWidth*  
 Określa grubość pióra.  
  
-   W pierwszej wersji programu `CreatePen`, jeśli ta wartość wynosi 0, szerokość w jednostkach urządzenia jest zawsze 1 piksela, niezależnie od tego trybu mapowania.  
  
-   Druga wersja dla `CreatePen`, jeśli *nPenStyle* jest PS_GEOMETRIC, szerokość znajduje się w jednostkach logicznych. Jeśli *nPenStyle* jest PS_COSMETIC, szerokość musi być równa 1.  
  
 *crColor*  
 Zawiera kolor RGB pióra.  
  
 *pLogBrush*  
 Wskazuje [LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) struktury. Jeśli *nPenStyle* jest PS_COSMETIC, `lbColor` członkiem `LOGBRUSH` struktury Określa kolor pióra i *lbStyle* członkiem `LOGBRUSH` struktury musi być równa BS_ STAŁE. Jeśli nPenStyle PS_GEOMETRIC, wszystkie elementy Członkowskie musi służyć do określania atrybutów pędzla pióra.  
  
 *nStyleCount*  
 Określa długość w jednostkach bitowego *lpStyle* tablicy. Ta wartość musi być zero, jeśli *nPenStyle* nie jest PS_USERSTYLE.  
  
 *lpStyle*  
 Wskazuje na tablicę wartości bitowego. Pierwsza wartość określa długość kreski pierwszy w stylu zdefiniowanych przez użytkownika, druga wartość Określa pierwszą przestrzeń i tak dalej. This, wskaźnik musi mieć wartość NULL, jeśli *nPenStyle* nie jest PS_USERSTYLE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli kończy się pomyślnie, lub zero, jeśli metoda nie powiedzie się.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsza wersja `CreatePen` inicjuje przy użyciu stylu określonego, szerokość i kolor pióra. Jako bieżącego pióra we wszystkich kontekstach urządzenia można następnie wybrać pióra.  
  
 Pióra, które mają szerokość większą niż 1 piksel powinny zawsze występować PS_NULL, PS_SOLID lub PS_INSIDEFRAME stylu.  
  
 Jeśli styl PS_INSIDEFRAME i kolor, który nie pasuje do koloru w tabeli kolorów logiczne pióra, pióro jest rysowana szarych kolorem. Styl pióra PS_SOLID, nie może służyć do tworzenia pióra szarych kolorem. Styl PS_INSIDEFRAME jest taka sama jak PS_SOLID, jeśli szerokość pióra jest mniejsza niż lub równa 1.  
  
 Druga wersja `CreatePen` inicjuje logiczne pióra kosmetycznych lub geometryczne, określonym stylu i szerokości i odświeżyć atrybutów. Szerokość kosmetycznych pióro ma zawsze numer 1; szerokość geometrycznych pióra jest zawsze określona w jednostkach. Po utworzeniu aplikacji logicznej pióra, jego można wybrać tego pióra do kontekstu urządzenia przez wywołanie metody [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) funkcji. Po wybraniu pióra do kontekstu urządzenia może służyć do rysowania linii i krzywych.  
  
-   Jeśli *nPenStyle* PS_COSMETIC i PS_USERSTYLE, wpisów w *lpStyle* tablicy określ długość i miejsca do magazynowania w jednostkach stylu. Jednostka styl jest zdefiniowany przez urządzenie, w którym pióra jest używany, aby narysować linię.  
  
-   Jeśli *nPenStyle* PS_GEOMETRIC i PS_USERSTYLE, wpisów w *lpStyle* tablicy określ długość i miejsca do magazynowania w jednostkach logicznych.  
  
-   Jeśli *nPenStyle* PS_ALTERNATE, jednostki stylu jest ignorowana, a co drugi piksel jest ustawiana.  
  
 Gdy aplikacja nie wymaga już danego pióra, powinny wywoływać [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) element członkowski funkcji lub zniszczenia `CPen` obiektu, zasób nie jest już używana. Aplikacja nie należy usuwać pióra, gdy pióro jest zaznaczona w kontekście urządzenia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]  
  
##  <a name="createpenindirect"></a>  CPen::CreatePenIndirect  
 Inicjuje Pióro, które ma styl, szerokość i kolor w strukturze wskazywany przez *lpLogPen*.  
  
```  
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```  
  
### <a name="parameters"></a>Parametry  
 *lpLogPen*  
 Wskazuje Windows [LOGPEN](../../mfc/reference/logpen-structure.md) strukturę, która zawiera informacje o pióra.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Pióra, które mają szerokość większą niż 1 piksel powinny zawsze występować PS_NULL, PS_SOLID lub PS_INSIDEFRAME stylu.  
  
 Jeśli styl PS_INSIDEFRAME i kolor, który nie pasuje do koloru w tabeli kolorów logiczne pióra, pióro jest rysowana szarych kolorem. Styl PS_INSIDEFRAME jest taka sama jak PS_SOLID, jeśli szerokość pióra jest mniejsza niż lub równa 1.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]  
  
##  <a name="fromhandle"></a>  CPen::FromHandle  
 Zwraca wskaźnik do `CPen` obiektów nadana uchwyt obiekt pen Windows GDI.  
  
```  
static CPen* PASCAL FromHandle(HPEN hPen);
```  
  
### <a name="parameters"></a>Parametry  
 *hpen —*  
 `HPEN` Obsługa pióro Windows GDI.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CPen` obiektu, jeśli operacja się powiedzie; w przeciwnym razie wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CPen` obiektu nie jest dołączony do uchwyt tymczasowego `CPen` obiekt zostanie utworzony i dołączony. Ten tymczasowy `CPen` obiekt jest prawidłowy tylko do momentu przy następnym aplikacji ma czas bezczynności, po jego pętlę zdarzeń, w której czas wszystkich tymczasowych grafiki obiekty zostaną usunięte. Innymi słowy tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu w jednym oknie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]  
  
##  <a name="getextlogpen"></a>  CPen::GetExtLogPen  
 Pobiera `EXTLOGPEN` struktury.  
  
```  
int GetExtLogPen(EXTLOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>Parametry  
 *pLogPen*  
 Wskazuje [EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen) strukturę, która zawiera informacje o pióra.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `EXTLOGPEN` Definiuje struktury, style, szerokość i atrybuty pędzla pióra. Na przykład wywołać `GetExtLogPen` pasujące do konkretnego stylu pióra.  
  
 Zobacz następujące tematy w zestawie Windows SDK dla informacji o atrybutach pióra:  
  
- [GetObject](/windows/desktop/api/wingdi/nf-wingdi-getobject)  
  
- [EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen)  
  
- [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)  
  
- [ExtCreatePen](/windows/desktop/api/wingdi/nf-wingdi-extcreatepen)  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje wywołanie `GetExtLogPen` można pobrać atrybutów pióra, a następnie utwórz nowe, kosmetycznych pióra przy użyciu tego samego koloru.  
  
 [!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]  
  
##  <a name="getlogpen"></a>  CPen::GetLogPen  
 Pobiera `LOGPEN` struktury.  
  
```  
int GetLogPen(LOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>Parametry  
 *pLogPen*  
 Wskazuje [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen) struktury zawierają informacje na temat pióra.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `LOGPEN` Definiuje struktury, style, kolor i wzorzec pióra.  
  
 Na przykład wywołać `GetLogPen` pasujące do konkretnego stylu pióra.  
  
 Zobacz następujące tematy w zestawie Windows SDK dla informacji o atrybutach pióra:  
  
- [GetObject](/windows/desktop/api/wingdi/nf-wingdi-getobject)  
  
- [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje wywołanie `GetLogPen` można pobrać znaku pióra, a następnie utwórz nowe, pełne pióra przy użyciu tego samego koloru.  
  
 [!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]  
  
##  <a name="operator_hpen"></a>  CPen::operator hpen —  
 Pobiera uchwyt Windows GDI dołączonych `CPen` obiektu.  
  
```  
operator HPEN() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, dojścia do obiektu Windows GDI reprezentowany przez `CPen` obiektu; w przeciwnym razie wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator jest operatora rzutowania, który obsługuje bezpośredniego użycia obiektu hpen —.  
  
 Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz artykuł [obiektów grafiki](/windows/desktop/gdi/graphic-objects) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CBrush](../../mfc/reference/cbrush-class.md)
