---
title: Klasa CComMultiThreadModelNoCS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
dev_langs: C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f1f0b531942e281236c65ef9a2e1ad3d3f669bbe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccommultithreadmodelnocs-class"></a>Klasa CComMultiThreadModelNoCS
`CComMultiThreadModelNoCS`udostępnia metody wątkowo zwiększanie oraz zmniejszanie wartości zmiennej, bez sekcja krytyczna blokowanie lub odblokowywanie funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComMultiThreadModelNoCS
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|  
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Odwołuje się do klasy `CComFakeCriticalSection`.|  
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Odwołuje się do klasy `CComMultiThreadModelNoCS`.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::Decrement](#decrement)|(Statyczny) Zmniejsza wartość zmiennej określonej w sposób wątkowo.|  
|[CComMultiThreadModelNoCS::Increment](#increment)|(Statyczny) Zwiększa wartość zmiennej określonej w sposób wątkowo.|  
  
## <a name="remarks"></a>Uwagi  
 `CComMultiThreadModelNoCS`przypomina [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) w tym zapewnia metody wątkowo zwiększanie oraz zmniejszanie zmiennej. Jednak podczas odwoływania się za pośrednictwem klasy sekcja krytyczna `CComMultiThreadModelNoCS`, metod, takich jak `Lock` i `Unlock` nie przynosi.  
  
 Zazwyczaj `CComMultiThreadModelNoCS` za pośrednictwem `ThreadModelNoCS` `typedef` nazwy. To `typedef` jest zdefiniowany w `CComMultiThreadModelNoCS`, `CComMultiThreadModel`, i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).  
  
> [!NOTE]
>  Globalny `typedef` nazwy [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) i [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) nie odwołuj się do `CComMultiThreadModelNoCS`.  
  
 Oprócz `ThreadModelNoCS`, `CComMultiThreadModelNoCS` definiuje `AutoCriticalSection` i `CriticalSection`. Tych dwóch `typedef` nazwy odwołania [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), zapewniające pusty metod skojarzonych z uzyskiwania i wydanie sekcja krytyczna.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection  
 Korzystając z `CComMultiThreadModelNoCS`, `typedef` nazwa `AutoCriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ `CComFakeCriticalSection` nie zawiera sekcja krytyczna, nic nie rób jego metody.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) również zawierają definicje `AutoCriticalSection`. W poniższej tabeli przedstawiono relację między klasę modelu wątkowości i klasa sekcja krytyczna odwołuje się `AutoCriticalSection`:  
  
|Klasa zdefiniowana w|Odwołanie do klasy|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 Oprócz `AutoCriticalSection`, można użyć `typedef` nazwa [criticalsection —](#criticalsection). Nie należy określać `AutoCriticalSection` obiektów globalnych lub elementów klas statycznych, jeśli chcesz wyeliminować CRT kod uruchomienia.  
  
### <a name="example"></a>Przykład  
 Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="criticalsection"></a>CComMultiThreadModelNoCS::CriticalSection  
 Korzystając z `CComMultiThreadModelNoCS`, `typedef` nazwa `CriticalSection` odwołuje się do klasy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ `CComFakeCriticalSection` nie zawiera sekcja krytyczna, nic nie rób jego metody.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) również zawierają definicje `CriticalSection`. W poniższej tabeli przedstawiono relację między klasę modelu wątkowości i klasa sekcja krytyczna odwołuje się `CriticalSection`:  
  
|Klasa zdefiniowana w|Odwołanie do klasy|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 Oprócz `CriticalSection`, można użyć `typedef` nazwa `AutoCriticalSection`. Nie należy określać `AutoCriticalSection` obiektów globalnych lub elementów klas statycznych, jeśli chcesz wyeliminować CRT kod uruchomienia.  
  
### <a name="example"></a>Przykład  
 Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="decrement"></a>CComMultiThreadModelNoCS::Decrement  
 Ta funkcja statyczna wywołania funkcji Win32 [InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580), które zmniejsza wartość zmiennej wskazywana przez `p`.  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [in] Wskaźnik do zmiennej się wraz z przydzielaniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli wynik dekrementacja wynosi 0, to `Decrement` zwraca wartość 0. Jeśli wynik dekrementacja jest różna od zera, zwracana wartość jest różna od zera, ale nie może równa wartości wynik zmniejszenie.  
  
### <a name="remarks"></a>Uwagi  
 **InterlockedDecrement** uniemożliwia więcej niż jeden wątek jednocześnie za pomocą tej zmiennej.  
  
##  <a name="increment"></a>CComMultiThreadModelNoCS::Increment  
 Ta funkcja statyczna wywołania funkcji Win32 [InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614), która zwiększa wartość zmiennej wskazywana przez `p`.  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [in] Wskaźnik do zmiennej jest zwiększany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli wynik przyrost wynosi 0, to **przyrostu** zwraca wartość 0. Jeśli wynik przyrost jest różna od zera, zwracana wartość również jest różna od zera, ale nie mogą równa wartości przyrostu.  
  
### <a name="remarks"></a>Uwagi  
 **InterlockedIncrement** uniemożliwia więcej niż jeden wątek jednocześnie za pomocą tej zmiennej.  
  
##  <a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS  
 Korzystając z `CComMultiThreadModelNoCS`, `typedef` nazwa `ThreadModelNoCS` po prostu odwołuje się do `CComMultiThreadModelNoCS`.  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>Uwagi  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) i [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) również zawierają definicje `ThreadModelNoCS`. W poniższej tabeli przedstawiono relację między klasę modelu wątkowości i klasy odwołuje się `ThreadModelNoCS`:  
  
|Klasa zdefiniowana w|Odwołanie do klasy|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
  
 Należy pamiętać, że definicja `ThreadModelNoCS` w `CComMultiThreadModelNoCS` zapewnia symetrycznego z `CComMultiThreadModel` i `CComSingleThreadModel`. Na przykład, załóżmy, że przykładowy kod `CComMultiThreadModel::AutoCriticalSection` zgłoszone następujące `typedef`:  
  
 [!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]  
  
 Niezależnie od tego, klasa określona dla `ThreadModel` (takich jak `CComMultiThreadModelNoCS`), `_ThreadModel` rozpoznaje odpowiednio.  
  
### <a name="example"></a>Przykład  
 Zobacz [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)