---
title: codecvt — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8b430e93ba0e60986f37f16d0da172b845ad593
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="codecvt-class"></a>codecvt — Klasa

Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych. Jest w stanie kontrolować konwersje między sekwencją wartości używaną do kodowania znaków w ramach programu i sekwencją wartości używanych do kodowania znaków poza programem.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Parametry

`CharType` Typ używany w programie do kodowania znaków.

`Byte` Typ używany do kodowania znaków spoza programu.

`StateType` Typ, który może służyć do reprezentowania pośrednich stanów konwersji między typami wewnętrznych i zewnętrznych reprezentacje znaków.

## <a name="remarks"></a>Uwagi

Obiekt, który może służyć jako opis klasy szablonu [aspektu ustawień regionalnych](../standard-library/locale-class.md#facet_class), aby kontrolować konwersje między sekwencję wartości typu `CharType` i sekwencję wartości typu `Byte`. Klasa `StateType` charakteryzuje transformacja--i obiekt klasy `StateType` przechowuje żadnych informacji o stanie niezbędne podczas konwersji.

Wewnętrzny kodowanie używa reprezentację o stałą liczbę bajtów na znak, zwykle wpisz `char` lub typ `wchar_t`.

W przypadku dowolnego aspektu ustawień regionalnych, obiektu statycznego `id` początkowego przechowywanych wartości zero. Pierwsza próba jej wartości przechowywanej dostępu są przechowywane w unikatową wartość dodatnią `id`.

Wersje szablonu [do_in](#do_in) i [do_out](#do_out) zawsze zwraca `codecvt_base::noconv`.

Standardowa biblioteka C++ definiuje kilka jawne specjalizacje:

`template<>`

`codecvt<wchar_t, char, mbstate_t>`

wykonuje konwersję między `wchar_t` i `char` sekwencji.

`template<>`

`codecvt<char16_t, char, mbstate_t>`

wykonuje konwersję między `char16_t` sekwencji został zakodowany jako UTF-16 i `char` sekwencji został zakodowany jako UTF-8.

`template<>`

`codecvt<char32_t, char, mbstate_t>`

wykonuje konwersję między `char32_t` sekwencji został zakodowany jako UTF-32 (UCS-4) i `char` sekwencji został zakodowany jako UTF-8.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[codecvt](#codecvt)|Konstruktor dla obiektów klasy `codecvt` służy jako zestaw reguł ustawienia regionalne do obsługi konwersji.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[extern_type](#extern_type)|Typ znaku, który jest używany dla zewnętrznych reprezentacji.|
|[intern_type](#intern_type)|Typ znaku, który jest używany dla wewnętrznych reprezentacji.|
|[state_type](#state_type)|Typ znaku, który jest używany do reprezentowania pośrednich stanów w czasie konwersji między wewnętrznymi i zewnętrznymi reprezentacjami.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[always_noconv](#always_noconv)|Sprawdza, czy nie trzeba wykonać żadnych konwersji.|
|[do_always_noconv](#do_always_noconv)|Funkcja wirtualna wywoływana w celu sprawdzenia, czy nie trzeba wykonywać żadnych konwersji.|
|[do_encoding](#do_encoding)|Funkcja wirtualnego, który umożliwia sprawdzenie, czy kodowanie `Byte` strumień jest stan zależnych, czy stosunek `Byte`s używane i `CharType`s tworzone jest stałe i, jeśli tak, określa wartość tego stosunku.|
|[do_in](#do_in)|Funkcję wirtualną o nazwie przekonwertować sekwencji wewnętrznej `Byte`s z zewnętrznego sekwencji `CharType`s.|
|[do_length](#do_length)|Funkcji wirtualnej, który określa, ile `Byte`s z danej sekwencji zewnętrzne `Byte`produktu s nie więcej niż podany numer wewnętrzny `CharType`s i zwraca ten numer `Byte`s.|
|[do_max_length](#do_max_length)|Wirtualny funkcja, która zwraca maksymalną liczbę bajtów zewnętrznego należy utworzyć jeden wewnętrzny `CharType`.|
|[do_out](#do_out)|Funkcję wirtualną o nazwie przekonwertować sekwencji wewnętrznej `CharType`s do sekwencji bajtów zewnętrznych.|
|[do_unshift](#do_unshift)|Wywołuje funkcję wirtualną zapewnienie `Byte`s wymagane podczas konwersji zależny od stanu do ukończenia ostatni znak w sekwencji `Byte`s.|
|[Kodowanie](#encoding)|Sprawdza, czy kodowanie `Byte` strumień jest stan zależnych, czy stosunek `Byte`s używane i `CharType`s tworzone jest stałe i, jeśli tak, określa wartość tego stosunku.|
|[in](#in)|Konwertuje zewnętrznej reprezentacja sekwencji `Byte`s do reprezentacji wewnętrznej sekwencji `CharType`s.|
|[długość](#length)|Określa, ile `Byte`s z danej sekwencji zewnętrzne `Byte`produktu s nie więcej niż podany numer wewnętrzny `CharType`s i zwraca ten numer `Byte`s.|
|[MAX_LENGTH](#max_length)|Zwraca maksymalną liczbę zewnętrzne `Byte`s należy utworzyć jeden wewnętrzny `CharType`.|
|[out](#out)|Konwertuje sekwencji wewnętrznej `CharType`s z zewnętrznego sekwencji `Byte`s.|
|[unshift](#unshift)|Udostępnia zewnętrznej `Byte`s wymagane podczas konwersji zależny od stanu do ukończenia ostatni znak w sekwencji `Byte`s.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** Standard

## <a name="always_noconv"></a>  codecvt::always_noconv

Sprawdza, czy nie trzeba wykonać żadnych konwersji.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna, która jest **true** Jeśli nie ma konwersji muszą być; **false** jest co najmniej jeden musi być przeprowadzane.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_always_noconv](#do_always_noconv).

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

Konstruktor obiektów codecvt — klasa, służącym jako zestaw reguł ustawienia regionalne do obsługi konwersji.

```cpp
explicit codecvt(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

`_Refs` Wartość całkowita używany do określania typu zarządzania pamięci dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości `_Refs` i ich znaczenie są:

- 0: okres istnienia obiektu zarządza ustawieniami regionalnymi, które zawierałoby proces.

- 1: okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: te wartości są niezdefiniowane.

Konstruktor inicjuje jego `locale::facet` obiektu podstawowego z **locale::**[aspektu](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="do_always_noconv"></a>  codecvt::do_always_noconv

Funkcja wirtualna wywoływana w celu sprawdzenia, czy nie trzeba wykonywać żadnych konwersji.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję chronionego członka wirtualnego **true** tylko w przypadku każdego wywołania [do_in](#do_in) lub [do_out](#do_out) zwraca **noconv**.

Wersja szablonu zawsze zwraca **true**.

### <a name="example"></a>Przykład

Zobacz przykład [always_noconv —](#always_noconv), które wywołuje `do_always_noconv`.

## <a name="do_encoding"></a>  codecvt::do_encoding

Funkcji wirtualnej, który umożliwia sprawdzenie, czy kodowanie **bajtów** strumień jest stan zależnych, czy stosunek **bajtów**s użyty i **CharType**s tworzone jest stałe a jeśli tak, określa wartość tego stosunku.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję chroniony element członkowski wirtualnego:

- -1, jeśli kodowanie sekwencji typu `extern_type` stan jest zależne.

- 0, jeśli kodowanie obejmuje sekwencje różne długości.

- *N*, jeśli kodowanie obejmuje tylko sekwencji długości *N*

### <a name="example"></a>Przykład

Zobacz przykład [kodowanie](#encoding), które wywołuje `do_encoding`.

## <a name="do_in"></a>  codecvt::do_in

Funkcję wirtualną o nazwie przekonwertować sekwencję zewnętrzne **bajtów**s sekwencję wewnętrzny **CharType**s.

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

`_State` Stan konwersji obsługiwany między wywołań funkcji Członkowskich.

`first1` Wskaźnik na początku sekwencji do skonwertowania.

`last1` Wskaźnik na końcu sekwencji do skonwertowania.

`next1` Wskaźnik poza koniec sekwencja przekonwertowany, do pierwszego znaku nieprzekonwertowane.

`first2` Wskaźnik do początku przekonwertowany sekwencji.

`last2` Wskaźnik do końca przekonwertowany sekwencji.

`next2` Wskaźnik do **CharType** dołączony po przekonwertowaniu przez ostatnie **CharType**, do pierwszego znaku bez zmian w procesie docelowym.

### <a name="return-value"></a>Wartość zwracana

Typ zwracany, która wskazuje Powodzenie, częściowe powodzenie lub Niepowodzenie operacji. Funkcja zwraca:

- **codecvt_base::Error** Jeśli sekwencji źródłowej jest dotknięty sformułowany.

- `codecvt_base::noconv` Jeśli funkcja wykonuje brak konwersji.

- **codecvt_base::OK** Jeśli konwersja powiedzie się.

- **codecvt_base::Partial** Jeśli źródło jest niewystarczająca lub jeśli element docelowy nie jest niewystarczający, konwersja powiodła się.

### <a name="remarks"></a>Uwagi

`_State` musi reprezentować stan początkowy konwersji na początku nowego sekwencji źródłowej. Funkcja zmienia jej wartości przechowywanej w razie potrzeby, aby odzwierciedlały bieżący stan konwersji powiodło się. Jej wartości przechowywanej w przeciwnym razie jest nieokreślony.

### <a name="example"></a>Przykład

Zobacz przykład [w](#in), które wywołuje `do_in`.

## <a name="do_length"></a>  codecvt::do_length

Funkcji wirtualnej, który określa, ile **bajtów**s z danej sekwencji zewnętrzne **bajtów**produktu s nie więcej niż podany numer wewnętrzny **CharType**s i zwraca go Liczba **bajtów**s.

```cpp
virtual int do_length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>Parametry

`_State` Stan konwersji obsługiwany między wywołań funkcji Członkowskich.

`first1` Wskaźnik na początku sekwencji zewnętrznych.

`last1` Wskaźnik na końcu sekwencji zewnętrznych.

`_Len2` Maksymalna liczba **bajtów**s, który może być zwracany przez funkcję elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która reprezentuje liczbę konwersje nie większa niż maksymalna liczba `_Len2`, zdefiniowany przez źródło zewnętrzne sekwencję w [ `first1`, `last1`).

### <a name="remarks"></a>Uwagi

Wywołuje funkcję chroniony element członkowski wirtualnego `do_in`( `_State`, `first1`, `last1`, `next1`, `_Buf`, `_Buf`  +  `_Len2`, `next2`) dla `_State` (kopia stanie), niektórych buforu `_Buf`i wskaźniki `next1`i `next2`.

Następnie zwraca `next2`  -  **buforze**. W związku z tym liczy konwersje nie większa niż maksymalna liczba `_Len2`, zdefiniowany przez sekwencji źródłowej na [ `first1`, `last1`).

Wersja szablonu zawsze zwraca o mniejszej `last1`  -  `first1` i `_Len2`.

### <a name="example"></a>Przykład

Zobacz przykład [długość](#length), które wywołuje **do_length**.

## <a name="do_max_length"></a>  codecvt::do_max_length

Wirtualny funkcja, która zwraca maksymalną liczbę zewnętrzne **bajtów**s należy utworzyć jeden wewnętrzny **CharType**.

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba **bajtów**s należy utworzyć jeden **CharType**.

### <a name="remarks"></a>Uwagi

Funkcja chroniony wirtualny element członkowski zwraca największą wartość dopuszczalną wartość, która może być zwracany przez [do_length](#do_length)( `first1`, `last1`, 1) dla dowolnego prawidłowe wartości `first1` i `last1`.

### <a name="example"></a>Przykład

Zobacz przykład [max_length](#max_length), które wywołuje `do_max_length`.

## <a name="do_out"></a>  codecvt::do_out

Funkcję wirtualną o nazwie przekonwertować sekwencji wewnętrznej **CharType**s z zewnętrznego sekwencji **bajtów**s.

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

`_State` Stan konwersji obsługiwany między wywołań funkcji Członkowskich.

`first1` Wskaźnik na początku sekwencji do skonwertowania.

`last1` Wskaźnik na końcu sekwencji do skonwertowania.

`next1` Odwołanie do wskaźnika do pierwszej nieprzekonwertowany **CharType**, po ostatniej **CharType** przekonwertować.

`first2` Wskaźnik do początku przekonwertowany sekwencji.

`last2` Wskaźnik do końca przekonwertowany sekwencji.

`next2` Odwołanie do wskaźnika do pierwszej nieprzekonwertowany **bajtów**, po ostatniej **bajtów** przekonwertować.

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca:

- **codecvt_base::Error** Jeśli sekwencji źródłowej jest dotknięty sformułowany.

- `codecvt_base::noconv` Jeśli funkcja wykonuje brak konwersji.

- **codecvt_base::OK** Jeśli konwersja powiedzie się.

- **codecvt_base::Partial** Jeśli źródło jest niewystarczająca lub jeśli element docelowy nie jest wystarczająco duży dla konwersja powiodła się.

### <a name="remarks"></a>Uwagi

`_State` musi reprezentować stan początkowy konwersji na początku nowego sekwencji źródłowej. Funkcja zmienia jej wartości przechowywanej w razie potrzeby, aby odzwierciedlały bieżący stan konwersji powiodło się. Jej wartości przechowywanej w przeciwnym razie jest nieokreślony.

### <a name="example"></a>Przykład

Zobacz przykład [limit](#out), które wywołuje `do_out`.

## <a name="do_unshift"></a>  codecvt::do_unshift

Wywołuje funkcję wirtualną zapewnienie **bajtów**s wymagane podczas konwersji zależny od stanu do ukończenia ostatni znak w sekwencji **bajtów**s.

```cpp
virtual result do_unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

`_State` Stan konwersji obsługiwany między wywołań funkcji Członkowskich.

`first2` Wskaźnik do pierwszą pozycję w zakresie docelowym.

`last2` Wskaźnik do ostatniej pozycji w zakresie docelowym.

`next2` Wskaźnik do pierwszego elementu bez zmian w procesie docelowym.

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca:

- **codecvt_base::Error** Jeśli _ *stanu* reprezentuje nieprawidłowy stan.

- `codecvt_base::noconv` Jeśli funkcja wykonuje bez konwersji

- **codecvt_base::OK** Jeśli konwersja zakończy się powodzeniem.

- **codecvt_base::Partial** Jeśli element docelowy nie jest wystarczająco duży dla konwersja powiodła się

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego podejmuje próbę przekonwertowania elementu źródła **CharType**(0) do sekwencji docelowego, który jest przechowywany w [ `first2`, `last2`), z wyjątkiem zakończenia elementu **bajtów** (0). Zawsze są przechowywane w `next2` wskaźnik do pierwszego elementu bez zmian w procesie docelowym.

_ *Stanu* musi reprezentować stan początkowy konwersji na początku nowego sekwencji źródłowej. Funkcja zmienia jej wartości przechowywanej w razie potrzeby, aby odzwierciedlały bieżący stan konwersji powiodło się. Zazwyczaj Konwertowanie elementu źródła **CharType**(0) wyjdzie ze stanu bieżący stan początkowy konwersji.

### <a name="example"></a>Przykład

Zobacz przykład [unshift](#unshift), które wywołuje `do_unshift`.

## <a name="encoding"></a>  codecvt::Encoding

Sprawdzenie, czy kodowanie **bajtów** strumień jest stan zależnych, czy stosunek **bajtów**s używane i **CharType**s tworzone jest stałe i, jeśli tak, określa wartość tego stosunku.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość zwracana jest dodatnia, ta wartość jest stała liczba **bajtów** znaków wymagane do utworzenia **CharType** znaków.

Zwraca funkcję chroniony element członkowski wirtualnego:

- -1, jeśli kodowanie sekwencji typu `extern_type` stan jest zależne.

- 0, jeśli kodowanie obejmuje sekwencje różne długości.

- *N*, jeśli kodowanie obejmuje tylko sekwencji długości *N.*

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_encoding](#do_encoding).

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

Typ jest synonimem parametru szablonu **bajtów**.

## <a name="in"></a>  codecvt::in

Konwertuje zewnętrznej reprezentacja sekwencji **bajtów**s do reprezentacji wewnętrznej sekwencji **CharType**s.

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

`_State` Stan konwersji obsługiwany między wywołań funkcji Członkowskich.

`first1` Wskaźnik na początku sekwencji do skonwertowania.

`last1` Wskaźnik na końcu sekwencji do skonwertowania.

`next1` Wskaźnik poza koniec sekwencja przekonwertowane do pierwszego znaku nieprzekonwertowane.

`first2` Wskaźnik do początku przekonwertowany sekwencji.

`last2` Wskaźnik do końca przekonwertowany sekwencji.

`next2` Wskaźnik do **CharType** dołączony po przekonwertowaniu przez ostatnie **Chartype** do pierwszego znaku bez zmian w procesie docelowym.

### <a name="return-value"></a>Wartość zwracana

Typ zwracany, która wskazuje Powodzenie, częściowe powodzenie lub Niepowodzenie operacji. Funkcja zwraca:

- **codecvt_base::Error** Jeśli sekwencji źródłowej jest dotknięty sformułowany.

- `codecvt_base::noconv` Jeśli funkcja wykonuje brak konwersji.

- **codecvt_base::OK** Jeśli konwersja powiedzie się.

- **codecvt_base::Partial** Jeśli źródło jest niewystarczająca lub jeśli element docelowy nie jest wystarczająco duży dla konwersja powiodła się.

### <a name="remarks"></a>Uwagi

`_State` musi reprezentować stan początkowy konwersji na początku nowego sekwencji źródłowej. Funkcja zmienia jego przechowywana wartość zgodnie z potrzebami, aby odzwierciedlały bieżący stan konwersji powiodło się. Po przeprowadzeniu konwersji częściowe `_State` musi być ustawiona tak, aby umożliwić konwersji wznowienie nadejściu nowych znaków.

Funkcja członkowska zwraca [do_in](#do_in)( `_State`, _ *First1, Nazwisko1, next1, First2, _Llast2, next2*).

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

Typ jest synonimem parametru szablonu **CharType**.

## <a name="length"></a>  codecvt::length

Określa, ile **bajtów**s z danej sekwencji zewnętrzne **bajtów**produktu s nie więcej niż podany numer wewnętrzny **CharType**s i zwraca ten numer **Bajtów**s.

```cpp
int length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>Parametry

`_State` Stan konwersji obsługiwany między wywołań funkcji Członkowskich.

`first1` Wskaźnik na początku sekwencji zewnętrznych.

`last1` Wskaźnik na końcu sekwencji zewnętrznych.

`_Len2` Maksymalna liczba bajtów, które mogą być zwracane przez funkcję elementu członkowskiego.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która reprezentuje liczbę konwersje nie większa niż maksymalna liczba `_Len2`, zdefiniowany przez źródło zewnętrzne sekwencję w [ `first1`, `last1`).

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_length](#do_length)( *_State, first1*, `last1`, `_Len2`).

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

Zwraca maksymalną liczbę zewnętrzne **bajtów**s należy utworzyć jeden wewnętrzny **CharType**.

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba **bajtów**s należy utworzyć jeden **CharType**.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_max_length](#do_max_length).

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

Konwertuje sekwencji wewnętrznej **CharType**s z zewnętrznego sekwencji **bajtów**s.

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

`_State` Stan konwersji obsługiwany między wywołań funkcji Członkowskich.

`first1` Wskaźnik na początku sekwencji do skonwertowania.

`last1` Wskaźnik na końcu sekwencji do skonwertowania.

`next1` Odwołanie do wskaźnika do pierwszej nieprzekonwertowany **CharType** po ostatniej **CharType** przekonwertować.

`first2` Wskaźnik do początku przekonwertowany sekwencji.

`last2` Wskaźnik do końca przekonwertowany sekwencji.

`next2` Odwołanie do wskaźnika do pierwszej nieprzekonwertowany **bajtów** po przekonwertowaniu przez ostatnie **bajtów**.

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zwraca [do_out](#do_out)( `_State`, `first1`, `last1`, `next1`, `first2`, `last2`, `next2`).

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

Typ jest synonimem parametru szablonu **StateType**.

## <a name="unshift"></a>  codecvt::unshift

Udostępnia **bajtów**s wymagane podczas konwersji zależny od stanu do ukończenia ostatni znak w sekwencji **bajtów**s.

```cpp
result unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

`_State` Stan konwersji obsługiwany między wywołań funkcji Członkowskich.

`first2` Wskaźnik do pierwszą pozycję w zakresie docelowym.

`last2` Wskaźnik do ostatniej pozycji w zakresie docelowym.

`next2` Wskaźnik do pierwszego elementu bez zmian w procesie docelowym.

### <a name="return-value"></a>Wartość zwracana

Funkcja zwraca:

- **codecvt_base::Error** Jeśli stan reprezentuje nieprawidłowy stan.

- `codecvt_base::noconv` Jeśli funkcja wykonuje brak konwersji.

- **codecvt_base::OK** Jeśli konwersja powiedzie się.

- **codecvt_base::Partial** Jeśli element docelowy nie jest wystarczająco duży dla konwersja powiodła się.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego podejmuje próbę przekonwertowania elementu źródła **CharType**(0) do sekwencji docelowego, który jest przechowywany w [ `first2`, `last2`), z wyjątkiem zakończenia elementu **bajtów** (0). Zawsze są przechowywane w `next2` wskaźnik do pierwszego elementu bez zmian w procesie docelowym.

`_State` musi reprezentować stan początkowy konwersji na początku nowego sekwencji źródłowej. Funkcja zmienia jego przechowywana wartość zgodnie z potrzebami, aby odzwierciedlały bieżący stan konwersji powiodło się. Zazwyczaj Konwertowanie elementu źródła **CharType**(0) wyjdzie ze stanu bieżący stan początkowy konwersji.

Funkcja członkowska zwraca [do_unshift](#do_unshift)( `_State`, `first2`, `last2`, `next2` ).

## <a name="see-also"></a>Zobacz także

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>
[Strony kodowe](../c-runtime-library/code-pages.md)<br/>
[Nazwy lokalne, języki i ciągi Kraj/Region](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
