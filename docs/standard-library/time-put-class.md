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
ms.openlocfilehash: 4f7b609493e16d3d1c0a9ab6274ed6f5bfd7b033
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212114"
---
# <a name="time_put-class"></a>time_put — Klasa

Szablon klasy opisuje obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu kontrolowania konwersji wartości czasu na sekwencje typu `CharType` .

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ używany w programie do kodowania znaków.

*OutputIterator*\
Typ iteratora, do którego funkcje czasu put zapisują swoje dane wyjściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[time_put](#time_put)|Konstruktor dla obiektów typu `time_put` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wyjściowych.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[do_put](#do_put)|Funkcja wirtualna, która wyprowadza informacje o dacie i godzinie jako sekwencję `CharType` s.|
|[Ubrani](#put)|Wyprowadza informacje o dacie i godzinie jako sekwencję `CharType` s.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<locale>

**Przestrzeń nazw:** std

## <a name="time_putchar_type"></a><a name="char_type"></a>time_put:: char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `CharType` .

## <a name="time_putdo_put"></a><a name="do_put"></a>time_put::d o_put

Funkcja wirtualna, która wyprowadza informacje o dacie i godzinie jako sekwencję `CharType` s.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>Parametry

*ponown*\
Iterator danych wyjściowych, w którym sekwencja znaków reprezentująca datę i godzinę ma zostać wstawiona.

*_Iosbase*\
Nieużywany.

*_Pt*\
Informacje o godzinie i dacie, które są wyprowadzane.

*_Fmt*\
Format danych wyjściowych. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l,](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać prawidłowe wartości.

*_Mod*\
Modyfikator dla formatu. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l,](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać prawidłowe wartości.

### <a name="return-value"></a>Wartość zwracana

Iterator do pierwszej pozycji po wstawieniu ostatniego elementu.

### <a name="remarks"></a>Uwagi

Wirtualna funkcja chroniona składowa generuje elementy sekwencyjne zaczynające się `next` od wartości czasu, które są przechowywane w obiekcie \* `_Pt` typu `tm` . Funkcja zwraca iterator wyznaczający następne miejsce do wstawienia elementu poza wygenerowanymi danymi wyjściowymi.

Dane wyjściowe są generowane przez te same reguły, które są używane przez `strftime` , z ostatnim argumentem *_Pt*, do generowania serii **`char`** elementów w tablicy. Każdy taki **`char`** element jest założono, że mapuje do równoważnego elementu typu `CharType` przez proste, jedno-do-jednego mapowania. Jeśli *_Mod* jest równe zero, efektywnym formatem jest "% F", gdzie F jest zastępowany przez *_Fmt*. W przeciwnym razie obowiązuje format "% MF", gdzie M jest zastępowany przez *_Mod*.

### <a name="example"></a>Przykład

Zobacz przykład [umieszczania](#put)wywołań `do_put` .

## <a name="time_putiter_type"></a><a name="iter_type"></a>time_put:: iter_type

Typ, który opisuje iterator danych wyjściowych.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `OutputIterator` .

## <a name="time_putput"></a><a name="put"></a>time_put::p UT

Wyprowadza informacje o dacie i godzinie jako sekwencję `CharType` s.

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

*ponown*\
Iterator danych wyjściowych, w którym sekwencja znaków reprezentująca datę i godzinę ma zostać wstawiona.

*_Iosbase*\
Nieużywany.

*_Fill*\
Znak typu `CharType` używany do odstępów.

*_Pt*\
Informacje o godzinie i dacie, które są wyprowadzane.

*_Fmt*\
Format danych wyjściowych. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l,](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać prawidłowe wartości.

*_Mod*\
Modyfikator dla formatu. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l,](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać prawidłowe wartości.

*pierwszego*\
Początek ciągu formatowania dla danych wyjściowych. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l,](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać prawidłowe wartości.

*ostatniego*\
Koniec ciągu formatowania dla danych wyjściowych. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l,](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Aby uzyskać prawidłowe wartości.

### <a name="return-value"></a>Wartość zwracana

Iterator do pierwszej pozycji po wstawieniu ostatniego elementu.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca [do_put](#do_put)( `next` , `_Iosbase` ,,, `_Fill` `_Pt` `_Fmt` , `_Mod` ). Druga funkcja członkowska jest kopiowana do \* `next` + + dowolnego elementu w interwale [ `first` , `last` ) innym niż procent (%). Dla procentu, po którym następuje znak *C* w interwale [ `first` , `last` ), zamiast tego funkcja oblicza wartość `next`  =  `do_put` ( `next` ,,,, `_Iosbase` `_Fill` `_Pt` *C*, 0) i pomija ostatnich *C*. Jeśli jednak *C* jest znakiem kwalifikatora z zestawu EOQ #, po którym następuje znak `C2` w interwale [ `first` , `last` ), funkcja zamiast oblicza wartość `next`  =  `do_put` ( `next` ,,,, `_Iosbase` `_Fill` `_Pt` `C2` , *C*) i pomija poprzednie `C2` .

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

## <a name="time_puttime_put"></a><a name="time_put"></a>time_put:: time_put

Konstruktor dla obiektów typu `time_put` .

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Wartość całkowita służąca do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie są następujące:

- 0: okres istnienia obiektu jest zarządzany przez elementy lokalne, które go zawierają.

- 1: okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: te wartości nie są zdefiniowane.

Konstruktor inicjuje swój obiekt podstawowy przy użyciu [ustawień regionalnych:: facet](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="see-also"></a>Zobacz także

[\<locale>](../standard-library/locale.md)\
[Klasa time_base](../standard-library/time-base-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
