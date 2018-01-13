---
title: Klasa CAtlList | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlList
- ATLCOLL/ATL::CAtlList
- ATLCOLL/ATL::CAtlList::INARGTYPE
- ATLCOLL/ATL::CAtlList::CAtlList
- ATLCOLL/ATL::CAtlList::AddHead
- ATLCOLL/ATL::CAtlList::AddHeadList
- ATLCOLL/ATL::CAtlList::AddTail
- ATLCOLL/ATL::CAtlList::AddTailList
- ATLCOLL/ATL::CAtlList::AssertValid
- ATLCOLL/ATL::CAtlList::Find
- ATLCOLL/ATL::CAtlList::FindIndex
- ATLCOLL/ATL::CAtlList::GetAt
- ATLCOLL/ATL::CAtlList::GetCount
- ATLCOLL/ATL::CAtlList::GetHead
- ATLCOLL/ATL::CAtlList::GetHeadPosition
- ATLCOLL/ATL::CAtlList::GetNext
- ATLCOLL/ATL::CAtlList::GetPrev
- ATLCOLL/ATL::CAtlList::GetTail
- ATLCOLL/ATL::CAtlList::GetTailPosition
- ATLCOLL/ATL::CAtlList::InsertAfter
- ATLCOLL/ATL::CAtlList::InsertBefore
- ATLCOLL/ATL::CAtlList::IsEmpty
- ATLCOLL/ATL::CAtlList::MoveToHead
- ATLCOLL/ATL::CAtlList::MoveToTail
- ATLCOLL/ATL::CAtlList::RemoveAll
- ATLCOLL/ATL::CAtlList::RemoveAt
- ATLCOLL/ATL::CAtlList::RemoveHead
- ATLCOLL/ATL::CAtlList::RemoveHeadNoReturn
- ATLCOLL/ATL::CAtlList::RemoveTail
- ATLCOLL/ATL::CAtlList::RemoveTailNoReturn
- ATLCOLL/ATL::CAtlList::SetAt
- ATLCOLL/ATL::CAtlList::SwapElements
dev_langs: C++
helpviewer_keywords: CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13d26ba7107e21e64ad65ec53264b4f3740fd13a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="catllist-class"></a>Klasa CAtlList
Ta klasa dostarcza metody do tworzenia i zarządzania obiekt listy.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename E, class ETraits = CElementTraits<E>>  
class CAtlList
```  
  
#### <a name="parameters"></a>Parametry  
 `E`  
 Typ elementu.  
  
 `ETraits`  
 Kod używany do kopiowania lub przenoszenia elementów. Zobacz [CElementTraits klasy](../../atl/reference/celementtraits-class.md) więcej szczegółów.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlList::INARGTYPE](#inargtype)||  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlList::CAtlList](#catllist)|Konstruktor.|  
|[CAtlList:: ~ CAtlList](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlList::AddHead](#addhead)|Wywołaj tę metodę w celu dodania elementu do head listy.|  
|[CAtlList::AddHeadList](#addheadlist)|Wywołanie tej metody można dodać istniejącej listy nagłówek listy.|  
|[CAtlList::AddTail](#addtail)|Wywołaj tę metodę w celu dodania elementu do fragmentu tej listy.|  
|[CAtlList::AddTailList](#addtaillist)|Wywołanie tej metody można dodać istniejącej listy na końcu tej listy.|  
|[CAtlList::AssertValid](#assertvalid)|Wywołaj tę metodę, aby potwierdzić, że lista jest nieprawidłowy.|  
|[CAtlList::Find](#find)|Wywołanie tej metody do wyszukiwania dla określonego elementu listy.|  
|[CAtlList::FindIndex](#findindex)|Wywołaj tę metodę, aby uzyskać położenie elementu w danej wartości indeksu.|  
|[CAtlList::GetAt](#getat)|Wywołaj tę metodę, aby zwracać element na określonej pozycji na liście.|  
|[CAtlList::GetCount](#getcount)|Wywołaj tę metodę, aby zwrócić liczbę obiektów na liście.|  
|[CAtlList::GetHead](#gethead)|Wywołaj tę metodę, aby zwrócić elementu head listy.|  
|[CAtlList::GetHeadPosition](#getheadposition)|Wywołaj tę metodę w celu uzyskania pozycja head listy.|  
|[CAtlList::GetNext](#getnext)|Wywołaj tę metodę w celu zwrócenia następnego elementu z listy.|  
|[CAtlList::GetPrev](#getprev)|Wywołaj tę metodę w celu zwrócenia poprzedni element z listy.|  
|[CAtlList::GetTail](#gettail)|Wywołaj tę metodę, aby zwracać element na końcu listy.|  
|[CAtlList::GetTailPosition](#gettailposition)|Wywołaj tę metodę w celu uzyskania pozycja tail listy.|  
|[CAtlList::InsertAfter](#insertafter)|Wywołaj tę metodę, aby wstawić nowy element do listy po określonej pozycji.|  
|[CAtlList::InsertBefore](#insertbefore)|Wywołaj tę metodę, aby wstawić nowy element do listy przed określonej pozycji.|  
|[CAtlList::IsEmpty](#isempty)|Wywołaj tę metodę, aby określić, jeśli lista jest pusta.|  
|[CAtlList::MoveToHead](#movetohead)|Wywołanie tej metody, aby przenieść określony element head listy.|  
|[CAtlList::MoveToTail](#movetotail)|Wywołaj tę metodę, aby przenieść określony element na końcu listy.|  
|[CAtlList::RemoveAll](#removeall)|Wywołaj tę metodę, aby usunąć wszystkie elementy z listy.|  
|[CAtlList::RemoveAt](#removeat)|Wywołaj tę metodę, aby usunąć pojedynczego elementu z listy.|  
|[CAtlList::RemoveHead](#removehead)|Wywołanie tej metody można usunąć elementu head listy.|  
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Wywołanie tej metody można usunąć elementu head listy bez zwracania wartości.|  
|[CAtlList::RemoveTail](#removetail)|Wywołaj tę metodę, aby usunąć element na końcu listy.|  
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Wywołaj tę metodę, aby usunąć element na końcu listy bez zwracania wartości.|  
|[CAtlList::SetAt](#setat)|Wywołanie tej metody można ustawić wartości elementu na określonej pozycji na liście.|  
|[CAtlList::SwapElements](#swapelements)|Wywołanie tej metody można zamienić elementów na liście.|  
  
## <a name="remarks"></a>Uwagi  
 `CAtlList` Klasy obsługuje uporządkowane listy obiektów nieunikatowy dostępny sekwencyjnie lub przez wartość. `CAtlList`Wyświetla przypominają podwójnie połączonej listy. Każda lista ma head i tail oraz nowe elementy (lub list w niektórych przypadkach) można dodać na dowolnym jej końcu listy lub wstawiony przed lub po określonych elementów.  
  
 Większość `CAtlList` metody należy użyć wartości pozycji. Ta wartość jest używana przez metody do odwołania lokalizacji pamięci rzeczywista, której elementy są przechowywane i nie należy obliczyć ani przewidzieć bezpośrednio. Jeśli konieczne jest, aby uzyskać dostęp do  *n* element th na liście, Metoda [CAtlList::FindIndex](#findindex) zwróci wartość pozycji odpowiednie dla danego indeksu. Metody [CAtlList::GetNext](#getnext) i [CAtlList::GetPrev](#getprev) może służyć do iterowania po obiektów na liście.  
  
 Aby uzyskać więcej informacji na temat klasy kolekcji ATL dostępne, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="addhead"></a>CAtlList::AddHead  
 Wywołaj tę metodę w celu dodania elementu do head listy.  
  
```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `element`  
 Nowy element.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pozycję nowo dodany element.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli używana jest pierwszą wersję, pustego elementu jest tworzony przy użyciu jego konstruktora kopiującego, a nie jego domyślny konstruktor.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]  
  
