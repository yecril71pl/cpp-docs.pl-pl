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
ms.openlocfilehash: 2c2f8b787e5366ec893538a88049f6f53dc35caf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327380"
---
# <a name="ccomsafearraybound-class"></a>Klasa CComSafeArrayBound

Ta klasa jest otoką dla struktury [SAFEARRAYBOUND.](/windows/win32/api/oaidl/ns-oaidl-safearraybound)

## <a name="syntax"></a>Składnia

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Ccomsafearraybound](#ccomsafearraybound)|Konstruktor.|
|[GetCount](#getcount)|Wywołanie tej metody, aby zwrócić liczbę elementów.|
|[GetLowerBound (GetLowerBound)](#getlowerbound)|Wywołanie tej metody, aby zwrócić dolną granicę.|
|[Getupperbound](#getupperbound)|Wywołanie tej metody, aby zwrócić górną granicę.|
|[SetCount (licz).](#setcount)|Wywołanie tej metody, aby ustawić liczbę elementów.|
|[SetLowerBound (Przystawka SetLowerBound)](#setlowerbound)|Wywołanie tej metody, aby ustawić dolną granicę.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#operator_eq)|Ustawia `CComSafeArrayBound` nową wartość.|

## <a name="remarks"></a>Uwagi

Ta klasa jest otoką `SAFEARRAYBOUND` dla struktury używanej przez [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Zawiera metody wykonywania zapytań i ustawiania górnych i dolnych granic pojedynczego wymiaru `CComSafeArray` obiektu oraz liczby elementów, które zawiera. `CComSafeArray` Obiekt wielowymiarowy używa tablicy `CComSafeArrayBound` obiektów, po jednym dla każdego wymiaru. W związku z tym podczas korzystania z metod, takich jak [GetCount](#getcount), należy pamiętać, że ta metoda nie zwróci całkowitą liczbę elementów w tablicy wielowymiarowej.

**Nagłówek:** atlsafe.h

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsafe.h

## <a name="ccomsafearrayboundccomsafearraybound"></a><a name="ccomsafearraybound"></a>CComSafeArrayBound::CComSafeArrayBound

Konstruktor.

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Parametry

*UlCount (ulCount)*<br/>
Liczba elementów w tablicy.

*lLowerBound (Przylot)*<br/>
Dolna granica, z której tablica jest numerowana.

### <a name="remarks"></a>Uwagi

Jeśli tablica ma być dostępny z programu C++, zaleca się, aby dolna granica była zdefiniowana jako 0. Może być lepsze użycie innej wartości dolnej granicy, jeśli tablica ma być używana z innymi językami, takimi jak Visual Basic.

## <a name="ccomsafearrayboundgetcount"></a><a name="getcount"></a>CComSafeArrayBound::GetCount

Wywołanie tej metody, aby zwrócić liczbę elementów.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów.

### <a name="remarks"></a>Uwagi

Jeśli skojarzony `CComSafeArray` obiekt reprezentuje tablicę wielowymiarową, ta metoda zwróci tylko całkowitą liczbę elementów w wymiarze po prawej stronie. Użyj [CComSafeArray::GetCount,](../../atl/reference/ccomsafearray-class.md#getcount) aby uzyskać całkowitą liczbę elementów.

## <a name="ccomsafearrayboundgetlowerbound"></a><a name="getlowerbound"></a>CComSafeArrayBound::GetLowerBound

Wywołanie tej metody, aby zwrócić dolną granicę.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dolną granicę `CComSafeArrayBound` obiektu.

## <a name="ccomsafearrayboundgetupperbound"></a><a name="getupperbound"></a>CComSafeArrayBound::GetUpperBound

Wywołanie tej metody, aby zwrócić górną granicę.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca górną granicę `CComSafeArrayBound` obiektu.

### <a name="remarks"></a>Uwagi

Górna granica zależy od liczby elementów i dolnej wartości granicy. Na przykład jeśli dolna granica wynosi 0, a liczba elementów wynosi 10, górna granica zostanie automatycznie ustawiona na 9.

## <a name="ccomsafearrayboundoperator-"></a><a name="operator_eq"></a>CComSafeArrayBound::operator =

Ustawia `CComSafeArrayBound` nową wartość.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Parametry

*Powiązane*<br/>
Obiekt `CComSafeArrayBound`.

*UlCount (ulCount)*<br/>
Liczba elementów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `CComSafeArrayBound` obiektu.

### <a name="remarks"></a>Uwagi

Obiekt `CComSafeArrayBound` można przypisać przy użyciu `CComSafeArrayBound`istniejącego lub przez podanie liczby elementów, w którym to przypadku dolna granica jest domyślnie ustawiona na 0.

## <a name="ccomsafearrayboundsetcount"></a><a name="setcount"></a>CComSafeArrayBound::SetCount

Wywołanie tej metody, aby ustawić liczbę elementów.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Parametry

*UlCount (ulCount)*<br/>
Liczba elementów.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów `CComSafeArrayBound` w obiekcie.

## <a name="ccomsafearrayboundsetlowerbound"></a><a name="setlowerbound"></a>CComSafeArrayBound::SetLowerBound

Wywołanie tej metody, aby ustawić dolną granicę.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Parametry

*lLowerBound (Przylot)*<br/>
Dolna granica.

### <a name="return-value"></a>Wartość zwracana

Zwraca nową dolną `CComSafeArrayBound` granicę obiektu.

### <a name="remarks"></a>Uwagi

Jeśli tablica ma być dostępny z programu Visual C++, zaleca się, aby dolna granica była zdefiniowana jako 0. Może być lepsze użycie innej wartości dolnej granicy, jeśli tablica ma być używana z innymi językami, takimi jak Visual Basic.

Górna granica zależy od liczby elementów i dolnej wartości granicy. Na przykład jeśli dolna granica wynosi 0, a liczba elementów wynosi 10, górna granica zostanie automatycznie ustawiona na 9.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
