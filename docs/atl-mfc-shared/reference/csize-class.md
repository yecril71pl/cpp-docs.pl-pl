---
title: Klasa CSize | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
dev_langs: C++
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ac18decc8a2bb6bbc2d9e9677640eba67c85077e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="csize-class"></a>Klasa CSize
Podobne do systemu Windows [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury, która implementuje współrzędnych względnych lub pozycji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSize : public tagSIZE 
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSize::CSize](#csize)|Konstruuje `CSize` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSize::operator-](#operator_-)|Odejmuje dwóch rozmiarach.|  
|[CSize::operator! =](#operator_neq)|Sprawdza, czy nierówności między `CSize` i rozmiarze.|  
|[CSize::operator +](#operator_add)|Dodaje dwa rozmiary.|  
|[CSize::operator +=](#operator_add_eq)|Dodaje rozmiar do `CSize`.|  
|[CSize::operator-=](#operator_-_eq)|Odejmuje o rozmiarze z `CSize`.|  
|[CSize::operator ==](#operator_eq_eq)|Sprawdza, czy równość `CSize` i rozmiarze.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa pochodzi od **rozmiar** struktury. Oznacza to, że można przekazać `CSize` w parametr, który odwołuje się do **rozmiar** i elementów członkowskich danych **rozmiar** struktury są elementami członkowskimi danych dostępny `CSize`.  
  
 **Cx** i **cy** członkami **rozmiar** (i `CSize`) są publiczne. Ponadto `CSize` implementuje funkcje elementów członkowskich do manipulowania **rozmiar** struktury.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat udostępnionych klasy narzędzia (takie jak `CSize`), zobacz [udostępnionego klasy](../../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `tagSIZE`  
  
 `CSize`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atltypes.h  
  
##  <a name="csize"></a>CSize::CSize  
 Konstruuje `CSize` obiektu.  
  
```  
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 *initCX*  
 Ustawia **cx** element członkowski `CSize`.  
  
 *initCY*  
 Ustawia **cy** element członkowski `CSize`.  
  
 `initSize`  
 [ROZMIAR](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury lub `CSize` używaną do inicjalizacji obiektu `CSize`.  
  
 `initPt`  
 [PUNKT](../../mfc/reference/point-structure1.md) struktury lub `CPoint` używaną do inicjalizacji obiektu `CSize`.  
  
 `dwSize`  
 `DWORD`używany do inicjowania `CSize`. Trwa znaczącymi bitami **cx** jest element członkowski i word znaczącymi bitami **cy** elementu członkowskiego.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli są podane bez argumentów, **cx** i **cy** są inicjowane od zera.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]  
  
##  <a name="operator_eq_eq"></a>CSize::operator ==  
 Sprawdza, czy równości między dwoma rozmiary.  
  
```   
BOOL operator==(SIZE size) const throw(); 
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca wartość niezerową, jeśli rozmiary są takie same, otherwize 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]  
  
##  <a name="operator_neq"></a>CSize::operator! =  
 Sprawdza, czy nierówności między dwoma rozmiary.  
  
```   
BOOL operator!=(SIZE size) const throw(); 
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca wartość niezerową, jeśli rozmiary nie są takie same, w przeciwnym razie wartość 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]  
  
##  <a name="operator_add_eq"></a>CSize::operator +=  
 Dodaje o rozmiarze do tego `CSize`.  
  
```   
void operator+=(SIZE size) throw(); 
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]  
  
##  <a name="operator_-_eq"></a>CSize::operator-=  
 Odejmuje rozmiar tego `CSize`.  
  
```   
void operator-=(SIZE size) throw(); 
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]  
  
##  <a name="operator_add"></a>CSize::operator +  
 Dodaj tych operatorów, to `CSize` wartość parametru.  
  
```   
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw(); 
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz poniższe opisy poszczególnych operatory:  
  
- **Operator + (** `size` **)**tej operacji dodaje dwa `CSize` wartości.  
  
- **Operator + (** `point` **)**ta operacja powoduje przesunięcie (przenosi) [punktu](http://msdn.microsoft.com/library/windows/desktop/dd162805) (lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) wartość to `CSize` wartość. **Cx** i **cy** członkami to `CSize` wartości są dodawane do **x** i **y** elementów członkowskich danych **punktu**  wartość. Jest ono odpowiednikiem wersja [CPoint::operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) pobierającej [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) parametru.  
  
- **Operator + (** `lpRect` **)**ta operacja powoduje przesunięcie (przenosi) [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) (lub [CRect](../../atl-mfc-shared/reference/crect-class.md)) wartość to `CSize` wartość. **Cx** i **cy** członkami to `CSize` wartości są dodawane do **po lewej stronie**, **górnej**, **prawo**, i **dolnej** elementów członkowskich danych `RECT` wartość. Jest ono odpowiednikiem wersja [CRect::operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) pobierającej [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) parametru.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]  
  
##  <a name="operator_-"></a>CSize::operator-  
 Pierwsze trzy tych operatorów odejmowania to `CSize` wartość parametru.  
  
```   
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw(); 
```  
  
### <a name="remarks"></a>Uwagi  
 Czwarty operator jednoargumentowy minus, zmienia znak `CSize` wartość. Zobacz poniższe opisy poszczególnych operatory:  
  
- **Operator-(** `size` **)**tej operacji odejmuje dwa `CSize` wartości.  
  
- **Operator-(** `point` **)**ta operacja powoduje przesunięcie (przenosi) [punktu](http://msdn.microsoft.com/library/windows/desktop/dd162805) lub [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) wartości przez odwrotność dodatku `CSize` wartość. **Cx** i **cy** tego `CSize` wartość jest odejmowany od **x** i **y** elementów członkowskich danych **punktu**  wartość. Jest ono odpowiednikiem wersja [CPoint::operator -](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) pobierającej [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) parametru.  
  
- **Operator-(** `lpRect` **)**ta operacja powoduje przesunięcie (przenosi) [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) lub [CRect](../../atl-mfc-shared/reference/crect-class.md) wartości przez odwrotność dodatku `CSize` wartość. **Cx** i **cy** członkami to `CSize` wartość jest odejmowany od **po lewej stronie**, **górnej**, **prawo**, i **dolnej** elementów członkowskich danych `RECT` wartość. Jest ono odpowiednikiem wersja [CRect::operator -](../../atl-mfc-shared/reference/crect-class.md#operator_-) pobierającej [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) parametru.  
  
- **Operator-()**tej operacji zwraca odwrotność dodatku `CSize` wartość.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MDI](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CRect](../../atl-mfc-shared/reference/crect-class.md)   
 [CPoint, klasa](../../atl-mfc-shared/reference/cpoint-class.md)

