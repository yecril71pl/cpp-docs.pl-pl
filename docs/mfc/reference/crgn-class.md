---
title: Klasa CRgn | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
dev_langs:
- C++
helpviewer_keywords:
- CRgn [MFC], CRgn
- CRgn [MFC], CombineRgn
- CRgn [MFC], CopyRgn
- CRgn [MFC], CreateEllipticRgn
- CRgn [MFC], CreateEllipticRgnIndirect
- CRgn [MFC], CreateFromData
- CRgn [MFC], CreateFromPath
- CRgn [MFC], CreatePolygonRgn
- CRgn [MFC], CreatePolyPolygonRgn
- CRgn [MFC], CreateRectRgn
- CRgn [MFC], CreateRectRgnIndirect
- CRgn [MFC], CreateRoundRectRgn
- CRgn [MFC], EqualRgn
- CRgn [MFC], FromHandle
- CRgn [MFC], GetRegionData
- CRgn [MFC], GetRgnBox
- CRgn [MFC], OffsetRgn
- CRgn [MFC], PtInRegion
- CRgn [MFC], RectInRegion
- CRgn [MFC], SetRectRgn
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d5556db19d7f0ec92f915dda49dfeb24390ab70
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="crgn-class"></a>Klasa CRgn
Hermetyzuje region interfejsu (GDI) systemu Windows grafiki urządzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CRgn : public CGdiObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRgn::CRgn](#crgn)|Konstruuje `CRgn` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRgn::CombineRgn](#combinergn)|Ustawia `CRgn` obiekt, tak aby jest odpowiednikiem złożenie dwóch określony `CRgn` obiektów.|  
|[CRgn::CopyRgn](#copyrgn)|Ustawia `CRgn` obiekt tak, aby kopii określonego `CRgn` obiektu.|  
|[CRgn::CreateEllipticRgn](#createellipticrgn)|Inicjuje `CRgn` obiektu o eliptycznej regionu.|  
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Inicjuje `CRgn` obiektu o eliptycznej region zdefiniowany przez [RECT](../../mfc/reference/rect-structure1.md) struktury.|  
|[CRgn::CreateFromData](#createfromdata)|Tworzy obszar z danego regionu i przekształcania danych.|  
|[CRgn::CreateFromPath](#createfrompath)|Tworzy obszar ze ścieżki, który wybrano w kontekście danego urządzenia.|  
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|Inicjuje `CRgn` obiektu za pomocą wielokątne obszaru. System wielokąta zostanie automatycznie zamknięte, jeśli to konieczne, za pomocą rysowania linii z ostatnim wierzchołku jako pierwszy.|  
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|Inicjuje `CRgn` obiektu za pomocą obszaru składający się z szeregu zamkniętych wielokątów. Wielokąty mogą być rozłączne lub mogą nakładać się na.|  
|[CRgn::CreateRectRgn](#createrectrgn)|Inicjuje `CRgn` obiektu o prostokątny obszar.|  
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|Inicjuje `CRgn` obiektu o prostokątny obszar zdefiniowany przez [RECT](../../mfc/reference/rect-structure1.md) struktury.|  
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|Inicjuje `CRgn` obiektu o prostokątny obszar z zaokrąglonymi narożnikami.|  
|[CRgn::EqualRgn](#equalrgn)|Sprawdza dwie `CRgn` obiektów do ustalenia, czy są równoważne.|  
|[CRgn::FromHandle](#fromhandle)|Zwraca wskaźnik do `CRgn` obiektu, gdy uchwyt do regionu systemu Windows.|  
|[CRgn::GetRegionData](#getregiondata)|Wstawia określony bufor dane opisujące dla danego regionu.|  
|[CRgn::GetRgnBox](#getrgnbox)|Pobiera współrzędne prostokąt ograniczający `CRgn` obiektu.|  
|[CRgn::OffsetRgn](#offsetrgn)|Przenosi `CRgn` obiektu określonego przesunięcia.|  
|[CRgn::PtInRegion](#ptinregion)|Określa, czy określony punkt znajduje się w regionie.|  
|[CRgn::RectInRegion](#rectinregion)|Określa, czy część określonego prostokąta znajduje się w granicach regionu.|  
|[CRgn::SetRectRgn](#setrectrgn)|Ustawia `CRgn` obiektu określonego regionu prostokątny.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRgn::operator hrgn —](#operator_hrgn)|Zwraca uchwytów okien zawartych w `CRgn` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Region jest eliptycznej lub wielobocznych obszarze okna. Aby użyć regionów, należy użyć funkcji elementów członkowskich klasy `CRgn` z funkcjami wycinka zdefiniowane jako elementy członkowskie klasy `CDC`.  
  
 Funkcje Członkowskie `CRgn` tworzenia, alter i pobierania informacji o obiekcie regionu, dla której są nazywane.  
  
 Aby uzyskać więcej informacji na temat używania `CRgn`, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CRgn`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="combinergn"></a>CRgn::CombineRgn  
 Tworzy nowy region GDI łącząc dwóch regionach istniejących.  
  
```  
int CombineRgn(
    CRgn* pRgn1,  
    CRgn* pRgn2,  
    int nCombineMode);
```  
  
### <a name="parameters"></a>Parametry  
 `pRgn1`  
 Identyfikuje istniejącym regionem.  
  
 `pRgn2`  
 Identyfikuje istniejącym regionem.  
  
 `nCombineMode`  
 Określa operację można wykonać, gdy połączenie źródła dwóch regionach. Może być jeden z następujących wartości:  
  
- **RGN_AND** używa nakładające się obszary obu regionów (część wspólną).  
  
- **RGN_COPY** tworzy kopię regionu 1 (identyfikowane przez `pRgn1`).  
  
- **RGN_DIFF** tworzy obszar składające się z obszarów regionu 1 (identyfikowane przez `pRgn1`) nie są częścią regionu 2 (identyfikowane przez `pRgn2`).  
  
- **RGN_OR** łączy obu regionów, w całości (złożenie).  
  
- **RGN_XOR** łączy obu regionów, ale usuwa nakładające się obszary.  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa typ wynikowy regionu. Może być jedną z następujących wartości:  
  
- **COMPLEXREGION** nowy region ma nakładających się obramowań.  
  
- **Błąd** nie nowych region utworzona.  
  
- **NULLREGION** nowy region jest pusta.  
  
- **SIMPLEREGION** nowy region nie ma nakładające się obramowania.  
  
### <a name="remarks"></a>Uwagi  
 Regiony są łączone zgodnie z określonym `nCombineMode`.  
  
 Dwa określone regiony są połączone, a wynikowy uchwyt regionu są przechowywane w `CRgn` obiektu. W związku z tym niezależnie od regionu są przechowywane w `CRgn` obiektu zastępuje Scalonej regionu.  
  
 Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, w zależności od jest mniejsza.  
  
 Użyj [CopyRgn](#copyrgn) wystarczy skopiować jeden region w innym regionie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]  
  
##  <a name="copyrgn"></a>CRgn::CopyRgn  
 Kopiuje region zdefiniowany przez `pRgnSrc` do `CRgn` obiektu.  
  
```  
int CopyRgn(CRgn* pRgnSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `pRgnSrc`  
 Identyfikuje istniejącym regionem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa typ wynikowy regionu. Może być jedną z następujących wartości:  
  
- **COMPLEXREGION** nowy region ma nakładających się obramowań.  
  
- **Błąd** nie nowych region utworzona.  
  
- **NULLREGION** nowy region jest pusta.  
  
- **SIMPLEREGION** nowy region nie ma nakładające się obramowania.  
  
### <a name="remarks"></a>Uwagi  
 Nowy region zastępuje wcześniej są przechowywane w regionie `CRgn` obiektu. Ta funkcja jest specjalny przypadek [CombineRgn](#combinergn) funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRgn::CreateEllipticRgn](#createellipticrgn).  
  
##  <a name="createellipticrgn"></a>CRgn::CreateEllipticRgn  
 Tworzy eliptycznej regionu.  
  
```  
BOOL CreateEllipticRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>Parametry  
 `x1`  
 Określa logicznej współrzędną x górnego lewego rogu prostokątem elipsy.  
  
 `y1`  
 Określa logicznej współrzędną y lewego górnego rogu prostokątem elipsy.  
  
 `x2`  
 Określa logicznej współrzędną x prawym dolnym rogu prostokątem elipsy.  
  
 `y2`  
 Określa logicznej współrzędną y prawego dolnego rogu prostokątem elipsy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Region jest definiowana za pomocą prostokątem określony przez `x1`, `y1`, `x2`, i `y2`. Region jest przechowywany w `CRgn` obiektu.  
  
 Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, w zależności od jest mniejsza.  
  
 Po zakończeniu przy użyciu region utworzone za pomocą `CreateEllipticRgn` funkcji aplikacji powinien wybierz region limit kontekstu urządzenia i używanie `DeleteObject` funkcji, aby go usunąć.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]  
  
##  <a name="createellipticrgnindirect"></a>CRgn::CreateEllipticRgnIndirect  
 Tworzy eliptycznej regionu.  
  
```  
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Wskazuje `RECT` struktury lub `CRect` obiekt, który zawiera logicznej współrzędne górnego lewego i prawego dolnego rogu prostokątem elipsy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Region jest definiowana za pomocą struktury lub wskazywanego przez obiekt `lpRect` i są przechowywane w `CRgn` obiektu.  
  
 Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, w zależności od jest mniejsza.  
  
 Po zakończeniu przy użyciu region utworzone za pomocą `CreateEllipticRgnIndirect` funkcji aplikacji powinien wybierz region limit kontekstu urządzenia i używanie `DeleteObject` funkcji, aby go usunąć.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRgn::CreateRectRgnIndirect](#createrectrgnindirect).  
  
##  <a name="createfromdata"></a>CRgn::CreateFromData  
 Tworzy obszar z danego regionu i przekształcania danych.  
  
```  
BOOL CreateFromData(
    const XFORM* lpXForm,  
    int nCount,  
    const RGNDATA* pRgnData);
```  
  
### <a name="parameters"></a>Parametry  
 *lpXForm*  
 Wskazuje [XFORM](../../mfc/reference/xform-structure.md) struktura danych, która definiuje przekształcania na region. Jeśli ten wskaźnik jest **NULL**, transformacja tożsamości jest używana.  
  
 `nCount`  
 Określa liczbę bajtów wskazywana przez `pRgnData`.  
  
 `pRgnData`  
 Wskazuje [RGNDATA](../../mfc/reference/rgndata-structure.md) struktura danych, która zawiera dane regionu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aplikacja może pobrać danych dla regionu, wywołując `CRgn::GetRegionData` funkcji.  
  
##  <a name="createfrompath"></a>CRgn::CreateFromPath  
 Tworzy obszar ze ścieżki, który wybrano w kontekście danego urządzenia.  
  
```  
BOOL CreateFromPath(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Identyfikuje kontekst urządzenia, zawierającą ścieżkę zamkniętą.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Kontekst urządzenia identyfikowane przez `pDC` parametr musi zawierać ścieżkę zamkniętą. Po `CreateFromPath` konwertuje ścieżkę do regionu, systemu Windows odrzuca zamkniętego ścieżki z kontekstu urządzenia.  
  
##  <a name="createpolygonrgn"></a>CRgn::CreatePolygonRgn  
 Tworzy wielokątne regionu.  
  
```  
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,  
    int nCount,  
    int nMode);
```  
  
### <a name="parameters"></a>Parametry  
 `lpPoints`  
 Wskazuje tablicę **punktu** struktury lub tablicę `CPoint` obiektów. Każda struktura Określa współrzędną x i y współrzędne jednego wierzchołka wielokąta. **Punktu** struktury ma następujący format:  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `nCount`  
 Określa liczbę **punktu** struktury lub `CPoint` obiektów w tablicy wskazywana przez `lpPoints`.  
  
 `nMode`  
 Określa tryb wypełnianie dla regionu. Ten parametr może być **alternatywny** lub **ZAWIJANIA**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 System wielokąta zostanie automatycznie zamknięte, jeśli to konieczne, za pomocą rysowania linii z ostatnim wierzchołku jako pierwszy. Wynikowa region jest przechowywany w `CRgn` obiektu.  
  
 Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, w zależności od jest mniejsza.  
  
 Gdy tryb wielokąta wypełnianie jest **alternatywny**, system wypełnia obszar między stronami nieparzystych i parzystych wielokąta w każdym wierszu skanowania. Oznacza to, że system wypełnia obszar między pierwszej i drugiej strony, między po stronie trzeciej i czwartej i tak dalej.  
  
 Gdy tryb wielokąta wypełnianie jest **ZAWIJANIA**, system używa kierunek, w którym rysunku narysowaniu do ustalenia, czy w celu wypełnienia obszaru. Każdy z segmentów wiersza wielokąta jest rysowane w prawo lub wskazówek zegara. Zawsze, gdy linią urojony z obszaru na zewnątrz rysunku przechodzi przez segment linii zegara, licznik jest zwiększany. Wiersz przejścia przez segment linii zegara, wartość licznika jest zmniejszany. Obszar jest wypełniony, jeśli wartość licznika jest różna od zera, gdy wiersz osiągnie zewnętrznej rysunku.  
  
 Kiedy aplikacja zakończy region utworzone za pomocą `CreatePolygonRgn` funkcji, go należy wybrać region limit kontekstu urządzenia i używanie `DeleteObject` funkcji, aby go usunąć.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]  
  
##  <a name="createpolypolygonrgn"></a>CRgn::CreatePolyPolygonRgn  
 Tworzy obszar składający się z szeregu zamkniętych wielokątów.  
  
```  
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,  
    LPINT lpPolyCounts,  
    int nCount,  
    int nPolyFillMode);
```  
  
### <a name="parameters"></a>Parametry  
 `lpPoints`  
 Wskazuje tablicę **punktu** struktury lub tablicę `CPoint` obiektów, które definiuje wierzchołki wielokątów. Każdy Wielokąt musi być jawnie zamknięty, ponieważ system nie Zamknij je automatycznie. Wielokąty podano po kolei. **Punktu** struktury ma następujący format:  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `lpPolyCounts`  
 Wskazuje tablicy liczb całkowitych. Pierwszej liczby całkowitej określa liczbę wierzchołków w pierwszym wielokąta w `lpPoints` tablicy, drugi całkowitą określa liczbę wierzchołków w drugim wielokąta i tak dalej.  
  
 `nCount`  
 Określa sumę liczb całkowitych w `lpPolyCounts` tablicy.  
  
 `nPolyFillMode`  
 Określa tryb wypełnianie wielokąta. Ta wartość może być **alternatywny** lub **ZAWIJANIA**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wynikowa region jest przechowywany w `CRgn` obiektu.  
  
 Wielokąty mogą być rozłączne lub mogą nakładać się na.  
  
 Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, w zależności od jest mniejsza.  
  
 Gdy tryb wielokąta wypełnianie jest **alternatywny**, system wypełnia obszar między stronami nieparzystych i parzystych wielokąta w każdym wierszu skanowania. Oznacza to, że system wypełnia obszar między pierwszej i drugiej strony, między po stronie trzeciej i czwartej i tak dalej.  
  
 Gdy tryb wielokąta wypełnianie jest **ZAWIJANIA**, system używa kierunek, w którym rysunku narysowaniu do ustalenia, czy w celu wypełnienia obszaru. Każdy z segmentów wiersza wielokąta jest rysowane w prawo lub wskazówek zegara. Zawsze, gdy linią urojony z obszaru na zewnątrz rysunku przechodzi przez segment linii zegara, licznik jest zwiększany. Wiersz przejścia przez segment linii zegara, wartość licznika jest zmniejszany. Obszar jest wypełniony, jeśli wartość licznika jest różna od zera, gdy wiersz osiągnie zewnętrznej rysunku.  
  
 Kiedy aplikacja zakończy region utworzone za pomocą `CreatePolyPolygonRgn` funkcji, go należy wybrać region limit kontekstu urządzenia i używanie [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funkcji członkowskiej go usunąć.  
  
##  <a name="createrectrgn"></a>CRgn::CreateRectRgn  
 Tworzy prostokątny obszar, który jest przechowywany w `CRgn` obiektu.  
  
```  
BOOL CreateRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>Parametry  
 `x1`  
 Określa logicznej współrzędną x górnego lewego rogu regionu.  
  
 `y1`  
 Określa logicznej współrzędną y lewego górnego rogu regionu.  
  
 `x2`  
 Określa logicznej współrzędną x prawym dolnym rogu regionu.  
  
 `y2`  
 Określa logicznej współrzędną y prawego dolnego rogu regionu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, w zależności od jest mniejsza.  
  
 Po zakończeniu przy użyciu region utworzone przez `CreateRectRgn`, należy użyć aplikacji [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funkcji członkowskiej, aby usunąć region.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]  
  
 Na przykład dodatkowe zobacz [CRgn::CombineRgn](#combinergn).  
  
##  <a name="createrectrgnindirect"></a>CRgn::CreateRectRgnIndirect  
 Tworzy prostokątny obszar, który jest przechowywany w `CRgn` obiektu.  
  
```  
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Wskazuje `RECT` struktury lub `CRect` obiekt, który zawiera logicznej współrzędne górnego lewego i prawego dolnego rogu regionu. `RECT` Struktury ma następujący format:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, w zależności od jest mniejsza.  
  
 Po zakończeniu przy użyciu region utworzone przez `CreateRectRgnIndirect`, należy użyć aplikacji [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funkcji członkowskiej, aby usunąć region.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]  
  
##  <a name="createroundrectrgn"></a>CRgn::CreateRoundRectRgn  
 Tworzy prostokątny obszar z zaokrąglonymi narożnikami, które są przechowywane w `CRgn` obiektu.  
  
```  
BOOL CreateRoundRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3);
```  
  
### <a name="parameters"></a>Parametry  
 `x1`  
 Określa logicznej współrzędną x górnego lewego rogu regionu.  
  
 `y1`  
 Określa logicznej współrzędną y lewego górnego rogu regionu.  
  
 `x2`  
 Określa logicznej współrzędną x prawym dolnym rogu regionu.  
  
 `y2`  
 Określa logicznej współrzędną y prawego dolnego rogu regionu.  
  
 *x3*  
 Określa szerokość elipsy pozwala utworzyć zaokrąglone narożniki.  
  
 `y3`  
 Określa wysokość elipsy pozwala utworzyć zaokrąglone narożniki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar regionu jest ograniczony do 32 767 przez 32 767 jednostki logiczne lub 64 KB pamięci, w zależności od jest mniejsza.  
  
 Kiedy aplikacja zakończy region utworzone za pomocą `CreateRoundRectRgn` funkcji, go należy wybrać region limit kontekstu urządzenia i używanie [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funkcji członkowskiej go usunąć.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]  
  
##  <a name="crgn"></a>CRgn::CRgn  
 Konstruuje `CRgn` obiektu.  
  
```  
CRgn();
```  
  
### <a name="remarks"></a>Uwagi  
 `m_hObject` Element członkowski danych nie zawiera nieprawidłowy region GDI systemu Windows, aż obiekt jest inicjowany z co najmniej jednego z innych `CRgn` funkcji elementów członkowskich.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRgn::CreateRoundRectRgn](#createroundrectrgn).  
  
##  <a name="equalrgn"></a>CRgn::EqualRgn  
 Określa, czy dany region jest odpowiednikiem przechowywanych w regionie `CRgn` obiektu.  
  
```  
BOOL EqualRgn(CRgn* pRgn) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pRgn`  
 Identyfikuje regionu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dwóch regionach są równoważne; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]  
  
##  <a name="fromhandle"></a>CRgn::FromHandle  
 Zwraca wskaźnik do `CRgn` obiektu, gdy uchwyt do regionu systemu Windows.  
  
```  
static CRgn* PASCAL FromHandle(HRGN hRgn);
```  
  
### <a name="parameters"></a>Parametry  
 `hRgn`  
 Określa dojścia do regionu systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CRgn` obiektu. Jeśli funkcja zakończyła się niepowodzeniem, jest zwracana wartość **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CRgn` obiekt nie jest już dołączony do uchwytu, tymczasowej `CRgn` obiekt jest tworzony i dołączyć. To tymczasowe `CRgn` obiekt jest prawidłowy tylko do momentu przy następnym aplikacja ma czas bezczynności w pętli jego zdarzeń, w czasu grafiki wszystkie tymczasowe obiekty zostaną usunięte. Innymi słowy to jest, że tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu jedno okno.  
  
##  <a name="getregiondata"></a>CRgn::GetRegionData  
 Wstawia określony bufor dane opisujące regionu.  
  
```  
int GetRegionData(
    LPRGNDATA lpRgnData,  
    int nCount) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRgnData`  
 Wskazuje [RGNDATA](../../mfc/reference/rgndata-structure.md) struktury danych, który odbiera dane. Jeśli ten parametr ma **NULL**, zwracana wartość zawiera liczbę bajtów potrzebnych danych regionu.  
  
 `nCount`  
 Określa rozmiar w bajtach `lpRgnData` buforu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem i `nCount` określa odpowiednią liczbą bajtów, zwracana wartość jest zawsze `nCount`. Jeśli funkcja nie powiedzie się lub `nCount` określa mniejsza niż odpowiednia liczba bajtów, zwracana wartość to 0 (błąd).  
  
### <a name="remarks"></a>Uwagi  
 Te dane obejmują wymiary prostokątów wchodzące w skład regionu. Ta funkcja jest używana w połączeniu z `CRgn::CreateFromData` funkcji.  
  
##  <a name="getrgnbox"></a>CRgn::GetRgnBox  
 Pobiera współrzędne prostokąt ograniczający `CRgn` obiektu.  
  
```  
int GetRgnBox(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Wskazuje `RECT` struktury lub `CRect` obiektu do odbierania współrzędne prostokątem. `RECT` Struktury ma następujący format:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa typ regionu. Może być jedną z następujących wartości:  
  
- **COMPLEXREGION** Region ma nakładających się obramowań.  
  
- **NULLREGION** Region jest pusta.  
  
- **Błąd** `CRgn` w obiekcie nie określono nieprawidłowy region.  
  
- **SIMPLEREGION** regionie nie ma nakładające się obramowania.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRgn::CreatePolygonRgn](#createpolygonrgn).  
  
##  <a name="offsetrgn"></a>CRgn::OffsetRgn  
 Przenosi przechowywanych w regionie `CRgn` obiektu określonego przesunięcia.  
  
```  
int OffsetRgn(
    int x,  
    int y);  
  
int OffsetRgn(POINT point);
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Określa liczbę jednostek można przenieść do lewej lub do prawej.  
  
 *y*  
 Określa liczbę jednostek można przenieść w górę lub w dół.  
  
 `point`  
 Współrzędna x `point` określa liczbę jednostek można przenieść do lewej lub do prawej. Współrzędna y `point` określa liczbę jednostek można przenieść w górę lub w dół. `point` Parametru może być **punktu** struktury lub `CPoint` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ nowego regionu. Może być jeden z następujących wartości:  
  
- **COMPLEXREGION** Region ma nakładających się obramowań.  
  
- **Błąd** Region dojście jest nieprawidłowe.  
  
- **NULLREGION** Region jest pusta.  
  
- **SIMPLEREGION** regionie nie ma nakładające się obramowania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja przenosi region *x* jednostki wzdłuż osi x i *y* jednostki wzdłuż osi y.  
  
 Współrzędna wartości regionu musi być mniejsza lub równa 32 767 i większa niż lub równa-32 768. *x* i *y* parametry muszą być starannie wybrane zapobiegające współrzędne nieprawidłowy region.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CRgn::CreateEllipticRgn](#createellipticrgn).  
  
##  <a name="operator_hrgn"></a>CRgn::operator hrgn —  
 Użyj tego operatora, aby uzyskać dojście Windows GDI dołączonych `CRgn` obiektu.  
  
```  
operator HRGN() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli się powiedzie, uchwyt do obiektu Windows GDI reprezentowany przez `CRgn` obiektu; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator jest operatora rzutowania obsługuje bezpośredniego użycia **hrgn —** obiektu.  
  
 Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz artykuł [obiektów grafiki](http://msdn.microsoft.com/library/windows/desktop/dd144962) w zestawie Windows SDK.  
  
##  <a name="ptinregion"></a>CRgn::PtInRegion  
 Sprawdza, czy punktu określonego przez *x* i *y* znajduje się w regionie przechowywane w `CRgn` obiektu.  
  
```  
BOOL PtInRegion(
    int x,  
    int y) const;  
  
BOOL PtInRegion(POINT point) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Określa logicznej współrzędną x punktu do testowania.  
  
 *y*  
 Określa logicznej współrzędną y punktu do testowania.  
  
 `point`  
 X i y współrzędne `point` Określ współrzędne x i y punktu do testowania wartości. `point` Parametru może być **punktu** struktury lub `CPoint` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli punkt znajduje się w regionie; w przeciwnym razie 0.  
  
##  <a name="rectinregion"></a>CRgn::RectInRegion  
 Określa, czy część prostokąt określony przez `lpRect` znajduje się w granicach przechowywanych w regionie `CRgn` obiektu.  
  
```  
BOOL RectInRegion(LPCRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Wskazuje `RECT` struktury lub `CRect` obiektu. `RECT` Struktury ma następujący format:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli część określonego prostokąta znajduje się w obrębie regionu; w przeciwnym razie 0.  
  
##  <a name="setrectrgn"></a>CRgn::SetRectRgn  
 Tworzy prostokątny obszar.  
  
```  
void SetRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
void SetRectRgn(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `x1`  
 Określa współrzędną x górnego lewego rogu prostokątny obszar.  
  
 `y1`  
 Określa współrzędną y lewego górnego rogu prostokątny obszar.  
  
 `x2`  
 Określa współrzędną x prawym dolnym rogu prostokątny obszar.  
  
 `y2`  
 Określa współrzędną y prawego dolnego rogu prostokątny obszar.  
  
 `lpRect`  
 Określa prostokątny obszar. Może być wskaźnikiem do `RECT` struktury lub `CRect` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 W odróżnieniu od [CreateRectRgn](#createrectrgn), jednak go nie przydzielić wszystkie dodatkowe pamięci sterty lokalnych aplikacji systemu Windows. Zamiast tego używa ilość miejsca przydzielonego dla regionu są przechowywane w `CRgn` obiektu. Oznacza to, że `CRgn` obiektu musi już zostać inicjowane z prawidłową regionu systemu Windows przed wywołaniem `SetRectRgn`. Punkty przez `x1`, `y1`, `x2`, i `y2` określ minimalny rozmiar przydzielonego miejsca.  
  
 Aby użyć tej funkcji, zamiast `CreateRectRgn` funkcji członkowskiej, aby uniknąć wywołań Menedżer pamięci lokalnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



