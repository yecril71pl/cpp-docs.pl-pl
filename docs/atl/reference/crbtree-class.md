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
ms.openlocfilehash: 58c001ccef35d4265ef5b7fe200654781f130872
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746580"
---
# <a name="crbtree-class"></a>Klasa CRBTree

Ta klasa zawiera metody tworzenia i korzystania z drzewa czerwono-czarne.

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

*KTraits ( ktraits )*<br/>
Kod używany do kopiowania lub przenoszenia elementów klucza. Zobacz [CElementTraits Klasy,](../../atl/reference/celementtraits-class.md) aby uzyskać więcej informacji.

*VTraits (Wyjęto)*<br/>
Kod używany do kopiowania lub przenoszenia elementów wartości.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CRBTree::KINARGTYPE](#kinargtype)|Typ używany, gdy klucz jest przekazywany jako argument wejściowy.|
|[CRBTree::KOUTARGTYPE](#koutargtype)|Typ używany, gdy klucz jest zwracany jako argument wyjściowy.|
|[CRBTree::VINARGTYPE](#vinargtype)|Typ używany, gdy wartość jest przekazywana jako argument wejściowy.|
|[CRBTree::VOUTARGTYPE](#voutargtype)|Typ używany, gdy wartość jest przekazywana jako argument danych wyjściowych.|

### <a name="public-classes"></a>Klasy publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBTree::CPair Klasa](#cpair_class)|Klasa zawierająca elementy klucza i wartości.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBTree::~CRBTree](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBTree::ZnajdźPotwierdzić](#findfirstkeyafter)|Wywołanie tej metody, aby znaleźć położenie elementu, który używa następnego dostępnego klucza.|
|[CRBTree::GetAt](#getat)|Wywołanie tej metody, aby uzyskać element w danej pozycji w drzewie.|
|[CRBTree::GetCount](#getcount)|Wywołanie tej metody, aby uzyskać liczbę elementów w drzewie.|
|[CRBTree::Pozycja nagłówka](#getheadposition)|Wywołanie tej metody, aby uzyskać wartość pozycji dla elementu na czele drzewa.|
|[CRBTree::GetKeyAt](#getkeyat)|Wywołanie tej metody, aby uzyskać klucz z danej pozycji w drzewie.|
|[CRBTree::PobierzNastęp](#getnext)|Wywołanie tej metody, aby uzyskać wskaźnik `CRBTree` do elementu przechowywanego w obiekcie i przejść pozycję do następnego elementu.|
|[CRBTree::GetNextAssoc](#getnextassoc)|Wywołanie tej metody, aby uzyskać klucz i wartość elementu przechowywane na mapie i przejść pozycję do następnego elementu.|
|[CRBTree::GetNextKey](#getnextkey)|Wywołanie tej metody, aby uzyskać klucz elementu przechowywane w drzewie i przejść do pozycji do następnego elementu.|
|[CRBTree::GetNextValue](#getnextvalue)|Wywołanie tej metody, aby uzyskać wartość elementu przechowywane w drzewie i przejść do pozycji do następnego elementu.|
|[CRBTree::GetPrev](#getprev)|Wywołanie tej metody, aby uzyskać wskaźnik `CRBTree` do elementu przechowywanego w obiekcie, a następnie zaktualizować położenie do poprzedniego elementu.|
|[CRBTree::Pozycja GetTail](#gettailposition)|Wywołanie tej metody, aby uzyskać wartość położenia dla elementu w ogonie drzewa.|
|[CRBTree::GetValueAt](#getvalueat)|Wywołanie tej metody, aby pobrać wartość przechowywaną w danej pozycji w `CRBTree` obiekcie.|
|[CRBTree::IsEmpty](#isempty)|Wywołanie tej metody, aby przetestować dla pustego obiektu drzewa.|
|[CRBTree::Usuńwszywszystki](#removeall)|Wywołanie tej metody, aby `CRBTree` usunąć wszystkie elementy z obiektu.|
|[CRBTree::Usuń](#removeat)|Wywołanie tej metody, aby usunąć element `CRBTree` w danej pozycji w obiekcie.|
|[CRBTree::SetValueAt](#setvalueat)|Wywołanie tej metody, aby zmienić wartość `CRBTree` przechowywaną w danej pozycji w obiekcie.|

## <a name="remarks"></a>Uwagi

Drzewo czerwono-czarne to binarne drzewo wyszukiwania, które używa dodatkowego bitu informacji na węzeł, aby upewnić się, że pozostaje "zrównoważone", to znaczy, że wysokość drzewa nie rośnie nieproporcjonalnie duża i wpływa na wydajność.

Ta klasa szablonu jest przeznaczona do użycia przez [CRBMap](../../atl/reference/crbmap-class.md) i [CRBMultiMap](../../atl/reference/crbmultimap-class.md). Większość metod, które składają się na te `CRBTree`klasy pochodne są dostarczane przez .

Aby uzyskać pełniejszą dyskusję na temat różnych klas kolekcji oraz ich cech i cech wydajności, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="crbtreecpair-class"></a><a name="cpair_class"></a>CRBTree::CPair Klasa

Klasa zawierająca elementy klucza i wartości.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Uwagi

Ta klasa jest używana przez metody [CRBTree::GetAt](#getat), [CRBTree::GetNext](#getnext)i [CRBTree::GetPrev,](#getprev) aby uzyskać dostęp do elementów klucza i wartości przechowywanych w strukturze drzewa.

Członkowie są następujące:

|||
|-|-|
|`m_key`|Element członkowski danych przechowujący element klucza.|
|`m_value`|Element członkowski danych przechowujący element wartości.|

## <a name="crbtreecrbtree"></a><a name="dtor"></a>CRBTree::~CRBTree

Destruktor.

```
~CRBTree() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby. Wywołuje [CRBTree::RemoveAll,](#removeall) aby usunąć wszystkie elementy.

## <a name="crbtreefindfirstkeyafter"></a><a name="findfirstkeyafter"></a>CRBTree::ZnajdźPotwierdzić

Wywołanie tej metody, aby znaleźć położenie elementu, który używa następnego dostępnego klucza.

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Wartość klucza.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji elementu, który używa następnego dostępnego klucza. Jeśli nie ma więcej elementów, null jest zwracany.

### <a name="remarks"></a>Uwagi

Ta metoda ułatwia przechodzenie przez drzewo bez konieczności wcześniejszego obliczania wartości położenia.

## <a name="crbtreegetat"></a><a name="getat"></a>CRBTree::GetAt

Wywołanie tej metody, aby uzyskać element w danej pozycji w drzewie.

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Wartość pozycji.

*key*<br/>
Zmienna, która odbiera klucz.

*value*<br/>
Zmienna, która odbiera wartość.

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwa formularze zwracają wskaźnik do [CPair](#cpair_class). Trzeci formularz uzyskuje klucz i wartość dla danej pozycji.

### <a name="remarks"></a>Uwagi

Wartość pozycji można wcześniej określić za pomocą wywołania metody, takiej jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::GetTailPosition](#gettailposition).

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *pos* jest równa NULL.

## <a name="crbtreegetcount"></a><a name="getcount"></a>CRBTree::GetCount

Wywołanie tej metody, aby uzyskać liczbę elementów w drzewie.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów (każda para klucz/wartość jest jednym elementem) przechowywana w drzewie.

## <a name="crbtreegetheadposition"></a><a name="getheadposition"></a>CRBTree::Pozycja nagłówka

Wywołanie tej metody, aby uzyskać wartość pozycji dla elementu na czele drzewa.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pozycji elementu na czele drzewa.

### <a name="remarks"></a>Uwagi

Wartość zwracana `GetHeadPosition` przez może służyć z metod, takich jak [CRBTree::GetKeyAt](#getkeyat) lub [CRBTree::GetNext](#getnext) do przechodzenia przez drzewo i pobrać wartości.

## <a name="crbtreegetkeyat"></a><a name="getkeyat"></a>CRBTree::GetKeyAt

Wywołanie tej metody, aby uzyskać klucz z danej pozycji w drzewie.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Wartość pozycji.

### <a name="return-value"></a>Wartość zwracana

Zwraca klucz przechowywany w pozycji *poz* w drzewie.

### <a name="remarks"></a>Uwagi

Jeśli *pos* nie jest prawidłową wartością pozycji, wyniki są nieprzewidywalne. W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *pos* jest równa NULL.

## <a name="crbtreegetnext"></a><a name="getnext"></a>CRBTree::PobierzNastęp

Wywołanie tej metody, aby uzyskać wskaźnik `CRBTree` do elementu przechowywanego w obiekcie i przejść pozycję do następnego elementu.

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwracany przez poprzednie wywołanie metod, takich jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do następnej wartości [CPair](#cpair_class) w drzewie.

### <a name="remarks"></a>Uwagi

Licznik pozycji *poz* jest aktualizowany po każdym wywołaniu. Jeśli pobrany element jest ostatnim w drzewie, pos jest *ustawiona* na NULL.

## <a name="crbtreegetnextassoc"></a><a name="getnextassoc"></a>CRBTree::GetNextAssoc

Wywołanie tej metody, aby uzyskać klucz i wartość elementu przechowywane na mapie i przejść pozycję do następnego elementu.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwracany przez poprzednie wywołanie metod, takich jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*key*<br/>
Parametr szablonu określający typ klucza drzewa.

*value*<br/>
Parametr szablonu określający typ wartości drzewa.

### <a name="remarks"></a>Uwagi

Licznik pozycji *poz* jest aktualizowany po każdym wywołaniu. Jeśli pobrany element jest ostatnim w drzewie, pos jest *ustawiona* na NULL.

## <a name="crbtreegetnextkey"></a><a name="getnextkey"></a>CRBTree::GetNextKey

Wywołanie tej metody, aby uzyskać klucz elementu przechowywane w drzewie i przejść do pozycji do następnego elementu.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwracany przez poprzednie wywołanie metod, takich jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do następnego klucza w drzewie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżący licznik pozycji, *poz*. Jeśli w drzewie nie ma więcej wpisów, licznik pozycji jest ustawiony na wartość NULL.

## <a name="crbtreegetnextvalue"></a><a name="getnextvalue"></a>CRBTree::GetNextValue

Wywołanie tej metody, aby uzyskać wartość elementu przechowywane w drzewie i przejść do pozycji do następnego elementu.

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwracany przez poprzednie wywołanie metod, takich jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do następnej wartości w drzewie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżący licznik pozycji, *poz*. Jeśli w drzewie nie ma więcej wpisów, licznik pozycji jest ustawiony na wartość NULL.

## <a name="crbtreegetprev"></a><a name="getprev"></a>CRBTree::GetPrev

Wywołanie tej metody, aby uzyskać wskaźnik `CRBTree` do elementu przechowywanego w obiekcie, a następnie zaktualizować położenie do poprzedniego elementu.

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwracany przez poprzednie wywołanie metod, takich jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniej wartości [CPair](#cpair_class) przechowywanej w drzewie.

### <a name="remarks"></a>Uwagi

Aktualizuje bieżący licznik pozycji, *poz*. Jeśli w drzewie nie ma więcej wpisów, licznik pozycji jest ustawiony na wartość NULL.

## <a name="crbtreegettailposition"></a><a name="gettailposition"></a>CRBTree::Pozycja GetTail

Wywołanie tej metody, aby uzyskać wartość położenia dla elementu w ogonie drzewa.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość położenia elementu w ogonie drzewa.

### <a name="remarks"></a>Uwagi

Wartość zwracana `GetTailPosition` przez może służyć z metod, takich jak [CRBTree::GetKeyAt](#getkeyat) lub [CRBTree::GetPrev](#getprev) do przechodzenia przez drzewo i pobrać wartości.

## <a name="crbtreegetvalueat"></a><a name="getvalueat"></a>CRBTree::GetValueAt

Wywołanie tej metody, aby pobrać wartość przechowywaną w danej pozycji w `CRBTree` obiekcie.

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwracany przez poprzednie wywołanie metod, takich jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wartości przechowywanej w `CRBTree` danej pozycji w obiekcie.

## <a name="crbtreeisempty"></a><a name="isempty"></a>CRBTree::IsEmpty

Wywołanie tej metody, aby przetestować dla pustego obiektu drzewa.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli drzewo jest puste, w przeciwnym razie wartość FAŁSZ.

## <a name="crbtreekinargtype"></a><a name="kinargtype"></a>CRBTree::KINARGTYPE

Typ używany, gdy klucz jest przekazywany jako argument wejściowy.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="crbtreekoutargtype"></a><a name="koutargtype"></a>CRBTree::KOUTARGTYPE

Typ używany, gdy klucz jest zwracany jako argument wyjściowy.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="crbtreeremoveall"></a><a name="removeall"></a>CRBTree::Usuńwszywszystki

Wywołanie tej metody, aby `CRBTree` usunąć wszystkie elementy z obiektu.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Uwagi

Czyści `CRBTree` obiekt, zwalniając pamięć używaną do przechowywania elementów.

## <a name="crbtreeremoveat"></a><a name="removeat"></a>CRBTree::Usuń

Wywołanie tej metody, aby usunąć element `CRBTree` w danej pozycji w obiekcie.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwracany przez poprzednie wywołanie metod, takich jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="remarks"></a>Uwagi

Usuwa parę klucz/wartość przechowywaną w określonym położeniu. Pamięć używana do przechowywania elementu jest zwalniana. Pozycja, do której odwołuje *się poz,* staje się nieprawidłowa i chociaż pozycja innych elementów w drzewie pozostaje prawidłowa, nie muszą one zachowywać tej samej kolejności.

## <a name="crbtreesetvalueat"></a><a name="setvalueat"></a>CRBTree::SetValueAt

Wywołanie tej metody, aby zmienić wartość `CRBTree` przechowywaną w danej pozycji w obiekcie.

```cpp
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Licznik pozycji, zwracany przez poprzednie wywołanie metod, takich jak [CRBTree::GetHeadPosition](#getheadposition) lub [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*value*<br/>
Wartość dodana do `CRBTree` obiektu.

### <a name="remarks"></a>Uwagi

Zmienia element wartości przechowywany w danej `CRBTree` pozycji w obiekcie.

## <a name="crbtreevinargtype"></a><a name="vinargtype"></a>CRBTree::VINARGTYPE

Typ używany, gdy wartość jest przekazywana jako argument wejściowy.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="crbtreevoutargtype"></a><a name="voutargtype"></a>CRBTree::VOUTARGTYPE

Typ używany, gdy wartość jest przekazywana jako argument danych wyjściowych.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
