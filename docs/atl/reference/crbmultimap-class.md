---
title: Klasa CRBMultiMap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
dev_langs:
- C++
helpviewer_keywords:
- CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae9a83ff8cc8e4909e23e7751e0c82da690a0c21
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093821"
---
# <a name="crbmultimap-class"></a>Klasa CRBMultiMap

Ta klasa reprezentuje strukturę mapowania, która umożliwia każdy klucz może być skojarzony z więcej niż jedną wartość, przy użyciu drzewa binarnego Red czarny.

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
Typ klucza elementu.

*V*<br/>
Typ elementu wartości.

*KTraits*<br/>
Kod używany, aby skopiować lub przenieść kluczowe elementy. Zobacz [klasa CElementTraits](../../atl/reference/celementtraits-class.md) Aby uzyskać więcej informacji.

*VTraits*<br/>
Kod używany do kopiowania lub przenoszenia elementów wartości.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|Konstruktor.|
|[CRBMultiMap:: ~ CRBMultiMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|Wywołaj tę metodę, aby znaleźć położenie pierwszego elementu z danym kluczem.|
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|Wywołanie tej metody można pobrać wartość skojarzoną z danym kluczem, a następnie zaktualizuj wartość pozycji.|
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|Wywołaj tę metodę, aby pobrać element skojarzony z danym kluczem i zaktualizuj wartość pozycji.|
|[CRBMultiMap::Insert](#insert)|Wywołaj tę metodę, aby wstawić para elementów do mapy.|
|[CRBMultiMap::RemoveKey](#removekey)|Wywołaj tę metodę, aby usunąć wszystkie elementy klucz/wartość dla danego klucza.|

## <a name="remarks"></a>Uwagi

`CRBMultiMap` zapewnia obsługę mapowania tablicę dla dowolnego typu, zarządzanie uporządkowanej tablicy elementów klucza i wartości. W odróżnieniu od [CRBMap](../../atl/reference/crbmap-class.md) klasy, każdy klucz może być skojarzony z więcej niż jedną wartość.

Elementów (składające się z klucza i wartości) są przechowywane w drzewie binarnym struktury, za pomocą [CRBMultiMap::Insert](#insert) metody. Elementy, można je usunąć za pomocą [CRBMultiMap::RemoveKey](#removekey) metody, która usuwa wszystkie elementy, które odpowiadają danym kluczem.

Przechodzenie drzewa jest możliwe za pomocą metod takich jak [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), i [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue). Uzyskiwanie dostępu do potencjalnie wiele wartości dla każdego klucza jest to możliwe przy użyciu [CRBMultiMap::FindFirstWithKey](#findfirstwithkey), [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), i [CRBMultiMap::GetNextWithKey ](#getnextwithkey) metody. Zobacz przykład [CRBMultiMap::CRBMultiMap](#crbmultimap) opisano to w praktyce.

*KTraits* i *VTraits* parametry są traits — klasy, które zawierają dodatkowe wymagane do kopiowania lub przenoszenia elementów kodu.

`CRBMultiMap` jest tworzony na podstawie [CRBTree](../../atl/reference/crbtree-class.md), który implementuje drzewa binarnego przy użyciu algorytmu Red czarny. Alternatywa `CRBMultiMap` i `CRBMap` jest oferowany przez [CAtlMap](../../atl/reference/catlmap-class.md) klasy. Gdy tylko niewielka liczba elementów musi być przechowywany, należy wziąć pod uwagę przy użyciu [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy zamiast tego.

Pełniejsze omówienie różnych klas kolekcji i ich funkcje i charakterystyk wydajności, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="crbmultimap"></a>  CRBMultiMap::CRBMultiMap

Konstruktor.

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Rozmiar bloku.

### <a name="remarks"></a>Uwagi

*NBlockSize* parametr jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszają liczbę interwencji do procedur alokacji pamięci, ale używa więcej zasobów. Wartość domyślna będzie przydzielić miejsca dla 10 elementów w danym momencie.

Zobacz dokumentację dla klasy bazowej [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

##  <a name="dtor"></a>  CRBMultiMap:: ~ CRBMultiMap

Destruktor.

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie zasoby przydzielone.

Zobacz dokumentację dla klasy bazowej [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.

##  <a name="findfirstwithkey"></a>  CRBMultiMap::FindFirstWithKey

Wywołaj tę metodę, aby znaleźć położenie pierwszego elementu z danym kluczem.

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Określa klucz, który identyfikuje element, który ma zostać odnaleziona.

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję pierwszego elementu klucz/wartość, jeśli klucz zostanie znaleziony, wartość NULL w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Klucz w `CRBMultiMap` może mieć jedną lub więcej wartości skojarzone. Ta metoda zapewnia wartość pozycji pierwszej wartości, (które w rzeczywistości może być jedyną wartością) skojarzone z tego określonego klucza. Pozycja wartości zwracanej mogą następnie służyć za pomocą [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey) lub [CRBMultiMap::GetNextWithKey](#getnextwithkey) do uzyskania wartości i aktualizowania pozycji.

Zobacz dokumentację dla klasy bazowej [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.

### <a name="example"></a>Przykład

Zobacz przykład [CRBMultiMap::CRBMultiMap](#crbmultimap).

##  <a name="getnextvaluewithkey"></a>  CRBMultiMap::GetNextValueWithKey

Wywołaj tę metodę, aby pobrać wartość skojarzoną z danym kluczem i zaktualizuj wartość pozycji.

```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Pozycja, uzyskaną wartość przy użyciu wywołania do [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) lub [CRBMultiMap::GetNextWithKey](#getnextwithkey), lub poprzednie wywołanie `GetNextValueWithKey`.

*Klucz*<br/>
Określa klucz, który identyfikuje element, który ma zostać odnaleziona.

### <a name="return-value"></a>Wartość zwracana

Zwraca parę element skojarzony z danym kluczem.

### <a name="remarks"></a>Uwagi

Wartość pozycji jest aktualizowana, aby wskazywał następną wartość skojarzoną z kluczem. Jeśli nie istnieją dodatkowe wartości, wartość pozycji jest równa NULL.

Zobacz dokumentację dla klasy bazowej [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.

### <a name="example"></a>Przykład

Zobacz przykład [CRBMultiMap::CRBMultiMap](#crbmultimap).

##  <a name="getnextwithkey"></a>  CRBMultiMap::GetNextWithKey

Wywołaj tę metodę, aby pobrać element skojarzony z danym kluczem i zaktualizuj wartość pozycji.

```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*punktu sprzedaży*<br/>
Pozycja, uzyskaną wartość przy użyciu wywołania do [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) lub [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), lub poprzednie wywołanie `GetNextWithKey`.

*Klucz*<br/>
Określa klucz, który identyfikuje element, który ma zostać odnaleziona.

### <a name="return-value"></a>Wartość zwracana

Zwraca następne [klasy CRBTree::CPair](crbtree-class.md#cpair_class) element skojarzony z danym kluczem.

### <a name="remarks"></a>Uwagi

Wartość pozycji jest aktualizowana, aby wskazywał następną wartość skojarzoną z kluczem. Jeśli nie istnieją dodatkowe wartości, wartość pozycji jest równa NULL.

Zobacz dokumentację dla klasy bazowej [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.

##  <a name="insert"></a>  CRBMultiMap::Insert

Wywołaj tę metodę, aby wstawić para elementów do mapy.

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza do dodania do `CRBMultiMap` obiektu.

*value*<br/>
Wartość do dodania `CRBMultiMap` obiekt, skojarzony z *klucz*.

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję pary klucz/wartość elementu, w `CRBMultiMap` obiektu.

### <a name="remarks"></a>Uwagi

Zobacz dokumentację dla klasy bazowej [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.

### <a name="example"></a>Przykład

Zobacz przykład [CRBMultiMap::CRBMultiMap](#crbmultimap).

##  <a name="removekey"></a>  CRBMultiMap::RemoveKey

Wywołaj tę metodę, aby usunąć wszystkie elementy klucz/wartość dla danego klucza.

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Określa klucz, który identyfikuje następującą liczbę elementów do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wartości skojarzone z danym kluczem.

### <a name="remarks"></a>Uwagi

`RemoveKey` Usuwa wszystkie elementy klucz/wartość, które mają klucz, który odpowiada *klucz*.

Zobacz dokumentację dla klasy bazowej [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.

### <a name="example"></a>Przykład

Zobacz przykład [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="see-also"></a>Zobacz też

[Klasa CRBTree](../../atl/reference/crbtree-class.md)<br/>
[Klasa CAtlMap](../../atl/reference/catlmap-class.md)<br/>
[Klasa CRBMap](../../atl/reference/crbmap-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
