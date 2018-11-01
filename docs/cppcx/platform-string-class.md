---
title: Platform::String, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::String::String
- VCCORLIB/Platform::String::Begin
- VCCORLIB/Platform::String::CompareOrdinal
- VCCORLIB/Platform::String::Concat
- VCCORLIB/Platform::String::Data
- VCCORLIB/Platform::String::Dispose
- VCCORLIB/Platform::String::End
- VCCORLIB/Platform::String::Equals
- VCCORLIB/Platform::String::GetHashCode
- VCCORLIB/Platform::String::IsEmpty
- VCCORLIB/Platform::String::IsFastPass
- VCCORLIB/Platform::String::Length
- VCCORLIB/Platform::String::ToString
helpviewer_keywords:
- Platform::String
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
ms.openlocfilehash: ef9838fa8a6a34eac1d2d3531ff93fb124c81d4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607041"
---
# <a name="platformstring-class"></a>Platform::String, klasa

Reprezentuje sekwencyjną kolekcją znaków Unicode, który jest używany do reprezentowania tekstu. Aby uzyskać więcej informacji i przykładów, zobacz [ciągi](../cppcx/strings-c-cx.md).

## <a name="syntax"></a>Składnia

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>Iteratory

Dwie funkcje iteratora, które nie należą do klasy String, mogą być używane z `std::for_each` funkcji szablonu, można wyliczyć znaków w obiekcie String.

|Element członkowski|Opis|
|------------|-----------------|
|`const char16* begin(String^ s)`|Zwraca wskaźnik do początku określonego obiektu ciągu.|
|`const char16* end(String^ s)`|Zwraca wskaźnik poza końcem z określonym obiektem ciągu.|

### <a name="members"></a>Elementy członkowskie

Klasa String dziedziczy z obiektu i interfejs IDisposable, IEquatable i IPrintable interfejsów.

Klasa String ma również następujące rodzaje elementów członkowskich.

**Konstruktory**

