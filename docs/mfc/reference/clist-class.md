---
title: Clist — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CList [MFC], CList
- CList [MFC], AddHead
- CList [MFC], AddTail
- CList [MFC], Find
- CList [MFC], FindIndex
- CList [MFC], GetAt
- CList [MFC], GetCount
- CList [MFC], GetHead
- CList [MFC], GetHeadPosition
- CList [MFC], GetNext
- CList [MFC], GetPrev
- CList [MFC], GetSize
- CList [MFC], GetTail
- CList [MFC], GetTailPosition
- CList [MFC], InsertAfter
- CList [MFC], InsertBefore
- CList [MFC], IsEmpty
- CList [MFC], RemoveAll
- CList [MFC], RemoveAt
- CList [MFC], RemoveHead
- CList [MFC], RemoveTail
- CList [MFC], SetAt
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2a84e73c165efd8f2f17e66af149e33d90395e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372524"
---
# <a name="clist-class"></a>Clist — klasa
Obsługuje uporządkowane listy obiektów nieunikatowy dostępny sekwencyjnie lub przez wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class TYPE, class ARG_TYPE = const TYPE&>  
class CList : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CList::CList](#clist)|Tworzy pusty listy uporządkowanej.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CList::AddHead](#addhead)|Dodaje nagłówek listy (sprawia, że nowe head) elementu (lub wszystkie elementy w innej listy).|  
|[CList::AddTail](#addtail)|Dodaje elementu (lub wszystkie elementy w innej listy) do fragmentu listy (sprawia, że nowe fragmentu).|  
|[CList::Find](#find)|Pobiera pozycję element określony przez wartość wskaźnika.|  
|[CList::FindIndex](#findindex)|Pobiera pozycję element określony przez indeks liczony od zera.|  
|[CList::GetAt](#getat)|Pobiera element na określonej pozycji.|  
|[CList::GetCount](#getcount)|Zwraca liczbę elementów na tej liście.|  
|[CList::GetHead](#gethead)|Zwraca element head listy (nie może być pusta).|  
|[CList::GetHeadPosition](#getheadposition)|Zwraca pozycję głównym elementem na liście.|  
|[CList::GetNext](#getnext)|Pobiera następnego elementu potrzeby iteracji.|  
|[CList::GetPrev](#getprev)|Pobiera poprzedni element potrzeby iteracji.|  
|[CList::GetSize](#getsize)|Zwraca liczbę elementów na tej liście.|  
|[CList::GetTail](#gettail)|Zwraca element tail listy (nie może być pusta).|  
|[CList::GetTailPosition](#gettailposition)|Zwraca pozycję tail elementu listy.|  
|[CList::InsertAfter](#insertafter)|Wstawia nowego elementu po określonej pozycji.|  
|[CList::InsertBefore](#insertbefore)|Wstawia nowy element przed określonej pozycji.|  
|[CList::IsEmpty](#isempty)|Testy dla warunku lista jest pusta (Brak elementów).|  
|[CList::RemoveAll](#removeall)|Usuwa wszystkie elementy z tej listy.|  
|[CList::RemoveAt](#removeat)|Usuwa element z tej listy, określony przez pozycji.|  
|[CList::RemoveHead](#removehead)|Usuwa element z listy węzła głównego.|  
|[CList::RemoveTail](#removetail)|Usuwa element z tail listy.|  
|[CList::SetAt](#setat)|Ustawia element na określonej pozycji.|  
  
#### <a name="parameters"></a>Parametry  
 `TYPE`  
 Typ obiektu przechowywane na liście.  
  
 `ARG` *_* `TYPE`  
 Typ używany do odwołują się obiekty przechowywane na liście. Może być odwołanie.  
  
## <a name="remarks"></a>Uwagi  
 `CList` Wyświetla przypominają podwójnie połączone list.  
  
 Zmienna typu **pozycji** jest kluczem dla listy. Można użyć **pozycji** zmiennej iteratora przechodzenia przez listę sekwencyjnie, a zakładkę do przechowywania miejsce. Pozycji nie jest taka sama jak indeksu, jednak.  
  
 Element wstawiania jest bardzo szybkiego w head listy, na końcu oraz w znanego **pozycji**. Sekwencyjne wyszukiwania jest Wyszukiwanie elementu przez wartość lub indeksu. To wyszukiwanie może działać powoli, jeśli lista jest długa.  
  
 Zrzut poszczególne elementy na liście, należy do co najmniej 1 należy ustawić głębokość kontekstu zrzutu.  
  
 Niektóre funkcje Członkowskie wywołanie klasy funkcje globalne pomocy, które muszą być dostosowane dla większości zastosowań `CList` klasy. Zobacz [pomocnicy klasy kolekcji](../../mfc/reference/collection-class-helpers.md) w sekcji "Makra i funkcje globalne".  
  
 Aby uzyskać więcej informacji na temat używania `CList`, zapoznaj się z artykułem [kolekcji](../../mfc/collections.md).  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtempl.h  
  
##  <a name="addhead"></a>  CList::AddHead  
 Dodaje nowy element lub lista elementów nagłówek tej listy.  
  
```  
POSITION AddHead(ARG_TYPE newElement);  
void AddHead(CList* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_TYPE`  
 Parametr szablonu określający typ elementu listy (może być odwołaniem).  
  
 `newElement`  
 Nowy element.  
  
 `pNewList`  
 Wskaźnik do innego `CList` listy. Elementy w `pNewList` zostaną dodane do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pierwszą wersję **pozycji** wartość nowo wstawiony element.  
  
### <a name="remarks"></a>Uwagi  
 Lista może być pusty przed operacją.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]  
  
##  <a name="addtail"></a>  CList::AddTail  
 Dodaje nowy element lub lista elementów na końcu tej listy.  
  
```  
POSITION AddTail(ARG_TYPE newElement);  
void AddTail(CList* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_TYPE`  
 Parametr szablonu określający typ elementu listy (może być odwołaniem).  
  
 `newElement`  
 Element, który ma zostać dodany do tej listy.  
  
 `pNewList`  
 Wskaźnik do innego `CList` listy. Elementy w `pNewList` zostaną dodane do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pierwszą wersję **pozycji** wartość nowo wstawiony element.  
  
### <a name="remarks"></a>Uwagi  
 Lista może być pusty przed operacją.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]  
  
##  <a name="clist"></a>  CList::CList  
 Tworzy pusty listy uporządkowanej.  
  
```  
CList(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Stopień szczegółowości Alokacja pamięci dla rozszerzenia wykazu.  
  
### <a name="remarks"></a>Uwagi  
 Wraz z rozwojem listy, w jednostkach jest przydzielana pamięć `nBlockSize` wpisów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]  
  
##  <a name="find"></a>  CList::Find  
 Wyszukuje liście sekwencyjnie, aby znaleźć pierwszego elementu dopasowania określonego `searchValue`.  
  
```  
POSITION Find(
    ARG_TYPE searchValue,  
    POSITION startAfter = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_TYPE`  
 Parametr szablonu określający typ elementu listy (może być odwołaniem).  
  
 `searchValue`  
 Wartość, która ma zostać odnaleziona na liście.  
  
 `startAfter`  
 Pozycja początkowa wyszukiwania. Jeśli nie określono wartości, wyszukiwanie rozpoczyna się od elementu głównego.  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do iteracji lub pobieranie wskaźnika obiektu; **NULL** Jeżeli nie znaleziono obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]  
  
##  <a name="findindex"></a>  CList::FindIndex  
 Używa wartości `nIndex` jako indeks w liście.  
  
```  
POSITION FindIndex(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczony od zera indeks elementu listy do znalezienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do iteracji lub pobieranie wskaźnika obiektu; **NULL** Jeśli `nIndex` jest ujemny lub zbyt duży.  
  
### <a name="remarks"></a>Uwagi  
 Rozpoczyna się kolejny skanowania z węzła głównego listy zatrzymywanie na *n*th element.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]  
  
##  <a name="getat"></a>  CList::GetAt  
 Pobiera element listy na określonej pozycji.  
  
```  
TYPE& GetAt(POSITION position);  
const TYPE& GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Określanie typu obiektu na liście parametrów szablonu.  
  
 *Stanowisko*  
 Pozycja na liście elementu do pobrania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz opis wartości zwracanej `GetHead`.  
  
### <a name="remarks"></a>Uwagi  
 `GetAt` Zwraca element (lub odwołanie do elementu) skojarzone z określonej pozycji. Nie jest taka sama jak indeksu i nie może działać na **pozycji** wartość samodzielnie. Zmienna typu **pozycji** jest kluczem dla listy.  
  
 Upewnij się, że Twoje **pozycji** wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CList::GetHeadPosition](#getheadposition).  
  
##  <a name="getcount"></a>  CList::GetCount  
 Pobiera liczbę elementów na tej liście.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość całkowita zawierająca element count.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody spowoduje wygenerowanie takiego samego wyniku jako [CList::GetSize](#getsize) metody.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CList::RemoveHead](#removehead).  
  
##  <a name="gethead"></a>  CList::GetHead  
 Pobiera head element (lub odwołanie do elementu nagłówkowego) z tej listy.  
  
```  
const TYPE& GetHead() const;  
  
TYPE& GetHead();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Określanie typu obiektu na liście parametrów szablonu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest **const**, `GetHead` zwraca kopię elementu head listy. Umożliwia funkcję, która ma być używany tylko po prawej stronie instrukcji przypisania i chroni przed modyfikacją listy.  
  
 Jeśli lista jest **const**, `GetHead` zwraca odwołanie do elementu head listy. Umożliwia funkcji można używać po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście do zmodyfikowania.  
  
### <a name="remarks"></a>Uwagi  
 Musi upewnij się, że listy nie jest pusty przed wywołaniem `GetHead`. Jeśli lista jest pusta, wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]  
  
##  <a name="getheadposition"></a>  CList::GetHeadPosition  
 Pobiera położenie elementu head tej listy.  
  
```  
POSITION GetHeadPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do iteracji lub pobieranie wskaźnika obiektu; **NULL** Jeśli lista jest pusta.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]  
  
##  <a name="getnext"></a>  CList::GetNext  
 Pobiera element listy identyfikowane przez `rPosition`, następnie ustawia `rPosition` do **pozycji** wartość następnego wpisu na liście.  
  
```  
TYPE& GetNext(POSITION& rPosition);  
const TYPE& GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Określenie typu elementów na liście parametrów szablonu.  
  
 `rPosition`  
 Odwołanie do **pozycji** wartość zwrócona przez poprzednie `GetNext`, [GetHeadPosition](#getheadposition), lub inne wywołanie funkcji Członkowskich.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest **const**, `GetNext` zwraca kopię elementu listy. Umożliwia funkcję, która ma być używany tylko po prawej stronie instrukcji przypisania i chroni przed modyfikacją listy.  
  
 Jeśli lista jest **const**, `GetNext` zwraca odwołanie do elementu listy. Umożliwia funkcji można używać po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście do zmodyfikowania.  
  
### <a name="remarks"></a>Uwagi  
 Można użyć `GetNext` w pętli do przodu iteracji, jeśli ustanowić położenie początkowe w wyniku wywołania `GetHeadPosition` lub **znaleźć**.  
  
 Upewnij się, że Twoje **pozycji** wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
 Jeśli element pobrane przez ostatnie na liście jest następnie nowa wartość `rPosition` ustawiono **NULL**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]  
  
##  <a name="getprev"></a>  CList::GetPrev  
 Pobiera element listy identyfikowane przez `rPosition`, następnie ustawia `rPosition` do **pozycji** wartość poprzedniej pozycji listy.  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
const TYPE& GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Określenie typu elementów na liście parametrów szablonu.  
  
 `rPosition`  
 Odwołanie do **pozycji** wartość zwrócona przez poprzednie `GetPrev` lub inne wywołanie funkcji Członkowskich.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest **const**, `GetPrev` zwraca kopię elementu head listy. Umożliwia funkcję, która ma być używany tylko po prawej stronie instrukcji przypisania i chroni przed modyfikacją listy.  
  
 Jeśli lista jest **const**, `GetPrev` zwraca odwołanie do elementu listy. Umożliwia funkcji można używać po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście do zmodyfikowania.  
  
### <a name="remarks"></a>Uwagi  
 Można użyć `GetPrev` w odwrotnej iteracji pętli po nawiązaniu położenie początkowe w wyniku wywołania `GetTailPosition` lub **znaleźć**.  
  
 Upewnij się, że Twoje **pozycji** wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
 Jeśli element pobrane pierwszy na liście jest następnie nowa wartość `rPosition` ustawiono **NULL**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]  
  
##  <a name="getsize"></a>  CList::GetSize  
 Zwraca liczbę elementów listy.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów na liście.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby pobrać liczbę elementów na liście.  Wywołanie tej metody spowoduje wygenerowanie takiego samego wyniku jako [CList::GetCount](#getcount) metody.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]  
  
##  <a name="gettail"></a>  CList::GetTail  
 Pobiera `CObject` wskaźnik, który reprezentuje element tail tej listy.  
  
```  
TYPE& GetTail();  
const TYPE& GetTail() const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Określenie typu elementów na liście parametrów szablonu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz opis wartości zwracanej [GetHead](../../mfc/reference/coblist-class.md#gethead).  
  
### <a name="remarks"></a>Uwagi  
 Musi upewnij się, że listy nie jest pusty przed wywołaniem `GetTail`. Jeśli lista jest pusta, wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń. Użyj [IsEmpty](../../mfc/reference/coblist-class.md#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]  
  
##  <a name="gettailposition"></a>  CList::GetTailPosition  
 Pobiera położenie elementu tail tej listy; **NULL** Jeśli lista jest pusta.  
  
```  
POSITION GetTailPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do iteracji lub pobieranie wskaźnika obiektu; **NULL** Jeśli lista jest pusta.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]  
  
##  <a name="insertafter"></a>  CList::InsertAfter  
 Dodaje element do tej listy po elemencie w określonej pozycji.  
  
```  
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *Stanowisko*  
 A **pozycji** wartość zwrócona przez poprzednie `GetNext`, `GetPrev`, lub **znaleźć** wywołanie funkcji Członkowskich.  
  
 `ARG_TYPE`  
 Parametr szablonu określający typ elementu listy.  
  
 `newElement`  
 Element, który ma zostać dodany do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do pobierania elementu iteracji lub na liście.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]  
  
##  <a name="insertbefore"></a>  CList::InsertBefore  
 Dodaje element do tej listy przed elementem w określonej pozycji.  
  
```  
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *Stanowisko*  
 A **pozycji** wartość zwrócona przez poprzednie `GetNext`, `GetPrev`, lub **znaleźć** wywołanie funkcji Członkowskich.  
  
 `ARG_TYPE`  
 Parametr szablonu określający typ elementu listy (może być odwołaniem).  
  
 `newElement`  
 Element, który ma zostać dodany do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do pobierania elementu iteracji lub na liście.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *pozycji* jest **NULL**, element jest wstawione w head listy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]  
  
##  <a name="isempty"></a>  CList::IsEmpty  
 Wskazuje, czy ta lista nie zawiera żadnych elementów.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ta lista jest pusta. w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]  
  
##  <a name="removeall"></a>  CList::RemoveAll  
 Usuwa wszystkie elementy z tej listy i zwalnia pamięć skojarzone.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Nie zostanie wygenerowany błąd, jeśli lista jest pusta.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]  
  
##  <a name="removeat"></a>  CList::RemoveAt  
 Usuwa określony element z tej listy.  
  
```  
void RemoveAt(POSITION position);
```  
  
### <a name="parameters"></a>Parametry  
 *Stanowisko*  
 Położenie elementu do usunięcia z listy.  
  
### <a name="remarks"></a>Uwagi  
 Upewnij się, że Twoje **pozycji** wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]  
  
##  <a name="removehead"></a>  CList::RemoveHead  
 Usuwa element z węzła głównego z listy i zwraca wskaźnik do niego.  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Określenie typu elementów na liście parametrów szablonu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Element wcześniej w head listy.  
  
### <a name="remarks"></a>Uwagi  
 Musi upewnij się, że listy nie jest pusty przed wywołaniem `RemoveHead`. Jeśli lista jest pusta, wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]  
  
##  <a name="removetail"></a>  CList::RemoveTail  
 Usuwa element z tail listy i zwraca wskaźnik do niego.  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Określenie typu elementów na liście parametrów szablonu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Element, który został na końcu listy.  
  
### <a name="remarks"></a>Uwagi  
 Musi upewnij się, że listy nie jest pusty przed wywołaniem `RemoveTail`. Jeśli lista jest pusta, wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]  
  
##  <a name="setat"></a>  CList::SetAt  
 Zmienna typu **pozycji** jest kluczem dla listy.  
  
```  
void SetAt(POSITION pos, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 **Pozycji** można ustawić elementu.  
  
 `ARG_TYPE`  
 Parametr szablonu określający typ elementu listy (może być odwołaniem).  
  
 `newElement`  
 Element, który ma zostać dodany do listy.  
  
### <a name="remarks"></a>Uwagi  
 Nie jest taka sama jak indeksu i nie może działać na **pozycji** wartość samodzielnie. `SetAt` Zapisuje element w określonej pozycji na liście.  
  
 Upewnij się, że Twoje **pozycji** wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC ZBIERANIE](../../visual-cpp-samples.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CMap](../../mfc/reference/cmap-class.md)   
 [Klasa CArray](../../mfc/reference/carray-class.md)
