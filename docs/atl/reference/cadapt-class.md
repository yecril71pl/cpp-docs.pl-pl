---
title: Klasa CAdapt | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
dev_langs:
- C++
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13a04f9ba199205d84d94b9b3792c4bafb570319
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766493"
---
# <a name="cadapt-class"></a>Klasa CAdapt

Ten szablon jest używany do opakowywania klas, które ponownie definiują operator address-of, aby zwrócić coś innego niż adres obiektu.

## <a name="syntax"></a>Składnia

```
template <class T>  
class CAdapt
```

#### <a name="parameters"></a>Parametry

*T*  
Typ dostosowany.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAdapt::CAdapt](#cadapt)|Konstruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAdapt::operator const T &](#operator_const_t_amp)|Zwraca **const** odwołanie do `m_T`.|
|[CAdapt::operator T &](#operator_t_amp)|Zwraca odwołanie do `m_T`.|
|[CAdapt::operator <](#operator_lt)|Porównuje obiekt typu z `m_T`.|
|[CAdapt::operator =](#operator_eq)|Przypisuje obiekt typu dostosowane do `m_T`.|
|[CAdapt::operator ==](#operator_eq_eq)|Porównuje obiekt typu z `m_T`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAdapt::m_T](#m_t)|Dostosowywane dane.|

## <a name="remarks"></a>Uwagi

`CAdapt` jest używany do opakowywania klas, które ponownie definiują operator address-of prostego szablonu (`operator &`), aby zwrócić coś innego niż adres obiektu. Przykłady takich klas obejmują klasy ATL `CComBSTR`, `CComPtr`, i `CComQIPtr` klasy, a także klasę obsługi kompilatora COM, `_com_ptr_t`. Wszystkie te klasy ponownie zdefiniować operator address-of, aby zwrócić adres jednej z ich składowych danych (BSTR w przypadku właściwości `CComBSTR`i wskaźnik interfejsu w przypadku innych klas).

`CAdapt`firmy podstawową rolą jest ukrycie operatora address-of zdefiniowanego przez klasę *T*, a jednocześnie zachowanie charakterystyk klasy dostosowanej. `CAdapt` wypełnia tę rolę poprzez posiadanie publicznego elementu członkowskiego, [m_T](#m_t), typu *T*oraz w drodze określenia operatorów konwersji, operatorów porównania i Konstruktor kopiujący, umożliwiające specjalizacje `CAdapt` jako traktowane tak, jakby są obiektami typu *T*.

Klasa karty `CAdapt` jest przydatne, ponieważ niektóre klasy w stylu pojemnika oczekują można było uzyskać adresy ich zawartych obiektów za pomocą operatora address-of. Ponowne zdefiniowanie operatora address-of może spowodować problemy z tym wymaganiem, zazwyczaj powoduje błędy kompilacji i uniemożliwia wykorzystywanie typu niezaadaptowanego z klasami, które oczekują, że „po prostu ma działać”. `CAdapt` zapewnia sposób obejścia tych problemów.

Zazwyczaj można użyć `CAdapt` kiedy chcesz przechowywać `CComBSTR`, `CComPtr`, `CComQIPtr`, lub `_com_ptr_t` obiektów w klasie stylu kontenera. Było to najczęściej konieczne dla przed kontenery standardowej biblioteki języka C++ do obsługi standardu C ++ 11, ale kontenery 11 standardowej biblioteki C ++ automatycznie pracują z typami, które przeciążają `operator&()`. Standardowa biblioteka osiąga to za pomocą wewnętrznego korzystania [std::addressof](../../standard-library/memory-functions.md#addressof) uzyskać prawdziwe adresy obiektów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli.h

##  <a name="cadapt"></a>  CAdapt::CAdapt

Konstruktory umożliwiają karty obiekt, do którego jest domyślnie tworzony, skopiowane z obiektu typu lub z innego obiektu karty.

```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*rSrc*  
Zmienna o typie adaptowanego ma zostać skopiowana do karty nowo skonstruowany obiekt.

*rSrCA*  
Obiekt karty, którego dane zawarte powinny zostać skopiowane (lub przeniesione) do obiektu nowo skonstruowany karty.

##  <a name="m_t"></a>  CAdapt::m_T

Przechowuje dostosowywane dane.

```
T m_T;
```

### <a name="remarks"></a>Uwagi

To **publicznych** element członkowski danych jest możliwy bezpośrednio lub pośrednio z [operator const T &](#operator_const_t_amp) i [operator T &](#operator_t_amp).

##  <a name="operator_const_t_amp"></a>  CAdapt::operator const T&amp;

Zwraca **const** odwołanie do [m_T](#m_t) elementu członkowskiego, umożliwiając traktowane tak, jakby był to obiekt typu obiekt karty *T*.

```  
operator const T&() const;
```

### <a name="return-value"></a>Wartość zwracana

A **const** odwołanie do `m_T`.

##  <a name="operator_t_amp"></a>  CAdapt::operator T&amp;

Zwraca odwołanie do [m_T](#m_t) elementu członkowskiego, umożliwiając traktowane tak, jakby był to obiekt typu obiekt karty *T*.

```  
operator T&();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `m_T`.

##  <a name="operator_lt"></a>  CAdapt::operator &lt;

Porównuje obiekt typu z [m_T](#m_t).

```
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>Parametry

*rSrc*  
Odwołanie do obiektu, który ma zostać porównane.

### <a name="return-value"></a>Wartość zwracana

Wynik porównania między `m_T` i *rSrc*.

##  <a name="operator_eq"></a>  CAdapt::operator =

Operator przypisania przypisuje argumentu, *rSrc*, element członkowski danych [m_T](#m_t) i zwraca bieżący obiekt karty.

```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*rSrc*  
Odwołanie do obiektu typu ma być skopiowany. 

*rSrCA* odwołanie do obiektu do przeniesienia.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego obiektu.

##  <a name="operator_eq_eq"></a>  CAdapt::operator ==

Porównuje obiekt typu z [m_T](#m_t).

```
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>Parametry

*rSrc*  
Odwołanie do obiektu, który ma zostać porównane.

### <a name="return-value"></a>Wartość zwracana

Wynik porównania między *m_T* i *rSrc*.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
