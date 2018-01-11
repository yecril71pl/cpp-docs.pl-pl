---
title: Klasa CComSafeArrayBound | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
dev_langs: C++
helpviewer_keywords: CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4de823b4cdb2d7926b2a9d640b2e8f7352e389fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomsafearraybound-class"></a>Klasa CComSafeArrayBound
Ta klasa jest otoki dla [SAFEARRAYBOUND](http://msdn.microsoft.com/en-us/303a9bdb-71d6-4f14-8747-84cf84936c6d) struktury.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComSafeArrayBound : public SAFEARRAYBOUND
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CComSafeArrayBound](#ccomsafearraybound)|Konstruktor.|  
|[GetCount](#getcount)|Wywołaj tę metodę, aby zwrócić liczby elementów.|  
|[GetLowerBound](#getlowerbound)|Wywołaj tę metodę, aby zwrócić dolnej granicy.|  
|[GetUpperBound](#getupperbound)|Wywołaj tę metodę, aby zwrócić górna granica.|  
|[SetCount](#setcount)|Wywołanie tej metody, aby ustawić liczbę elementów.|  
|[SetLowerBound](#setlowerbound)|Wywołaj tę metodę, aby ustawić dolnej granicy.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](#operator_eq)|Ustawia `CComSafeArrayBound` na nową wartość.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa jest otoki dla **SAFEARRAYBOUND** struktury używane przez [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Zapewnia metody do badania i ustawiania górne i dolne granice jednego wymiaru `CComSafeArray` obiekt i liczba elementów, które zawiera. Wielowymiarowe `CComSafeArray` obiekt używa tablicę `CComSafeArrayBound` obiektów, dla każdego wymiaru. W związku z tym gdy przy użyciu metod, takich jak [GetCount](#getcount), należy pamiętać, że ta metoda nie zwróci łączna liczba elementów w tablicy wielowymiarowej.  
  
 **Nagłówek:** atlsafe.h  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsafe.h  
  
##  <a name="ccomsafearraybound"></a>CComSafeArrayBound::CComSafeArrayBound  
 Konstruktor.  
  
```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ulCount`  
 Liczba elementów w tablicy.  
  
 `lLowerBound`  
 Dolna granica z którego są ponumerowane tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli tablica jest można uzyskać dostępu do programu Visual C++, zaleca się, że dolna granica jest zdefiniowany jako 0. Można użyć różnych dolna granica wartości, jeśli tablica ma być używany z innymi językami, takich jak Visual Basic.  
  
##  <a name="getcount"></a>CComSafeArrayBound::GetCount  
 Wywołaj tę metodę, aby zwrócić liczby elementów.  
  
```
ULONG GetCount() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę elementów.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli skojarzony `CComSafeArray` obiekt reprezentuje tablicy wielowymiarowej, ta metoda zwróci tylko całkowita liczba elementów w wymiarze po prawej stronie. Użyj [CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount) uzyskać całkowitą liczbę elementów.  
  
##  <a name="getlowerbound"></a>CComSafeArrayBound::GetLowerBound  
 Wywołaj tę metodę, aby zwrócić dolnej granicy.  
  
```
LONG GetLowerBound() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dolną granicę `CComSafeArrayBound` obiektu.  
  
##  <a name="getupperbound"></a>CComSafeArrayBound::GetUpperBound  
 Wywołaj tę metodę, aby zwrócić górna granica.  
  
```
LONG GetUpperBound() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca górną granicę `CComSafeArrayBound` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Górna granica zależy od liczby elementów i wartość dolnej granicy. Na przykład jeśli dolna granica jest równa 0, a liczba elementów to 10, górna granica będzie automatyczne ustawienie 9.  
  
##  <a name="operator_eq"></a>CComSafeArrayBound::operator =  
 Ustawia `CComSafeArrayBound` na nową wartość.  
  
```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bound`  
 A `CComSafeArrayBound` obiektu.  
  
 `ulCount`  
 Liczba elementów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do `CComSafeArrayBound` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `CComSafeArrayBound` Obiektu można przypisać przy użyciu istniejącego `CComSafeArrayBound`, lub podając liczba elementów, w których przypadku dolna granica jest równa 0 domyślnie.  
  
##  <a name="setcount"></a>CComSafeArrayBound::SetCount  
 Wywołanie tej metody, aby ustawić liczbę elementów.  
  
```
ULONG SetCount(ULONG ulCount) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ulCount`  
 Liczba elementów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę elementów w `CComSafeArrayBound` obiektu.  
  
##  <a name="setlowerbound"></a>CComSafeArrayBound::SetLowerBound  
 Wywołaj tę metodę, aby ustawić dolnej granicy.  
  
```
LONG SetLowerBound(LONG lLowerBound) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lLowerBound`  
 Dolna granica.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca nowy dolna granica `CComSafeArrayBound` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli tablica jest można uzyskać dostępu do programu Visual C++, zaleca się, że dolna granica jest zdefiniowany jako 0. Można użyć różnych dolna granica wartości, jeśli tablica ma być używany z innymi językami, takich jak Visual Basic.  
  
 Górna granica zależy od liczby elementów i wartość dolnej granicy. Na przykład jeśli dolna granica jest równa 0, a liczba elementów to 10, górna granica będzie automatyczne ustawienie 9.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
