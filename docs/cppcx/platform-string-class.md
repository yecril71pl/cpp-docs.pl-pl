---
title: Platforma::Klasa ciągu
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
ms.openlocfilehash: 3f29c60d0d6a4618d97d8f750a048fcc18f976b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322114"
---
# <a name="platformstring-class"></a>Platforma::Klasa ciągu

Reprezentuje sekwencyjną kolekcję znaków Unicode, która jest używana do reprezentowania tekstu. Aby uzyskać więcej informacji i przykładów, zobacz [Ciągi ciągów](../cppcx/strings-c-cx.md).

## <a name="syntax"></a>Składnia

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>Iteratory

Dwie funkcje iteratora, które nie są członkami String `std::for_each` klasy, mogą być używane z funkcją szablonu do wyliczenia znaków w String obiektu.

|Członek|Opis|
|------------|-----------------|
|`const char16* begin(String^ s)`|Zwraca wskaźnik na początku określonego obiektu String.|
|`const char16* end(String^ s)`|Zwraca wskaźnik poza koniec określonego obiektu String.|

## <a name="members"></a>Elementy członkowskie

String Klasy dziedziczy z Object i IDisposable, IEquatable i IPrintable interfejsów.

String Klasa ma również następujące typy elementów członkowskich.

### <a name="constructors"></a>Konstruktorów

