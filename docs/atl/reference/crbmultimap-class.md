---
title: Klasa CRBMultiMap
ms.date: 11/04/2016
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
helpviewer_keywords:
- CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
ms.openlocfilehash: 1e36bc267b3a539d2d1d4bf370b9cdc33828c760
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331423"
---
# <a name="crbmultimap-class"></a>Klasa CRBMultiMap

Ta klasa reprezentuje strukturę mapowania, która umożliwia każdy klucz może być skojarzony z więcej niż jedną wartość, przy użyciu drzewa binarnego Red-Black.

## <a name="syntax"></a>Składnia

```
template<typename K,
         typename V,
         class KTraits = CElementTraits<K>,
         class VTraits = CElementTraits<V>>
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
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

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|Konstruktor.|
|[CRBMultiMap::~CRBMultiMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBMultiMap::Znajdź Powierze Z kluczem](#findfirstwithkey)|Wywołanie tej metody, aby znaleźć położenie pierwszego elementu z danym kluczem.|
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|Wywołanie tej metody, aby uzyskać wartość skojarzoną z danym kluczem i zaktualizować wartość pozycji.|
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|Wywołanie tej metody, aby uzyskać element skojarzony z danym kluczem i zaktualizować wartość pozycji.|
|[CRBMultiMap::Wstaw](#insert)|Wywołanie tej metody, aby wstawić parę elementów do mapy.|
|[CRBMultiMap::RemoveKey](#removekey)|Wywołanie tej metody, aby usunąć wszystkie elementy klucz/wartość dla danego klucza.|

## <a name="remarks"></a>Uwagi

`CRBMultiMap`zapewnia obsługę tablicy mapowania dowolnego typu, zarządzając uporządkowaną tablicą kluczowych elementów i wartości. W przeciwieństwie do [klasy CRBMap,](../../atl/reference/crbmap-class.md) każdy klucz może być skojarzony z więcej niż jedną wartością.

Elementy (składające się z klucza i wartości) są przechowywane w strukturze drzewa binarnego, przy użyciu [METODY CRBMultiMap::Insert.](#insert) Elementy można usunąć za pomocą [METODY CRBMultiMap::RemoveKey,](#removekey) która usuwa wszystkie elementy, które pasują do danego klucza.

Przechodzenie przez drzewo jest możliwe dzięki metodom takim jak [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)i [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue). Dostęp do potencjalnie wielu wartości na klucz jest możliwy przy użyciu [metod CRBMultiMap::FindFirstWithKey](#findfirstwithkey), [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)i [CRBMultiMap::GetNextWithKey.](#getnextwithkey) Zobacz przykład [dla CRBMultiMap::CRBMultiMap](#crbmultimap) na ilustrację tego w praktyce.

*Parametry KTraits* i *VTraits* są klasami cech, które zawierają dowolny kod uzupełniający potrzebny do kopiowania lub przenoszenia elementów.

`CRBMultiMap`pochodzi z [CRBTree](../../atl/reference/crbtree-class.md), który implementuje drzewa binarnego przy użyciu algorytmu Red-Black. Alternatywa `CRBMultiMap` dla `CRBMap` i jest oferowana przez [CAtlMap](../../atl/reference/catlmap-class.md) klasy. Gdy tylko niewielka liczba elementów musi być przechowywana, należy rozważyć użycie [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy zamiast.

Aby uzyskać pełniejszą dyskusję na temat różnych klas kolekcji oraz ich cech i cech wydajności, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Crbtree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="crbmultimapcrbmultimap"></a><a name="crbmultimap"></a>CRBMultiMap::CRBMultiMap

Konstruktor.

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize (Rozmiar)*<br/>
Rozmiar bloku.

### <a name="remarks"></a>Uwagi

Parametr *nBlockSize* jest miarą ilości przydzielonej pamięci, gdy wymagany jest nowy element. Większe rozmiary bloków zmniejszają liczbę wywołań procedur alokacji pamięci, ale zużywają więcej zasobów. Wartość domyślna będzie przydzielać miejsce dla 10 elementów naraz.

Zobacz dokumentację dla klasy podstawowej [CRBTree, aby](../../atl/reference/crbtree-class.md) uzyskać informacje na temat innych dostępnych metod.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

## <a name="crbmultimapcrbmultimap"></a><a name="dtor"></a>CRBMultiMap::~CRBMultiMap

Destruktor.

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

Zobacz dokumentację dla klasy podstawowej [CRBTree, aby](../../atl/reference/crbtree-class.md) uzyskać informacje na temat innych dostępnych metod.

## <a name="crbmultimapfindfirstwithkey"></a><a name="findfirstwithkey"></a>CRBMultiMap::Znajdź Powierze Z kluczem

Wywołanie tej metody, aby znaleźć położenie pierwszego elementu z danym kluczem.

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Określa klucz, który identyfikuje element, który ma zostać znaleziony.

### <a name="return-value"></a>Wartość zwracana

Zwraca położenie pierwszego klucza/elementu wartości, jeśli zostanie znaleziony klucz, NULL inaczej.

### <a name="remarks"></a>Uwagi

Klucz w `CRBMultiMap` może mieć jedną lub więcej skojarzonych wartości. Ta metoda zapewni wartość pozycji pierwszej wartości (która w rzeczywistości może być jedyną wartością) skojarzoną z tym kluczem. Zwrócona wartość pozycji może być następnie użyta z [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey) lub [CRBMultiMap::GetNextWithKey](#getnextwithkey) w celu uzyskania wartości i aktualizacji pozycji.

Zobacz dokumentację dla klasy podstawowej [CRBTree, aby](../../atl/reference/crbtree-class.md) uzyskać informacje na temat innych dostępnych metod.

### <a name="example"></a>Przykład

Zobacz przykład [dla CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapgetnextvaluewithkey"></a><a name="getnextvaluewithkey"></a>CRBMultiMap::GetNextValueWithKey

Wywołanie tej metody, aby uzyskać wartość skojarzoną z danym kluczem i zaktualizować wartość pozycji.

```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Wartość pozycji uzyskana za pomocą wywołania [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) lub [CRBMultiMap::GetNextWithKey](#getnextwithkey) `GetNextValueWithKey`lub poprzedniego wywołania do .

*key*<br/>
Określa klucz, który identyfikuje element, który ma zostać znaleziony.

### <a name="return-value"></a>Wartość zwracana

Zwraca parę elementów skojarzoną z danym kluczem.

### <a name="remarks"></a>Uwagi

Wartość pozycji jest aktualizowana w celu wskazanie następnej wartości skojarzonej z kluczem. Jeśli nie ma więcej wartości, wartość pozycji jest ustawiona na WARTOŚĆ NULL.

Zobacz dokumentację dla klasy podstawowej [CRBTree, aby](../../atl/reference/crbtree-class.md) uzyskać informacje na temat innych dostępnych metod.

### <a name="example"></a>Przykład

Zobacz przykład [dla CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapgetnextwithkey"></a><a name="getnextwithkey"></a>CRBMultiMap::GetNextWithKey

Wywołanie tej metody, aby uzyskać element skojarzony z danym kluczem i zaktualizować wartość pozycji.

```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*Poz*<br/>
Wartość pozycji uzyskana za pomocą wywołania [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) lub [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey) `GetNextWithKey`lub poprzedniego wywołania do .

*key*<br/>
Określa klucz, który identyfikuje element, który ma zostać znaleziony.

### <a name="return-value"></a>Wartość zwracana

Zwraca następny [element CRBTree::CPair Class](crbtree-class.md#cpair_class) skojarzony z danym kluczem.

### <a name="remarks"></a>Uwagi

Wartość pozycji jest aktualizowana w celu wskazanie następnej wartości skojarzonej z kluczem. Jeśli nie ma więcej wartości, wartość pozycji jest ustawiona na WARTOŚĆ NULL.

Zobacz dokumentację dla klasy podstawowej [CRBTree, aby](../../atl/reference/crbtree-class.md) uzyskać informacje na temat innych dostępnych metod.

## <a name="crbmultimapinsert"></a><a name="insert"></a>CRBMultiMap::Wstaw

Wywołanie tej metody, aby wstawić parę elementów do mapy.

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Wartość klucza, aby `CRBMultiMap` dodać do obiektu.

*value*<br/>
Wartość dodana do `CRBMultiMap` obiektu skojarzona z *kluczem*.

### <a name="return-value"></a>Wartość zwracana

Zwraca położenie pary elementu klucz/wartość `CRBMultiMap` w obiekcie.

### <a name="remarks"></a>Uwagi

Zobacz dokumentację dla klasy podstawowej [CRBTree, aby](../../atl/reference/crbtree-class.md) uzyskać informacje na temat innych dostępnych metod.

### <a name="example"></a>Przykład

Zobacz przykład [dla CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapremovekey"></a><a name="removekey"></a>CRBMultiMap::RemoveKey

Wywołanie tej metody, aby usunąć wszystkie elementy klucz/wartość dla danego klucza.

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Określa klucz identyfikujący elementy, które mają zostać usunięte.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wartości skojarzonych z danym kluczem.

### <a name="remarks"></a>Uwagi

`RemoveKey`usuwa wszystkie elementy klucza/wartości, które mają klucz odpowiadający *kluczowi*.

Zobacz dokumentację dla klasy podstawowej [CRBTree, aby](../../atl/reference/crbtree-class.md) uzyskać informacje na temat innych dostępnych metod.

### <a name="example"></a>Przykład

Zobacz przykład [dla CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="see-also"></a>Zobacz też

[Klasa CRBTree](../../atl/reference/crbtree-class.md)<br/>
[Klasa CAtlMap](../../atl/reference/catlmap-class.md)<br/>
[Klasa CRBMap](../../atl/reference/crbmap-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
