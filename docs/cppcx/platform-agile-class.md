---
title: Platform::Agile, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
dev_langs:
- C++
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3745ead4fec8466df3f164c415b21d98f68c0ef7
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109787"
---
# <a name="platformagile-class"></a>Platform::Agile, klasa

Reprezentuje obiekt, który ma MashalingBehavior = Standard jako obiekt agile, co znacznie zmniejsza prawdopodobieństwo, że wątki wyjątki środowiska uruchomieniowego. `Agile<T>` Umożliwia-agile obiekt, aby wywołać lub być wywoływana z tym samym lub innym wątku. Aby uzyskać więcej informacji, zobacz [wątkowość i Marshaling](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
class Agile;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Element typename-agile klasy.

### <a name="remarks"></a>Uwagi

Większość klas środowiska wykonawczego Windows to agile. Obiekt agile można wywołać lub być wywoływany przez obiekt wewnątrzprocesową lub poza poza procesem, w tym samym lub innym wątku. Jeśli obiekt nie jest agile, opakowywanie-agile obiektu w `Agile<T>` obiektu, który jest agile. A następnie `Agile<T>` obiekt może być organizowany i podstawowych-agile obiekt może być używany.

`Agile<T>` Klasa jest klasą natywnych, standard C++ i wymaga `agile.h`. Reprezentuje obiekt agile i obiekt Agile *kontekstu*. Kontekst określa model wątkowości i zachowanie marshalingu obiektu agile. System operacyjny używa kontekstu ustalenie sposobu organizowania obiektu.

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Agile::Agile](#ctor)|Inicjuje nowe wystąpienie klasy Agile.|
|[Agile:: ~ Agile — destruktor](#dtor)|Likwiduje bieżące wystąpienia klasy Agile.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Agile::Get](#get)|Zwraca uchwyt do obiektu, który jest reprezentowany przez bieżący obiekt Agile.|
|[Agile::GetAddressOf](#getaddressof)|Ponownie inicjuje bieżący obiekt Agile, a następnie zwraca adres dojścia do obiektu typu `T`.|
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|Zwraca adres dojścia do obiektu reprezentowanego przez bieżący obiekt Agile.|
|[Agile::Release](#release)|Usuwa obiekt źródłowy i kontekstu bieżącego obiektu Agile.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Agile::operator ->](#operator-arrow)|Pobiera uchwyt do obiektu reprezentowanego przez bieżący obiekt Agile.|
|[Agile::operator =](#operator-assign)|Przypisuje określoną wartość, jak bieżący obiekt Agile.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Object`

`Agile`

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** systemu Windows 8

**Minimalna obsługiwana serwera:** systemu Windows Server 2012

**Namespace:** platformy

**Nagłówek:** agile.h

## <a name="ctor"></a>  Konstruktor Agile::Agile

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
Typ określony przez parametr typename szablonu.

*object*<br/>
W drugiej wersji tego konstruktora obiekt służący do inicjuje nowe wystąpienie Agile. W trzeciej wersji obiekt, który jest kopiowany do nowego wystąpienia Agile. W czwartym wersja obiektu, który jest przenoszony do nowego wystąpienia Agile.

### <a name="remarks"></a>Uwagi

Pierwsza wersja tego konstruktora jest konstruktor domyślny. Druga wersja inicjuje nową klasę Agile wystąpienia w obiekcie określonym przez `object` parametru. Trzecia wersja jest Konstruktor kopiujący. Czwarta wersja jest konstruktora przenoszącego. Ten konstruktor nie może zgłaszać wyjątki.

## <a name="dtor"></a>  Agile:: ~ Agile — destruktor

Likwiduje bieżące wystąpienia klasy Agile.

## <a name="syntax"></a>Składnia

```cpp
~Agile();
```

### <a name="remarks"></a>Uwagi

Ten destruktor zwalnia również obiekt reprezentowany przez bieżący obiekt Agile.

## <a name="get"></a>   Metoda Agile::Get

Zwraca uchwyt do obiektu, który jest reprezentowany przez bieżący obiekt Agile.

## <a name="syntax"></a>Składnia

```cpp
T^ Get() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu, który jest reprezentowany przez bieżący obiekt Agile.

Typ wartości zwracanej jest faktycznie niejawne typu wewnętrznego. Jest to wygodny sposób przechowywania wartości zwracanej, przypisać ją do zmiennej, która jest zadeklarowana za pomocą **automatycznie** słowem kluczowym dedukcji typu. Na przykład `auto x = myAgileTvariable->Get();`.

## <a name="getaddressof"></a>  Metoda Agile::GetAddressOf

Ponownie inicjuje bieżący obiekt Agile, a następnie zwraca adres dojścia do obiektu typu `T`.

## <a name="syntax"></a>Składnia

```cpp
T^* GetAddressOf() throw();
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ określony przez parametr typename szablonu.

### <a name="return-value"></a>Wartość zwracana

Adres dojścia do obiektu typu `T`.

### <a name="remarks"></a>Uwagi

Ta operacja wydaje reprezentujący bieżący obiekt typu `T`, jeśli występują; ponownie inicjuje elementy członkowskie danych obiektu Agile; uzyskuje bieżącego kontekstu wątkowości; a następnie zwraca adres zmiennej uchwytu do obiektu, który może reprezentować Obiekt agile. Aby spowodować wystąpienie klasy Agile, które reprezentują obiektu, należy użyć operatora przypisania ([Agile::operator =](#operator-assign)) można przypisać obiekt do wystąpienia klasy Agile.

## <a name="getaddressofforinout"></a>  Metoda Agile::GetAddressOfForInOut

Zwraca adres dojścia do obiektu reprezentowanego przez bieżący obiekt Agile.

## <a name="syntax"></a>Składnia

```cpp
T^* GetAddressOfForInOut()  throw();
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ określony przez parametr typename szablonu.

### <a name="return-value"></a>Wartość zwracana

Adres dojścia do obiektu reprezentowanego przez bieżący obiekt Agile.

### <a name="remarks"></a>Uwagi

Ta operacja uzyskuje bieżący kontekst wątku, a następnie zwraca adres dojścia do obiektu źródłowego.

## <a name="release"></a>  Metoda Agile::Release

Usuwa obiekt źródłowy i kontekstu bieżącego obiektu Agile.

## <a name="syntax"></a>Składnia

```cpp
void Release() throw();
```

### <a name="remarks"></a>Uwagi

Obiekt źródłowy i kontekstu bieżącego obiektu Agile są usuwane, jeśli są obecne, a następnie Agile obiektu ma wartość null.

## <a name="operator-arrow"></a>  Agile::operator -&gt; — Operator

Pobiera uchwyt do obiektu reprezentowanego przez bieżący obiekt Agile.

## <a name="syntax"></a>Składnia

```cpp
T^ operator->() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu reprezentowanego przez bieżący obiekt Agile.

Ten operator zwraca faktycznie niejawne typu wewnętrznego. Jest to wygodny sposób przechowywania wartości zwracanej, przypisać ją do zmiennej, która jest zadeklarowana za pomocą **automatycznie** słowem kluczowym dedukcji typu.

## <a name="operator-assign"></a>  Agile::operator = — Operator

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
Typ określony przez nazwę typu szablonu.

*object*<br/>
Obiekt lub uchwytu do obiektu, który jest kopiowany lub przenoszony do bieżącego obiektu Agile.

*LP*<br/>
Wskaźnik interfejsu IUnknown obiektu.

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu typu `T`

### <a name="remarks"></a>Uwagi

Pierwsza wersja operator przypisania kopiuje dojścia do typu odwołania, jak bieżący obiekt Agile. Drugi kopie wersji typu odwołanie do zwinnego projektowania, jak bieżący obiekt Agile. Trzeci wersji przenosi wpisz Agile do bieżącego obiektu Agile. Czwarta wersja przesuwa wskaźnik do obiektu COM, jak bieżący obiekt Agile.

Operacja przypisania automatycznie utrzymuje kontekst bieżącego obiektu Agile.

## <a name="see-also"></a>Zobacz też

[Namespace platformy](platform-namespace-c-cx.md)