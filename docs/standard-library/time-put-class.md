---
title: time_put — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
dev_langs:
- C++
helpviewer_keywords:
- std::time_put [C++]
- std::time_put [C++], char_type
- std::time_put [C++], iter_type
- std::time_put [C++], do_put
- std::time_put [C++], put
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fbd4cf162ba16ac5c9ae9c6bf018be2988507bcb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="timeput-class"></a>time_put — Klasa

Klasa szablonu opisuje obiekt, który może służyć jako zestaw reguł ustawienia regionalne do sterowania konwersji wartości czasu sekwencji typu `CharType`.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

`CharType` Typ używany w programie do kodowania znaków.

`OutputIterator` Typ iteratora, w której czas umieścić funkcji zapisywania ich danych wyjściowych.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba jej wartości przechowywanej dostępu są przechowywane w unikatową wartość dodatnią **identyfikator.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[time_put](#time_put)|Konstruktor dla obiektów typu `time_put`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wyjściowych.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[do_put](#do_put)|Funkcję wirtualną, która wyświetla datę i godzinę informacji jako sekwencja `CharType`s.|
|[put](#put)|Wyświetla datę i godzinę informacji jako sekwencja `CharType`s.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** Standard

## <a name="char_type"></a>  time_put::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType**.

## <a name="do_put"></a>  time_put::do_put

Funkcję wirtualną, która wyświetla datę i godzinę informacji jako sekwencja **CharType**s.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>Parametry

`next` Dane wyjściowe iteratora których sekwencja znaków reprezentująca datę i godzinę mają zostać wstawione.

`_Iosbase` Nieużywane.

`_Pt` Data i godzina informacje są dane wyjściowe.

`_Fmt` Format danych wyjściowych. Zobacz [strftime —, wcsftime —, _strftime_l —, _wcsftime_l —](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) prawidłowe wartości.

`_Mod` Modyfikator formatu. Zobacz [strftime —, wcsftime —, _strftime_l —, _wcsftime_l —](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) prawidłowe wartości.

### <a name="return-value"></a>Wartość zwracana

Iteratora na pierwszą pozycję po ostatnim elemencie wstawiony.

### <a name="remarks"></a>Uwagi

Funkcja wirtualnej chroniony element członkowski generuje elementy sekwencyjnych, zaczynając od `next` od wartości czasu przechowywane w obiekcie \* `_Pt`, typu **tm**. Funkcja zwraca iteratora wyznaczenie dalej miejsca do wstawienia elementu poza wygenerowanych danych wyjściowych.

Dane wyjściowe jest generowany przez te same reguły używane przez `strftime`, z ostatnim argumentem `_Pt`, generowania serii `char` elementów w tablicy. Każdy taki `char` element przyjęto, że do mapowania na równoważny element typu **CharType** mapowanie proste i jeden do jednego. Jeśli `_Mod` jest równa zero, skutecznego format to "%F", gdzie zastępuje F `_Fmt`. W przeciwnym razie skuteczne format to "% MF", gdzie zastępuje M `_Mod`.

### <a name="example"></a>Przykład

Zobacz przykład [put](#put), które wywołuje `do_put`.

## <a name="iter_type"></a>  time_put::iter_type

Typ, który opisuje iterator danych wyjściowych.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **OutputIterator**.

## <a name="put"></a>  time_put::Put

Wyświetla datę i godzinę informacji jako sekwencja **CharType**s.

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

`next` Dane wyjściowe iteratora których sekwencja znaków reprezentująca datę i godzinę mają zostać wstawione.

`_Iosbase` Nieużywane.

`_Fill` Znak typu **CharType** użytego do rozdzielenia.

`_Pt` Data i godzina informacje są dane wyjściowe.

`_Fmt` Format danych wyjściowych. Zobacz [strftime —, wcsftime —, _strftime_l —, _wcsftime_l —](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) prawidłowe wartości.

`_Mod` Modyfikator formatu. Zobacz [strftime —, wcsftime —, _strftime_l —, _wcsftime_l —](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) prawidłowe wartości.

`first` Na początku ciąg formatowania dla danych wyjściowych. Zobacz [strftime —, wcsftime —, _strftime_l —, _wcsftime_l —](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) prawidłowe wartości.

`last` Koniec ciągu formatowania dla danych wyjściowych. Zobacz [strftime —, wcsftime —, _strftime_l —, _wcsftime_l —](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) prawidłowe wartości.

### <a name="return-value"></a>Wartość zwracana

Iteratora na pierwszą pozycję po ostatnim elemencie wstawiony.

### <a name="remarks"></a>Uwagi

Zwraca pierwszy funkcji członkowskiej [do_put](#do_put)( `next`, `_Iosbase`, `_Fill`, `_Pt`, `_Fmt`, `_Mod`). Drugi funkcji członkowskiej kopiuje do \* `next` ++ dowolny element w interwale [ `first`, `last`) innych niż procentu (%). Dla %, a po niej znak *C* w interwale [ `first`, `last`), funkcja zamiast oblicza `next`  =  `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, *C*, 0) i pomija *C*. Jeśli, jednak *C* jest kwalifikator znak ze zbioru EOQ # następuje znak `C2` w interwale [ `first`, `last`), funkcja zamiast oblicza `next`  =  `do_put` ( `next`, `_Iosbase`, `_Fill`, `_Pt`, `C2`, *C*) i pomija `C2`.

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

## <a name="time_put"></a>  time_put::time_put

Konstruktor dla obiektów typu `time_put`.

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

`_Refs` Wartość całkowita używany do określania typu zarządzania pamięci dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości `_Refs` i ich znaczenie są:

- 0: okres istnienia obiektu zarządza ustawieniami regionalnymi, które zawierałoby proces.

- 1: okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: te wartości są niezdefiniowane.

Konstruktor inicjuje jego obiektu podstawowego z [locale::facet](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="see-also"></a>Zobacz także

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>
[time_base, klasa](../standard-library/time-base-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