##  <a name="addheadlist"></a>CAtlList::AddHeadList  
 Wywołanie tej metody można dodać istniejącej listy nagłówek listy.  
  
```
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```  
  
### <a name="parameters"></a>Parametry  
 `plNew`  
 Lista do dodania.  
  
### <a name="remarks"></a>Uwagi  
 Listy wskazywana przez `plNew` dodaje się na początku listy. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli `plNew` jest równa NULL.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]  
  
##  <a name="addtail"></a>CAtlList::AddTail  
 Wywołaj tę metodę w celu dodania elementu do fragmentu tej listy.  
  
```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `element`  
 Element do dodania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pozycję nowo dodany element.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli używana jest pierwszą wersję, pustego elementu jest tworzony przy użyciu jego konstruktora kopiującego, a nie jego domyślny konstruktor. Element zostanie dodany na końcu listy, a więc teraz staje się końcowego fragmentu. Tej metody można użyć pustej listy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]  
  
##  <a name="addtaillist"></a>CAtlList::AddTailList  
 Wywołanie tej metody można dodać istniejącej listy na końcu tej listy.  
  
```
void AddTailList(const CAtlList<E, ETraits>* plNew);
```  
  
### <a name="parameters"></a>Parametry  
 `plNew`  
 Lista do dodania.  
  
### <a name="remarks"></a>Uwagi  
 Listy wskazywana przez `plNew` dodaje się po ostatnim elemencie (jeśli istnieją) w obiekcie listy. Ostatnim elementem w `plNew` lista staje się zatem końcowego fragmentu. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli *plNew* jest równa NULL.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]  
  
##  <a name="assertvalid"></a>CAtlList::AssertValid  
 Wywołaj tę metodę, aby potwierdzić, że lista jest nieprawidłowy.  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach do debugowania błędu potwierdzenia będą wystąpić, jeśli obiekt listy jest nieprawidłowy. Aby identyfikator był prawidłowy, pusta lista musi mieć head i tail wskazujące na wartość NULL, a listy, który nie jest pusty musi mieć head i tail wskazujący prawidłowych adresów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]  
  
##  <a name="catllist"></a>CAtlList::CAtlList  
 Konstruktor.  
  
```
CAtlList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Rozmiar bloku.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor `CAtlList` obiektu. Rozmiar bloku jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszyć wywołania procedury alokacji pamięci, ale użyj więcej zasobów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]  
  