|Członek|Opis|
|------------|-----------------|
|[Ciąg::Ciąg](#ctor)|Inicjuje nowe wystąpienie String klasy.|

### <a name="methods"></a>Metody

Klasa String dziedziczy metody Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() i ToString() z [platformy::Object Class](../cppcx/platform-object-class.md). Ciąg ma również następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[Ciąg::Początek](#begin)|Zwraca wskaźnik na początku bieżącego ciągu.|
|[Ciąg::CompareOrdinal](#compareordinal)|Porównuje dwa `String` obiekty, oceniając wartości liczbowe odpowiednich znaków w dwóch wartościach ciągu reprezentowanych przez obiekty.|
|[Ciąg::Concat](#concat)|Łączy wartości dwóch String obiektów.|
|[Ciąg::Data](#data)|Zwraca wskaźnik na początku bieżącego ciągu.|
|[Ciąg::Dzdejspoń.](#dispose)|Uwalnia lub zwalnia zasoby.|
|[Ciąg::Koniec](#end)|Zwraca wskaźnik poza koniec bieżącego ciągu.|
|[Ciąg:::Równa się](#equals)|Wskazuje, czy określony obiekt jest równy bieżącemu obiektowi.|
|[Ciąg::GetHashCode](#gethashcode)|Zwraca wartość skrótu dla tego wystąpienia.|
|[Ciąg::IsEmpty](#isempty)|Wskazuje, czy bieżący obiekt String jest pusty.|
|[Ciąg::IsFastPass](#isfastpass)|Wskazuje, czy bieżący String obiekt uczestniczy w operacji *szybkiego przebiegu.* W trybie szybkiego przejścia zliczanie odwołań jest zawieszone.|
|[Ciąg::Długość](#length)|Pobiera długość bieżącego String obiektu.|
|[Ciąg::ToString](#tostring)|Zwraca String obiektu, którego wartość jest taka sama jak bieżącego ciągu.|

### <a name="operators"></a>Operatory

String Klasa ma następujące operatory.

|Członek|Opis|
|------------|-----------------|
|[Ciąg::operator== Operator](#operator-equality)|Wskazuje, czy dwa określone String obiekty mają taką samą wartość.|
|[operator+ Operator](#operator-plus)|Łączy dwa String obiektów do nowego String obiektu.|
|[Ciąg::operator> operator](#operator-greater-than)|Wskazuje, czy wartość jednego obiektu String jest większa niż wartość drugiego obiektu String.|
|[Ciąg::operator>= Operator](#operator-greater-than-or-equals)|Wskazuje, czy wartość jednego obiektu String jest większa lub równa wartości drugiego obiektu String.|
|[Ciąg::operator!= Operator](#operator-inequality)|Wskazuje, czy dwa określone String obiekty mają różne wartości.|
|[Ciąg::operator< operator](#operator-less-than)|Wskazuje, czy wartość jednego obiektu String jest mniejsza niż wartość drugiego obiektu String.|

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Obszar nazw:** Platformy

**Nagłówek** vccorlib.h (domyślnie dołączony)

## <a name="stringbegin-method"></a><a name="begin"></a>Ciąg:::Metoda begin

Zwraca wskaźnik na początku bieżącego ciągu.

### <a name="syntax"></a>Składnia

```cpp
char16* Begin();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku bieżącego ciągu.

## <a name="stringcompareordinal-method"></a><a name="compareordinal"></a>Ciąg::CompareOrinal Metoda

Metoda statyczna, która `String` porównuje dwa obiekty, oceniając wartości liczbowe odpowiednich znaków w dwóch wartościach ciągu reprezentowanych przez obiekty.

### <a name="syntax"></a>Składnia

```cpp
static int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy String obiektu.

*str2*<br/>
Drugi String obiektu.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita wskazująca leksykalne relacje między dwoma comparands. W poniższej tabeli wymieniono możliwe wartości zwracane.

|Wartość|Warunek|
|-----------|---------------|
|-1|`str1`jest mniejsza `str2`niż .|
|0|`str1`jest równa `str2`.|
|1|`str1`jest większa `str2`niż .|

## <a name="stringconcat-method"></a><a name="concat"></a>Ciąg:::Metoda concat

Łączy wartości dwóch String obiektów.

### <a name="syntax"></a>Składnia

```cpp
String^ Concat( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy obiekt String `null`lub .

*str2*<br/>
Drugi obiekt String `null`lub .

### <a name="return-value"></a>Wartość zwracana

Nowy obiekt String^, którego wartością jest łączenie `str1` `str2`wartości i .

Jeśli `str1` `null` jest, `str2` a `str1` nie, jest zwracany. Jeśli `str2` `null` jest, `str1` a `str2` nie, jest zwracany. Jeśli `str1` `str2` i `null`są oba , zwracany jest pusty ciąg (L").

## <a name="stringdata-method"></a><a name="data"></a>Ciąg:metoda :Data

Zwraca wskaźnik na początku buforu danych obiektu jako tablicę `char16` w`wchar_t`stylu C ( ) elementów.

### <a name="syntax"></a>Składnia

```cpp
const char16* Data();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku `const char16` tablicy znaków Unicode`char16` ( jest `wchar_t`typedef for ).

### <a name="remarks"></a>Uwagi

Ta metoda służy `Platform::String^` do `wchar_t*`konwersji z do . Gdy `String` obiekt wykracza poza zakres, wskaźnik danych nie jest już gwarantowana jako prawidłowa. Aby przechowywać dane poza okresem istnienia oryginalnego `String` obiektu, należy użyć [wcscpy_s,](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) aby skopiować tablicę do pamięci, która została przydzielona samodzielnie.

## <a name="stringdispose-method"></a><a name="dispose"></a>Ciąg:metoda :Dzgodna

Uwalnia lub zwalnia zasoby.

### <a name="syntax"></a>Składnia

```cpp
virtual override void Dispose();
```

## <a name="stringend-method"></a><a name="end"></a>Ciąg::Metoda końcowa

Zwraca wskaźnik poza koniec bieżącego ciągu.

### <a name="syntax"></a>Składnia

```cpp
char16* End();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przeszłości koniec bieżącego ciągu.

### <a name="remarks"></a>Uwagi

End() zwraca wartość Begin() + Length.

## <a name="stringequals-method"></a><a name="equals"></a>Ciąg::Metoda równa się

Wskazuje, czy określony ciąg ma taką samą wartość jak bieżący obiekt.

### <a name="syntax"></a>Składnia

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli `str` jest równa bieżącemu obiektowi; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta metoda jest równoważna ciągowi [statycznemu::CompareOrdinal](#compareordinal). W pierwszym przeciążeniu oczekuje `str` się, że parametr może być rzutowy na String^ obiektu.

## <a name="stringgethashcode-method"></a><a name="gethashcode"></a>Ciąg::Metoda GetHashCode

Zwraca wartość skrótu dla tego wystąpienia.

### <a name="syntax"></a>Składnia

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>Wartość zwracana

Kod skrótu dla tego wystąpienia.

## <a name="stringisempty-method"></a><a name="isempty"></a>Ciąg::Metoda IsEmpty

Wskazuje, czy bieżący obiekt String jest pusty.

### <a name="syntax"></a>Składnia

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli `String` bieżący obiekt ma **wartość null** lub pusty ciąg (L""); w przeciwnym razie **false**.

## <a name="stringisfastpass-method"></a><a name="isfastpass"></a>Ciąg::Metoda IsFastPass

Wskazuje, czy bieżący String obiekt uczestniczy w operacji *szybkiego przebiegu.* W trybie szybkiego przejścia zliczanie odwołań jest zawieszone.

### <a name="syntax"></a>Składnia

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli `String` bieżący obiekt jest szybko przeszłości; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

W wywołaniu funkcji, w której obiekt zliczany odwołaniem jest parametrem, a wywoływana funkcja odczytuje tylko ten obiekt, kompilator może bezpiecznie zawiesić zliczanie odwołań i poprawić wydajność wywoływania. Nie ma nic przydatne, że kod może zrobić z tej właściwości. System obsługuje wszystkie szczegóły.

## <a name="stringlength-method"></a><a name="length"></a>Ciąg::Metoda długości

Pobiera liczbę znaków w bieżącym `String` obiekcie.

### <a name="syntax"></a>Składnia

```cpp
unsigned int Length();
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaków w bieżącym `String` obiekcie.

### <a name="remarks"></a>Uwagi

Długość String bez znaków wynosi zero. Długość następującego ciągu wynosi 5:

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

Tablica znaków zwrócona przez [String::Data](#data) ma jeden dodatkowy znak, który jest kończącą się wartością NULL lub '\0'. Ten znak ma również dwa bajty długości.

## <a name="stringoperator-operator"></a><a name="operator-plus"></a>Ciąg::operator+ Operator

Łączy dwa [String](../cppcx/platform-string-class.md) obiektów do nowego [String](../cppcx/platform-string-class.md) obiektu.

### <a name="syntax"></a>Składnia

```cpp
bool String::operator+( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
Pierwszy `String` obiekt.

*str2*<br/>
Drugi `String` obiekt, którego zawartość zostanie dołączona do `str1`.

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli *str1* jest równa *str2*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ten operator `String^` tworzy obiekt, który zawiera dane z dwóch operands. Użyj go dla wygody, gdy ekstremalna wydajność nie jest krytyczna. Kilka wywołań`+`do " " w funkcji prawdopodobnie nie będzie zauważalne, ale jeśli manipulujesz dużymi obiektami lub danymi tekstowymi w ciasnej pętli, użyj standardowych mechanizmów i typów języka C++.

## <a name="stringoperator-operator"></a><a name="operator-equality"></a>Ciąg::operator== Operator

Wskazuje, czy dwa określone String obiekty mają taką samą wartość tekstową.

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

**true,** jeżeli `str1` zawartość są `str2`równe ; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ten operator jest odpowiednikiem [String::CompareOrdinal](#compareordinal).

## <a name="stringoperatorgt"></a><a name="operator-greater-than"></a>Ciąg::operator&gt;

Wskazuje, czy wartość `String` jednego obiektu jest większa niż `String` wartość drugiego obiektu.

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

**true,** jeśli `str1` wartość jest większa `str2`niż wartość ; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ten operator jest odpowiednikiem jawnie wywołanie [String::CompareOrdinal](#compareordinal) i uzyskanie wyniku większego niż zero.

## <a name="stringoperatorgt"></a><a name="operator-greater-than-or-equals"></a>Ciąg::operator&gt;=

Wskazuje, czy wartość `String` jednego obiektu jest większa lub równa `String` wartości drugiego obiektu.

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

**true,** jeżeli `str1` wartość jest większa lub równa `str2`wartości; w przeciwnym razie **false**.

## <a name="stringoperator"></a><a name="operator-inequality"></a>Ciąg::operator!=

Wskazuje, czy `String` dwa określone obiekty mają różne wartości.

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

**prawda,** jeśli `str1` nie `str2`jest równa ; w przeciwnym razie **false**.

## <a name="stringoperatorlt"></a><a name="operator-less-than"></a>Ciąg::operator&lt;

Wskazuje, czy wartość `String` jednego obiektu jest mniejsza niż `String` wartość drugiego obiektu.

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

**true,** jeśli wartość *str1* jest mniejsza niż wartość *str2;* w przeciwnym razie **false**.

## <a name="stringstring-constructor"></a><a name="ctor"></a>Ciąg::Konstruktor ciągów

Inicjuje nowe wystąpienie `String` klasy z kopią danych ciągu wejściowego.

### <a name="syntax"></a>Składnia

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>Parametry

*S*<br/>
Seria szerokich znaków, które inicjują ciąg. char16

*N*<br/>
Liczba określająca długość ciągu.

### <a name="remarks"></a>Uwagi

Jeśli wydajność jest krytyczna i można kontrolować okres istnienia ciągu źródłowego, można użyć [Platform::StringReference](../cppcx/platform-stringreference-class.md) w miejsce String.

### <a name="example"></a>Przykład

```cpp
String^ s = L"Hello!";
```

## <a name="stringtostring"></a><a name="tostring"></a>Ciąg::ToString

Zwraca `String` obiekt, którego wartość jest taka sama jak bieżący ciąg.

### <a name="syntax"></a>Składnia

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt, `String` którego wartość jest taka sama jak bieżący ciąg.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
