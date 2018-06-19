---
title: Klasa CComSingleThreadModel | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
dev_langs:
- C++
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 175cc1b867356949ca861f7015dedb6d64c4282f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365103"
---
# <a name="ccomsinglethreadmodel-class"></a>Klasa CComSingleThreadModel
Ta klasa dostarcza metody zwiększanie oraz zmniejszanie wartości zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComSingleThreadModel
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|Odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|  
|[CComSingleThreadModel::CriticalSection](#criticalsection)|Odwołuje się do klasy `CComFakeCriticalSection`.|  
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odwołania `CComSingleThreadModel`.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComSingleThreadModel::Decrement](#decrement)|Zmniejsza wartość określonej zmiennej. Ta implementacja nie jest bezpieczne wątkowo.|  
|[CComSingleThreadModel::Increment](#increment)|Zwiększa wartość określonej zmiennej. Ta implementacja nie jest bezpieczne wątkowo.|  
  
## <a name="remarks"></a>Uwagi  
 `CComSingleThreadModel` udostępnia metody zwiększanie oraz zmniejszanie wartości zmiennej. W odróżnieniu od [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), metody te nie są wątkowo.  

 Zazwyczaj `CComSingleThreadModel` za pomocą jednego z dwóch `typedef` nazw albo [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) lub [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). Klasa odwołuje się każdego `typedef` zależy model wątkowy używany, jak pokazano w poniższej tabeli:  

  
|— klasa typedef|Pojedynczy model wątkowości|Model wątkowości typu apartment|Bezpłatne model wątkowości|  
|-------------|----------------------------|-------------------------------|--------------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`; M = `CComMultiThreadModel`  
  
 `CComSingleThreadModel` definiuje się trzy `typedef` nazwy. `ThreadModelNoCS` odwołania `CComSingleThreadModel`. `AutoCriticalSection` i `CriticalSection` klasę referencyjną [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), zapewniające pusty metod skojarzonych z uzyskiwania i wydanie własność sekcja krytyczna.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="autocriticalsection"></a>  CComSingleThreadModel::AutoCriticalSection  
 Korzystając z `CComSingleThreadModel`, `typedef` nazwa `AutoCriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ `CComFakeCriticalSection` nie zawiera sekcja krytyczna, nic nie rób jego metody.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają definicje `AutoCriticalSection`. W poniższej tabeli przedstawiono relację między klasę modelu wątkowości i klasa sekcja krytyczna odwołuje się `AutoCriticalSection`:  
  
|Klasa zdefiniowana w|Odwołanie do klasy|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 Oprócz `AutoCriticalSection`, można użyć `typedef` nazwa [criticalsection —](#criticalsection). Nie należy określać `AutoCriticalSection` obiektów globalnych lub elementów klas statycznych, jeśli chcesz wyeliminować CRT kod uruchomienia.  
  
### <a name="example"></a>Przykład  
 Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="criticalsection"></a>  CComSingleThreadModel::CriticalSection  
 Korzystając z `CComSingleThreadModel`, `typedef` nazwa `CriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ `CComFakeCriticalSection` nie zawiera sekcja krytyczna, nic nie rób jego metody.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają definicje `CriticalSection`. W poniższej tabeli przedstawiono relację między klasę modelu wątkowości i klasa sekcja krytyczna odwołuje się `CriticalSection`:  
  
|Klasa zdefiniowana w|Odwołanie do klasy|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 Oprócz `CriticalSection`, można użyć `typedef` nazwa [AutoCriticalSection](#autocriticalsection). Nie należy określać `AutoCriticalSection` obiektów globalnych lub elementów klas statycznych, jeśli chcesz wyeliminować CRT kod uruchomienia.  
  
### <a name="example"></a>Przykład  
 Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="decrement"></a>  CComSingleThreadModel::Decrement  
 Ta funkcja statyczna zmniejsza wartość zmiennej wskazywana przez `p`.  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [in] Wskaźnik do zmiennej się wraz z przydzielaniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynik zmniejszenie.  
  
##  <a name="increment"></a>  CComSingleThreadModel::Increment  
 Ta funkcja statyczna zmniejsza wartość zmiennej wskazywana przez `p`.  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [in] Wskaźnik do zmiennej jest zwiększany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynik przyrostu.  
  
##  <a name="threadmodelnocs"></a>  CComSingleThreadModel::ThreadModelNoCS  
 Korzystając z `CComSingleThreadModel`, `typedef` nazwa `ThreadModelNoCS` po prostu odwołuje się do `CComSingleThreadModel`.  
  
```
typedef CComSingleThreadModel ThreadModelNoCS;
```  
  
### <a name="remarks"></a>Uwagi  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) zawierają definicje `ThreadModelNoCS`. W poniższej tabeli przedstawiono relację między klasę modelu wątkowości i klasy odwołuje się `ThreadModelNoCS`:  
  
|Klasa zdefiniowana w|Odwołanie do klasy|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
  
### <a name="example"></a>Przykład  
 Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