##  <a name="dtor"></a>CAtlList:: ~ CAtlList  
 Destruktor.  
  
```
~CAtlList() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby, w tym wywołaniu [CAtlList::RemoveAll](#removeall) Aby usunąć wszystkie elementy z listy.  
  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista zawiera niektóre elementy nadal po wywołaniu `RemoveAll`.  
  
##  <a name="find"></a>CAtlList::Find  
 Wywołanie tej metody do wyszukiwania dla określonego elementu listy.  
  
```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `element`  
 Element, który ma zostać odnaleziona na liście.  
  
 `posStartAfter`  
 Pozycja początkowa wyszukiwania. Jeśli nie określono wartości, wyszukiwanie rozpoczyna się od elementu głównego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość pozycji elementu, jeśli znaleziono, w przeciwnym razie zwraca wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli obiekt listy jest nieprawidłowy lub `posStartAfter` wartość jest poza zakresem.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]  
  
##  <a name="findindex"></a>CAtlList::FindIndex  
 Wywołaj tę metodę, aby uzyskać położenie elementu w danej wartości indeksu.  
  
```
POSITION FindIndex(size_t iElement) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Liczony od zera indeks elementu listy wymaganych elementów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odpowiadającej jej wartości pozycji, lub wartość NULL, jeśli `iElement` jest poza zakresem.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartość odpowiadająca wartości danego indeksu, pozycja zezwalania na dostęp do  *n* element th na liście.  
  
 W kompilacjach do debugowania błędu potwierdzenia będą wystąpić, jeśli obiekt listy jest nieprawidłowy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]  
  
##  <a name="getat"></a>CAtlList::GetAt  
 Wywołaj tę metodę, aby zwracać element na określonej pozycji na liście.  
  
```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Wartość pozycji, określając dany element.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do, lub kopię elementu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli lista jest **const**, `GetAt` zwraca kopii elementu. Metoda do użycia tylko po prawej stronie instrukcji przypisania umożliwia i chroni przed modyfikacją listy.  
  
 Jeśli lista jest **const**, `GetAt` zwraca odwołanie do elementu. Zapewnia metody do użycia po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście można zmodyfikować.  
  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli `pos` jest równa NULL.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlList::FindIndex](#findindex).  
  
##  <a name="getcount"></a>CAtlList::GetCount  
 Wywołaj tę metodę, aby zwrócić liczbę obiektów na liście.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę elementów na liście.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlList::Find](#find).  
  
##  <a name="gethead"></a>CAtlList::GetHead  
 Wywołaj tę metodę, aby zwrócić elementu head listy.  
  
```
E& GetHead() throw();
const E& GetHead() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do lub kopię, elementu head listy.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli lista jest **const**, `GetHead` zwraca kopię elementu head listy. Metoda do użycia tylko po prawej stronie instrukcji przypisania umożliwia i chroni przed modyfikacją listy.  
  
 Jeśli lista jest **const**, `GetHead` zwraca odwołanie do elementu head listy. Zapewnia metody do użycia po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście można zmodyfikować.  
  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli będą head listy punktów na wartość NULL.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlList::AddHead](#addhead).  
  
##  <a name="getheadposition"></a>CAtlList::GetHeadPosition  
 Wywołaj tę metodę w celu uzyskania pozycja head listy.  
  
```
POSITION GetHeadPosition() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość pozycji odpowiadającego elementu head listy.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli lista jest pusta, wartość zwracana jest wartość NULL.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]  
  
