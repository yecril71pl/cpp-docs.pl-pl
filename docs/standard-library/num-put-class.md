---
title: num_put — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_put
- locale/std::num_put::char_type
- locale/std::num_put::iter_type
- locale/std::num_put::do_put
- locale/std::num_put::put
helpviewer_keywords:
- std::num_put [C++]
- std::num_put [C++], char_type
- std::num_put [C++], iter_type
- std::num_put [C++], do_put
- std::num_put [C++], put
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
ms.openlocfilehash: 32bfc29b7bc645dd37ae4aaaf498823c0d139dfc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224711"
---
# <a name="num_put-class"></a>num_put — Klasa

Szablon klasy, który opisuje obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontrolowania konwersji wartości numerycznych na sekwencje typu `CharType` .

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

*OutputIterator*\
Typ iteratora, do którego funkcje numeryczne put zapisują swoje dane wyjściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[num_put](#num_put)|Konstruktor dla obiektów typu `num_put` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wyjściowych.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[do_put](#do_put)|Funkcja wirtualna, która jest wywoływana w celu przekonwertowania liczby na sekwencję `CharType` s, która reprezentuje liczbę sformatowaną dla danego ustawienia regionalnego.|
|[Ubrani](#put)|Konwertuje liczbę na sekwencję `CharType` s, która reprezentuje liczbę sformatowaną dla danego ustawienia regionalnego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<locale>

**Przestrzeń nazw:** std

## <a name="num_putchar_type"></a><a name="char_type"></a>num_put:: char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `CharType` .

## <a name="num_putdo_put"></a><a name="do_put"></a>num_put::d o_put

Funkcja wirtualna, która jest wywoływana w celu przekonwertowania liczby na sekwencję `CharType` s, która reprezentuje liczbę sformatowaną dla danego ustawienia regionalnego.

```cpp
virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const long long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const unsigned long long val) const;
```

### <a name="parameters"></a>Parametry

*ponown*\
Iterator odnoszący się do pierwszego elementu wstawionego ciągu.

*_Iosbase*\
Określono strumień zawierający ustawienia regionalne z zestawem reguł numpunct używany do punctuate danych wyjściowych i flag do formatowania danych wyjściowych.

*_Fill*\
Znak, który jest używany na potrzeby odstępów.

*użyte*\
Liczba lub typ wartości logicznej, która ma być wyjściowa.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnosi się do położenia jednej poza ostatnim produkowanym elementem.

### <a name="remarks"></a>Uwagi

Funkcja pierwszej wirtualnej chronionej składowej generuje elementy sekwencyjne zaczynające się *obok* pola danych wyjściowych Integer z wartości *Val*. Funkcja zwraca iterator wyznaczający następne miejsce do wstawienia elementu poza wygenerowane pole danych wyjściowych.

Pole danych wyjściowych w postaci liczby całkowitej jest generowane przez te same reguły, które są używane przez funkcje drukowania do generowania serii **`char`** elementów do pliku. Każdy taki znak jest założono, że jest mapowany na odpowiednik elementu typu `CharType` przez proste, jedno-do-jednego mapowania. Gdy funkcja drukowania jest konsolą pola z spacjami lub cyfrą 0, `do_put` zamiast tego używa `fill` . Równoważna specyfikacja konwersji druku jest określana w następujący sposób:

- Jeśli **iosbase**. [flags](../standard-library/ios-base-class.md#flags)  &  `ios_base::basefield` flagi  ==  `ios_base::` [KTZ](../standard-library/ios-functions.md#oct), specyfikacja konwersji to `lo` .

- Jeśli **iosbase. flags**  &  **ios_base:: basefield**  ==  `ios_base::` [HEX](../standard-library/ios-functions.md#hex), specyfikacja konwersji to `lx` .

- W przeciwnym razie specyfikacja konwersji to `ld` .

Jeśli **iosbase**. [Szerokość](../standard-library/ios-base-class.md#width) jest różna od zera, a szerokość pola tej wartości jest dołączona. Funkcja następnie wywołuje **iosbase**. **Szerokość**(0), aby zresetować szerokość pola do zera.

Uzupełnienie występuje tylko wtedy, gdy minimalna liczba elementów ( *N* ) wymagana do określenia pola danych wyjściowych jest mniejsza niż **iosbase**. [Szerokość](../standard-library/ios-base-class.md#width). Takie uzupełnienie składa się z sekwencji o długości " *N*"  -  **width** kopii **wypełnienia**. Uzupełnienie jest wykonywane w następujący sposób:

- Jeśli **iosbase**. **flags**  &  `ios_base::adjustfield` flagi  ==  `ios_base::` [po lewej stronie](../standard-library/ios-functions.md#left)flaga **-** jest poprzedzona. (Uzupełnienie występuje po wygenerowaniu tekstu).

- Jeśli **iosbase. flags**  &  **ios_base:: adjustfield**  ==  `ios_base::` [Internal](../standard-library/ios-functions.md#internal), flaga **0** jest poprzedzona. (W przypadku pola danych wyjściowych liczbowych dopełnienie ma miejsce w przypadku, gdy konsola funkcji drukowania ma wartość 0).

- W przeciwnym razie żadna dodatkowa flaga nie jest połączona. (Dopełnienie występuje przed wygenerowaną sekwencją).

Ostateczny

- Jeśli **iosbase**. **flags**  &  flagi `ios_base::` [showpos](../standard-library/ios-functions.md#showpos) jest różna od zera, flaga **+** jest poprzedzona specyfikacją konwersji.

- Jeśli **iosbase**. **flagi**  &  **ios_base::**[showbase](../standard-library/ios-functions.md#showbase) jest różna od zera, flaga **#** jest poprzedzona specyfikacją konwersji.

Format pola danych wyjściowych w postaci liczby całkowitej jest bardziej określony przez zestaw [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class)**FAC** zwrócony przez wywołanie [use_facet](../standard-library/locale-functions.md#use_facet)  <  [numpunct](../standard-library/numpunct-class.md) \< **Elem**> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). W szczególności:

- **FAC**. [grupowanie](../standard-library/numpunct-class.md#grouping) określa sposób grupowania cyfr na lewo od dowolnego punktu dziesiętnego

- **FAC**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) Określa sekwencję oddziela grupy cyfr po lewej stronie dowolnego punktu dziesiętnego

Jeśli żadne ograniczenia grupowania nie są nakładane przez **FAC**. **grupowanie** (jego pierwszy element ma wartość CHAR_MAX), a następnie brak wystąpień elementu **FAC**. `thousands_sep`są generowane w polu danych wyjściowych. W przeciwnym razie separatory są wstawiane po konwersji wydruku.

Druga wirtualna chroniona funkcja członkowska:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że zastępuje specyfikację konwersji `ld` z `lu` .

Trzecia wirtualna chroniona funkcja członkowska:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że generuje pole danych wyjściowych zmiennoprzecinkowych z wartości **Val**. **FAC**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) Określa sekwencję oddzielające cyfry całkowite od cyfr ułamkowych. Równoważna specyfikacja konwersji druku jest określana w następujący sposób:

- Jeśli **iosbase**. **flags**  &  `ios_base::floatfield` flagi  ==  `ios_base::` [Naprawiono](../standard-library/ios-functions.md#fixed)specyfikację konwersji `lf` .

- Jeśli **iosbase**. **flagi**  &  **ios_base:: floatfield**  ==  `ios_base::` w [przypadku specyfikacji](../standard-library/ios-functions.md#scientific)konwersji jest to `le` . Jeśli **iosbase**. **flags**  &  flagi `ios_base::` [wielkie litery](../standard-library/ios-functions.md#uppercase) są różne `e` od zera `E` .

- W przeciwnym razie specyfikacja konwersji to **LG**. Jeśli **iosbase**. **flagi**  &  **ios_base:: wielkie litery** jest różna `g` od zera `G` .

Jeśli **iosbase**. **flagi**  &  **ios_base:: fixed** jest różna od zera lub jeśli **iosbase**. [precyzja](../standard-library/ios-base-class.md#precision) jest większa od zera, dokładność z wartością **iosbase**. **precyzja** jest poprzedzona specyfikacją konwersji. Każde uzupełnienie zachowuje się tak samo jak w przypadku pola danych wyjściowych w postaci liczby całkowitej. Znak uzupełniania jest **wypełniany**. Ostateczny

- Jeśli **iosbase**. **flags**  &  flagi `ios_base::` [showpos](../standard-library/ios-functions.md#showpos) jest różna od zera, flaga **+** jest poprzedzona specyfikacją konwersji.

- Jeśli **iosbase**. **flags**  &  flagi `ios_base::` [Showpoint](../standard-library/ios-functions.md#showpoint) jest różna od zera, flaga **#** jest poprzedzona specyfikacją konwersji.

Czwarta chroniona funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

zachowuje się tak samo, z tą różnicą, że kwalifikator `l` w specyfikacji konwersji jest zastępowany przez `L` .

Piąta chroniona funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

zachowuje się tak samo, z tą różnicą, że specyfikacja konwersji to `p` **,** i kwalifikator, który jest wymagany do określenia uzupełnienia.

Szósta chroniona funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że generuje pole danych wyjściowych Boolean z wartości *Val*.

Pole dane wyjściowe wartości logicznej przyjmuje jedną z dwóch form. Jeśli `iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) jest **`false`** , funkcja członkowska zwraca `do_put(_Next, _Iosbase, _Fill, (long)val)` , która zwykle generuje wygenerowaną sekwencję 0 (dla **`false`** ) lub 1 (dla **`true`** ). W przeciwnym razie wygenerowana sekwencja to *FAC*. [falsename](../standard-library/numpunct-class.md#falsename) (for **`false`** ) lub *FAC*.[ TrueName](../standard-library/numpunct-class.md#truename) (for **`true`** ).

Siódma wirtualna chroniona funkcja członkowska:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że zastępuje specyfikację konwersji `ld` z `lld` .

Ósma wirtualna chroniona funkcja członkowska:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że zastępuje specyfikację konwersji `ld` z `llu` .

### <a name="example"></a>Przykład

Zobacz przykład [umieszczania](#put)wywołań `do_put` .

## <a name="num_putiter_type"></a><a name="iter_type"></a>num_put:: iter_type

Typ, który opisuje iterator danych wyjściowych.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu **OutputIterator.**

## <a name="num_putnum_put"></a><a name="num_put"></a>num_put:: num_put

Konstruktor dla obiektów typu `num_put` .

```cpp
explicit num_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Wartość całkowita służąca do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie są następujące:

- 0: okres istnienia obiektu jest zarządzany przez elementy lokalne, które go zawierają.

- 1: okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój obiekt podstawowy przy użyciu **ustawień regionalnych::**[facet](../standard-library/locale-class.md#facet_class)(_ *ReFS*).

## <a name="num_putput"></a><a name="put"></a>num_put::p UT

Konwertuje liczbę na sekwencję `CharType` s, która reprezentuje liczbę sformatowaną dla danego ustawienia regionalnego.

```cpp
iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Unsigned long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;
```

### <a name="parameters"></a>Parametry

*dest*\
Iterator odnoszący się do pierwszego elementu wstawionego ciągu.

*_Iosbase*\
Określono strumień zawierający ustawienia regionalne z aspektem numpunct używanym do punctuate danych wyjściowych i flag do formatowania danych wyjściowych.

*_Fill*\
Znak, który jest używany na potrzeby odstępów.

*użyte*\
Liczba lub typ wartości logicznej, która ma być wyjściowa.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych odnosi się do położenia jednej poza ostatnim produkowanym elementem.

### <a name="remarks"></a>Uwagi

Wszystkie funkcje składowe zwracają [do_put](#do_put)( `next` ,,, `_Iosbase` `_Fill` `val` ).

### <a name="example"></a>Przykład

```cpp
// num_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );
   basic_stringstream<char> psz2;
   ios_base::iostate st = 0;
   long double fVal;
   cout << "The thousands separator is: "
        << use_facet < numpunct <char> >(loc).thousands_sep( )
        << endl;

   psz2.imbue( loc );
   use_facet < num_put < char > >
      ( loc ).put(basic_ostream<char>::_Iter(psz2.rdbuf( ) ),
                    psz2, ' ', fVal=1000.67);

   if ( st & ios_base::failbit )
      cout << "num_put( ) FAILED" << endl;
   else
      cout << "num_put( ) = " << psz2.rdbuf( )->str( ) << endl;
}
```

```Output
The thousands separator is: .
num_put( ) = 1.000,67
```

## <a name="see-also"></a>Zobacz także

[\<locale>](../standard-library/locale.md)\
[facet — Klasa](../standard-library/locale-class.md#facet_class)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
