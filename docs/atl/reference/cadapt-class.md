---
title: Klasa CAdapt
ms.date: 11/04/2016
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
ms.openlocfilehash: 23544bc103de0d7b76cd73d403626ba93af6e31a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321639"
---
# <a name="cadapt-class"></a>Klasa CAdapt

Ten szablon jest używany do opakowywania klas, które ponownie definiują operator address-of, aby zwrócić coś innego niż adres obiektu.

## <a name="syntax"></a>Składnia

```
template <class T>
class CAdapt
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dostosowany.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAdapt::CAdapt](#cadapt)|Konstruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAdapt::operator const T&](#operator_const_t_amp)|Zwraca odwołanie **const** do `m_T`.|
|[CAdapt::operator T&](#operator_t_amp)|Zwraca odwołanie `m_T`do .|
|[CAdapt::operator <](#operator_lt)|Porównuje obiekt dostosowanego typu z `m_T`programem .|
|[CAdapt::operator =](#operator_eq)|Przypisuje obiekt dostosowanego typu do `m_T`pliku .|
|[CAdapt::operator ==](#operator_eq_eq)|Porównuje obiekt dostosowanego typu z `m_T`programem .|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAdapt::m_T](#m_t)|Dostosowywane dane.|

## <a name="remarks"></a>Uwagi

`CAdapt`jest prostym szablonem używanym do zawijania klas,`operator &`które na nowo definiują operator adresu ( ), aby zwrócić coś innego niż adres obiektu. Przykłady `CComBSTR`takich klas obejmują ATL `CComPtr`, `CComQIPtr` i klas i kompilatora COM klasy obsługi. `_com_ptr_t`. Wszystkie te klasy ponownie zdefiniować adres operatora, aby zwrócić adres jednego z ich `CComBSTR`elementów członkowskich danych (BSTR w przypadku , i wskaźnik interfejsu w przypadku innych klas).

`CAdapt`"Podstawową rolą jest ukrycie operatora adresu zdefiniowanego przez klasę *T,* ale nadal zachowują cechy klasy dostosowanej. `CAdapt`pełni tę rolę, trzymając członka publicznego, [m_T](#m_t), typu *T*oraz definiując operatory konwersji, operatory porównawcze i konstruktora kopii, aby umożliwić specjalizację, aby były traktowane tak, jakby były obiektami `CAdapt` typu *T*.

Klasa `CAdapt` karty jest przydatna, ponieważ niektóre klasy w stylu kontenera oczekują, że będą mogli uzyskać adresy swoich obiektów zawartych przy użyciu operatora adresu. Ponowne zdefiniowanie operatora address-of może spowodować problemy z tym wymaganiem, zazwyczaj powoduje błędy kompilacji i uniemożliwia wykorzystywanie typu niezaadaptowanego z klasami, które oczekują, że „po prostu ma działać”. `CAdapt`zapewnia sposób na obejście tych problemów.

Zazwyczaj będzie używany, `CAdapt` gdy chcesz `CComBSTR`przechowywać `CComQIPtr`, `_com_ptr_t` `CComPtr`, lub obiektów w klasie w stylu kontenera. Było to najczęściej konieczne dla kontenerów biblioteki standardowej języka C++ przed obsługą standardu C++11, ale kontenery biblioteki standardowej języka C++11 automatycznie działają z typami, które mają przeciążone `operator&()`. Biblioteka standardowa osiąga to przez wewnętrznie za pomocą [std::addressof,](../../standard-library/memory-functions.md#addressof) aby uzyskać prawdziwe adresy obiektów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli.h

## <a name="cadaptcadapt"></a><a name="cadapt"></a>CAdapt::CAdapt

Konstruktory umożliwiają domyślne konstruowanie obiektu karty, skopiowanie z obiektu dostosowanego typu lub skopiowanie go z innego obiektu karty.

```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*Rsrc*<br/>
Zmienna typu dostosowanego do skopiowania do nowo utworzonego obiektu karty.

*rSrCA*<br/>
Obiekt karty, którego zawarte dane powinny być kopiowane (lub przenoszone) do nowo utworzonego obiektu karty.

## <a name="cadaptm_t"></a><a name="m_t"></a>CAdapt::m_T

Przechowuje dane są dostosowywane.

```
T m_T;
```

### <a name="remarks"></a>Uwagi

Ten **publiczny** element członkowski danych jest dostępny bezpośrednio lub pośrednio za pomocą [operatora const T&](#operator_const_t_amp) i operatora T [&](#operator_t_amp).

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a>CAdapt::operator const T&amp;

Zwraca odwołanie **const** do [m_T](#m_t) elementu członkowskiego, dzięki czemu obiekt karty ma być traktowany tak, jakby był obiektem typu *T*.

```
operator const T&() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie **do const** do `m_T`.

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a>CAdapt::operator T&amp;

Zwraca odwołanie do [m_T](#m_t) elementu członkowskiego, dzięki czemu obiekt karty ma być traktowany tak, jakby był obiektem typu *T*.

```
operator T&();
```

### <a name="return-value"></a>Wartość zwracana

Odniesienie do `m_T`.

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a>CAdapt::operator&lt;

Porównuje obiekt dostosowanego typu z [m_T](#m_t).

```
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>Parametry

*Rsrc*<br/>
Odwołanie do obiektu, który ma być porównywany.

### <a name="return-value"></a>Wartość zwracana

Wynik porównania między `m_T` i *rSrc*.

## <a name="cadaptoperator-"></a><a name="operator_eq"></a>CAdapt::operator =

Operator przypisania przypisuje argument *rSrc*do elementu członkowskiego danych [m_T](#m_t) i zwraca bieżący obiekt karty.

```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*Rsrc*<br/>
Odwołanie do obiektu dostosowanego typu do skopiowania.

*rSrCA*<br/>
Odwołanie do obiektu, który ma zostać przeniesiony.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego obiektu.

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a>CAdapt::operator ==

Porównuje obiekt dostosowanego typu z [m_T](#m_t).

```
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>Parametry

*Rsrc*<br/>
Odwołanie do obiektu, który ma być porównywany.

### <a name="return-value"></a>Wartość zwracana

Wynik porównania między *m_T* i *rSrc*.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
