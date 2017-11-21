---
title: Klasa CAtlMap | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlMap
- ATLCOLL/ATL::CAtlMap
- ATLCOLL/ATL::CAtlMap::KINARGTYPE
- ATLCOLL/ATL::CAtlMap::KOUTARGTYPE
- ATLCOLL/ATL::CAtlMap::VINARGTYPE
- ATLCOLL/ATL::CAtlMap::VOUTARGTYPE
- ATLCOLL/ATL::CPair::m_key
- ATLCOLL/ATL::CPair::m_value
- ATLCOLL/ATL::CAtlMap::CAtlMap
- ATLCOLL/ATL::CAtlMap::AssertValid
- ATLCOLL/ATL::CAtlMap::DisableAutoRehash
- ATLCOLL/ATL::CAtlMap::EnableAutoRehash
- ATLCOLL/ATL::CAtlMap::GetAt
- ATLCOLL/ATL::CAtlMap::GetCount
- ATLCOLL/ATL::CAtlMap::GetHashTableSize
- ATLCOLL/ATL::CAtlMap::GetKeyAt
- ATLCOLL/ATL::CAtlMap::GetNext
- ATLCOLL/ATL::CAtlMap::GetNextAssoc
- ATLCOLL/ATL::CAtlMap::GetNextKey
- ATLCOLL/ATL::CAtlMap::GetNextValue
- ATLCOLL/ATL::CAtlMap::GetStartPosition
- ATLCOLL/ATL::CAtlMap::GetValueAt
- ATLCOLL/ATL::CAtlMap::InitHashTable
- ATLCOLL/ATL::CAtlMap::IsEmpty
- ATLCOLL/ATL::CAtlMap::Lookup
- ATLCOLL/ATL::CAtlMap::Rehash
- ATLCOLL/ATL::CAtlMap::RemoveAll
- ATLCOLL/ATL::CAtlMap::RemoveAtPos
- ATLCOLL/ATL::CAtlMap::RemoveKey
- ATLCOLL/ATL::CAtlMap::SetAt
- ATLCOLL/ATL::CAtlMap::SetOptimalLoad
- ATLCOLL/ATL::CAtlMap::SetValueAt
dev_langs: C++
helpviewer_keywords: CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9d16ff30313a9346aa25f8febfba2f6e0d8307f1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="catlmap-class"></a>Klasa CAtlMap
Ta klasa dostarcza metody do tworzenia i zarządzania obiektu mapy.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>>
class CAtlMap
```  
  
#### <a name="parameters"></a>Parametry  
 `K`  
 Typ klucza elementu.  
  
 V  
 Typ wartości elementu.  
  
 `KTraits`  
 Kod używany do skopiować lub przenieść kluczowe elementy. Zobacz [CElementTraits klasy](../../atl/reference/celementtraits-class.md) więcej szczegółów.  
  
 `VTraits`  
 Kod używany do skopiować lub przenieść elementy wartość.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlMap::KINARGTYPE](#kinargtype)|Typ używany, gdy klucz jest przekazywany jako argument wejściowy|  
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Typ używany, gdy klucz jest zwracany jako argument danych wyjściowych.|  
|[CAtlMap::VINARGTYPE](#vinargtype)|Typ używany, gdy wartość jest przekazywany jako argument wejściowy.|  
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Typ używany, gdy wartość jest przekazywany jako argument danych wyjściowych.|  
  
### <a name="public-classes"></a>Klas publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Klasa CAtlMap::CPair](#cpair_class)|Klasa zawierająca elementy klucz i wartość.|  

  
### <a name="cpair-data-members"></a>Elementy członkowskie danych CPair  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPair::m_key](#m_key)|Element członkowski danych przechowywania klucza elementu.|  
|[CPair::m_value](#m_value)|Element członkowski danych przechowywania element wartości.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlMap::CAtlMap](#catlmap)|Konstruktor.|  
|[CAtlMap:: ~ CAtlMap](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlMap::AssertValid](#assertvalid)|Wywołaj tę metodę w celu potwierdzenia, że jeśli `CAtlMap` jest nieprawidłowy.|  
|[CAtlMap::DisableAutoRehash](#disableautorehash)|Wywołanie tej metody, aby wyłączyć automatyczne rehashing z `CAtlMap` obiektu.|  
|[CAtlMap::EnableAutoRehash](#enableautorehash)|Wywołanie tej metody, aby włączyć automatyczne rehashing z `CAtlMap` obiektu.|  
|[CAtlMap::GetAt](#getat)|Wywołaj tę metodę, aby zwracać element na określonej pozycji na mapie.|  
|[CAtlMap::GetCount](#getcount)|Wywołaj tę metodę, aby pobrać liczbę elementów w planie.|  
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Wywołaj tę metodę, aby określić liczbę pojemnikach w tablicy skrótów mapy.|  
|[CAtlMap::GetKeyAt](#getkeyat)|Wywołanie tej metody można pobrać klucza przechowywane w danej pozycji w `CAtlMap` obiektu.|  
|[CAtlMap::GetNext](#getnext)|Wywołanie tej metody można uzyskać wskaźnik do następnego elementu pary przechowywane w `CAtlMap` obiektu.|  
|[CAtlMap::GetNextAssoc](#getnextassoc)|Pobiera następnego elementu potrzeby iteracji.|  
|[CAtlMap::GetNextKey](#getnextkey)|Wywołanie tej metody można pobrać klucza dalej z `CAtlMap` obiektu.|  
|[CAtlMap::GetNextValue](#getnextvalue)|Wywołanie tej metody można uzyskać wartość dalej z `CAtlMap` obiektu.|  
|[CAtlMap::GetStartPosition](#getstartposition)|Wywołaj tę metodę, aby uruchomić iteracji mapy.|  
|[CAtlMap::GetValueAt](#getvalueat)|Wywołanie tej metody do pobierania wartości przechowywanych na określonej pozycji w `CAtlMap` obiektu.|  
|[CAtlMap::InitHashTable](#inithashtable)|Wywołanie tej metody można zainicjować tablicy skrótów.|  
|[CAtlMap::IsEmpty](#isempty)|Wywołanie tej metody do testowania dla obiekt pusta mapa.|  
|[CAtlMap::Lookup](#lookup)|Wywołanie tej metody do wyszukiwania kluczy i wartości w `CAtlMap` obiektu.|  
|[CAtlMap::Rehash](#rehash)|Wywołanie tej metody do rehash `CAtlMap` obiektu.|  
|[CAtlMap::RemoveAll](#removeall)|Wywołanie tej metody, aby usunąć wszystkie elementy z `CAtlMap` obiektu.|  
|[CAtlMap::RemoveAtPos](#removeatpos)|Wywołanie tej metody, aby usunąć element na pozycji w `CAtlMap` obiektu.|  
|[CAtlMap::RemoveKey](#removekey)|Wywołanie tej metody, aby usunąć element z `CAtlMap` obiekt danego klucza.|  
|[CAtlMap::SetAt](#setat)|Wywołaj tę metodę, aby wstawić parę elementu do mapy.|  
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Wywołanie tej metody można ustawić optymalne obciążenie `CAtlMap` obiektu.|  
|[CAtlMap::SetValueAt](#setvalueat)|Wywołanie tej metody, aby zmienić wartość przechowywana na określonej pozycji w `CAtlMap` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Zastępuje lub dodaje nowy element `CAtlMap`.|  

  
## <a name="remarks"></a>Uwagi  
 `CAtlMap`zapewnia obsługę mapowania tablicę dowolnego typu, zarządzanie nieuporządkowaną tablicę elementów kluczy oraz powiązanych wartości. Elementów (składające się z klucza i wartości) są przechowywane przy użyciu algorytmu wyznaczania wartości skrótu, dzięki czemu dużej ilości danych, aby wydajnie przechowywania i pobierania.  
  
 `KTraits` i `VTraits` parametry są klasy cech, które zawiera dodatkowe wymagane, aby skopiować lub przenieść elementy kodu.  
  
 Zamiast `CAtlMap` jest oferowany przez [CRBMap](../../atl/reference/crbmap-class.md) klasy. `CRBMap`również przechowuje pary klucz wartość, ale wykazuje różnych parametrów. Czas potrzebny do wstawienia elementu wyszukiwania klucza lub usuwanie klucza z `CRBMap` obiektu jest kolejność *log(n)*, gdzie  *n*  jest liczba elementów. Aby uzyskać `CAtlMap`, wszystkie te operacje zazwyczaj trwać stałej, chociaż najgorszych możliwych scenariuszach może być zlecenia  *n* . Dlatego w przypadku typowej `CAtlMap` jest szybsze.  
  
 Różnica między `CRBMap` i `CAtlMap` stała się oczywista podczas iteracji przez elementy przechowywane. W `CRBMap`, elementy są odwiedzane posortowane. W `CAtlMap`, elementy nie są uporządkowane i nie można wywnioskować nie kolejności.  
  
 W przypadku niewielkiej liczby elementów muszą być przechowywane, należy rozważyć użycie [CSimpleMap](../../atl/reference/csimplemap-class.md) zamiast klasy.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="assertvalid"></a>CAtlMap::AssertValid  
 Wywołaj tę metodę w celu potwierdzenia, że jeśli `CAtlMap` obiekt jest nieprawidłowy.  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach do debugowania tej metody spowoduje ASSERT, jeśli `CAtlMap` obiekt jest nieprawidłowy.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="catlmap"></a>CAtlMap::CAtlMap  
 Konstruktor.  
  
```
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```  
  
### <a name="parameters"></a>Parametry  
 `nBins`  
 Liczba bins, zapewniając wskaźników do elementów przechowywane. Zobacz uwagi w dalszej części tego tematu, aby uzyskać informacje o bins.  
  
 `fOptimalLoad`  
 Stosunek optymalnego obciążenia.  
  
 `fLoThreshold`  
 Niższy próg współczynnika obciążenia.  
  
 `fHiThreshold`  
 Górny próg współczynnika obciążenia.  
  
 `nBlockSize`  
 Rozmiar bloku.  
  
### <a name="remarks"></a>Uwagi  
 `CAtlMap`odwołuje się do wszystkich swoich elementów przechowywanych przez utworzenie indeksu przy użyciu algorytmu wyznaczania wartości skrótu dla klucza. "Bin" zawierającego wskaźnik do elementów przechowywanych odwołuje się do tego indeksu. Jeśli pojemnik jest już w użyciu, połączone listy jest tworzony na dostęp do kolejnych elementów. Przechodzenie przez listę działa wolniej niż bezpośredni dostęp do elementu poprawne, i tak struktury mapy należy saldo wymagania dotyczące magazynu względem wydajności. Parametry domyślne zostały wybrane do uzyskania dobrych wyników w większości przypadków.  
  
 Współczynnik ładowania jest stosunek liczby bins do liczby elementów przechowywanych w obiekcie mapy. Po obliczeniu struktury mapy *fOptimalLoad* wartość parametru będzie używany do obliczania liczba bins wymagane. Tę wartość można zmienić za pomocą [CAtlMap::SetOptimalLoad](#setoptimalload) metody.  
  
 `fLoThreshold` Parametru jest niższa wartość, która może osiągnąć współczynnik obciążenia, zanim `CAtlMap` ponownych optymalny rozmiar mapy.  
  
 `fHiThreshold` Parametr jest górna wartość, która może osiągnąć współczynnik obciążenia, zanim `CAtlMap` obiektu ponownych optymalny rozmiar mapy.  
  
 Ten proces ponownego obliczania (nazywane rehashing) jest domyślnie włączona. Jeśli chcesz wyłączyć ten proces, być może podczas wprowadzania dużych ilości danych w tym samym czasie, wywołanie [CAtlMap::DisableAutoRehash](#disableautorehash) metody. Uaktywnij ponownie za pomocą [CAtlMap::EnableAutoRehash](#enableautorehash) metody.  
  
 `nBlockSize` Parametr jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszyć wywołania procedury alokacji pamięci, ale użyj więcej zasobów.  
  
 Przed wszystkie dane mogą być przechowywane, konieczne jest inicjowanie tablicy skrótów wywołaniem [CAtlMap::InitHashTable](#inithashtable).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlMap:: ~ CAtlMap  
 Destruktor.  
  
```
~CAtlMap() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie zasoby przydzielone.  
  
