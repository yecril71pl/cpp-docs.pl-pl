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
ms.openlocfilehash: 6ec016df268b702fd8b26d742d702ac38b95fa06
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365194"
---
# <a name="crbmultimap-class"></a>Klasa CRBMultiMap
Ta klasa reprezentuje strukturę mapowania, która umożliwia każdy klucz może być skojarzony z więcej niż jedną wartość, przy użyciu drzewa binarnego czarne czerwony.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename K,
         typename V, 
         class KTraits = CElementTraits<K>, 
         class VTraits = CElementTraits<V>>  
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
```    
  
#### <a name="parameters"></a>Parametry  
 `K`  
 Typ klucza elementu.  
  
 *V*  
 Typ wartości elementu.  
  
 `KTraits`  
 Kod używany do skopiować lub przenieść kluczowe elementy. Zobacz [CElementTraits klasy](../../atl/reference/celementtraits-class.md) więcej szczegółów.  
  
 `VTraits`  
 Kod używany do skopiować lub przenieść elementy wartość.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|Konstruktor.|  
|[CRBMultiMap:: ~ CRBMultiMap](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|Wywołanie tej metody do znalezienia położenie pierwszego elementu z danym kluczem.|  
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|Wywołanie tej metody można pobrać wartość skojarzoną z danym kluczem, a następnie zaktualizuj wartość pozycji.|  
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|Wywołanie tej metody, aby uzyskać element skojarzony z danym kluczem, a następnie zaktualizuj wartość pozycji.|  
|[CRBMultiMap::Insert](#insert)|Wywołaj tę metodę, aby wstawić parę elementu do mapy.|  
|[CRBMultiMap::RemoveKey](#removekey)|Wywołaj tę metodę, aby usunąć wszystkie elementy klucza i wartości dla danego klucza.|  
  
## <a name="remarks"></a>Uwagi  
 `CRBMultiMap` zapewnia obsługę mapowania tablicę dowolnego typu, zarządzanie tablicy uporządkowanej kluczowych elementów i wartości. W odróżnieniu od [CRBMap](../../atl/reference/crbmap-class.md) klasy, każdy klucz może być skojarzony z więcej niż jedną wartość.  
  
 Elementów (składające się z klucza i wartości) są przechowywane w drzewa binarnego struktury, za pomocą [CRBMultiMap::Insert](#insert) metody. Elementy można usunąć przy użyciu [CRBMultiMap::RemoveKey](#removekey) metodę, która usuwa wszystkie elementy, które odpowiadają danym kluczem.  
  
 Przeglądanie drzewa jest możliwe za pomocą metod takich jak [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), i [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue). Uzyskiwanie dostępu do potencjalnie wiele wartości dla każdego klucza jest to możliwe przy użyciu [CRBMultiMap::FindFirstWithKey](#findfirstwithkey), [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), i [CRBMultiMap::GetNextWithKey ](#getnextwithkey) metody. Zobacz przykład [CRBMultiMap::CRBMultiMap](#crbmultimap) ilustrację to w praktyce.  
  
 `KTraits` i `VTraits` parametry są klasy cech, które zawiera dodatkowe wymagane, aby skopiować lub przenieść elementy kodu.  
  
 `CRBMultiMap` jest pochodną [CRBTree](../../atl/reference/crbtree-class.md), który implementuje drzewa binarnego przy użyciu algorytmu czarne czerwony. Zamiast `CRBMultiMap` i `CRBMap` jest oferowany przez [CAtlMap](../../atl/reference/catlmap-class.md) klasy. Gdy tylko niewielka liczba elementów musi być przechowywany, należy rozważyć użycie [CSimpleMap](../../atl/reference/csimplemap-class.md) zamiast klasy.  
  
 Aby bardziej szczegółowe omówienie różnych klas kolekcji i ich funkcje i charakterystyki wydajności, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
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
 `nBlockSize`  
 Rozmiar bloku.  
  
### <a name="remarks"></a>Uwagi  
 `nBlockSize` Parametr jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszyć wywołania procedury alokacji pamięci, ale użyj więcej zasobów. Wartość domyślna będzie zajmować miejsca na 10 elementów naraz.  
  
 W klasie podstawowej dokumentacji [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]  
  
##  <a name="dtor"></a>  CRBMultiMap:: ~ CRBMultiMap  
 Destruktor.  
  
```
~CRBMultiMap() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie zasoby przydzielone.  
  
 W klasie podstawowej dokumentacji [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.  
  
##  <a name="findfirstwithkey"></a>  CRBMultiMap::FindFirstWithKey  
 Wywołanie tej metody do znalezienia położenie pierwszego elementu z danym kluczem.  
  
```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Określa klucz identyfikujący element, który ma zostać odnaleziona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pozycję pierwszego elementu klucz/wartość, jeśli klucz zostanie znaleziony, wartość NULL w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Klucz w `CRBMultiMap` może mieć co najmniej jeden skojarzone wartości. Ta metoda będzie podania wartości pozycji pierwsza wartość (co w rzeczywistości może być tylko wartość), skojarzone z tym określonego klucza. Zwracane wartości pozycji można następnie użyć z [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey) lub [CRBMultiMap::GetNextWithKey](#getnextwithkey) uzyskać wartość i Aktualizuj położenie.  
  
 W klasie podstawowej dokumentacji [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CRBMultiMap::CRBMultiMap](#crbmultimap).  
  
##  <a name="getnextvaluewithkey"></a>  CRBMultiMap::GetNextValueWithKey  
 Wywołanie tej metody można pobrać wartość skojarzoną z danym kluczem i zaktualizuj wartość pozycji.  
  
```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Wartość pozycji, uzyskane z wywołaniem do [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) lub [CRBMultiMap::GetNextWithKey](#getnextwithkey), lub poprzednie wywołanie `GetNextValueWithKey`.  
  
 `key`  
 Określa klucz identyfikujący element, który ma zostać odnaleziona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca element pary skojarzone z danym kluczem.  
  
### <a name="remarks"></a>Uwagi  
 Wartość pozycji jest aktualizowana wskaż wartość następnego skojarzoną z kluczem. Jeśli nie istnieją dodatkowe wartości, wartość pozycji jest równa NULL.  
  
 W klasie podstawowej dokumentacji [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CRBMultiMap::CRBMultiMap](#crbmultimap).  
  
##  <a name="getnextwithkey"></a>  CRBMultiMap::GetNextWithKey  
 Wywołanie tej metody, aby uzyskać element skojarzony z danym kluczem i zaktualizuj wartość pozycji.  
  
```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Wartość pozycji, uzyskane z wywołaniem do [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) lub [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), lub poprzednie wywołanie `GetNextWithKey`.  
  
 `key`  
 Określa klucz identyfikujący element, który ma zostać odnaleziona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca następne [klasy CRBTree::CPair](crbtree-class.md#cpair_class) element skojarzony z danym kluczem.  
  
### <a name="remarks"></a>Uwagi  
 Wartość pozycji jest aktualizowana wskaż wartość następnego skojarzoną z kluczem. Jeśli nie istnieją dodatkowe wartości, wartość pozycji jest równa NULL.  
  
 W klasie podstawowej dokumentacji [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.  
  
##  <a name="insert"></a>  CRBMultiMap::Insert  
 Wywołaj tę metodę, aby wstawić parę elementu do mapy.  
  
```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Wartość klucza można dodać do `CRBMultiMap` obiektu.  
  
 *value*  
 Wartość do dodania do `CRBMultiMap` obiekt skojarzony z `key`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca element pary klucz wartość w `CRBMultiMap` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 W klasie podstawowej dokumentacji [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CRBMultiMap::CRBMultiMap](#crbmultimap).  
  
##  <a name="removekey"></a>  CRBMultiMap::RemoveKey  
 Wywołaj tę metodę, aby usunąć wszystkie elementy klucza i wartości dla danego klucza.  
  
```
size_t RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Określa klucz identyfikujący elementów do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę wartości skojarzone z danym kluczem.  
  
### <a name="remarks"></a>Uwagi  
 `RemoveKey` Usuwa wszystkie elementy klucza i wartości, które ma klucz pasujący `key`.  
  
 W klasie podstawowej dokumentacji [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CRBMultiMap::CRBMultiMap](#crbmultimap).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CRBTree](../../atl/reference/crbtree-class.md)   
 [Klasa CAtlMap](../../atl/reference/catlmap-class.md)   
 [Klasa CRBMap](../../atl/reference/crbmap-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
