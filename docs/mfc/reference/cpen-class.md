---
title: "Cpen — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 51ea9aadc5d5ca8fb5a5a253d2ddb5972bf0dfdc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cpen-class"></a>Cpen — klasa
Hermetyzuje pióra interfejsu (GDI) systemu Windows grafiki urządzenia.  
  
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
|[CPen::CreatePen](#createpen)|Tworzy logiczną pióra bardzo drobny lub geometrycznych z określonego stylu, szerokość i atrybuty pędzla i dołącza go do `CPen` obiektu.|  
|[CPen::CreatePenIndirect](#createpenindirect)|Tworzy pióra z styl, szerokość i kolor podany w [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) struktury i dołącza go do `CPen` obiektu.|  
|[CPen::FromHandle](#fromhandle)|Zwraca wskaźnik do `CPen` obiektu, gdy Windows `HPEN`.|  
|[CPen::GetExtLogPen](#getextlogpen)|Pobiera [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711) struktury.|  
|[CPen::GetLogPen](#getlogpen)|Pobiera [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) struktury.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPen::operator hpen —](#operator_hpen)|Zwraca dojście Windows dołączona do `CPen` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat używania `CPen`, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPen`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cpen"></a>CPen::CPen  
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
 `nPenStyle`  
 Określa styl pióra. Ten parametr w pierwszej wersji Konstruktor może być jedną z następujących wartości:  
  
- **PS_SOLID** tworzy stałe pióra.  
  
- **PS_DASH** tworzy kreskowane pióra. Prawidłowy tylko wtedy, gdy szerokość pióra jednostki 1 lub mniej, w urządzeniu.  
  
- **PS_DOT** tworzy kropkowanej pióra. Prawidłowy tylko wtedy, gdy szerokość pióra jednostki 1 lub mniej, w urządzeniu.  
  
- **PS_DASHDOT** tworzy pióra ze zmieniającymi się łączniki i kropki. Prawidłowy tylko wtedy, gdy szerokość pióra jednostki 1 lub mniej, w urządzeniu.  
  
- **PS_DASHDOTDOT** tworzy pióra ze zmieniającymi się łączniki i kropki dwa razy. Prawidłowy tylko wtedy, gdy szerokość pióra jednostki 1 lub mniej, w urządzeniu.  
  
- **PS_NULL** tworzy pióra wartości null.  
  
- **PS_INSIDEFRAME** tworzy Pióro rysuje wewnątrz ramki kształty zamknięte utworzonego przez funkcje dane wyjściowe GDI systemu Windows, które Określanie prostokąt ograniczający (na przykład **elipsy**, **prostokąt** , `RoundRect`, `Pie`, i `Chord` funkcji elementów członkowskich). Gdy ten styl jest używany z Windows GDI dane wyjściowe funkcji, które nie należy określać prostokąt ograniczający (na przykład `LineTo` funkcji członkowskiej), obszaru rysowania pióra nie jest ograniczona przez ramki.  
  
 Druga wersja `CPen` Konstruktor określa kombinację typu, stylu zakończenie i atrybuty sprzężenia. Wartości z każdej kategorii powinny być łączone przy użyciu bitowego operatora OR (&#124;). Typ pióra może być jedną z następujących wartości:  
  
- **PS_GEOMETRIC** tworzy geometrycznych pióra.  
  
- **PS_COSMETIC** tworzy bardzo drobny pióra.  
  
     Druga wersja `CPen` Konstruktor dodaje następujących stylów pióra `nPenStyle`:  
  
- **PS_ALTERNATE** tworzy pióra, która ustawia co inne pikseli. (Ten styl ma zastosowanie tylko w przypadku bardzo drobny pióra).  
  
- **PS_USERSTYLE** tworzy Pióro, które korzysta z tablicą stylów podane przez użytkownika.  
  
     Zakończenie może być jedną z następujących wartości:  
  
- **PS_ENDCAP_ROUND** zakończenia są round.  
  
- **PS_ENDCAP_SQUARE** zakończenia są kwadratowych.  
  
- **PS_ENDCAP_FLAT** zakończenia jest prosty.  
  
     Sprzężenie może być jedną z następujących wartości:  
  
- **PS_JOIN_BEVEL** ukośne są sprzężenia.  
  
- **PS_JOIN_MITER** sprzężeń są połączenia, gdy znajdują się w bieżącym określonym przez [SetMiterLimit](http://msdn.microsoft.com/library/windows/desktop/dd145076) funkcji. Jeśli sprzężenie przekracza ten limit, jest ukośne.  
  
- **PS_JOIN_ROUND** sprzężenia są round.  
  
 `nWidth`  
 Określa grubość pióra.  
  
-   Dla pierwszej wersji konstruktora Jeśli ta wartość wynosi 0, szerokość w jednostkach urządzenia jest zawsze 1 piksela, niezależnie od trybu mapowania.  
  
-   Dla drugiego wersja konstruktora Jeśli `nPenStyle` jest **PS_GEOMETRIC**, szerokość znajduje się w jednostkach logicznych. Jeśli `nPenStyle` jest **PS_COSMETIC**, szerokość musi być równa 1.  
  
 `crColor`  
 Zawiera kolor RGB pióra.  
  
 `pLogBrush`  
 Wskazuje `LOGBRUSH` struktury. Jeśli `nPenStyle` jest **PS_COSMETIC**, `lbColor` członkiem `LOGBRUSH` struktury Określa kolor pióra i `lbStyle` członkiem `LOGBRUSH` struktury musi mieć ustawioną **BS_ STAŁE**. Jeśli `nPenStyle` jest **PS_GEOMETRIC**, wszystkie elementy Członkowskie musi zostać użyty do określenia atrybuty pędzla pióra.  
  
 `nStyleCount`  
 Określa długość, w jednostkach bitowego `lpStyle` tablicy. Ta wartość nie może być zero, jeśli `nPenStyle` nie jest **PS_USERSTYLE**.  
  
 `lpStyle`  
 Wskazuje tablicy z bitowego wartości. Pierwsza wartość określa długość kreski pierwszy w stylu zdefiniowane przez użytkownika, druga wartość określa długość pierwszego miejsca i tak dalej. This, wskaźnik musi być **NULL** Jeśli `nPenStyle` nie jest **PS_USERSTYLE**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli używasz konstruktora bez argumentów musi inicjować powstałe w ten sposób `CPen` obiekt z `CreatePen`, `CreatePenIndirect`, lub `CreateStockObject` funkcji elementów członkowskich.  
  
 Jeśli używasz Konstruktor, który pobiera argumenty, nie dalsze inicjowania jest konieczne. Konstruktora z argumentami może zgłosić wyjątek, jeśli występują błędy, gdy zawsze powiedzie konstruktora bez argumentów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]  
  
##  <a name="createpen"></a>CPen::CreatePen  
 Tworzy logiczną pióra bardzo drobny lub geometrycznych z określonego stylu, szerokość i atrybuty pędzla i dołącza go do `CPen` obiektu.  
  
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
 `nPenStyle`  
 Określa styl pióra. Aby uzyskać listę możliwych wartości, zobacz `nPenStyle` parametru w [cpen —](#cpen) konstruktora.  
  
 `nWidth`  
 Określa grubość pióra.  
  
-   Dla pierwszej wersji `CreatePen`, jeśli ta wartość wynosi 0, szerokość w jednostkach urządzenia jest zawsze 1 piksela, niezależnie od trybu mapowania.  
  
-   Druga wersja dla `CreatePen`, jeśli `nPenStyle` jest **PS_GEOMETRIC**, szerokość znajduje się w jednostkach logicznych. Jeśli `nPenStyle` jest **PS_COSMETIC**, szerokość musi być równa 1.  
  
 `crColor`  
 Zawiera kolor RGB pióra.  
  
 `pLogBrush`  
 Wskazuje [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) struktury. Jeśli `nPenStyle` jest **PS_COSMETIC**, **lbColor** członkiem `LOGBRUSH` struktury Określa kolor pióra i `lbStyle` członkiem `LOGBRUSH` struktura musi być Ustaw **BS_SOLID**. Jeśli **nPenStyle** jest **PS_GEOMETRIC**, wszystkie elementy Członkowskie musi zostać użyty do określenia atrybuty pędzla pióra.  
  
 `nStyleCount`  
 Określa długość, w jednostkach bitowego `lpStyle` tablicy. Ta wartość nie może być zero, jeśli `nPenStyle` nie jest **PS_USERSTYLE**.  
  
 `lpStyle`  
 Wskazuje tablicy z bitowego wartości. Pierwsza wartość określa długość kreski pierwszy w stylu zdefiniowane przez użytkownika, druga wartość określa długość pierwszego miejsca i tak dalej. This, wskaźnik musi być **NULL** Jeśli `nPenStyle` nie jest **PS_USERSTYLE**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera w razie powodzenia lub zero, jeśli metoda nie powiedzie się.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszą wersję `CreatePen` inicjuje z określonego stylu, szerokość i kolor pióra. Jako bieżącego pióra we wszystkich kontekstach urządzenia można następnie wybrać pióra.  
  
 Pióra, które mają szerokość większą niż 1 piksela powinien zawsze mieć albo **PS_NULL**, **PS_SOLID**, lub **PS_INSIDEFRAME** stylu.  
  
 Jeśli ma pióra **PS_INSIDEFRAME** styl i kolor, który jest niezgodny z kolorów w tabeli kolorów logicznej pióra jest rysowany z kolor symulowany. **PS_SOLID** styl pióra nie może służyć do tworzenia pióra symulowanych kolorem. Styl **PS_INSIDEFRAME** jest taka sama jak **PS_SOLID** Jeśli szerokość pióra jest mniejsza niż lub równa 1.  
  
 Druga wersja `CreatePen` inicjuje logicznej pióra bardzo drobny lub geometryczne, z określonym stylu i szerokości i Pędzel atrybutów. Szerokość bardzo drobny pióro ma zawsze numer 1; szerokość pióra geometrycznych zawsze jest określona w jednostkach. Po aplikacja tworzy logiczną pióra, go można wybrać tego pióra do kontekstu urządzenia przez wywołanie metody [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) funkcji. Po wybraniu pióra do kontekstu urządzenia może służyć do rysowania linii i krzywych.  
  
-   Jeśli `nPenStyle` jest **PS_COSMETIC** i **PS_USERSTYLE**, wpisy w `lpStyle` tablicy w stylu jednostki określić długości kresek i spacji. Jednostka styl jest zdefiniowany przez urządzenie, którego pióra jest używany do rysowania linii.  
  
-   Jeśli `nPenStyle` jest **PS_GEOMETRIC** i **PS_USERSTYLE**, wpisy w `lpStyle` tablicy określić długości kresek i spacji w jednostkach logicznych.  
  
-   Jeśli `nPenStyle` jest **PS_ALTERNATE**, jednostki stylu zostanie zignorowana i ustawiono co inne pikseli.  
  
 Gdy aplikacja nie wymaga już danego pióra, powinny wywoływać [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) element członkowski funkcji lub zniszczenia `CPen` obiektów, zasób nie jest już używana. Aplikacja nie należy usuwać pióra, gdy pióro jest zaznaczone w kontekście urządzenia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]  
  
##  <a name="createpenindirect"></a>CPen::CreatePenIndirect  
 Inicjuje stylu, szerokość i kolor podany w strukturze wskazywana przez pióro `lpLogPen`.  
  
```  
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```  
  
### <a name="parameters"></a>Parametry  
 `lpLogPen`  
 Wskazuje systemu Windows [LOGPEN](../../mfc/reference/logpen-structure.md) struktury, który zawiera informacje o pióra.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Pióra, które mają szerokość większą niż 1 piksela powinien zawsze mieć albo **PS_NULL**, **PS_SOLID**, lub **PS_INSIDEFRAME** stylu.  
  
 Jeśli ma pióra **PS_INSIDEFRAME** styl i kolor, który jest niezgodny z kolorów w tabeli kolorów logicznej pióra jest rysowany z kolor symulowany. **PS_INSIDEFRAME** styl jest taki sam jak **PS_SOLID** Jeśli szerokość pióra jest mniejsza niż lub równa 1.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]  
  
##  <a name="fromhandle"></a>CPen::FromHandle  
 Zwraca wskaźnik do `CPen` obiekt na podstawie uchwyt do obiektu pióra GDI systemu Windows.  
  
```  
static CPen* PASCAL FromHandle(HPEN hPen);
```  
  
### <a name="parameters"></a>Parametry  
 *hpen —*  
 `HPEN`dojście do pióra GDI systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CPen` obiektu w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CPen` obiekt nie jest dołączony do uchwytu, tymczasowej `CPen` obiekt jest tworzony i dołączyć. To tymczasowe `CPen` obiekt jest prawidłowy tylko do momentu przy następnym aplikacja ma czas bezczynności w pętli jego zdarzeń, w czasu grafiki wszystkie tymczasowe obiekty zostaną usunięte. Innymi słowy tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu jedno okno.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]  
  
##  <a name="getextlogpen"></a>CPen::GetExtLogPen  
 Pobiera **EXTLOGPEN** struktury.  
  
```  
int GetExtLogPen(EXTLOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>Parametry  
 `pLogPen`  
 Wskazuje [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711) struktury, który zawiera informacje o pióra.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 **EXTLOGPEN** struktury definiuje styl, szerokość i atrybuty pędzla pióra. Na przykład wywołać `GetExtLogPen` pasujące do określonej stylu pióra.  
  
 Zobacz następujące tematy w zestawie Windows SDK dla informacji o atrybutach pióra:  
  
- [GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
- [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705)  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje wywołanie `GetExtLogPen` można pobrać atrybutów pióra, a następnie utwórz nowy, bardzo drobny pióra z tego samego koloru.  
  
 [!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]  
  
##  <a name="getlogpen"></a>CPen::GetLogPen  
 Pobiera `LOGPEN` struktury.  
  
```  
int GetLogPen(LOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>Parametry  
 `pLogPen`  
 Wskazuje [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) struktury zawierają informacje na temat pióra.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `LOGPEN` Definiuje struktury, style, kolor i wzorzec pióra.  
  
 Na przykład wywołać `GetLogPen` pasujące do określonej stylu pióra.  
  
 Zobacz następujące tematy w zestawie Windows SDK dla informacji o atrybutach pióra:  
  
- [GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje wywołanie `GetLogPen` pobrać znak pióra, a następnie utworzyć nowe, pełne pióra kolorem tego samego.  
  
 [!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]  
  
##  <a name="operator_hpen"></a>CPen::operator hpen —  
 Pobiera dołączone dojście Windows GDI `CPen` obiektu.  
  
```  
operator HPEN() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli się powiedzie, uchwyt do obiektu Windows GDI reprezentowany przez `CPen` obiektu; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator jest operatora rzutowania obsługuje bezpośredniego użycia `HPEN` obiektu.  
  
 Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz artykuł [obiektów grafiki](http://msdn.microsoft.com/library/windows/desktop/dd144962) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CBrush](../../mfc/reference/cbrush-class.md)