|Element członkowski|Opis|
|------------|-----------------|
|[String::String](#ctor)|Inicjuje nowe wystąpienie klasy String.|

**Metody**

Klasa String dziedziczy metodę Equals(), Finalize(), element GetHashCode(), wartości GetType(), MemberwiseClose() i ToString() metody z [Platform::Object, klasa](../cppcx/platform-object-class.md). Ciąg zawiera również następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[String::BEGIN](#begin)|Zwraca wskaźnik do początku bieżącego ciągu.|
|[String::CompareOrdinal](#compareordinal)|Porównuje dwa `String` obiektów wyniku obliczenia wartości liczbowe odpowiadające im znaki w dwa ciągi, reprezentowane przez obiekty.|
|[String::concat](#concat)|Łączy wartości dwóch obiektów w postaci ciągów.|
|[String::Data](#data)|Zwraca wskaźnik do początku bieżącego ciągu.|
|[String::Dispose](#dispose)|Zwalnia lub zwalnia zasoby.|
|[String::end](#end)|Zwraca wskaźnik poza końcem ciągu bieżącego.|
|[String::Equals](#equals)|Wskazuje, czy określony obiekt jest taki sam, jak bieżący obiekt.|
|[String::GetHashCode](#gethashcode)|Zwraca kod skrótu dla tego wystąpienia.|
|[String::IsEmpty](#isempty)|Wskazuje, czy bieżący obiekt ciąg jest pusty.|
|[String::IsFastPass](#isfastpass)|Wskazuje, czy bieżący obiekt ciągu jest uczestnikiem *szybko przekazywany* operacji. W szybkim przekazać operacji, zliczanie odwołań jest zawieszone.|
|[String::Length](#length)|Pobiera bieżący obiekt ciągu.|
|[String::toString](#tostring)|Zwraca obiekt ciągu, którego wartość jest taka sama jak bieżący ciąg.|

**Operatory**

Klasa String ma następujące operatory.

|Element członkowski|Opis|
|------------|-----------------|
|[String::operator == — Operator](#operator-equality)|Wskazuje, czy dwa obiekty ciągu określonego mają taką samą wartość.|
|[operator + — Operator](#operator-plus)|Łączy dwa obiekty ciąg do nowego obiektu ciągu.|
|[String::operator > — Operator](#operator-greater-than)|Wskazuje, czy wartość jeden obiekt na ciąg znaków jest większa niż wartość drugiej obiekt ciągu.|
|[String::operator > = — Operator](#operator-greater-than-or-equals)|Wskazuje, czy wartość jeden obiekt na ciąg znaków jest większa lub równa wartości drugiego obiektu String.|
|[String::operator! = — Operator](#operator-inequality)|Wskazuje, czy dwa obiekty ciągu określonego mają różne wartości.|
|[String::operator < — Operator](#operator-less-than)|Wskazuje, czy wartość jeden obiekt ciągu jest mniejsza niż wartość drugiego obiektu String.|

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** systemu Windows 8

**Minimalna obsługiwana serwera:** systemu Windows Server 2012

**Namespace:** platformy

**Nagłówek** vccorlib.h (domyślnie)

## <a name="begin"></a>  Metoda String::BEGIN

Zwraca wskaźnik do początku bieżącego ciągu.

### <a name="syntax"></a>Składnia

```cpp
char16* Begin();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku bieżącego ciągu.

## <a name="compareordinal"></a>  Metoda String::CompareOrdinal

Porównuje dwa `String` obiektów wyniku obliczenia wartości liczbowe odpowiadające im znaki w dwa ciągi, reprezentowane przez obiekty.

### <a name="syntax"></a>Składnia

```cpp
int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy ciąg obiektu.

*str2*<br/>
Drugi obiekt ciągu.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita wskazująca relację między dwa atrybuty porównania. Poniższa tabela zawiera listę możliwych wartości zwracanych.

|Wartość|Warunek|
|-----------|---------------|
|-1|`str1` jest mniejsza niż `str2`.|
|0|`str1` jest to `str2`.|
|1|`str1` jest większa niż `str2`.|

## <a name="concat"></a>  Metoda String::concat

Łączy wartości dwóch obiektów w postaci ciągów.

### <a name="syntax"></a>Składnia

```cpp
String^ Concat( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy ciąg obiektu lub `null`.

*str2*<br/>
Drugi obiekt ciągu lub `null`.

### <a name="return-value"></a>Wartość zwracana

Nowy ciąg ^ obiektu, którego wartość jest połączenie wartości występujących z `str1` i `str2`.

Jeśli `str1` jest `null` i `str2` nie jest dostępna, `str1` jest zwracana. Jeśli `str2` jest `null` i `str1` nie jest dostępna, `str2` jest zwracana. Jeśli `str1` i `str2` są `null`, pusty ciąg (L"") jest zwracany.

## <a name="data"></a>  Metoda String::Data

Zwraca wskaźnik do początku buforu danych obiektu w postaci tablicy stylu C z `char16` (`wchar_t`) elementów.

### <a name="syntax"></a>Składnia

```
const char16* Data();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku `const char16` tablicy znaków Unicode (`char16` jest element typedef dla `wchar_t`).

### <a name="remarks"></a>Uwagi

Ta metoda służy do konwersji z `Platform::String^` do `wchar_t*`. Gdy `String` obiekt wykracza poza zakres, wskaźnika danych już nie może być nieprawidłowy. Do przechowywania danych poza okres istnienia oryginału `String` obiektu, należy użyć [wcscpy_s —](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) do kopiowania tablicy do pamięci, która została przydzielona samodzielnie.

## <a name="dispose"></a>  Metoda String::Dispose

Zwalnia lub zwalnia zasoby.

### <a name="syntax"></a>Składnia

```cpp
virtual override void Dispose();
```

## <a name="end"></a>  Metoda String::end

Zwraca wskaźnik poza końcem ciągu bieżącego.

### <a name="syntax"></a>Składnia

```cpp
char16* End();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do poza końcem ciągu bieżącego.

### <a name="remarks"></a>Uwagi

Metoda End() zwraca Begin() i długości.

## <a name="equals"></a>  Metoda String::Equals

Wskazuje, czy określony ciąg ma taką samą wartość jak bieżący obiekt.

### <a name="syntax"></a>Składnia

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `str` jest taki sam jak bieżący obiekt; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta metoda jest odpowiednikiem [String::CompareOrdinal](#compareordinal). W pierwsze przeciążenie jest oczekiwany `str` parametru może być rzutowany na ciąg ^ obiektu.

## <a name="gethashcode"></a>  Metoda String::GetHashCode

Zwraca kod skrótu dla tego wystąpienia.

### <a name="syntax"></a>Składnia

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>Wartość zwracana

Kod skrótu dla tego wystąpienia.

## <a name="isempty"></a>  Metoda String::IsEmpty

Wskazuje, czy bieżący obiekt ciąg jest pusty.

### <a name="syntax"></a>Składnia

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli bieżący `String` obiekt jest **null** lub pusty ciąg znaków (L""); w przeciwnym razie **false**.

## <a name="isfastpass"></a>  Metoda String::IsFastPass

Wskazuje, czy bieżący obiekt ciągu jest uczestnikiem *szybko przekazywany* operacji. W szybkim przekazać operacji, zliczanie odwołań jest zawieszone.

### <a name="syntax"></a>Składnia

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli bieżące `String` obiekt jest w przeszłości fast; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

W wywołaniu funkcji, której obiekt zliczonych odwołań jest parametrem i wywołana funkcja odczytuje tylko tego obiektu kompilator można bezpiecznie zawiesić zliczaniu odwołań i zwiększenia wydajności wywoływania. Nie ma nic, które są przydatne, że Twój kod można zrobić za pomocą tej właściwości. System obsługuje wszystkie szczegółowe informacje.

## <a name="length"></a>  Metoda String::length

Pobiera liczbę znaków w bieżącym `String` obiektu.

### <a name="syntax"></a>Składnia

```cpp
unsigned int Length();
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaków w bieżącym `String` obiektu.

### <a name="remarks"></a>Uwagi

Długość ciągu, bez znaków wynosi zero. Długość ciągu następujące wynosi 5:

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

Tablica znaków zwrócona przez [String::Data](#data) ma jeden dodatkowy znak, który jest powodujący zakończenie o wartości NULL ani '\0'. Ten znak jest również długości dwóch bajtów.

## <a name="operator-plus"></a>  String::operator + — Operator

Łączy dwa [ciąg](../cppcx/platform-string-class.md) obiektów w nowym [ciąg](../cppcx/platform-string-class.md) obiektu.

### <a name="syntax"></a>Składnia

```cpp
bool String::operator+( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy `String` obiektu.

*str2*<br/>
Drugi `String` obiektu, którego zawartość zostanie dołączona do `str1`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *str1* jest równa *str2*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ten operator tworzy `String^` obiekt, który zawiera dane z dwóch argumentów operacji. Go użyć jako udogodnienie Jeśli najwyższej wydajności nie ma kluczowe znaczenie. Kilka wywołań "`+`" w funkcji prawdopodobnie nie będą zauważalne, ale jeśli modyfikujesz dużych obiektów lub danych tekstowych w pętli, użyj standardowych mechanizmów C++ i typów.

##  <a name="operator-equality"></a> String::operator == — Operator

Wskazuje, czy dwa określone obiekty ciąg mieć takiej samej wartości tekstowej.

### <a name="syntax"></a>Składnia

```cpp
bool String::operator==( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy `String` obiekt do porównania.

*str2*<br/>
Drugi `String` obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli zawartość `str1` są równe `str2`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ten operator jest odpowiednikiem [String::CompareOrdinal](#compareordinal).

##  <a name="operator-greater-than"></a>  String::operator&gt;

Wskazuje, czy wartość jednego `String` obiekt jest większy niż wartość drugiej `String` obiektu.

### <a name="syntax"></a>Składnia

```cpp
bool String::operator>( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy `String` obiektu.

*str2*<br/>
Drugi `String` obiektu.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wartość `str1` jest większa niż wartość `str2`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ten operator jest odpowiednikiem jawne wywołanie [String::CompareOrdinal](#compareordinal) i uzyskuje wynik większą niż zero.

## <a name="operator-greater-than-or-equals"></a> String::operator&gt;=

Wskazuje, czy wartość jednego `String` obiektów jest większa niż lub równa wartości drugiego `String` obiektu.

### <a name="syntax"></a>Składnia

```cpp
bool String::operator>=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy `String` obiektu.

*str2*<br/>
Drugi `String` obiektu.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wartość `str1` jest większa niż lub równa wartości `str2`; w przeciwnym razie **false**.

## <a name="operator-inequality"></a> String::operator! =

Wskazuje, czy dwa określona `String` obiekty mają różne wartości.

### <a name="syntax"></a>Składnia

```cpp
bool String::operator!=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy `String` obiekt do porównania.

*str2*<br/>
Drugi `String` obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `str1` nie jest równa `str2`; w przeciwnym razie **false**.

## <a name="operator-less-than"></a> String::operator&lt;

Wskazuje, czy wartość jednego `String` obiekt jest mniejszy niż wartość drugiej `String` obiektu.

### <a name="syntax"></a>Składnia

```cpp
bool String::operator<( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy `String` obiektu.

*str2*<br/>
Drugi `String` obiektu.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wartość *str1* jest mniejsza niż wartość *str2*; w przeciwnym razie **false**.

## <a name="ctor"></a> Konstruktor String::String

Inicjuje nowe wystąpienie klasy `String` klasy przy użyciu kopii danych w ciągu wejściowym.

### <a name="syntax"></a>Składnia

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>Parametry

*s*<br/>
Ciąg znaków dwubajtowych, które inicjuje ciąg. char16

*N*<br/>
Liczba, która określa długość ciągu.

### <a name="remarks"></a>Uwagi

Jeśli wydajność ma kluczowe znaczenie i kontrolować okres istnienia ciąg źródłowy, możesz użyć [Platform::StringReference](../cppcx/platform-stringreference-class.md) zamiast ciągu.
### <a name="example"></a>Przykład

```cpp
String^ s = L"Hello!";
```

## <a name="tostring"></a> String::toString

Zwraca `String` obiektu, którego wartość jest taka sama jak bieżący ciąg.

### <a name="syntax"></a>Składnia

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>Wartość zwracana

Element `String` obiektu, którego wartość jest taka sama jak bieżący ciąg.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)