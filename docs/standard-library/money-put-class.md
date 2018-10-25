---
title: money_put — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/std::money_put
- xlocmon/std::money_put::char_type
- xlocmon/std::money_put::iter_type
- xlocmon/std::money_put::string_type
- xlocmon/std::money_put::do_put
- xlocmon/std::money_put::put
dev_langs:
- C++
helpviewer_keywords:
- std::money_put [C++]
- std::money_put [C++], char_type
- std::money_put [C++], iter_type
- std::money_put [C++], string_type
- std::money_put [C++], do_put
- std::money_put [C++], put
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6163e3db11da717eaf188b4b2f585f78d7eb511
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073373"
---
# <a name="moneyput-class"></a>money_put — Klasa

Klasa szablonu opisuje obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu kontroli konwersji wartości pieniężnych na sekwencje typu `CharType`.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class money_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

*OutputIterator*<br/>
Typ iteratora, do którego funkcje pieniężne put zapisują swoje dane wyjściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba dostępu do jego przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikator.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[money_put](#money_put)|Konstruktor dla obiektów typu `money_put`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wyjściowych.|
|[string_type](#string_type)|Typ, który opisuje ciąg zawierający znaki typu `CharType`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[do_put](#do_put)|Funkcja wirtualna wywoływana w celu przekonwertowania liczby lub ciągu na sekwencję znaków, która reprezentuje wartość pieniężną.|
|[put](#put)|Konwertuje liczbę lub ciąg na sekwencję znaków, która reprezentuje wartość pieniężną.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="char_type"></a>  money_put::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu **CharType**.

## <a name="do_put"></a>  money_put::do_put

Funkcja wirtualna wywoływana w celu przekonwertowania liczby lub ciągu na sekwencję znaków, która reprezentuje wartość pieniężną.

```cpp
virtual iter_type do_put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    const string_type& val) const;

virtual iter_type do_put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

### <a name="parameters"></a>Parametry

*next*<br/>
Iterator adresujący pierwszy element wstawiony ciągu.

*_Intl*<br/>
Wartość logiczną wskazującą typ symbolu waluty, oczekiwano w sekwencji: **true** Jeśli międzynarodowe, **false** Jeśli krajowych.

*_Iosbase*<br/>
Flagi formatu, który po zestaw wskazuje, że symbol waluty jest opcjonalna. w przeciwnym razie jest wymagana

*_Fill*<br/>
Znak, który jest używany do rozdzielenia.

*Val*<br/>
Obiekt ciągu ma zostać przekonwertowany.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych adresy jednej pozycji za ostatnim elementem generowany.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja wirtualna elementu członkowskiego chronionego generuje elementów sekwencyjnego, rozpoczynając od *dalej* do produkcji pola pieniężnych danych wyjściowych z [string_type](#string_type) obiektu *val*. Na sekwencję kontrolowaną przez *val* musi zaczynać się od jednego lub więcej cyfr dziesiętnych, opcjonalnie poprzedzona znakiem minus (-), który reprezentuje wartość. Funkcja zwraca iterację, wyznaczanie pierwszego elementu poza pole wygenerowanego pieniężnych danych wyjściowych.

Druga funkcja wirtualna elementu członkowskiego chronionego zachowuje się taka sama jak pierwsza strona, z wyjątkiem że skutecznie pierwszy konwertuje *val* sekwencję cyfr dziesiętnych, opcjonalnie poprzedzona znakiem minus, a następnie konwertuje tej sekwencji opisanych powyżej.

Format pola pieniężnych danych wyjściowych jest określany przez [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class) fac zwracany przez wywołanie (aktywne) [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **intl**>> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)).

W szczególności:

- **FAC**. [pos_format —](../standard-library/moneypunct-class.md#pos_format) określa kolejność, w którym składniki, które pola są generowane dla wartość nieujemną.

- **FAC**. [neg_format —](../standard-library/moneypunct-class.md#neg_format) określa kolejność, w którym składniki, które pola są generowane dla wartości ujemnej.

- **FAC**. [curr_symbol —](../standard-library/moneypunct-class.md#curr_symbol) określa kolejność elementów do wygenerowania symbolu waluty.

- **FAC**. [positive_sign —](../standard-library/moneypunct-class.md#positive_sign) określa kolejność elementów, aby wygenerować znak wartości dodatnich.

- **FAC**. [negative_sign —](../standard-library/moneypunct-class.md#negative_sign) określa kolejność elementów w celu wygenerowania dla znaku ujemnego.

- **FAC**. [Grupowanie](../standard-library/moneypunct-class.md#grouping) określa sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.

- **FAC**. [thousands_sep —](../standard-library/moneypunct-class.md#thousands_sep) określa element, który oddziela grup cyfr na lewo od każdego znaku dziesiętnego.

- **FAC**. [decimal_point —](../standard-library/moneypunct-class.md#decimal_point) określa element, który oddziela liczby całkowite od cyfr wszelkie końcowej.

- **FAC**. [frac_digits —](../standard-library/moneypunct-class.md#frac_digits) określa liczbę cyfr znaczących ułamek z prawej strony każdego separatora dziesiętnego.

Jeśli parametry logowania ( **fac**. `negative_sign` lub **fac**. `positive_sign`) ma więcej niż jeden element, tylko pierwszy element jest generowany gdy element równy **money_base::sign** pojawia się we wzorcu formatu ( **fac**. `neg_format` lub **fac**. `pos_format`). Wszystkie pozostałe elementy są generowane na końcu pola pieniężnych danych wyjściowych.

Jeśli **iosbase**. [flagi](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) jest różna od zera, ciąg **fac**. `curr_symbol` jest generowany gdy element równy **money_base::symbol** pojawia się we wzorcu formatu. W przeciwnym razie zostanie wygenerowany bez symbolu waluty.

Jeśli narzuca bez ograniczeń grupowania **fac**. **Grupowanie** (jej pierwszego elementu z wartością CHAR_MAX), następnie żadnych wystąpień **fac**. `thousands_sep` są generowane w część wartości pola pieniężnych danych wyjściowych (gdzie element równy **money_base::value** pojawia się we wzorcu formatu). Jeśli **fac**. `frac_digits` zero, a następnie nie wystąpienie **fac**. `decimal_point` jest generowany po cyfr dziesiętnych. W przeciwnym razie pola pieniężnych danych wyjściowych wynikowego umieszcza niskiego rzędu **fac**. `frac_digits` cyfry po prawej stronie przecinka dziesiętnego.

Dopełnienie występuje, jak w przypadku dowolnego pola liczbowego danych wyjściowych, chyba że **iosbase**. **flagi** & **iosbase**. [wewnętrzny](../standard-library/ios-functions.md#internal) ma wartość różną od zera, wszelkie wewnętrzny uzupełnień jest generowany gdy element równy **money_base::space** pojawia się we wzorcu formatu, jeśli są wyświetlane. W przeciwnym razie dopełnienie wewnętrzne występuje przed wygenerowanym sekwencji. Jest znak dopełnienia **wypełnienia**.

Wywołania funkcji **iosbase**. **szerokość**(0), można zresetować szerokość pola na wartość zero.

### <a name="example"></a>Przykład

Zobacz przykład [umieścić](#put), w którym funkcja wirtualna elementu członkowskiego jest wywoływana przez **umieścić**.

## <a name="iter_type"></a>  money_put::iter_type

Typ, który opisuje iterator danych wyjściowych.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu **OutputIterator.**

## <a name="money_put"></a>  money_put::money_put

Konstruktor dla obiektów typu `money_put`.

```cpp
explicit money_put(size_t _Refs = 0);
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

Konstruktor inicjuje jego podstawowego obiektu z **locale::**[aspekt](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="put"></a>  money_put::Put

Konwertuje liczbę lub ciąg na sekwencję znaków, która reprezentuje wartość pieniężną.

```cpp
iter_type put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    const string_type& val) const;

iter_type put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

### <a name="parameters"></a>Parametry

*next*<br/>
Iterator adresujący pierwszy element wstawiony ciągu.

*_Intl*<br/>
Wartość logiczną wskazującą typ symbolu waluty, oczekiwano w sekwencji: **true** Jeśli międzynarodowe, **false** Jeśli krajowych.

*_Iosbase*<br/>
Flagi formatu, który po zestaw wskazuje, że symbol waluty jest opcjonalna. w przeciwnym razie jest wymagana

*_Fill*<br/>
Znak, który jest używany do rozdzielenia.

*Val*<br/>
Obiekt ciągu ma zostać przekonwertowany.

### <a name="return-value"></a>Wartość zwracana

Iterator danych wyjściowych adresy jednej pozycji za ostatnim elementem generowany.

### <a name="remarks"></a>Uwagi

Obie funkcje Członkowskie zwracają [do_put —](#do_put)( `next`, `_Intl`, `_Iosbase`, `_Fill`, `val`).

### <a name="example"></a>Przykład

```cpp
// money_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
//   locale loc( "german_germany" );
   locale loc( "english_canada" );
   basic_stringstream<char> psz, psz2;
   ios_base::iostate st = 0;

   psz2.imbue( loc );
   psz2.flags( psz2.flags( )|ios_base::showbase ); // force the printing of the currency symbol
   use_facet < money_put < char > >(loc).put(basic_ostream<char>::_Iter( psz2.rdbuf( ) ), true, psz2, st, 100012);
   if (st & ios_base::failbit)
      cout << "money_put( ) FAILED" << endl;
   else
      cout << "money_put( ) = \"" << psz2.rdbuf( )->str( ) <<"\""<< endl;

   st = 0;
};
```

```Output
money_put( ) = "CAD1,000.12"
```

## <a name="string_type"></a>  money_put::STRING_TYPE

Typ, który opisuje ciąg zawierający znaki typu `CharType`.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizacji szablonu klasy [basic_string](../standard-library/basic-string-class.md) których obiekty można przechowywać elementów z sekwencji źródłowej.

## <a name="see-also"></a>Zobacz także

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>
[facet — klasa](../standard-library/locale-class.md#facet_class)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
