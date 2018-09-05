---
title: Klasa CComSafeArrayBound | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
dev_langs:
- C++
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 457c880f7f7eb6c011637b438fa3bcc25d57303b
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758277"
---
# <a name="ccomsafearraybound-class"></a>Klasa CComSafeArrayBound

Ta klasa jest otoką [SAFEARRAYBOUND](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagsafearraybound) struktury.

## <a name="syntax"></a>Składnia

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[CComSafeArrayBound](#ccomsafearraybound)|Konstruktor.|
|[GetCount](#getcount)|Wywołaj tę metodę, aby zwrócić liczbę elementów.|
|[GetLowerBound](#getlowerbound)|Wywołaj tę metodę, aby zwrócić dolną granicę.|
|[GetUpperBound](#getupperbound)|Wywołaj tę metodę, aby zwrócić górną granicę.|
|[SetCount](#setcount)|Wywołaj tę metodę, aby ustawić liczbę elementów.|
|[SetLowerBound](#setlowerbound)|Wywołaj tę metodę, aby ustawić dolną granicę.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#operator_eq)|Zestawy `CComSafeArrayBound` na nową wartość.|

## <a name="remarks"></a>Uwagi

Ta klasa jest otoką `SAFEARRAYBOUND` struktury używane przez [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Udostępnia metody do tworzenia zapytań i ustawiania granic górnych i dolnych jednego wymiaru `CComSafeArray` obiektu i liczbę elementów, które zawiera. Wielowymiarowe `CComSafeArray` obiektu wykorzystuje tablicę `CComSafeArrayBound` obiektów, po jednym dla każdego wymiaru. W związku z tym korzystając z metody takie jak [GetCount](#getcount), należy pamiętać, że ta metoda nie zwróci całkowitą liczbę elementów w tablicy wielowymiarowej.

**Nagłówek:** atlsafe.h

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsafe.h

##  <a name="ccomsafearraybound"></a>  CComSafeArrayBound::CComSafeArrayBound

Konstruktor.

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Parametry

*ulCount*  
Liczba elementów w tablicy.

*lLowerBound*  
Dolna granica, z którego są ponumerowane tablicy.

### <a name="remarks"></a>Uwagi

Jeśli tablica jest można uzyskać dostęp z poziomu programu Visual C++, zalecane jest, że dolna granica jest zdefiniowana jako 0. Może to być lepiej jest używać różnych dolna granica wartości, jeśli tablica jest ma być używany z innymi językami, takie jak Visual Basic.

##  <a name="getcount"></a>  CComSafeArrayBound::GetCount

Wywołaj tę metodę, aby zwrócić liczbę elementów.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów.

### <a name="remarks"></a>Uwagi

Jeśli skojarzonego `CComSafeArray` obiekt reprezentuje tablicę wielowymiarową, ta metoda zwróci tylko całkowitą liczbę elementów w wymiarze po prawej stronie. Użyj [CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount) uzyskać całkowitą liczbę elementów.

##  <a name="getlowerbound"></a>  CComSafeArrayBound::GetLowerBound

Wywołaj tę metodę, aby zwrócić dolną granicę.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dolną granicę `CComSafeArrayBound` obiektu.

##  <a name="getupperbound"></a>  CComSafeArrayBound::GetUpperBound

Wywołaj tę metodę, aby zwrócić górną granicę.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca górną granicę `CComSafeArrayBound` obiektu.

### <a name="remarks"></a>Uwagi

Górna granica zależy od liczby elementów i wartość dolnej granicy. Na przykład jeśli dolna granica jest równa 0, a liczba elementów to 10, górna granica będzie automatycznie ustawić do 9.

##  <a name="operator_eq"></a>  CComSafeArrayBound::operator =

Zestawy `CComSafeArrayBound` na nową wartość.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Parametry

*powiązane*  
Element `CComSafeArrayBound` obiektu.

*ulCount*  
Liczba elementów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `CComSafeArrayBound` obiektu.

### <a name="remarks"></a>Uwagi

`CComSafeArrayBound` Obiekt można przypisać przy użyciu istniejącego `CComSafeArrayBound`, lub podając liczbę elementów, w których przypadku dolna granica jest równa 0 domyślnie.

##  <a name="setcount"></a>  CComSafeArrayBound::SetCount

Wywołaj tę metodę, aby ustawić liczbę elementów.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Parametry

*ulCount*  
Liczba elementów.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów w `CComSafeArrayBound` obiektu.

##  <a name="setlowerbound"></a>  CComSafeArrayBound::SetLowerBound

Wywołaj tę metodę, aby ustawić dolną granicę.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Parametry

*lLowerBound*  
Dolna granica.

### <a name="return-value"></a>Wartość zwracana

Zwraca nowy dolna granica `CComSafeArrayBound` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli tablica jest można uzyskać dostęp z poziomu programu Visual C++, zalecane jest, że dolna granica jest zdefiniowana jako 0. Może to być lepiej jest używać różnych dolna granica wartości, jeśli tablica jest ma być używany z innymi językami, takie jak Visual Basic.

Górna granica zależy od liczby elementów i wartość dolnej granicy. Na przykład jeśli dolna granica jest równa 0, a liczba elementów to 10, górna granica będzie automatycznie ustawić do 9.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
