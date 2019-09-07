---
title: Klasa CComSafeArrayBound
ms.date: 05/06/2019
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
ms.openlocfilehash: 0386092ac26e71fcf5e840594a6b07f56cc9badd
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739747"
---
# <a name="ccomsafearraybound-class"></a>Klasa CComSafeArrayBound

Ta klasa jest otoką dla struktury [SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-safearraybound) .

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
|[operator =](#operator_eq)|`CComSafeArrayBound` Ustawia nową wartość.|

## <a name="remarks"></a>Uwagi

Ta klasa jest otoką dla `SAFEARRAYBOUND` struktury używanej przez [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Zapewnia metody wykonywania zapytań i ustawiania górnych i dolnych granic pojedynczego wymiaru `CComSafeArray` obiektu oraz liczby elementów, które zawiera. Obiekt wielowymiarowy `CComSafeArray` używa `CComSafeArrayBound` tablicy obiektów, po jednej dla każdego wymiaru. W związku z tym, w przypadku używania metod, takich jak [GetCount](#getcount), należy pamiętać, że ta metoda nie zwróci całkowitej liczby elementów w tablicy wielowymiarowej.

**Nagłówek:** atlsafe. h

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsafe. h

##  <a name="ccomsafearraybound"></a>CComSafeArrayBound::CComSafeArrayBound

Konstruktor.

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Parametry

*ulCount*<br/>
Liczba elementów w tablicy.

*lLowerBound*<br/>
Dolna granica, z której jest numerowana tablica.

### <a name="remarks"></a>Uwagi

Jeśli tablica jest dostępna z poziomu C++ programu, zaleca się, aby Dolna granica była zdefiniowana jako 0. Zalecane jest użycie innej mniejszej wartości powiązanej, jeśli tablica ma być używana z innymi językami, takich jak Visual Basic.

##  <a name="getcount"></a>CComSafeArrayBound:: GetCount

Wywołaj tę metodę, aby zwrócić liczbę elementów.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów.

### <a name="remarks"></a>Uwagi

Jeśli skojarzony `CComSafeArray` obiekt reprezentuje tablicę wielowymiarową, ta metoda zwróci jedynie łączną liczbę elementów w wymiarze po prawej stronie. Użyj [CComSafeArray:: GetCount](../../atl/reference/ccomsafearray-class.md#getcount) , aby uzyskać łączną liczbę elementów.

##  <a name="getlowerbound"></a>CComSafeArrayBound::GetLowerBound

Wywołaj tę metodę, aby zwrócić dolną granicę.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dolną granicę `CComSafeArrayBound` obiektu.

##  <a name="getupperbound"></a>CComSafeArrayBound::GetUpperBound

Wywołaj tę metodę, aby zwrócić górną granicę.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca górną granicę `CComSafeArrayBound` obiektu.

### <a name="remarks"></a>Uwagi

Górna granica zależy od liczby elementów i dolnej wartości powiązanej. Na przykład, jeśli Dolna granica to 0, a liczba elementów wynosi 10, Górna granica zostanie automatycznie ustawiona na 9.

##  <a name="operator_eq"></a>CComSafeArrayBound:: operator =

`CComSafeArrayBound` Ustawia nową wartość.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Parametry

*obowiązując*<br/>
Element `CComSafeArrayBound` obiektu.

*ulCount*<br/>
Liczba elementów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `CComSafeArrayBound` obiektu.

### <a name="remarks"></a>Uwagi

Obiekt może być przypisany przy użyciu istniejącego `CComSafeArrayBound`lub dostarczając liczbę elementów. w takim przypadku Dolna granica jest domyślnie ustawiona na 0. `CComSafeArrayBound`

##  <a name="setcount"></a>CComSafeArrayBound:: SetCount

Wywołaj tę metodę, aby ustawić liczbę elementów.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Parametry

*ulCount*<br/>
Liczba elementów.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów w `CComSafeArrayBound` obiekcie.

##  <a name="setlowerbound"></a>CComSafeArrayBound::SetLowerBound

Wywołaj tę metodę, aby ustawić dolną granicę.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Parametry

*lLowerBound*<br/>
Dolna granica.

### <a name="return-value"></a>Wartość zwracana

Zwraca nową dolną granicę `CComSafeArrayBound` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli tablica jest dostępna z poziomu programu wizualnego C++ , zaleca się, aby Dolna granica była zdefiniowana jako 0. Zalecane jest użycie innej mniejszej wartości powiązanej, jeśli tablica ma być używana z innymi językami, takich jak Visual Basic.

Górna granica zależy od liczby elementów i dolnej wartości powiązanej. Na przykład, jeśli Dolna granica to 0, a liczba elementów wynosi 10, Górna granica zostanie automatycznie ustawiona na 9.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
