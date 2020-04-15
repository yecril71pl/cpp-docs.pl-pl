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
ms.openlocfilehash: 3f65d7140bb5c691fa58ec9d74ceda5573280ddb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373646"
---
# <a name="num_put-class"></a>num_put — Klasa

Szablon klasy opisujący obiekt, który może służyć jako aspekt ustawień regionalnych do kontrolowania `CharType`konwersji wartości liczbowych do sekwencji typu .

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

*Dane wyjścioweIterator*\
Typ iteratora, do którego funkcje numeryczne put zapisują swoje dane wyjściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[num_put](#num_put)|Konstruktor obiektów typu `num_put`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wyjściowych.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[do_put](#do_put)|Funkcja wirtualna, która jest wywoływana do `CharType`konwersji liczby na sekwencję s, która reprezentuje liczbę sformatowaną dla danego ustawienia regionalne.|
|[Umieścić](#put)|Konwertuje liczbę na `CharType`sekwencję s, która reprezentuje liczbę sformatowaną dla danego ustawienia regionalne.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="num_putchar_type"></a><a name="char_type"></a>num_put::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `CharType`szablonu .

## <a name="num_putdo_put"></a><a name="do_put"></a>num_put::do_put

Funkcja wirtualna, która jest wywoływana do `CharType`konwersji liczby na sekwencję s, która reprezentuje liczbę sformatowaną dla danego ustawienia regionalne.

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

*Następnego*\
Iterator adresowania pierwszy element wstawionego ciągu.

*_Iosbase*\
Określono strumień, który zawiera ustawienia regionalne z aspektem numpunct używanym do przerywania danych wyjściowych i flag do formatowania danych wyjściowych.

*_Fill*\
Znak, który jest używany do odstępów.

*Val*\
Liczba lub typ logiczny, który ma być wyjściowy.

### <a name="return-value"></a>Wartość zwracana

Iterator wyjściowy adresuje pozycję jedną poza ostatnim produkowanym elementem.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja wirtualnego chronionego elementu członkowskiego generuje kolejne elementy rozpoczynające się *obok,* aby utworzyć pole wyjściowe całkowite od wartości *val*. Funkcja zwraca iterator wyznaczający następne miejsce, aby wstawić element poza wygenerowanym polem wyjściowym liczby całkowitej.

Pole wyjściowe liczby całkowitej jest generowane przez te same reguły używane przez funkcje drukowania do generowania serii elementów **char** do pliku. Każdy taki char element zakłada się mapować `CharType` do równoważnego elementu typu przez proste, jeden do jednego mapowania. W przypadku, gdy funkcja drukowania wypełnia pole z spacjami lub cyfrą 0, `do_put` zamiast tego używa `fill`. Równoważną specyfikację konwersji wydruku określa się w następujący sposób:

- Jeśli **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & flagi ==  `lo`października, specyfikacja konwersji jest .[oct](../standard-library/ios-functions.md#oct)`ios_base::basefield``ios_base::`

- Jeśli **plik iosbase.flags** & **ios_base::basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex), `lx`specyfikacja konwersji jest .

- W przeciwnym razie `ld`specyfikacja konwersji to .

Jeśli **iosbase**. [szerokość](../standard-library/ios-base-class.md#width) jest niezerowa, szerokość pola tej wartości jest zalecana. Następnie funkcja wywołuje **iosbase**. **szerokości**(0), aby zresetować szerokość pola do zera.

Dopełnienie występuje tylko wtedy, gdy minimalna liczba elementów *N* wymagane do określenia pola wyjściowego jest mniejsza niż **iosbase**. [szerokości](../standard-library/ios-base-class.md#width). Taka dopełnienie składa się *z* - sekwencji N**szerokości** kopii **wypełnienia**. Dopełnienie następnie występuje w następujący sposób:

- Jeśli **iosbase**. **flags** & flagi ==  **-** w lewo , flaga jest poprzedzony.[left](../standard-library/ios-functions.md#left)`ios_base::adjustfield``ios_base::` (Dopełnienie występuje po wygenerowanym tekście).

- Jeśli **plik iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[internal](../standard-library/ios-functions.md#internal), flaga **0** jest dołączana. (W przypadku pola danych wyjściowych liczbowych dopełnienie występuje tam, gdzie klawiatura funkcji drukowania z 0.)

- W przeciwnym razie nie ma dodatkowej flagi jest poprzedzony. (Dopełnienie występuje przed wygenerowaną sekwencją.)

Wreszcie:

- Jeśli **iosbase**. **flags** & flagi`ios_base::`[showpos](../standard-library/ios-functions.md#showpos) jest nonzero, flaga **+** jest poprzedzony do specyfikacji konwersji.

- Jeśli **iosbase**. **flagi** & **ios_base::**[showbase](../standard-library/ios-functions.md#showbase) jest niezerowy, **#** flaga jest poprzedzony do specyfikacji konwersji.

Format pola wyjściowego liczby całkowitej jest dalej określany przez ustawienia regionalne**fac** aspekt zwracany przez [wywołanie](../standard-library/locale-class.md#facet_class) [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md) \< **Elem**>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). Są to:

- **fac**. [grupowanie](../standard-library/numpunct-class.md#grouping) określa sposób grupowania cyfr po lewej stronie dowolnego przecinka dziesiętnego

- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) określa sekwencję oddzielaą grupy cyfr po lewej stronie dowolnego przecinka dziesiętnego

Jeśli **fac**nie narzuca żadnych ograniczeń grupowania. **grouping** (jego pierwszy element ma wartość CHAR_MAX), a następnie nie ma wystąpień **fac**. `thousands_sep`są generowane w polu wyjściowym. W przeciwnym razie separatory są wstawiane po konwersji wydruku.

Druga funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

zachowuje się tak samo jak pierwszy, z tą `ld` różnicą, że zastępuje specyfikację konwersji za pomocą `lu`pliku .

Trzecia funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że wytwarza zmiennoprzecinkowe pole wyjściowe od wartości **val**. **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) określa sekwencję oddzielaną cyfry całkowite od cyfr ułamkowych. Równoważną specyfikację konwersji wydruku określa się w następujący sposób:

- Jeśli **iosbase**. **flags** & flagi ==  `lf`stałe , specyfikacja konwersji jest .[fixed](../standard-library/ios-functions.md#fixed)`ios_base::floatfield``ios_base::`

- Jeśli **iosbase**. **flagi** & **ios_base::floatfield** == `ios_base::`[naukowych](../standard-library/ios-functions.md#scientific), specyfikacja `le`konwersji jest . Jeśli **iosbase**. **flags** & flagi`ios_base::`[wielkie litery](../standard-library/ios-functions.md#uppercase) jest `e` nonzero, jest zastępowany `E`.

- W przeciwnym razie specyfikacja konwersji jest **lg**. Jeśli **iosbase**. **flagi** & **ios_base::wielkie litery** niezerowe, `g` zastępowane `G`.

Jeśli **iosbase**. **flagi** & **ios_base::fixed** jest niezerowy lub jeśli **iosbase**. [precyzja](../standard-library/ios-base-class.md#precision) jest większa niż zero, dokładność z wartością **iosbase**. **precyzja** jest dołączona do specyfikacji konwersji. Dopełnienie zachowuje się tak samo jak w przypadku pola wyjściowego liczby całkowitej. Znak dopełnienia jest **wypełnienie**. Wreszcie:

- Jeśli **iosbase**. **flags** & flagi`ios_base::`[showpos](../standard-library/ios-functions.md#showpos) jest nonzero, flaga **+** jest poprzedzony do specyfikacji konwersji.

- Jeśli **iosbase**. **flags** & flagi`ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint) jest niezerowy, flaga **#** jest poprzedzony do specyfikacji konwersji.

Czwarta funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

zachowuje się tak samo trzeci, `l` z tą różnicą, `L`że kwalifikator w specyfikacji konwersji jest zastępowany .

Piąta funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

zachowuje się tak samo pierwszy, z `p`tą różnicą, że specyfikacja konwersji jest **,** plus wszelkie kwalifikator potrzebne do określenia dopełnienia.

Szósta funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że generuje pole wyjściowe logiczne z *val*.

Pole wyjściowe logiczne przyjmuje jedną z dwóch form. Jeśli `iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) jest **false**, `do_put(_Next, _Iosbase, _Fill, (long)val)`funkcja elementu członkowskiego zwraca , który zazwyczaj tworzy wygenerowaną sekwencję 0 (dla **false)** lub 1 (dla **true).** W przeciwnym razie wygenerowana sekwencja to *fac*. [falsename](../standard-library/numpunct-class.md#falsename) (dla **false)** lub *fac*. [truename](../standard-library/numpunct-class.md#truename) (dla **true**).

Siódma funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

zachowuje się tak samo jak pierwszy, z tą `ld` różnicą, że zastępuje specyfikację konwersji za pomocą `lld`pliku .

Ósma funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

zachowuje się tak samo jak pierwszy, z tą `ld` różnicą, że zastępuje specyfikację konwersji za pomocą `llu`pliku .

### <a name="example"></a>Przykład

Zobacz przykład [put](#put), `do_put`który wywołuje .

## <a name="num_putiter_type"></a><a name="iter_type"></a>num_put::iter_type

Typ, który opisuje iterator danych wyjściowych.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **OutputIterator.**

## <a name="num_putnum_put"></a><a name="num_put"></a>num_put::num_put

Konstruktor obiektów typu `num_put`.

```cpp
explicit num_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_refs*\
Wartość całkowita używana do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie to:

- 0: Okres istnienia obiektu jest zarządzany przez ustawienia regionalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: Te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój obiekt bazowy za pomocą **ustawień regionalnych::**[aspekt](../standard-library/locale-class.md#facet_class)(_ *refs*).

## <a name="num_putput"></a><a name="put"></a>num_put::put

Konwertuje liczbę na `CharType`sekwencję s, która reprezentuje liczbę sformatowaną dla danego ustawienia regionalne.

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

*Dest*\
Iterator adresowania pierwszy element wstawionego ciągu.

*_Iosbase*\
Określono strumień, który zawiera ustawienia regionalne z aspektem numpunct używanym do przerywania danych wyjściowych i flag do formatowania danych wyjściowych.

*_Fill*\
Znak, który jest używany do odstępów.

*Val*\
Liczba lub typ logiczny, który ma być wyjściowy.

### <a name="return-value"></a>Wartość zwracana

Iterator wyjściowy adresuje pozycję jedną poza ostatnim produkowanym elementem.

### <a name="remarks"></a>Uwagi

Wszystkie funkcje [do_put](#do_put)członkowskie zwracają `next` `_Iosbase`do_put `_Fill` `val`( , , , ).

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

## <a name="see-also"></a>Zobacz też

[\<>ustawień regionalnych](../standard-library/locale.md)\
[klasa facet](../standard-library/locale-class.md#facet_class)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