##  <a name="getnext"></a>CAtlList::GetNext  
 Wywołaj tę metodę w celu zwrócenia następnego elementu z listy.  
  
```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Wartość pozycji zwrócony przez poprzednie wywołanie `GetNext`, [CAtlList::GetHeadPosition](#getheadposition), lub inne `CAtlList` metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest **const**, `GetNext` zwraca kopię następnego elementu listy. Metoda do użycia tylko po prawej stronie instrukcji przypisania umożliwia i chroni przed modyfikacją listy.  
  
 Jeśli lista jest **const**, `GetNext` zwraca odwołanie do następnego elementu listy. Zapewnia metody do użycia po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście można zmodyfikować.  
  
### <a name="remarks"></a>Uwagi  
 Licznik pozycji `pos`, zostaną zmienione na punkt do następnego elementu na liście, lub wartość NULL, jeśli istnieje więcej elementów. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli `pos` jest równa NULL.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlList::GetHeadPosition](#getheadposition).  
  
##  <a name="getprev"></a>CAtlList::GetPrev  
 Wywołaj tę metodę w celu zwrócenia poprzedni element z listy.  
  
```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Wartość pozycji zwrócony przez poprzednie wywołanie `GetPrev`, [CAtlList::GetTailPosition](#gettailposition), lub inne `CAtlList` metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest **const**, `GetPrev` zwraca kopię elementu listy. Metoda do użycia tylko po prawej stronie instrukcji przypisania umożliwia i chroni przed modyfikacją listy.  
  
 Jeśli lista jest **const**, `GetPrev` zwraca odwołanie do elementu listy. Zapewnia metody do użycia po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście można zmodyfikować.  
  
### <a name="remarks"></a>Uwagi  
 Licznik pozycji `pos`, zostaną zmienione na punkt do poprzedniego elementu na liście, lub wartość NULL, jeśli istnieje więcej elementów. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli `pos` jest równa NULL.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlList::GetTailPosition](#gettailposition).  
  
##  <a name="gettail"></a>CAtlList::GetTail  
 Wywołaj tę metodę, aby zwracać element na końcu listy.  
  
```
E& GetTail() throw();
const E& GetTail() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do lub kopię, element na końcu listy.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli lista jest **const**, `GetTail` zwraca kopię elementu head listy. Metoda do użycia tylko po prawej stronie instrukcji przypisania umożliwia i chroni przed modyfikacją listy.  
  
 Jeśli lista jest **const**, `GetTail` zwraca odwołanie do elementu head listy. Zapewnia metody do użycia po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście można zmodyfikować.  
  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli będą tail listy punktów na wartość NULL.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlList::AddTail](#addtail).  
  
##  <a name="gettailposition"></a>CAtlList::GetTailPosition  
 Wywołaj tę metodę w celu uzyskania pozycja tail listy.  
  
```
POSITION GetTailPosition() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość pozycji odpowiadający element na końcu listy.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli lista jest pusta, wartość zwracana jest wartość NULL.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]  
  
##  <a name="inargtype"></a>CAtlList::INARGTYPE  
 Typ używany, gdy element jest przekazywany jako argument wejściowy.  
  
```
typedef ETraits::INARGTYPE INARGTYPE;
```  
  
##  <a name="insertafter"></a>CAtlList::InsertAfter  
 Wywołaj tę metodę, aby wstawić nowy element do listy po określonej pozycji.  
  
```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Wartość pozycji, po którym zostanie wstawiony nowego elementu.  
  
 `element`  
 Element do wstawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość pozycji nowego elementu.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli będą listy nie jest prawidłowa, czy insert nie powiedzie się, czy jest próba wstawienia elementu po końcowego fragmentu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]  
  
##  <a name="insertbefore"></a>CAtlList::InsertBefore  
 Wywołaj tę metodę, aby wstawić nowy element do listy przed określonej pozycji.  
  
```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Nowy element zostanie wstawiony do listy przed tej wartości pozycji.  
  
 `element`  
 Element do wstawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość pozycji nowego elementu.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli będą listy nie jest prawidłowa, czy insert nie powiedzie się, czy jest próba wstawienia elementu przed nagłówek.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]  
  
