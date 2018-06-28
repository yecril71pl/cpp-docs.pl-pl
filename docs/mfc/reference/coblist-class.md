---
title: Klasa cObList | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CObList
- AFXCOLL/CObList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d66c26fb94fa0f4e1863a6a6a9663de4239611db
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039134"
---
# <a name="coblist-class"></a>Klasa cObList
uporządkowana lista nieunikatowy fSupports `CObject` wskaźniki dostępny sekwencyjnie lub przez wskaźnik wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CObList : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CObList::CObList](#coblist)|Tworzy pustą listę dla `CObject` wskaźników.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CObList::AddHead](#addhead)|Dodaje nagłówek listy (sprawia, że nowe head) elementu (lub wszystkie elementy w innej listy).|  
|[CObList::AddTail](#addtail)|Dodaje elementu (lub wszystkie elementy w innej listy) do fragmentu listy (sprawia, że nowe fragmentu).|  
|[CObList::Find](#find)|Pobiera pozycję element określony przez wartość wskaźnika.|  
|[CObList::FindIndex](#findindex)|Pobiera pozycję element określony przez indeks liczony od zera.|  
|[CObList::GetAt](#getat)|Pobiera element na określonej pozycji.|  
|[CObList::GetCount](#getcount)|Zwraca liczbę elementów na tej liście.|  
|[CObList::GetHead](#gethead)|Zwraca element head listy (nie może być pusta).|  
|[CObList::GetHeadPosition](#getheadposition)|Zwraca pozycję głównym elementem na liście.|  
|[CObList::GetNext](#getnext)|Pobiera następnego elementu potrzeby iteracji.|  
|[CObList::GetPrev](#getprev)|Pobiera poprzedni element potrzeby iteracji.|  
|[CObList::GetSize](#getsize)|Zwraca liczbę elementów na tej liście.|  
|[CObList::GetTail](#gettail)|Zwraca element tail listy (nie może być pusta).|  
|[CObList::GetTailPosition](#gettailposition)|Zwraca pozycję tail elementu listy.|  
|[CObList::InsertAfter](#insertafter)|Wstawia nowego elementu po określonej pozycji.|  
|[CObList::InsertBefore](#insertbefore)|Wstawia nowy element przed określonej pozycji.|  
|[CObList::IsEmpty](#isempty)|Testy dla warunku lista jest pusta (Brak elementów).|  
|[CObList::RemoveAll](#removeall)|Usuwa wszystkie elementy z tej listy.|  
|[CObList::RemoveAt](#removeat)|Usuwa element z tej listy, określony przez pozycji.|  
|[CObList::RemoveHead](#removehead)|Usuwa element z listy węzła głównego.|  
|[CObList::RemoveTail](#removetail)|Usuwa element z tail listy.|  
|[CObList::SetAt](#setat)|Ustawia element na określonej pozycji.|  
  
## <a name="remarks"></a>Uwagi  
 `CObList` Wyświetla przypominają podwójnie połączone list.  
  
 Zmienna typu **pozycji** jest kluczem dla listy. Można użyć **pozycji** zmiennej iteratora przechodzenia przez listę sekwencyjnie oraz w zakładkę do przechowywania miejsce. Pozycji nie jest taka sama jak indeksu, jednak.  
  
 Element wstawiania jest bardzo szybkiego w head listy, na końcu oraz w znanego **pozycji**. Sekwencyjne wyszukiwania jest Wyszukiwanie elementu przez wartość lub indeksu. To wyszukiwanie może działać powoli, jeśli lista jest długa.  
  
 `CObList` zawiera implement_serial — makro do obsługi serializacji i zrzucanie swoich elementów. Jeśli lista `CObject` wskaźniki są przechowywane do archiwum z operatorem przeciążone wstawiania lub z `Serialize` wszystkich funkcji członkowskiej `CObject` element jest serializowany z kolei.  
  
 Jeśli potrzebujesz zrzutu osoba `CObject` elementów na liście, należy ustawić głębokość kontekstu zrzutu 1 lub większą.  
  
 Gdy `CObList` obiekt jest usunięty lub gdy jego elementy są usuwane, tylko `CObject` wskaźniki są usuwane i nie obiektów odwołujących się.  
  
 Mogą pochodzić własnych klas z `CObList`. Nowej klasie listy, przeznaczony do przechowywania wskaźników do obiektów pochodzących od `CObject`, dodaje nowe elementy członkowskie danych i nowe funkcje elementów członkowskich. Należy zwrócić uwagę że wynikowa lista nie jest ściśle typu bezpieczne, ponieważ zezwala ona wstawiania dowolnego `CObject` wskaźnika.  
  
> [!NOTE]
>  Należy użyć [implement_serial —](run-time-object-model-services.md#implement_serial) makra w implementacji klasy pochodnej Jeśli zamierzasz serializować na liście.  
  
 Aby uzyskać więcej informacji na temat używania `CObList`, zapoznaj się z artykułem [kolekcji](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcoll.h  
  
##  <a name="addhead"></a>  CObList::AddHead  
 Dodaje nowy element lub lista elementów nagłówek tej listy.  
  
```  
POSITION AddHead(CObject* newElement);  
void AddHead(CObList* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 *newElement*  
 `CObject` Wskaźnika do dodania do tej listy.  
  
 *pNewList*  
 Wskaźnik do innego `CObList` listy. Elementy w *pNewList* zostaną dodane do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pierwszą wersję **pozycji** wartość nowo wstawiony element.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::AddHead`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja AddHead (void\***  `newElement` **);**<br /><br /> **void AddHead (CPtrList\***  `pNewList` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozycja AddHead (const cstring — &** `newElement` **);**<br /><br /> **Pozycja AddHead (LPCTSTR** `newElement` **);**<br /><br /> **void AddHead (CStringList\***  `pNewList` **);**|  
  
### <a name="remarks"></a>Uwagi  
 Lista może być pusty przed operacją.  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `AddHead example: A CObList with 2 elements`  
  
 `a CAge at $44A8 40`  
  
 `a CAge at $442A 21`  
  
##  <a name="addtail"></a>  CObList::AddTail  
 Dodaje nowy element lub lista elementów na końcu tej listy.  
  
```  
POSITION AddTail(CObject* newElement);  
void AddTail(CObList* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 *newElement*  
 `CObject` Wskaźnika do dodania do tej listy.  
  
 *pNewList*  
 Wskaźnik do innego `CObList` listy. Elementy w *pNewList* zostaną dodane do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pierwszą wersję **pozycji** wartość nowo wstawiony element.  
  
### <a name="remarks"></a>Uwagi  
 Lista może być pusty przed operacją.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::AddTail`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**AddTail pozycji (void\***  `newElement` **);**<br /><br /> **void AddTail (CPtrList\***  `pNewList` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**AddTail pozycji (const cstring — &** `newElement` **);**<br /><br /> **AddTail pozycji (LPCTSTR** `newElement` **);**<br /><br /> **void AddTail (CStringList\***  `pNewList` **);**|  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `AddTail example: A CObList with 2 elements`  
  
 `a CAge at $444A 21`  
  
 `a CAge at $4526 40`  
  
##  <a name="coblist"></a>  CObList::CObList  
 Tworzy pustą `CObject` listy wskaźnika.  
  
```  
CObList(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parametry  
 *nBlockSize*  
 Stopień szczegółowości Alokacja pamięci dla rozszerzenia wykazu.  
  
### <a name="remarks"></a>Uwagi  
 Wraz z rozwojem listy, w jednostkach jest przydzielana pamięć *nBlockSize* wpisów. W przypadku niepowodzenia alokacji pamięci `CMemoryException` jest generowany.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::CObList`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **= 10);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **= 10);**|  
  
### <a name="example"></a>Przykład  
  Poniżej znajduje się lista `CObject`-klasy `CAge` przykłady kolekcji:  
  
 [!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]  
  
 Poniżej przedstawiono przykładowy `CObList` Konstruktor użycia:  
  
 [!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]  
  
##  <a name="find"></a>  CObList::Find  
 Wyszukuje liście sekwencyjnie, aby znaleźć pierwszy `CObject` wskaźnik dopasowania określonego `CObject` wskaźnika.  
  
```  
POSITION Find(
    CObject* searchValue,  
    POSITION startAfter = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Wyszukiwana_wartość*  
 Wskaźnik obiektu ma zostać odnaleziona na liście.  
  
 *startAfter*  
 Pozycja początkowa wyszukiwania.  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do iteracji lub pobieranie wskaźnika obiektu; **NULL** Jeżeli nie znaleziono obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że są porównywane wartości wskaźników, nie zawartość obiektów.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::Find`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Znajdź pozycję (void\***  `searchValue` **, pozycja** `startAfter` **= NULL) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Znajdź pozycję (LPCTSTR** `searchValue` **, pozycja** `startAfter` **= NULL) const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]  
  
##  <a name="findindex"></a>  CObList::FindIndex  
 Używa wartości *nIndex* jako indeks w liście.  
  
```  
POSITION FindIndex(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczony od zera indeks elementu listy do znalezienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do iteracji lub pobieranie wskaźnika obiektu; **NULL** Jeśli *nIndex* jest zbyt duży. (Platformę generuje potwierdzenia, jeśli *nIndex* jest ujemna.)  
  
### <a name="remarks"></a>Uwagi  
 Rozpoczyna się kolejny skanowania z węzła głównego listy zatrzymywanie na *n*th element.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::FindIndex`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**FindIndex pozycji (INT_PTR** `nIndex` **) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**FindIndex pozycji (INT_PTR** `nIndex` **) const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]  
  
##  <a name="getat"></a>  CObList::GetAt  
 Zmienna typu **pozycji** jest kluczem dla listy.  
  
```  
CObject*& GetAt(POSITION position);  
const CObject*& GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Stanowisko*  
 A **pozycji** wartość zwrócona przez poprzednie `GetHeadPosition` lub `Find` wywołanie funkcji Członkowskich.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz opis wartości zwracanej [GetHead](#gethead).  
  
### <a name="remarks"></a>Uwagi  
 Nie jest taka sama jak indeksu i nie może działać na **pozycji** wartość samodzielnie. `GetAt` pobiera `CObject` wskaźnika skojarzone z określonej pozycji.  
  
 Upewnij się, że Twoje **pozycji** wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetAt`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const void\*& GetAt (pozycja** *pozycji* **) const;**<br /><br /> **void\*& GetAt (pozycja** *pozycji* **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**cstring — stała & GetAt (pozycja** *pozycji* **) const;**<br /><br /> **Cstring — & GetAt (pozycja** *pozycji* **);**|  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [FindIndex](#findindex).  
  
##  <a name="getcount"></a>  CObList::GetCount  
 Pobiera liczbę elementów na tej liście.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość całkowita zawierająca element count.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetCount`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount () const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount () const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]  
  
##  <a name="gethead"></a>  CObList::GetHead  
 Pobiera `CObject` wskaźnika, który reprezentuje element head tej listy.  
  
```  
CObject*& GetHead();  
const CObject*& GetHead() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest dostępna za pośrednictwem wskaźnik do **const CObList**, następnie `GetHead` zwraca `CObject` wskaźnika. Dzięki temu funkcja ma być używany tylko po prawej stronie instrukcji przypisania, a w związku z tym chroni przed modyfikacją listy.  
  
 Jeśli lista jest dostępny bezpośrednio lub za pomocą wskaźnika `CObList`, następnie `GetHead` zwraca odwołanie do `CObject` wskaźnika. Umożliwia funkcji można używać po obu stronach instrukcji przypisania i w związku z tym umożliwia pozycji na liście do zmodyfikowania.  
  
### <a name="remarks"></a>Uwagi  
 Musi upewnij się, że listy nie jest pusty przed wywołaniem `GetHead`. Jeśli lista jest pusta, wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetHead`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const void\*& () GetHead const; void\*& GetHead ();**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Stała obiektu CString & GetHead () const; Cstring — & GetHead ();**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 Poniższy przykład przedstawia użycie `GetHead` po lewej stronie instrukcji przypisania.  
  
 [!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]  
  
##  <a name="getheadposition"></a>  CObList::GetHeadPosition  
 Pobiera położenie elementu head tej listy.  
  
```  
POSITION GetHeadPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do iteracji lub pobieranie wskaźnika obiektu; **NULL** Jeśli lista jest pusta.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetHeadPosition`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja GetHeadPosition () const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozycja GetHeadPosition () const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]  
  
##  <a name="getnext"></a>  CObList::GetNext  
 Pobiera element listy identyfikowane przez *rPosition*, następnie ustawia *rPosition* do `POSITION` wartości następnego wpisu na liście.  
  
```  
CObject*& GetNext(POSITION& rPosition);  
const CObject* GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *rPosition*  
 Odwołanie do `POSITION` wartość zwrócona przez poprzednie `GetNext`, `GetHeadPosition`, lub inne wywołanie funkcji Członkowskich.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz opis wartości zwracanej [GetHead](#gethead).  
  
### <a name="remarks"></a>Uwagi  
 Można użyć `GetNext` w pętli do przodu iteracji, jeśli ustanowić położenie początkowe w wyniku wywołania `GetHeadPosition` lub `Find`.  
  
 Upewnij się, że Twoje `POSITION` wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
 Jeśli element pobrane przez ostatnie na liście jest następnie nowa wartość *rPosition* ma ustawioną wartość `NULL`.  
  
 Istnieje możliwość usunięcia elementu podczas iteracji. Zobacz przykład [Element RemoveAt](#removeat).  
  
> [!NOTE]
>  Począwszy od MFC 8.0 const wersji tej metody został zmieniony do zwrócenia `const CObject*` zamiast `const CObject*&`.  Ta zmiana została wprowadzona do zapewnienia zgodności z C++ standard kompilatora.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetNext`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `a CAge at $479C 40`  
  
 `a CAge at $46C0 21`  
  
##  <a name="getprev"></a>  CObList::GetPrev  
 Pobiera element listy identyfikowane przez *rPosition*, następnie ustawia *rPosition* do `POSITION` wartość poprzedniej pozycji listy.  
  
```  
CObject*& GetPrev(POSITION& rPosition);  
const CObject* GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *rPosition*  
 Odwołanie do `POSITION` wartość zwrócona przez poprzednie `GetPrev` lub inne wywołanie funkcji Członkowskich.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz opis wartości zwracanej [GetHead](#gethead).  
  
### <a name="remarks"></a>Uwagi  
 Można użyć `GetPrev` w odwrotnej iteracji pętli po nawiązaniu położenie początkowe w wyniku wywołania `GetTailPosition` lub `Find`.  
  
 Upewnij się, że Twoje `POSITION` wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
 Jeśli element pobrane pierwszy na liście jest następnie nowa wartość `rPosition` ma ustawioną wartość `NULL`.  
  
> [!NOTE]
>  Począwszy od MFC 8.0 const wersji tej metody został zmieniony do zwrócenia `const CObject*` zamiast `const CObject*&`.  Ta zmiana została wprowadzona do zapewnienia zgodności z C++ standard kompilatora.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetPrev`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `a CAge at $421C 21`  
  
 `a CAge at $421C 40`  
  
##  <a name="getsize"></a>  CObList::GetSize  
 Zwraca liczbę elementów listy.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów na liście.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby pobrać liczbę elementów na liście.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetSize`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize () const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize () const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]  
  
##  <a name="gettail"></a>  CObList::GetTail  
 Pobiera `CObject` wskaźnik, który reprezentuje element tail tej listy.  
  
```  
CObject*& GetTail();  
const CObject*& GetTail() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz opis wartości zwracanej [GetHead](#gethead).  
  
### <a name="remarks"></a>Uwagi  
 Musi upewnij się, że listy nie jest pusty przed wywołaniem `GetTail`. Jeśli lista jest pusta, wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetTail`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const void\*& () GetTail const; void\*& GetTail ();**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Stała obiektu CString & GetTail () const; Cstring — & GetTail ();**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]  
  
##  <a name="gettailposition"></a>  CObList::GetTailPosition  
 Pobiera położenie elementu tail tej listy; **NULL** Jeśli lista jest pusta.  
  
```  
POSITION GetTailPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do iteracji lub pobieranie wskaźnika obiektu; **NULL** Jeśli lista jest pusta.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetTailPosition`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja GetTailPosition () const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozycja GetTailPosition () const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]  
  
##  <a name="insertafter"></a>  CObList::InsertAfter  
 Dodaje element do tej listy po elemencie w określonej pozycji.  
  
```  
POSITION InsertAfter(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *Stanowisko*  
 A **pozycji** wartość zwrócona przez poprzednie `GetNext`, `GetPrev`, lub `Find` wywołanie funkcji Członkowskich.  
  
 `newElement`  
 Wskaźnik obiektu ma zostać dodany do tej listy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::InsertAfter`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja InsertAfter (pozycja** *pozycji* **, void\***  `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozycja InsertAfter (pozycja** *pozycji* **, const cstring — &** `newElement` **);**<br /><br /> **Pozycja InsertAfter (pozycja** *pozycji* **, LPCTSTR** `newElement` **);**|  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która jest taka sama jak *pozycji* parametru.  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `InsertAfter example: A CObList with 3 elements`  
  
 `a CAge at $4A44 40`  
  
 `a CAge at $4A64 65`  
  
 `a CAge at $4968 21`  
  
##  <a name="insertbefore"></a>  CObList::InsertBefore  
 Dodaje element do tej listy przed elementem w określonej pozycji.  
  
```  
POSITION InsertBefore(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *Stanowisko*  
 A **pozycji** wartość zwrócona przez poprzednie `GetNext`, `GetPrev`, lub `Find` wywołanie funkcji Członkowskich.  
  
 *newElement*  
 Wskaźnik obiektu ma zostać dodany do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do iteracji lub pobieranie wskaźnika obiektu; **NULL** Jeśli lista jest pusta.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::InsertBefore`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja InsertBefore (pozycja** *pozycji* **, void\***  `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozycja InsertBefore (pozycja** *pozycji* **, const cstring — &** `newElement` **);**<br /><br /> **Pozycja InsertBefore (pozycja** *pozycji* **, LPCTSTR** `newElement` **);**|  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `InsertBefore example: A CObList with 3 elements`  
  
 `a CAge at $4AE2 40`  
  
 `a CAge at $4B02 65`  
  
 `a CAge at $49E6 21`  
  
##  <a name="isempty"></a>  CObList::IsEmpty  
 Wskazuje, czy ta lista nie zawiera żadnych elementów.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ta lista jest pusta. w przeciwnym razie 0.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::IsEmpty`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Wartość logiczna IsEmpty () const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Wartość logiczna IsEmpty () const;**|  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [RemoveAll](#removeall).  
  
##  <a name="removeall"></a>  CObList::RemoveAll  
 Usuwa wszystkie elementy z tej listy i zwalnia skojarzony `CObList` pamięci.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Nie zostanie wygenerowany błąd, jeśli lista jest pusta.  
  
 Usunięcie elementów z `CObList`, Usuń wskaźniki obiekt z listy. Jest obowiązek usunąć same obiekty.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::RemoveAll`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll( );**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll( );**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]  
  
##  <a name="removeat"></a>  CObList::RemoveAt  
 Usuwa określony element z tej listy.  
  
```  
void RemoveAt(POSITION position);
```  
  
### <a name="parameters"></a>Parametry  
 *Stanowisko*  
 Położenie elementu do usunięcia z listy.  
  
### <a name="remarks"></a>Uwagi  
 Po usunięciu elementu `CObList`, Usuń wskaźnik do obiektu z listy. Jest obowiązek usunąć same obiekty.  
  
 Upewnij się, że Twoje **pozycji** wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::RemoveAt`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Element RemoveAt void (pozycja** *pozycji* **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Element RemoveAt void (pozycja** *pozycji* **);**|  
  
### <a name="example"></a>Przykład  
  Należy zachować ostrożność podczas usuwania elementu podczas iteracji listy. W poniższym przykładzie przedstawiono metody usuwania, która zapewnia prawidłową **pozycji** wartość [GetNext](#getnext).  
  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `RemoveAt example: A CObList with 2 elements`  
  
 `a CAge at $4C1E 65`  
  
 `a CAge at $4B22 21`  
  
##  <a name="removehead"></a>  CObList::RemoveHead  
 Usuwa element z węzła głównego z listy i zwraca wskaźnik do niego.  
  
```  
CObject* RemoveHead();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `CObject` Wskaźnika wcześniej w head listy.  
  
### <a name="remarks"></a>Uwagi  
 Musi upewnij się, że listy nie jest pusty przed wywołaniem `RemoveHead`. Jeśli lista jest pusta, wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::RemoveHead`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead ();**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Cstring — RemoveHead ();**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]  
  
##  <a name="removetail"></a>  CObList::RemoveTail  
 Usuwa element z tail listy i zwraca wskaźnik do niego.  
  
```  
CObject* RemoveTail();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do obiektu, który został na końcu listy.  
  
### <a name="remarks"></a>Uwagi  
 Musi upewnij się, że listy nie jest pusty przed wywołaniem `RemoveTail`. Jeśli lista jest pusta, wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::RemoveTail`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail ();**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Cstring — RemoveTail ();**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]  
  
##  <a name="setat"></a>  CObList::SetAt  
 Ustawia element na określonej pozycji.  
  
```  
void SetAt(
    POSITION pos,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 **Pozycji** można ustawić elementu.  
  
 *newElement*  
 `CObject` Wskaźnik do zapisania do listy.  
  
### <a name="remarks"></a>Uwagi  
 Zmienna typu **pozycji** jest kluczem dla listy. Nie jest taka sama jak indeksu i nie może działać na **pozycji** wartość samodzielnie. `SetAt` zapisuje `CObject` wskaźnik do określonej pozycji na liście.  
  
 Upewnij się, że Twoje **pozycji** wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::SetAt`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt (pozycja** `pos` **, const cstring — &** `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt (pozycja** `pos` **, LPCTSTR** `newElement` **);**|  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `SetAt example: A CObList with 2 elements`  
  
 `a CAge at $4D98 40`  
  
 `a CAge at $4DB8 65`  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CStringList](../../mfc/reference/cstringlist-class.md)   
 [Klasa CPtrList](../../mfc/reference/cptrlist-class.md)
