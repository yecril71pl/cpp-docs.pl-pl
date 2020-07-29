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
ms.openlocfilehash: 2ea8fc8a26642abf593c7f4df3928ff90e66e2b3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230003"
---
# <a name="cadapt-class"></a>Klasa CAdapt

Ten szablon jest używany do opakowywania klas, które ponownie definiują operator address-of, aby zwrócić coś innego niż adres obiektu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class CAdapt
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ dostosowany.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAdapt:: CAdapt](#cadapt)|Konstruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAdapt:: operator const T&](#operator_const_t_amp)|Zwraca **`const`** odwołanie do `m_T` .|
|[CAdapt:: operator T&](#operator_t_amp)|Zwraca odwołanie do `m_T` .|
|[CAdapt:: operator <](#operator_lt)|Porównuje obiekt typu dostosowanego z `m_T` .|
|[CAdapt:: operator =](#operator_eq)|Przypisuje obiekt typu dostosowanego do `m_T` .|
|[CAdapt:: operator = =](#operator_eq_eq)|Porównuje obiekt typu dostosowanego z `m_T` .|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAdapt:: m_T](#m_t)|Dostosowywane dane.|

## <a name="remarks"></a>Uwagi

`CAdapt`jest prostym szablonem używanym do zawijania klas, które definiują operator address-of ( `operator &` ), aby zwrócić coś innego niż adres obiektu. Przykładami takich klas są klasy ATL `CComBSTR` , `CComPtr` , i i `CComQIPtr` Klasa obsługi kompilatora com `_com_ptr_t` . W tych klasach wszystkie ponownie definiują operator address-of, aby zwrócić adres jednego z ich składowych danych (BSTR w przypadku `CComBSTR` i wskaźnik interfejsu w przypadku innych klas).

`CAdapt`podstawowa rola to ukrycie operatora address-of zdefiniowanego przez klasę *T*, ale nadal zachowuje charakterystykę przystosowanej klasy. `CAdapt`spełnia tę rolę, przechowując publiczną składową, [m_T](#m_t), typu *T*, i definiując operatory konwersji, operatory porównania i Konstruktor kopiujący, aby zezwolić na traktowanie specjalizacji, tak jakby były `CAdapt` obiektami typu *T*.

Klasa adaptera `CAdapt` jest przydatna, ponieważ niektóre klasy stylu kontenera mogą uzyskać adresy zawartych w nich obiektów przy użyciu operatora address-of. Ponowne zdefiniowanie operatora address-of może spowodować problemy z tym wymaganiem, zazwyczaj powoduje błędy kompilacji i uniemożliwia wykorzystywanie typu niezaadaptowanego z klasami, które oczekują, że „po prostu ma działać”. `CAdapt`pozwala na obejście tych problemów.

Zwykle, `CAdapt` gdy chcesz przechowywać `CComBSTR` , `CComPtr` , `CComQIPtr` , lub `_com_ptr_t` obiekty w klasie stylu kontenera. Jest to najczęściej konieczne w przypadku kontenerów standardowej biblioteki języka C++ przed wsparciem standardu C++ 11, ale Kontenery biblioteki standardowej języka C++ 11 automatycznie pracują z typami, które mają przeciążony `operator&()` . Biblioteka standardowa realizuje ją wewnętrznie przy użyciu [std:: AddressOf](../../standard-library/memory-functions.md#addressof) , aby uzyskać prawdziwe adresy obiektów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli. h

## <a name="cadaptcadapt"></a><a name="cadapt"></a>CAdapt:: CAdapt

Konstruktory umożliwiają Konstruowanie obiektu adaptera, skopiowane z obiektu typu dostosowanego lub skopiowane z innego obiektu adaptera.

```cpp
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Zmienna typu dostosowanego do kopiowania do nowo skonstruowanego obiektu adaptera.

*rSrCA*<br/>
Obiekt karty, którego zawarte dane powinny zostać skopiowane (lub przeniesione) do nowo skonstruowanego obiektu adaptera.

## <a name="cadaptm_t"></a><a name="m_t"></a>CAdapt:: m_T

Przechowuje dane, które są dostosowywane.

```cpp
T m_T;
```

### <a name="remarks"></a>Uwagi

**`public`** Dostęp do tego elementu członkowskiego danych można uzyskać bezpośrednio lub pośrednio z [operatorem const t&](#operator_const_t_amp) i [operatorem t&](#operator_t_amp).

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a>CAdapt:: operator const T&amp;

Zwraca **`const`** odwołanie do elementu członkowskiego [m_T](#m_t) , co umożliwia podtraktowanie obiektu adaptera tak, jakby był obiektem typu *T*.

```cpp
operator const T&() const;
```

### <a name="return-value"></a>Wartość zwracana

**`const`** Odwołanie do `m_T` .

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a>CAdapt:: operator T&amp;

Zwraca odwołanie do elementu członkowskiego [m_T](#m_t) , co umożliwia podtraktowanie obiektu adaptera tak, jakby był obiektem typu *T*.

```cpp
operator T&();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `m_T` .

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a>CAdapt:: operator&lt;

Porównuje obiekt typu dostosowanego z [m_T](#m_t).

```cpp
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odwołanie do obiektu, który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Wynik porównania między `m_T` i *RSRC*.

## <a name="cadaptoperator-"></a><a name="operator_eq"></a>CAdapt:: operator =

Operator przypisania przypisuje argument, *RSRC*do elementu członkowskiego danych [m_T](#m_t) i zwraca bieżący obiekt adaptera.

```cpp
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odwołanie do obiektu, który został dostosowany, do skopiowania.

*rSrCA*<br/>
Odwołanie do obiektu, który ma zostać przeniesiony.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego obiektu.

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a>CAdapt:: operator = =

Porównuje obiekt typu dostosowanego z [m_T](#m_t).

```cpp
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odwołanie do obiektu, który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Wynik porównania między *m_T* i *RSRC*.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
