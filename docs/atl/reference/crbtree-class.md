---
title: Klasa CRBTree | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRBTree
- ATLCOLL/ATL::CRBTree
- ATLCOLL/ATL::CRBTree::KINARGTYPE
- ATLCOLL/ATL::CRBTree::KOUTARGTYPE
- ATLCOLL/ATL::CRBTree::VINARGTYPE
- ATLCOLL/ATL::CRBTree::VOUTARGTYPE
- ATLCOLL/ATL::CRBTree::FindFirstKeyAfter
- ATLCOLL/ATL::CRBTree::GetAt
- ATLCOLL/ATL::CRBTree::GetCount
- ATLCOLL/ATL::CRBTree::GetHeadPosition
- ATLCOLL/ATL::CRBTree::GetKeyAt
- ATLCOLL/ATL::CRBTree::GetNext
- ATLCOLL/ATL::CRBTree::GetNextAssoc
- ATLCOLL/ATL::CRBTree::GetNextKey
- ATLCOLL/ATL::CRBTree::GetNextValue
- ATLCOLL/ATL::CRBTree::GetPrev
- ATLCOLL/ATL::CRBTree::GetTailPosition
- ATLCOLL/ATL::CRBTree::GetValueAt
- ATLCOLL/ATL::CRBTree::IsEmpty
- ATLCOLL/ATL::CRBTree::RemoveAll
- ATLCOLL/ATL::CRBTree::RemoveAt
- ATLCOLL/ATL::CRBTree::SetValueAt
dev_langs: C++
helpviewer_keywords: CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f9014233631eda9d1f3576382e71e377a3f7fcfd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crbtree-class"></a>Klasa CRBTree
Ta klasa dostarcza metody do tworzenia i przy użyciu drzewa czarne czerwony.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>> 
class CRBTree
```  
  
#### <a name="parameters"></a>Parametry  
 `K`  
 Typ klucza elementu.  
  
 *V*  
 Typ wartości elementu.  
  
 `KTraits`  
 Kod używany do skopiować lub przenieść kluczowe elementy. Zobacz [CElementTraits klasy](../../atl/reference/celementtraits-class.md) więcej szczegółów.  
  
 `VTraits`  
 Kod używany do skopiować lub przenieść elementy wartość.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRBTree::KINARGTYPE](#kinargtype)|Typ używany, gdy klucz jest przekazywany jako argument wejściowy.|  
|[CRBTree::KOUTARGTYPE](#koutargtype)|Typ używany, gdy klucz jest zwracany jako argument danych wyjściowych.|  
|[CRBTree::VINARGTYPE](#vinargtype)|Typ używany, gdy wartość jest przekazywany jako argument wejściowy.|  
|[CRBTree::VOUTARGTYPE](#voutargtype)|Typ używany, gdy wartość jest przekazywany jako argument danych wyjściowych.|  
  
### <a name="public-classes"></a>Klas publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Klasa CRBTree::CPair](#cpair_class)|Klasa zawierająca elementy klucz i wartość.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRBTree:: ~ CRBTree](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|Wywołanie tej metody do znalezienia położenie elementu, który korzysta z klucza dostępne dalej.|  
|[CRBTree::GetAt](#getat)|Wywołaj tę metodę, aby uzyskać elementu na określonej pozycji w drzewie.|  
|[CRBTree::GetCount](#getcount)|Wywołaj tę metodę, aby pobrać liczbę elementów w drzewie.|  
|[CRBTree::GetHeadPosition](#getheadposition)|Wywołanie tej metody można uzyskać wartość pozycji elementu nagłówek drzewa.|  
|[CRBTree::GetKeyAt](#getkeyat)|Wywołaj tę metodę, aby uzyskać klucz z określonej pozycji w drzewie.|  
|[CRBTree::GetNext](#getnext)|Wywołanie tej metody można uzyskać wskaźnika do elementu przechowywane w `CRBTree` obiektu i przejść do następnego elementu położenie.|  
|[CRBTree::GetNextAssoc](#getnextassoc)|Wywołanie tej metody można uzyskać klucz i wartość elementu przechowywane w planie i przejść do następnego elementu położenie.|  
|[CRBTree::GetNextKey](#getnextkey)|Wywołanie tej metody, aby pobrać klucz elementu przechowywanego w drzewie i przejść do następnego elementu położenie.|  
|[CRBTree::GetNextValue](#getnextvalue)|Wywołanie tej metody można uzyskać wartość elementu przechowywanego w drzewie i przejść do następnego elementu położenie.|  
|[CRBTree::GetPrev](#getprev)|Wywołanie tej metody można uzyskać wskaźnika do elementu przechowywane w `CRBTree` obiekt, a następnie zaktualizuj położenie do poprzedniego elementu.|  
|[CRBTree::GetTailPosition](#gettailposition)|Wywołanie tej metody można uzyskać wartość pozycji element na końcu drzewa.|  
|[CRBTree::GetValueAt](#getvalueat)|Wywołanie tej metody do pobierania wartości przechowywanych na określonej pozycji w `CRBTree` obiektu.|  
|[CRBTree::IsEmpty](#isempty)|Wywołanie tej metody do testowania dla obiekt pusty drzewa.|  
|[CRBTree::RemoveAll](#removeall)|Wywołanie tej metody, aby usunąć wszystkie elementy z **CRBTree** obiektu.|  
|[CRBTree::RemoveAt](#removeat)|Wywołanie tej metody, aby usunąć element na pozycji w **CRBTree** obiektu.|  
|[CRBTree::SetValueAt](#setvalueat)|Wywołanie tej metody, aby zmienić wartość przechowywana na określonej pozycji w `CRBTree` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Drzewo czarne czerwony jest drzewa wyszukiwanie binarne, który korzysta z dodatkową bit informacji w każdym węźle, aby upewnić się, że pozostaje "równoważenia," będący, wysokość drzewa nie wzrostu nieproporcjonalnie dużych i negatywnie wpłynąć na wydajność.  
  
 Ta klasa szablonu jest przeznaczona do użycia przez [CRBMap](../../atl/reference/crbmap-class.md) i [CRBMultiMap](../../atl/reference/crbmultimap-class.md). Zbiorczego metody wchodzące w skład tych klas pochodnych są dostarczane przez `CRBTree`.  
  
 Aby bardziej szczegółowe omówienie różnych klas kolekcji i ich funkcje i charakterystyki wydajności, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="cpair_class"></a>Klasa CRBTree::CPair  
 Klasa zawierająca elementy klucz i wartość.  
  
```
class CPair : public __POSITION
```  
  
### <a name="remarks"></a>Uwagi  
 Ta klasa jest używana przez metody [CRBTree::GetAt](#getat), [CRBTree::GetNext](#getnext), i [CRBTree::GetPrev](#getprev) do uzyskania dostępu do elementów kluczy i wartości przechowywane w strukturze drzewa.  
  
 Dostępne są następujące elementy:  
  
|||  
|-|-|  
|`m_key`|Element członkowski danych przechowywania klucza elementu.|  
|`m_value`|Element członkowski danych przechowywania element wartości.|  
  
##  <a name="dtor"></a>CRBTree:: ~ CRBTree  
 Destruktor.  
  
```
~CRBTree() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie zasoby przydzielone. Wywołania [CRBTree::RemoveAll](#removeall) można usunąć wszystkie elementy.  
  
##  <a name="findfirstkeyafter"></a>CRBTree::FindFirstKeyAfter  
 Wywołanie tej metody do znalezienia położenie elementu, który korzysta z klucza dostępne dalej.  
  
```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Wartość klucza.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość pozycji elementu, który używa klawisza następna dostępna. Jeśli nie ma więcej elementów, zwracana jest wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ułatwia przechodzenia drzewa bez konieczności wcześniejszego obliczania wartości pozycji.  
  
##  <a name="getat"></a>CRBTree::GetAt  
 Wywołaj tę metodę, aby uzyskać elementu na określonej pozycji w drzewie.  
  
```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Wartość pozycji.  
  
 `key`  
 Zmienna, która odbiera klucz.  
  
 *wartość*  
 Zmienna, która odbiera wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwsze dwa formularze zwraca wskaźnik do [CPair](#cpair_class). Trzeci formularza uzyskuje klucz oraz wartość dla podanego położenia.  
  
### <a name="remarks"></a>Uwagi  
 Wartość pozycji może być ustalona wcześniej przez wywołanie do metody takie jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::GetTailPosition](#gettailposition).  
  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli `pos` jest równa NULL.  
  
##  <a name="getcount"></a>CRBTree::GetCount  
 Wywołaj tę metodę, aby pobrać liczbę elementów w drzewie.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę elementów (każda para klucza i wartości jest jeden element) przechowywanego w drzewie.  
  
##  <a name="getheadposition"></a>CRBTree::GetHeadPosition  
 Wywołanie tej metody można uzyskać wartość pozycji elementu nagłówek drzewa.  
  
```
POSITION GetHeadPosition() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość pozycji elementu nagłówek drzewa.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez `GetHeadPosition` mogą być używane z metody takie jak [CRBTree::GetKeyAt](#getkeyat) lub [CRBTree::GetNext](#getnext) przechodzenia drzewa i pobierania wartości.  
  
##  <a name="getkeyat"></a>CRBTree::GetKeyAt  
 Wywołaj tę metodę, aby uzyskać klucz z określonej pozycji w drzewie.  
  
```
const K& GetKeyAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Wartość pozycji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca klucz przechowywany na pozycji `pos` w drzewie.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `pos` nie jest wartością prawidłową pozycją są nieprzewidywalne wyniki. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli `pos` jest równa NULL.  
  
##  <a name="getnext"></a>CRBTree::GetNext  
 Wywołanie tej metody można uzyskać wskaźnika do elementu przechowywane w `CRBTree` obiektu i przejść do następnego elementu położenie.  
  
```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji, takich jak zwrócony przez poprzednie wywołanie metody [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do następnego [CPair](#cpair_class) wartość w drzewie.  
  
### <a name="remarks"></a>Uwagi  
 `pos` Pozycji licznik jest aktualizowany po każdym wywołaniu. Jeśli element pobrane jest ostatnim w drzewie `pos` jest równa NULL.  
  
##  <a name="getnextassoc"></a>CRBTree::GetNextAssoc  
 Wywołanie tej metody można uzyskać klucz i wartość elementu przechowywane w planie i przejść do następnego elementu położenie.  
  
```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji, takich jak zwrócony przez poprzednie wywołanie metody [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
 `key`  
 Parametr szablonu określający typ klucza w drzewie.  
  
 *wartość*  
 Parametr szablonu określający typ wartości drzewa.  
  
### <a name="remarks"></a>Uwagi  
 `pos` Pozycji licznik jest aktualizowany po każdym wywołaniu. Jeśli element pobrane jest ostatnim w drzewie `pos` jest równa NULL.  
  
##  <a name="getnextkey"></a>CRBTree::GetNextKey  
 Wywołanie tej metody, aby pobrać klucz elementu przechowywanego w drzewie i przejść do następnego elementu położenie.  
  
```
const K& GetNextKey(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji, takich jak zwrócony przez poprzednie wywołanie metody [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do następnego klucza w drzewie.  
  
### <a name="remarks"></a>Uwagi  
 Aktualizuje licznik bieżącej pozycji `pos`. Jeśli nie ma żadnych więcej wpisów w drzewie, licznik pozycja jest ustawiony na wartość NULL.  
  
##  <a name="getnextvalue"></a>CRBTree::GetNextValue  
 Wywołanie tej metody można uzyskać wartość elementu przechowywanego w drzewie i przejść do następnego elementu położenie.  
  
```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji, takich jak zwrócony przez poprzednie wywołanie metody [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do najbliższej wartości w drzewie.  
  
### <a name="remarks"></a>Uwagi  
 Aktualizuje licznik bieżącej pozycji `pos`. Jeśli nie ma żadnych więcej wpisów w drzewie, licznik pozycja jest ustawiony na wartość NULL.  
  
##  <a name="getprev"></a>CRBTree::GetPrev  
 Wywołanie tej metody można uzyskać wskaźnika do elementu przechowywane w `CRBTree` obiekt, a następnie zaktualizuj położenie do poprzedniego elementu.  
  
```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji, takich jak zwrócony przez poprzednie wywołanie metody [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do poprzedniego [CPair](#cpair_class) wartości przechowywanej w drzewie.  
  
### <a name="remarks"></a>Uwagi  
 Aktualizuje licznik bieżącej pozycji `pos`. Jeśli nie ma żadnych więcej wpisów w drzewie, licznik pozycja jest ustawiony na wartość NULL.  
  
##  <a name="gettailposition"></a>CRBTree::GetTailPosition  
 Wywołanie tej metody można uzyskać wartość pozycji element na końcu drzewa.  
  
```
POSITION GetTailPosition() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość pozycji element na końcu drzewa.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez `GetTailPosition` mogą być używane z metody takie jak [CRBTree::GetKeyAt](#getkeyat) lub [CRBTree::GetPrev](#getprev) przechodzenia drzewa i pobierania wartości.  
  
##  <a name="getvalueat"></a>CRBTree::GetValueAt  
 Wywołanie tej metody do pobierania wartości przechowywanych na określonej pozycji w `CRBTree` obiektu.  
  
```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji, takich jak zwrócony przez poprzednie wywołanie metody [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do wartości przechowywanych na pozycji w `CRBTree` obiektu.  
  
##  <a name="isempty"></a>CRBTree::IsEmpty  
 Wywołanie tej metody do testowania dla obiekt pusty drzewa.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli drzewa jest pusta, **false** inaczej.  
  
##  <a name="kinargtype"></a>CRBTree::KINARGTYPE  
 Typ używany, gdy klucz jest przekazywany jako argument wejściowy.  
  
```
typedef KTraits::INARGTYPE KINARGTYPE;
```  
  
##  <a name="koutargtype"></a>CRBTree::KOUTARGTYPE  
 Typ używany, gdy klucz jest zwracany jako argument danych wyjściowych.  
  
```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```  
  
##  <a name="removeall"></a>CRBTree::RemoveAll  
 Wywołanie tej metody, aby usunąć wszystkie elementy z `CRBTree` obiektu.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Powoduje `CRBTree` obiektu zwolnić pamięć, używany do przechowywania elementów.  
  
##  <a name="removeat"></a>CRBTree::RemoveAt  
 Wywołanie tej metody, aby usunąć element na pozycji w **CRBTree** obiektu.  
  
```
void RemoveAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji, takich jak zwrócony przez poprzednie wywołanie metody [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="remarks"></a>Uwagi  
 Usuwa parę klucza i wartości przechowywane w określonej pozycji. Pamięć używana do przechowywania element zostanie zwolniona. Odwołuje się pozycja `pos` staje się nieprawidłowy, a gdy pozycja inne elementy w drzewie pozostaje ważny, niekoniecznie jak zachowanie tej samej kolejności.  
  
##  <a name="setvalueat"></a>CRBTree::SetValueAt  
 Wywołanie tej metody, aby zmienić wartość przechowywana na określonej pozycji w `CRBTree` obiektu.  
  
```
void SetValueAt(POSITION pos, VINARGTYPE value);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji, takich jak zwrócony przez poprzednie wywołanie metody [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
 *wartość*  
 Wartość do dodania do `CRBTree` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Zmienia element wartości przechowywane w danej pozycji w `CRBTree` obiektu.  
  
##  <a name="vinargtype"></a>CRBTree::VINARGTYPE  
 Typ używany, gdy wartość jest przekazywany jako argument wejściowy.  
  
```
typedef VTraits::INARGTYPE VINARGTYPE;
```  
  
##  <a name="voutargtype"></a>CRBTree::VOUTARGTYPE  
 Typ używany, gdy wartość jest przekazywany jako argument danych wyjściowych.  
  
```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
