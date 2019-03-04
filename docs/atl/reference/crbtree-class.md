---
title: Klasa CRBTree
ms.date: 11/04/2016
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
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
ms.openlocfilehash: 59416000eecf4be25746d9dedd86ea2af116087a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281346"
---
# <a name="crbtree-class"></a>Klasa CRBTree

Ta klasa dostarcza metody do tworzenia i przy użyciu drzewa Red czarny.

## <a name="syntax"></a>Składnia

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBTree
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

|Nazwa|Opis|
|----------|-----------------|
|[CRBTree::KINARGTYPE](#kinargtype)|Typ używany, gdy klucz jest przekazywany jako argument wejściowy.|
|[CRBTree::KOUTARGTYPE](#koutargtype)|Typ używany, gdy klucz jest zwracany jako argument dane wyjściowe.|
|[CRBTree::VINARGTYPE](#vinargtype)|Typ używany, gdy wartość jest przekazywany jako argument wejściowy.|
|[CRBTree::VOUTARGTYPE](#voutargtype)|Typ używany, gdy wartość jest przekazywany jako argument danych wyjściowych.|

### <a name="public-classes"></a>Publiczne klasy

|Nazwa|Opis|
|----------|-----------------|
|[Klasa CRBTree::CPair](#cpair_class)|Klasa zawierająca elementy klucza i wartości.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBTree::~CRBTree](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|Wywołaj tę metodę, aby znaleźć położenie elementu, który używa następny dostępny klucz.|
|[CRBTree::GetAt](#getat)|Wywołaj tę metodę można pobrać elementu na określonej pozycji w drzewie.|
|[CRBTree::GetCount](#getcount)|Wywołaj tę metodę, aby uzyskać liczbę elementów w drzewie.|
|[CRBTree::GetHeadPosition](#getheadposition)|Wywołaj tę metodę, aby uzyskać wartość pozycji dla elementu na główny drzewa.|
|[CRBTree::GetKeyAt](#getkeyat)|Wywołaj tę metodę, aby uzyskać klucz z danej pozycji w drzewie.|
|[CRBTree::GetNext](#getnext)|Wywołaj tę metodę, aby uzyskać wskaźnik do elementu przechowywanego w `CRBTree` obiektu, a następnie przejdź położenie do następnego elementu.|
|[CRBTree::GetNextAssoc](#getnextassoc)|Wywołanie tej metody, aby uzyskać klucz i wartość elementu przechowywanego w mapie, a następnie przejdź położenie do następnego elementu.|
|[CRBTree::GetNextKey](#getnextkey)|Wywołaj tę metodę, aby pobrać klucz elementu przechowywanego w drzewie, a następnie przejdź położenie do następnego elementu.|
|[CRBTree::GetNextValue](#getnextvalue)|Wywołaj tę metodę, aby uzyskać wartość elementu przechowywanego w drzewie, a następnie przejdź położenie do następnego elementu.|
|[CRBTree::GetPrev](#getprev)|Wywołaj tę metodę, aby uzyskać wskaźnik do elementu przechowywanego w `CRBTree` obiektu, a następnie zaktualizować pozycji do poprzedniego elementu.|
|[CRBTree::GetTailPosition](#gettailposition)|Wywołaj tę metodę, aby uzyskać wartość pozycji elementu w ogon drzewa.|
|[CRBTree::GetValueAt](#getvalueat)|Wywołaj tę metodę, aby pobrać wartość przechowywaną w określonej pozycji w `CRBTree` obiektu.|
|[CRBTree::IsEmpty](#isempty)|Wywołaj tę metodę do testowania dla obiektu pusty drzewa.|
|[CRBTree::RemoveAll](#removeall)|Wywołaj tę metodę, aby usunąć wszystkie elementy z `CRBTree` obiektu.|
|[CRBTree::RemoveAt](#removeat)|Wywołanie tej metody, aby usunąć element w danej pozycji w `CRBTree` obiektu.|
|[CRBTree::SetValueAt](#setvalueat)|Wywołaj tę metodę, aby zmienić wartość przechowywaną w określonej pozycji w `CRBTree` obiektu.|

## <a name="remarks"></a>Uwagi

Drzewo czarny czerwony jest drzewo binarnego wyszukiwania, który używa dodatkowy informacja na węzeł, aby upewnić się, że pozostaje "zrównoważony," będącego, wysokość drzewa nie rozwój nieproporcjonalnie duży i wpłynąć na wydajność.

Tej klasy szablonu jest przeznaczona do użycia przez [CRBMap](../../atl/reference/crbmap-class.md) i [CRBMultiMap](../../atl/reference/crbmultimap-class.md). Większość metod, które tworzą te klasy pochodne są dostarczane przez `CRBTree`.

Pełniejsze omówienie różnych klas kolekcji i ich funkcje i charakterystyk wydajności, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="cpair_class"></a>  Klasa CRBTree::CPair

Klasa zawierająca elementy klucza i wartości.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Uwagi

Ta klasa jest używana przez metody [CRBTree::GetAt](#getat), [CRBTree::GetNext](#getnext), i [CRBTree::GetPrev](#getprev) do uzyskania dostępu do kluczy i wartości elementów przechowywanych w strukturze drzewa.

Elementy członkowskie są następujące:

|||
|-|-|
|`m_key`|Element członkowski danych, przechowywania klucza elementu.|
|`m_value`|Element członkowski danych, przechowywania element wartości.|

##  <a name="dtor"></a>  CRBTree:: ~ CRBTree

Destruktor.

```
~CRBTree() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie zasoby przydzielone. Wywołania [CRBTree::RemoveAll](#removeall) można usunąć wszystkich elementów.

##  <a name="findfirstkeyafter"></a>  CRBTree::FindFirstKeyAfter

Wywołaj tę metodę, aby znaleźć położenie elementu, który używa następny dostępny klucz.

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji elementu, który używa następny dostępny klucz. Jeśli nie ma elementów więcej, zwracana jest wartość NULL.

### <a name="remarks"></a>Uwagi

Ta metoda ułatwia przenoszenie drzewa bez konieczności wcześniejszego obliczania wartości pozycji.

##  <a name="getat"></a>  CRBTree::GetAt

Wywołaj tę metodę można pobrać elementu na określonej pozycji w drzewie.

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Wartość pozycji.

*Klucz*<br/>
Zmienna, która odbiera klucz.

*value*<br/>
Zmienna, która otrzymuje wartość.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwa formularze zwracają wskaźnik do [CPair](#cpair_class). Trzecia formą uzyskuje klucza i wartości dla danego stanowiska.

### <a name="remarks"></a>Uwagi

Wartość pozycji można wcześniej ustalić przy użyciu wywołania do metody, takie jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::GetTailPosition](#gettailposition).

W kompilacjach do debugowania błędu potwierdzenia wystąpi *pos* jest równa NULL.

##  <a name="getcount"></a>  CRBTree::GetCount

Wywołaj tę metodę, aby uzyskać liczbę elementów w drzewie.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów (każdej pary klucz/wartość jest jeden element) przechowywane w drzewie.

##  <a name="getheadposition"></a>  CRBTree::GetHeadPosition

Wywołaj tę metodę, aby uzyskać wartość pozycji dla elementu na główny drzewa.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji dla elementu na główny drzewa.

### <a name="remarks"></a>Uwagi

Wartość zwrócona przez obiekt `GetHeadPosition` mogą być używane z metodami takich jak [CRBTree::GetKeyAt](#getkeyat) lub [CRBTree::GetNext](#getnext) przechodzić przez drzewo i pobierać wartości.

##  <a name="getkeyat"></a>  CRBTree::GetKeyAt

Wywołaj tę metodę, aby uzyskać klucz z danej pozycji w drzewie.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Wartość pozycji.

### <a name="return-value"></a>Wartość zwracana

Zwraca klucz przechowywany w położeniu *pos* w drzewie.

### <a name="remarks"></a>Uwagi

Jeśli *pos* nie jest wartością poprawnej pozycji wyniki są nieprzewidywalne. W kompilacjach do debugowania błędu potwierdzenia wystąpi *pos* jest równa NULL.

##  <a name="getnext"></a>  CRBTree::GetNext

Wywołaj tę metodę, aby uzyskać wskaźnik do elementu przechowywanego w `CRBTree` obiektu, a następnie przejdź położenie do następnego elementu.

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie metody, takie jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do następnego [CPair](#cpair_class) wartość w drzewie.

### <a name="remarks"></a>Uwagi

*Pos* pozycji licznik jest aktualizowany po każdym wywołaniu. Jeśli pobrano element jest ostatni w drzewie *pos* ma wartość NULL.

##  <a name="getnextassoc"></a>  CRBTree::GetNextAssoc

Wywołanie tej metody, aby uzyskać klucz i wartość elementu przechowywanego w mapie, a następnie przejdź położenie do następnego elementu.

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie metody, takie jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*Klucz*<br/>
Parametr szablonu określający typ klucza drzewa.

*value*<br/>
Parametr szablonu określający typ wartości drzewa.

### <a name="remarks"></a>Uwagi

*Pos* pozycji licznik jest aktualizowany po każdym wywołaniu. Jeśli pobrano element jest ostatni w drzewie *pos* ma wartość NULL.

##  <a name="getnextkey"></a>  CRBTree::GetNextKey

Wywołaj tę metodę, aby pobrać klucz elementu przechowywanego w drzewie, a następnie przejdź położenie do następnego elementu.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie metody, takie jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do kluczowi w drzewie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżącej pozycji licznika, *pos*. Jeśli nie ma żadnych więcej wpisów w drzewie, licznik pozycja jest ustawiony na wartość NULL.

##  <a name="getnextvalue"></a>  CRBTree::GetNextValue

Wywołaj tę metodę, aby uzyskać wartość elementu przechowywanego w drzewie, a następnie przejdź położenie do następnego elementu.

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie metody, takie jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do następnej wartości, w drzewie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżącej pozycji licznika, *pos*. Jeśli nie ma żadnych więcej wpisów w drzewie, licznik pozycja jest ustawiony na wartość NULL.

##  <a name="getprev"></a>  CRBTree::GetPrev

Wywołaj tę metodę, aby uzyskać wskaźnik do elementu przechowywanego w `CRBTree` obiektu, a następnie zaktualizować pozycji do poprzedniego elementu.

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie metody, takie jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniego [CPair](#cpair_class) wartość przechowywaną w drzewie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżącej pozycji licznika, *pos*. Jeśli nie ma żadnych więcej wpisów w drzewie, licznik pozycja jest ustawiony na wartość NULL.

##  <a name="gettailposition"></a>  CRBTree::GetTailPosition

Wywołaj tę metodę, aby uzyskać wartość pozycji elementu w ogon drzewa.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji elementu w ogon drzewa.

### <a name="remarks"></a>Uwagi

Wartość zwrócona przez obiekt `GetTailPosition` mogą być używane z metodami takich jak [CRBTree::GetKeyAt](#getkeyat) lub [CRBTree::GetPrev](#getprev) przechodzić przez drzewo i pobierać wartości.

##  <a name="getvalueat"></a>  CRBTree::GetValueAt

Wywołaj tę metodę, aby pobrać wartość przechowywaną w określonej pozycji w `CRBTree` obiektu.

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie metody, takie jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wartość przechowywaną w danej pozycji w `CRBTree` obiektu.

##  <a name="isempty"></a>  CRBTree::IsEmpty

Wywołaj tę metodę do testowania dla obiektu pusty drzewa.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli drzewa jest pusta, wartość FALSE w przeciwnym razie.

##  <a name="kinargtype"></a>  CRBTree::KINARGTYPE

Typ używany, gdy klucz jest przekazywany jako argument wejściowy.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

##  <a name="koutargtype"></a>  CRBTree::KOUTARGTYPE

Typ używany, gdy klucz jest zwracany jako argument dane wyjściowe.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

##  <a name="removeall"></a>  CRBTree::RemoveAll

Wywołaj tę metodę, aby usunąć wszystkie elementy z `CRBTree` obiektu.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Uwagi

Czyści `CRBTree` obiektu, pamięć, używany do przechowywania elementów.

##  <a name="removeat"></a>  CRBTree::RemoveAt

Wywołanie tej metody, aby usunąć element w danej pozycji w `CRBTree` obiektu.

```
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie metody, takie jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="remarks"></a>Uwagi

Usuwa pary klucz/wartość przechowywaną w określonej pozycji. Pamięć używana do przechowywania elementu jest zwalniana. Odwołuje się do niego pozycja *pos* staje się nieprawidłowy, a gdy pozycji innych elementów w drzewie nadal jest ważna, niekoniecznie robią zachować takiej samej kolejności.

##  <a name="setvalueat"></a>  CRBTree::SetValueAt

Wywołaj tę metodę, aby zmienić wartość przechowywaną w określonej pozycji w `CRBTree` obiektu.

```
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Licznik pozycji, zwrócony przez poprzednie wywołanie metody, takie jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*value*<br/>
Wartość do dodania `CRBTree` obiektu.

### <a name="remarks"></a>Uwagi

Zmienia element wartości przechowywane w danej pozycji w `CRBTree` obiektu.

##  <a name="vinargtype"></a>  CRBTree::VINARGTYPE

Typ używany, gdy wartość jest przekazywany jako argument wejściowy.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

##  <a name="voutargtype"></a>  CRBTree::VOUTARGTYPE

Typ używany, gdy wartość jest przekazywany jako argument danych wyjściowych.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
