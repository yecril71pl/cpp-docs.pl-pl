---
title: Klasa CRect | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRect
- ATLTYPES/ATL::CRect
- ATLTYPES/ATL::CRect::CRect
- ATLTYPES/ATL::CRect::BottomRight
- ATLTYPES/ATL::CRect::CenterPoint
- ATLTYPES/ATL::CRect::CopyRect
- ATLTYPES/ATL::CRect::DeflateRect
- ATLTYPES/ATL::CRect::EqualRect
- ATLTYPES/ATL::CRect::Height
- ATLTYPES/ATL::CRect::InflateRect
- ATLTYPES/ATL::CRect::IntersectRect
- ATLTYPES/ATL::CRect::IsRectEmpty
- ATLTYPES/ATL::CRect::IsRectNull
- ATLTYPES/ATL::CRect::MoveToX
- ATLTYPES/ATL::CRect::MoveToXY
- ATLTYPES/ATL::CRect::MoveToY
- ATLTYPES/ATL::CRect::NormalizeRect
- ATLTYPES/ATL::CRect::OffsetRect
- ATLTYPES/ATL::CRect::PtInRect
- ATLTYPES/ATL::CRect::SetRect
- ATLTYPES/ATL::CRect::SetRectEmpty
- ATLTYPES/ATL::CRect::Size
- ATLTYPES/ATL::CRect::SubtractRect
- ATLTYPES/ATL::CRect::TopLeft
- ATLTYPES/ATL::CRect::UnionRect
- ATLTYPES/ATL::CRect::Width
dev_langs: C++
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 067f683b5322b11a4ca33f015d64850c8113ce18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="crect-class"></a>Klasa CRect
Podobnie jak Windows [RECT](../../mfc/reference/rect-structure1.md) struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CRect : public tagRECT  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRect::CRect](#crect)|Konstruuje `CRect` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRect::BottomRight](#bottomright)|Zwraca punkt prawym dolnym rogu `CRect`.|  
|[CRect::CenterPoint](#centerpoint)|Zwraca centerpoint z `CRect`.|  
|[CRect::CopyRect](#copyrect)|Kopiuje wymiary źródła prostokąt `CRect`.|  
|[CRect::DeflateRect](#deflaterect)|Szerokość i wysokość `CRect`.|  
|[CRect::EqualRect](#equalrect)|Określa, czy `CRect` jest równa danego prostokąta.|  
|[CRect::Height](#height)|Oblicza wysokość `CRect`.|  
|[CRect::InflateRect](#inflaterect)|Zwiększa szerokość i wysokość `CRect`.|  
|[CRect::IntersectRect](#intersectrect)|Ustawia `CRect` równą część wspólną dwóch prostokątów.|  
|[CRect::IsRectEmpty](#isrectempty)|Określa, czy `CRect` jest pusta. `CRect`Jeśli szerokość lub wysokość są 0 jest pusty.|  
|[CRect::IsRectNull](#isrectnull)|Określa, czy **górnej**, **dolnej**, **po lewej stronie**, i **prawo** zmienne Członkowskie są równe 0.|  
|[CRect::MoveToX](#movetox)|Przenosi `CRect` do określonego współrzędną x.|  
|[CRect::MoveToXY](#movetoxy)|Przenosi `CRect` do określonych x i y współrzędnych.|  
|[CRect::MoveToY](#movetoy)|Przenosi `CRect` do określonego współrzędną y.|  
|[CRect::NormalizeRect](#normalizerect)|Standaryzuje wysokość i szerokość `CRect`.|  
|[CRect::OffsetRect](#offsetrect)|Przenosi `CRect` przez określonych przesunięć.|  
|[CRect::PtInRect](#ptinrect)|Określa, czy określony punkt znajduje się w obrębie `CRect`.|  
|[CRect::SetRect](#setrect)|Ustawia wymiary `CRect`.|  
|[CRect::SetRectEmpty](#setrectempty)|Zestawy `CRect` do pusty prostokąt (wszystkie współrzędne równe 0).|  
|[CRect::Size](#size)|Oblicza rozmiar `CRect`.|  
|[CRect::SubtractRect](#subtractrect)|Odejmuje jedną prostokąt z innej.|  
|[CRect::TopLeft](#topleft)|Zwraca punkt lewego górnego `CRect`.|  
|[CRect::UnionRect](#unionrect)|Ustawia `CRect` równa złożenie dwóch prostokątów.|  
|[CRect::Width](#width)|Oblicza szerokość `CRect`.|  
  
### <a name="public-operators"></a>Operatory publiczne    
|Nazwa|Opis|  
|----------|-----------------|  
|[CRect::operator-](#operator_-)|Odejmuje danego przesunięcia od `CRect` lub deflates `CRect` i zwraca wynikowy `CRect`.|  
|[Lpcrect — CRect::operator](#operator_lpcrect)|Konwertuje `CRect` do **lpcrect —**.|  
|[CRect::operator lprect —](#operator_lprect)|Konwertuje `CRect` do `LPRECT`.|  
|[CRect::operator! =](#operator_neq)|Określa, czy `CRect` nie jest równa prostokąta.|  
|[CRect::operator&amp;](#operator_amp)|Tworzy punkt przecięcia `CRect` i prostokąt i zwraca wynikowy `CRect`.|  
|[CRect::operator&amp;=](#operator_amp_eq)|Ustawia `CRect` równą część wspólną `CRect` i prostokąta.|  
|[CRect::operator |](#operator_or)|Tworzy złożenie `CRect` i prostokąt i zwraca wynikowy `CRect`.|  
|[CRect::operator |=](#operator_or_eq)|Ustawia `CRect` równa złożenie `CRect` i prostokąta.|  
|[CRect::operator +](#operator_add)|Dodaje danego przesunięcia do `CRect` lub nadyma `CRect` i zwraca wynikowy `CRect`.|  
|[CRect::operator +=](#operator_add_eq)|Dodaje określonego przesunięcia do `CRect` lub nadyma `CRect`.|  
|[CRect::operator =](#operator_eq)|Kopiuje wymiary prostokąt `CRect`.|  
|[CRect::operator-=](#operator_-_eq)|Odejmuje określonych przesunięć z `CRect` lub deflates `CRect`.|  
|[CRect::operator ==](#operator_eq_eq)|Określa, czy `CRect` jest równa prostokąta.|  
  
## <a name="remarks"></a>Uwagi  
 `CRect`zawiera również funkcje elementów członkowskich do manipulowania `CRect` obiektów i Windows `RECT` struktury.  
  
 A `CRect` obiekt można przekazać jako parametru funkcji wszędzie tam, gdzie `RECT` struktury **lpcrect —**, lub `LPRECT` mogą zostać przekazane.  
  
> [!NOTE]
>  Ta klasa pochodzi od **tagRECT** struktury. (Nazwa **tagRECT** jest mniej — często używane nazwę `RECT` struktury.) Oznacza to, że elementy członkowskie danych (**po lewej stronie**, **górnej**, **prawo**, i **dolnej**) z `RECT` struktury są dostępnych danych. elementy członkowskie `CRect`.  
  
 A `CRect` zawiera zmienne Członkowskie, które definiują punktów górnym rogu i prawym dolnym rogu prostokąta.  
  
 Podczas określania `CRect`, należy pamiętać, aby go utworzyć, dzięki czemu jest on znormalizowany — innymi słowy, tak, aby wartość Lewa współrzędna jest mniejsza od góry i prawej jest mniejsza od dołu. Na przykład lewym górnym rogu (10,10) i prawym dolnym rogu (20,20) definiuje znormalizowane prostokąt, ale lewym górnym rogu (20,20) i prawym dolnym rogu (10,10) definiuje nieznormalizowanej prostokąta. Jeśli prostokąt nie jest znormalizowana, wiele `CRect` funkcji elementów członkowskich może zwracać niepoprawne wyniki. (Zobacz [CRect::NormalizeRect](#normalizerect) lista tych funkcji.) Przed wywołaniem funkcji, która wymaga znormalizowane prostokąty można znormalizować nieznormalizowanej prostokąty wywołując `NormalizeRect` funkcji.  
  
 Należy zachować ostrożność podczas manipulowania `CRect` z [CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp) i [CDC::LPtoDP](../../mfc/reference/cdc-class.md#lptodp) funkcji elementów członkowskich. Jeśli tryb mapowania kontekstu wyświetlanie jest taka, że zakres y jest ujemna, podobnie jak w `MM_LOENGLISH`, następnie `CDC::DPtoLP` przekształci `CRect` tak, aby jego górnej jest większa od dołu. Funkcje, takie jak **wysokość** i **rozmiar** będą zwracać wartości ujemnych dla wysokość przekształcone `CRect`, i prostokąt będzie nieznormalizowanej.  

  
 Kiedy za pomocą przeciążony `CRect` operatorów, pierwszy argument musi być `CRect`; druga mogą być [RECT](../../mfc/reference/rect-structure1.md) struktury lub `CRect` obiektu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `tagRECT`  
  
 `CRect`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atltypes.h  
  
##  <a name="bottomright"></a>CRect::BottomRight  
 Współrzędne są zwracane jako odwołanie do [CPoint](cpoint-class.md) obiektu, który jest zawarty w `CRect`.  
  
```  
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Współrzędne prawym dolnym rogu prostokąta.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja umożliwia należy pobrać lub ustawić prawym dolnym rogu prostokąta. Ustaw rogu przy użyciu tej funkcji po lewej stronie operatora przypisania.  
  
### <a name="example"></a>Przykład  
```cpp  
 // use BottomRight() to retrieve the bottom
 // right POINT 
 CRect rect(210, 150, 350, 900);
 CPoint ptDown;

 ptDown = rect.BottomRight();

 // ptDown is now set to (350, 900)
 ASSERT(ptDown == CPoint(350, 900));

 // or, use BottomRight() to set the bottom
 // right POINT 
 CRect rect2(10, 10, 350, 350);
 CPoint ptLow(180, 180);

   CRect rect2(10, 10, 350, 350);
   CPoint ptLow(180, 180);
rect2.BottomRight() = ptLow;

   // rect2 is now (10, 10, 180, 180)
   ASSERT(rect2 == CRect(10, 10, 180, 180));   
```
  
##  <a name="centerpoint"></a>CRect::CenterPoint 
 Oblicza centerpoint z `CRect` przez dodanie wartości lewy i prawy i podzielenie przez dwa i dodawanie górnej i dolnej wartości i podzielenie przez dwa.  
  
```  
CPoint CenterPoint() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CPoint` obiekt, który jest centerpoint z `CRect`.  
  
### <a name="example"></a>Przykład  
```cpp  
// Code from this OnPaint() implementation can be pasted into your own application
// to draw lines that would look like a letter "Y" within your dialog. 
void CMyDlg::OnPaint()
{
    CPaintDC dc(this);


    // device context for painting

    // get the size and position of the client area of 
    // your window

    CRect rect;
    GetClientRect(&rect);

    // Move the current pen to the top left of the window. We call the
    // TopLeft() member of CRect here and it returns a CPoint object we
    // pass to the override of CDC::MoveTo() that accepts a CPoint.

    dc.MoveTo(rect.TopLeft());

    // Draw a line from the top left to the center of the window.
    // CenterPoint() gives us the middle point of the window as a
    // CPoint, and since CDC::LineTo() has an override that accepts a
    // CPoint, we can just pass it along.

    dc.LineTo(rect.CenterPoint());

    // Now, draw a line to the top right of the window. There's no
    // CRect member which returns a CPoint for the top right of the
    // window, so we'll reference the CPoint members directly and call
    // the CDC::LineTo() override which takes two integers.

    dc.LineTo(rect.right, rect.top);

    // The top part of the "Y" is drawn. Now, we'll draw the stem. We
    // start from the center point.

    dc.MoveTo(rect.CenterPoint());

    // and then draw to the middle of the bottom edge of the window.
    // We'll get the x-coordinate from the x member of the CPOINT 
  // returned by CenterPoint(), and the y value comes directly from
    // the rect.

    dc.LineTo(rect.CenterPoint().x, rect.bottom);
}
```
  
##  <a name="copyrect"></a>CRect::CopyRect  
 Kopie `lpSrcRect` prostokąta do `CRect`.  
  
```  
void CopyRect(LPCRECT lpSrcRect) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `lpSrcRect`  
 Wskazuje [RECT](../../mfc/reference/rect-structure1.md) struktury lub `CRect` obiekt, który ma zostać skopiowany.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rectSource(35, 10, 125, 10);
 CRect rectDest;

 rectDest.CopyRect(&rectSource);

 // rectDest is now set to (35, 10, 125, 10)

 RECT rectSource2;
 rectSource2.left = 0;
 rectSource2.top = 0;
 rectSource2.bottom = 480;
 rectSource2.right = 640;

 rectDest.CopyRect(&rectSource2);

 // works against RECT structures, too!
 // rectDest is now set to (0, 0, 640, 480)   
```

  
##  <a name="crect"></a>CRect::CRect  
 Konstruuje `CRect` obiektu.  
  
```  
CRect() throw();
CRect(int l, int t, int r, int b) throw();
CRect(const RECT& srcRect) throw();
CRect(LPCRECT lpSrcRect) throw();
CRect(POINT point, SIZE size) throw();
CRect(POINT topLeft, POINT bottomRight) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *l*  
 Umiejscowienie lewego `CRect`.  
  
 *t*  
 Określa początku `CRect`.  
  
 *r*  
 Określa położenie prawo `CRect`.  
  
 *b*  
 Określa dołu `CRect`.  
  
 *srcRect*  
 Odwołuje się do [RECT](../../mfc/reference/rect-structure1.md) struktury z dla współrzędnych `CRect`.  
  
 `lpSrcRect`  
 Wskazuje `RECT` struktury z dla współrzędnych `CRect`.  
  
 `point`  
 Określa punkt początku prostokąta nastąpi. Odnosi się do lewego górnego rogu.  
  
 `size`  
 Określa przesunięcie od lewego górnego rogu do prawego dolnego rogu prostokąta nastąpi.  
  
 *topLeft*  
 Umiejscowienie lewego górnego `CRect`.  
  
 *bottomRight*  
 Określa położenie prawym dolnym rogu `CRect`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli podana jest bez argumentów, **po lewej stronie**, **górnej**, **prawo**, i **dolnej** elementy członkowskie nie zostały zainicjowane.  
  
 `CRect`(**Const RECT &**) i `CRect`(**lpcrect —**) wykonaj konstruktorów [CopyRect](#copyrect). Inne konstruktorów zainicjować zmienne Członkowskie obiektu bezpośrednio.  
  
### <a name="example"></a>Przykład  
```cpp  
 // default constructor doesn't initialize!
 CRect rectUnknown;

 // four-integers are left, top, right, and bottom
 CRect rect(0, 0, 100, 50);
 ASSERT(rect.Width() == 100);
 ASSERT(rect.Height() == 50);

 // Initialize from RECT stucture
 RECT sdkRect;
 sdkRect.left = 0;
 sdkRect.top = 0;
 sdkRect.right = 100;
 sdkRect.bottom = 50;

 CRect rect2(sdkRect);
 // by reference
 CRect rect3(&sdkRect);


 // by address
 ASSERT(rect2 == rect);
 ASSERT(rect3 == rect);

 // from a point and a size
 CPoint pt(0, 0);
 CSize sz(100, 50);
 CRect rect4(pt, sz);
 ASSERT(rect4 == rect2);

 // from two points
 CPoint ptBottomRight(100, 50);
 CRect rect5(pt, ptBottomRight);
 ASSERT(rect5 == rect4);  
```
  
##  <a name="deflaterect"></a>CRect::DeflateRect  
 `DeflateRect`deflates `CRect` przenosząc boków kierunku jej center.  
  
```  
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Określa liczbę jednostek deflate po lewej i prawej krawędzi `CRect`.  
  
 *y*  
 Określa liczbę jednostek deflate górą a dołem `CRect`.  
  
 `size`  
 A [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) lub [CSize](csize-class.md) , który określa liczbę jednostek deflate `CRect`. `cx` Wartość określa liczbę jednostek deflate lewej i prawej stronie i `cy` wartość określa liczbę jednostek deflate górny i dolny.  
  
 `lpRect`  
 Wskazuje [RECT](../../mfc/reference/rect-structure1.md) struktury lub `CRect` , który określa liczbę jednostek do korygowania każdej strony.  
  
 *l*  
 Określa liczbę jednostek w lewej części deflate `CRect`.  
  
 *t*  
 Określa liczbę jednostek w górnej części deflate `CRect`.  
  
 *r*  
 Określa liczbę jednostek deflate po prawej stronie `CRect`.  
  
 *b*  
 Określa liczbę jednostek w dolnej części deflate `CRect`.  
  
### <a name="remarks"></a>Uwagi  
 Aby to zrobić, `DeflateRect` dodaje jednostki w lewo i górnej i odejmuje jednostki z prawej strony i na dole. Parametry `DeflateRect` są podpisane wartości; wartości dodatnie deflate `CRect` i wartości ujemnych zwiększyć go.  
  
 Pierwsze dwa przeciążenia deflate pary przeciwną stron `CRect` tak, aby jego łączna szerokość zostaje zmniejszona przez dwa razy *x* (lub `cx`) i jego całkowitej wysokości zostaje zmniejszona przez dwa razy *y* () lub `cy`). Inne przeciążenia korygowania każdej strony `CRect` niezależnie od innych.  
  
### <a name="example"></a>Przykład  
```cpp  
   CRect rect(10, 10, 50, 50);
   rect.DeflateRect(1, 2);
   ASSERT(rect.left == 11 && rect.right == 49);
   ASSERT(rect.top == 12 && rect.bottom == 48);
   
   CRect rect2(10, 10, 50, 50);
   CRect rectDeflate(1, 2, 3, 4);
   rect2.DeflateRect(&rectDeflate);
   ASSERT(rect2.left == 11 && rect2.right == 47);
   ASSERT(rect2.top == 12 && rect2.bottom == 46);   
```
  
##  <a name="equalrect"></a>CRect::EqualRect  
 Określa, czy `CRect` jest równa danego prostokąta.  
  
```  
BOOL EqualRect(LPCRECT lpRect) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Wskazuje [RECT](../../mfc/reference/rect-structure1.md) struktury lub `CRect` obiekt, który zawiera współrzędne górnego lewego i prawego dolnego rogu prostokąta.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dwa prostokąty ma tego samego początku, po lewej, dolnej i prawej wartości; w przeciwnym razie 0.  
  
> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
```cpp  
   CRect rect1(35, 150, 10, 25);
   CRect rect2(35, 150, 10, 25);
   CRect rect3(98, 999, 6, 3);
ASSERT(rect1.EqualRect(rect2));
   ASSERT(!rect1.EqualRect(rect3));
 // works just fine against RECTs, as well

 RECT test;
 test.left = 35;
 test.top = 150;
 test.right = 10;
 test.bottom = 25;

 ASSERT(rect1.EqualRect(&test));  
```

##  <a name="height"></a>CRect::Height  
 Oblicza wysokość `CRect` przez odjęcie wysokiej wartości niż wartość dolnej.  
  
```  
int Height() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wysokość `CRect`.  
  
### <a name="remarks"></a>Uwagi  
 Wartość wynikową może być ujemna.  
  
> [!NOTE]
>  Prostokąt muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąt przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect(20, 30, 80, 70);
 int nHt = rect.Height();

```cpp  
   CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

   // nHt is now 40
   ASSERT(nHt == 40);   
```

  
##  <a name="inflaterect"></a>CRect::InflateRect  
 `InflateRect`nadyma `CRect` przenosząc boków od środka.  
  
```  
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Określa liczbę jednostek można zwiększyć po lewej i prawej krawędzi `CRect`.  
  
 *y*  
 Określa liczbę jednostek można zwiększyć górą a dołem `CRect`.  
  
 `size`  
 A [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) lub [CSize](csize-class.md) , który określa liczbę jednostek można zwiększyć `CRect`. `cx` Wartość określa liczbę jednostek zwiększyć lewej i prawej stronie i `cy` wartość określa liczbę jednostek, aby zwiększyć górny i dolny.  
  
 `lpRect`  
 Wskazuje [RECT](../../mfc/reference/rect-structure1.md) struktury lub `CRect` , który określa liczbę jednostek można zwiększyć każdej strony.  
  
 *l*  
 Określa liczbę jednostek w lewej części zwiększyć `CRect`.  
  
 *t*  
 Określa liczbę jednostek w górnej części zwiększyć `CRect`.  
  
 *r*  
 Określa liczbę jednostek można zwiększyć po prawej stronie `CRect`.  
  
 *b*  
 Określa liczbę jednostek w dolnej części zwiększyć `CRect`.  
  
### <a name="remarks"></a>Uwagi  
 Aby to zrobić, `InflateRect` odejmuje jednostki z lewej i górnej i dodaje jednostki w prawo i w dół. Parametry `InflateRect` są podpisane wartości; dodatnią, zwiększyć wartości `CRect` i wartości ujemnych deflate go.  
  
 Pierwsze dwa przeciążenia zwiększyć pary przeciwną stron `CRect` tak, aby jego łączna szerokość zwiększa się o dwa razy *x* (lub `cx`) i jego całkowitej wysokości zwiększa się o dwa razy *y* () lub `cy`). Inne przeciążenia zwiększyć każdej strony `CRect` niezależnie od innych.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect(0, 0, 300, 300);
 rect.InflateRect(50, 200);

 // rect is now (-50, -200, 350, 500)
 ASSERT(rect == CRect(-50, -200, 350, 500));  
```
  
##  <a name="intersectrect"></a>CRect::IntersectRect  
 Sprawia, że `CRect` równą część wspólną dwóch prostokątów istniejących.  
  
```  
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect1`  
 Wskazuje [RECT](../../mfc/reference/rect-structure1.md) struktury lub `CRect` obiekt, który zawiera prostokąta źródłowego.  
  
 `lpRect2`  
 Wskazuje `RECT` struktury lub `CRect` obiekt, który zawiera prostokąta źródłowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli część wspólną nie jest pusty; 0, jeśli część wspólną jest pusta.  
  
### <a name="remarks"></a>Uwagi  
 Część wspólną ma największy prostokąt zawarte w obu prostokąty istniejących.  
  
> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rectOne(125, 0, 150, 200);
 CRect rectTwo(0, 75, 350,  95);
 CRect rectInter;

```cpp  
   CRect rectOne(125,  0, 150, 200);
   CRect rectTwo(0, 75, 350, 95);
   CRect rectInter;

   rectInter.IntersectRect(rectOne, rectTwo);
 ASSERT(rectInter == CRect(125, 75, 150, 95));
 // operator &= can do the same task:

 CRect rectInter2 = rectOne;
 rectInter2 &= rectTwo;
 ASSERT(rectInter2 == CRect(125, 75, 150, 95));  
```
  
##  <a name="isrectempty"></a>CRect::IsRectEmpty  
 Określa, czy `CRect` jest pusta.  
  
```  
BOOL IsRectEmpty() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `CRect` jest pusty; 0 Jeśli `CRect` nie jest pusty.  
  
### <a name="remarks"></a>Uwagi  
 Prostokąt jest pusta, jeśli szerokość lub wysokość 0 lub ujemną. Różni się od `IsRectNull`, która określa, czy wszystkie współrzędne prostokąta to zero.  
  
> [!NOTE]
>  Prostokąt muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąt przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rectNone(0, 0, 0, 0);
 CRect rectSome(35, 50, 135, 150);

```cpp  
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
   ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
   ASSERT(rectEmpty.IsRectEmpty());   
```

  
##  <a name="isrectnull"></a>CRect::IsRectNull  
 Określa, czy, lewego górnego, dół i kliknij prawym przyciskiem myszy wartości `CRect` są równe 0.  
  
```  
BOOL IsRectNull() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `CRect`do dołu, lewego górnego, i prawej wartości są wszystkie równa 0, w przeciwnym 0.  
  
### <a name="remarks"></a>Uwagi  
 Różni się od `IsRectEmpty`, która określa, czy prostokąt jest pusta.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rectNone(0, 0, 0, 0);
 CRect rectSome(35, 50, 135, 150);

```cpp  
   CRect rectNone(0, 0, 0, 0);
   CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
   ASSERT(!rectSome.IsRectNull());
 // note that null means _all_ zeros

 CRect rectNotNull(0, 0, 35, 50);
 ASSERT(!rectNotNull.IsRectNull());  
```
  
##  <a name="movetox"></a>CRect::MoveToX  
 Wywołanie tej funkcji, aby przenieść prostokąt bezwzględną współrzędną x określony przez *x*.  
  
```  
void MoveToX(int x) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Bezwzględny współrzędną x górnego lewego rogu prostokąta.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect(0, 0, 100, 100);
 rect.MoveToX(10);

```cpp  
   CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

   // rect is now (10, 0, 110, 100);
   ASSERT(rect == CRect(10, 0, 110, 100));   
```
  
##  <a name="movetoxy"></a>CRect::MoveToXY  
 Wywołanie tej funkcji można przesuwać do bezwzględne współrzędne x i y-określony.  
  
```  
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Bezwzględny współrzędną x górnego lewego rogu prostokąta.  
  
 *y*  
 Bezwzględny współrzędną y lewego górnego rogu prostokąta.  
  
 `point`  
 A **punktu** struktury, określając bezwzględną górnego lewego rogu prostokąta.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect(0, 0, 100, 100);
 rect.MoveToXY(10, 10);

```cpp  
   CRect rect(0, 0, 100, 100);
   rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
   ASSERT(rect == CRect(10, 10, 110, 110));   
```

  
##  <a name="movetoy"></a>CRect::MoveToY  
 Wywołanie tej funkcji, aby przenieść prostokąt bezwzględną współrzędną y określony przez *y*.  
  
```  
void MoveToY(int y) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *y*  
 Bezwzględny współrzędną y lewego górnego rogu prostokąta.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect(0, 0, 100, 100);
 rect.MoveToY(10);

```cpp  
   CRect rect(0, 0, 100, 100);
   rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
   ASSERT(rect == CRect(0, 10, 100, 110));   
```

  
##  <a name="normalizerect"></a>CRect::NormalizeRect  
 Normalizuje `CRect` tak, aby wysokość i szerokość są dodatnie.  
  
```  
void NormalizeRect() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Prostokąt jest znormalizowanych się dla wiązania kwadrantu czwarty rozmieszczania, używający systemu Windows zazwyczaj współrzędnych. `NormalizeRect`porównuje wartości górny i dolny i zamienia je, jeśli górnej jest większa od dołu. Podobnie go zamienia wartości lewy i prawy, jeśli po lewej stronie jest większa niż prawo. Ta funkcja jest przydatne podczas pracy nad mapowania różnych trybach i prostokąty odwrócony.  
  
> [!NOTE]
>  Następujące `CRect` funkcje Członkowskie znormalizowane prostokąty prawidłowego funkcjonowania wymagają: [wysokość](#height), [szerokość](#width), [rozmiar](#size), [ IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [ SubtractRect](#subtractrect), [operator ==](#operator_eq_eq), [operator! =](#operator_neq), [operatora &#124;](#operator_or), [operatora &#124; =](#operator_or_eq), [operatora &](#operator_amp), i [— operator & =](#operator_amp_eq).  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect1(110, 100, 250, 310);
 CRect rect2(250, 310, 110, 100);

```cpp  
   CRect rect1(110, 100, 250, 310);
   CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
   rect2.NormalizeRect();
 ASSERT(rect1 == rect2);  
```
  
##  <a name="offsetrect"></a>CRect::OffsetRect  
 Przenosi `CRect` przez określonych przesunięć.  
  
```  
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Określa się w lewo lub w prawo. Musi być ujemna i w lewo.  
  
 *y*  
 Określa, aby przenieść w górę lub w dół. Musi być ujemna i Przenieś w górę.  
  
 `point`  
 Zawiera [punktu](../../mfc/reference/point-structure1.md) struktury lub [CPoint](cpoint-class.md) obiektu określenia obu tych wymiarów, przez którą ma zostać przeniesiony.  
  
 `size`  
 Zawiera [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](csize-class.md) obiektu określenia obu tych wymiarów, przez którą ma zostać przeniesiony.  
  
### <a name="remarks"></a>Uwagi  
 Przenosi `CRect` *x* jednostki wzdłuż osi x i *y* jednostki wzdłuż osi y. *x* i *y* parametry są podpisane wartości, więc `CRect` mogą zostać przeniesione w lewo lub w prawo i w górę lub w dół.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect(0, 0, 35, 35);
 rect.OffsetRect(230, 230);

```cpp  
   CRect rect(0, 0, 35, 35);
   rect.OffsetRect(230, 230);

   // rect is now (230, 230, 265, 265)
   ASSERT(rect == CRect(230, 230, 265, 265));   
```

  
##  <a name="operator_lpcrect"></a>Konwertuje lpcrect — CRect::operator `CRect` do [lpcrect —](../../mfc/reference/data-types-mfc.md).  

  
```  
operator LPCRECT() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Korzystając z tej funkcji, nie potrzebujesz adresu z (**&**) operatora. Ten operator będzie automatycznie używany podczas przekazywania `CRect` obiektu do funkcji, która oczekuje **lpcrect —**.  
  

##  <a name="operator_lprect"></a>CRect::operator lprect —  
 Konwertuje `CRect` do [lprect —](../../mfc/reference/data-types-mfc.md).  

  
```
operator LPRECT() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Korzystając z tej funkcji, nie potrzebujesz adresu z (**&**) operatora. Ten operator będzie automatycznie używany podczas przekazywania `CRect` obiektu do funkcji, która oczekuje `LPRECT`.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [lpcrect — CRect::operator](#operator_lpcrect).  
  
##  <a name="operator_eq"></a>CRect::operator =  
 Przypisuje *srcRect* do `CRect`.  
  
```  
void operator=(const RECT& srcRect) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *srcRect*  
 Odnosi się do prostokąta źródłowego. Może być [RECT](../../mfc/reference/rect-structure1.md) lub `CRect`.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect(0, 0, 127, 168);
 CRect rect2;

```cpp  
   CRect rect(0, 0, 127, 168);
   CRect rect2;

   rect2 = rect;
   ASSERT(rect2 == CRect(0, 0, 127, 168));   
```

  
##  <a name="operator_eq_eq"></a>CRect::operator ==  
 Określa, czy `rect` jest równa `CRect` porównując współrzędne ich rogi górnego lewego i prawego dolnego.  
  
```  
BOOL operator==(const RECT& rect) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Odnosi się do prostokąta źródłowego. Może być [RECT](../../mfc/reference/rect-structure1.md) lub `CRect`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli takie same; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect1(35, 150, 10, 25);
 CRect rect2(35, 150, 10, 25);
 CRect rect3(98, 999,  6,  3);

```cpp  
   CRect rect1(35, 150, 10, 25);
   CRect rect2(35, 150, 10, 25);
   CRect rect3(98, 999, 6, 3);
ASSERT(rect1 == rect2);
 // works just fine against RECTs, as well

 RECT test;
 test.left = 35;
 test.top = 150;
 test.right = 10;
 test.bottom = 25;

 ASSERT(rect1 == test);  
```

  
##  <a name="operator_neq"></a>CRect::operator! =  
 Określa, czy `rect` nie jest równa `CRect` porównując współrzędne ich rogi górnego lewego i prawego dolnego.  
  
```  
BOOL operator!=(const RECT& rect) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Odnosi się do prostokąta źródłowego. Może być [RECT](../../mfc/reference/rect-structure1.md) lub `CRect`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli nie jest równa; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect1(35, 150, 10, 25);
 CRect rect2(35, 150, 10, 25);
 CRect rect3(98, 999,  6,  3);

```cpp  
   CRect rect1(35, 150, 10, 25);
   CRect rect2(35, 150, 10, 25);
   CRect rect3(98, 999, 6, 3);
ASSERT(rect1 != rect3);
 // works just fine against RECTs, as well

 RECT test;
 test.left = 35;
 test.top = 150;
 test.right = 10;
 test.bottom = 25;

 ASSERT(rect3 != test);  
```
  
##  <a name="operator_add_eq"></a>CRect::operator +=  
 Przenieś pierwsze dwa przeciążenia `CRect` przez określonych przesunięć.  
  
```  
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 A [punktu](../../mfc/reference/point-structure1.md) struktury lub [CPoint](cpoint-class.md) obiekt, który określa liczbę jednostek prostokąt.  
  
 `size`  
 A [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](csize-class.md) obiekt, który określa liczbę jednostek prostokąt.  
  
 `lpRect`  
 Wskazuje [RECT](../../mfc/reference/rect-structure1.md) struktury lub `CRect` obiekt, który zawiera liczbę jednostek na każdej stronie zwiększyć `CRect`.  
  
### <a name="remarks"></a>Uwagi  
 Parametr *x* i *y* (lub `cx` i `cy`) wartości są dodawane do `CRect`.  
  
 Trzeci przeciążenia nadyma `CRect` przez liczbę jednostek określona w każdym elemencie członkowskim parametru.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect1(100, 235, 200, 335);
 CPoint pt(35, 65);
 CRect rect2(135, 300, 235, 400);

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2(135, 300, 235, 400);

   rect1 += pt;
   ASSERT(rect1 == rect2);   
```
  
##  <a name="operator_-_eq"></a>CRect::operator-=  
 Przenieś pierwsze dwa przeciążenia `CRect` przez określonych przesunięć.  
  
```  
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 A [punktu](../../mfc/reference/point-structure1.md) struktury lub [CPoint](cpoint-class.md) obiekt, który określa liczbę jednostek prostokąt.  
  
 `size`  
 A [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](csize-class.md) obiekt, który określa liczbę jednostek prostokąt.  
  
 `lpRect`  
 Wskazuje [RECT](../../mfc/reference/rect-structure1.md) struktury lub `CRect` obiekt, który zawiera liczbę jednostek do korygowania każdej strony `CRect`.  
  
### <a name="remarks"></a>Uwagi  
 Parametr *x* i *y* (lub `cx` i `cy`) wartości jest odejmowany od `CRect`.  
  
 Trzeci przeciążenia deflates `CRect` przez liczbę jednostek określona w każdym elemencie członkowskim parametru. Należy pamiętać, że to przeciążenie funkcji takich jak [DeflateRect](#deflaterect).  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect1(100, 235, 200, 335);
 CPoint pt(35, 65);
 rect1 -= pt;

```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);

   rect1 -= pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect1 == rectResult);   
```
  
##  <a name="operator_amp_eq"></a>CRect::operator&amp;=  
 Ustawia `CRect` równą część wspólną `CRect` i `rect`.  
  
```  
void operator&=(const RECT& rect) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Zawiera [RECT](../../mfc/reference/rect-structure1.md) lub `CRect`.  
  
### <a name="remarks"></a>Uwagi  
 Część wspólną ma największy prostokąt zawarte w obu prostokąty.  
  
> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CRect::IntersectRect](#intersectrect).  
  
##  <a name="operator_or_eq"></a>CRect::operator &#124; =  
 Ustawia `CRect` równa złożenie `CRect` i `rect`.  
  
```  
void operator|=(const RECT& rect) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Zawiera `CRect` lub [RECT](../../mfc/reference/rect-structure1.md).  
  
### <a name="remarks"></a>Uwagi  
 Unia jest najmniejszego prostokąta zawierający zarówno prostokąty źródła.  
  
> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect1(100,   0, 200, 300);
 CRect rect2( 0, 100, 300, 200);
 rect1 |= rect2;

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);

   rect1 |= rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect1);   
```

  
##  <a name="operator_add"></a>CRect::operator +  
 Zwraca pierwsze dwa przeciążenia `CRect` obiekt, który jest taki sam `CRect` przesuwane za pomocą określonego przesunięcia.  
  
```  
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 A [punktu](../../mfc/reference/point-structure1.md) struktury lub [CPoint](cpoint-class.md) obiekt, który określa liczbę jednostek można przenieść wartości zwracanej.  
  
 `size`  
 A [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](csize-class.md) obiekt, który określa liczbę jednostek można przenieść wartości zwracanej.  
  
 `lpRect`  
 Wskazuje [RECT](../../mfc/reference/rect-structure1.md) struktury lub `CRect` obiekt, który zawiera liczbę jednostek, aby zwiększyć wartości zwracanej każdej strony.  
  
### <a name="return-value"></a>Wartość zwracana  
 `CRect` Wyniku przenoszenia lub pompowania `CRect` przez liczbę jednostek określona w parametrze.  
  
### <a name="remarks"></a>Uwagi  
 Parametr *x* i *y* (lub `cx` i `cy`) parametry są dodawane do `CRect`na pozycji.  
  
 Trzeci przeciążenia zwraca nową `CRect` jest równa `CRect` zwiększony przez liczbę jednostek określona w każdym elemencie członkowskim parametru.  
  
### <a name="example"></a>Przykład  
```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 + pt;
   CRect   rectResult(135, 300, 235, 400);
   ASSERT(rectResult == rect2);   
```

  
##  <a name="operator_-"></a>CRect::operator-  
 Zwraca pierwsze dwa przeciążenia `CRect` obiekt, który jest taki sam `CRect` przesuwane za pomocą określonego przesunięcia.  
  
```  
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 A [punktu](../../mfc/reference/point-structure1.md) struktury lub `CPoint` obiekt, który określa liczbę jednostek można przenieść wartości zwracanej.  
  
 `size`  
 A [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub `CSize` obiekt, który określa liczbę jednostek można przenieść wartości zwracanej.  
  
 `lpRect`  
 Wskazuje [RECT](../../mfc/reference/rect-structure1.md) struktury lub `CRect` obiekt, który zawiera liczbę jednostek do korygowania każdej strony zwracanej wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 `CRect` Wyniku przenoszenia lub przeliczania `CRect` przez liczbę jednostek określona w parametrze.  
  
### <a name="remarks"></a>Uwagi  
 Parametr *x* i *y* (lub `cx` i `cy`) parametrów jest odejmowany od `CRect`na pozycji.  
  
 Trzeci przeciążenia zwraca nową `CRect` jest równa `CRect` za pomocą liczba jednostek określona w każdym elemencie członkowskim parametru. Należy pamiętać, że to przeciążenie funkcji takich jak [DeflateRect](#deflaterect), a nie [SubtractRect](#subtractrect).  
  
### <a name="example"></a>Przykład  
```cpp  
   CRect   rect1(100, 235, 200, 335);
   CPoint pt(35, 65);
   CRect   rect2;

   rect2 = rect1 - pt;
   CRect   rectResult(65, 170, 165, 270);
   ASSERT(rect2 == rectResult);   
```

  
##  <a name="operator_amp"></a>CRect::operator&amp;  
 Zwraca `CRect` czyli przecięcie `CRect` i *rect2*.  
  
```  
CRect operator&(const RECT& rect2) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *rect2*  
 Zawiera [RECT](../../mfc/reference/rect-structure1.md) lub `CRect`.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CRect` czyli przecięcie `CRect` i *rect2*.  
  
### <a name="remarks"></a>Uwagi  
 Część wspólną ma największy prostokąt zawarte w obu prostokąty.  
  
> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 & rect2;
   CRect   rectResult(100, 100, 200, 200);
   ASSERT(rectResult == rect3);   
```

  
##  <a name="operator_or"></a>CRect::operator &#124;  
 Zwraca `CRect` to znaczy sumę `CRect` i *rect2*.  
  
```   
CRect operator|(const RECT& 
rect2) const throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 *rect2*  
 Zawiera [RECT](../../mfc/reference/rect-structure1.md) lub `CRect`.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CRect` to znaczy sumę `CRect` i *rect2*.  
  
### <a name="remarks"></a>Uwagi  
 Unia jest najmniejszego prostokąta zawierający zarówno prostokąty.  
  
> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect1(100,   0, 200, 300);
 CRect rect2( 0, 100, 300, 200);
 CRect rect3;

```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3 = rect1 | rect2;
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);   
```

  
##  <a name="ptinrect"></a>CRect::PtInRect  
 Określa, czy określony punkt znajduje się w obrębie `CRect`.  
  
```   
BOOL PtInRect(POINT point) const throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Zawiera [punktu](../../mfc/reference/point-structure1.md) struktury lub [CPoint](cpoint-class.md) obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli punkt znajduje się w obrębie `CRect`; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Punkt znajduje się w `CRect` jeśli znajduje się po lewej lub górnej lub jest w obrębie wszystkich czterech krawędzi. Punkt po prawej lub dolnej znajduje się poza `CRect`.  
  
> [!NOTE]
>  Prostokąt muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąt przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect(5, 5, 100, 100);
 CPoint pt1(35, 50);
 CPoint pt2(125, 298);

 // this is true, because pt1 is inside the rectangle
 ASSERT(rect.PtInRect(pt1));

 // this is NOT true, because pt2 is outside the rectangle
 ASSERT(!rect.PtInRect(pt2));

 // note that the right and the bottom aren't inside
 ASSERT(!rect.PtInRect(CPoint(35, 100)));
 ASSERT(!rect.PtInRect(CPoint(100, 98)));

 // but the top and the left are inside
 ASSERT(rect.PtInRect(CPoint(5, 65)));
 ASSERT(rect.PtInRect(CPoint(88, 5)));

 // and that PtInRect() works against a POINT, too
 POINT pt;
 pt.x = 35;
 pt.y = 50;
 ASSERT(rect.PtInRect(pt));  
```
  
##  <a name="setrect"></a>CRect::SetRect  
 Ustawia wymiary `CRect` do określonych współrzędnych.  
  
```   
void SetRect(int x1, int y1, int x2, int y2) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `x1`  
 Określa współrzędną x lewego górnego rogu.  
  
 `y1`  
 Określa współrzędną y lewego górnego rogu.  
  
 `x2`  
 Określa współrzędną x prawym dolnym rogu.  
  
 `y2`  
 Określa współrzędną y prawego dolnego rogu.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect;
 rect.SetRect(256, 256, 512, 512);

```cpp  
   CRect rect;
   rect.SetRect(256, 256, 512, 512);
   ASSERT(rect == CRect(256, 256, 512, 512));   
```

  
##  <a name="setrectempty"></a>CRect::SetRectEmpty  
 Sprawia, że `CRect` zerowy prostokąt przez ustawienie wszystkie współrzędne od zera.  
  
```  
void SetRectEmpty() throw();
```  
  
### <a name="example"></a>Przykład  
```cpp  
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());  
```
  
##  <a name="size"></a>CRect::SIZE 
 `cx` i `cy` zawierają elementy członkowskie wartości zwracanej wysokość i szerokość `CRect`.  
  
```  
CSize Size() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CSize](csize-class.md) obiekt, który zawiera rozmiar `CRect`.  
  
### <a name="remarks"></a>Uwagi  
 Wysokość lub szerokość może być ujemna.  
  
> [!NOTE]
>  Prostokąt muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąt przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
```cpp  
 CRect rect(10, 10, 50, 50);
 CSize sz = rect.Size();
 ASSERT(sz.cx == 40 && sz.cy == 40);  
```

##  <a name="subtractrect"></a>CRect::SubtractRect  
 Powoduje, że wymiary **CRect** równa odejmowanie `lpRectSrc2` z `lpRectSrc1`.  
  
```  
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpRectSrc1`  
 Wskazuje [RECT](../../mfc/reference/rect-structure1.md) struktury lub `CRect` obiektu, z którego ma być odjęta prostokąta.  
  
 `lpRectSrc2`  
 Wskazuje `RECT` struktury lub `CRect` obiekt, który ma być odjęta od prostokąt wskazywana przez `lpRectSrc1` parametru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Odejmowania jest najmniejszego prostokąta, który zawiera wszystkie punkty w `lpRectScr1` nie znajdują się w część wspólną `lpRectScr1` i *lpRectScr2*.  
  
 Prostokąt określony przez `lpRectSrc1` pozostaje bez zmian, jeśli prostokąt określony przez `lpRectSrc2` całkowicie nie nakładają się na prostokąt określony przez *lpRectSrc1* w co najmniej jednym z x - lub y instrukcje.  
  
 Na przykład jeśli `lpRectSrc1` zostały (10,10, 100,100) i `lpRectSrc2` zostały (50,50, 150,150), prostokąt wskazywana przez `lpRectSrc1` byłoby bez zmian, gdy wartość zwrócona przez funkcję. Jeśli `lpRectSrc1` zostały (10,10, 100,100) i `lpRectSrc2` zostały (50,10, 150,150), jednak prostokąt wskazywana przez `lpRectSrc1` będzie zawierać współrzędne (10,10, 50,100) Jeśli wartość zwrócona przez funkcję.  
  
 `SubtractRect`nie jest taka sama jak [operator -](#operator_-) ani [operator-=](#operator_-_eq). Żadna z tych operatorów kiedykolwiek wywołuje `SubtractRect`.  
  
> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
```cpp  
   RECT   rectOne;
   RECT   rectTwo;

   rectOne.left = 10;
   rectOne.top = 10;
   rectOne.bottom = 100;
   rectOne.right = 100;

   rectTwo.left = 50;
   rectTwo.top = 10;
   rectTwo.bottom = 150;
   rectTwo.right = 150;

   CRect   rectDiff;

   rectDiff.SubtractRect(&rectOne, &rectTwo);
CRect   rectResult(10, 10, 50, 100);

   ASSERT(rectDiff == rectResult);

   // works for CRect, too, since there is
   // implicit CRect -> LPCRECT conversion

   CRect rect1(10, 10, 100, 100);
   CRect rect2(50, 10, 150, 150);
   CRect rectOut;

   rectOut.SubtractRect(rect1, rect2);
   ASSERT(rectResult == rectOut);   
```
  
##  <a name="topleft"></a>CRect::TopLeft  
 Współrzędne są zwracane jako odwołanie do [CPoint](cpoint-class.md) obiektu, który jest zawarty w `CRect`.  
  
```  
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Współrzędne górnego lewego rogu prostokąta.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja umożliwia należy pobrać lub ustawić górnego lewego rogu prostokąta. Ustaw rogu przy użyciu tej funkcji po lewej stronie operatora przypisania.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CRect::CenterPoint](#centerpoint).  
  
##  <a name="unionrect"></a>CRect::UnionRect  
 Powoduje, że wymiary `CRect` równa Unii prostokąty dwa źródła.  
  
```  
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect1`  
 Wskazuje [RECT](../../mfc/reference/rect-structure1.md) lub `CRect` zawierający prostokąta źródłowego.  
  
 `lpRect2`  
 Wskazuje `RECT` lub `CRect` zawierający prostokąta źródłowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli połączenie nie jest pusty; 0, jeśli Unii jest pusta.  
  
### <a name="remarks"></a>Uwagi  
 Unia jest najmniejszego prostokąta zawierający zarówno prostokąty źródła.  
  
 Windows ignoruje wymiary pusty prostokąt; oznacza to, które ma nie wysokość lub szerokość nie prostokąt.  
  
> [!NOTE]
>  Zarówno prostokątów muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokątów przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  
```cpp  
   CRect   rect1(100,  0, 200, 300);
   CRect   rect2(0, 100, 300, 200);
   CRect   rect3;

   rect3.UnionRect(&rect1, &rect2);
   CRect   rectResult(0, 0, 300, 300);
   ASSERT(rectResult == rect3);   
```
 
##  <a name="width"></a>CRect::Width  
 Oblicza szerokość `CRect` przez odjęcie wartości po lewej stronie z wartość prawej strony.  
  
```  
int Width() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość `CRect`.  
  
### <a name="remarks"></a>Uwagi  
 Szerokość może być ujemna.  
  
> [!NOTE]
>  Prostokąt muszą być znormalizowane lub tej funkcji może zakończyć się niepowodzeniem. Możesz wywołać [NormalizeRect](#normalizerect) do normalizacji prostokąt przed wywołaniem tej funkcji.  
  
### <a name="example"></a>Przykład  

```cpp  
   CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
   // nWid is now 60
   ASSERT(nWid == 60);   
```
## <a name="see-also"></a>Zobacz też  
 [Klasa CPoint](cpoint-class.md)   
 [Klasa CSize](csize-class.md)   
 [RECT](../../mfc/reference/rect-structure1.md)