##  <a name="isempty"></a>CAtlList::IsEmpty  
 Wywołaj tę metodę, aby określić, jeśli lista jest pusta.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli lista nie zawiera obiektów, w przeciwnym razie wartość false.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]  
  
##  <a name="movetohead"></a>CAtlList::MoveToHead  
 Wywołanie tej metody, aby przenieść określony element head listy.  
  
```
void MoveToHead(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Wartość pozycji elementu, aby przenieść.  
  
### <a name="remarks"></a>Uwagi  
 Określony element jest przenoszona z jego bieżącym położeniu nagłówek listy. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli `pos` jest równa NULL.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]  
  
##  <a name="movetotail"></a>CAtlList::MoveToTail  
 Wywołaj tę metodę, aby przenieść określony element na końcu listy.  
  
```
void MoveToTail(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Wartość pozycji elementu, aby przenieść.  
  
### <a name="remarks"></a>Uwagi  
 Określony element jest przenoszony z jego bieżącym położeniu na koniec listy. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli `pos` jest równa NULL.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlList::MoveToHead](#movetohead).  
  
##  <a name="removeall"></a>CAtlList::RemoveAll  
 Wywołaj tę metodę, aby usunąć wszystkie elementy z listy.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa wszystkie elementy z listy i zwalnia alokacji pamięci. W kompilacjach debuguje ATLASSERT zostanie wygenerowany, jeśli wszystkie elementy nie są usuwane lub jeśli struktura listy uległa uszkodzeniu.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlList::IsEmpty](#isempty).  
  
##  <a name="removeat"></a>CAtlList::RemoveAt  
 Wywołaj tę metodę, aby usunąć pojedynczego elementu z listy.  
  
```
void RemoveAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Wartość pozycji elementu do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Odwołuje się element `pos` zostanie usunięty, i pamięci zostanie zwolniona. Można użyć `RemoveAt` do usunięcia, head lub tail listy.  
  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista jest nieprawidłowa lub usunięcie elementu powoduje, że na liście w celu dostępu do pamięci, która nie jest częścią struktury listy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]  
  
##  <a name="removehead"></a>CAtlList::RemoveHead  
 Wywołanie tej metody można usunąć elementu head listy.  
  
```
E RemoveHead();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca element przy head listy.  
  
### <a name="remarks"></a>Uwagi  
 Head element został usunięty z listy, a pamięć zostanie zwolniona. Zwracany jest kopii elementu. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista jest pusta.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]  
  
##  <a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn  
 Wywołanie tej metody można usunąć elementu head listy bez zwracania wartości.  
  
```
void RemoveHeadNoReturn() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Head element został usunięty z listy, a pamięć zostanie zwolniona. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista jest pusta.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlList::IsEmpty](#isempty).  
  
##  <a name="removetail"></a>CAtlList::RemoveTail  
 Wywołaj tę metodę, aby usunąć element na końcu listy.  
  
```
E RemoveTail();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca element na końcu listy.  
  
### <a name="remarks"></a>Uwagi  
 Tail element zostanie usunięty z listy, a pamięć zostanie zwolniona. Zwracany jest kopii elementu. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista jest pusta.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]  
  
##  <a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn  
 Wywołaj tę metodę, aby usunąć element na końcu listy bez zwracania wartości.  
  
```
void RemoveTailNoReturn() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Tail element zostanie usunięty z listy, a pamięć zostanie zwolniona. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli lista jest pusta.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlList::IsEmpty](#isempty).  
  
##  <a name="setat"></a>CAtlList::SetAt  
 Wywołanie tej metody można ustawić wartości elementu na określonej pozycji na liście.  
  
```
void SetAt(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Wartość pozycji odpowiadający element, aby zmienić.  
  
 `element`  
 Nowa wartość elementu.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje istniejącą wartość z `element`. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli `pos` jest równa NULL.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]  
  
##  <a name="swapelements"></a>CAtlList::SwapElements  
 Wywołanie tej metody można zamienić elementów na liście.  
  
```
void SwapElements(POSITION pos1, POSITION pos2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pos1*  
 Pierwsza wartość pozycji.  
  
 *pos2*  
 Druga wartość pozycji.  
  
### <a name="remarks"></a>Uwagi  
 Zamienia elementy w dwóch miejscach. W kompilacjach do debugowania błędu potwierdzenia będzie wystąpić, jeśli obie wartości pozycji jest równa NULL.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Clist — klasa](../../mfc/reference/clist-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
