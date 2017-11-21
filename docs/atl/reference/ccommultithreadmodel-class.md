---
title: Klasa CComMultiThreadModel | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
dev_langs: C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7aad1856f28a1d76b53b983e63f36cf5fd4a7cfe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccommultithreadmodel-class"></a>Klasa CComMultiThreadModel
`CComMultiThreadModel`udostępnia bezpieczne wątkowo metody zwiększanie oraz zmniejszanie wartości zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComMultiThreadModel
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|Odwołuje się do klasy [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|  
|[CComMultiThreadModel::CriticalSection](#criticalsection)|Odwołuje się do klasy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|  
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odwołuje się do klasy [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComMultiThreadModel::Decrement](#decrement)|(Statyczny) Zmniejsza wartość zmiennej określonej w sposób wątkowo.|  
|[CComMultiThreadModel::Increment](#increment)|(Statyczny) Zwiększa wartość zmiennej określonej w sposób wątkowo.|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj `CComMultiThreadModel` za pomocą jednego z dwóch `typedef` nazwy, albo [CComObjectThreadModel] (atl — typedefs.md #ccomobjectthreadmodel lub [CComGlobalsThreadModel] (atl — typedefs.md #ccomglobalsthreadmodel. Klasa odwołuje się każdego `typedef` zależy model wątkowy używany, jak pokazano w poniższej tabeli:  
  
|— klasa typedef|Pojedynczy wątkowość|Wątkowości typu apartment|Wolnych wątków|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`; M =`CComMultiThreadModel`  
  
 `CComMultiThreadModel`definiuje się trzy `typedef` nazwy. `AutoCriticalSection`i `CriticalSection` odwołania klasy, które udostępniają metody służące do uzyskiwania i wydanie własność sekcja krytyczna. `ThreadModelNoCS`odwołania do klasy [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="autocriticalsection"></a>CComMultiThreadModel::AutoCriticalSection  
 Korzystając z `CComMultiThreadModel`, `typedef` nazwa `AutoCriticalSection` odwołuje się do klasy [CComAutoCriticalSection](ccomautocriticalsection-class.md), który udostępnia metody uzyskiwania i zwalniania prawo własności obiektu sekcja krytyczna.  
  
```
typedef CComAutoCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>Uwagi  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md) i [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) również zawierają definicje `AutoCriticalSection`. W poniższej tabeli przedstawiono relację między klasę modelu wątkowości i klasa sekcja krytyczna odwołuje się `AutoCriticalSection`:  
  
|Klasa zdefiniowana w|Odwołanie do klasy|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 Oprócz `AutoCriticalSection`, można użyć `typedef` nazwa [criticalsection —](#criticalsection). Nie należy określać `AutoCriticalSection` obiektów globalnych lub elementów klas statycznych, jeśli chcesz wyeliminować CRT kod uruchomienia.  
  
### <a name="example"></a>Przykład  
 Poniższy kod jest modelowana po [CComObjectRootEx](ccomobjectrootex-class.md)i pokazuje `AutoCriticalSection` używane w środowisku wątków.  
  

```cpp  
template<class ThreadModel>
class CMyAutoCritClass
{
public:
   typedef ThreadModel _ThreadModel;
   typedef typename _ThreadModel::AutoCriticalSection _CritSec;

   CMyAutoCritClass() : m_dwRef(0) {}

   ULONG InternalAddRef()
   {
      return _ThreadModel::Increment(&m_dwRef);
   }
   ULONG InternalRelease()
   {
      return _ThreadModel::Decrement(&m_dwRef);   
   }
   void Lock() { m_critsec.Lock( ); }
   void Unlock() { m_critsec.Unlock(); }

private:
   _CritSec m_critsec;
   LONG m_dwRef;
```  
  
 W poniższej tabeli przedstawiono wyniki `InternalAddRef` i `Lock` metod, w zależności od **ThreadModel** parametr szablonu i model wątkowy używany przez aplikację:  
  
### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel  
  
|Metoda|Pojedyncza lub wątkowości typu Apartment|Wolnych wątków|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|Przyrost nie jest bezpieczne wątkowo.|Przyrost jest bezpieczne wątkowo.|  
|`Lock`|Nie robi nic; nie ma krytycznych części do zablokowania.|Sekcja krytyczna jest zablokowany.|  
  
### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS  
  
|Metoda|Pojedyncza lub wątkowości typu Apartment|Wolnych wątków|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|Przyrost nie jest bezpieczne wątkowo.|Przyrost jest bezpieczne wątkowo.|  
|`Lock`|Nie robi nic; nie ma krytycznych części do zablokowania.|Nie robi nic; nie ma krytycznych części do zablokowania.|  
  
##  <a name="criticalsection"></a>CComMultiThreadModel::CriticalSection  
 Korzystając z `CComMultiThreadModel`, `typedef` nazwa `CriticalSection` odwołuje się do klasy [CComCriticalSection](ccomcriticalsection-class.md), który udostępnia metody uzyskiwania i zwalniania prawo własności obiektu sekcja krytyczna.  
  
```
typedef CComCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>Uwagi  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md) i [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) również zawierają definicje `CriticalSection`. W poniższej tabeli przedstawiono relację między klasę modelu wątkowości i klasa sekcja krytyczna odwołuje się `CriticalSection`:  
  
|Klasa zdefiniowana w|Odwołanie do klasy|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 Oprócz `CriticalSection`, można użyć `typedef` nazwa [AutoCriticalSection](#autocriticalsection). Nie należy określać `AutoCriticalSection` obiektów globalnych lub elementów klas statycznych, jeśli chcesz wyeliminować CRT kod uruchomienia.  
  
### <a name="example"></a>Przykład  
 Zobacz [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).  
  
##  <a name="decrement"></a>CComMultiThreadModel::Decrement  
 Ta funkcja statyczna wywołania funkcji Win32 [InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580), które zmniejsza wartość zmiennej wskazywana przez `p`.  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [in] Wskaźnik do zmiennej się wraz z przydzielaniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli wynik dekrementacja wynosi 0, to `Decrement` zwraca wartość 0. Jeśli wynik dekrementacja jest różna od zera, zwracana wartość jest różna od zera, ale nie może równa wartości wynik zmniejszenie.  
  
### <a name="remarks"></a>Uwagi  
 **InterlockedDecrement** uniemożliwia więcej niż jeden wątek jednocześnie za pomocą tej zmiennej.  
  
##  <a name="increment"></a>CComMultiThreadModel::Increment  
 Ta funkcja statyczna wywołania funkcji Win32 [InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614), która zwiększa wartość zmiennej wskazywana przez `p`.  
  
```
static ULONG WINAPI Increment(LPLONG p) throw ();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [in] Wskaźnik do zmiennej jest zwiększany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli wynik przyrost wynosi 0, to **przyrostu** zwraca wartość 0. Jeśli wynik przyrost jest różna od zera, zwracana wartość również jest różna od zera, ale nie mogą równa wartości przyrostu.  
  
### <a name="remarks"></a>Uwagi  
 **InterlockedIncrement** uniemożliwia więcej niż jeden wątek jednocześnie za pomocą tej zmiennej.  
  
##  <a name="threadmodelnocs"></a>CComMultiThreadModel::ThreadModelNoCS  
 Korzystając z `CComMultiThreadModel`, `typedef` nazwa `ThreadModelNoCS` odwołuje się do klasy [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>Uwagi  
 `CComMultiThreadModelNoCS`udostępnia metody wątkowo zwiększanie oraz zmniejszanie zmiennej; jednak nie zawiera sekcja krytyczna.  
  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md) i `CComMultiThreadModelNoCS` również zawierają definicje `ThreadModelNoCS`. W poniższej tabeli przedstawiono relację między klasę modelu wątkowości i klasy odwołuje się `ThreadModelNoCS`:  
  
|Klasa zdefiniowana w|Odwołanie do klasy|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
  
### <a name="example"></a>Przykład  
 Zobacz [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComSingleThreadModel](ccomsinglethreadmodel-class.md)   
 [Klasa CComAutoCriticalSection](ccomautocriticalsection-class.md)   
 [Klasa CComCriticalSection](ccomcriticalsection-class.md)   
 [Przegląd klas](../atl-class-overview.md)
