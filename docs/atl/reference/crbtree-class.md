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
ms.openlocfilehash: 7b8e47b5cd0ac278711947abc867956333371be3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833494"
---
# <a name="crbtree-class"></a>Klasa CRBTree

Ta klasa zawiera metody tworzenia i używania czarnego drzewa.

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
|[CRBTree::KINARGTYPE](#kinargtype)|Typ używany, gdy klucz jest przesyłany jako argument wejściowy.|
|[CRBTree::KOUTARGTYPE](#koutargtype)|Typ używany, gdy klucz jest zwracany jako argument wyjściowy.|
|[CRBTree::VINARGTYPE](#vinargtype)|Typ używany, gdy wartość jest przenoszona jako argument wejściowy.|
|[CRBTree::VOUTARGTYPE](#voutargtype)|Typ używany, gdy wartość jest przenoszona jako argument wyjściowy.|

### <a name="public-classes"></a>Klasy publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBTree:: CPair, Klasa](#cpair_class)|Klasa zawierająca elementy klucza i wartości.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBTree:: ~ CRBTree](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|Wywołaj tę metodę, aby znaleźć pozycję elementu, który używa następnego dostępnego klucza.|
|[CRBTree::GetAt](#getat)|Wywołaj tę metodę, aby pobrać element z danego położenia w drzewie.|
|[CRBTree:: GetCount](#getcount)|Wywołaj tę metodę, aby uzyskać liczbę elementów w drzewie.|
|[CRBTree::GetHeadPosition](#getheadposition)|Wywołaj tę metodę, aby uzyskać wartość pozycji dla elementu w nagłówku drzewa.|
|[CRBTree::GetKeyAt](#getkeyat)|Wywołaj tę metodę, aby pobrać klucz z danego położenia w drzewie.|
|[CRBTree:: GetNext](#getnext)|Wywołaj tę metodę, aby uzyskać wskaźnik do elementu przechowywanego w `CRBTree` obiekcie, i przejdź do następnego elementu.|
|[CRBTree::GetNextAssoc](#getnextassoc)|Wywołaj tę metodę, aby uzyskać klucz i wartość elementu przechowywanego na mapie, a następnie przejdź do następnego elementu.|
|[CRBTree::GetNextKey](#getnextkey)|Wywołaj tę metodę, aby uzyskać klucz elementu przechowywanego w drzewie i przejdź do następnego elementu.|
|[CRBTree::GetNextValue](#getnextvalue)|Wywołaj tę metodę, aby pobrać wartość elementu przechowywanego w drzewie i przejdź do następnego elementu.|
|[CRBTree:: getpoprz](#getprev)|Wywołaj tę metodę, aby uzyskać wskaźnik do elementu przechowywanego w `CRBTree` obiekcie, a następnie zaktualizuj pozycję do poprzedniego elementu.|
|[CRBTree::GetTailPosition](#gettailposition)|Wywołaj tę metodę, aby uzyskać wartość pozycji dla elementu na końcu drzewa.|
|[CRBTree::GetValueAt](#getvalueat)|Wywołaj tę metodę, aby pobrać wartość przechowywaną w danej pozycji w `CRBTree` obiekcie.|
|[CRBTree:: IsEmpty](#isempty)|Wywołaj tę metodę, aby przetestować dla pustego obiektu drzewa.|
|[CRBTree::](#removeall)|Wywołaj tę metodę, aby usunąć wszystkie elementy z `CRBTree` obiektu.|
|[CRBTree::RemoveAt](#removeat)|Wywołaj tę metodę, aby usunąć element z danego położenia w `CRBTree` obiekcie.|
|[CRBTree::SetValueAt](#setvalueat)|Wywołaj tę metodę, aby zmienić wartość przechowywaną w danej pozycji w `CRBTree` obiekcie.|

## <a name="remarks"></a>Uwagi

Drzewo z czerwonym czarnym jest drzewem wyszukiwania binarnego, które używa dodatkowej ilości informacji na węzeł, aby upewnić się, że pozostaje "Zrównoważona", czyli wysokość drzewa nie rośnie proporcjonalnie do wydajności.

Ta klasa szablonu została zaprojektowana tak, aby była używana przez [CRBMap](../../atl/reference/crbmap-class.md) i [CRBMultiMap](../../atl/reference/crbmultimap-class.md). Większość metod, które składają się na te klasy pochodne, jest udostępnianych przez `CRBTree` .

Dokładniejsze Omówienie różnych klas kolekcji i ich funkcji oraz charakterystyki wydajności znajdują się w temacie [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll. h

## <a name="crbtreecpair-class"></a><a name="cpair_class"></a> CRBTree:: CPair, Klasa

Klasa zawierająca elementy klucza i wartości.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Uwagi

Ta klasa jest używana przez metody [CRBTree:: GetAt](#getat), [CRBTree:: GetNext](#getnext)i [CRBTree:: getpoprz](#getprev) , aby uzyskać dostęp do elementów klucza i wartości przechowywanych w strukturze drzewa.

Elementy członkowskie są następujące:

|Element członkowski danych|Opis|
|-|-|
|`m_key`|Element członkowski danych przechowujący element klucza.|
|`m_value`|Element członkowski danych przechowujący element Value.|

## <a name="crbtreecrbtree"></a><a name="dtor"></a> CRBTree:: ~ CRBTree

Destruktor.

```
~CRBTree() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby. Wywołuje [CRBTree::](#removeall) Usuń wszystkie elementy.

## <a name="crbtreefindfirstkeyafter"></a><a name="findfirstkeyafter"></a> CRBTree::FindFirstKeyAfter

Wywołaj tę metodę, aby znaleźć pozycję elementu, który używa następnego dostępnego klucza.

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Wartość klucza.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji elementu, który używa następnego dostępnego klucza. Jeśli nie ma więcej elementów, zwracana jest wartość NULL.

### <a name="remarks"></a>Uwagi

Ta metoda ułatwia przechodzenie drzewa bez konieczności wcześniejszego obliczania wartości pozycji.

## <a name="crbtreegetat"></a><a name="getat"></a> CRBTree::GetAt

Wywołaj tę metodę, aby pobrać element z danego położenia w drzewie.

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Wartość pozycji.

*głównych*<br/>
Zmienna, która otrzymuje klucz.

*wartościami*<br/>
Zmienna, która otrzymuje wartość.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwa formularze zwracają wskaźnik do [CPair](#cpair_class). Trzeci formularz uzyskuje klucz i wartość dla danego położenia.

### <a name="remarks"></a>Uwagi

Wartość pozycji można wcześniej określić za pomocą wywołania metody, takiej jak [CRBTree:: GetHeadPosition](#getheadposition) lub [CRBTree:: GetTailPosition](#gettailposition).

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli wartość *pos* będzie równa null.

## <a name="crbtreegetcount"></a><a name="getcount"></a> CRBTree:: GetCount

Wywołaj tę metodę, aby uzyskać liczbę elementów w drzewie.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów (każda para klucz/wartość jest jednym elementem) przechowywaną w drzewie.

## <a name="crbtreegetheadposition"></a><a name="getheadposition"></a> CRBTree::GetHeadPosition

Wywołaj tę metodę, aby uzyskać wartość pozycji dla elementu w nagłówku drzewa.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji dla elementu w nagłówku drzewa.

### <a name="remarks"></a>Uwagi

Wartość zwrócona przez `GetHeadPosition` może być używana z metodami takimi jak [CRBTree:: GetKeyAt](#getkeyat) lub [CRBTree:: GetNext](#getnext) w celu przechodzenia przez drzewo i pobierania wartości.

## <a name="crbtreegetkeyat"></a><a name="getkeyat"></a> CRBTree::GetKeyAt

Wywołaj tę metodę, aby pobrać klucz z danego położenia w drzewie.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Wartość pozycji.

### <a name="return-value"></a>Wartość zwracana

Zwraca klucz przechowywany w pozycji *pos* w drzewie.

### <a name="remarks"></a>Uwagi

Jeśli *punkt sprzedaży* nie jest prawidłową wartością pozycji, wyniki są nieprzewidywalne. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli wartość *pos* będzie równa null.

## <a name="crbtreegetnext"></a><a name="getnext"></a> CRBTree:: GetNext

Wywołaj tę metodę, aby uzyskać wskaźnik do elementu przechowywanego w `CRBTree` obiekcie, i przejdź do następnego elementu.

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie metod, takich jak [CRBTree:: GetHeadPosition](#getheadposition) lub [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do następnej wartości [CPair](#cpair_class) w drzewie.

### <a name="remarks"></a>Uwagi

Po każdym wywołaniu zostanie zaktualizowany licznik pozycji *punktu sprzedaży* . Jeśli pobrany element jest ostatnim w drzewie, *pos* ma USTAWIONĄ wartość null.

## <a name="crbtreegetnextassoc"></a><a name="getnextassoc"></a> CRBTree::GetNextAssoc

Wywołaj tę metodę, aby uzyskać klucz i wartość elementu przechowywanego na mapie, a następnie przejdź do następnego elementu.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie metod, takich jak [CRBTree:: GetHeadPosition](#getheadposition) lub [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter).

*głównych*<br/>
Parametr szablonu określający typ klucza drzewa.

*wartościami*<br/>
Parametr szablonu określający typ wartości drzewa.

### <a name="remarks"></a>Uwagi

Po każdym wywołaniu zostanie zaktualizowany licznik pozycji *punktu sprzedaży* . Jeśli pobrany element jest ostatnim w drzewie, *pos* ma USTAWIONĄ wartość null.

## <a name="crbtreegetnextkey"></a><a name="getnextkey"></a> CRBTree::GetNextKey

Wywołaj tę metodę, aby uzyskać klucz elementu przechowywanego w drzewie i przejdź do następnego elementu.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie metod, takich jak [CRBTree:: GetHeadPosition](#getheadposition) lub [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do następnego klawisza w drzewie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżący licznik pozycji w *punkcie sprzedaży*. Jeśli w drzewie nie ma więcej wpisów, licznik pozycji ma wartość NULL.

## <a name="crbtreegetnextvalue"></a><a name="getnextvalue"></a> CRBTree::GetNextValue

Wywołaj tę metodę, aby pobrać wartość elementu przechowywanego w drzewie i przejdź do następnego elementu.

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie metod, takich jak [CRBTree:: GetHeadPosition](#getheadposition) lub [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do następnej wartości w drzewie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżący licznik pozycji w *punkcie sprzedaży*. Jeśli w drzewie nie ma więcej wpisów, licznik pozycji ma wartość NULL.

## <a name="crbtreegetprev"></a><a name="getprev"></a> CRBTree:: getpoprz

Wywołaj tę metodę, aby uzyskać wskaźnik do elementu przechowywanego w `CRBTree` obiekcie, a następnie zaktualizuj pozycję do poprzedniego elementu.

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie metod, takich jak [CRBTree:: GetHeadPosition](#getheadposition) lub [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniej wartości [CPair](#cpair_class) przechowywanej w drzewie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżący licznik pozycji w *punkcie sprzedaży*. Jeśli w drzewie nie ma więcej wpisów, licznik pozycji ma wartość NULL.

## <a name="crbtreegettailposition"></a><a name="gettailposition"></a> CRBTree::GetTailPosition

Wywołaj tę metodę, aby uzyskać wartość pozycji dla elementu na końcu drzewa.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji dla elementu na końcu drzewa.

### <a name="remarks"></a>Uwagi

Wartość zwrócona przez `GetTailPosition` może być używana z metodami takimi jak [CRBTree:: GetKeyAt](#getkeyat) lub [CRBTree:: getpoprz](#getprev) w celu przechodzenia przez drzewo i pobierania wartości.

## <a name="crbtreegetvalueat"></a><a name="getvalueat"></a> CRBTree::GetValueAt

Wywołaj tę metodę, aby pobrać wartość przechowywaną w danej pozycji w `CRBTree` obiekcie.

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie metod, takich jak [CRBTree:: GetHeadPosition](#getheadposition) lub [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wartości przechowywanej w danej pozycji w `CRBTree` obiekcie.

## <a name="crbtreeisempty"></a><a name="isempty"></a> CRBTree:: IsEmpty

Wywołaj tę metodę, aby przetestować dla pustego obiektu drzewa.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli drzewo jest puste, w przeciwnym razie FALSE.

## <a name="crbtreekinargtype"></a><a name="kinargtype"></a> CRBTree::KINARGTYPE

Typ używany, gdy klucz jest przesyłany jako argument wejściowy.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="crbtreekoutargtype"></a><a name="koutargtype"></a> CRBTree::KOUTARGTYPE

Typ używany, gdy klucz jest zwracany jako argument wyjściowy.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="crbtreeremoveall"></a><a name="removeall"></a> CRBTree::

Wywołaj tę metodę, aby usunąć wszystkie elementy z `CRBTree` obiektu.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Uwagi

Czyści `CRBTree` obiekt, zwalniając pamięć używaną do przechowywania elementów.

## <a name="crbtreeremoveat"></a><a name="removeat"></a> CRBTree::RemoveAt

Wywołaj tę metodę, aby usunąć element z danego położenia w `CRBTree` obiekcie.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie metod, takich jak [CRBTree:: GetHeadPosition](#getheadposition) lub [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter).

### <a name="remarks"></a>Uwagi

Usuwa pary klucz/wartość przechowywane w określonej pozycji. Pamięć użyta do przechowywania elementu jest zwolniona. POZYCJA, do której odwołuje się *punkt sprzedaży* , jest nieprawidłowa, a mimo że pozycja innych elementów w drzewie pozostaje ważna, niekoniecznie nie zachowują się one w tej samej kolejności.

## <a name="crbtreesetvalueat"></a><a name="setvalueat"></a> CRBTree::SetValueAt

Wywołaj tę metodę, aby zmienić wartość przechowywaną w danej pozycji w `CRBTree` obiekcie.

```cpp
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*Terminal*<br/>
Licznik pozycji zwrócony przez poprzednie wywołanie metod, takich jak [CRBTree:: GetHeadPosition](#getheadposition) lub [CRBTree:: FindFirstKeyAfter](#findfirstkeyafter).

*wartościami*<br/>
Wartość, która ma zostać dodana do `CRBTree` obiektu.

### <a name="remarks"></a>Uwagi

Zmienia element wartości przechowywany w danej pozycji w `CRBTree` obiekcie.

## <a name="crbtreevinargtype"></a><a name="vinargtype"></a> CRBTree::VINARGTYPE

Typ używany, gdy wartość jest przenoszona jako argument wejściowy.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="crbtreevoutargtype"></a><a name="voutargtype"></a> CRBTree::VOUTARGTYPE

Typ używany, gdy wartość jest przenoszona jako argument wyjściowy.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
