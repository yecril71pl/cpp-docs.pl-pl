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
ms.openlocfilehash: 10691de0a583dc7d5a66c319968d90978bf59480
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367999"
---
# <a name="time_put-class"></a>time_put — Klasa

Szablon klasy opisuje obiekt, który może służyć jako aspekt ustawień regionalnych do `CharType`kontrolowania konwersji wartości czasu do sekwencji typu .

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ używany w programie do kodowania znaków.

*Dane wyjścioweIterator*\
Typ iteratora, do którego funkcje czasu put zapisują swoje dane wyjściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikatorze.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[time_put](#time_put)|Konstruktor obiektów typu `time_put`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wyjściowych.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[do_put](#do_put)|Funkcja wirtualna, która wyprowadza informacje o `CharType`czasie i dacie jako sekwencję s.|
|[Umieścić](#put)|Wyprowadza informacje o czasie i `CharType`dacie jako sekwencję s.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="time_putchar_type"></a><a name="char_type"></a>time_put::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `CharType`szablonu .

## <a name="time_putdo_put"></a><a name="do_put"></a>time_put::do_put

Funkcja wirtualna, która wyprowadza informacje o `CharType`czasie i dacie jako sekwencję s.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>Parametry

*Następnego*\
Iterator wyjściowy, w którym ma zostać wstawiona sekwencja znaków reprezentujących godzinę i datę.

*_Iosbase*\
Nieużywany.

*_Pt*\
Dane wyjściowe dotyczące godziny i daty.

*_Fmt*\
Format danych wyjściowych. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dla prawidłowych wartości.

*_Mod*\
Modyfikator formatu. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dla prawidłowych wartości.

### <a name="return-value"></a>Wartość zwracana

Iterator do pierwszej pozycji po wstawionym ostatnim elemencie.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnego chronionego elementu członkowskiego generuje kolejne `next` elementy zaczynające się \* `_Pt`od `tm`wartości czasu przechowywanych w obiekcie , typu . Funkcja zwraca iterator wyznaczający następne miejsce, aby wstawić element poza wygenerowane dane wyjściowe.

Dane wyjściowe są generowane przez `strftime`te same reguły używane przez , z ostatnim argumentem *_Pt*, do generowania serii elementów **char** do tablicy. Każdy **taki** char element zakłada się mapować `CharType` do równoważnego elementu typu przez proste, jeden do jednego mapowania. Jeśli *_Mod* równa się zero, formatem efektywnym jest "%F", gdzie F jest zastępowany *przez _Fmt*. W przeciwnym razie format efektywny to "%MF", gdzie M jest zastępowany *przez _Mod*.

### <a name="example"></a>Przykład

Zobacz przykład [put](#put), `do_put`który wywołuje .

## <a name="time_putiter_type"></a><a name="iter_type"></a>time_put::iter_type

Typ, który opisuje iterator danych wyjściowych.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `OutputIterator`szablonu .

## <a name="time_putput"></a><a name="put"></a>time_put::put

Wyprowadza informacje o czasie i `CharType`dacie jako sekwencję s.

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

*Następnego*\
Iterator wyjściowy, w którym ma zostać wstawiona sekwencja znaków reprezentujących godzinę i datę.

*_Iosbase*\
Nieużywany.

*_Fill*\
Znak typu `CharType` używanego do odstępów.

*_Pt*\
Dane wyjściowe dotyczące godziny i daty.

*_Fmt*\
Format danych wyjściowych. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dla prawidłowych wartości.

*_Mod*\
Modyfikator formatu. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dla prawidłowych wartości.

*Pierwszym*\
Początek ciągu formatowania dla danych wyjściowych. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dla prawidłowych wartości.

*Ostatnio*\
Koniec ciągu formatowania dla danych wyjściowych. Zobacz [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) dla prawidłowych wartości.

### <a name="return-value"></a>Wartość zwracana

Iterator do pierwszej pozycji po wstawionym ostatnim elemencie.

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu [do_put](#do_put)członkowskiego zwraca`next`do_put `_Iosbase` `_Fill`( `_Pt` `_Fmt`, `_Mod`, , , , , . Funkcja drugiego elementu członkowskiego \* `next` jest kopiowana do `first`++ dowolnego elementu w interwale [ , `last`) innego niż procent (%). Dla procentu, po którym następuje `first` `last`znak *C* w interwale `_Iosbase` `_Fill`[ `_Pt`, ), funkcja zamiast tego ocenia `next`  =  `do_put`( `next`, , , , *, C*, 0) i pomija przeszłości *C*. Jeśli jednak *C* jest znakiem kwalifikatora z zestawu EOQ#, `last`po którym następuje `next`  =  `do_put`znak `next` `C2` `_Iosbase`w `_Fill` `_Pt`interwale [ `first`,), funkcja zamiast tego ocenia ( , , , , `C2`, , , *C*) i pomija przemiebie `C2`.

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

## <a name="time_puttime_put"></a><a name="time_put"></a>time_put::time_put

Konstruktor obiektów `time_put`typu .

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_refs*\
Wartość całkowita używana do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie to:

- 0: Okres istnienia obiektu jest zarządzany przez ustawienia regionalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: Te wartości nie są zdefiniowane.

Konstruktor inicjuje swój obiekt bazowy za pomocą [ustawień regionalnych::facet](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="see-also"></a>Zobacz też

[\<>ustawień regionalnych](../standard-library/locale.md)\
[Klasa time_base](../standard-library/time-base-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
