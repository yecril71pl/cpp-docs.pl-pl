---
title: Klasa CAtlMap
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
ms.openlocfilehash: 1821532a4d5a3078202f180273b02945b8d8e4ba
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774558"
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

*K*<br/>
Typ klucza elementu.

*V*<br/>
Typ elementu wartości.

*KTraits*<br/>
Kod używany, aby skopiować lub przenieść kluczowe elementy. Zobacz [klasa CElementTraits](../../atl/reference/celementtraits-class.md) Aby uzyskać więcej informacji.

*VTraits*<br/>
Kod używany do kopiowania lub przenoszenia elementów wartości.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name|Opis|
|----------|-----------------|
|[CAtlMap::KINARGTYPE](#kinargtype)|Typ używany, gdy klucz jest przekazywany jako argument wejściowy|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Typ używany, gdy klucz jest zwracany jako argument dane wyjściowe.|
|[CAtlMap::VINARGTYPE](#vinargtype)|Typ używany, gdy wartość jest przekazywany jako argument wejściowy.|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Typ używany, gdy wartość jest przekazywany jako argument danych wyjściowych.|

### <a name="public-classes"></a>Publiczne klasy

|Name|Opis|
|----------|-----------------|
|[Klasa CAtlMap::CPair](#cpair_class)|Klasa zawierająca elementy klucza i wartości.|

### <a name="cpair-data-members"></a>Elementy członkowskie danych CPair

|Name|Opis|
|----------|-----------------|
|[CPair::m_key](#m_key)|Element członkowski danych, przechowywania klucza elementu.|
|[CPair::m_value](#m_value)|Element członkowski danych, przechowywania element wartości.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name|Opis|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|Konstruktor.|
|[CAtlMap::~CAtlMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name|Opis|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|Wywołaj tę metodę, aby spowodować ASSERT, jeśli `CAtlMap` jest nieprawidłowy.|
|[CAtlMap::DisableAutoRehash](#disableautorehash)|Wywołaj tę metodę, aby wyłączyć automatyczne rehashing z `CAtlMap` obiektu.|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|Wywołaj tę metodę, aby włączyć automatyczne rehashing z `CAtlMap` obiektu.|
|[CAtlMap::GetAt](#getat)|Wywołaj tę metodę w celu zwrócenia elementu na określonej pozycji na mapie.|
|[CAtlMap::GetCount](#getcount)|Wywołaj tę metodę, aby pobrać liczbę elementów w mapie.|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Wywołaj tę metodę, aby określić liczbę pojemników w mapy mieszającej.|
|[CAtlMap::GetKeyAt](#getkeyat)|Wywołaj tę metodę, aby pobrać klucz przechowywany w danej pozycji w `CAtlMap` obiektu.|
|[CAtlMap::GetNext](#getnext)|Wywołaj tę metodę, aby uzyskać wskaźnik do następnego elementu pary przechowywane w `CAtlMap` obiektu.|
|[CAtlMap::GetNextAssoc](#getnextassoc)|Pobiera następny element do wykonania iteracji.|
|[CAtlMap::GetNextKey](#getnextkey)|Wywołaj tę metodę, aby pobrać następny klawisz z `CAtlMap` obiektu.|
|[CAtlMap::GetNextValue](#getnextvalue)|Wywołanie tej metody można pobrać następnej wartości z `CAtlMap` obiektu.|
|[CAtlMap::GetStartPosition](#getstartposition)|Wywołaj tę metodę, aby uruchomić iteracji mapy.|
|[CAtlMap::GetValueAt](#getvalueat)|Wywołaj tę metodę, aby pobrać wartość przechowywaną w określonej pozycji w `CAtlMap` obiektu.|
|[CAtlMap::InitHashTable](#inithashtable)|Wywołaj tę metodę w celu inicjowania tabeli wyznaczania wartości skrótu.|
|[CAtlMap::IsEmpty](#isempty)|Wywołaj tę metodę, aby sprawdzić, czy obiekt pusta mapa.|
|[CAtlMap::Lookup](#lookup)|Wywołaj tę metodę, aby wyszukać kluczy ani wartości w `CAtlMap` obiektu.|
|[CAtlMap::Rehash](#rehash)|Wywołaj tę metodę w celu rehash — `CAtlMap` obiektu.|
|[CAtlMap::RemoveAll](#removeall)|Wywołaj tę metodę, aby usunąć wszystkie elementy z `CAtlMap` obiektu.|
|[CAtlMap::RemoveAtPos](#removeatpos)|Wywołanie tej metody, aby usunąć element w danej pozycji w `CAtlMap` obiektu.|
|[CAtlMap::RemoveKey](#removekey)|Wywołaj tę metodę, aby usunąć element z `CAtlMap` obiekt, na podstawie klucza.|
|[CAtlMap::SetAt](#setat)|Wywołaj tę metodę, aby wstawić para elementów do mapy.|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Wywołanie tej metody, aby ustawić optymalne obciążenie `CAtlMap` obiektu.|
|[CAtlMap::SetValueAt](#setvalueat)|Wywołaj tę metodę, aby zmienić wartość przechowywaną w określonej pozycji w `CAtlMap` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Name|Opis|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Zastępuje lub dodaje nowy element do `CAtlMap`.|

## <a name="remarks"></a>Uwagi

`CAtlMap` zapewnia obsługę mapowania tablicę dla dowolnego typu, Zarządzanie macierzą Nieuporządkowana kluczami elementów i ich skojarzone wartości. Elementów (składające się z klucza i wartości) są przechowywane przy użyciu algorytmu wyznaczania wartości skrótu, dzięki czemu dużej ilości danych, efektywnie przechowywane i pobierane.

*KTraits* i *VTraits* parametry są traits — klasy, które zawierają dodatkowe wymagane do kopiowania lub przenoszenia elementów kodu.

Alternatywa `CAtlMap` jest oferowany przez [CRBMap](../../atl/reference/crbmap-class.md) klasy. `CRBMap` również przechowuje pary klucz/wartość, ale wykazuje różną charakterystykę wydajności. Czas poświęcony na wstawienie elementu wyszukiwania klucza lub Usuń klucz z `CRBMap` obiektu to zamówienie *log(n)*, gdzie *n* jest liczba elementów. Aby uzyskać `CAtlMap`, wszystkie te operacje zazwyczaj trwać stałej, chociaż najgorszego przypadku scenariuszy może być zamówienia *n*. W związku z tym, w przypadku typowej `CAtlMap` jest szybsze.

Różnica między `CRBMap` i `CAtlMap` staje się oczywisty, gdy iteracji na elementach przechowywanych. W `CRBMap`, elementy są odwiedzane w kolejności posortowanej. W `CAtlMap`, elementy nie są uporządkowane i kolejność nie można wywnioskować.

W przypadku niewielkiej liczby elementów muszą być przechowywane, należy wziąć pod uwagę przy użyciu [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy zamiast tego.

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="assertvalid"></a>  CAtlMap::AssertValid

Wywołaj tę metodę, aby spowodować ASSERT, jeśli `CAtlMap` obiektu jest nieprawidłowy.

```
void AssertValid() const;
```

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania, ta metoda spowoduje, że ASERCJA Jeśli `CAtlMap` obiektu jest nieprawidłowy.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

##  <a name="catlmap"></a>  CAtlMap::CAtlMap

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

*nBins*<br/>
Liczba pojemników, zapewniając wskaźników do elementów przechowywanych. Zobacz uwagi w dalszej części tego tematu objaśnienia dotyczące pojemniki.

*fOptimalLoad*<br/>
Stosunek optymalnego obciążenia.

*fLoThreshold*<br/>
Próg niższy współczynnik obciążenia.

*fHiThreshold*<br/>
Górny próg współczynnik obciążenia.

*nBlockSize*<br/>
Rozmiar bloku.

### <a name="remarks"></a>Uwagi

`CAtlMap` odwołuje się do wszystkich swoich elementów przechowywanych przez utworzenie indeksu za pomocą algorytmu wyznaczania wartości skrótu klucza. Indeks ten odwołuje się do "bin", który zawiera wskaźnik do przechowywanej elementów. Pojemnik jest już używana, zostanie utworzona dostęp do kolejnych elementów listy. Przechodzenie przez listy jest wolniejszy niż bezpośredni dostęp do elementu poprawne, a więc struktury mapy musi równoważyć wymagania dotyczące magazynu w odniesieniu do wydajności. Aby zapewnić dobre wyniki w większości przypadków zostały wybrane parametry domyślne.

Współczynnik obciążenia to stosunek liczby pojemniki do liczby elementów przechowywanych w obiekcie mapy. Po obliczeniu struktury mapy *fOptimalLoad* zostanie użyta wartość parametru, aby obliczyć liczbę pojemniki wymagane. Tę wartość można zmienić za pomocą [CAtlMap::SetOptimalLoad](#setoptimalload) metody.

*FLoThreshold* parametr jest niższa wartość, która może osiągnąć współczynnik obciążenia, zanim `CAtlMap` ponownych optymalny rozmiar mapy.

*FHiThreshold* parametr ma wartość górnego, który może osiągnąć współczynnik obciążenia, zanim `CAtlMap` obiektu ponownych optymalny rozmiar mapy.

Ten proces ponownego obliczania (znanych jako rehashing) jest domyślnie włączona. Jeśli chcesz wyłączyć ten proces, być może podczas wprowadzania dużą ilość danych w tym samym czasie, wywołanie [CAtlMap::DisableAutoRehash](#disableautorehash) metody. Uaktywnij ponownie ją za pomocą [CAtlMap::EnableAutoRehash](#enableautorehash) metody.

*NBlockSize* parametr jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszają liczbę interwencji do procedur alokacji pamięci, ale używa więcej zasobów.

Przed wszystkie dane mogą być przechowywane, konieczne jest inicjowania tabeli wyznaczania wartości skrótu z wywołaniem [CAtlMap::InitHashTable](#inithashtable).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

##  <a name="dtor"></a>  CAtlMap:: ~ CAtlMap

Destruktor.

```
~CAtlMap() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie zasoby przydzielone.

##  <a name="cpair_class"></a>  Klasa CAtlMap::CPair

Klasa zawierająca elementy klucza i wartości.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Uwagi

Ta klasa jest używana przez metody [CAtlMap::GetNext](#getnext) i [CAtlMap::Lookup](#lookup) do dostępu do kluczy i wartości elementów, zapisane w strukturze mapowania.

##  <a name="disableautorehash"></a>  CAtlMap::DisableAutoRehash

Wywołaj tę metodę, aby wyłączyć automatyczne rehashing z `CAtlMap` obiektu.

```
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Uwagi

Włączenie automatycznego rehashing (co jest ustawieniem domyślnym), liczba pojemników, w tabeli skrótów zostaną automatycznie ponownie obliczone Jeśli wartość obciążenia (stosunek liczby pojemniki do liczby elementów przechowywanych w tablicy) przekracza wartości maksymalnej lub minimalnej określony w momencie utworzenia mapy.

`DisableAutoRehash` jest najbardziej użyteczna gdy dużą liczbę elementów zostanie dodany do mapy na raz. Zamiast wyzwolenie procesu rehashing, za każdym razem, gdy zostaną przekroczone limity, jest bardziej wydajne, aby wywołać `DisableAutoRehash`, dodać elementy, a na koniec Wywołaj [CAtlMap::EnableAutoRehash](#enableautorehash).

##  <a name="enableautorehash"></a>  CAtlMap::EnableAutoRehash

Wywołaj tę metodę, aby włączyć automatyczne rehashing z `CAtlMap` obiektu.

```
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Uwagi

Włączenie automatycznego rehashing (co jest ustawieniem domyślnym), liczba pojemników, w tabeli skrótów zostaną automatycznie ponownie obliczone Jeśli wartość obciążenia (stosunek liczby pojemniki do liczby elementów przechowywanych w tablicy) przekracza wartości maksymalnej lub minimalnej określony w momencie utworzenia mapy.

`EnableAutoRefresh` stosuje się najczęściej po wywołaniu [CAtlMap::DisableAutoRehash](#disableautorehash).

##  <a name="getat"></a>  CAtlMap::GetAt

Wywołaj tę metodę w celu zwrócenia elementu na określonej pozycji na mapie.

```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Pozycja licznika, zwracane przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

*Klucz*<br/>
Parametr szablonu określający typ klucza mapy.

*value*<br/>
Parametr szablonu określający typ wartości mapy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do bieżącej pary klucz/wartość elementów przechowywany w mapie.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania, wystąpi błąd asercji Jeśli *pos* jest równa NULL.

##  <a name="getcount"></a>  CAtlMap::GetCount

Wywołaj tę metodę, aby pobrać liczbę elementów w mapie.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów w obiekcie mapy. Pojedynczy element jest parą klucz/wartość.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

##  <a name="gethashtablesize"></a>  CAtlMap::GetHashTableSize

Wywołaj tę metodę, aby określić liczbę pojemników w mapy mieszającej.

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę pojemników, w tabeli wyznaczania wartości skrótu. Zobacz [CAtlMap::CAtlMap](#catlmap) objaśnienia.

##  <a name="getkeyat"></a>  CAtlMap::GetKeyAt

Wywołaj tę metodę, aby pobrać klucz przechowywany w danej pozycji w `CAtlMap` obiektu.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Pozycja licznika, zwracane przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do klucz przechowywany w danej pozycji w `CAtlMap` obiektu.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

##  <a name="getnext"></a>  CAtlMap::GetNext

Wywołaj tę metodę, aby uzyskać wskaźnik do następnego elementu pary przechowywane w `CAtlMap` obiektu.

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Pozycja licznika, zwracane przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do następnego pary klucz/wartość elementów przechowywany w mapie. *Pos* pozycji licznik jest aktualizowany po każdym wywołaniu. Jeśli pobrano element jest ostatni w mapie, *pos* ma wartość NULL.

##  <a name="getnextassoc"></a>  CAtlMap::GetNextAssoc

Pobiera następny element do wykonania iteracji.

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Pozycja licznika, zwracane przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

*Klucz*<br/>
Parametr szablonu określający typ klucza mapy.

*value*<br/>
Parametr szablonu określający typ wartości mapy.

### <a name="remarks"></a>Uwagi

*Pos* pozycji licznik jest aktualizowany po każdym wywołaniu. Jeśli pobrano element jest ostatni w mapie, *pos* ma wartość NULL.

##  <a name="getnextkey"></a>  CAtlMap::GetNextKey

Wywołaj tę metodę, aby pobrać następny klawisz z `CAtlMap` obiektu.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Pozycja licznika, zwracane przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do kluczowi w mapie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżącej pozycji licznika, *pos*. Jeśli nie ma żadnych więcej wpisów w mapie, licznik pozycja jest ustawiony na wartość NULL.

##  <a name="getnextvalue"></a>  CAtlMap::GetNextValue

Wywołanie tej metody można pobrać następnej wartości z `CAtlMap` obiektu.

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Pozycja licznika, zwracane przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do następnej wartości na mapie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżącej pozycji licznika, *pos*. Jeśli nie ma żadnych więcej wpisów w mapie, licznik pozycja jest ustawiony na wartość NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

##  <a name="getstartposition"></a>  CAtlMap::GetStartPosition

Wywołaj tę metodę, aby uruchomić iteracji mapy.

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycja początkowa lub wartość NULL jest zwracany, jeśli mapa jest pusta.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody można uruchomić iteracji mapy, zwracając pozycji wartość, która może być przekazywany do `GetNextAssoc` metody.

> [!NOTE]
>  Sekwencja iteracji nie jest przewidywalne

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

##  <a name="getvalueat"></a>  CAtlMap::GetValueAt

Wywołaj tę metodę, aby pobrać wartość przechowywaną w określonej pozycji w `CAtlMap` obiektu.

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Pozycja licznika, zwracane przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wartość przechowywaną w danej pozycji w `CAtlMap` obiektu.

##  <a name="inithashtable"></a>  CAtlMap::InitHashTable

Wywołaj tę metodę w celu inicjowania tabeli wyznaczania wartości skrótu.

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Parametry

*nBins*<br/>
Liczba pojemników używane przez tabelę mieszania. Zobacz [CAtlMap::CAtlMap](#catlmap) objaśnienia.

*bAllocNow*<br/>
Wskazanie flagi, gdy można przydzielić pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, prawidłowego zainicjowania FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`InitHashTable` musi zostać wywołana przed wszystkie elementy są przechowywane w tabeli wyznaczania wartości skrótu.  Jeśli ta metoda nie jest wywoływana jawnie, będzie ona wywoływana automatycznie po raz pierwszy element zostanie dodany przy użyciu liczba pojemników, określony przez `CAtlMap` konstruktora.  W przeciwnym razie mapy zostaną zainicjowane przy użyciu nowego licznika bin określony przez *nBins* parametru.

Jeśli *bAllocNow* parametr ma wartość false, ilość pamięci wymaganej przez tabelę mieszania nie zostaną przydzielone, dopóki nie zostanie najpierw wymagane. Może to być przydatne, jeśli niepewne, jeśli mapa ma być używany.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

##  <a name="isempty"></a>  CAtlMap::IsEmpty

Wywołaj tę metodę, aby sprawdzić, czy obiekt pusta mapa.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli mapa jest pusta, wartość FALSE w przeciwnym razie.

##  <a name="kinargtype"></a>  CAtlMap::KINARGTYPE

Typ używany, gdy klucz jest przekazywany jako argument wejściowy.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

##  <a name="koutargtype"></a>  CAtlMap::KOUTARGTYPE

Typ używany, gdy klucz jest zwracany jako argument dane wyjściowe.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

##  <a name="lookup"></a>  CAtlMap::Lookup

Wywołaj tę metodę, aby wyszukać kluczy ani wartości w `CAtlMap` obiektu.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Określa klucz, który identyfikuje elementu, który ma być wyszukiwana.

*value*<br/>
Zmienna, która otrzymuje wartość oglądałem się w górę.

### <a name="return-value"></a>Wartość zwracana

Pierwszy formularz metoda zwraca wartość true, jeśli klucz zostanie znaleziony, w przeciwnym razie wartość false. Drugi i trzeci formularzy zwracają wskaźnik do [CPair](#cpair_class) który może służyć jako stanie dla wywołań [CAtlMap::GetNext](#getnext) i tak dalej.

### <a name="remarks"></a>Uwagi

`Lookup` używa algorytmu wyznaczania wartości skrótu, aby szybko znaleźć element map, zawierającego klucz, który dokładnie pasuje do danego klucza parametru.

##  <a name="operator_at"></a>  CAtlMap::operator \[\]

Zastępuje lub dodaje nowy element do `CAtlMap`.

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz elementu do dodania lub zamiany.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wartości skojarzone z danym kluczem.

### <a name="example"></a>Przykład

Jeśli klucz już istnieje, jest zastępowany elementu. Jeśli klucz nie istnieje, zostanie dodany nowy element. Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

##  <a name="rehash"></a>  CAtlMap::Rehash

Wywołaj tę metodę w celu rehash — `CAtlMap` obiektu.

```
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Parametry

*nBins*<br/>
Nowy numer pojemniki do użycia w tabeli wyznaczania wartości skrótu. Zobacz [CAtlMap::CAtlMap](#catlmap) objaśnienia.

### <a name="remarks"></a>Uwagi

Jeśli *nBins* ma wartość 0, `CAtlMap` oblicza liczbę uzasadnione, na podstawie liczby elementów w mapie i ustawienie obciążenia optymalne. Zwykle proces rehashing odbywa się automatycznie, ale w tym przypadku [CAtlMap::DisableAutoRehash](#disableautorehash) została wywołana, ta metoda będzie wykonywać niezbędne zmiany rozmiaru.

##  <a name="removeall"></a>  CAtlMap::RemoveAll

Wywołaj tę metodę, aby usunąć wszystkie elementy z `CAtlMap` obiektu.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Uwagi

Czyści `CAtlMap` obiektu, pamięć, używany do przechowywania elementów.

##  <a name="removeatpos"></a>  CAtlMap::RemoveAtPos

Wywołanie tej metody, aby usunąć element w danej pozycji w `CAtlMap` obiektu.

```
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Pozycja licznika, zwracane przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

### <a name="remarks"></a>Uwagi

Usuwa pary klucz/wartość przechowywaną w określonej pozycji. Pamięć używana do przechowywania elementu jest zwalniana. Odwołuje się do niego pozycja *pos* staje się nieprawidłowy, a gdy pozycja innych elementów w mapie nadal jest ważna, niekoniecznie robią zachować takiej samej kolejności.

##  <a name="removekey"></a>  CAtlMap::RemoveKey

Wywołaj tę metodę, aby usunąć element z `CAtlMap` obiekt, na podstawie klucza.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz odpowiadający para elementów chcesz usunąć.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli klucz jest znaleziono i usunięte, wartość FALSE w przypadku niepowodzenia.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

##  <a name="setat"></a>  CAtlMap::SetAt

Wywołaj tę metodę, aby wstawić para elementów do mapy.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza do dodania do `CAtlMap` obiektu.

*value*<br/>
Wartość do dodania `CAtlMap` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję pary klucz/wartość elementu, w `CAtlMap` obiektu.

### <a name="remarks"></a>Uwagi

`SetAt` zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony. Jeśli klucz nie zostanie znaleziony, zostanie utworzony nową parę klucz wartość.

##  <a name="setoptimalload"></a>  CAtlMap::SetOptimalLoad

Wywołanie tej metody, aby ustawić optymalne obciążenie `CAtlMap` obiektu.

```
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>Parametry

*fOptimalLoad*<br/>
Stosunek optymalnego obciążenia.

*fLoThreshold*<br/>
Próg niższy współczynnik obciążenia.

*fHiThreshold*<br/>
Górny próg współczynnik obciążenia.

*bRehashNow*<br/>
Flaga wskazująca, czy w tabeli wyznaczania wartości skrótu powinny zostać ponownie obliczone.

### <a name="remarks"></a>Uwagi

Ta metoda redefiniuje wartość obciążenia optymalne `CAtlMap` obiektu. Zobacz [CAtlMap::CAtlMap](#catlmap) dyskusję na temat różnych parametrów. Jeśli *bRehashNow* ma wartość true, a liczba elementów, które znajduje się poza minimalne i maksymalne wartości, jest ponownie obliczana w tabeli wyznaczania wartości skrótu.

##  <a name="setvalueat"></a>  CAtlMap::SetValueAt

Wywołaj tę metodę, aby zmienić wartość przechowywaną w określonej pozycji w `CAtlMap` obiektu.

```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Pozycja licznika, zwracane przez poprzednie wywołanie [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

*value*<br/>
Wartość do dodania `CAtlMap` obiektu.

### <a name="remarks"></a>Uwagi

Zmienia element wartości przechowywane w danej pozycji w `CAtlMap` obiektu.

##  <a name="vinargtype"></a>  CAtlMap::VINARGTYPE

Typ używany, gdy wartość jest przekazywany jako argument wejściowy.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

##  <a name="voutargtype"></a>  CAtlMap::VOUTARGTYPE

Typ używany, gdy wartość jest przekazywany jako argument danych wyjściowych.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

##  <a name="m_key"></a>  CAtlMap::CPair::m_key

Element członkowski danych, przechowywania klucza elementu.

```
const K m_key;
```

### <a name="parameters"></a>Parametry

*K*<br/>
Typ klucza elementu.

##  <a name="m_value"></a>  CAtlMap::CPair::m_value

Element członkowski danych, przechowywania element wartości.

```
V  m_value;
```

### <a name="parameters"></a>Parametry

*V*<br/>
Typ elementu wartości.

## <a name="see-also"></a>Zobacz także

[Przykładowe Neon](../../overview/visual-cpp-samples.md)<br/>
[Przykładowe UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
