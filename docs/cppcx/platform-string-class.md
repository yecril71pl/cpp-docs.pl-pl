---
title: 'Platform:: String — Klasa'
ms.date: 10/16/2019
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
ms.openlocfilehash: f8b5888ee2d28a3d870b5f0eeab143b189c88180
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87185258"
---
# <a name="platformstring-class"></a>Platform:: String — Klasa

Reprezentuje sekwencyjną kolekcję znaków Unicode, która jest używana do reprezentowania tekstu. Aby uzyskać więcej informacji i przykładów, zobacz [ciągi](../cppcx/strings-c-cx.md).

## <a name="syntax"></a>Składnia

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>Iteratory

Dwie funkcje iteratora, które nie są elementami członkowskimi klasy String, mogą być używane z `std::for_each` funkcją Template do wyliczania znaków w obiekcie String.

|Członek|Opis|
|------------|-----------------|
|`const char16* begin(String^ s)`|Zwraca wskaźnik do początku określonego obiektu ciągu.|
|`const char16* end(String^ s)`|Zwraca wskaźnik poza końcem określonego obiektu ciągu.|

## <a name="members"></a>Elementy członkowskie

Klasa String dziedziczy z obiektu i interfejsów IDisposable, IEquatable i IPrintable.

Klasa String ma również następujące typy elementów członkowskich.

### <a name="constructors"></a>Konstruktory

