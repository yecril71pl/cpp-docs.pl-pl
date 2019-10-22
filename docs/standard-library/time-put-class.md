---
title: time_put — Klasa
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
helpviewer_keywords:
- std::time_put [C++]
- std::time_put [C++], char_type
- std::time_put [C++], iter_type
- std::time_put [C++], do_put
- std::time_put [C++], put
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
ms.openlocfilehash: 2c0ae501693a8abffc72a23be9c427f31bad65b6
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685420"
---
# <a name="time_put-class"></a>time_put — Klasa

Szablon klasy opisuje obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontrolowania konwersji wartości czasu na sekwencje typu `CharType`.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

@No__t_1 *CharType*
Typ używany w programie do kodowania znaków.

*OutputIterator* \
Typ iteratora, do którego funkcje czasu put zapisują swoje dane wyjściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[time_put](#time_put)|Konstruktor dla obiektów typu `time_put`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wyjściowych.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[do_put](#do_put)|Funkcja wirtualna, która wyprowadza informacje o dacie i godzinie jako sekwencję `CharType`s.|
|[Ubrani](#put)|Wyprowadza informacje o dacie i godzinie jako sekwencję `CharType`s.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<locale >

**Przestrzeń nazw:** std

## <a name="char_type"></a>time_put::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `CharType`.

## <a name="do_put"></a>time_put::d o_put

Funkcja wirtualna, która wyprowadza informacje o dacie i godzinie jako sekwencję `CharType`s.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>Parametry

*następny* \
Iterator danych wyjściowych, w którym sekwencja znaków reprezentująca datę i godzinę ma zostać wstawiona.

*_Iosbase* \
Przestrzeń.

*_Pt* \
Informacje o godzinie i dacie, które są wyprowadzane.

*_Fmt* \
Format danych wyjściowych. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l,](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać prawidłowe wartości.

*_Mod* \
Modyfikator dla formatu. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l,](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać prawidłowe wartości.

### <a name="return-value"></a>Wartość zwracana

Iterator do pierwszej pozycji po wstawieniu ostatniego elementu.

### <a name="remarks"></a>Uwagi

Wirtualna funkcja chroniona składowa generuje elementy sekwencyjne zaczynające się na `next` od wartości czasu przechowywanych w obiekcie \* `_Pt` typu `tm`. Funkcja zwraca iterator wyznaczający następne miejsce do wstawienia elementu poza wygenerowanymi danymi wyjściowymi.

Dane wyjściowe są generowane przez te same reguły, które są używane przez `strftime`, z ostatnim argumentem *_Pt*, do generowania serii elementów **char** w tablicy. Każdy taki element **char** jest założono, aby mapować do równoważnego elementu typu `CharType` przez proste mapowanie jeden do jednego. Jeśli *_Mod* jest równe zero, efektywnym formatem jest "% F", gdzie F jest zastępowany przez *_Fmt*. W przeciwnym razie obowiązuje format "% MF", gdzie M jest zastępowany przez *_Mod*.

### <a name="example"></a>Przykład

Zobacz przykład dla elementu [Put](#put), który wywołuje `do_put`.

## <a name="iter_type"></a>time_put::iter_type

Typ, który opisuje iterator danych wyjściowych.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `OutputIterator`.

## <a name="put"></a>time_put::p UT

Wyprowadza informacje o dacie i godzinie jako sekwencję `CharType`s.

```cpp
iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;

iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*następny* \
Iterator danych wyjściowych, w którym sekwencja znaków reprezentująca datę i godzinę ma zostać wstawiona.

*_Iosbase* \
Przestrzeń.

*_Fill* \
Znak typu `CharType` używany do odstępów.

*_Pt* \
Informacje o godzinie i dacie, które są wyprowadzane.

*_Fmt* \
Format danych wyjściowych. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l,](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać prawidłowe wartości.

*_Mod* \
Modyfikator dla formatu. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l,](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać prawidłowe wartości.

*pierwszy* \
Początek ciągu formatowania dla danych wyjściowych. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l,](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać prawidłowe wartości.

*ostatni* \
Koniec ciągu formatowania dla danych wyjściowych. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l,](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać prawidłowe wartości.

### <a name="return-value"></a>Wartość zwracana

Iterator do pierwszej pozycji po wstawieniu ostatniego elementu.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca [do_put](#do_put)(`next`, `_Iosbase`, `_Fill`, `_Pt`, `_Fmt`, `_Mod`). Druga funkcja członkowska jest kopiowana do \* `next` + + dowolnego elementu w interwale [`first`, `last`) innym niż procent (%). W przypadku wartości procentowej, po której następuje znak *C* w interwale [`first`, `last`), zamiast tego funkcja szacuje `next`  =  `do_put` (`next`, `_Iosbase`, `_Fill`, `_Pt`, *C*, 0) i pomija ostatnich *C*. Jeśli jednak *C* jest znakiem kwalifikatora z zestawu EOQ #, po którym następuje znak 3 w interwale [4, 5), zamiast tego funkcja szacuje 6 7 8 (9, 0 , 1, 2, 3, *C*) i pomija poprzednie 5.

### <a name="example"></a>Przykład

```cpp
// time_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   t.tm_hour = 5;
   t.tm_min = 30;
   t.tm_sec = 40;
   t.tm_year = 00;
   t.tm_mday = 4;
   t.tm_mon = 6;

   pszPutI.imbue( loc );
   char *pattern = "x: %X %x";
   use_facet <time_put <char> >
   (loc).put(basic_ostream<char>::_Iter(pszPutI.rdbuf( )),
          pszPutI, ' ', &t, pattern, pattern+strlen(pattern));

      cout << "num_put( ) = " << pszPutI.rdbuf( )->str( ) << endl;

      char strftimebuf[255];
      strftime(&strftimebuf[0], 255, pattern, &t);
      cout << "strftime( ) = " << &strftimebuf[0] << endl;
}
```

```Output
num_put( ) = x: 05:30:40 07/04/00
strftime( ) = x: 05:30:40 07/04/00
```

## <a name="time_put"></a>time_put::time_put

Konstruktor dla obiektów typu `time_put`.

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs* \
Wartość całkowita służąca do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie są następujące:

- 0: okres istnienia obiektu jest zarządzany przez elementy lokalne, które go zawierają.

- 1: okres istnienia obiektu musi być zarządzany ręcznie.

- \> 1: te wartości nie są zdefiniowane.

Konstruktor inicjuje swój obiekt podstawowy przy użyciu [ustawień regionalnych:: facet](../standard-library/locale-class.md#facet_class)( *_Refs*).

## <a name="see-also"></a>Zobacz także

[\<locale >](../standard-library/locale.md) \
[Klasa time_base](../standard-library/time-base-class.md) \
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
