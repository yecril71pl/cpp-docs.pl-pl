---
title: codecvt — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocale/std::codecvt
- xlocale/std::codecvt::extern_type
- xlocale/std::codecvt::intern_type
- xlocale/std::codecvt::state_type
- xlocale/std::codecvt::always_noconv
- xlocale/std::codecvt::do_always_noconv
- xlocale/std::codecvt::do_encoding
- xlocale/std::codecvt::do_in
- xlocale/std::codecvt::do_length
- xlocale/std::codecvt::do_max_length
- xlocale/std::codecvt::do_out
- xlocale/std::codecvt::do_unshift
- xlocale/std::codecvt::encoding
- xlocale/std::codecvt::in
- xlocale/std::codecvt::length
- xlocale/std::codecvt::max_length
- xlocale/std::codecvt::out
- xlocale/std::codecvt::unshift
dev_langs:
- C++
helpviewer_keywords:
- std::codecvt [C++]
- std::codecvt [C++], extern_type
- std::codecvt [C++], intern_type
- std::codecvt [C++], state_type
- std::codecvt [C++], always_noconv
- std::codecvt [C++], do_always_noconv
- std::codecvt [C++], do_encoding
- std::codecvt [C++], do_in
- std::codecvt [C++], do_length
- std::codecvt [C++], do_max_length
- std::codecvt [C++], do_out
- std::codecvt [C++], do_unshift
- std::codecvt [C++], encoding
- std::codecvt [C++], in
- std::codecvt [C++], length
- std::codecvt [C++], max_length
- std::codecvt [C++], out
- std::codecvt [C++], unshift
ms.assetid: 37d3efa1-2b7f-42b6-b04f-7a972c8c2c86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f02f6a2810f5ac3a51abb80245c22a7f0c2df434
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074152"
---
# <a name="codecvt-class"></a>codecvt — Klasa

Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych. Jest w stanie kontrolować konwersje między sekwencją wartości używaną do kodowania znaków w ramach programu i sekwencją wartości używanych do kodowania znaków poza programem.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ używany w programie do kodowania znaków.

*Byte*<br/>
Typ używany do kodowania znaków poza programem.

*StateType*<br/>
Typ, który może służyć do reprezentowania pośrednich stanów konwersji między typami wewnętrznymi i zewnętrznymi reprezentacji znaków.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który może służyć jako [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class)w celu kontroli konwersji między sekwencjami wartości typu *CharType* i sekwencjami wartości typu *bajtów*. Klasa *StateType* charakteryzuje transformację--i obiekt klasy *StateType* przechowuje wszystkie niezbędne informacje o stanie podczas konwersji.

Wewnętrzne kodowanie wykorzystuje reprezentację z stałą liczbą bajtów na znak, zwykle albo typu **char** lub typ **wchar_t**.

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych obiektu statycznego `id` ma początkową przechowywaną wartość zero. Pierwsza próba dostępu do jego przechowywanej wartości przechowuje unikatową wartość dodatnią w `id`.