##  <a name="cpair_class"></a>Klasa CAtlMap::CPair  
 Klasa zawierająca elementy klucz i wartość.  
  
```
class CPair : public __POSITION
```  
  
### <a name="remarks"></a>Uwagi  
 Ta klasa jest używana przez metody [CAtlMap::GetNext](#getnext) i [CAtlMap::Lookup](#lookup) do uzyskania dostępu do elementów kluczy i wartości zapisane w strukturze mapowania.  
  
##  <a name="disableautorehash"></a>CAtlMap::DisableAutoRehash  
 Wywołanie tej metody, aby wyłączyć automatyczne rehashing z `CAtlMap` obiektu.  
  
```
void DisableAutoRehash() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Włączenie automatycznego rehashing (który jest domyślnie), liczba pojemnikach w tablicy skrótów zostaną automatycznie ponownie obliczone Jeśli wartość obciążenia (stosunek liczby bins liczby elementy przechowywane w tablicy) przekracza wartości maksymalnej lub minimalnej określony w momencie utworzenia mapy.  
  
 `DisableAutoRehash`jest najbardziej przydatna, gdy dużą liczbę elementów zostanie dodany do mapy na raz. Zamiast wyzwolenie procesu rehashing, za każdym razem, gdy zostaną przekroczone limity, jest bardziej wydajne, aby wywołać `DisableAutoRehash`Dodaj elementy, a na koniec wywołania [CAtlMap::EnableAutoRehash](#enableautorehash).  
  
##  <a name="enableautorehash"></a>CAtlMap::EnableAutoRehash  
 Wywołanie tej metody, aby włączyć automatyczne rehashing z `CAtlMap` obiektu.  
  
```
void EnableAutoRehash() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Włączenie automatycznego rehashing (który jest domyślnie), liczba pojemnikach w tablicy skrótów zostaną automatycznie ponownie obliczone Jeśli wartość obciążenia (stosunek liczby bins liczby elementy przechowywane w tablicy) przekracza wartości maksymalnej lub minimalnej określony w momencie utworzenia mapy.  
  
 **EnableAutoRefresh** jest najczęściej używana po wywołaniu [CAtlMap::DisableAutoRehash](#disableautorehash).  
  
##  <a name="getat"></a>CAtlMap::GetAt  
 Wywołaj tę metodę, aby zwracać element na określonej pozycji na mapie.  
  
```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).  
  
 `key`  
 Parametr szablonu określający typ klucza mapy.  
  
 *wartość*  
 Parametr szablonu określający typ wartości mapy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do bieżącej pary klucz/wartość elementy przechowywane w planie.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli `pos` jest równa NULL.  
  
##  <a name="getcount"></a>CAtlMap::GetCount  
 Wywołaj tę metodę, aby pobrać liczbę elementów w planie.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę elementów w obiekcie mapy. Pojedynczy element jest para klucza i wartości.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="gethashtablesize"></a>CAtlMap::GetHashTableSize  
 Wywołaj tę metodę, aby określić liczbę pojemnikach w tablicy skrótów mapy.  
  
```
UINT GetHashTableSize() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę bins w tablicy skrótów. Zobacz [CAtlMap::CAtlMap](#catlmap) wyjaśnienie.  
  
##  <a name="getkeyat"></a>CAtlMap::GetKeyAt  
 Wywołanie tej metody można pobrać klucza przechowywane w danej pozycji w `CAtlMap` obiektu.  
  
```
const K& GetKeyAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do klucza przechowywane w danej pozycji w `CAtlMap` obiektu.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="getnext"></a>CAtlMap::GetNext  
 Wywołanie tej metody można uzyskać wskaźnik do następnego elementu pary przechowywane w `CAtlMap` obiektu.  
  
```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do dalej pary klucz/wartość elementy przechowywane w planie. `pos` Pozycji licznik jest aktualizowany po każdym wywołaniu. Jeśli element pobrane jest ostatnie na mapie `pos` jest równa NULL.  
  
##  <a name="getnextassoc"></a>CAtlMap::GetNextAssoc  
 Pobiera następnego elementu potrzeby iteracji.  
  
```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).  
  
 `key`  
 Parametr szablonu określający typ klucza mapy.  
  
 *wartość*  
 Parametr szablonu określający typ wartości mapy.  
  
### <a name="remarks"></a>Uwagi  
 `pos` Pozycji licznik jest aktualizowany po każdym wywołaniu. Jeśli element pobrane jest ostatnie na mapie `pos` jest równa NULL.  
  
##  <a name="getnextkey"></a>CAtlMap::GetNextKey  
 Wywołanie tej metody można pobrać klucza dalej z `CAtlMap` obiektu.  
  
```
const K& GetNextKey(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do następnego klucza na mapie.  
  
### <a name="remarks"></a>Uwagi  
 Aktualizuje licznik bieżącej pozycji `pos`. Jeśli nie ma żadnych więcej wpisów w planie, licznik pozycja jest ustawiony na wartość NULL.  
  
##  <a name="getnextvalue"></a>CAtlMap::GetNextValue  
 Wywołanie tej metody można uzyskać wartość dalej z `CAtlMap` obiektu.  
  
```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do następnej wartości na mapie.  
  
### <a name="remarks"></a>Uwagi  
 Aktualizuje licznik bieżącej pozycji `pos`. Jeśli nie ma żadnych więcej wpisów w planie, licznik pozycja jest ustawiony na wartość NULL.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="getstartposition"></a>CAtlMap::GetStartPosition  
 Wywołaj tę metodę, aby uruchomić iteracji mapy.  
  
```
POSITION GetStartPosition() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pozycji początkowej lub wartość NULL jest zwracany, gdy mapy jest pusta.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody można uruchomić iteracji mapy zwracając **pozycji** wartości, które mogą zostać przekazane do `GetNextAssoc` metody.  
  
> [!NOTE]
>  Sekwencja iteracji nie jest przewidywalne  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="getvalueat"></a>CAtlMap::GetValueAt  
 Wywołanie tej metody do pobierania wartości przechowywanych na określonej pozycji w `CAtlMap` obiektu.  
  
```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do wartości przechowywanych na pozycji w `CAtlMap` obiektu.  
  
##  <a name="inithashtable"></a>CAtlMap::InitHashTable  
 Wywołanie tej metody można zainicjować tablicy skrótów.  
  
```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```  
  
### <a name="parameters"></a>Parametry  
 `nBins`  
 Liczba bins używane przez tablicy skrótów. Zobacz [CAtlMap::CAtlMap](#catlmap) wyjaśnienie.  
  
 `bAllocNow`  
 Wskazanie flagi, gdy można przydzielić pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** na pomyślne inicjowania **false** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 `InitHashTable`musi zostać wywołana przed elementów są przechowywane w tablicy skrótów.  Jeśli ta metoda nie jest wywoływana jawnie, będzie ona wywoływana automatycznie po raz pierwszy element zostanie dodany za pomocą liczby bin określony przez **CAtlMap** konstruktora.  W przeciwnym razie mapy zostaną zainicjowane przy użyciu nowego licznika bin określony przez `nBins` parametru.  
  
 Jeśli `bAllocNow` parametr ma wartość false, nie będzie można przydzielić pamięci wymagane przez tablicy skrótów, aż najpierw jest wymagana. Może to być przydatne, jeśli jest wiedzą, w przypadku użycia mapy.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="isempty"></a>CAtlMap::IsEmpty  
 Wywołanie tej metody do testowania dla obiekt pusta mapa.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli mapy jest pusta, **false** inaczej.  
  
##  <a name="kinargtype"></a>CAtlMap::KINARGTYPE  
 Typ używany, gdy klucz jest przekazywany jako argument wejściowy.  
  
```
typedef KTraits::INARGTYPE KINARGTYPE;
```  
  
##  <a name="koutargtype"></a>CAtlMap::KOUTARGTYPE  
 Typ używany, gdy klucz jest zwracany jako argument danych wyjściowych.  
  
```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```  
  
##  <a name="lookup"></a>CAtlMap::Lookup  
 Wywołanie tej metody do wyszukiwania kluczy i wartości w `CAtlMap` obiektu.  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Określa klucz identyfikujący element, aby wyszukiwać.  
  
 *wartość*  
 Zmienna, która odbiera wartość wyszukiwanego w górę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy formularz metoda zwraca wartość true, jeśli klucz zostanie znaleziony, w przeciwnym razie wartość false. Formularze drugiego i trzeciego zwraca wskaźnik do [CPair](#cpair_class) które mogą służyć jako stanie w przypadku wywołań [CAtlMap::GetNext](#getnext) i tak dalej.  
  
### <a name="remarks"></a>Uwagi  
 `Lookup`używa algorytmu wyznaczania wartości skrótu, aby szybko znaleźć element map, zawierającego klucz, która dokładnie odpowiada danego klucza parametru.  
  
##  <a name="operator_at"></a>CAtlMap::operator\[\]  
 Zastępuje lub dodaje nowy element `CAtlMap`.  
  
```
V& operator[](kinargtype key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz elementu do dodania lub zamiany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do wartości skojarzone z danym kluczem.  
  
### <a name="example"></a>Przykład  
 Jeśli klucz już istnieje, zostanie zastąpiony elementu. Jeśli klucz nie istnieje, zostanie dodany nowy element. Zobacz przykład [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="rehash"></a>CAtlMap::Rehash  
 Wywołanie tej metody do rehash `CAtlMap` obiektu.  
  
```
void Rehash(UINT nBins = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nBins`  
 Nowy numer bins do użycia w tablicy skrótów. Zobacz [CAtlMap::CAtlMap](#catlmap) wyjaśnienie.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `nBins` ma wartość 0, `CAtlMap` oblicza liczbę uzasadnione, na podstawie liczby elementów w planie i ustawienie optymalnego obciążenia. Zwykle rehashing proces odbywa się automatycznie, ale w tym przypadku [CAtlMap::DisableAutoRehash](#disableautorehash) została wywołana, ta metoda będzie wykonywać niezbędne zmiany rozmiaru.  
  
##  <a name="removeall"></a>CAtlMap::RemoveAll  
 Wywołanie tej metody, aby usunąć wszystkie elementy z `CAtlMap` obiektu.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Powoduje `CAtlMap` obiektu zwolnić pamięć, używany do przechowywania elementów.  
  
##  <a name="removeatpos"></a>CAtlMap::RemoveAtPos  
 Wywołanie tej metody, aby usunąć element na pozycji w `CAtlMap` obiektu.  
  
```
void RemoveAtPos(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="remarks"></a>Uwagi  
 Usuwa parę klucza i wartości przechowywane w określonej pozycji. Pamięć używana do przechowywania element zostanie zwolniona. Odwołuje się pozycja `pos` staje się nieprawidłowy, a gdy pozycja inne elementy w mapie pozostaje ważny, niekoniecznie jak zachowanie tej samej kolejności.  
  
##  <a name="removekey"></a>CAtlMap::RemoveKey  
 Wywołanie tej metody, aby usunąć element z `CAtlMap` obiekt danego klucza.  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz odpowiadający pary element chcesz usunąć.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli klucz jest odnalezione i usunięte, **false** w przypadku awarii.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="setat"></a>CAtlMap::SetAt  
 Wywołaj tę metodę, aby wstawić parę elementu do mapy.  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Wartość klucza można dodać do `CAtlMap` obiektu.  
  
 *wartość*  
 Wartość do dodania do `CAtlMap` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca element pary klucz wartość w `CAtlMap` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `SetAt`zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony. Jeśli klucz nie zostanie znaleziony, jest tworzony nowy pary klucza/wartości.  
  
##  <a name="setoptimalload"></a>CAtlMap::SetOptimalLoad  
 Wywołanie tej metody można ustawić optymalne obciążenie `CAtlMap` obiektu.  
  
```
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```  
  
### <a name="parameters"></a>Parametry  
 `fOptimalLoad`  
 Stosunek optymalnego obciążenia.  
  
 `fLoThreshold`  
 Niższy próg współczynnika obciążenia.  
  
 `fHiThreshold`  
 Górny próg współczynnika obciążenia.  
  
 `bRehashNow`  
 Flaga wskazująca, czy powinien być obliczany ponownie tablicy skrótów.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda ponownie definiuje wartość obciążenia optymalne `CAtlMap` obiektu. Zobacz [CAtlMap::CAtlMap](#catlmap) omówienie różnych parametrów. Jeśli `bRehashNow` ma wartość true, a liczba elementów jest poza wartości minimalną i maksymalną, są przeliczane tablicy skrótów.  
  
##  <a name="setvalueat"></a>CAtlMap::SetValueAt  
 Wywołanie tej metody, aby zmienić wartość przechowywana na określonej pozycji w `CAtlMap` obiektu.  
  
```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).  
  
 *wartość*  
 Wartość do dodania do `CAtlMap` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Zmienia element wartości przechowywane w danej pozycji w `CAtlMap` obiektu.  
  
##  <a name="vinargtype"></a>CAtlMap::VINARGTYPE  
 Typ używany, gdy wartość jest przekazywany jako argument wejściowy.  
  
```
typedef VTraits::INARGTYPE VINARGTYPE;
```  
  
##  <a name="voutargtype"></a>CAtlMap::VOUTARGTYPE  
 Typ używany, gdy wartość jest przekazywany jako argument danych wyjściowych.  
  
```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```  
  
##  <a name="m_key"></a>CAtlMap::CPair::m_key  
 Element członkowski danych przechowywania klucza elementu.  
  
```
const K m_key;
```    
  
### <a name="parameters"></a>Parametry  
 `K`  
 Typ klucza elementu.  
  
##  <a name="m_value"></a>CAtlMap::CPair::m_value  
 Element członkowski danych przechowywania element wartości.  
  
```
V  m_value;
```    
  
### <a name="parameters"></a>Parametry  
 *V*  
 Typ wartości elementu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe ramki](../../visual-cpp-samples.md)   
 [Przykładowe UpdatePV](../../visual-cpp-samples.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