|Członek|Opis|
|------------|-----------------|
|[String:: String](#ctor)|Inicjuje nowe wystąpienie klasy String.|

### <a name="methods"></a>Metody

Klasa String dziedziczy metody Equals (), Finalize (), GetHashCode (), GetType (), MemberwiseClose () i ToString () z [klasy platform:: Object](../cppcx/platform-object-class.md). Ciąg ma również następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[String:: BEGIN](#begin)|Zwraca wskaźnik do początku bieżącego ciągu.|
|[String:: CompareOrdinal](#compareordinal)|Porównuje dwa `String` obiekty, oceniając wartości liczbowe odpowiednich znaków w dwóch wartościach ciągu reprezentowanych przez obiekty.|
|[String:: Concat](#concat)|Łączy wartości dwóch obiektów String.|
|[Ciąg::D ATA](#data)|Zwraca wskaźnik do początku bieżącego ciągu.|
|[Ciąg::D isułożenia](#dispose)|Zwalnia lub zwalnia zasoby.|
|[String:: end](#end)|Zwraca wskaźnik poza końcem bieżącego ciągu.|
|[Ciąg:: Equals](#equals)|Wskazuje, czy określony obiekt jest równy bieżącemu obiektowi.|
|[String:: GetHashCode](#gethashcode)|Zwraca wartość skrótu dla tego wystąpienia.|
|[String:: IsEmpty](#isempty)|Wskazuje, czy bieżący obiekt ciągu jest pusty.|
|[String:: IsFastPass](#isfastpass)|Wskazuje, czy bieżący obiekt ciągu uczestniczy w operacji *szybkiego przekazywania* . W przypadku operacji szybkiego przebiegu zliczanie odwołań jest zawieszone.|
|[String:: length](#length)|Pobiera długość bieżącego obiektu ciągu.|
|[String:: ToString](#tostring)|Zwraca obiekt String, którego wartość jest taka sama jak bieżący ciąg.|

### <a name="operators"></a>Operatory

Klasa String ma następujące operatory.

|Członek|Opis|
|------------|-----------------|
|[String:: operator = = — operator](#operator-equality)|Wskazuje, czy dwa określone obiekty ciągu mają tę samą wartość.|
|[operator + — operator](#operator-plus)|Łączy dwa obiekty String z nowym obiektem ciągu.|
|[String:: operator> — operator](#operator-greater-than)|Wskazuje, czy wartość jednego obiektu ciągu jest większa niż wartość drugiego obiektu ciągu.|
|[String:: operator>= — operator](#operator-greater-than-or-equals)|Wskazuje, czy wartość jednego obiektu ciągu jest większa lub równa wartości drugiego obiektu ciągu.|
|[String:: operator! = — operator](#operator-inequality)|Wskazuje, czy dwa określone obiekty ciągu mają różne wartości.|
|[String:: operator< — operator](#operator-less-than)|Wskazuje, czy wartość jednego obiektu ciągu jest mniejsza niż wartość drugiego obiektu ciągu.|

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** System Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Przestrzeń nazw:** Platformach

**Nagłówek** vccorlib. h (włączony domyślnie)

## <a name="stringbegin-method"></a><a name="begin"></a>String:: BEGIN — Metoda

Zwraca wskaźnik do początku bieżącego ciągu.

### <a name="syntax"></a>Składnia

```cpp
char16* Begin();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku bieżącego ciągu.

## <a name="stringcompareordinal-method"></a><a name="compareordinal"></a>String:: CompareOrdinal, Metoda

Metoda statyczna, która porównuje dwa `String` obiekty, oceniając wartości liczbowe odpowiednich znaków w dwóch wartościach ciągu reprezentowanych przez obiekty.

### <a name="syntax"></a>Składnia

```cpp
static int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy obiekt ciągu.

*str2*<br/>
Drugi obiekt ciągu.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która wskazuje leksykalną relację między dwoma comparands. Poniższa tabela zawiera listę możliwych zwracanych wartości.

|Wartość|Warunek|
|-----------|---------------|
|-1|`str1`jest mniejsze niż `str2` .|
|0|`str1`jest równa `str2` .|
|1|`str1`jest większa niż `str2` .|

## <a name="stringconcat-method"></a><a name="concat"></a>String:: concat — Metoda

Łączy wartości dwóch obiektów String.

### <a name="syntax"></a>Składnia

```cpp
String^ Concat( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy obiekt ciągu lub `null` .

*str2*<br/>
Drugi obiekt ciągu lub `null` .

### <a name="return-value"></a>Wartość zwracana

Nowy ciąg obiektu ciągu ^, którego wartością jest łączenie wartości `str1` i `str2` .

Jeśli `str1` jest `null` i `str2` nie jest, `str1` jest zwracana. Jeśli `str2` jest `null` i `str1` nie jest, `str2` jest zwracana. Jeśli `str1` i `str2` są oba `null` , zwracany jest pusty ciąg (L "").

## <a name="stringdata-method"></a><a name="data"></a>String::D ATA — Metoda

Zwraca wskaźnik do początku bufora danych obiektu jako tablicę w stylu C `char16` ( **`wchar_t`** ) elementów.

### <a name="syntax"></a>Składnia

```cpp
const char16* Data();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku `const char16` tablicy znaków Unicode ( `char16` jest elementem TypeDef dla **`wchar_t`** ).

### <a name="remarks"></a>Uwagi

Użyj tej metody do konwersji z `Platform::String^` na `wchar_t*` . Gdy `String` obiekt wykracza poza zakres, wskaźnik danych nie jest już prawidłowy. Aby przechowywać dane poza okresem istnienia oryginalnego `String` obiektu, użyj [wcscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) , aby skopiować tablicę do pamięci, która została przyalokowana samodzielnie.

## <a name="stringdispose-method"></a><a name="dispose"></a>String::D Metoda isułożenia

Zwalnia lub zwalnia zasoby.

### <a name="syntax"></a>Składnia

```cpp
virtual override void Dispose();
```

## <a name="stringend-method"></a><a name="end"></a>String:: end — Metoda

Zwraca wskaźnik poza końcem bieżącego ciągu.

### <a name="syntax"></a>Składnia

```cpp
char16* End();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ostatniego końca bieżącego ciągu.

### <a name="remarks"></a>Uwagi

End () zwraca wartość begin () + length.

## <a name="stringequals-method"></a><a name="equals"></a>String:: Equals — Metoda

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

**`true`** Jeśli `str` jest równe bieżącemu obiektowi; w przeciwnym razie, **`false`** .

### <a name="remarks"></a>Uwagi

Ta metoda jest równoważna z ciągiem statycznym [:: CompareOrdinal](#compareordinal). W pierwszym przeciążeniu oczekiwano, że `str` parametr może być rzutowany na obiekt ciągu ^.

## <a name="stringgethashcode-method"></a><a name="gethashcode"></a>String:: GetHashCode, Metoda

Zwraca wartość skrótu dla tego wystąpienia.

### <a name="syntax"></a>Składnia

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>Wartość zwracana

Kod skrótu dla tego wystąpienia.

## <a name="stringisempty-method"></a><a name="isempty"></a>String:: IsEmpty — Metoda

Wskazuje, czy bieżący obiekt ciągu jest pusty.

### <a name="syntax"></a>Składnia

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżący `String` obiekt ma **wartość null** lub jest pustym ciągiem (L ""); w przeciwnym razie **`false`** .

## <a name="stringisfastpass-method"></a><a name="isfastpass"></a>String:: IsFastPass, Metoda

Wskazuje, czy bieżący obiekt ciągu uczestniczy w operacji *szybkiego przekazywania* . W przypadku operacji szybkiego przebiegu zliczanie odwołań jest zawieszone.

### <a name="syntax"></a>Składnia

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżący `String` obiekt jest szybko przekroczenia; w przeciwnym razie, **`false`** .

### <a name="remarks"></a>Uwagi

W wywołaniu funkcji, w której obiekt zlicza odwołania jest parametrem, a wywoływana funkcja tylko odczytuje ten obiekt, kompilator może bezpiecznie wstrzymać zliczanie odwołań i zwiększyć wydajność wywoływania. Nic nie jest przydatne, ponieważ kod można wykonać przy użyciu tej właściwości. System obsługuje wszystkie szczegóły.

## <a name="stringlength-method"></a><a name="length"></a>String:: length — Metoda

Pobiera liczbę znaków w bieżącym `String` obiekcie.

### <a name="syntax"></a>Składnia

```cpp
unsigned int Length();
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaków w bieżącym `String` obiekcie.

### <a name="remarks"></a>Uwagi

Długość ciągu bez znaków wynosi zero. Długość następującego ciągu to 5:

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

Tablica znaków zwracana przez [ciąg::D ATA](#data) ma jeden dodatkowy znak, który jest kończącą się wartością null lub "\ 0". Ten znak jest również dwa bajty długie.

## <a name="stringoperator-operator"></a><a name="operator-plus"></a>String:: operator + — operator

Łączy dwa obiekty [String](../cppcx/platform-string-class.md) z nowym obiektem [ciągu](../cppcx/platform-string-class.md) .

### <a name="syntax"></a>Składnia

```cpp
bool String::operator+( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy `String` obiekt.

*str2*<br/>
Drugi `String` obiekt, którego zawartość zostanie dołączona do `str1` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli *str1* jest równa *str2*; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Ten operator tworzy `String^` obiekt, który zawiera dane z dwóch operandów. Należy jej używać w celu wygody, gdy ekstremalna wydajność nie jest krytyczna. Niektóre wywołania " `+` " w funkcji prawdopodobnie nie będą widoczne, ale jeśli manipulujesz dużymi obiektami lub danymi tekstowymi w ścisłej pętli, użyj standardowych mechanizmów i typów języka C++.

## <a name="stringoperator-operator"></a><a name="operator-equality"></a>String:: operator = = — operator

Wskazuje, czy dwa określone obiekty ciągu mają tę samą wartość tekstową.

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

**`true`** Jeśli zawartość `str1` jest równa `str2` ; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Ten operator jest odpowiednikiem [ciągu:: CompareOrdinal](#compareordinal).

## <a name="stringoperatorgt"></a><a name="operator-greater-than"></a>String:: operator&gt;

Wskazuje, czy wartość jednego `String` obiektu jest większa niż wartość drugiego `String` obiektu.

### <a name="syntax"></a>Składnia

```cpp
bool String::operator>( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy `String` obiekt.

*str2*<br/>
Drugi `String` obiekt.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wartość `str1` jest większa niż wartość `str2` ; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Ten operator jest odpowiednikiem jawnego wywołania [ciągu:: CompareOrdinal](#compareordinal) i uzyskania wyniku większego od zera.

## <a name="stringoperatorgt"></a><a name="operator-greater-than-or-equals"></a>String:: operator&gt;=

Wskazuje, czy wartość jednego `String` obiektu jest większa lub równa wartości drugiego `String` obiektu.

### <a name="syntax"></a>Składnia

```cpp
bool String::operator>=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy `String` obiekt.

*str2*<br/>
Drugi `String` obiekt.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wartość `str1` jest większa lub równa wartości `str2` ; w przeciwnym razie **`false`** .

## <a name="stringoperator"></a><a name="operator-inequality"></a>String:: operator! =

Wskazuje, czy dwa określone `String` obiekty mają różne wartości.

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

**`true`** Jeśli `str1` nie jest równe `str2` ; w przeciwnym razie **`false`** .

## <a name="stringoperatorlt"></a><a name="operator-less-than"></a>String:: operator&lt;

Wskazuje, czy wartość jednego `String` obiektu jest mniejsza niż wartość drugiego `String` obiektu.

### <a name="syntax"></a>Składnia

```cpp
bool String::operator<( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy `String` obiekt.

*str2*<br/>
Drugi `String` obiekt.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wartość *str1* jest mniejsza niż wartość *str2*; w przeciwnym razie **`false`** .

## <a name="stringstring-constructor"></a><a name="ctor"></a>String:: String — Konstruktor

Inicjuje nowe wystąpienie `String` klasy z kopią danych ciągu wejściowego.

### <a name="syntax"></a>Składnia

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>Parametry

*wolumin*<br/>
Seria znaków dwubajtowych, które inicjują ciąg. char16

*Azotan*<br/>
Liczba, która określa długość ciągu.

### <a name="remarks"></a>Uwagi

Jeśli wydajność jest krytyczna i kontrolujesz okres istnienia ciągu źródłowego, możesz użyć klasy [platform:: StringReference](../cppcx/platform-stringreference-class.md) zamiast ciągu.

### <a name="example"></a>Przykład

```cpp
String^ s = L"Hello!";
```

## <a name="stringtostring"></a><a name="tostring"></a>String:: ToString

Zwraca `String` obiekt, którego wartość jest taka sama jak bieżący ciąg.

### <a name="syntax"></a>Składnia

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>Wartość zwracana

`String`Obiekt, którego wartość jest taka sama jak bieżący ciąg.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
