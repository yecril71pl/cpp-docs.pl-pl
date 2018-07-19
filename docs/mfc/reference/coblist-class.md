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
ms.openlocfilehash: 6f816e4fd83439b528e6f2ab92212c763d769bed
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853059"
---
# <a name="coblist-class"></a>Klasa cObList
fSupports uporządkowane listy nieunikatowy `CObject` wskaźników dostępnych sekwencyjnie lub według wskaźnika wartości.  
  
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
|[CObList::AddHead](#addhead)|Dodaje nagłówek listy (sprawia, że nowy główny) elementu (lub wszystkie elementy w innej listy).|  
|[CObList::AddTail](#addtail)|Dodaje ogona listy (sprawia, że nowe tail) elementu (lub wszystkie elementy w innej listy).|  
|[CObList::Find](#find)|Pobiera położenie elementu określonego przez wartość wskaźnika.|  
|[CObList::FindIndex](#findindex)|Pobiera położenie elementu, który został określony przez indeks zaczynający się od zera.|  
|[CObList::GetAt](#getat)|Pobiera element na określonej pozycji.|  
|[CObList::GetCount](#getcount)|Zwraca liczbę elementów na tej liście.|  
|[CObList::GetHead](#gethead)|Zwraca element główny listy (nie może być pusta).|  
|[CObList::GetHeadPosition](#getheadposition)|Zwraca pozycję głównego elementu listy.|  
|[CObList::GetNext](#getnext)|Pobiera następny element do wykonania iteracji.|  
|[CObList::GetPrev](#getprev)|Pobiera poprzedni element do wykonania iteracji.|  
|[CObList::GetSize](#getsize)|Zwraca liczbę elementów na tej liście.|  
|[CObList::GetTail](#gettail)|Zwraca element tail listy (nie może być pusta).|  
|[CObList::GetTailPosition](#gettailposition)|Zwraca położenie elementu tail listy.|  
|[CObList::InsertAfter](#insertafter)|Wstawia nowy element po określonej pozycji.|  
|[CObList::InsertBefore](#insertbefore)|Wstawia nowy element przed określonej pozycji.|  
|[CObList::IsEmpty](#isempty)|Testuje pod kątem warunku lista jest pusta (Brak elementów).|  
|[CObList::RemoveAll](#removeall)|Usuwa wszystkie elementy z tej listy.|  
|[CObList::RemoveAt](#removeat)|Usuwa element z tej listy, który jest określony za pomocą pozycji.|  
|[CObList::RemoveHead](#removehead)|Usuwa element z głowy listy.|  
|[CObList::RemoveTail](#removetail)|Usuwa element z zakończeniem listy.|  
|[CObList::SetAt](#setat)|Ustawia element na określonej pozycji.|  
  
## <a name="remarks"></a>Uwagi  
 `CObList` Wyświetla zachowują się jak podwójnie połączonej listy.  
  
 Zmienna typu pozycja jest kluczem dla listy. Zarówno jako iterator przechodzić sekwencyjnie przez listę i jako zakładki do przechowywania w miejscu, można użyć zmiennej pozycji. Pozycja nie jest taka sama jak indeksu, jednak.  
  
 Wstawianie elementu jest bardzo szybkie na czele listy w ogon i pozycja znane. Sekwencyjne wyszukiwania jest niezbędne do wyszukiwania według wartości lub indeks elementu. To wyszukiwanie może działać powoli, jeśli lista jest długa.  
  
 `CObList` dołącza IMPLEMENT_SERIAL — makro do obsługi serializacji i zrzucanie z jego elementów. Jeśli lista `CObject` wskaźniki są przechowywane do archiwum, za pomocą operatora przeciążona wstawiania lub za pomocą `Serialize` funkcję członkowską, każdy `CObject` element jest serializowana z osobna.  
  
 Jeśli potrzebujesz zrzutu indywidualnego `CObject` elementów na liście, należy ustawić głębokość kontekstu zrzutu 1 lub większą.  
  
 Gdy `CObList` obiekt zostanie usunięty lub gdy jego elementy są usuwane, tylko `CObject` wskaźniki są usuwane i obiekty nie mogą odwoływać się.  
  
 Uzyskujesz własnych klas z `CObList`. Nowej klasie listy, przeznaczone do przechowywania wskaźników do obiektów pochodzących od `CObject`, dodaje nowe elementy członkowskie danych i nowe funkcje Członkowskie. Należy pamiętać, że wynikowa lista nie ściśle bezpiecznych, ponieważ zezwala ona na dowolne operacje wstawiania `CObject` wskaźnika.  
  
> [!NOTE]
>  Należy użyć [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) makra w realizacji swojej otrzymanej klasy, aby przeprowadzić serializacji na liście.  
  
 Aby uzyskać więcej informacji na temat korzystania z `CObList`, zapoznaj się z artykułem [kolekcje](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcoll.h  
  
##  <a name="addhead"></a>  CObList::AddHead  
 Dodaje nowy element lub Podaj listę elementów do głowy tej listy.  
  
```  
POSITION AddHead(CObject* newElement);  
void AddHead(CObList* pNewList);
```  
  
### <a name="parameters"></a>Parametry  
 *newElement*  
 `CObject` Wskaźnika, które mają zostać dodane do tej listy.  
  
 *pNewList*  
 Wskaźnik do innego `CObList` listy. Elementy w *pNewList* zostaną dodane do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwsza wersja zwraca wartość pozycji nowo wstawionego elementu.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::AddHead`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja AddHead (void\***  `newElement` **);**<br /><br /> **void AddHead (CPtrList\***  `pNewList` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozycja AddHead (const CString &** `newElement` **);**<br /><br /> **Pozycja AddHead (LPCTSTR** `newElement` **);**<br /><br /> **void AddHead (CStringList\***  `pNewList` **);**|  
  
### <a name="remarks"></a>Uwagi  
 Lista może być pusta, przed wykonaniem operacji.  
  
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
 `CObject` Wskaźnika, które mają zostać dodane do tej listy.  
  
 *pNewList*  
 Wskaźnik do innego `CObList` listy. Elementy w *pNewList* zostaną dodane do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwsza wersja zwraca wartość pozycji nowo wstawionego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Lista może być pusta, przed wykonaniem operacji.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::AddTail`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Addtail — pozycja (void\***  `newElement` **);**<br /><br /> **addtail — void (CPtrList\***  `pNewList` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Addtail — pozycja (const CString &** `newElement` **);**<br /><br /> **Addtail — pozycja (LPCTSTR** `newElement` **);**<br /><br /> **addtail — void (CStringList\***  `pNewList` **);**|  
  
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
 Alokacja pamięci poziom szczegółowości Rozszerzanie listy.  
  
### <a name="remarks"></a>Uwagi  
 Wraz z rozwojem listy pamięć została przydzielona w jednostkach *nBlockSize* wpisów. Jeśli alokacja pamięci nie powiedzie się, `CMemoryException` zgłaszany.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::CObList`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **= 10);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **= 10);**|  
  
### <a name="example"></a>Przykład  
  Poniżej znajduje się lista `CObject`-klasy pochodnej `CAge` używane we wszystkich przykładach kolekcji:  
  
 [!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]  
  
 Poniżej znajduje się przykład `CObList` Konstruktor użycia:  
  
 [!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]  
  
##  <a name="find"></a>  CObList::Find  
 Przeszukuje listę po kolei, aby znaleźć pierwszy `CObject` wskaźnik dopasowania określonej `CObject` wskaźnika.  
  
```  
POSITION Find(
    CObject* searchValue,  
    POSITION startAfter = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Wyszukiwana_wartość*  
 Wskaźnik obiektu ma zostać odnaleziona na tej liście.  
  
 *startAfter*  
 Pozycja początkowa wyszukiwania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, która może służyć do iteracji lub pobieranie wskaźnika obiektu; Wartość NULL, jeśli nie można odnaleźć obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że są porównywane wartości wskaźnika, nie zawartość obiektów.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::Find`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Znajdź pozycję (void\***  `searchValue` **, pozycja** `startAfter` **= NULL) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Znajdź pozycję (LPCTSTR** `searchValue` **, pozycja** `startAfter` **= NULL) const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]  
  
##  <a name="findindex"></a>  CObList::FindIndex  
 Używa wartości *nIndex* jako indeks do listy.  
  
```  
POSITION FindIndex(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczony od zera indeks elementu listy, które ma zostać odnaleziona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, która może służyć do iteracji lub pobieranie wskaźnika obiektu; Wartość NULL, jeśli *nIndex* jest zbyt duży. (Struktura generuje potwierdzenie, jeśli *nIndex* jest ujemna.)  
  
### <a name="remarks"></a>Uwagi  
 Uruchamia kolejne skanowania od czoła listy zatrzymywanie na *n*th element.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::FindIndex`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Findindex — pozycja (INT_PTR** `nIndex` **) const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Findindex — pozycja (INT_PTR** `nIndex` **) const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]  
  
##  <a name="getat"></a>  CObList::GetAt  
 Zmienna typu pozycja jest kluczem dla listy.  
  
```  
CObject*& GetAt(POSITION position);  
const CObject*& GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Stanowisko*  
 Wartość pozycji zwrócony przez poprzednie `GetHeadPosition` lub `Find` wywołanie funkcji elementu członkowskiego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz opis wartości zwracanej [GetHead](#gethead).  
  
### <a name="remarks"></a>Uwagi  
 Nie jest taka sama jak indeksu, a użytkownik nie może działać na wartość pozycji samodzielnie. `GetAt` pobiera `CObject` kursor skojarzony z określonej pozycji.  
  
 Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetAt`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Stała wartość void\*& GetAt (pozycja** *pozycji* **) const;**<br /><br /> **void\*& GetAt (pozycja** *pozycji* **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**cstring — Const & GetAt (pozycja** *pozycji* **) const;**<br /><br /> **Cstring — & GetAt (pozycja** *pozycji* **);**|  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [findindex —](#findindex).  
  
##  <a name="getcount"></a>  CObList::GetCount  
 Pobiera liczbę elementów na tej liście.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Całkowitą zawierającą liczbę elementów.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetCount`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount () const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount () const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]  
  
##  <a name="gethead"></a>  CObList::GetHead  
 Pobiera `CObject` wskaźnika, który reprezentuje główny element tej listy.  
  
```  
CObject*& GetHead();  
const CObject*& GetHead() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli lista jest dostępna za pośrednictwem wskaźnik do `const CObList`, następnie `GetHead` zwraca `CObject` wskaźnika. Umożliwia korzystanie z funkcji ma być używany tylko po prawej stronie instrukcji przypisania, a zatem chroni listy przed modyfikacją.  
  
 Jeśli lista jest dostępny bezpośrednio lub za pomocą wskaźnika do `CObList`, następnie `GetHead` zwraca odwołanie do `CObject` wskaźnika. Umożliwia korzystanie z funkcji ma być używany po obu stronach instrukcji przypisania, a zatem umożliwia pozycji listy do zmodyfikowania.  
  
### <a name="remarks"></a>Uwagi  
 Należy upewnić się, lista nie jest pusta, przed wywołaniem `GetHead`. Jeśli lista jest pusta, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetHead`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Stała wartość void\*& () GetHead const; void\*& GetHead ();**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Const CString & GetHead () const; Cstring — & GetHead ();**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 Poniższy przykład ilustruje użycie `GetHead` po lewej stronie instrukcji przypisania.  
  
 [!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]  
  
##  <a name="getheadposition"></a>  CObList::GetHeadPosition  
 Pobiera położenie elementu głównego tej listy.  
  
```  
POSITION GetHeadPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, która może służyć do iteracji lub pobieranie wskaźnika obiektu; Wartość NULL, jeśli lista jest pusta.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetHeadPosition`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja GetHeadPosition () const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozycja GetHeadPosition () const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]  
  
##  <a name="getnext"></a>  CObList::GetNext  
 Pobiera element listy identyfikowane przez *elemencie rPosition*, następnie ustawia *elemencie rPosition* do `POSITION` wartość następnego wpisu na liście.  
  
```  
CObject*& GetNext(POSITION& rPosition);  
const CObject* GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *elemencie rPosition*  
 Odwołanie do wartości pozycji, zwrócony przez poprzednie `GetNext`, `GetHeadPosition`, lub inne wywołanie funkcji elementu członkowskiego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz opis wartości zwracanej [GetHead](#gethead).  
  
### <a name="remarks"></a>Uwagi  
 Możesz użyć `GetNext` w pętli do przodu iteracji, jeśli ustanowisz początkowe położenie w wyniku wywołania `GetHeadPosition` lub `Find`.  
  
 Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.  
  
 Jeśli element pobrane ostatnio na liście jest następnie nowa wartość *elemencie rPosition* ma wartość NULL.  
  
 Istnieje możliwość usunięcia elementu podczas iteracji. Zobacz przykład [Element RemoveAt](#removeat).  
  
> [!NOTE]
>  Począwszy od MFC 8.0 const wersji tej metody został zmieniony do zwrócenia `const CObject*` zamiast `const CObject*&`.  Ta zmiana została wprowadzona w celu dostosowania kompilator do zgodności ze standardem C++.  
  
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
 Pobiera element listy identyfikowane przez *elemencie rPosition*, następnie ustawia *elemencie rPosition* wartość pozycji poprzedni wpis na liście.  
  
```  
CObject*& GetPrev(POSITION& rPosition);  
const CObject* GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *elemencie rPosition*  
 Odwołanie do wartości pozycji, zwrócony przez poprzednie `GetPrev` lub inne wywołanie funkcji elementu członkowskiego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz opis wartości zwracanej [GetHead](#gethead).  
  
### <a name="remarks"></a>Uwagi  
 Możesz użyć `GetPrev` w iteracji odwrotnej pętli, jeśli ustanowisz początkowe położenie w wyniku wywołania `GetTailPosition` lub `Find`.  
  
 Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.  
  
 Jeśli element pobrane jest pierwsze na liście, nowa wartość *elemencie rPosition* ma wartość NULL.  
  
> [!NOTE]
>  Począwszy od MFC 8.0 const wersji tej metody został zmieniony do zwrócenia `const CObject*` zamiast `const CObject*&`.  Ta zmiana została wprowadzona w celu dostosowania kompilator do zgodności ze standardem C++.  
  
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
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR getsize — () const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR getsize — () const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]  
  
##  <a name="gettail"></a>  CObList::GetTail  
 Pobiera `CObject` wskaźnika, który reprezentuje element tail tej listy.  
  
```  
CObject*& GetTail();  
const CObject*& GetTail() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz opis wartości zwracanej [GetHead](#gethead).  
  
### <a name="remarks"></a>Uwagi  
 Należy upewnić się, lista nie jest pusta, przed wywołaniem `GetTail`. Jeśli lista jest pusta, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetTail`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Stała wartość void\*& () GetTail const; void\*& GetTail ();**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Const CString & GetTail () const; Cstring — & GetTail ();**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]  
  
##  <a name="gettailposition"></a>  CObList::GetTailPosition  
 Pobiera położenie elementu tail tej listy; **NULL** Jeśli lista jest pusta.  
  
```  
POSITION GetTailPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, która może służyć do iteracji lub pobieranie wskaźnika obiektu; Wartość NULL, jeśli lista jest pusta.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::GetTailPosition`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja GetTailPosition () const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozycja GetTailPosition () const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]  
  
##  <a name="insertafter"></a>  CObList::InsertAfter  
 Dodaje element do tej listy, po elemencie w określonej pozycji.  
  
```  
POSITION InsertAfter(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *Stanowisko*  
 Wartość pozycji zwrócony przez poprzednie `GetNext`, `GetPrev`, lub `Find` wywołanie funkcji elementu członkowskiego.  
  
 *newElement*  
 Wskaźnik obiektu, który ma zostać dodany do tej listy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::InsertAfter`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja InsertAfter (pozycja** *pozycji* **, void\***  `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozycja InsertAfter (pozycja** *pozycji* **, const CString &** `newElement` **);**<br /><br /> **Pozycja InsertAfter (pozycja** *pozycji* **, LPCTSTR** `newElement` **);**|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, która jest taka sama jak *pozycji* parametru.  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `InsertAfter example: A CObList with 3 elements`  
  
 `a CAge at $4A44 40`  
  
 `a CAge at $4A64 65`  
  
 `a CAge at $4968 21`  
  
##  <a name="insertbefore"></a>  CObList::InsertBefore  
 Dodaje element do tej listy, przed elementem w określonej pozycji.  
  
```  
POSITION InsertBefore(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *Stanowisko*  
 Wartość pozycji zwrócony przez poprzednie `GetNext`, `GetPrev`, lub `Find` wywołanie funkcji elementu członkowskiego.  
  
 *newElement*  
 Wskaźnik obiektu, który ma zostać dodany do tej listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, która może służyć do iteracji lub pobieranie wskaźnika obiektu; Wartość NULL, jeśli lista jest pusta.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::InsertBefore`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Pozycja InsertBefore (pozycja** *pozycji* **, void\***  `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Pozycja InsertBefore (pozycja** *pozycji* **, const CString &** `newElement` **);**<br /><br /> **Pozycja InsertBefore (pozycja** *pozycji* **, LPCTSTR** `newElement` **);**|  
  
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
 Wartość różną od zera, jeśli ta lista jest pusta. w przeciwnym razie 0.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::IsEmpty`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Wartość logiczna IsEmpty () const;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Wartość logiczna IsEmpty () const;**|  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [RemoveAll](#removeall).  
  
##  <a name="removeall"></a>  CObList::RemoveAll  
 Usuwa wszystkie elementy z tej listy i zwalnia skojarzonego `CObList` pamięci.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Błąd nie jest generowany, gdy lista jest pusty.  
  
 Po usunięciu elementów z `CObList`, Usuń wskaźniki obiektu z listy. Jest odpowiedzialny za Usuń same obiekty.  
  
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
 Po usunięciu elementu z `CObList`, Usuń wskaźnik do obiektu z listy. Jest odpowiedzialny za Usuń same obiekty.  
  
 Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::RemoveAt`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Unieważnij Element RemoveAt (pozycja** *pozycji* **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Unieważnij Element RemoveAt (pozycja** *pozycji* **);**|  
  
### <a name="example"></a>Przykład  
  Należy zachować ostrożność podczas usuwania elementu podczas iteracji listy. W poniższym przykładzie pokazano metody usuwania, która gwarantuje prawidłowy **pozycji** wartość [GetNext](#getnext).  
  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `RemoveAt example: A CObList with 2 elements`  
  
 `a CAge at $4C1E 65`  
  
 `a CAge at $4B22 21`  
  
##  <a name="removehead"></a>  CObList::RemoveHead  
 Usuwa element z głowy listy, a następnie zwraca wskaźnik do niego.  
  
```  
CObject* RemoveHead();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `CObject` Wskaźnika wcześniej na czele listy.  
  
### <a name="remarks"></a>Uwagi  
 Należy upewnić się, lista nie jest pusta, przed wywołaniem `RemoveHead`. Jeśli lista jest pusta, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::RemoveHead`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead ();**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Cstring — RemoveHead ();**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]  
  
##  <a name="removetail"></a>  CObList::RemoveTail  
 Usuwa element z zakończeniem listy, a następnie zwraca wskaźnik do niego.  
  
```  
CObject* RemoveTail();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do obiektu, który został na końcu listy.  
  
### <a name="remarks"></a>Uwagi  
 Należy upewnić się, lista nie jest pusta, przed wywołaniem `RemoveTail`. Jeśli lista jest pusta, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation. Użyj [IsEmpty](#isempty) Aby sprawdzić, czy lista zawiera elementy.  
  
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
 *punktu sprzedaży*  
 POŁOŻENIE elementu do ustawienia.  
  
 *newElement*  
 `CObject` Wskaźnik do zapisania na liście.  
  
### <a name="remarks"></a>Uwagi  
 Zmienna typu pozycja jest kluczem dla listy. Nie jest taka sama jak indeksu, a użytkownik nie może działać na wartość pozycji samodzielnie. `SetAt` zapisuje `CObject` wskaźnik do określonej pozycji na liście.  
  
 Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObList::SetAt`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt (pozycja** `pos` **, const CString &** `newElement` **);**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt (pozycja** `pos` **, LPCTSTR** `newElement` **);**|  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](#coblist) listę `CAge` klasy.  
  
 [!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `SetAt example: A CObList with 2 elements`  
  
 `a CAge at $4D98 40`  
  
 `a CAge at $4DB8 65`  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CObject](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CStringList](../../mfc/reference/cstringlist-class.md)   
 [Klasa CPtrList](../../mfc/reference/cptrlist-class.md)
