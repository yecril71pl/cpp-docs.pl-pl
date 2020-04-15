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
ms.openlocfilehash: 8a89ca7f7dedcd386abdd41e7487f1b838260c83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321443"
---
# <a name="catlmap-class"></a>Klasa CAtlMap

Ta klasa zawiera metody tworzenia obiektu mapy i zarządzania nim.

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
Typ elementu klucza.

*V*<br/>
Typ elementu wartości.

*KTraits ( ktraits )*<br/>
Kod używany do kopiowania lub przenoszenia elementów klucza. Zobacz [CElementTraits Klasy,](../../atl/reference/celementtraits-class.md) aby uzyskać więcej informacji.

*VTraits (Wyjęto)*<br/>
Kod używany do kopiowania lub przenoszenia elementów wartości.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CAtlMap::KINARGTYPE](#kinargtype)|Typ używany, gdy klucz jest przekazywany jako argument wejściowy|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Typ używany, gdy klucz jest zwracany jako argument wyjściowy.|
|[CAtlMap::VINARGTYPE](#vinargtype)|Typ używany, gdy wartość jest przekazywana jako argument wejściowy.|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Typ używany, gdy wartość jest przekazywana jako argument danych wyjściowych.|

### <a name="public-classes"></a>Klasy publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlMap::CPair Klasa](#cpair_class)|Klasa zawierająca elementy klucza i wartości.|

### <a name="cpair-data-members"></a>Członkowie CPair Data

|Nazwa|Opis|
|----------|-----------------|
|[CPair::m_key](#m_key)|Element członkowski danych przechowujący element klucza.|
|[CPair::m_value](#m_value)|Element członkowski danych przechowujący element wartości.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|Konstruktor.|
|[CAtlMap::~CAtlMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|Wywołanie tej metody, aby `CAtlMap` spowodować ASSERT, jeśli jest nieprawidłowy.|
|[CAtlMap::DisableAutoRehash](#disableautorehash)|Wywołanie tej metody, aby wyłączyć `CAtlMap` automatyczne rehashing obiektu.|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|Wywołanie tej metody, aby włączyć `CAtlMap` automatyczne rehashing obiektu.|
|[CAtlMap::GetAt](#getat)|Wywołanie tej metody, aby zwrócić element w określonej pozycji na mapie.|
|[CAtlMap::GetCount](#getcount)|Wywołanie tej metody, aby pobrać liczbę elementów na mapie.|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Wywołanie tej metody, aby określić liczbę pojemników w tabeli skrótów mapy.|
|[CAtlMap::GetKeyAt](#getkeyat)|Wywołanie tej metody, aby pobrać klucz przechowywany `CAtlMap` w danej pozycji w obiekcie.|
|[CAtlMap::GetNext](#getnext)|Wywołanie tej metody, aby uzyskać wskaźnik do `CAtlMap` następnej pary elementów przechowywanych w obiekcie.|
|[CAtlMap::GetNextAssoc](#getnextassoc)|Pobiera następny element do iteracji.|
|[CAtlMap::GetNextKey](#getnextkey)|Wywołanie tej metody, aby pobrać `CAtlMap` następny klucz z obiektu.|
|[CAtlMap::GetNextValue](#getnextvalue)|Wywołanie tej metody, aby `CAtlMap` uzyskać następną wartość z obiektu.|
|[CAtlMap::GetStartPosition](#getstartposition)|Wywołanie tej metody, aby rozpocząć iterację mapy.|
|[CAtlMap::GetValueAt](#getvalueat)|Wywołanie tej metody, aby pobrać wartość przechowywaną w danej pozycji w `CAtlMap` obiekcie.|
|[CAtlMap::InitHashTable](#inithashtable)|Wywołanie tej metody, aby zainicjować tabelę mieszania.|
|[CAtlMap::IsEmpty](#isempty)|Wywołanie tej metody, aby przetestować pusty obiekt mapy.|
|[CAtlMap::Odnośnik](#lookup)|Wywołanie tej metody, aby wyszukać klucze lub wartości w `CAtlMap` obiekcie.|
|[CAtlMap::Rehash](#rehash)|Wywołanie tej metody, `CAtlMap` aby ponownie zmiksować obiekt.|
|[CAtlMap::UsuńWszystki](#removeall)|Wywołanie tej metody, aby `CAtlMap` usunąć wszystkie elementy z obiektu.|
|[CAtlMap::RemoveAtPos](#removeatpos)|Wywołanie tej metody, aby usunąć element `CAtlMap` w danej pozycji w obiekcie.|
|[CAtlMap::Usuń klucz](#removekey)|Wywołanie tej metody, aby `CAtlMap` usunąć element z obiektu, biorąc pod uwagę klucz.|
|[CAtlMap::SetAt](#setat)|Wywołanie tej metody, aby wstawić parę elementów do mapy.|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Wywołanie tej metody, aby `CAtlMap` ustawić optymalne obciążenie obiektu.|
|[CAtlMap::SetValueAt](#setvalueat)|Wywołanie tej metody, aby zmienić wartość `CAtlMap` przechowywaną w danej pozycji w obiekcie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Zastępuje lub dodaje nowy element `CAtlMap`do pliku .|

## <a name="remarks"></a>Uwagi

`CAtlMap`zapewnia obsługę tablicy mapowania dowolnego typu, zarządzanie nieuiszczona tablica kluczowych elementów i ich skojarzone wartości. Elementy (składające się z klucza i wartości) są przechowywane przy użyciu algorytmu mieszania, dzięki czemu duża ilość danych ma być skutecznie przechowywane i pobierane.

*Parametry KTraits* i *VTraits* są klasami cech, które zawierają dowolny kod uzupełniający potrzebny do kopiowania lub przenoszenia elementów.

Alternatywą `CAtlMap` jest oferowana przez [CRBMap](../../atl/reference/crbmap-class.md) klasy. `CRBMap`przechowuje również pary klucz/wartość, ale wykazuje różne cechy wydajności. Czas wstawienia elementu, wyszukiwania klucza lub usuwania `CRBMap` klucza z obiektu to *dziennik kolejności(n)*, gdzie *n* jest liczbą elementów. Dla `CAtlMap`, wszystkie te operacje zwykle zajmują stały czas, chociaż najgorsze scenariusze mogą być w kolejności *n*. Dlatego w typowym przypadku `CAtlMap` jest szybszy.

Inna różnica `CRBMap` między `CAtlMap` i staje się widoczne, gdy iteracji za pośrednictwem przechowywanych elementów. W `CRBMap`programie elementy są odwiedzane w kolejności posortowane. W `CAtlMap`programie elementy nie są uporządkowane i nie można wywnioskować żadnej kolejności.

Gdy mała liczba elementów muszą być przechowywane, należy rozważyć użycie [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy zamiast.

Aby uzyskać więcej informacji, zobacz [ATL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a>CAtlMap::AssertValid

Wywołanie tej metody, aby `CAtlMap` spowodować ASSERT, jeśli obiekt jest nieprawidłowy.

```
void AssertValid() const;
```

### <a name="remarks"></a>Uwagi

W debugowania kompilacji ta metoda spowoduje `CAtlMap` ASSERT, jeśli obiekt jest nieprawidłowy.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapcatlmap"></a><a name="catlmap"></a>CAtlMap::CAtlMap

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

*nBiny*<br/>
Liczba pojemników zapewniających wskaźniki do przechowywanych elementów. Zobacz Uwagi w dalszej części tego tematu, aby uzyskać wyjaśnienie pojemników.

*fOptimalLoad*<br/>
Optymalny współczynnik obciążenia.

*fLoThreshold*<br/>
Niższy próg współczynnika obciążenia.

*fHiThreshold*<br/>
Górny próg współczynnika obciążenia.

*nBlockSize (Rozmiar)*<br/>
Rozmiar bloku.

### <a name="remarks"></a>Uwagi

`CAtlMap`odwołuje się do wszystkich jego przechowywanych elementów, najpierw tworząc indeks przy użyciu algorytmu mieszania na kluczu. Ten indeks odwołuje się do "bin", który zawiera wskaźnik do przechowywanych elementów. Jeśli pojemnik jest już używany, tworzona jest lista połączona, aby uzyskać dostęp do kolejnych elementów. Przechodzenie przez listę jest wolniejsze niż bezpośredni dostęp do poprawnego elementu, a więc struktura mapy musi równoważyć wymagania dotyczące magazynu z wydajnością. Parametry domyślne zostały wybrane, aby dać dobre wyniki w większości przypadków.

Współczynnik obciążenia jest stosunkiem liczby pojemników do liczby elementów przechowywanych w obiekcie mapy. Po ponownym obliczeniu struktury mapy wartość parametru *fOptimalLoad* zostanie użyta do obliczenia wymaganej liczby pojemników. Tę wartość można zmienić za pomocą [CAtlMap::SetOptimalLoad](#setoptimalload) metody.

Parametr *fLoThreshold* jest niższą wartością, jaką `CAtlMap` może osiągnąć współczynnik obciążenia przed ponownym obliczeniem optymalnego rozmiaru mapy.

Parametr *fHiThreshold* jest górną wartością, jaką `CAtlMap` może osiągnąć współczynnik obciążenia, zanim obiekt ponownie obliczy optymalny rozmiar mapy.

Ten proces ponownego obliczania (znany jako rehashing) jest domyślnie włączony. Jeśli chcesz wyłączyć ten proces, być może podczas wprowadzania dużej ilości danych w tym samym czasie, wywołaj [metodę CAtlMap::DisableAutoRehash.](#disableautorehash) Aktywuj go ponownie za pomocą [CAtlMap::EnableAutoRehash](#enableautorehash) metody.

Parametr *nBlockSize* jest miarą ilości przydzielonej pamięci, gdy wymagany jest nowy element. Większe rozmiary bloków zmniejszają liczbę wywołań procedur alokacji pamięci, ale zużywają więcej zasobów.

Przed przechowywaniem jakichkolwiek danych należy zainicjować tabelę mieszania za pomocą wywołania [CAtlMap::InitHashTable](#inithashtable).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a>CAtlMap::~CAtlMap

Destruktor.

```
~CAtlMap() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a>CAtlMap::CPair Klasa

Klasa zawierająca elementy klucza i wartości.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Uwagi

Ta klasa jest używana przez metody [CAtlMap::GetNext](#getnext) i [CAtlMap::Lookup,](#lookup) aby uzyskać dostęp do elementów klucza i wartości przechowywanych w strukturze mapowania.

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a>CAtlMap::DisableAutoRehash

Wywołanie tej metody, aby wyłączyć `CAtlMap` automatyczne rehashing obiektu.

```
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Uwagi

Po włączeniu automatycznego ponownego rozsyłania (co jest domyślnie), liczba pojemników w tabeli skrótów zostanie automatycznie przeliczona, jeśli wartość obciążenia (stosunek liczby pojemników do liczby elementów przechowywanych w tablicy) przekroczy wartości maksymalne lub minimalne określone w momencie utworzenia mapy.

`DisableAutoRehash`jest najbardziej przydatna, gdy duża liczba elementów zostanie dodana do mapy naraz. Zamiast wyzwalać proces rehashing za każdym razem, gdy limity są `DisableAutoRehash`przekroczone, jest bardziej efektywne, aby wywołać, dodać elementy, a na koniec wywołać [CAtlMap::EnableAutoRehash](#enableautorehash).

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a>CAtlMap::EnableAutoRehash

Wywołanie tej metody, aby włączyć `CAtlMap` automatyczne rehashing obiektu.

```
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Uwagi

Po włączeniu automatycznego ponownego rozsyłania (co jest domyślnie), liczba pojemników w tabeli skrótów zostanie automatycznie przeliczona, jeśli wartość obciążenia (stosunek liczby pojemników do liczby elementów przechowywanych w tablicy) przekroczy wartości maksymalne lub minimalne określone w momencie tworzenia mapy.

`EnableAutoRefresh`jest najczęściej używany po wywołaniu [CAtlMap::DisableAutoRehash](#disableautorehash).

## <a name="catlmapgetat"></a><a name="getat"></a>CAtlMap::GetAt

Wywołanie tej metody, aby zwrócić element w określonej pozycji na mapie.

```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie do [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Parametr szablonu określający typ klucza mapy.

*value*<br/>
Parametr szablonu określający typ wartości mapy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do bieżącej pary elementów klucza/wartości przechowywanych na mapie.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *pos* jest równa NULL.

## <a name="catlmapgetcount"></a><a name="getcount"></a>CAtlMap::GetCount

Wywołanie tej metody, aby pobrać liczbę elementów na mapie.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów w obiekcie mapy. Pojedynczy element jest parą klucz/wartość.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a>CAtlMap::GetHashTableSize

Wywołanie tej metody, aby określić liczbę pojemników w tabeli skrótów mapy.

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę pojemników w tabeli mieszania. Zobacz [CAtlMap::CAtlMap](#catlmap) wyjaśnienie.

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a>CAtlMap::GetKeyAt

Wywołanie tej metody, aby pobrać klucz przechowywany `CAtlMap` w danej pozycji w obiekcie.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie do [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do klucza przechowywanego w `CAtlMap` danej pozycji w obiekcie.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetnext"></a><a name="getnext"></a>CAtlMap::GetNext

Wywołanie tej metody, aby uzyskać wskaźnik do `CAtlMap` następnej pary elementów przechowywanych w obiekcie.

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie do [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do następnej pary elementów klucza/wartości przechowywanych na mapie. Licznik pozycji *poz* jest aktualizowany po każdym wywołaniu. Jeśli pobrany element jest ostatnim na mapie, pos jest *ustawiona* na WARTOŚĆ NULL.

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a>CAtlMap::GetNextAssoc

Pobiera następny element do iteracji.

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie do [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Parametr szablonu określający typ klucza mapy.

*value*<br/>
Parametr szablonu określający typ wartości mapy.

### <a name="remarks"></a>Uwagi

Licznik pozycji *poz* jest aktualizowany po każdym wywołaniu. Jeśli pobrany element jest ostatnim na mapie, pos jest *ustawiona* na WARTOŚĆ NULL.

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a>CAtlMap::GetNextKey

Wywołanie tej metody, aby pobrać `CAtlMap` następny klucz z obiektu.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie do [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do następnego klucza na mapie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżący licznik pozycji, *poz*. Jeśli na mapie nie ma więcej wpisów, licznik pozycji jest ustawiony na wartość NULL.

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a>CAtlMap::GetNextValue

Wywołanie tej metody, aby `CAtlMap` uzyskać następną wartość z obiektu.

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie do [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do następnej wartości na mapie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżący licznik pozycji, *poz*. Jeśli na mapie nie ma więcej wpisów, licznik pozycji jest ustawiony na wartość NULL.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a>CAtlMap::GetStartPosition

Wywołanie tej metody, aby rozpocząć iterację mapy.

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję początkową lub wartość NULL jest zwracana, jeśli mapa jest pusta.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby rozpocząć iterację mapy, zwracając wartość `GetNextAssoc` POSITION, która może być przekazana do metody.

> [!NOTE]
> Sekwencja iteracji nie jest przewidywalna

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a>CAtlMap::GetValueAt

Wywołanie tej metody, aby pobrać wartość przechowywaną w danej pozycji w `CAtlMap` obiekcie.

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie do [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wartości przechowywanej w `CAtlMap` danej pozycji w obiekcie.

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a>CAtlMap::InitHashTable

Wywołanie tej metody, aby zainicjować tabelę mieszania.

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Parametry

*nBiny*<br/>
Liczba pojemników używanych przez tabelę mieszania. Zobacz [CAtlMap::CAtlMap](#catlmap) wyjaśnienie.

*bLokalnyTeraz*<br/>
Oznaczenie flagi, gdy pamięć powinna być przydzielona.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE przy pomyślnym inicjalizacji, FAŁSZ w przypadku awarii.

### <a name="remarks"></a>Uwagi

`InitHashTable`należy wywołać, zanim wszystkie elementy są przechowywane w tabeli mieszania.  Jeśli ta metoda nie jest wywoływana jawnie, zostanie wywołana automatycznie przy pierwszym dodaniu elementu przy użyciu liczby pojemników określonej przez `CAtlMap` konstruktora.  W przeciwnym razie mapa zostanie zainicjowana przy użyciu nowej liczby pojemników określonej przez parametr *nBins.*

Jeśli parametr *bAllocNow* jest fałszywy, pamięć wymagana przez tabelę mieszania nie zostanie przydzielona, dopóki nie zostanie najpierw wymagana. Może to być przydatne, jeśli nie ma pewności, czy mapa będzie używana.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapisempty"></a><a name="isempty"></a>CAtlMap::IsEmpty

Wywołanie tej metody, aby przetestować pusty obiekt mapy.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli mapa jest pusta, w przeciwnym razie wartość FAŁsz.

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a>CAtlMap::KINARGTYPE

Typ używany, gdy klucz jest przekazywany jako argument wejściowy.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a>CAtlMap::KOUTARGTYPE

Typ używany, gdy klucz jest zwracany jako argument wyjściowy.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a>CAtlMap::Odnośnik

Wywołanie tej metody, aby wyszukać klucze lub wartości w `CAtlMap` obiekcie.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Określa klucz identyfikujący element, który ma być wyszukany.

*value*<br/>
Zmienna, która odbiera wartość wyszukiwania.

### <a name="return-value"></a>Wartość zwracana

Pierwsza forma metody zwraca wartość true, jeśli zostanie znaleziony klucz, w przeciwnym razie false. Drugi i trzeci formularz zwraca wskaźnik do [CPair,](#cpair_class) który może służyć jako pozycja dla wywołań [CAtlMap::GetNext](#getnext) i tak dalej.

### <a name="remarks"></a>Uwagi

`Lookup`używa algorytmu mieszania, aby szybko znaleźć element mapy zawierający klucz, który dokładnie pasuje do danego parametru klucza.

## <a name="catlmapoperator-"></a><a name="operator_at"></a>CAtlMap::operator\[\]

Zastępuje lub dodaje nowy element `CAtlMap`do pliku .

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz elementu do dodania lub zastąpienia.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wartości skojarzonej z danym kluczem.

### <a name="example"></a>Przykład

Jeśli klucz już istnieje, element jest zastępowany. Jeśli klucz nie istnieje, dodaje się nowy element. Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmaprehash"></a><a name="rehash"></a>CAtlMap::Rehash

Wywołanie tej metody, `CAtlMap` aby ponownie zmiksować obiekt.

```
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Parametry

*nBiny*<br/>
Nowa liczba pojemników do użycia w tabeli mieszania. Zobacz [CAtlMap::CAtlMap](#catlmap) wyjaśnienie.

### <a name="remarks"></a>Uwagi

Jeśli *nBins* wynosi `CAtlMap` 0, oblicza rozsądną liczbę na podstawie liczby elementów na mapie i optymalnego ustawienia obciążenia. Zwykle proces rehashing jest automatyczny, ale jeśli [CAtlMap::DisableAutoRehash](#disableautorehash) został wywołany, ta metoda wykona niezbędne zmiany rozmiaru.

## <a name="catlmapremoveall"></a><a name="removeall"></a>CAtlMap::UsuńWszystki

Wywołanie tej metody, aby `CAtlMap` usunąć wszystkie elementy z obiektu.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Uwagi

Czyści `CAtlMap` obiekt, zwalniając pamięć używaną do przechowywania elementów.

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a>CAtlMap::RemoveAtPos

Wywołanie tej metody, aby usunąć element `CAtlMap` w danej pozycji w obiekcie.

```
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie do [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

### <a name="remarks"></a>Uwagi

Usuwa parę klucz/wartość przechowywaną w określonym położeniu. Pamięć używana do przechowywania elementu jest zwalniana. Pozycja, do której odwołuje *się poz,* staje się nieprawidłowa i chociaż pozycja innych elementów na mapie pozostaje prawidłowa, nie muszą one zachowywać tej samej kolejności.

## <a name="catlmapremovekey"></a><a name="removekey"></a>CAtlMap::Usuń klucz

Wywołanie tej metody, aby `CAtlMap` usunąć element z obiektu, biorąc pod uwagę klucz.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz odpowiadający parze elementów, którą chcesz usunąć.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli klucz zostanie znaleziony i usunięty, WARTOŚĆ FAŁSZ W przypadku awarii.

### <a name="example"></a>Przykład

Zobacz przykład [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapsetat"></a><a name="setat"></a>CAtlMap::SetAt

Wywołanie tej metody, aby wstawić parę elementów do mapy.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Wartość klucza, aby `CAtlMap` dodać do obiektu.

*value*<br/>
Wartość dodana do `CAtlMap` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca położenie pary elementu klucz/wartość `CAtlMap` w obiekcie.

### <a name="remarks"></a>Uwagi

`SetAt`zastępuje istniejący element, jeśli zostanie znaleziony pasujący klucz. Jeśli klucz nie zostanie znaleziony, zostanie utworzona nowa para klucz/wartość.

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a>CAtlMap::SetOptimalLoad

Wywołanie tej metody, aby `CAtlMap` ustawić optymalne obciążenie obiektu.

```
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
Niższy próg współczynnika obciążenia.

*fHiThreshold*<br/>
Górny próg współczynnika obciążenia.

*bRehashNow*<br/>
Flaga wskazująca, czy tabela mieszania powinna zostać ponownie obliczona.

### <a name="remarks"></a>Uwagi

Ta metoda na nowo definiuje `CAtlMap` optymalną wartość obciążenia dla obiektu. Zobacz [CAtlMap::CAtlMap](#catlmap) do dyskusji na temat różnych parametrów. Jeśli *bRehashNow* jest true, a liczba elementów jest poza wartościami minimalnymi i maksymalnymi, tabela mieszania jest ponownie obliczana.

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a>CAtlMap::SetValueAt

Wywołanie tej metody, aby zmienić wartość `CAtlMap` przechowywaną w danej pozycji w obiekcie.

```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie do [CAtlMap::GetNextAssoc](#getnextassoc) lub [CAtlMap::GetStartPosition](#getstartposition).

*value*<br/>
Wartość dodana do `CAtlMap` obiektu.

### <a name="remarks"></a>Uwagi

Zmienia element wartości przechowywany w danej `CAtlMap` pozycji w obiekcie.

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a>CAtlMap::VINARGTYPE

Typ używany, gdy wartość jest przekazywana jako argument wejściowy.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a>CAtlMap::VOUTARGTYPE

Typ używany, gdy wartość jest przekazywana jako argument danych wyjściowych.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a>CAtlMap::CPair::m_key

Element członkowski danych przechowujący element klucza.

```
const K m_key;
```

### <a name="parameters"></a>Parametry

*K*<br/>
Typ elementu klucza.

## <a name="catlmapcpairm_value"></a><a name="m_value"></a>CAtlMap::CPair::m_value

Element członkowski danych przechowujący element wartości.

```
V  m_value;
```

### <a name="parameters"></a>Parametry

*V*<br/>
Typ elementu wartości.

## <a name="see-also"></a>Zobacz też

[Przykłada markizy](../../overview/visual-cpp-samples.md)<br/>
[Próbka aktualizacjiPV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
