---
title: num_put — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocnum/std::num_put
- locale/std::num_put::char_type
- locale/std::num_put::iter_type
- locale/std::num_put::do_put
- locale/std::num_put::put
dev_langs:
- C++
helpviewer_keywords:
- std::num_put [C++]
- std::num_put [C++], char_type
- std::num_put [C++], iter_type
- std::num_put [C++], do_put
- std::num_put [C++], put
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a860f7c266685e7e10f9b4cbe46c280c356f2681
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="numput-class"></a>num_put — Klasa

Szablon klasy, która opisuje obiekt, który może służyć jako zestaw reguł ustawienia regionalne do sterowania konwersji wartości liczbowych sekwencji typu `CharType`.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

`CharType` Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

`OutputIterator` Typ iteratora, w której funkcje numeryczne put zapisuje ich dane wyjściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba jej wartości przechowywanej dostępu są przechowywane w unikatową wartość dodatnią **identyfikator.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[num_put](#num_put)|Konstruktor dla obiektów typu `num_put`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wyjściowych.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[do_put](#do_put)|Wirtualny funkcję wywoływaną w taki sposób, aby przekonwertować numeru sekwencji `CharType`s, który reprezentuje liczbę sformatowany dla danego ustawień regionalnych.|
|[put](#put)|Konwertuje liczbę do sekwencji `CharType`s, co oznacza liczbę sformatowany dla danego ustawień regionalnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** Standard

## <a name="char_type"></a>  num_put::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType**.

## <a name="do_put"></a>  num_put::do_put

Wirtualny funkcję wywoływaną w taki sposób, aby przekonwertować numeru sekwencji **CharType**s, który reprezentuje liczbę sformatowany dla danego ustawień regionalnych.

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

`next` Iteratora adresowania pierwszego elementu obiektu wstawionych ciągów.

`_Iosbase` Określony strumień, który zawiera ustawienia regionalne z aspekt numpunct — umożliwia znak przestankowy dane wyjściowe i flagi formatowanie danych wyjściowych.

`_Fill` Znak używany do rozdzielenia.

`val` Liczba lub typ Boolean, który ma być danych wyjściowych.

### <a name="return-value"></a>Wartość zwracana

Dane wyjściowe iteratora wyprodukowanych pozycji jeden po ostatnim elemencie adresy.

### <a name="remarks"></a>Uwagi

Pierwszej funkcji wirtualnych chroniony element członkowski generuje elementy sekwencyjnych, zaczynając od `next` polu dane wyjściowe liczbą całkowitą od wartości `val`. Funkcja zwraca iteratora wyznaczenie dalej miejsca do wstawienia elementu poza pola danych wyjściowych wygenerowanych liczby całkowitej.

W polu dane wyjściowe liczba całkowita jest generowany przez te same reguły używane przez funkcje drukowania generowania serii `char` elementy do pliku. Przyjęto, że każdy element char mapowania na równoważny element typu **CharType** mapowanie proste i jeden do jednego. W przypadku, gdy funkcja wydruku dopełnia pola spacjami lub cyfry 0, jednak `do_put` użyje **wypełnienia**. Specyfikacja równoważne konwersji wydruku jest określane w następujący sposób:

- Jeśli **iosbase**. [flagi](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct), specyfikacja konwersji jest **lo**.

- Jeśli **iosbase.flags** & **ios_base::basefield** == `ios_base::`[szesnastkowych](../standard-library/ios-functions.md#hex), specyfikacja konwersji jest **lx** .

- W przeciwnym razie specyfikacja konwersji jest **ld**.

Jeśli **iosbase**. [szerokość](../standard-library/ios-base-class.md#width) jest różna od zera, jest reprezentowana szerokość pola tej wartości. Wywołuje funkcję **iosbase**. **szerokość**(0), można zresetować szerokość pola od zera.

Dopełnienie występuje tylko wtedy, gdy minimalną liczbę elementów *N* wymagane do określenia pola danych wyjściowych jest mniejsza niż **iosbase**. [szerokość](../standard-library/ios-base-class.md#width). Takie uzupełnienie składa się z sekwencji *N* - **szerokość** kopie **wypełnienia**. Dopełnienie następnie odbywa się w następujący sposób:

- Jeśli **iosbase**. **flagi** & `ios_base::adjustfield` == `ios_base::`[po lewej stronie](../standard-library/ios-functions.md#left), Flaga **-** jest dołączany na początku. (Po wygenerowanego tekstu występuje dopełnienie.)

- Jeśli **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[wewnętrzny](../standard-library/ios-functions.md#internal), Flaga **0** dołączany początku. (Pola liczbowego danych wyjściowych, dopełnienie występuje, gdy funkcje drukowania uzupełniania 0.)

- W przeciwnym razie nie dodatkowe flagi jest dołączany początku. (Dopełnienie wcześniejsza wygenerowanego sekwencji).

Na koniec:

- Jeśli **iosbase**. **flagi** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) jest różna od zera, Flaga **+** jest dołączany na początku specyfikacji konwersji.

- Jeśli **iosbase**. **flagi** & **ios_base —::**[showbase](../standard-library/ios-functions.md#showbase) jest różna od zera, Flaga **#** jest dołączany na początku specyfikacji konwersji.

Format liczby całkowitej output pola dodatkowe jest określany przez [aspektu ustawień regionalnych](../standard-library/locale-class.md#facet_class)**fac** zwrócony przez wywołanie [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct — ](../standard-library/numpunct-class.md) \< **Elementu**> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). W szczególności:

- **FAC**. [Grupowanie](../standard-library/numpunct-class.md#grouping) określa sposób grupowania cyfr na lewo od dowolnego punktu dziesiętnego

- **FAC**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) określa sekwencji, która oddziela grup cyfr w lewą stronę dowolnego punktu dziesiętnego

Jeśli żadne ograniczenia grupowania są narzucone przez **fac**. **Grupowanie** (pierwszego elementu ma wartość char_max —), następnie żadnych wystąpień **fac**. `thousands_sep` w polu dane wyjściowe będą generowane. W przeciwnym razie wartość separatorów są wstawiane po konwersji wydruku.

Drugi funkcji wirtualnych chroniony element członkowski:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

zachowuje się taka sama jak pierwsza strona, z wyjątkiem tego, że zastępuje specyfikację konwersji **ld** z **lu**.

Trzeci funkcji wirtualnych chroniony element członkowski:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

zachowuje się taka sama jak pierwsza strona, z wyjątkiem tego, że tworzy pole zmiennoprzecinkowe dane wyjściowe z wartości **val**. **FAC**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) określa sekwencji, która oddziela cyfr liczbą całkowitą od cyfr ułamek. Specyfikacja równoważne konwersji wydruku jest określane w następujący sposób:

- Jeśli **iosbase**. **flagi** & `ios_base::floatfield` == `ios_base::`[stałej](../standard-library/ios-functions.md#fixed), specyfikacja konwersji jest **lf**.

- Jeśli **iosbase**. **flagi** & **ios_base::floatfield** == `ios_base::`[naukowych](../standard-library/ios-functions.md#scientific), specyfikacja konwersji jest `le`. Jeśli **iosbase**. **flagi** & `ios_base::`[wielkich](../standard-library/ios-functions.md#uppercase) jest różna od zera, **e** jest zastępowany **E**.

- W przeciwnym razie specyfikacja konwersji jest **lg**. Jeśli **iosbase**. **flagi** & **ios_base::uppercase** jest różna od zera, **g** jest zastępowany **G**.

Jeśli **iosbase**. **flagi** & **ios_base::fixed** jest różna od zera lub, jeśli **iosbase**. [dokładność](../standard-library/ios-base-class.md#precision) jest większa od zera, dokładności z wartością **iosbase**. **dokładność** jest dołączany na początku specyfikacji konwersji. Wszelkie uzupełniania działa tak samo jak w przypadku pola danych wyjściowych jest liczbą całkowitą. Jest znak dopełnienia **wypełnienia**. Na koniec:

- Jeśli **iosbase**. **flagi** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) jest różna od zera, Flaga **+** jest dołączany na początku specyfikacji konwersji.

- Jeśli **iosbase**. **flagi** & `ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint) jest różna od zera, Flaga **#** jest dołączany na początku specyfikacji konwersji.

Czwarty funkcji wirtualnych chroniony element członkowski:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

działa tak samo trzecie, z wyjątkiem kwalifikator **l** podczas konwersji jest zastępowany specyfikacji **L**.

Piąty funkcji wirtualnych chroniony element członkowski:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

działa tak samo, pierwsza strona, z wyjątkiem tego, że specyfikacja konwersji jest `p` **,** oraz wszelkie kwalifikator potrzebne do określania dopełnienia.

Szóstym funkcji wirtualnych chroniony element członkowski:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

zachowuje się taka sama jak pierwsza strona, z wyjątkiem tego, że generuje dane wyjściowe pole `val`.

Pole dane wyjściowe przyjmuje jeden z dwóch formach. Jeśli **iosbase**. **flagi** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) jest **false**, zwraca funkcja członkowska `do_put`(_ *dalej*, \_ *Iosbase*, \_ *wypełnienia*, ( **długi**) `val`), które zwykle tworzy sekwencję wygenerowanego albo 0 (dla **false**) lub 1 (dla **true**). W przeciwnym razie sekwencja wygenerowanego jest **fac**. [falsename](../standard-library/numpunct-class.md#falsename) `)` (dla **false**), lub **fac**. [truename](../standard-library/numpunct-class.md#truename) (dla **true**).

Siódmego funkcji wirtualnych chroniony element członkowski:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

zachowuje się taka sama jak pierwsza strona, z wyjątkiem tego, że zastępuje specyfikację konwersji **ld** z **lld**.

Ósmego funkcji wirtualnych chroniony element członkowski:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

zachowuje się taka sama jak pierwsza strona, z wyjątkiem tego, że zastępuje specyfikację konwersji `ld` z `llu`.

### <a name="example"></a>Przykład

Zobacz przykład [put](#put), które wywołuje `do_put`.

## <a name="iter_type"></a>  num_put::iter_type

Typ, który opisuje iterator danych wyjściowych.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **OutputIterator.**

## <a name="num_put"></a>  num_put::num_put

Konstruktor dla obiektów typu `num_put`.

```cpp
explicit num_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

`_Refs` Wartość całkowita używany do określania typu zarządzania pamięci dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości `_Refs` i ich znaczenie są:

- 0: okres istnienia obiektu zarządza ustawieniami regionalnymi, które zawierałoby proces.

- 1: okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: te wartości są niezdefiniowane.

Nie bezpośredniego przykładów to możliwe, ponieważ destruktor jest chroniony.

Konstruktor inicjuje jego obiektu podstawowego z **locale::**[aspektu](../standard-library/locale-class.md#facet_class)(_ *system plików Refs*).

## <a name="put"></a>  num_put::Put

Konwertuje liczbę do sekwencji **CharType**s, który reprezentuje liczbę sformatowany dla danego ustawień regionalnych.

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

`dest` Iteratora adresowania pierwszego elementu obiektu wstawionych ciągów.

`_Iosbase` Określony strumień, który zawiera ustawienia regionalne z aspekt numpunct — umożliwia znak przestankowy dane wyjściowe i flagi formatowanie danych wyjściowych.

`_Fill` Znak używany do rozdzielenia.

`val` Liczba lub typ Boolean, który ma być danych wyjściowych.

### <a name="return-value"></a>Wartość zwracana

Dane wyjściowe iteratora wyprodukowanych pozycji jeden po ostatnim elemencie adresy.

### <a name="remarks"></a>Uwagi

Wszystkie funkcje Członkowskie zwracają [do_put](#do_put)( `next`, `_Iosbase`, `_Fill`, `val`).

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

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>
[facet — klasa](../standard-library/locale-class.md#facet_class)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
