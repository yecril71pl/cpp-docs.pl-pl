---
title: Ctypedptrlist — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afb32a662c538526c4fe26f6abf46e56a42de728
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ctypedptrlist-class"></a>Ctypedptrlist — klasa
Udostępnia bezpieczne "otoki" dla obiektów klasy `CPtrList`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrList : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>Parametry  
 `BASE_CLASS`  
 Klasa podstawowa klasy list typizowaną wskaźnika; musi być klasą listy wskaźnika ( `CObList` lub `CPtrList`).  
  
 `TYPE`  
 Typ elementów przechowywane na liście klasy podstawowej.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTypedPtrList::AddHead](#addhead)|Dodaje nagłówek listy (sprawia, że nowe head) elementu (lub wszystkie elementy w innej listy).|  
|[CTypedPtrList::AddTail](#addtail)|Dodaje elementu (lub wszystkie elementy w innej listy) do fragmentu listy (sprawia, że nowe fragmentu).|  
|[CTypedPtrList::GetAt](#getat)|Pobiera element na określonej pozycji.|  
|[CTypedPtrList::GetHead](#gethead)|Zwraca element head listy (nie może być pusta).|  
|[CTypedPtrList::GetNext](#getnext)|Pobiera następnego elementu potrzeby iteracji.|  
|[CTypedPtrList::GetPrev](#getprev)|Pobiera poprzedni element potrzeby iteracji.|  
|[CTypedPtrList::GetTail](#gettail)|Zwraca element tail listy (nie może być pusta).|  
|[CTypedPtrList::RemoveHead](#removehead)|Usuwa element z listy węzła głównego.|  
|[CTypedPtrList::RemoveTail](#removetail)|Usuwa element z tail listy.|  
|[CTypedPtrList::SetAt](#setat)|Ustawia element na określonej pozycji.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz `CTypedPtrList` zamiast `CObList` lub `CPtrList`, funkcji Kontrola typów języka C++ pozwala wyeliminować błędy spowodowane przez wskaźnik niezgodne typy.  
  
 Ponadto `CTypedPtrList` otoki wykonuje większość rzutowanie, które będą wymagane, jeśli używasz `CObList` lub `CPtrList`.  
  
 Ponieważ wszystkie `CTypedPtrList` funkcje są wbudowane, użyj tego szablonu nie znacząco wpływa na rozmiar lub prędkość kodu.  
  
 Wyświetla pochodzące z `CObList` może być Zserializowany, ale te pochodzące z `CPtrList` nie.  
  
 Gdy `CTypedPtrList` obiekt jest usunięty lub gdy jego elementy są usuwane, są usuwane tylko wskaźniki, nie odwołują się do jednostek.  
  
 Aby uzyskać więcej informacji na temat używania `CTypedPtrList`, zobacz artykuły [kolekcje](../../mfc/collections.md) i [na podstawie szablonu klasy](../../mfc/template-based-classes.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie powoduje utworzenie wystąpienia `CTypedPtrList`, dodaje jeden obiekt serializuje listy na dysku i usuwa obiekt:  
  
 [!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `BASE_CLASS`  
  
 `_CTypedPtrList`  
  
 `CTypedPtrList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtempl.h  
  
##  <a name="addhead"></a>  CTypedPtrList::AddHead  
 Wywołania funkcji członkowskiej `BASE_CLASS` **:: AddHead**.  
  
```  
POSITION AddHead(TYPE newElement);  
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Typ elementów przechowywane na liście klasy podstawowej.  
  
 `newElement`  
 Wskaźnik obiektu ma zostać dodany do tej listy. A **NULL** wartość jest dozwolona.  
  
 `BASE_CLASS`  
 Klasa podstawowa klasy list typizowaną wskaźnika; musi być klasą listy wskaźnika ( [CObList](../../mfc/reference/coblist-class.md) lub [CPtrList](../../mfc/reference/cptrlist-class.md)).  
  
 `pNewList`  
 Wskaźnik do innego [ctypedptrlist —](../../mfc/reference/ctypedptrlist-class.md) obiektu. Elementy w `pNewList` zostaną dodane do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pierwszą wersję **pozycji** wartość nowo wstawiony element.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszą wersję dodaje nowy element przed head listy. Druga wersja dodaje innej listy elementów przed nagłówek.  
  
##  <a name="addtail"></a>  CTypedPtrList::AddTail  
 Wywołania funkcji członkowskiej `BASE_CLASS` **:: AddTail**.  
  
```  
POSITION AddTail(TYPE newElement);  
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Typ elementów przechowywane na liście klasy podstawowej.  
  
 `newElement`  
 Wskaźnik obiektu ma zostać dodany do tej listy. A **NULL** wartość jest dozwolona.  
  
 `BASE_CLASS`  
 Klasa podstawowa klasy list typizowaną wskaźnika; musi być klasą listy wskaźnika ( [CObList](../../mfc/reference/coblist-class.md) lub [CPtrList](../../mfc/reference/cptrlist-class.md)).  
  
 `pNewList`  
 Wskaźnik do innego [ctypedptrlist —](../../mfc/reference/ctypedptrlist-class.md) obiektu. Elementy w `pNewList` zostaną dodane do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pierwszą wersję **pozycji** wartość nowo wstawiony element.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszą wersję dodaje nowy element po tail listy. Druga wersja dodaje innej listy elementów po tail listy.  
  
##  <a name="getat"></a>  CTypedPtrList::GetAt  
 Zmienna typu **pozycji** jest kluczem dla listy.  
  
```  
TYPE& GetAt(POSITION position);  
TYPE GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów przechowywane na liście.  
  
 *Stanowisko*  
 A **pozycji** wartość zwrócona przez poprzednie `GetHeadPosition` lub **znaleźć** wywołanie funkcji Członkowskich.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest dostępna za pośrednictwem wskaźnik do **const ctypedptrlist —**, następnie `GetAt` zwraca wskaźnik typu określonego przez parametr szablonu *typu*. Dzięki temu funkcja ma być używany tylko po prawej stronie instrukcji przypisania, a w związku z tym chroni przed modyfikacją listy.  
  
 Jeśli lista jest dostępny bezpośrednio lub za pomocą wskaźnika `CTypedPtrList`, następnie `GetAt` zwraca odwołanie do wskaźnika typu określonego przez parametr szablonu *typu*. Umożliwia funkcji można używać po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście do zmodyfikowania.  
  
### <a name="remarks"></a>Uwagi  
 Nie jest taka sama jak indeksu i nie może działać na **pozycji** wartość samodzielnie. `GetAt` pobiera `CObject` wskaźnika skojarzone z określonej pozycji.  
  
 Upewnij się, że Twoje **pozycji** wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
 Wywołania tej funkcji wbudowanej `BASE_CLASS` **:: GetAt**.  
  
##  <a name="gethead"></a>  CTypedPtrList::GetHead  
 Pobiera wskaźnik, który reprezentuje element head tej listy.  
  
```  
TYPE& GetHead();  
TYPE GetHead() const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów przechowywane na liście.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest dostępna za pośrednictwem wskaźnik do **const ctypedptrlist —**, następnie `GetHead` zwraca wskaźnik typu określonego przez parametr szablonu *typu*. Dzięki temu funkcja ma być używany tylko po prawej stronie instrukcji przypisania, a w związku z tym chroni przed modyfikacją listy.  
  
 Jeśli lista jest dostępny bezpośrednio lub za pomocą wskaźnika `CTypedPtrList`, następnie `GetHead` zwraca odwołanie do wskaźnika typu określonego przez parametr szablonu *typu*. Umożliwia funkcji można używać po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście do zmodyfikowania.  
  
### <a name="remarks"></a>Uwagi  
 Musi upewnij się, że listy nie jest pusty przed wywołaniem `GetHead`. Jeśli lista jest pusta, wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń. Użyj [IsEmpty](../../mfc/reference/coblist-class.md#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
##  <a name="getnext"></a>  CTypedPtrList::GetNext  
 Pobiera element listy identyfikowane przez `rPosition`, następnie ustawia `rPosition` do **pozycji** wartość następnego wpisu na liście.  
  
```  
TYPE& GetNext(POSITION& rPosition);  
TYPE GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określenie typu elementy znajdujące się na tej liście.  
  
 `rPosition`  
 Odwołanie do **pozycji** wartość zwrócona przez poprzednie `GetNext`, `GetHeadPosition`, lub inne wywołanie funkcji Członkowskich.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest dostępna za pośrednictwem wskaźnik do **const ctypedptrlist —**, następnie `GetNext` zwraca wskaźnik typu określonego przez parametr szablonu *typu*. Dzięki temu funkcja ma być używany tylko po prawej stronie instrukcji przypisania, a w związku z tym chroni przed modyfikacją listy.  
  
 Jeśli lista jest dostępny bezpośrednio lub za pomocą wskaźnika `CTypedPtrList`, następnie `GetNext` zwraca odwołanie do wskaźnika typu określonego przez parametr szablonu *typu*. Umożliwia funkcji można używać po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście do zmodyfikowania.  
  
### <a name="remarks"></a>Uwagi  
 Można użyć `GetNext` w pętli do przodu iteracji, jeśli ustanowić położenie początkowe w wyniku wywołania `GetHeadPosition` lub [CPtrList::Find](../../mfc/reference/coblist-class.md#find).  
  
 Upewnij się, że Twoje **pozycji** wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
 Jeśli element pobrane przez ostatnie na liście jest następnie nowa wartość `rPosition` ustawiono **NULL**.  
  
 Istnieje możliwość usunięcia elementu podczas iteracji. Zobacz przykład [CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat).  
  
##  <a name="getprev"></a>  CTypedPtrList::GetPrev  
 Pobiera element listy identyfikowane przez `rPosition`, następnie ustawia `rPosition` do **pozycji** wartość poprzedniej pozycji listy.  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
TYPE GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określenie typu elementy znajdujące się na tej liście.  
  
 `rPosition`  
 Odwołanie do **pozycji** wartość zwrócona przez poprzednie `GetPrev` lub inne wywołanie funkcji Członkowskich.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest dostępna za pośrednictwem wskaźnik do **const ctypedptrlist —**, następnie `GetPrev` zwraca wskaźnik typu określonego przez parametr szablonu *typu*. Dzięki temu funkcja ma być używany tylko po prawej stronie instrukcji przypisania, a w związku z tym chroni przed modyfikacją listy.  
  
 Jeśli lista jest dostępny bezpośrednio lub za pomocą wskaźnika `CTypedPtrList`, następnie `GetPrev` zwraca odwołanie do wskaźnika typu określonego przez parametr szablonu *typu*. Umożliwia funkcji można używać po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście do zmodyfikowania.  
  
### <a name="remarks"></a>Uwagi  
 Można użyć `GetPrev` w odwrotnej iteracji pętli po nawiązaniu położenie początkowe w wyniku wywołania `GetTailPosition` lub **znaleźć**.  
  
 Upewnij się, że Twoje **pozycji** wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
 Jeśli element pobrane pierwszy na liście jest następnie nowa wartość `rPosition` ustawiono **NULL**.  
  
##  <a name="gettail"></a>  CTypedPtrList::GetTail  
 Pobiera wskaźnik, który reprezentuje element head tej listy.  
  
```  
TYPE& GetTail();  
TYPE GetTail() const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów przechowywane na liście.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest dostępna za pośrednictwem wskaźnik do **const ctypedptrlist —**, następnie `GetTail` zwraca wskaźnik typu określonego przez parametr szablonu *typu*. Dzięki temu funkcja ma być używany tylko po prawej stronie instrukcji przypisania, a w związku z tym chroni przed modyfikacją listy.  
  
 Jeśli lista jest dostępny bezpośrednio lub za pomocą wskaźnika `CTypedPtrList`, następnie `GetTail` zwraca odwołanie do wskaźnika typu określonego przez parametr szablonu *typu*. Umożliwia funkcji można używać po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście do zmodyfikowania.  
  
### <a name="remarks"></a>Uwagi  
 Musi upewnij się, że listy nie jest pusty przed wywołaniem `GetTail`. Jeśli lista jest pusta, wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń. Użyj [IsEmpty](../../mfc/reference/coblist-class.md#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
##  <a name="removehead"></a>  CTypedPtrList::RemoveHead  
 Usuwa element z węzła głównego z listy i zwraca go.  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów przechowywane na liście.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik wcześniej w head listy. Ten wskaźnik jest typu określonego przez parametr szablonu *typu*.  
  
### <a name="remarks"></a>Uwagi  
 Musi upewnij się, że listy nie jest pusty przed wywołaniem `RemoveHead`. Jeśli lista jest pusta, wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń. Użyj [IsEmpty](../../mfc/reference/coblist-class.md#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
##  <a name="removetail"></a>  CTypedPtrList::RemoveTail  
 Usuwa element z tail listy i zwraca go.  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów przechowywane na liście.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik wcześniej na końcu listy. Ten wskaźnik jest typu określonego przez parametr szablonu *typu*.  
  
### <a name="remarks"></a>Uwagi  
 Musi upewnij się, że listy nie jest pusty przed wywołaniem `RemoveTail`. Jeśli lista jest pusta, wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń. Użyj [IsEmpty](../../mfc/reference/coblist-class.md#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
##  <a name="setat"></a>  CTypedPtrList::SetAt  
 Wywołania funkcji członkowskiej `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(POSITION pos, TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 **Pozycji** można ustawić elementu.  
  
 *TYP*  
 Typ elementów przechowywane na liście klasy podstawowej.  
  
 `newElement`  
 Wskaźnik do obiektu do zapisania do listy.  
  
### <a name="remarks"></a>Uwagi  
 Zmienna typu **pozycji** jest kluczem dla listy. Nie jest taka sama jak indeksu i nie może działać na **pozycji** wartość samodzielnie. `SetAt` zapisuje wskaźnik do obiektu w określonej pozycji na liście.  
  
 Upewnij się, że Twoje **pozycji** wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
 Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObList::SetAt](../../mfc/reference/coblist-class.md#setat).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC ZBIERANIE](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CPtrList](../../mfc/reference/cptrlist-class.md)   
 [Klasa CObList](../../mfc/reference/coblist-class.md)
