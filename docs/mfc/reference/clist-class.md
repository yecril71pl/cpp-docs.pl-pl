---
title: Klasa CList | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: f7079cf657d1be545f8ddb915815448a1d3b870f
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339335"
---
# <a name="clist-class"></a>Clist — klasa
Obsługuje uporządkowane listy obiektów nieunikatowych dostępnych sekwencyjnie lub według wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class TYPE, class ARG_TYPE = const TYPE&>  
class CList : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CList::CList](#clist)|Tworzy pustą listę uporządkowaną.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CList::AddHead](#addhead)|Dodaje nagłówek listy (sprawia, że nowy główny) elementu (lub wszystkie elementy w innej listy).|  
|[CList::AddTail](#addtail)|Dodaje ogona listy (sprawia, że nowe tail) elementu (lub wszystkie elementy w innej listy).|  
|[CList::Find](#find)|Pobiera położenie elementu określonego przez wartość wskaźnika.|  
|[CList::FindIndex](#findindex)|Pobiera położenie elementu, który został określony przez indeks zaczynający się od zera.|  
|[CList::GetAt](#getat)|Pobiera element na określonej pozycji.|  
|[CList::GetCount](#getcount)|Zwraca liczbę elementów na tej liście.|  
|[CList::GetHead](#gethead)|Zwraca element główny listy (nie może być pusta).|  
|[CList::GetHeadPosition](#getheadposition)|Zwraca pozycję głównego elementu listy.|  
|[CList::GetNext](#getnext)|Pobiera następny element do wykonania iteracji.|  
|[CList::GetPrev](#getprev)|Pobiera poprzedni element do wykonania iteracji.|  
|[CList::GetSize](#getsize)|Zwraca liczbę elementów na tej liście.|  
|[CList::GetTail](#gettail)|Zwraca element tail listy (nie może być pusta).|  
|[CList::GetTailPosition](#gettailposition)|Zwraca położenie elementu tail listy.|  
|[CList::InsertAfter](#insertafter)|Wstawia nowy element po określonej pozycji.|  
|[CList::InsertBefore](#insertbefore)|Wstawia nowy element przed określonej pozycji.|  
|[CList::IsEmpty](#isempty)|Testuje pod kątem warunku lista jest pusta (Brak elementów).|  
|[CList::RemoveAll](#removeall)|Usuwa wszystkie elementy z tej listy.|  
|[CList::RemoveAt](#removeat)|Usuwa element z tej listy, który jest określony za pomocą pozycji.|  
|[CList::RemoveHead](#removehead)|Usuwa element z głowy listy.|  
|[CList::RemoveTail](#removetail)|Usuwa element z zakończeniem listy.|  
|[CList::SetAt](#setat)|Ustawia element na określonej pozycji.|  
  
#### <a name="parameters"></a>Parametry  
 *TYP*  
 Typ obiektu przechowywane na liście.  
  
 *ARG* *_* *TYPU*  
 Typ używany do odwoływać się do obiektów przechowywanych na liście. Może być odwołaniem.  
  
## <a name="remarks"></a>Uwagi  
 `CList` Wyświetla zachowują się jak podwójnie połączonej listy.  
  
 Zmienna typu pozycja jest kluczem dla listy. Zmienna pozycji jako iterator umożliwia przechodzenie przez listę sekwencyjnie i jako zakładkę do przechowywania w miejscu. Pozycja nie jest taka sama jak indeksu, jednak.  
  
 Wstawianie elementu jest bardzo szybkie na czele listy w ogon i pozycja znane. Sekwencyjne wyszukiwania jest niezbędne do wyszukiwania według wartości lub indeks elementu. To wyszukiwanie może działać powoli, jeśli lista jest długa.  
  
 Zrzut poszczególne elementy na liście, należy należy ustawić głębokość kontekstu zrzutu do 1 lub większą.  
  
 Niektóre funkcje Członkowskie to wywołanie klasy, funkcje globalne pomocy, które muszą być dostosowane dla większości zastosowań `CList` klasy. Zobacz [pomocnicy klasy kolekcji](../../mfc/reference/collection-class-helpers.md) w sekcji "Makra i funkcje globalne".  
  
 Aby uzyskać więcej informacji na temat korzystania z `CList`, zapoznaj się z artykułem [kolekcje](../../mfc/collections.md).  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtempl.h  
  
##  <a name="addhead"></a>  CList::AddHead  
 Dodaje nowy element lub Podaj listę elementów do głowy tej listy.  
  
```  
POSITION AddHead(ARG_TYPE newElement);  
void AddHead(CList* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 *ARG_TYPE*  
 Parametr szablonu określający typ elementu listy (może być odwołaniem).  
  
 *newElement*  
 Nowy element.  
  
 *pNewList*  
 Wskaźnik do innego `CList` listy. Elementy w *pNewList* zostaną dodane do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwsza wersja zwraca wartość pozycji nowo wstawionego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Lista może być pusta, przed wykonaniem operacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]  
  
##  <a name="addtail"></a>  CList::AddTail  
 Dodaje nowy element lub lista elementów na końcu tej listy.  
  
```  
POSITION AddTail(ARG_TYPE newElement);  
void AddTail(CList* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 *ARG_TYPE*  
 Parametr szablonu określający typ elementu listy (może być odwołaniem).  
  
 *newElement*  
 Element, który ma zostać dodany do tej listy.  
  
 *pNewList*  
 Wskaźnik do innego `CList` listy. Elementy w *pNewList* zostaną dodane do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwsza wersja zwraca wartość pozycji nowo wstawionego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Lista może być pusta, przed wykonaniem operacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]  
  
##  <a name="clist"></a>  CList::CList  
 Tworzy pustą listę uporządkowaną.  
  
```  
CList(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parametry  
 *nBlockSize*  
 Alokacja pamięci poziom szczegółowości Rozszerzanie listy.  
  
### <a name="remarks"></a>Uwagi  
 Wraz z rozwojem listy pamięć została przydzielona w jednostkach *nBlockSize* wpisów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]  
  
##  <a name="find"></a>  CList::Find  
 Przeszukuje listę po kolei, aby znaleźć pierwszego elementu dopasowania określonej *Wyszukiwana_wartość*.  
  
```  
POSITION Find(
    ARG_TYPE searchValue,  
    POSITION startAfter = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *ARG_TYPE*  
 Parametr szablonu określający typ elementu listy (może być odwołaniem).  
  
 *Wyszukiwana_wartość*  
 Wartość, która ma zostać odnaleziona na liście.  
  
 *startAfter*  
 Pozycja początkowa wyszukiwania. Jeśli nie określono wartości, wyszukiwanie rozpoczyna się od elementu głównego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, która może służyć do iteracji lub pobieranie wskaźnika obiektu; Wartość NULL, jeśli nie można odnaleźć obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]  
  
##  <a name="findindex"></a>  CList::FindIndex  
 Używa wartości *nIndex* jako indeks do listy.  
  
```  
POSITION FindIndex(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczony od zera indeks elementu listy, które ma zostać odnaleziona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, która może służyć do iteracji lub pobieranie wskaźnika obiektu; Wartość NULL, jeśli *nIndex* jest ujemny lub zbyt duży.  
  
### <a name="remarks"></a>Uwagi  
 Uruchamia kolejne skanowania od czoła listy zatrzymywanie na *n*th element.  
  
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
 Parametr szablonu określający typ obiektu, na liście.  
  
 *Stanowisko*  
 Pozycja na liście elementu do pobrania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz opis wartości zwracanej `GetHead`.  
  
### <a name="remarks"></a>Uwagi  
 `GetAt` Zwraca element (lub odwołanie do elementu) skojarzonego z określonej pozycji. Nie jest taka sama jak indeksu, a użytkownik nie może działać na wartość pozycji samodzielnie. Zmienna typu pozycja jest kluczem dla listy.  
  
 Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CList::GetHeadPosition](#getheadposition).  
  
##  <a name="getcount"></a>  CList::GetCount  
 Pobiera liczbę elementów na tej liście.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Całkowitą zawierającą liczbę elementów.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody spowoduje wygenerowanie ten sam wynik jako [CList::GetSize](#getsize) metody.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CList::RemoveHead](#removehead).  
  
##  <a name="gethead"></a>  CList::GetHead  
 Pobiera head element (lub odwołanie do elementu głównego) tej listy.  
  
```  
const TYPE& GetHead() const;  
  
TYPE& GetHead();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ obiektu, na liście.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest **const**, `GetHead` zwraca kopię elementu na czele listy. Umożliwia korzystanie z funkcji ma być używany tylko po prawej stronie instrukcji przypisania, a chroni listy przed modyfikacją.  
  
 Jeśli lista nie jest **const**, `GetHead` zwraca odwołanie do elementu na czele listy. Umożliwia korzystanie z funkcji ma być używany po obu stronach instrukcji przypisania, a zatem umożliwia pozycji listy do zmodyfikowania.  
  
### <a name="remarks"></a>Uwagi  
 Należy upewnić się, lista nie jest pusta, przed wywołaniem `GetHead`. Jeśli lista jest pusta, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]  
  
##  <a name="getheadposition"></a>  CList::GetHeadPosition  
 Pobiera położenie elementu głównego tej listy.  
  
```  
POSITION GetHeadPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, która może służyć do iteracji lub pobieranie wskaźnika obiektu; Wartość NULL, jeśli lista jest pusta.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]  
  
##  <a name="getnext"></a>  CList::GetNext  
 Pobiera element listy identyfikowane przez *elemencie rPosition*, następnie ustawia *elemencie rPosition* wartość pozycji następnego wpisu na liście.  
  
```  
TYPE& GetNext(POSITION& rPosition);  
const TYPE& GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów na liście.  
  
 *elemencie rPosition*  
 Odwołanie do wartości pozycji, zwrócony przez poprzednie `GetNext`, [GetHeadPosition](#getheadposition), lub inne wywołanie funkcji elementu członkowskiego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest **const**, `GetNext` zwraca kopię elementu listy. Umożliwia korzystanie z funkcji ma być używany tylko po prawej stronie instrukcji przypisania, a chroni listy przed modyfikacją.  
  
 Jeśli lista nie jest **const**, `GetNext` zwraca odwołanie do elementu listy. Umożliwia korzystanie z funkcji ma być używany po obu stronach instrukcji przypisania, a zatem umożliwia pozycji listy do zmodyfikowania.  
  
### <a name="remarks"></a>Uwagi  
 Możesz użyć `GetNext` w pętli do przodu iteracji, jeśli ustanowisz początkowe położenie w wyniku wywołania `GetHeadPosition` lub `Find`.  
  
 Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.  
  
 Jeśli element pobrane ostatnio na liście jest następnie nowa wartość `rPosition` ma wartość NULL.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]  
  
##  <a name="getprev"></a>  CList::GetPrev  
 Pobiera element listy identyfikowane przez `rPosition`, następnie ustawia `rPosition` wartość pozycji poprzedni wpis na liście.  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
const TYPE& GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów na liście.  
  
 *elemencie rPosition*  
 Odwołanie do wartości pozycji, zwrócony przez poprzednie `GetPrev` lub inne wywołanie funkcji elementu członkowskiego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest **const**, `GetPrev` zwraca kopię elementu na czele listy. Umożliwia korzystanie z funkcji ma być używany tylko po prawej stronie instrukcji przypisania, a chroni listy przed modyfikacją.  
  
 Jeśli lista nie jest **const**, `GetPrev` zwraca odwołanie do elementu listy. Umożliwia korzystanie z funkcji ma być używany po obu stronach instrukcji przypisania, a zatem umożliwia pozycji listy do zmodyfikowania.  
  
### <a name="remarks"></a>Uwagi  
 Możesz użyć `GetPrev` w iteracji odwrotnej pętli, jeśli ustanowisz początkowe położenie w wyniku wywołania `GetTailPosition` lub `Find`.  
  
 Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.  
  
 Jeśli element pobrane jest pierwsze na liście, nowa wartość *elemencie rPosition* ma wartość NULL.  
  
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
 Wywołaj tę metodę, aby pobrać liczbę elementów na liście.  Wywołanie tej metody spowoduje wygenerowanie ten sam wynik jako [CList::GetCount](#getcount) metody.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]  
  
##  <a name="gettail"></a>  CList::GetTail  
 Pobiera `CObject` wskaźnika, który reprezentuje element tail tej listy.  
  
```  
TYPE& GetTail();  
const TYPE& GetTail() const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów na liście.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz opis wartości zwracanej [GetHead](../../mfc/reference/coblist-class.md#gethead).  
  
### <a name="remarks"></a>Uwagi  
 Należy upewnić się, lista nie jest pusta, przed wywołaniem `GetTail`. Jeśli lista jest pusta, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation. Użyj [IsEmpty](../../mfc/reference/coblist-class.md#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]  
  
##  <a name="gettailposition"></a>  CList::GetTailPosition  
 Pobiera położenie elementu tail tej listy; Wartość NULL, jeśli lista jest pusta.  
  
```  
POSITION GetTailPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, która może służyć do iteracji lub pobieranie wskaźnika obiektu; Wartość NULL, jeśli lista jest pusta.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]  
  
##  <a name="insertafter"></a>  CList::InsertAfter  
 Dodaje element do tej listy, po elemencie w określonej pozycji.  
  
```  
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *Stanowisko*  
 Wartość pozycji zwrócony przez poprzednie `GetNext`, `GetPrev`, lub `Find` wywołanie funkcji elementu członkowskiego.  
  
 *ARG_TYPE*  
 Parametr szablonu określający typ elementu listy.  
  
 *newElement*  
 Element, który ma zostać dodany do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, który może służyć do iteracji lub listy pobrania elementu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]  
  
##  <a name="insertbefore"></a>  CList::InsertBefore  
 Dodaje element do tej listy, przed elementem w określonej pozycji.  
  
```  
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *Stanowisko*  
 Wartość pozycji zwrócony przez poprzednie `GetNext`, `GetPrev`, lub `Find` wywołanie funkcji elementu członkowskiego.  
  
 *ARG_TYPE*  
 Parametr szablonu określający typ elementu listy (może być odwołaniem).  
  
 *newElement*  
 Element, który ma zostać dodany do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, który może służyć do iteracji lub listy pobrania elementu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *pozycji* ma wartość NULL, element jest wstawiany na czele listy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]  
  
##  <a name="isempty"></a>  CList::IsEmpty  
 Wskazuje, czy ta lista nie zawiera żadnych elementów.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli ta lista jest pusta. w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]  
  
##  <a name="removeall"></a>  CList::RemoveAll  
 Usuwa wszystkie elementy z tej listy, a następnie zwalnia pamięć skojarzone.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Błąd nie jest generowany, gdy lista jest pusty.  
  
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
 Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]  
  
##  <a name="removehead"></a>  CList::RemoveHead  
 Usuwa element z głowy listy, a następnie zwraca wskaźnik do niego.  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów na liście.  
  
### <a name="return-value"></a>Wartość zwracana  
 Element, który wcześniej na czele listy.  
  
### <a name="remarks"></a>Uwagi  
 Należy upewnić się, lista nie jest pusta, przed wywołaniem `RemoveHead`. Jeśli lista jest pusta, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]  
  
##  <a name="removetail"></a>  CList::RemoveTail  
 Usuwa element z zakończeniem listy, a następnie zwraca wskaźnik do niego.  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów na liście.  
  
### <a name="return-value"></a>Wartość zwracana  
 Element, który został na końcu listy.  
  
### <a name="remarks"></a>Uwagi  
 Należy upewnić się, lista nie jest pusta, przed wywołaniem `RemoveTail`. Jeśli lista jest pusta, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]  
  
##  <a name="setat"></a>  CList::SetAt  
 Zmienna typu pozycja jest kluczem dla listy.  
  
```  
void SetAt(POSITION pos, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *punktu sprzedaży*  
 POŁOŻENIE elementu do ustawienia.  
  
 *ARG_TYPE*  
 Parametr szablonu określający typ elementu listy (może być odwołaniem).  
  
 *newElement*  
 Element, który ma zostać dodany do listy.  
  
### <a name="remarks"></a>Uwagi  
 Nie jest taka sama jak indeksu, a użytkownik nie może działać na wartość pozycji samodzielnie. `SetAt` Zapisuje element w określonej pozycji na liście.  
  
 Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Próbki MFC ZBIERANIE](../../visual-cpp-samples.md)   
 [Klasa CObject](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CMap](../../mfc/reference/cmap-class.md)   
 [Klasa CArray](../../mfc/reference/carray-class.md)