Wersje szablonów z [do_in](#do_in) i [do_out](#do_out) zawsze zwracają `codecvt_base::noconv`.

Standardowa biblioteka C++ definiuje kilka jawnych specjalizacji:

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

wykonuje konwersję między **wchar_t** i **char** sekwencji.

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

wykonuje konwersję między `char16_t` zakodowanymi w formacie UTF-16 i **char** zakodowanymi w formacie UTF-8.

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

wykonuje konwersję między `char32_t` zakodowanymi w formacie UTF-32 (UCS-4) i **char** zakodowanymi w formacie UTF-8.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[codecvt](#codecvt)|Konstruktor dla obiektów klasy `codecvt` służy jako zestaw reguł ustawień regionalnych do obsługi konwersji.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[extern_type](#extern_type)|Typ znaku, który jest używany dla zewnętrznych reprezentacji.|
|[intern_type](#intern_type)|Typ znaku, który jest używany dla wewnętrznych reprezentacji.|
|[state_type](#state_type)|Typ znaku, który jest używany do reprezentowania pośrednich stanów w czasie konwersji między wewnętrznymi i zewnętrznymi reprezentacjami.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[always_noconv](#always_noconv)|Sprawdza, czy nie trzeba wykonać żadnych konwersji.|
|[do_always_noconv](#do_always_noconv)|Funkcja wirtualna wywoływana w celu sprawdzenia, czy nie trzeba wykonywać żadnych konwersji.|
|[do_encoding](#do_encoding)|Funkcja wirtualna, która sprawdza, czy kodowanie `Byte` strumień jest zależy od stanu, czy stosunek między używanymi `Byte`używane i `CharType`produkowanymi jest stały i jeśli tak, określa wartość tego stosunku.|
|[do_in](#do_in)|Funkcja wirtualna wywoływana w celu konwersji sekwencji wewnętrznych `Byte`na sekwencję zewnętrznych `CharType`s.|
|[do_length](#do_length)|Funkcja wirtualna, która określa, ile `Byte`s z danej sekwencji zewnętrznych `Byte`produkuje nie więcej niż określoną liczbę wewnętrznych `CharType`s i zwraca tę liczbę `Byte`s.|
|[do_max_length](#do_max_length)|Funkcja wirtualna, która zwraca maksymalną liczbę zewnętrznych Byte niezbędnych do wyprodukowania jednego wewnętrznego `CharType`.|
|[do_out](#do_out)|Funkcja wirtualna wywoływana w celu konwersji sekwencji wewnętrznych `CharType`na sekwencję zewnętrznych Byte.|
|[do_unshift](#do_unshift)|Funkcja wirtualna wywoływana w celu zapewnienia `Byte`potrzebnych podczas konwersji zależnej od stanu, aby zakończyć ostatni znak w sekwencji `Byte`s.|
|[Kodowanie](#encoding)|Sprawdza, czy kodowanie `Byte` strumień jest zależy od stanu, czy stosunek między używanymi `Byte`używane i `CharType`produkowanymi jest stały i jeśli tak, określa wartość tego stosunku.|
|[in](#in)|Konwertuje zewnętrzną reprezentację sekwencji `Byte`s do wewnętrznej reprezentacji sekwencji `CharType`s.|
|[Długość](#length)|Określa, ile `Byte`s z danej sekwencji zewnętrznych `Byte`produkuje nie więcej niż określoną liczbę wewnętrznych `CharType`s i zwraca tę liczbę `Byte`s.|
|[MAX_LENGTH](#max_length)|Zwraca maksymalną liczbę zewnętrznych `Byte`niezbędnych do wyprodukowania jednego wewnętrznego `CharType`.|
|[out](#out)|Konwertuje sekwencję wewnętrznych `CharType`na sekwencję zewnętrznych `Byte`s.|
|[unshift](#unshift)|Zapewnia zewnętrzne `Byte`potrzebnych podczas konwersji zależnej od stanu, aby zakończyć ostatni znak w sekwencji `Byte`s.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="always_noconv"></a>  codecvt::always_noconv

Sprawdza, czy nie trzeba wykonać żadnych konwersji.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna, która jest **true** przypadku nie trzeba wykonywać żadnych konwersji; **false** jest co najmniej jeden musi odbywać się.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_always_noconv —](#do_always_noconv).

### <a name="example"></a>Przykład

```cpp
// codecvt_always_noconv.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = use_facet<codecvt<char, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result1 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;

   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result2 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;
}
```

```Output
No conversion is needed.
At least one conversion is required.
```

## <a name="codecvt"></a>  codecvt::codecvt

Konstruktor dla obiektów klasy codecvt, która służy jako zestaw reguł ustawień regionalnych do obsługi konwersji.

```cpp
explicit codecvt(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*<br/>
Wartość liczby całkowitej, można określić typ zarządzania pamięci dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* parametrów i ich znaczenie są:

- 0: okres istnienia obiektu jest zarządzany przez ustawienia regionalne, zawierających go.

- 1: okres istnienia obiektu musi być zarządzane ręcznie.

- 2: nie zdefiniowano tych wartości.

Konstruktor inicjuje jego `locale::facet` podstawowego obiektu z **locale::**[aspekt](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="do_always_noconv"></a>  codecvt::do_always_noconv

Funkcja wirtualna wywoływana w celu sprawdzenia, czy nie trzeba wykonywać żadnych konwersji.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja chronionych wirtualna elementu członkowskiego zwraca **true** tylko wtedy, gdy każde wywołanie [do_in](#do_in) lub [do_out](#do_out) zwraca `noconv`.

Wersja szablonu zawsze zwraca **true**.

### <a name="example"></a>Przykład

Zobacz przykład [always_noconv —](#always_noconv), która wywołuje metodę `do_always_noconv`.

## <a name="do_encoding"></a>  codecvt::do_encoding

Funkcja wirtualna, która sprawdza, czy kodowanie `Byte` strumień jest zależy od stanu, czy stosunek między używanymi `Byte`używane i `CharType`produkowanymi jest stały i jeśli tak, określa wartość tego stosunku.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja chronionych wirtualna elementu członkowskiego zwraca:

- -1, jeśli kodowanie sekwencji typu `extern_type` zależy od stanu.

- 0, jeśli kodowanie obejmuje sekwencje różnych długości.

- *N*, jeśli kodowanie obejmuje tylko sekwencje długości *N*

### <a name="example"></a>Przykład

Zobacz przykład [kodowanie](#encoding), która wywołuje metodę `do_encoding`.

## <a name="do_in"></a>  codecvt::do_in

Funkcja wirtualna wywoływana w celu konwersji sekwencji zewnętrznych `Byte`sekwencję wewnętrznych `CharType`s.

```cpp
virtual result do_in(
    StateType& _State,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parametry

*_Stanu*<br/>
Stan konwersji, który jest zachowywane między wywołaniami funkcji elementu członkowskiego.

*first1*<br/>
Wskaźnik na początku sekwencji, który ma zostać przekonwertowany.

*Nazwisko1*<br/>
Wskaźnik końca sekwencji, który ma zostać przekonwertowany.

*next1*<br/>
Wskaźnik poza końcem przekonwertowany sekwencji do pierwszego znaku nieprzekonwertowane.

*first2*<br/>
Wskaźnik do początku przekonwertowany sekwencji.

*Nazwisko2*<br/>
Wskaźnik końca sekwencji przekonwertowana.

*next2*<br/>
Wskaźnik do `CharType` dostarczany po przekonwertowaniu ostatniego `CharType`, do niezmienionym pierwszego znaku w sekwencji docelowej.

### <a name="return-value"></a>Wartość zwracana

Return, która wskazuje Powodzenie, częściowe powodzenie lub Niepowodzenie operacji. Funkcja zwraca:

- `codecvt_base::error` Jeśli sekwencja źródłowa jest ill sformułowana.

- `codecvt_base::noconv` Jeśli funkcja nie wykonuje żadnych konwersji.

- `codecvt_base::ok` Jeśli konwersja powiedzie się.

- `codecvt_base::partial` Jeśli źródło jest za mało lub element docelowy nie jest wystarczający, aby konwersja się powiodła się.

### <a name="remarks"></a>Uwagi

*_Stanu* musi reprezentować stan początkowy konwersji na początku nowego sekwencji źródłowej. Funkcja zmienia jego przechowywanej wartości zgodnie z potrzebami, aby odzwierciedlić bieżący stan przekształcenia pomyślne. Jego przechowywanej wartości, w przeciwnym razie jest nieokreślona.

### <a name="example"></a>Przykład

Zobacz przykład [w](#in), która wywołuje metodę `do_in`.

## <a name="do_length"></a>  codecvt::do_length

Funkcja wirtualna, która określa, ile `Byte`s z danej sekwencji zewnętrznych `Byte`produkuje nie więcej niż określoną liczbę wewnętrznych `CharType`s i zwraca tę liczbę `Byte`s.

```cpp
virtual int do_length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>Parametry

*_Stanu*<br/>
Stan konwersji, który jest zachowywane między wywołaniami funkcji elementu członkowskiego.

*first1*<br/>
Wskaźnik na początku sekwencji zewnętrznych.

*Nazwisko1*<br/>
Wskaźnik końca sekwencji zewnętrznych.

*_Len2*<br/>
Maksymalna liczba `Byte`s, który może zostać zwrócony przez funkcję elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która reprezentuje liczbę maksymalną liczbę konwersje nie większą niż *_Len2*, zdefiniowany przez sekwencję zewnętrznego źródła, w [ `first1`, `last1`).

### <a name="remarks"></a>Uwagi

Skutecznie wywołuje chroniony wirtualna funkcja składowa `do_in`( `_State`, `first1`, `last1`, `next1`, `_Buf`, `_Buf`  +  `_Len2`, `next2`) dla *_Stanu* (kopia stanie), niektóre buforu `_Buf`i wskaźniki `next1`i `next2`.

Następnie zwraca `next2`  -  `buf`. Tak więc liczy konwersji, nie jest większa niż maksymalna liczba *_Len2*, zdefiniowany przez sekwencję źródłową na [ `first1`, `last1`).

Wersja szablonu zawsze zwraca mniejszy z *Nazwisko1* - *first1* i *_Len2*.

### <a name="example"></a>Przykład

Zobacz przykład [długość](#length), która wywołuje metodę `do_length`.

## <a name="do_max_length"></a>  codecvt::do_max_length

Funkcja wirtualna, która zwraca maksymalną liczbę zewnętrznych `Byte`niezbędnych do wyprodukowania jednego wewnętrznego `CharType`.

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba `Byte`niezbędnych do wyprodukowania jednego `CharType`.

### <a name="remarks"></a>Uwagi

Funkcja chronionych wirtualna elementu członkowskiego zwraca największą wartość dopuszczalną wartość, która może zostać zwrócony przez [do_length —](#do_length)( `first1`, `last1`, 1) dla dowolnego prawidłowe wartości *first1* i *Nazwisko1*.

### <a name="example"></a>Przykład

Zobacz przykład [max_length](#max_length), która wywołuje metodę `do_max_length`.

## <a name="do_out"></a>  codecvt::do_out

Funkcja wirtualna wywoływana w celu konwersji sekwencji wewnętrznych `CharType`na sekwencję zewnętrznych `Byte`s.

```cpp
virtual result do_out(
    StateType& _State,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_Stanu*<br/>
Stan konwersji, który jest zachowywane między wywołaniami funkcji elementu członkowskiego.

*first1*<br/>
Wskaźnik na początku sekwencji, który ma zostać przekonwertowany.

*Nazwisko1*<br/>
Wskaźnik końca sekwencji, który ma zostać przekonwertowany.

*next1*<br/>
Odwołanie do wskaźnika do pierwszego nieprzekonwertowany `CharType`, po ostatnim `CharType` konwertowane.

*first2*<br/>
Wskaźnik do początku przekonwertowany sekwencji.

*Nazwisko2*<br/>
Wskaźnik końca sekwencji przekonwertowana.

*next2*<br/>
Odwołanie do wskaźnika do pierwszego nieprzekonwertowany `Byte`, po ostatnim `Byte` konwertowane.

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca:

- `codecvt_base::error` Jeśli sekwencja źródłowa jest ill sformułowana.

- `codecvt_base::noconv` Jeśli funkcja nie wykonuje żadnych konwersji.

- `codecvt_base::ok` Jeśli konwersja powiedzie się.

- `codecvt_base::partial` Jeśli źródło jest za mało lub miejsce docelowe nie jest wystarczająco duży, aby konwersja się powiodła się.

### <a name="remarks"></a>Uwagi

*_Stanu* musi reprezentować stan początkowy konwersji na początku nowego sekwencji źródłowej. Funkcja zmienia jego przechowywanej wartości zgodnie z potrzebami, aby odzwierciedlić bieżący stan przekształcenia pomyślne. Jego przechowywanej wartości, w przeciwnym razie jest nieokreślona.

### <a name="example"></a>Przykład

Zobacz przykład [się](#out), która wywołuje metodę `do_out`.

## <a name="do_unshift"></a>  codecvt::do_unshift

Funkcja wirtualna wywoływana w celu zapewnienia `Byte`potrzebnych podczas konwersji zależnej od stanu, aby zakończyć ostatni znak w sekwencji `Byte`s.

```cpp
virtual result do_unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_Stanu*<br/>
Stan konwersji, który jest zachowywane między wywołaniami funkcji elementu członkowskiego.

*first2*<br/>
Wskaźnik do pierwszego pozycji w zakresie docelowym.

*Nazwisko2*<br/>
Wskaźnik do ostatniej pozycji w zakresie docelowym.

*next2*<br/>
Wskaźnik do pierwszego elementu niezmienione w sekwencji docelowej.

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca:

- `codecvt_base::error` Jeśli _ *stanu* reprezentuje nieprawidłowy stan

- `codecvt_base::noconv` Jeśli funkcja wykonuje bez konwersji

- `codecvt_base::ok` Jeśli konwersja zakończy się powodzeniem.

- `codecvt_base::partial` Jeśli miejsce docelowe nie jest wystarczająco duży, aby konwersja się powiodła się

### <a name="remarks"></a>Uwagi

Chronione wirtualna funkcja składowa podejmuje próbę przekonwertowania elementu źródłowego `CharType`(0) do sekwencji docelowej, która jest przechowywana w [ `first2`, `last2`), z wyjątkiem kończącego elementu `Byte`(0). Zawsze są przechowywane w *next2* wskaźnik do pierwszego elementu niezmienione w sekwencji docelowej.

_ *Stanu* musi reprezentować stan początkowy konwersji na początku nowego sekwencji źródłowej. Funkcja zmienia jego przechowywanej wartości zgodnie z potrzebami, aby odzwierciedlić bieżący stan przekształcenia pomyślne. Zazwyczaj Konwertowanie elementu źródłowego `CharType`(0) pozostawia bieżącego stanu w stanie początkowej konwersji.

### <a name="example"></a>Przykład

Zobacz przykład [unshift](#unshift), która wywołuje metodę `do_unshift`.

## <a name="encoding"></a>  codecvt::Encoding

Sprawdza, czy kodowanie `Byte` strumień jest zależy od stanu, czy stosunek między używanymi `Byte`używane i `CharType`produkowanymi jest stały i jeśli tak, określa wartość tego stosunku.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli zwracana jest wartość dodatnią, wówczas ta wartość jest stała liczba `Byte` znaków wymaganych do utworzenia `CharType` znaków.

Funkcja chronionych wirtualna elementu członkowskiego zwraca:

- -1, jeśli kodowanie sekwencji typu `extern_type` zależy od stanu.

- 0, jeśli kodowanie obejmuje sekwencje różnych długości.

- *N*, jeśli kodowanie obejmuje tylko sekwencje długości *N.*

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_encoding —](#do_encoding).

### <a name="example"></a>Przykład

```cpp
// codecvt_encoding.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   int result1 = use_facet<codecvt<char, char, mbstate_t> > ( loc ).encoding ( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
}
```

```Output
1
1
1
```

## <a name="extern_type"></a>  codecvt::extern_type

Typ znaku, który jest używany dla zewnętrznych reprezentacji.

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Byte`.

## <a name="in"></a>  codecvt::in

Konwertuje zewnętrzną reprezentację sekwencji `Byte`s do wewnętrznej reprezentacji sekwencji `CharType`s.

```cpp
result in(
    StateType& _State,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parametry

*_Stanu*<br/>
Stan konwersji, który jest zachowywane między wywołaniami funkcji elementu członkowskiego.

*first1*<br/>
Wskaźnik na początku sekwencji, który ma zostać przekonwertowany.

*Nazwisko1*<br/>
Wskaźnik końca sekwencji, który ma zostać przekonwertowany.

*next1*<br/>
Wskaźnik poza końcem sekwencji przekonwertowany do pierwszego znaku nieprzekonwertowane.

*first2*<br/>
Wskaźnik do początku przekonwertowany sekwencji.

*Nazwisko2*<br/>
Wskaźnik końca sekwencji przekonwertowana.

*next2*<br/>
Wskaźnik do `CharType` dostarczany po przekonwertowaniu ostatniego `Chartype` do niezmienionym pierwszego znaku w sekwencji docelowej.

### <a name="return-value"></a>Wartość zwracana

Return, która wskazuje Powodzenie, częściowe powodzenie lub Niepowodzenie operacji. Funkcja zwraca:

- `codecvt_base::error` Jeśli sekwencja źródłowa jest ill sformułowana.

- `codecvt_base::noconv` Jeśli funkcja nie wykonuje żadnych konwersji.

- `codecvt_base::ok` Jeśli konwersja powiedzie się.

- `codecvt_base::partial` Jeśli źródło jest za mało lub miejsce docelowe nie jest wystarczająco duży, aby konwersja się powiodła się.

### <a name="remarks"></a>Uwagi

*_Stanu* musi reprezentować stan początkowy konwersji na początku nowego sekwencji źródłowej. Funkcja zmienia jego przechowywanej wartości zgodnie z potrzebami, aby odzwierciedlić bieżący stan przekształcenia pomyślne. Po częściowej konwersji *_stanu* musi być ustawiona tak, aby umożliwić konwersji wznowić działanie po nadejściu nowych znaków.

Funkcja elementu członkowskiego zwraca [do_in](#do_in)( `_State`, _ *First1, Nazwisko1, next1, First2, _Llast2, next2*).

### <a name="example"></a>Przykład

```cpp
// codecvt_in.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));
   const char* pszNext;
   wchar_t* pwszNext;
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).in( state,
          pszExt, &pszExt[strlen(pszExt)], pszNext,
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error)  L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;
   exit(-1);
}
```

```Output
It worked! The converted string is:
[This is the string to be converted!]
```

## <a name="intern_type"></a>  codecvt::intern_type

Typ znaku, który jest używany dla wewnętrznych reprezentacji.

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `CharType`.

## <a name="length"></a>  codecvt::length

Określa, ile `Byte`s z danej sekwencji zewnętrznych `Byte`produkuje nie więcej niż określoną liczbę wewnętrznych `CharType`s i zwraca tę liczbę `Byte`s.

```cpp
int length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>Parametry

*_Stanu*<br/>
Stan konwersji, który jest zachowywane między wywołaniami funkcji elementu członkowskiego.

*first1*<br/>
Wskaźnik na początku sekwencji zewnętrznych.

*Nazwisko1*<br/>
Wskaźnik końca sekwencji zewnętrznych.

*_Len2*<br/>
Maksymalna liczba bajtów, które mogą być zwracane przez funkcję elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która reprezentuje liczbę maksymalną liczbę konwersje nie większą niż *_Len2*, zdefiniowany przez sekwencję zewnętrznego źródła, w [ `first1`, `last1`).

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_length —](#do_length)( *_stanu, first1*, `last1`, `_Len2`).

### <a name="example"></a>Przykład

```cpp
// codecvt_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   char* pszExt = "This is the string whose length is to be measured!";
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).length( state,
          pszExt, &pszExt[strlen(pszExt)], LEN );
   cout << "The length of the string is: ";
   wcout << res;
   cout << "." << endl;
   exit(-1);
}
```

```Output
The length of the string is: 50.
```

## <a name="max_length"></a>  codecvt::MAX_LENGTH

Zwraca maksymalną liczbę zewnętrznych `Byte`niezbędnych do wyprodukowania jednego wewnętrznego `CharType`.

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba `Byte`niezbędnych do wyprodukowania jednego `CharType`.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_max_length —](#do_max_length).

### <a name="example"></a>Przykład

```cpp
// codecvt_max_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc( "C");//English_Britain" );//German_Germany
   int res = use_facet<codecvt<char, char, mbstate_t> >
     ( loc ).max_length( );
   wcout << res << endl;
}
```

```Output
1
```

## <a name="out"></a>  codecvt::Out

Konwertuje sekwencję wewnętrznych `CharType`na sekwencję zewnętrznych `Byte`s.

```cpp
result out(
    StateType& _State,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_Stanu*<br/>
Stan konwersji, który jest zachowywane między wywołaniami funkcji elementu członkowskiego.

*first1*<br/>
Wskaźnik na początku sekwencji, który ma zostać przekonwertowany.

*Nazwisko1*<br/>
Wskaźnik końca sekwencji, który ma zostać przekonwertowany.

*next1*<br/>
Odwołanie do wskaźnika do pierwszego nieprzekonwertowany `CharType` po ostatnim `CharType` konwertowane.

*first2*<br/>
Wskaźnik do początku przekonwertowany sekwencji.

*Nazwisko2*<br/>
Wskaźnik końca sekwencji przekonwertowana.

*next2*<br/>
Odwołanie do wskaźnika do pierwszego nieprzekonwertowany `Byte` po przekonwertowaniu ostatniego `Byte`.

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca [do_out](#do_out)( `_State`, `first1`, `last1`, `next1`, `first2`, `last2`, `next2`).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [codecvt::do_out](#do_out).

### <a name="example"></a>Przykład

```cpp
// codecvt_out.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
#include <wchar.h>
using namespace std;
#define LEN 90
int main( )
{
   char pszExt[LEN+1];
   wchar_t *pwszInt = L"This is the wchar_t string to be converted.";
   memset( &pszExt[0], 0, ( sizeof( char ) )*( LEN+1 ) );
   char* pszNext;
   const wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).out( state,
      pwszInt, &pwszInt[wcslen( pwszInt )], pwszNext ,
      pszExt, &pszExt[wcslen( pwszInt )], pszNext );
   pszExt[wcslen( pwszInt )] = 0;
   cout << ( ( res!=codecvt_base::error )  "It worked: " : "It didn't work: " )
   << "The converted string is:\n ["
   << &pszExt[0]
   << "]" << endl;
}
```

```Output
It worked: The converted string is:
[This is the wchar_t string to be converted.]
```

## <a name="state_type"></a>  codecvt::state_type

Typ znaku, który jest używany do reprezentowania pośrednich stanów w czasie konwersji między wewnętrznymi i zewnętrznymi reprezentacjami.

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `StateType`.

## <a name="unshift"></a>  codecvt::unshift

Udostępnia `Byte`potrzebnych podczas konwersji zależnej od stanu, aby zakończyć ostatni znak w sekwencji `Byte`s.

```cpp
result unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_Stanu*<br/>
Stan konwersji, który jest zachowywane między wywołaniami funkcji elementu członkowskiego.

*first2*<br/>
Wskaźnik do pierwszego pozycji w zakresie docelowym.

*Nazwisko2*<br/>
Wskaźnik do ostatniej pozycji w zakresie docelowym.

*next2*<br/>
Wskaźnik do pierwszego elementu niezmienione w sekwencji docelowej.

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca:

- `codecvt_base::error` Jeśli stan reprezentuje nieprawidłowym stanie.

- `codecvt_base::noconv` Jeśli funkcja nie wykonuje żadnych konwersji.

- `codecvt_base::ok` Jeśli konwersja powiedzie się.

- `codecvt_base::partial` Jeśli miejsce docelowe nie jest wystarczająco duży dla konwersja powiodła się.

### <a name="remarks"></a>Uwagi

Chronione wirtualna funkcja składowa podejmuje próbę przekonwertowania elementu źródłowego `CharType`(0) do sekwencji docelowej, która jest przechowywana w [ `first2`, `last2`), z wyjątkiem kończącego elementu `Byte`(0). Zawsze są przechowywane w *next2* wskaźnik do pierwszego elementu niezmienione w sekwencji docelowej.

*_Stanu* musi reprezentować stan początkowy konwersji na początku nowego sekwencji źródłowej. Funkcja zmienia jego przechowywanej wartości zgodnie z potrzebami, aby odzwierciedlić bieżący stan przekształcenia pomyślne. Zazwyczaj Konwertowanie elementu źródłowego `CharType`(0) pozostawia bieżącego stanu w stanie początkowej konwersji.

Funkcja elementu członkowskiego zwraca [do_unshift —](#do_unshift)( `_State`, `first2`, `last2`, `next2` ).

## <a name="see-also"></a>Zobacz także

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>
[Strony kodowe](../c-runtime-library/code-pages.md)<br/>
[Nazwy lokalne, języki i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
