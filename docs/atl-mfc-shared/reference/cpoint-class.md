---
title: Klasa CPoint | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
dev_langs: C++
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7140e2db55db8a28c1af63f89517708f4dc0d835
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cpoint-class"></a>Klasa CPoint
Podobne do systemu Windows `POINT` struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPoint : public tagPOINT 
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPoint::CPoint](#cpoint)|Konstruuje `CPoint`.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPoint::Offset](#offset)|Dodaje wartości do **x** i **y** członkami `CPoint`.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPoint::operator-](#operator_-)|Zwraca różnicę `CPoint` i rozmiarze lub negacji punktu lub różnica w rozmiarze między dwoma punktami lub przesunięcie według rozmiaru ujemnego.|  
|[CPoint::operator! =](#operator_neq)|Sprawdza, czy nierówności między dwoma punktami.|  
|[CPoint::operator +](#operator_add)|Zwraca sumę `CPoint` i rozmiaru lub punkt, lub `CRect` przesunięty o rozmiarze.|  
|[CPoint::operator +=](#operator_add_eq)|Przesuwa `CPoint` przez dodanie rozmiaru lub punktu.|  
|[CPoint::operator-=](#operator_-_eq)|Przesuwa `CPoint` przez odjęcie rozmiaru lub punktu.|  
|[CPoint::operator ==](#operator_eq_eq)|Sprawdza, czy równości między dwoma punktami.|  
  
## <a name="remarks"></a>Uwagi  
 Funkcje elementów członkowskich do manipulowania obejmuje również `CPoint` i [punktu](../../mfc/reference/point-structure1.md) struktury.  
  
 A `CPoint` obiekt może być używane wszędzie tam, gdzie `POINT` struktura jest używana. Operatory tej klasy, które współdziałają z "rozmiar" Zaakceptuj albo [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektów lub [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury, ponieważ są one wymienne.  
  
> [!NOTE]
>  Ta klasa pochodzi od `tagPOINT` struktury. (Nazwa `tagPOINT` jest nazwą rzadziej używanych dla `POINT` struktury.) Oznacza to, że członkowie danych `POINT` struktury `x` i `y`, są dostępne dane członkami `CPoint`.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat udostępnionych klasy narzędzia (takie jak `CPoint`), zobacz [udostępnionego klasy](../../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `tagPOINT`  
  
 `CPoint`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atltypes.h  
  
##  <a name="cpoint"></a>CPoint::CPoint
 Konstruuje `CPoint` obiektu.  
  
```  
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `initX`  
 Określa wartość `x` członkiem `CPoint`.  
  
 `initY`  
 Określa wartość `y` członkiem `CPoint`.  
  
 `initPt`  
 [PUNKT](../../mfc/reference/point-structure1.md) struktury lub `CPoint` , który określa wartości używane do zainicjowania `CPoint`.  
  
 `initSize`  
 [ROZMIAR](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](../../atl-mfc-shared/reference/csize-class.md) , który określa wartości używane do zainicjowania `CPoint`.  
  
 `dwPoint`  
 Ustawia `x` członka wyrazu znaczącymi bitami `dwPoint` i `y` członka wyrazu znaczącymi bitami `dwPoint`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli są podane bez argumentów, `x` i `y` elementy członkowskie są ustawione na 0.  
  
### <a name="example"></a>Przykład  
  
```cpp   
CPoint   ptTopLeft(0, 0); 
// works from a POINT, too  
 
POINT   ptHere;  
ptHere.x = 35;  
ptHere.y = 95;  
 
CPoint   ptMFCHere(ptHere);
 
// works from a SIZE 
SIZE   sHowBig;  
sHowBig.cx = 300;  
sHowBig.cy = 10;  
 
CPoint ptMFCBig(sHowBig); 
// or from a DWORD  
 
DWORD   dwSize;  
dwSize = MAKELONG(35, 95);
 
CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```  
  
##  <a name="offset"></a>CPoint::Offset  
 Dodaje wartości do **x** i **y** członkami `CPoint`.  
  
```  
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *xOffset*  
 Określa wielkość przesunięcia **x** członkiem `CPoint`.  
  
 *yOffset*  
 Określa wielkość przesunięcia **y** członkiem `CPoint`.  
  
 `point`  
 Określa ilość ( [punktu](../../mfc/reference/point-structure1.md) lub `CPoint`) do przesunięcia `CPoint`.  
  
 `size`  
 Określa ilość ( [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) lub [CSize](../../atl-mfc-shared/reference/csize-class.md)) do przesunięcia `CPoint`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]  
  
##  <a name="operator_eq_eq"></a>CPoint::operator ==  
 Sprawdza, czy równości między dwoma punktami.  
  
```  
BOOL operator==(POINT point) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Zawiera [punktu](../../mfc/reference/point-structure1.md) struktury lub `CPoint` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli punkty są równe; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]  
  
##  <a name="operator_neq"></a>CPoint::operator! =  
 Sprawdza, czy nierówności między dwoma punktami.  
  
```  
BOOL operator!=(POINT point) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Zawiera [punktu](../../mfc/reference/point-structure1.md) struktury lub `CPoint` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli punkty nie są równe; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]  
  
##  <a name="operator_add_eq"></a>CPoint::operator +=  
 Pierwszy przeciążenia dodaje rozmiar do `CPoint`.  
  
```  
void operator+=(SIZE size) throw(); 
void operator+=(POINT point) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Zawiera [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.  
  
 `point`  
 Zawiera [punktu](../../mfc/reference/point-structure1.md) struktury lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Drugi przeciążenia dodaje punkt do `CPoint`.  
  
 W obu przypadkach dodanie polega na dodaniu **x** (lub **cx**) członkiem prawostronny operand do **x** członkiem `CPoint` i dodawanie **y**  (lub **cy**) członkiem prawostronny operand do **y** członkiem `CPoint`.  
  
 Na przykład dodać `CPoint(5, -7)` do zmiennej, która zawiera `CPoint(30, 40)` zmienia zmienną `CPoint(35, 33)`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]  
  
##  <a name="operator_-_eq"></a>CPoint::operator-=  
 Rozmiar od odejmuje pierwszy przeciążenia `CPoint`.  
  
```  
void operator-=(SIZE size) throw(); 
void operator-=(POINT point) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Zawiera [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.  
  
 `point`  
 Zawiera [punktu](../../mfc/reference/point-structure1.md) struktury lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Drugi przeciążenia odejmuje punktu z `CPoint`.  
  
 W obu przypadkach odejmowania odbywa się przez odjęcie **x** (lub **cx**) członkiem prawostronny operand z **x** członkiem `CPoint` i odejmowanie **y** (lub **cy**) członkiem prawostronny operand z **y** członkiem `CPoint`.  
  
 Na przykład odjęcie `CPoint(5, -7)` ze zmienną, która zawiera `CPoint(30, 40)` zmienia zmienną `CPoint(25, 47)`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]  
  
##  <a name="operator_add"></a>CPoint::operator +  
 Użyj tego operatora, aby przesunąć `CPoint` przez `CPoint` lub `CSize` obiekt, lub do przesunięcia `CRect` przez `CPoint`.  
  
```  
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Zawiera [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.  
  
 `point`  
 Zawiera [punktu](../../mfc/reference/point-structure1.md) struktury lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiektu.  
  
 `lpRect`  
 Zawiera wskaźnik do [RECT](../../mfc/reference/rect-structure1.md) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CPoint` który przesunięty o rozmiarze **CPoint** która jest zwracana w punkcie, lub **CRect** przesunięcia przez punkt.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład przy użyciu jednej z dwóch pierwszych przeciążeń do przesunięcia punkt `CPoint(25, -19)` przez punkt `CPoint(15, 5)` lub rozmiar `CSize(15, 5)` zwraca wartość `CPoint(40, -14)`.  
  
 Dodanie prostokąta do punktu zwraca prostokąt po zostanie przesunięty **x** i **y** wartości określonych w punkcie. Na przykład za pomocą ostatniej przeciążenia do przesunięcia prostokąt `CRect(125, 219, 325, 419)` przez punkt `CPoint(25, -19)` zwraca `CRect(150, 200, 350, 400)`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]  
  
##  <a name="operator_-"></a>CPoint::operator-  
 Użyj jednej z dwóch pierwszych przeciążeń do odjęcia `CPoint` lub `CSize` obiekt z `CPoint`.  
  
```  
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 A [punktu](../../mfc/reference/point-structure1.md) struktury lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiektu.  
  
 `size`  
 A [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.  
  
 `lpRect`  
 Wskaźnik do [RECT](../../mfc/reference/rect-structure1.md) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CSize` oznacza to różnica między dwoma punktami `CPoint` który przesunięty Negacja o rozmiarze `CRect` negacji punktu, który jest równoważona lub `CPoint` czyli negacji punktu.  
  
### <a name="remarks"></a>Uwagi  
 Trzeci przeciążenia przesunięcia `CRect` przez Negacja `CPoint`. Na koniec użyj operatora jednoargumentowego, aby odwrócić `CPoint`.  
  
 Na przykład za pomocą pierwszego przeciążenia do obliczenia różnicy między dwoma punktami `CPoint(25, -19)` i `CPoint(15, 5)` zwraca `CSize(10, -24)`.  
  
 Odejmowanie `CSize` z `CPoint` jest samo obliczenie jak powyżej, ale zwraca `CPoint` obiektu nie `CSize` obiektu. Na przykład za pomocą drugiego przeciążenia do obliczenia różnicy między punktem `CPoint(25, -19)` i rozmiar `CSize(15, 5)` zwraca `CPoint(10, -24)`.  
  
 Odejmowanie prostokąt z punktu zwraca przesunięcie prostokąt przez negatywów z **x** i **y** wartości określonych w punkcie. Na przykład za pomocą ostatniej przeciążenia do przesunięcia prostokąt `CRect(125, 200, 325, 400)` przez punkt `CPoint(25, -19)` zwraca `CRect(100, 219, 300, 419)`.  
  
 Aby odwrócić punktu, należy użyć operatora jednoargumentowego. Na przykład za pomocą operatora jednoargumentowego z punktem `CPoint(25, -19)` zwraca `CPoint(-25, 19)`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MDI](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Struktura POINT](../../mfc/reference/point-structure1.md)   
 [Klasa CRect](../../atl-mfc-shared/reference/crect-class.md)   
 [CSize, klasa](../../atl-mfc-shared/reference/csize-class.md)



