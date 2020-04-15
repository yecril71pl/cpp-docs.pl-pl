---
title: Platform::Agile, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
ms.openlocfilehash: 0822cef10b199a5bc3b33f116065816e380bf8a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376498"
---
# <a name="platformagile-class"></a>Platform::Agile, klasa

Reprezentuje obiekt, który ma MashalingBehavior=Standard jako obiekt agile, co znacznie zmniejsza szanse na wyjątki wątkowe środowiska wykonawczego. Umożliwia `Agile<T>` nieaskładne obiektu do wywołania lub wywołać z tego samego lub innego wątku. Aby uzyskać więcej informacji, zobacz [Wątki i kierowanie](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
class Agile;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Nazwa typu dla klasy niezwiązanej.

### <a name="remarks"></a>Uwagi

Większość klas w czasie wykonywania systemu Windows są elastyczne. Obiekt agile można wywołać lub być wywoływane przez in-proc lub out-of-proc obiektu w tym samym lub innym wątku. Jeśli obiekt nie jest zwinny, zawiń obiekt `Agile<T>` nieznieasy w obiekcie, który jest elastyczny. Następnie `Agile<T>` obiekt może być zorganizowany, a podstawowy obiekt nieaskładny może być używany.

Klasa `Agile<T>` jest macierzystą, standardową klasą `agile.h`C++ i wymaga . Reprezentuje obiekt niezwięzowy i *kontekst*obiektu Agile. Kontekst określa model wątków obiektu agile i zachowanie organizowania. System operacyjny używa kontekstu do określenia sposobu organizowania obiektu.

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Zwinny::Zwinny](#ctor)|Inicjuje nowe wystąpienie agile klasy.|
|[Zwinny::~Zwinny destruktor](#dtor)|Niszczy bieżące wystąpienie agile klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Zwinny::Pobierz](#get)|Zwraca dojście do obiektu, który jest reprezentowany przez bieżący obiekt Agile.|
|[Zwinny::GetAddressOf](#getaddressof)|Ponownie inicjuje bieżący obiekt Agile, a następnie zwraca adres `T`dojścia do obiektu typu .|
|[Zwinny::GetAddressOfForInOut](#getaddressofforinout)|Zwraca adres dojścia do obiektu reprezentowanego przez bieżący obiekt Agile.|
|[Zwinny::Zwolnij](#release)|Odrzuca obiekt i kontekst obiektu źródłowego bieżącego obiektu Agile.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Zwinny::operator->](#operator-arrow)|Pobiera dojście do obiektu reprezentowanego przez bieżący obiekt Agile.|
|[Zwinny::operator=](#operator-assign)|Przypisuje określoną wartość do bieżącego obiektu Agile.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Object`

`Agile`

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Obszar nazw:** Platformy

**Nagłówek:** agile.h

## <a name="agileagile-constructor"></a><a name="ctor"></a>Zwinny::Zwinny konstruktor

Inicjuje nowe wystąpienie agile klasy.

## <a name="syntax"></a>Składnia

```cpp
Agile();
Agile(T^ object);
Agile(const Agile<T>& object);
Agile(Agile<T>&& object);
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ określony przez parametr nazwy typu szablonu.

*obiekt*<br/>
W drugiej wersji tego konstruktora obiektu używanego do inicjowania nowego agile instancji. W trzeciej wersji obiektu, który jest kopiowany do nowego agile instancji. W czwartej wersji obiektu, który jest przenoszony do nowego agile instancji.

### <a name="remarks"></a>Uwagi

Pierwsza wersja tego konstruktora jest konstruktorem domyślnym. Druga wersja inicjuje nową klasę instancji Agile `object` z obiektu określonego przez parametr. Trzecia wersja jest konstruktorem kopii. Czwarta wersja jest konstruktorem przenoszenia. Ten konstruktor nie może zgłaszać wyjątków.

## <a name="agileagile-destructor"></a><a name="dtor"></a>Zwinny::~Zwinny destruktor

Niszczy bieżące wystąpienie agile klasy.

## <a name="syntax"></a>Składnia

```cpp
~Agile();
```

### <a name="remarks"></a>Uwagi

Ten destruktor zwalnia również obiekt reprezentowany przez bieżący obiekt Agile.

## <a name="agileget-method"></a><a name="get"></a>Zwinny::Pobierz metodę

Zwraca dojście do obiektu, który jest reprezentowany przez bieżący obiekt Agile.

## <a name="syntax"></a>Składnia

```cpp
T^ Get() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu, który jest reprezentowany przez bieżący obiekt Agile.

Typ zwracanej wartości jest w rzeczywistości nieujawnionym typem wewnętrznym. Wygodnym sposobem przechowywania wartości zwracanej jest przypisanie jej do zmiennej zadeklarowanej za pomocą słowa kluczowego **automatycznego** potrącenia typu. Na przykład `auto x = myAgileTvariable->Get();`.

## <a name="agilegetaddressof-method"></a><a name="getaddressof"></a>Agile::Metoda GetAddressOf

Ponownie inicjuje bieżący obiekt Agile, a następnie zwraca adres `T`dojścia do obiektu typu .

## <a name="syntax"></a>Składnia

```cpp
T^* GetAddressOf() throw();
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ określony przez parametr nazwy typu szablonu.

### <a name="return-value"></a>Wartość zwracana

Adres dojścia do obiektu `T`typu .

### <a name="remarks"></a>Uwagi

Ta operacja zwalnia bieżącą reprezentację `T`obiektu typu , jeśli istnieje; ponownie inicjuje członków danych obiektu Agile; uzyskuje bieżący kontekst wątków; a następnie zwraca adres zmiennej dojście do obiektu, która może reprezentować obiekt niezwiązany z agile. Aby spowodować, że wystąpienie klasy Agile będzie reprezentować obiekt, użyj operatora przypisania ([Agile::operator=](#operator-assign)), aby przypisać obiekt do instancji klasy Agile.

## <a name="agilegetaddressofforinout-method"></a><a name="getaddressofforinout"></a>Agile::Metoda GetAddressOfForInOut

Zwraca adres dojścia do obiektu reprezentowanego przez bieżący obiekt Agile.

## <a name="syntax"></a>Składnia

```cpp
T^* GetAddressOfForInOut()  throw();
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ określony przez parametr nazwy typu szablonu.

### <a name="return-value"></a>Wartość zwracana

Adres dojścia do obiektu reprezentowanego przez bieżący obiekt Agile.

### <a name="remarks"></a>Uwagi

Ta operacja uzyskuje bieżącego kontekstu wątku, a następnie zwraca adres dojście do leżącego u podstaw obiektu.

## <a name="agilerelease-method"></a><a name="release"></a>Agile::Metoda zwalniania

Odrzuca obiekt i kontekst obiektu źródłowego bieżącego obiektu Agile.

## <a name="syntax"></a>Składnia

```cpp
void Release() throw();
```

### <a name="remarks"></a>Uwagi

Obiekt i kontekst obiektu i kontekstu bieżącego obiektu Agile są odrzucane, jeśli istnieją, a następnie wartość obiektu Agile jest ustawiona na wartość null.

## <a name="agileoperator-gt-operator"></a><a name="operator-arrow"></a>Zwinny::operator-&gt; Operator

Pobiera dojście do obiektu reprezentowanego przez bieżący obiekt Agile.

## <a name="syntax"></a>Składnia

```cpp
T^ operator->() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu reprezentowanego przez bieżący obiekt Agile.

Ten operator faktycznie zwraca nieujawniony typ wewnętrzny. Wygodnym sposobem przechowywania wartości zwracanej jest przypisanie jej do zmiennej zadeklarowanej za pomocą słowa kluczowego **automatycznego** potrącenia typu.

## <a name="agileoperator-operator"></a><a name="operator-assign"></a>Zwinny::operator= Operator

Przypisuje określony obiekt do bieżącego obiektu Agile.

## <a name="syntax"></a>Składnia

```cpp
Agile<T> operator=( T^ object ) throw();
Agile<T> operator=( const Agile<T>& object ) throw();
Agile<T> operator=( Agile<T>&& object ) throw();
T^ operator=( IUnknown* lp ) throw();
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ określony przez typa szablonu.

*obiekt*<br/>
Obiekt lub uchwyt do obiektu, który jest kopiowany lub przenoszony do bieżącego obiektu Agile.

*Lp*<br/>
Wskaźnik interfejsu IUnknown obiektu.

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu typu`T`

### <a name="remarks"></a>Uwagi

Pierwsza wersja operatora przypisania kopiuje dojście do typu odwołania do bieżącego obiektu Agile. Druga wersja kopiuje odwołanie do typu Agile do bieżącego obiektu Agile. Trzecia wersja przenosi typ Agile do bieżącego obiektu Agile. Czwarta wersja przenosi wskaźnik do obiektu COM do bieżącego obiektu Agile.

Operacja przypisania automatycznie upiera się w kontekście bieżącego obiektu Agile.

## <a name="see-also"></a>Zobacz też

[Obszar nazw platformy](platform-namespace-c-cx.md)
