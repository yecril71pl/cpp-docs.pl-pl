---
title: num_get — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
ms.openlocfilehash: 76d2832141c65ca67c42f1994a3c8f5b532f0092
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373657"
---
# <a name="num_get-class"></a>num_get — Klasa

Szablon klasy, który opisuje obiekt, który może służyć jako aspekt ustawień `CharType` regionalnych do kontrolowania konwersji sekwencji typu do wartości liczbowych.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

*InputIterator*\
Typ iteratora, z którego liczbowe funkcje get odczytują swoje dane wejściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[num_get](#num_get)|Konstruktor obiektów typu, `num_get` które są używane do wyodrębniania wartości liczbowych z sekwencji.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wejściowych.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[do_get](#do_get)|Funkcja wirtualna wywoływana w celu wyodrębniania wartości liczbowej lub logicznej z sekwencji znaków.|
|[get](#get)|Wyodrębnia wartość liczbową lub logiczną z sekwencji znaków.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="num_getchar_type"></a><a name="char_type"></a>num_get::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType**.

## <a name="num_getdo_get"></a><a name="do_get"></a>num_get::do_get

Funkcja wirtualna wywoływana w celu wyodrębniania wartości liczbowej lub logicznej z sekwencji znaków.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Początek zakresu znaków, z których należy odczytać liczbę.

*Ostatnio*\
Koniec zakresu znaków, z których ma być odczytywany numer.

*baza iosbase*\
[ios_base,](../standard-library/ios-base-class.md) których flagi są używane przez konwersję.

*Państwa*\
Stan, do którego failbit (zobacz [ios_base::iostate)](../standard-library/ios-base-class.md#iostate)jest dodawany po awarii.

*Val*\
Wartość, która została przeczytana.

### <a name="return-value"></a>Wartość zwracana

Iterator po odczytywanie wartości.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja wirtualnego chronionego elementu członkowskiego,

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;
```

dopasowuje kolejne elementy rozpoczynające się `[first, last)` od *początku* w sekwencji, dopóki nie rozpozna kompletne, niepusty pole wprowadzania całkowitych. Jeśli się powiedzie, konwertuje to pole na jego wartość równoważną jako typ **długi**i przechowuje wynik w *wartości val*. Zwraca iterator wyznaczający pierwszy element poza pole danych liczbowych. W przeciwnym razie funkcja *val* nie `ios_base::failbit` przechowuje nic w val i ustawia się w `state`. Zwraca iterator wyznaczający pierwszy element poza prefiksem prawidłowego pola wejściowego liczby całkowitej. W obu przypadkach, jeśli zwracana `last`wartość jest `ios_base::eofbit` `state`równa, funkcja ustawia się w .

Pole wejściowe liczby całkowitej jest konwertowane przez te same reguły używane przez funkcje skanowania do dopasowywania i konwertowania serii elementów **char** z pliku. (Zakłada **char** się, że każdy taki element char `Elem` mapuje do równoważnego elementu typu za pomocą prostego mapowania jeden do jednego). Równoważną specyfikację konwersji skanowania określa się w następujący sposób:

Jeśli `iosbase.` [ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), specyfikacja `lo`konwersji jest .

Jeśli `iosbase.flags() & ios_base::basefield == ios_base::` [hex](../standard-library/ios-functions.md#hex), specyfikacja konwersji jest `lx`.

Jeśli `iosbase.flags() & ios_base::basefield == 0`specyfikacja konwersji jest `li`.

W przeciwnym razie `ld`specyfikacja konwersji to .

Format pola wejściowego liczby całkowitej jest dalej określany`fac` przez aspekt ustawień regionalnych zwracany przez [wywołanie](../standard-library/locale-class.md#facet_class) [use_facet](../standard-library/locale-functions.md#use_facet) `<` [numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())`. Są to:

`fac.`[numpunct::grupowanie](../standard-library/numpunct-class.md#grouping) `()` określa sposób grupowania cyfr po lewej stronie dowolnego przecinka dziesiętnego

`fac.`[numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` określa sekwencję oddzielaą grupy cyfr po lewej stronie dowolnego przecinka dziesiętnego.

Jeśli w polu `fac.thousands_sep()` danych wejściowych liczbowych nie występują żadne wystąpienia, nie jest narzucane żadne ograniczenie grupowania. W przeciwnym razie wszelkie ograniczenia `fac.grouping()` grupowania nałożone przez są wymuszane i separatory są usuwane przed konwersji skanowania występuje.

Czwarta funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

zachowuje się tak samo jak pierwszy, z tą `ld` różnicą, że zastępuje specyfikację konwersji za pomocą `lu`pliku . Jeśli się powiedzie, konwertuje pole danych liczbowych na wartość typu **niepodpisaną long** i przechowuje tę wartość w *wartości val*.

Piąta funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;
```

zachowuje się tak samo jak pierwszy, z tą `ld` różnicą, że zastępuje specyfikację konwersji za pomocą `lld`pliku . Jeśli się powiedzie, konwertuje pole danych liczbowych na wartość typu **long long** i przechowuje tę wartość w *wartości val*.

Szósta funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;
```

zachowuje się tak samo jak pierwszy, z tą `ld` różnicą, że zastępuje specyfikację konwersji za pomocą `llu`pliku . Jeśli się powiedzie, konwertuje pole danych liczbowych na wartość typu **niepodpisaną długo** i przechowuje tę wartość w *wartości val*.

Siódma funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że stara się dopasować kompletne, niepusty zmiennoprzecinkowe pole wejściowe. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` określa sekwencję oddzielaną cyfry całkowite od cyfr ułamka. Równoważnym specyfikatorem `lf`konwersji skanowania jest .

Ósma funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że stara się dopasować kompletne, niepusty zmiennoprzecinkowe pole wejściowe. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` określa sekwencję oddzielaną cyfry całkowite od cyfr ułamka. Równoważnym specyfikatorem `lf`konwersji skanowania jest .

Dziewiąta funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

zachowuje się tak samo jak ósmy, z tą `Lf`różnicą, że odpowiednik specyfikatora konwersji skanowania jest .

Dziesiąta funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

zachowuje się tak samo pierwszy, z tą różnicą, że odpowiednik specyfikator konwersji skanowania jest `p`.

Ostatnia (jedenasta) funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że stara się dopasować do pełnego, niepuste pole wejściowe logiczne. Jeśli się powiedzie, konwertuje pole wejściowe logiczne na wartość **typu bool** i przechowuje tę wartość w *wartości val*.

Pole wejściowe logiczne przyjmuje jedną z dwóch form. Jeśli `iosbase.flags() & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) jest false, jest taka sama jak pole wejściowe liczby całkowitej, z tą różnicą, że przekonwertowana wartość musi być 0 (dla false) lub 1 (dla true). W przeciwnym razie sekwencja musi być zgodna `fac.` [z numpunct::falsename](../standard-library/numpunct-class.md#falsename) `()` (dla false) lub `fac.` [numpunct::truename](../standard-library/numpunct-class.md#truename) `()` (dla true).

### <a name="example"></a>Przykład

Zobacz [przykład, aby uzyskać](#get), gdzie funkcja `do_get`wirtualnego elementu członkowskiego jest wywoływana przez .

## <a name="num_getget"></a><a name="get"></a>num_get::get

Wyodrębnia wartość liczbową lub logiczną z sekwencji znaków.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Początek zakresu znaków, z których należy odczytać liczbę.

*Ostatnio*\
Koniec zakresu znaków, z których ma być odczytywany numer.

*baza iosbase*\
[ios_base,](../standard-library/ios-base-class.md) których flagi są używane przez konwersję.

*Państwa*\
Stan, do którego failbit (zobacz [ios_base::iostate)](../standard-library/ios-base-class.md#iostate)jest dodawany po awarii.

*Val*\
Wartość, która została przeczytana.

### <a name="return-value"></a>Wartość zwracana

Iterator po odczytywanie wartości.

### <a name="remarks"></a>Uwagi

Wszystkie funkcje członkowskie zwracają [do_get](#do_get)`( first, last, iosbase, state, val)`.

Pierwsza funkcja wirtualnego chronionego elementu członkowskiego próbuje dopasować kolejne elementy `first` `last`rozpoczynające się od początku w sekwencji [ , ), dopóki nie rozpozna kompletne, niepusty pole wejściowe liczby całkowitej. Jeśli się powiedzie, konwertuje to pole na jego równoważną wartość jako typ **długi** i przechowuje wynik w *wartości .* Zwraca iterator wyznaczający pierwszy element poza pole danych liczbowych. W przeciwnym razie funkcja przechowuje `ios_base::failbit` nic w *val* i ustawia w *stanie*. Zwraca iterator wyznaczający pierwszy element poza prefiksem prawidłowego pola wejściowego liczby całkowitej. W obu przypadkach, jeśli zwracana wartość jest `ios_base::eofbit` równa *ostatniej,* funkcja ustawia się w *stanie*.

Pole wejściowe liczby całkowitej jest konwertowane przez te same reguły używane przez funkcje skanowania do dopasowywania i konwertowania serii elementów **char** z pliku. Każdy **taki** char element zakłada się mapować `CharType` do równoważnego elementu typu przez proste, jeden do jednego mapowania. Równoważną specyfikację konwersji skanowania określa się w następujący sposób:

- Jeśli `iosbase.` [flagi](../standard-library/ios-base-class.md#flags)`& ios_base::basefield == ios_base::`[z października,](../standard-library/ios-functions.md#oct)specyfikacja konwersji jest `lo`.

- Jeśli `iosbase.flags & ios_base::basefield == ios_base::` [hex](../standard-library/ios-functions.md#hex), specyfikacja konwersji jest `lx`.

- Jeśli `iosbase.flags & ios_base::basefield == 0`specyfikacja konwersji jest `li`.

- W przeciwnym razie `ld`specyfikacja konwersji to .

Format pola wejściowego liczby całkowitej jest dalej określany przez [use_facet](../standard-library/locale-functions.md#use_facet)`<`[`numpunct`](../standard-library/numpunct-class.md)`<Elem>(iosbase.` [aspekt](../standard-library/locale-class.md#facet_class) `fac` ustawień regionalnych zwracany przez wywołanie use_facet[getloc](../standard-library/ios-base-class.md#getloc)`())`. Są to:

- `fac.`[grupowanie](../standard-library/numpunct-class.md#grouping) określa sposób grupowania cyfr po lewej stronie dowolnego przecinka dziesiętnego.

- `fac.`[thousands_sep](../standard-library/numpunct-class.md#thousands_sep) określa sekwencję oddzielaą grupy cyfr po lewej stronie dowolnego przecinka dziesiętnego.

Jeśli w polu `fac.thousands_sep` danych wejściowych liczbowych nie występują żadne wystąpienia, nie jest narzucane żadne ograniczenie grupowania. W przeciwnym razie wszelkie ograniczenia `fac.grouping` grupowania nałożone przez jest wymuszane i separatory są usuwane przed konwersji skanowania występuje.

Druga funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

zachowuje się tak samo jak pierwszy, z tą `ld` różnicą, że zastępuje specyfikację konwersji za pomocą `lu`pliku . Jeśli się powiedzie, konwertuje pole danych liczbowych na wartość typu **niepodpisaną long** i przechowuje tę wartość w *wartości val*.

Trzecia funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że próbuje dopasować kompletne, niepusty zmiennoprzecinkowe pole wejściowe. `fac.`[decimal_point](../standard-library/numpunct-class.md#decimal_point) określa sekwencję oddzielaną cyfry całkowite od cyfr ułamkowych. Równoważnym specyfikatorem `lf`konwersji skanowania jest .

Czwarta funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

zachowuje się tak samo trzeci, z tą różnicą, że odpowiednik specyfikatora konwersji skanowania jest `Lf`.

Piąta funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

zachowuje się tak samo pierwszy, z tą różnicą, że odpowiednik specyfikator konwersji skanowania jest `p`.

Szósta funkcja wirtualnego chronionego elementu członkowskiego:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

zachowuje się tak samo jak pierwszy, z tą różnicą, że próbuje dopasować kompletne, niepuste pole wejściowe logiczne. Jeśli się powiedzie, konwertuje pole wejściowe logiczne na wartość **typu bool** i przechowuje tę wartość w *wartości val*.

Pole wejściowe logiczne przyjmuje jedną z dwóch form. Jeśli `iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) jest **false**, jest taka sama jak pole wejściowe liczby całkowitej, z tą różnicą, że przekonwertowana wartość musi wynosić 0 (dla **false)** lub 1 (dla **true).** W przeciwnym razie sekwencja `fac.`musi być zgodna albo `fac.` [falsename](../standard-library/numpunct-class.md#falsename) (dla **false)** lub [truename](../standard-library/numpunct-class.md#truename) (dla **true).**

### <a name="example"></a>Przykład

```cpp
// num_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   basic_stringstream<char> psz, psz2;
   psz << "-1000,56";

   ios_base::iostate st = 0;
   long double fVal;
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;

   psz.imbue( loc );
   use_facet <num_get <char> >
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter(0), psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get( ) FAILED" << endl;
   else
      cout << "money_get( ) = " << fVal << endl;
}
```

## <a name="num_getiter_type"></a><a name="iter_type"></a>num_get::iter_type

Typ, który opisuje iterator danych wejściowych.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `InputIterator`szablonu .

## <a name="num_getnum_get"></a><a name="num_get"></a>num_get::num_get

Konstruktor obiektów typu, `num_get` które są używane do wyodrębniania wartości liczbowych z sekwencji.

```cpp
explicit num_get(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

*Bibl*\
Wartość całkowita używana do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *refs* i ich znaczenie to:

- 0: Okres istnienia obiektu jest zarządzany przez ustawienia regionalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: Te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój `locale::`obiekt bazowy z [aspektem](../standard-library/locale-class.md#facet_class)`(refs)`.

## <a name="see-also"></a>Zobacz też

[\<>ustawień regionalnych](../standard-library/locale.md)\
[klasa facet](../standard-library/locale-class.md#facet_class)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
