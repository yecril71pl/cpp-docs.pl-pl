---
title: Klasa CRBMap | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
dev_langs: C++
helpviewer_keywords: CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3cfa4d6fff6b46341f01b4d5ce18d9ec418738bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="crbmap-class"></a>Klasa CRBMap
Ta klasa reprezentuje struktury mapowanie za pomocą czarnego Red drzewa binarnego.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>> 
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
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
|[CRBMap::CRBMap](#crbmap)|Konstruktor.|  
|[CRBMap:: ~ CRBMap](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRBMap::Lookup](#lookup)|Wywołanie tej metody do wyszukiwania kluczy i wartości w `CRBMap` obiektu.|  
|[CRBMap::RemoveKey](#removekey)|Wywołanie tej metody, aby usunąć element z `CRBMap` obiekt danego klucza.|  
|[CRBMap::SetAt](#setat)|Wywołaj tę metodę, aby wstawić parę elementu do mapy.|  
  
## <a name="remarks"></a>Uwagi  
 `CRBMap`zapewnia obsługę mapowania tablicę dowolnego typu, zarządzanie tablicy uporządkowanej elementów kluczy oraz powiązanych wartości. Każdy klucz może mieć tylko jeden skojarzona wartość. Elementów (składające się z klucza i wartości) są przechowywane w drzewa binarnego struktury, za pomocą [CRBMap::SetAt](#setat) metody. Elementy można usunąć przy użyciu [CRBMap::RemoveKey](#removekey) metodę, która usuwa element z danej wartości klucza.  
  
 Przeglądanie drzewa jest możliwe za pomocą metod takich jak [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), i [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).  
  
 `KTraits` i `VTraits` parametry są klasy cech, które zawiera dodatkowe wymagane, aby skopiować lub przenieść elementy kodu.  
  
 `CRBMap`jest pochodną [CRBTree](../../atl/reference/crbtree-class.md), który implementuje drzewa binarnego przy użyciu algorytmu czarne czerwony. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) jest odmianą, która umożliwia wiele wartości dla każdego klucza. Zbyt pochodzi z `CRBTree`i dlatego udostępnia wiele funkcji z `CRBMap`.  
  
 Zamiast zarówno `CRBMap` i `CRBMultiMap` jest oferowany przez [CAtlMap](../../atl/reference/catlmap-class.md) klasy. Gdy tylko niewielka liczba elementów musi być przechowywany, należy rozważyć użycie [CSimpleMap](../../atl/reference/csimplemap-class.md) zamiast klasy.  
  
 Aby bardziej szczegółowe omówienie różnych klas kolekcji i ich funkcje i charakterystyki wydajności, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMap`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="crbmap"></a>CRBMap::CRBMap  
 Konstruktor.  
  
```
explicit CRBMap(size_t nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Rozmiar bloku.  
  
### <a name="remarks"></a>Uwagi  
 `nBlockSize` Parametr jest miarą ilość pamięci przydzielonej, gdy nowy element jest wymagany. Większe rozmiary bloków zmniejszyć wywołania procedury alokacji pamięci, ale użyj więcej zasobów. Wartość domyślna będzie zajmować miejsca na 10 elementów naraz.  
  
 W klasie podstawowej dokumentacji [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]  
  
##  <a name="dtor"></a>CRBMap:: ~ CRBMap  
 Destruktor.  
  
```
~CRBMap() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie zasoby przydzielone.  
  
 W klasie podstawowej dokumentacji [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.  
  
##  <a name="lookup"></a>CRBMap::Lookup  
 Wywołanie tej metody do wyszukiwania kluczy i wartości w `CRBMap` obiektu.  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Określa klucz identyfikujący element, aby wyszukiwać.  
  
 *value*  
 Zmienna, która odbiera wartość wyszukiwanego w górę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy formularz metoda zwraca wartość true, jeśli klucz zostanie znaleziony, w przeciwnym razie wartość false. Formularze drugiego i trzeciego zwraca wskaźnik do [CPair](crbtree-class.md#cpair_class).  
  
### <a name="remarks"></a>Uwagi  
 W klasie podstawowej dokumentacji [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]  
  
##  <a name="removekey"></a>CRBMap::RemoveKey  
 Wywołanie tej metody, aby usunąć element z `CRBMap` obiekt danego klucza.  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz odpowiadający pary element chcesz usunąć.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli klucz został znaleziony i usunięty, wartość false w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 W klasie podstawowej dokumentacji [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]  
  
##  <a name="setat"></a>CRBMap::SetAt  
 Wywołaj tę metodę, aby wstawić parę elementu do mapy.  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Wartość klucza można dodać do `CRBMap` obiektu.  
  
 *value*  
 Wartość do dodania do `CRBMap` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca element pary klucz wartość w `CRBMap` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `SetAt`zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony. Jeśli klucz nie zostanie znaleziony, jest tworzony nowy pary klucza/wartości.  
  
 W klasie podstawowej dokumentacji [CRBTree](../../atl/reference/crbtree-class.md) informacji na temat dostępnych metod.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CRBTree](../../atl/reference/crbtree-class.md)   
 [Klasa CAtlMap](../../atl/reference/catlmap-class.md)   
 [Klasa CRBMultiMap](../../atl/reference/crbmultimap-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
