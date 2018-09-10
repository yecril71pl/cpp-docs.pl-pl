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
ms.openlocfilehash: 19e08d1544a23ad1272bde5066a63f37b1e511fd
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100927"
---
# <a name="numput-class"></a>num_put — Klasa

Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu kontroli konwersji wartości liczbowych na sekwencje typu `CharType`.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

*OutputIterator*<br/>
Typ iteratora, do którego funkcje numeryczne put zapisują swoje dane wyjściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba dostępu do jego przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikator.**

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

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[do_put](#do_put)|Funkcja wirtualna, która jest wywoływana w celu przekonwertowania liczby na sekwencję `CharType`s, która reprezentuje liczbę sformatowaną dla danego ustawienia regionalnego.|
|[put](#put)|Konwertuje liczbę na sekwencję `CharType`s, która reprezentuje liczbę sformatowaną dla danego ustawienia regionalnego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="char_type"></a>  num_put::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `CharType`.

## <a name="do_put"></a>  num_put::do_put

Funkcja wirtualna, która jest wywoływana w celu przekonwertowania liczby na sekwencję `CharType`s, która reprezentuje liczbę sformatowaną dla danego ustawienia regionalnego.

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

*next*<br/>
Iterator adresujący pierwszy element wstawiony ciągu.

*_Iosbase*<br/>
Należy określić strumień, który zawiera ustawień regionalnych przy użyciu reguł numpunct — umożliwia znak przestankowy danych wyjściowych i flagi do formatowania danych wyjściowych.

*_Fill*<br/>
Znak, który jest używany do rozdzielenia.

*Val*<br/>
Liczba lub typu Boolean, który ma być danych wyjściowych.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych adresy jednej pozycji za ostatnim elementem generowany.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja wirtualna elementu członkowskiego chronionego generuje elementów sekwencyjnego, rozpoczynając od *dalej* aby wygenerować dane wyjściowe pola Liczba całkowita od wartości *val*. Funkcja zwraca iterator wyznaczanie dalej miejscem, w którym można wstawić elementu poza pole danych wyjściowych wygenerowana liczba całkowita.

Pola Liczba całkowita w danych wyjściowych jest generowany przez te same zasady, które są używane przez funkcje drukowania do generowania szereg **char** elementy do pliku. Przyjęto, że każdy element char mapowania na równoważne elementu typu `CharType` przez mapowania proste, jeden do jednego. W przypadku, gdy funkcja drukowania dopełnia pola z miejsc do magazynowania lub cyfry 0, jednak `do_put` zamiast tego używa `fill`. Specyfikacja równoważna konwersji wydruku jest określany w następujący sposób:

- Jeśli **iosbase**. [flagi](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct), to specyfikacja konwersji `lo`.

- Jeśli **iosbase.flags** & **ios_base::basefield** == `ios_base::`[szesnastkowy](../standard-library/ios-functions.md#hex), to specyfikacja konwersji `lx`.

- W przeciwnym razie jest specyfikacja konwersji `ld`.

Jeśli **iosbase**. [szerokość](../standard-library/ios-base-class.md#width) jest różna od zera, szerokość pola w tej wartości jest dołączony. Następnie wywołuje funkcję **iosbase**. **szerokość**(0), można zresetować szerokość pola na wartość zero.

Dopełnienie występuje tylko wtedy, gdy minimalną liczbę elementów *N* określić pole danych wyjściowych jest mniejsza niż **iosbase**. [szerokość](../standard-library/ios-base-class.md#width). Takie dopełnienie składa się z sekwencji *N* - **szerokość** kopie **wypełnienia**. Dopełnienie następnie odbywa się w następujący sposób:

- Jeśli **iosbase**. **flagi** & `ios_base::adjustfield` == `ios_base::`[po lewej stronie](../standard-library/ios-functions.md#left), Flaga **-** jest dołączony. (Dopełnienie występuje po wygenerowanego tekstu.)

- Jeśli **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[wewnętrzny](../standard-library/ios-functions.md#internal), Flaga **0** jest dołączony. (Pola liczbowego danych wyjściowych, dopełnienie występuje gdy konsoli funkcji drukowania od 0.)

- W przeciwnym razie jest poprzedzona nie dodatkowe flagi. (Dopełnienie występuje przed wygenerowanym sekwencji.)

Na koniec:

- Jeśli **iosbase**. **flagi** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) jest różna od zera, Flaga **+** jest dołączony do specyfikacja konwersji.

- Jeśli **iosbase**. **flagi** & **ios_base —::**[showbase](../standard-library/ios-functions.md#showbase) jest różna od zera, Flaga **#** jest dołączony do specyfikacja konwersji.

Format liczby całkowitej danych wyjściowych pola dalsze jest określana przez [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class)**fac** zwracany przez wywołanie [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct — ](../standard-library/numpunct-class.md) \< **Elem**> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). W szczególności:

- **FAC**. [Grupowanie](../standard-library/numpunct-class.md#grouping) określa sposób grupowania cyfr na lewo od każdego znaku dziesiętnego

- **FAC**. [thousands_sep —](../standard-library/numpunct-class.md#thousands_sep) określa kolejność, która oddziela grup cyfr na lewo od każdego znaku dziesiętnego

Jeśli narzuca bez ograniczeń grupowania **fac**. **Grupowanie** (jej pierwszego elementu z wartością CHAR_MAX), następnie żadnych wystąpień **fac**. `thousands_sep` w polu dane wyjściowe będą generowane. W przeciwnym razie separatory są wstawiane po konwersji drukowania.

Druga funkcja wirtualna elementu członkowskiego chronionego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

zachowuje się taka sama jak pierwsza strona, z tą różnicą, że zastępuje specyfikacja konwersji `ld` z `lu`.

Trzecia funkcja wirtualna elementu członkowskiego chronionego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

zachowuje się taka sama jak pierwsza strona, chyba że generuje pole zmiennoprzecinkowych dane wyjściowe z wartości **val**. **FAC**. [decimal_point —](../standard-library/numpunct-class.md#decimal_point) określa kolejność, która oddziela liczby całkowite od cyfr końcowej. Specyfikacja równoważna konwersji wydruku jest określany w następujący sposób:

- Jeśli **iosbase**. **flagi** & `ios_base::floatfield` == `ios_base::`[stałej](../standard-library/ios-functions.md#fixed), to specyfikacja konwersji `lf`.

- Jeśli **iosbase**. **flagi** & **ios_base::floatfield** == `ios_base::`[naukowych](../standard-library/ios-functions.md#scientific), to specyfikacja konwersji `le`. Jeśli **iosbase**. **flagi** & `ios_base::`[wielkie](../standard-library/ios-functions.md#uppercase) jest różna od zera, `e` zostaje zastąpiona opcją `E`.

- W przeciwnym razie jest specyfikacja konwersji **lg**. Jeśli **iosbase**. **flagi** & **ios_base::uppercase** jest różna od zera, `g` zostaje zastąpiona opcją `G`.

Jeśli **iosbase**. **flagi** & **ios_base::fixed** jest różna od zera lub jeśli **iosbase**. [dokładność](../standard-library/ios-base-class.md#precision) jest większa od zera, dokładności, wartością **iosbase**. **dokładność** jest dołączony do specyfikacja konwersji. Wszelkie dopełnienie zachowuje się takie same jak dla pola Liczba całkowita danych wyjściowych. Jest znak dopełnienia **wypełnienia**. Na koniec:

- Jeśli **iosbase**. **flagi** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) jest różna od zera, Flaga **+** jest dołączony do specyfikacja konwersji.

- Jeśli **iosbase**. **flagi** & `ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint) jest różna od zera, Flaga **#** jest dołączony do specyfikacja konwersji.

Czwarty chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

działa tak samo trzeci, chyba że kwalifikator `l` w konwersji jest zastępowany specyfikacji `L`.

Piąty chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

działa tak samo, pierwsza strona, z tą różnicą, że jest specyfikacja konwersji `p` **,** oraz wszelkie kwalifikator potrzebne do określenia dopełnienia.

Szósty chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

zachowuje się taka sama jak pierwsza strona, z tą różnicą, że generuje pola logicznych dane wyjściowe z *val*.

Pola logicznych danych wyjściowych ma jedną z dwóch form. Jeśli **iosbase**. **flagi** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) jest **false**, funkcja elementu członkowskiego zwraca `do_put`(_ *dalej*, \_ *Iosbase*, \_ *wypełnienia*, ( **długie**) `val`), która zazwyczaj tworzy sekwencję wygenerowanego albo 0 (dla **false**) lub 1 (dla **true**). W przeciwnym razie wygenerowany sekwencji jest **fac**. [falsename —](../standard-library/numpunct-class.md#falsename) `)` (dla **false**), lub **fac**. [truename —](../standard-library/numpunct-class.md#truename) (dla **true**).

Siódmego chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

zachowuje się taka sama jak pierwsza strona, z tą różnicą, że zastępuje specyfikacja konwersji `ld` z `lld`.

Ósmego chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

zachowuje się taka sama jak pierwsza strona, z tą różnicą, że zastępuje specyfikacja konwersji `ld` z `llu`.

### <a name="example"></a>Przykład

Zobacz przykład [umieścić](#put), która wywołuje metodę `do_put`.

## <a name="iter_type"></a>  num_put::iter_type

Typ, który opisuje iterator danych wyjściowych.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu **OutputIterator.**

## <a name="num_put"></a>  num_put::num_put

Konstruktor dla obiektów typu `num_put`.

```cpp
explicit num_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*<br/>
Wartość liczby całkowitej, można określić typ zarządzania pamięci dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* parametrów i ich znaczenie są:

- 0: okres istnienia obiektu jest zarządzany przez ustawienia regionalne, zawierających go.

- 1: okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: nie zdefiniowano tych wartości.

Żadnych przykładów bezpośrednie są to tylko możliwe, ponieważ destruktor jest chroniony.

Konstruktor inicjuje jego podstawowego obiektu z **locale::**[aspekt](../standard-library/locale-class.md#facet_class)(_ *system plików Refs*).

## <a name="put"></a>  num_put::Put

Konwertuje liczbę na sekwencję `CharType`s, która reprezentuje liczbę sformatowaną dla danego ustawienia regionalnego.

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

*dest*<br/>
Iterator adresujący pierwszy element wstawiony ciągu.

*_Iosbase*<br/>
Należy określić strumień, który zawiera ustawień regionalnych przy użyciu reguł numpunct — umożliwia znak przestankowy danych wyjściowych i flagi do formatowania danych wyjściowych.

*_Fill*<br/>
Znak, który jest używany do rozdzielenia.

*Val*<br/>
Liczba lub typu Boolean, który ma być danych wyjściowych.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych adresy jednej pozycji za ostatnim elementem generowany.

### <a name="remarks"></a>Uwagi

Wszystkie funkcje Członkowskie zwracają [do_put —](#do_put)( `next`, `_Iosbase`, `_Fill`, `val`).

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
