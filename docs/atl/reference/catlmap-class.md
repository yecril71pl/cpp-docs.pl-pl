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
ms.openlocfilehash: b79e6cbd796569e6ba11c96158099de6c30b310a
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168062"
---
# <a name="catlmap-class"></a>Klasa CAtlMap

Ta klasa udostępnia metody tworzenia obiektu mapy i zarządzania nim.

## <a name="syntax"></a>Składnia

```cpp
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
```

### <a name="parameters"></a>Parametry

*K*<br/>
Typ elementu klucza.

*V*<br/>
Typ elementu wartości.

*KTraits*<br/>
Kod używany do kopiowania lub przenoszenia elementów klucza. Aby uzyskać więcej informacji, zobacz [Klasa CElementTraits](../../atl/reference/celementtraits-class.md) .

*VTraits*<br/>
Kod używany do kopiowania lub przenoszenia elementów wartości.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CAtlMap::KINARGTYPE](#kinargtype)|Typ używany, gdy klucz jest przesyłany jako argument wejściowy|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Typ używany, gdy klucz jest zwracany jako argument wyjściowy.|
|[CAtlMap::VINARGTYPE](#vinargtype)|Typ używany, gdy wartość jest przenoszona jako argument wejściowy.|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Typ używany, gdy wartość jest przenoszona jako argument wyjściowy.|

### <a name="public-classes"></a>Klasy publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlMap:: CPair, Klasa](#cpair_class)|Klasa zawierająca elementy klucza i wartości.|

### <a name="cpair-data-members"></a>CPair elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPair:: m_key](#m_key)|Element członkowski danych przechowujący element klucza.|
|[CPair:: m_value](#m_value)|Element członkowski danych przechowujący element Value.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|Konstruktor.|
|[CAtlMap:: ~ CAtlMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|Wywołaj tę metodę, aby spowodować potwierdzenie, `CAtlMap` jeśli jest nieprawidłowe.|
|[CAtlMap::D isableAutoRehash](#disableautorehash)|Wywołaj tę metodę, aby wyłączyć automatyczne przemieszanie `CAtlMap` obiektu.|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|Wywołaj tę metodę, aby włączyć automatyczne odmieszanie `CAtlMap` obiektu.|
|[CAtlMap::GetAt](#getat)|Wywołaj tę metodę, aby zwrócić element w określonej pozycji na mapie.|
|[CAtlMap:: GetCount](#getcount)|Wywołaj tę metodę, aby pobrać liczbę elementów na mapie.|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Wywołaj tę metodę, aby określić liczbę pojemników w tabeli skrótów mapy.|
|[CAtlMap::GetKeyAt](#getkeyat)|Wywołaj tę metodę, aby pobrać klucz przechowywany w danej pozycji w `CAtlMap` obiekcie.|
|[CAtlMap:: GetNext](#getnext)|Wywołaj tę metodę, aby uzyskać wskaźnik do pary elementów znajdujących się w `CAtlMap` obiekcie.|
|[CAtlMap::GetNextAssoc](#getnextassoc)|Pobiera następny element do iteracji.|
|[CAtlMap::GetNextKey](#getnextkey)|Wywołaj tę metodę, aby pobrać następny klucz z `CAtlMap` obiektu.|
|[CAtlMap::GetNextValue](#getnextvalue)|Wywołaj tę metodę, aby uzyskać następną wartość `CAtlMap` z obiektu.|
|[CAtlMap::GetStartPosition](#getstartposition)|Wywołaj tę metodę, aby rozpocząć iterację mapy.|
|[CAtlMap::GetValueAt](#getvalueat)|Wywołaj tę metodę, aby pobrać wartość przechowywaną w danej pozycji w `CAtlMap` obiekcie.|
|[CAtlMap::InitHashTable](#inithashtable)|Wywołaj tę metodę, aby zainicjować tablicę skrótów.|
|[CAtlMap:: IsEmpty](#isempty)|Wywołaj tę metodę, aby przetestować dla pustego obiektu mapy.|
|[CAtlMap:: Lookup](#lookup)|Wywołaj tę metodę, aby wyszukiwać klucze lub wartości `CAtlMap` w obiekcie.|
|[CAtlMap:: rehash](#rehash)|Wywołaj tę metodę, aby skrócić `CAtlMap` obiekt.|
|[CAtlMap::](#removeall)|Wywołaj tę metodę, aby usunąć wszystkie elementy `CAtlMap` z obiektu.|
|[CAtlMap::RemoveAtPos](#removeatpos)|Wywołaj tę metodę, aby usunąć element z danego położenia w `CAtlMap` obiekcie.|
|[CAtlMap::RemoveKey](#removekey)|Wywołaj tę metodę, aby usunąć element z `CAtlMap` obiektu, uwzględniając klucz.|
|[CAtlMap::SetAt](#setat)|Wywołaj tę metodę, aby wstawić parę elementów do mapy.|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Wywołaj tę metodę, aby ustawić optymalne obciążenie `CAtlMap` obiektu.|
|[CAtlMap::SetValueAt](#setvalueat)|Wywołaj tę metodę, aby zmienić wartość przechowywaną w danej pozycji w `CAtlMap` obiekcie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlMap:: operator\[\]](catlmap-class.md#operator_at)|Zamienia lub dodaje nowy element do elementu `CAtlMap`.|

## <a name="remarks"></a>Uwagi

`CAtlMap`zapewnia obsługę tablicy mapowania dowolnego danego typu, zarządzając nieuporządkowaną tablicą elementów kluczy i ich skojarzone wartości. Elementy (składające się z klucza i wartości) są przechowywane przy użyciu algorytmu wyznaczania wartości skrótu, co pozwala na efektywne przechowywanie i pobieranie dużej ilości danych.

Parametry *KTraits* i *VTraits* są klasami cech, które zawierają dowolny dodatkowy kod wymagany do kopiowania lub przenoszenia elementów.

Alternatywa dla `CAtlMap` jest oferowana przez klasę [CRBMap](../../atl/reference/crbmap-class.md) . `CRBMap`przechowuje także pary klucz/wartość, ale wykazuje różne charakterystyki wydajności. Czas potrzebny do wstawienia elementu, wyszukania klucza lub usunięcia klucza z `CRBMap` obiektu jest *dziennikiem porządku (n)*, gdzie *n* jest liczbą elementów. W `CAtlMap`przypadku programu wszystkie te operacje zazwyczaj pobierają stały czas, chociaż najgorszym scenariuszem może być kolejność *n*. W związku z tym w typowym `CAtlMap` przypadku jest to szybsze.

Druga różnica między `CRBMap` i `CAtlMap` jest widoczna podczas iterowania przez przechowywane elementy. W `CRBMap`, elementy są odwiedzane w sortowanej kolejności. W `CAtlMap`, elementy nie są uporządkowane i nie można wywnioskować żadnych zamówień.

W przypadku konieczności przechowywania niewielkiej liczby elementów należy rozważyć użycie klasy [CSimpleMap](../../atl/reference/csimplemap-class.md) .

Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll. h

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a>CAtlMap::AssertValid

Wywołaj tę metodę, aby spowodować potwierdzenie, `CAtlMap` Jeśli obiekt jest nieprawidłowy.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania ta metoda będzie powodowała potwierdzenie, czy `CAtlMap` obiekt jest nieprawidłowy.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapcatlmap"></a><a name="catlmap"></a>CAtlMap::CAtlMap

Konstruktor.

```cpp
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>Parametry

*nBins*<br/>
Liczba pojemników dostarczających wskaźniki do przechowywanych elementów. Zobacz uwagi w dalszej części tego tematu, aby zapoznać się z objaśnieniem pojemników.

*fOptimalLoad*<br/>
Optymalny współczynnik obciążenia.

*fLoThreshold*<br/>
Dolny próg współczynnika obciążenia.

*fHiThreshold*<br/>
Górny próg współczynnika obciążenia.

*nBlockSize*<br/>
Rozmiar bloku.

### <a name="remarks"></a>Uwagi

`CAtlMap`odwołuje się do wszystkich przechowywanych elementów, tworząc najpierw indeks przy użyciu algorytmu wyznaczania wartości skrótu w kluczu. Ten indeks odwołuje się do "bin", który zawiera wskaźnik do przechowywanych elementów. Jeśli pojemnik jest już używany, tworzona jest lista połączonej w celu uzyskania dostępu do kolejnych elementów. Przechodzenie listy jest wolniejsze niż bezpośredni dostęp do poprawnego elementu, dlatego struktura mapy musi zrównoważyć wymagania dotyczące wydajności magazynu. W większości przypadków zostały wybrane domyślne parametry zapewniające dobre wyniki.

Współczynnik obciążenia to stosunek liczby pojemników do liczby elementów przechowywanych w obiekcie mapy. Po ponownym obliczeniu struktury mapy zostanie użyta wartość parametru *fOptimalLoad* w celu obliczenia liczby wymaganych pojemników. Tę wartość można zmienić przy użyciu metody [CAtlMap:: SetOptimalLoad](#setoptimalload) .

Parametr *fLoThreshold* jest niższą wartością, którą może osiągnąć współczynnik obciążenia, aby `CAtlMap` ponownie obliczyć optymalny rozmiar mapy.

Parametr *fHiThreshold* jest górną wartością, którą może osiągnąć współczynnik obciążenia, zanim `CAtlMap` obiekt obliczy optymalny rozmiar mapy.

Ten proces ponownego obliczania (znany jako ponowny hash) jest domyślnie włączony. Jeśli chcesz wyłączyć ten proces, być może w przypadku jednoczesnego wprowadzania dużej ilości danych, wywołaj metodę [CAtlMap::D isableautorehash](#disableautorehash) . Aktywuj ponownie przy użyciu metody [CAtlMap:: EnableAutoRehash](#enableautorehash) .

*NBlockSize* parametr jest miarą ilości pamięci przydzieloną, gdy wymagany jest nowy element. Większe rozmiary bloków redukują wywołania procedur alokacji pamięci, ale wykorzystują więcej zasobów.

Aby można było przechowywać dowolne dane, konieczne jest zainicjowanie tabeli skrótów z wywołaniem do [CAtlMap:: InitHashTable](#inithashtable).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a>CAtlMap:: ~ CAtlMap

Destruktor.

```cpp
~CAtlMap() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby.

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a>CAtlMap:: CPair, Klasa

Klasa zawierająca elementy klucza i wartości.

```cpp
class CPair : public __POSITION
```

### <a name="remarks"></a>Uwagi

Ta klasa jest używana przez metody [CAtlMap:: GetNext](#getnext) i [CAtlMap:: Lookup](#lookup) do uzyskiwania dostępu do elementów klucza i wartości przechowywanych w strukturze mapowania.

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a>CAtlMap::D isableAutoRehash

Wywołaj tę metodę, aby wyłączyć automatyczne przemieszanie `CAtlMap` obiektu.

```cpp
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Uwagi

Gdy jest włączone automatyczne ponowne tworzenie skrótów (domyślnie jest to ustawienie domyślne), liczba pojemników w tabeli skrótów będzie automatycznie obliczana ponownie, jeśli wartość obciążenia (stosunek liczby pojemników do liczby elementów przechowywanych w tablicy) przekracza maksymalne lub minimalne wartości określone w momencie utworzenia mapy.

`DisableAutoRehash`jest najbardziej przydatny, gdy duża liczba elementów zostanie dodana do mapy jednocześnie. Zamiast wyzwalać proces ponownej mieszania przy każdym przekroczeniu limitów, bardziej wydajne jest wywołanie `DisableAutoRehash`, dodanie elementów i zakończenie wywołania [CAtlMap:: EnableAutoRehash](#enableautorehash).

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a>CAtlMap::EnableAutoRehash

Wywołaj tę metodę, aby włączyć automatyczne odmieszanie `CAtlMap` obiektu.

```cpp
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Uwagi

Gdy jest włączone automatyczne ponowne tworzenie skrótów (domyślnie jest to ustawienie domyślne), liczba pojemników w tabeli skrótów będzie automatycznie obliczana ponownie, jeśli wartość obciążenia (stosunek liczby pojemników do liczby elementów przechowywanych w tablicy) przekracza maksymalne lub minimalne wartości określone w momencie utworzenia mapy.

`EnableAutoRefresh`najczęściej używane po wywołaniu [CAtlMap::D isableautorehash](#disableautorehash).

## <a name="catlmapgetat"></a><a name="getat"></a>CAtlMap::GetAt

Wywołaj tę metodę, aby zwrócić element w określonej pozycji na mapie.

```cpp
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap:: GetNextAssoc](#getnextassoc) lub [CAtlMap:: GetStartPosition](#getstartposition).

*głównych*<br/>
Parametr szablonu określający typ klucza mapy.

*value*<br/>
Parametr szablonu określający typ wartości mapy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do bieżącej pary elementów klucza/wartości przechowywanych w mapie.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli wartość *pos* będzie równa null.

## <a name="catlmapgetcount"></a><a name="getcount"></a>CAtlMap:: GetCount

Wywołaj tę metodę, aby pobrać liczbę elementów na mapie.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów w obiekcie mapy. Pojedynczy element jest parą klucz/wartość.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a>CAtlMap::GetHashTableSize

Wywołaj tę metodę, aby określić liczbę pojemników w tabeli skrótów mapy.

```cpp
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę pojemników w tabeli skrótów. Aby uzyskać wyjaśnienie, zobacz [CAtlMap:: CAtlMap](#catlmap) .

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a>CAtlMap::GetKeyAt

Wywołaj tę metodę, aby pobrać klucz przechowywany w danej pozycji w `CAtlMap` obiekcie.

```cpp
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap:: GetNextAssoc](#getnextassoc) lub [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do klucza przechowywanego w danej pozycji w `CAtlMap` obiekcie.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapgetnext"></a><a name="getnext"></a>CAtlMap:: GetNext

Wywołaj tę metodę, aby uzyskać wskaźnik do pary elementów znajdujących się w `CAtlMap` obiekcie.

```cpp
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap:: GetNextAssoc](#getnextassoc) lub [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do następnej pary elementów klucza/wartości przechowywanych w mapie. Po każdym wywołaniu zostanie zaktualizowany licznik pozycji *punktu sprzedaży* . Jeśli pobrany element jest ostatnim na mapie, *pos* ma USTAWIONĄ wartość null.

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a>CAtlMap::GetNextAssoc

Pobiera następny element do iteracji.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap:: GetNextAssoc](#getnextassoc) lub [CAtlMap:: GetStartPosition](#getstartposition).

*głównych*<br/>
Parametr szablonu określający typ klucza mapy.

*value*<br/>
Parametr szablonu określający typ wartości mapy.

### <a name="remarks"></a>Uwagi

Po każdym wywołaniu zostanie zaktualizowany licznik pozycji *punktu sprzedaży* . Jeśli pobrany element jest ostatnim na mapie, *pos* ma USTAWIONĄ wartość null.

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a>CAtlMap::GetNextKey

Wywołaj tę metodę, aby pobrać następny klucz z `CAtlMap` obiektu.

```cpp
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap:: GetNextAssoc](#getnextassoc) lub [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do następnego klawisza na mapie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżący licznik pozycji w *punkcie sprzedaży*. Jeśli na mapie nie ma więcej wpisów, licznik pozycji ma wartość NULL.

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a>CAtlMap::GetNextValue

Wywołaj tę metodę, aby uzyskać następną wartość `CAtlMap` z obiektu.

```cpp
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap:: GetNextAssoc](#getnextassoc) lub [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do następnej wartości na mapie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżący licznik pozycji w *punkcie sprzedaży*. Jeśli na mapie nie ma więcej wpisów, licznik pozycji ma wartość NULL.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a>CAtlMap::GetStartPosition

Wywołaj tę metodę, aby rozpocząć iterację mapy.

```cpp
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję początkową lub zwraca wartość NULL, jeśli mapa jest pusta.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby rozpocząć iterację mapy przez zwrócenie wartości pozycji, która może zostać przeniesiona do `GetNextAssoc` metody.

> [!NOTE]
> Sekwencja iteracji nie jest przewidywalna

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a>CAtlMap::GetValueAt

Wywołaj tę metodę, aby pobrać wartość przechowywaną w danej pozycji w `CAtlMap` obiekcie.

```cpp
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap:: GetNextAssoc](#getnextassoc) lub [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wartości przechowywanej w danej pozycji w `CAtlMap` obiekcie.

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a>CAtlMap::InitHashTable

Wywołaj tę metodę, aby zainicjować tablicę skrótów.

```cpp
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Parametry

*nBins*<br/>
Liczba pojemników używanych przez tablicę skrótów. Aby uzyskać wyjaśnienie, zobacz [CAtlMap:: CAtlMap](#catlmap) .

*bAllocNow*<br/>
Wskazanie flagi, gdy pamięć powinna zostać przypisana.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku pomyślnego inicjowania, FAŁSZ w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`InitHashTable`musi być wywoływana przed zapisaniem jakichkolwiek elementów w tabeli skrótów.  Jeśli ta metoda nie jest jawnie wywoływana, zostanie ona wywołana automatycznie przy pierwszym dodawaniu elementu przy użyciu liczby bin określonej przez `CAtlMap` konstruktora.  W przeciwnym razie mapa zostanie zainicjowana przy użyciu nowej liczby pojemników określonej przez parametr *nBins* .

Jeśli parametr *bAllocNow* ma wartość false, pamięć wymagana przez tabelę skrótów nie zostanie przydzielone do momentu pierwszej potrzeby. Może to być przydatne, jeśli nie jest to konieczne, jeśli mapa zostanie użyta.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapisempty"></a><a name="isempty"></a>CAtlMap:: IsEmpty

Wywołaj tę metodę, aby przetestować dla pustego obiektu mapy.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli mapa jest pusta, w przeciwnym razie FALSE.

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a>CAtlMap::KINARGTYPE

Typ używany, gdy klucz jest przesyłany jako argument wejściowy.

```cpp
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a>CAtlMap::KOUTARGTYPE

Typ używany, gdy klucz jest zwracany jako argument wyjściowy.

```cpp
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a>CAtlMap:: Lookup

Wywołaj tę metodę, aby wyszukiwać klucze lub wartości `CAtlMap` w obiekcie.

```cpp
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Określa klucz, który identyfikuje element, który ma zostać wyszukany.

*value*<br/>
Zmienna, która otrzymuje wartość wyszukiwania.

### <a name="return-value"></a>Wartość zwracana

Pierwsza forma metody zwraca wartość true, jeśli klucz zostanie znaleziony, w przeciwnym razie false. Drugi i trzeci formularz zwracają wskaźnik do elementu [CPair](#cpair_class) , który może być używany jako pozycja dla wywołań [CAtlMap:: GetNext](#getnext) i tak dalej.

### <a name="remarks"></a>Uwagi

`Lookup`używa algorytmu wyznaczania wartości skrótu, aby szybko znaleźć element mapy zawierający klucz, który dokładnie pasuje do podanego parametru klucza.

## <a name="catlmapoperator-"></a><a name="operator_at"></a>CAtlMap:: operator\[\]

Zamienia lub dodaje nowy element do elementu `CAtlMap`.

```cpp
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Klucz elementu do dodania lub zamiany.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wartości skojarzonej z danym kluczem.

### <a name="example"></a>Przykład

Jeśli klucz już istnieje, element zostanie zastąpiony. Jeśli klucz nie istnieje, zostanie dodany nowy element. Zobacz przykład dla [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmaprehash"></a><a name="rehash"></a>CAtlMap:: rehash

Wywołaj tę metodę, aby skrócić `CAtlMap` obiekt.

```cpp
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Parametry

*nBins*<br/>
Nowa liczba pojemników do użycia w tabeli skrótów. Aby uzyskać wyjaśnienie, zobacz [CAtlMap:: CAtlMap](#catlmap) .

### <a name="remarks"></a>Uwagi

Jeśli *nBins* ma wartość 0 `CAtlMap` , program oblicza odpowiednią liczbę na podstawie liczby elementów w mapie i optymalnego ustawienia ładowania. Zwykle proces ponownego tworzenia skrótów jest automatyczny, ale jeśli [CAtlMap::D isableautorehash](#disableautorehash) , ta metoda wykona wymagane zmiany rozmiarów.

## <a name="catlmapremoveall"></a><a name="removeall"></a>CAtlMap::

Wywołaj tę metodę, aby usunąć wszystkie elementy `CAtlMap` z obiektu.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Uwagi

Czyści `CAtlMap` obiekt, zwalniając pamięć używaną do przechowywania elementów.

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a>CAtlMap::RemoveAtPos

Wywołaj tę metodę, aby usunąć element z danego położenia w `CAtlMap` obiekcie.

```cpp
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap:: GetNextAssoc](#getnextassoc) lub [CAtlMap:: GetStartPosition](#getstartposition).

### <a name="remarks"></a>Uwagi

Usuwa pary klucz/wartość przechowywane w określonej pozycji. Pamięć użyta do przechowywania elementu jest zwolniona. POZYCJA, do której odwołuje się *punkt sprzedaży* , jest nieprawidłowa, a mimo że pozycja innych elementów na mapie pozostaje ważna, nie zawsze zachowują tę samą kolejność.

## <a name="catlmapremovekey"></a><a name="removekey"></a>CAtlMap::RemoveKey

Wywołaj tę metodę, aby usunąć element z `CAtlMap` obiektu, uwzględniając klucz.

```cpp
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Klucz odpowiadający parze elementu, który chcesz usunąć.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli klucz zostanie znaleziony i usunięty, wartość FALSE w przypadku niepowodzenia.

### <a name="example"></a>Przykład

Zobacz przykład dla [CAtlMap:: CAtlMap](#catlmap).

## <a name="catlmapsetat"></a><a name="setat"></a>CAtlMap::SetAt

Wywołaj tę metodę, aby wstawić parę elementów do mapy.

```cpp
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza do dodania do `CAtlMap` obiektu.

*value*<br/>
Wartość, która ma zostać dodana `CAtlMap` do obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję pary klucz/wartość w `CAtlMap` obiekcie.

### <a name="remarks"></a>Uwagi

`SetAt`Zastępuje istniejący element, jeśli zostanie znaleziony pasujący klucz. Jeśli klucz nie zostanie znaleziony, zostanie utworzona nowa para klucz/wartość.

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a>CAtlMap::SetOptimalLoad

Wywołaj tę metodę, aby ustawić optymalne obciążenie `CAtlMap` obiektu.

```cpp
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>Parametry

*fOptimalLoad*<br/>
Optymalny współczynnik obciążenia.

*fLoThreshold*<br/>
Dolny próg współczynnika obciążenia.

*fHiThreshold*<br/>
Górny próg współczynnika obciążenia.

*bRehashNow*<br/>
Flaga oznaczająca, czy tabela skrótów powinna być ponownie obliczana.

### <a name="remarks"></a>Uwagi

Ta metoda ponownie definiuje optymalną wartość ładowania dla `CAtlMap` obiektu. Zobacz [CAtlMap:: CAtlMap](#catlmap) , aby zapoznać się z różnymi parametrami. Jeśli *bRehashNow* ma wartość true, a liczba elementów znajduje się poza wartością minimalną i maksymalną, tabela skrótów jest ponownie obliczana.

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a>CAtlMap::SetValueAt

Wywołaj tę metodę, aby zmienić wartość przechowywaną w danej pozycji w `CAtlMap` obiekcie.

```cpp
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie [CAtlMap:: GetNextAssoc](#getnextassoc) lub [CAtlMap:: GetStartPosition](#getstartposition).

*value*<br/>
Wartość, która ma zostać dodana `CAtlMap` do obiektu.

### <a name="remarks"></a>Uwagi

Zmienia element wartości przechowywany w danej pozycji w `CAtlMap` obiekcie.

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a>CAtlMap::VINARGTYPE

Typ używany, gdy wartość jest przenoszona jako argument wejściowy.

```cpp
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a>CAtlMap::VOUTARGTYPE

Typ używany, gdy wartość jest przenoszona jako argument wyjściowy.

```cpp
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a>CAtlMap:: CPair:: m_key

Element członkowski danych przechowujący element klucza.

```cpp
const K m_key;
```

### <a name="parameters"></a>Parametry

*K*<br/>
Typ elementu klucza.

## <a name="catlmapcpairm_value"></a><a name="m_value"></a>CAtlMap:: CPair:: m_value

Element członkowski danych przechowujący element Value.

```cpp
V  m_value;
```

### <a name="parameters"></a>Parametry

*V*<br/>
Typ elementu wartości.

## <a name="see-also"></a>Zobacz także

[Przykład neonu](../../overview/visual-cpp-samples.md)<br/>
[Przykład UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
