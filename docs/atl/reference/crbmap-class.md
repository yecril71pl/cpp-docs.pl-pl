---
title: Klasa CRBMap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41b4bf9678f2382c124bcfef484d0becf687f530
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072710"
---
# <a name="crbmap-class"></a>Klasa CRBMap

Ta klasa reprezentuje strukturę mapowania przy użyciu drzewa binarnego Red czarny.

## <a name="syntax"></a>Składnia

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
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
|[CRBMap::CRBMap](#crbmap)|Konstruktor.|
|[CRBMap:: ~ CRBMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBMap::Lookup](#lookup)|Wywołaj tę metodę, aby wyszukać kluczy ani wartości w `CRBMap` obiektu.|
|[CRBMap::RemoveKey](#removekey)|Wywołaj tę metodę, aby usunąć element z `CRBMap` obiekt, na podstawie klucza.|
|[CRBMap::SetAt](#setat)|Wywołaj tę metodę, aby wstawić para elementów do mapy.|

## <a name="remarks"></a>Uwagi

`CRBMap` zapewnia obsługę mapowania tablicę dla dowolnego typu, zarządzanie uporządkowanej tablicy kluczowych elementów i ich skojarzone wartości. Każdy klucz może mieć tylko jedną skojarzoną wartość. Elementów (składające się z klucza i wartości) są przechowywane w drzewie binarnym struktury, za pomocą [CRBMap::SetAt](#setat) metody. Elementy, można je usunąć za pomocą [CRBMap::RemoveKey](#removekey) metody, która usuwa element z danej wartości klucza.

Przechodzenie drzewa jest możliwe za pomocą metod takich jak [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), i [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).

*KTraits* i *VTraits* parametry są traits — klasy, które zawierają dodatkowe wymagane do kopiowania lub przenoszenia elementów kodu.

`CRBMap` jest tworzony na podstawie [CRBTree](../../atl/reference/crbtree-class.md), który implementuje drzewa binarnego przy użyciu algorytmu Red czarny. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) jest odmianą, która zezwala na wiele wartości dla każdego klucza. Zbyt pochodzi z `CRBTree`i dlatego udostępnia wiele funkcji, korzystając z `CRBMap`.

Alternatywa dla obu `CRBMap` i `CRBMultiMap` jest oferowany przez [CAtlMap](../../atl/reference/catlmap-class.md) klasy. Gdy tylko niewielka liczba elementów musi być przechowywany, należy wziąć pod uwagę przy użyciu [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy zamiast tego.

Pełniejsze omówienie różnych klas kolekcji i ich funkcje i charakterystyk wydajności, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

##  <a name="crbmap"></a>  CRBMap::CRBMap

Konstruktor.

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize*<br/>
Rozmiar bloku.

### <a name="remarks"></a>Uwagi

*NBlockSize* parametr jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszają liczbę interwencji do procedur alokacji pamięci, ale używa więcej zasobów. Wartość domyślna będzie przydzielić miejsca dla 10 elementów w danym momencie.

Zobacz dokumentację dla klasy bazowej [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

##  <a name="dtor"></a>  CRBMap:: ~ CRBMap

Destruktor.

```
~CRBMap() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie zasoby przydzielone.

Zobacz dokumentację dla klasy bazowej [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.

##  <a name="lookup"></a>  CRBMap::Lookup

Wywołaj tę metodę, aby wyszukać kluczy ani wartości w `CRBMap` obiektu.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Określa klucz, który identyfikuje elementu, który ma być wyszukiwana.

*value*<br/>
Zmienna, która otrzymuje wartość oglądałem się w górę.

### <a name="return-value"></a>Wartość zwracana

Pierwszy formularz metoda zwraca wartość true, jeśli klucz zostanie znaleziony, w przeciwnym razie wartość false. Drugi i trzeci formularzy zwracają wskaźnik do [CPair](crbtree-class.md#cpair_class).

### <a name="remarks"></a>Uwagi

Zobacz dokumentację dla klasy bazowej [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

##  <a name="removekey"></a>  CRBMap::RemoveKey

Wywołaj tę metodę, aby usunąć element z `CRBMap` obiekt, na podstawie klucza.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz odpowiadający para elementów chcesz usunąć.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli klucz został znaleziony i usunięte, wartość false w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Zobacz dokumentację dla klasy bazowej [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

##  <a name="setat"></a>  CRBMap::SetAt

Wywołaj tę metodę, aby wstawić para elementów do mapy.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Wartość klucza do dodania do `CRBMap` obiektu.

*value*<br/>
Wartość do dodania `CRBMap` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję pary klucz/wartość elementu, w `CRBMap` obiektu.

### <a name="remarks"></a>Uwagi

`SetAt` zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony. Jeśli klucz nie zostanie znaleziony, zostanie utworzony nową parę klucz wartość.

Zobacz dokumentację dla klasy bazowej [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CRBTree](../../atl/reference/crbtree-class.md)<br/>
[Klasa CAtlMap](../../atl/reference/catlmap-class.md)<br/>
[Klasa CRBMultiMap](../../atl/reference/crbmultimap-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
