---
title: Klasa CRBMap
ms.date: 11/04/2016
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
ms.openlocfilehash: 9e367ccc875eedf63e4f47018598662af2dfcf7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331402"
---
# <a name="crbmap-class"></a>Klasa CRBMap

Ta klasa reprezentuje strukturę mapowania, przy użyciu drzewa binarnego Red-Black.

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
|[CRBMap::CRBMap](#crbmap)|Konstruktor.|
|[CRBMap::~CRBMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRBMap::Odnośnik](#lookup)|Wywołanie tej metody, aby wyszukać klucze lub wartości w `CRBMap` obiekcie.|
|[CRBMap::Usuń klucz](#removekey)|Wywołanie tej metody, aby `CRBMap` usunąć element z obiektu, biorąc pod uwagę klucz.|
|[MAPA CRBMap::SetAt](#setat)|Wywołanie tej metody, aby wstawić parę elementów do mapy.|

## <a name="remarks"></a>Uwagi

`CRBMap`zapewnia obsługę tablicy mapowania dowolnego typu, zarządzanie uporządkowaną tablicą kluczowych elementów i skojarzonymi z nimi wartościami. Każdy klucz może mieć tylko jedną skojarzoną wartość. Elementy (składające się z klucza i wartości) są przechowywane w strukturze drzewa binarnego, przy użyciu [metody CRBMap::SetAt.](#setat) Elementy można usunąć za pomocą [METODY CRBMap::RemoveKey,](#removekey) która usuwa element o podanej wartości klucza.

Przechodzenie przez drzewo jest możliwe dzięki metodom takim jak [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext)i [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).

*Parametry KTraits* i *VTraits* są klasami cech, które zawierają dowolny kod uzupełniający potrzebny do kopiowania lub przenoszenia elementów.

`CRBMap`pochodzi z [CRBTree](../../atl/reference/crbtree-class.md), który implementuje drzewa binarnego przy użyciu algorytmu Red-Black. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) to odmiana, która pozwala na wiele wartości dla każdego klucza. To też pochodzi `CRBTree`od , a więc `CRBMap`dzieli wiele funkcji z .

Alternatywa dla `CRBMap` `CRBMultiMap` obu i jest oferowana przez [CAtlMap](../../atl/reference/catlmap-class.md) klasy. Gdy tylko niewielka liczba elementów musi być przechowywana, należy rozważyć użycie [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy zamiast.

Aby uzyskać pełniejszą dyskusję na temat różnych klas kolekcji oraz ich cech i cech wydajności, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Crbtree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcoll.h

## <a name="crbmapcrbmap"></a><a name="crbmap"></a>CRBMap::CRBMap

Konstruktor.

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parametry

*nBlockSize (Rozmiar)*<br/>
Rozmiar bloku.

### <a name="remarks"></a>Uwagi

Parametr *nBlockSize* jest miarą ilości przydzielonej pamięci, gdy wymagany jest nowy element. Większe rozmiary bloków zmniejszają liczbę wywołań procedur alokacji pamięci, ale zużywają więcej zasobów. Wartość domyślna będzie przydzielać miejsce dla 10 elementów naraz.

Zobacz dokumentację dla klasy podstawowej [CRBTree, aby](../../atl/reference/crbtree-class.md) uzyskać informacje na temat innych dostępnych metod.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

## <a name="crbmapcrbmap"></a><a name="dtor"></a>CRBMap::~CRBMap

Destruktor.

```
~CRBMap() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

Zobacz dokumentację dla klasy podstawowej [CRBTree, aby](../../atl/reference/crbtree-class.md) uzyskać informacje na temat innych dostępnych metod.

## <a name="crbmaplookup"></a><a name="lookup"></a>CRBMap::Odnośnik

Wywołanie tej metody, aby wyszukać klucze lub wartości w `CRBMap` obiekcie.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Określa klucz identyfikujący element, który ma być wyszukany.

*value*<br/>
Zmienna, która odbiera wartość wyszukiwania.

### <a name="return-value"></a>Wartość zwracana

Pierwsza forma metody zwraca wartość true, jeśli zostanie znaleziony klucz, w przeciwnym razie false. Drugi i trzeci formularz zwracają wskaźnik do [CPair](crbtree-class.md#cpair_class).

### <a name="remarks"></a>Uwagi

Zobacz dokumentację dla klasy podstawowej [CRBTree, aby](../../atl/reference/crbtree-class.md) uzyskać informacje na temat innych dostępnych metod.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

## <a name="crbmapremovekey"></a><a name="removekey"></a>CRBMap::Usuń klucz

Wywołanie tej metody, aby `CRBMap` usunąć element z obiektu, biorąc pod uwagę klucz.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz odpowiadający parze elementów, którą chcesz usunąć.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli klucz zostanie znaleziony i usunięty, false na niepowodzenie.

### <a name="remarks"></a>Uwagi

Zobacz dokumentację dla klasy podstawowej [CRBTree, aby](../../atl/reference/crbtree-class.md) uzyskać informacje na temat innych dostępnych metod.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

## <a name="crbmapsetat"></a><a name="setat"></a>MAPA CRBMap::SetAt

Wywołanie tej metody, aby wstawić parę elementów do mapy.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Wartość klucza, aby `CRBMap` dodać do obiektu.

*value*<br/>
Wartość dodana do `CRBMap` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca położenie pary elementu klucz/wartość `CRBMap` w obiekcie.

### <a name="remarks"></a>Uwagi

`SetAt`zastępuje istniejący element, jeśli zostanie znaleziony pasujący klucz. Jeśli klucz nie zostanie znaleziony, zostanie utworzona nowa para klucz/wartość.

Zobacz dokumentację dla klasy podstawowej [CRBTree, aby](../../atl/reference/crbtree-class.md) uzyskać informacje na temat innych dostępnych metod.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CRBTree](../../atl/reference/crbtree-class.md)<br/>
[Klasa CAtlMap](../../atl/reference/catlmap-class.md)<br/>
[Klasa CRBMultiMap](../../atl/reference/crbmultimap-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
