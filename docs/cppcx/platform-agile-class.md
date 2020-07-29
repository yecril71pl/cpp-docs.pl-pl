---
title: 'Platform:: Agile — Klasa'
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
ms.openlocfilehash: 839002a614b54990fdc9180fa06737ff43039a4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226942"
---
# <a name="platformagile-class"></a>Platform:: Agile — Klasa

Reprezentuje obiekt, który ma MashalingBehavior = standardowy jako obiekt Agile, co znacznie zmniejsza prawdopodobieństwo wystąpienia wyjątków wątku środowiska uruchomieniowego. `Agile<T>`Umożliwia wywoływanie obiektu nieagile lub wywoływanie z, tego samego lub innego wątku. Aby uzyskać więcej informacji, zobacz [wątkowość i kierowanie](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
class Agile;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Nazwa typu dla klasy nieagile.

### <a name="remarks"></a>Uwagi

Większość klas w środowisko wykonawcze systemu Windows są Agile. Obiekt Agile może wywołać, lub wywołać przez, obiekt w procesie lub out-of-proc w tym samym lub innym wątku. Jeśli obiekt nie jest Agile, zawiń obiekt nieagile w `Agile<T>` obiekcie, który jest Agile. Następnie `Agile<T>` obiekt może być zorganizowany i można użyć bazowego obiektu niebędącego Agile.

`Agile<T>`Klasa jest natywną, standardową klasą C++ i wymaga `agile.h` . Reprezentuje obiekt nieagile i *kontekst*obiektu Agile. Kontekst Określa model wątkowości obiektu Agile i zachowanie organizowania. System operacyjny używa kontekstu, aby określić sposób organizowania obiektu.

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Agile:: Agile](#ctor)|Inicjuje nowe wystąpienie klasy Agile.|
|[Agile:: ~ Agile — destruktor](#dtor)|Niszczy bieżące wystąpienie klasy Agile.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Agile:: Get](#get)|Zwraca dojście do obiektu, który jest reprezentowany przez bieżący obiekt Agile.|
|[Agile:: GetAddressOf](#getaddressof)|Ponownie inicjuje bieżący obiekt Agile, a następnie zwraca adres dojścia do obiektu typu `T` .|
|[Agile:: GetAddressOfForInOut](#getaddressofforinout)|Zwraca adres dojścia do obiektu reprezentowanego przez bieżący obiekt Agile.|
|[Agile:: Release](#release)|Odrzuca bieżący obiekt i kontekst obiektu Agile.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Agile:: operator->](#operator-arrow)|Pobiera dojście do obiektu reprezentowanego przez bieżący obiekt Agile.|
|[Agile:: operator =](#operator-assign)|Przypisuje określoną wartość do bieżącego obiektu Agile.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Object`

`Agile`

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** System Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Przestrzeń nazw:** Platformach

**Nagłówek:** Agile. h

## <a name="agileagile-constructor"></a><a name="ctor"></a>Agile:: Agile — Konstruktor

Inicjuje nowe wystąpienie klasy Agile.

## <a name="syntax"></a>Składnia

```cpp
Agile();
Agile(T^ object);
Agile(const Agile<T>& object);
Agile(Agile<T>&& object);
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ określony przez parametr TypeName szablonu.

*object*<br/>
W drugiej wersji tego konstruktora obiekt używany do zainicjowania nowego wystąpienia Agile. W trzeciej wersji obiekt, który jest kopiowany do nowego wystąpienia Agile. W czwartej wersji obiekt, który jest przenoszony do nowego wystąpienia Agile.

### <a name="remarks"></a>Uwagi

Pierwsza wersja tego konstruktora jest konstruktorem domyślnym. Druga wersja Inicjuje nową klasę wystąpienia Agile z obiektu określonego przez `object` parametr. Trzecia wersja jest konstruktorem kopiowania. Czwarta wersja jest konstruktorem przenoszenia. Ten konstruktor nie może zgłosić wyjątków.

## <a name="agileagile-destructor"></a><a name="dtor"></a>Agile:: ~ Agile — destruktor

Niszczy bieżące wystąpienie klasy Agile.

## <a name="syntax"></a>Składnia

```cpp
~Agile();
```

### <a name="remarks"></a>Uwagi

Ten destruktor zwalnia również obiekt reprezentowany przez bieżący obiekt Agile.

## <a name="agileget-method"></a><a name="get"></a>Agile:: Get — Metoda

Zwraca dojście do obiektu, który jest reprezentowany przez bieżący obiekt Agile.

## <a name="syntax"></a>Składnia

```cpp
T^ Get() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu reprezentowanego przez bieżący obiekt Agile.

Typ wartości zwracanej jest w rzeczywistości niejawnym typem wewnętrznym. Wygodnym sposobem przechowywania wartości zwracanej jest przypisanie jej do zmiennej, która jest zadeklarowana za pomocą **`auto`** słowa kluczowego odejmowania. Na przykład `auto x = myAgileTvariable->Get();`.

## <a name="agilegetaddressof-method"></a><a name="getaddressof"></a>Agile:: GetAddressOf — Metoda

Ponownie inicjuje bieżący obiekt Agile, a następnie zwraca adres dojścia do obiektu typu `T` .

## <a name="syntax"></a>Składnia

```cpp
T^* GetAddressOf() throw();
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ określony przez parametr TypeName szablonu.

### <a name="return-value"></a>Wartość zwracana

Adres dojścia do obiektu typu `T` .

### <a name="remarks"></a>Uwagi

Ta operacja zwalnia bieżącą reprezentację obiektu typu `T` , jeśli istnieje; ponownie inicjuje składowe danych obiektu Agile; uzyskuje bieżący kontekst wątku, a następnie zwraca adres zmiennej dojścia do obiektu, która może reprezentować obiekt niebędący Agile. Aby spowodować, że wystąpienie klasy Agile reprezentuje obiekt, użyj operatora przypisania ([Agile:: operator =](#operator-assign)), aby przypisać obiekt do wystąpienia klasy Agile.

## <a name="agilegetaddressofforinout-method"></a><a name="getaddressofforinout"></a>Agile:: GetAddressOfForInOut, Metoda

Zwraca adres dojścia do obiektu reprezentowanego przez bieżący obiekt Agile.

## <a name="syntax"></a>Składnia

```cpp
T^* GetAddressOfForInOut()  throw();
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ określony przez parametr TypeName szablonu.

### <a name="return-value"></a>Wartość zwracana

Adres dojścia do obiektu reprezentowanego przez bieżący obiekt Agile.

### <a name="remarks"></a>Uwagi

Ta operacja uzyskuje bieżący kontekst wątku, a następnie zwraca adres dojścia do obiektu źródłowego.

## <a name="agilerelease-method"></a><a name="release"></a>Agile:: Release — Metoda

Odrzuca bieżący obiekt i kontekst obiektu Agile.

## <a name="syntax"></a>Składnia

```cpp
void Release() throw();
```

### <a name="remarks"></a>Uwagi

Obiekt źródłowy i kontekst bieżącego obiektu Agile są odrzucane, jeśli istnieją, a następnie wartość obiektu Agile jest ustawiona na wartość null.

## <a name="agileoperator-gt-operator"></a><a name="operator-arrow"></a>Agile:: operator-— &gt; operator

Pobiera dojście do obiektu reprezentowanego przez bieżący obiekt Agile.

## <a name="syntax"></a>Składnia

```cpp
T^ operator->() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu reprezentowane przez bieżący obiekt Agile.

Ten operator faktycznie zwraca niejawny typ wewnętrzny. Wygodnym sposobem przechowywania wartości zwracanej jest przypisanie jej do zmiennej, która jest zadeklarowana za pomocą **`auto`** słowa kluczowego odejmowania.

## <a name="agileoperator-operator"></a><a name="operator-assign"></a>Agile:: operator = — operator

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
Typ określony przez właściwość TypeName szablonu.

*object*<br/>
Obiekt lub dojście do obiektu, który jest kopiowany lub przenoszony do bieżącego obiektu Agile.

*LP*<br/>
Wskaźnik interfejsu IUnknown obiektu.

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu typu`T`

### <a name="remarks"></a>Uwagi

Pierwsza wersja operatora przypisania kopiuje dojście do typu referencyjnego do bieżącego obiektu Agile. Druga wersja kopiuje odwołanie do typu Agile do bieżącego obiektu Agile. Trzecia wersja przenosi typ Agile do bieżącego obiektu Agile. Czwarta wersja przenosi wskaźnik do obiektu COM do bieżącego obiektu Agile.

Operacja przypisania automatycznie utrzymuje kontekst bieżącego obiektu Agile.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](platform-namespace-c-cx.md)
