---
title: ctype — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype
- xlocale/std::ctype::char_type
- xlocale/std::ctype::do_is
- xlocale/std::ctype::do_narrow
- xlocale/std::ctype::do_scan_is
- xlocale/std::ctype::do_scan_not
- xlocale/std::ctype::do_tolower
- xlocale/std::ctype::do_toupper
- xlocale/std::ctype::do_widen
- xlocale/std::ctype::is
- xlocale/std::ctype::narrow
- xlocale/std::ctype::scan_is
- xlocale/std::ctype::scan_not
- xlocale/std::ctype::tolower
- xlocale/std::ctype::toupper
- xlocale/std::ctype::widen
helpviewer_keywords:
- std::ctype [C++]
- std::ctype [C++], char_type
- std::ctype [C++], do_is
- std::ctype [C++], do_narrow
- std::ctype [C++], do_scan_is
- std::ctype [C++], do_scan_not
- std::ctype [C++], do_tolower
- std::ctype [C++], do_toupper
- std::ctype [C++], do_widen
- std::ctype [C++], is
- std::ctype [C++], narrow
- std::ctype [C++], scan_is
- std::ctype [C++], scan_not
- std::ctype [C++], tolower
- std::ctype [C++], toupper
- std::ctype [C++], widen
ms.assetid: 3627154c-49d9-47b5-b28f-5bbedee38e3b
ms.openlocfilehash: 640b2cc8506e498006feedbea6825a0e51a88209
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876312"
---
# <a name="ctype-class"></a>ctype — Klasa

Klasa zawierająca zestaw reguł, który służy do klasyfikowania znaków, konwersji z wielkich i małych liter i konwersji między macierzystym zestawem znaków i zestawem używanym przez ustawienia regionalne.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>Parametry

\ *CharType*
Typ używany w programie do kodowania znaków.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w `id`. Do kryteriów klasyfikacji jest dostarczany typ zagnieżdżonej maski bitów w klasie bazowej ctype_base.

C++ Standardowa biblioteka definiuje dwie jawne specjalizacje tego szablonu klasy:

- `ctype<char>`, jawnej specjalizacji, której różnice są opisane osobno. Aby uzyskać więcej informacji, zobacz [ctype&lt;char&gt; Class](../standard-library/ctype-char-class.md).

- `ctype<wchar_t>`, która traktuje elementy jako znaki dwubajtowe.

Inne specjalizacje `ctype<CharType>`szablonu klasy:

- Konwertuj wartość *ch* typu *CharType* na wartość typu **char** z wyrażeniem `(char)ch`.

- Przekonwertuj wartość *bajtu* typu **char** na wartość typu *chartype* z wyrażeniem `CharType(byte)`.

Wszystkie inne operacje są wykonywane na wartościach **char** w taki sam sposób jak w przypadku jawnej specjalizacji `ctype<char>`.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[CType](#ctype)|Konstruktor dla obiektów klasy `ctype`, które stanowią zestawy reguł ustawień regionalnych dla znaków.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ, który opisuje znak używany przez ustawienie regionalne.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[do_is](#do_is)|Funkcja wirtualna wywoływana w celu sprawdzenia, czy pojedynczy znak ma określony atrybut, lub sklasyfikowania atrybutów każdego znaku w zakresie i przechowywania ich w tablicy.|
|[do_narrow](#do_narrow)|Funkcja wirtualna wywoływana w celu przekonwertowania znaku typu `CharType` używanego przez ustawienia regionalne do odpowiedniego znaku typu **char** w macierzystym zestawie znaków.|
|[do_scan_is](#do_scan_is)|Wirtualna funkcja wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który pasuje do określonej maski.|
|[do_scan_not](#do_scan_not)|Funkcja wirtualna wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który nie pasuje do określonej maski.|
|[do_tolower](#do_tolower)|Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na ich małe litery.|
|[do_toupper](#do_toupper)|Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na ich wielkie litery.|
|[do_widen](#do_widen)|Funkcja wirtualna wywoływana w celu przekonwertowania znaku typu **char** w macierzystym zestawie znaków do odpowiedniego znaku typu `CharType` używanego przez ustawienia regionalne.|
|[is](#is)|Sprawdza, czy pojedynczy znak ma określony atrybut, lub klasyfikuje atrybuty każdego znaku w zakresie i przechowuje je w tablicy.|
|[dokładniej](#narrow)|Konwertuje znak typu `CharType` używany przez ustawienia regionalne do odpowiedniego znaku typu char w macierzystym zestawie znaków.|
|[scan_is](#scan_is)|Lokalizuje pierwszy znak w zakresie, który pasuje do określonej maski.|
|[scan_not](#scan_not)|Lokalizuje pierwszy znak w zakresie, który nie pasuje do określonej maski.|
|[ToLower](#tolower)|Konwertuje znak lub zakres znaków na małe litery.|
|[ToUpper](#toupper)|Konwertuje znak lub zakres znaków na wielkie litery.|
|[szerzon](#widen)|Konwertuje znak typu **char** w macierzystym zestawie znaków na odpowiedni znak typu `CharType` używany przez ustawienia regionalne.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<locale >

**Przestrzeń nazw:** std

## <a name="char_type"></a>CType:: char_type

Typ, który opisuje znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *CharType*.

### <a name="example"></a>Przykład

Zobacz [rozszerzenie](#widen) funkcja członkowska, aby zapoznać się z przykładem, który używa `char_type` jako wartości zwracanej.

## <a name="ctype"></a>CType:: CType

Konstruktor dla obiektów klasy CType, które stanowią zestawy reguł ustawień regionalnych dla znaków.

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Wartość całkowita służąca do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie są następujące:

- 0: okres istnienia obiektu jest zarządzany przez elementy lokalne, które go zawierają.

- 1: okres istnienia obiektu musi być zarządzany ręcznie.

- \> 1: te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

Konstruktor inicjuje swój `locale::facet` obiektu podstawowego z **ustawieniami regionalnymi::** [facet](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="do_is"></a>CType::d o_is

Funkcja wirtualna wywoływana w celu sprawdzenia, czy pojedynczy znak ma określony atrybut, lub sklasyfikowania atrybutów każdego znaku w zakresie i przechowywania ich w tablicy.

```cpp
virtual bool do_is(
    mask maskVal,
    CharType ch) const;

virtual const CharType *do_is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parametry

*maskVal*\
Wartość maski, dla której ma zostać przetestowany znak.

*ch*\
Znak, którego atrybuty mają zostać przetestowane.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie, którego atrybuty mają być klasyfikowane.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie, którego atrybuty mają być klasyfikowane.

\ miejsca *docelowego*
Wskaźnik do początku tablicy, gdzie są przechowywane wartości maski charakteryzujące atrybuty każdego z znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja członkowska zwraca wartość logiczną **prawda** , jeśli testowany znak ma atrybut opisany przez wartość maski; **wartość false** , jeśli nie ma atrybutu.

Druga funkcja członkowska zwraca tablicę zawierającą wartości maski charakteryzujące atrybuty każdego ze znaków w zakresie.

### <a name="remarks"></a>Uwagi

Wartości masek klasyfikacji atrybutów znaków są udostępniane przez klasę [ctype_base](../standard-library/ctype-base-class.md), z których CType dziedziczy. Pierwsza funkcja członkowska może przyjmować wyrażenia dla pierwszego parametru, zwane jako masek bitowych i utworzone z kombinacji wartości maski przez logiczne operatory bitowe (&#124; , &, ^, ~).

### <a name="example"></a>Przykład

Zobacz przykład dla elementu [is](#is), który wywołuje `do_is`.

## <a name="do_narrow"></a>CType::d o_narrow

Funkcja wirtualna wywoływana w celu przekonwertowania znaku typu `CharType` używanego przez ustawienia regionalne do odpowiedniego znaku typu **char** w macierzystym zestawie znaków.

```cpp
virtual char do_narrow(
    CharType ch,
    char default = '\0') const;

virtual const CharType* do_narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parametry

*ch*\
Znak typu `Chartype` używany przez ustawienia regionalne do przekonwertowania.

\ *domyślne*
Wartość domyślna, która ma zostać przypisana przez funkcję członkowską do znaków typu `CharType`, które nie mają odpowiedników znaków typu **char**.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie znaków do przekonwertowania.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków do przekonwertowania.

\ miejsca *docelowego*
Stała wskaźnik do pierwszego znaku typu **char** w zakresie docelowym, który przechowuje przekonwertowany zakres znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza chroniona funkcja członkowska zwraca natywny znak typu char, który odpowiada znakowi parametru typu `CharType` lub *wartość domyślna* , jeśli nie zdefiniowano odpowiednika.

Druga funkcja chronionego elementu członkowskiego zwraca wskaźnik do zakresu docelowego znaków natywnych przekonwertowanych z znaków typu `CharType`.

### <a name="remarks"></a>Uwagi

Druga funkcja szablonu chronionego elementu członkowskiego przechowuje w `dest`[`I`] wartość `do_narrow`(`first` [`I`], `default`), dla `I` w interwale [0, `last` - `first`).

### <a name="example"></a>Przykład

Zobacz przykład [wąski](#narrow), który wywołuje `do_narrow`.

## <a name="do_scan_is"></a>CType::d o_scan_is

Wirtualna funkcja wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który pasuje do określonej maski.

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal*\
Wartość maski do dopasowania przez znak.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie, który ma być skanowany.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie, który ma być skanowany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego znaku w zakresie, który jest zgodny z określoną maską. Jeśli taka wartość nie istnieje, funkcja zwraca wartość *Last*.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego zwraca najmniejszy wskaźnik `ptr` w zakresie [`first`, `last`), dla którego [do_is](#do_is)(`maskVal`, \* `ptr`) ma wartość true.

### <a name="example"></a>Przykład

Zobacz przykład dla [scan_is](#scan_is), który wywołuje `do_scan_is`.

## <a name="do_scan_not"></a>CType::d o_scan_not

Funkcja wirtualna wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który nie pasuje do określonej maski.

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal*\
Wartość maski nie powinna być dopasowana przez znak.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie, który ma być skanowany.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie, który ma być skanowany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego znaku w zakresie, który nie pasuje do określonej maski. Jeśli taka wartość nie istnieje, funkcja zwraca wartość *Last*.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego zwraca najmniejszy wskaźnik `ptr` w zakresie [`first`, `last`), dla którego [do_is](#do_is)(`maskVal`, \* `ptr`) ma wartość false.

### <a name="example"></a>Przykład

Zobacz przykład dla [scan_not](#scan_not), który wywołuje `do_scan_not`.

## <a name="do_tolower"></a>CType::d o_tolower

Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na małe litery.

```cpp
virtual CharType do_tolower(CharType ch) const;

virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch*\
Znak do przekonwertowania na małe litery.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie znaków, którego przypadki mają być konwertowane.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków, którego przypadki mają być konwertowane.

### <a name="return-value"></a>Wartość zwracana

Pierwsza chroniona funkcja członkowska zwraca małą formę parametru *ch*. Jeśli nie istnieje małe litery, zwraca wartość *ch*. Druga funkcja chronionego elementu członkowskiego zwraca wartość *Last*.

### <a name="remarks"></a>Uwagi

Druga funkcja szablonu chronionego elementu członkowskiego zastępuje każdy element `first` [`I`], dla `I` w interwale [0, `last` - `first`), z `do_tolower`(`first` [`I`]).

### <a name="example"></a>Przykład

Zobacz przykład dla [ToLower](#tolower), który wywołuje `do_tolower`.

## <a name="do_toupper"></a>CType::d o_toupper

Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na ich wielkie litery.

```cpp
virtual CharType do_toupper(CharType ch) const;

virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch*\
Znak do przekonwertowania na wielkie litery.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie znaków, którego przypadki mają być konwertowane.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków, którego przypadki mają być konwertowane.

### <a name="return-value"></a>Wartość zwracana

Pierwsza chroniona funkcja członkowska zwraca wielką formę parametru *ch*. Jeśli nie istnieje Wielka litera, zwraca wartość *ch*. Druga funkcja chronionego elementu członkowskiego zwraca wartość *Last*.

### <a name="remarks"></a>Uwagi

Druga funkcja szablonu chronionego elementu członkowskiego zastępuje każdy element `first` [`I`], dla `I` w interwale [0, `last` - `first`), z `do_toupper`(`first` [`I`]).

### <a name="example"></a>Przykład

Zobacz przykład dla [ToUpper](#toupper), który wywołuje `do_toupper`.

## <a name="do_widen"></a>CType::d o_widen

Funkcja wirtualna wywoływana w celu przekonwertowania znaku typu **char** w macierzystym zestawie znaków do odpowiedniego znaku typu `CharType` używanego przez ustawienia regionalne.

```cpp
virtual CharType do_widen(char byte) const;

virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>Parametry

\ *bajtów*
Znak typu **char** w macierzystym zestawie znaków do przekonwertowania.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie znaków do przekonwertowania.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków do przekonwertowania.

\ miejsca *docelowego*
Wskaźnik do pierwszego znaku typu `CharType` w zakresie docelowym, który przechowuje przekonwertowany zakres znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza chroniona funkcja członkowska zwraca znak typu `CharType`, który odpowiada znakowi parametru typu natywnego **char**.

Druga funkcja chronionego elementu członkowskiego zwraca wskaźnik do docelowego zakresu znaków typu `CharType` używany przez ustawienia regionalne konwertowane z znaków natywnych typu **char**.

### <a name="remarks"></a>Uwagi

Druga funkcja szablonu chronionego elementu członkowskiego przechowuje w `dest`[`I`] wartość `do_widen`(`first`[`I`]) dla `I` w interwale [0, `last` - `first`).

### <a name="example"></a>Przykład

Zobacz przykład dla [rozszerzenia](#widen), który wywołuje `do_widen`.

## <a name="is"></a>CType:: is

Testuje, czy pojedynczy znak ma określony atrybut, lub klasyfikuje atrybuty każdego znaku w zakresie i zapisuje je w tablicy.

```cpp
bool is(mask maskVal, CharType ch) const;

const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parametry

*maskVal*\
Wartość maski, dla której ma zostać przetestowany znak.

*ch*\
Znak, którego atrybuty mają zostać przetestowane.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie, którego atrybuty mają być klasyfikowane.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie, którego atrybuty mają być klasyfikowane.

\ miejsca *docelowego*
Wskaźnik do początku tablicy, gdzie są przechowywane wartości maski charakteryzujące atrybuty każdego z znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja członkowska zwraca **wartość true** , jeśli testowany znak ma atrybut opisany przez wartość maski; **wartość false** , jeśli nie ma atrybutu.

Druga funkcja członkowska zwraca wskaźnik do ostatniego znaku w zakresie, którego atrybuty mają być klasyfikowane.

### <a name="remarks"></a>Uwagi

Wartości masek klasyfikacji atrybutów znaków są dostarczane przez klasę [Ctype_base klasy](../standard-library/ctype-base-class.md), z których dziedziczy CType. Pierwsza funkcja członkowska może przyjmować wyrażenia dla pierwszego parametru, zwane jako masek bitowych i utworzone z kombinacji wartości maski przez logiczne operatory bitowe (&#124; , &, ^, ~).

### <a name="example"></a>Przykład

```cpp
// ctype_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main() {
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );

   if (use_facet<ctype<char> > ( loc1 ).is( ctype_base::alpha, 'a' ))
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if (use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!' ))
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;

   char *string = "Hello, my name is John!";
   ctype<char>::mask maskarray[30];
   use_facet<ctype<char> > ( loc2 ).is(
      string, string + strlen(string), maskarray );
   for (unsigned int i = 0; i < strlen(string); i++) {
      cout << string[i] << ": "
           << (maskarray[i] & ctype_base::alpha  "alpha"
                                                : "not alpha")
           << endl;;
   };
}
```

## <a name="narrow"></a>CType:: Narrow

Konwertuje znaki typu `CharType` używane przez ustawienia regionalne do odpowiednich znaków typu **char** w macierzystym zestawie znaków.

```cpp
char narrow(CharType ch, char default = '\0') const;

const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parametry

*ch*\
Znak typu `Chartype` używany przez ustawienia regionalne do przekonwertowania.

\ *domyślne*
Wartość domyślna, która ma zostać przypisana przez funkcję członkowską do znaków typu `CharType`, które nie mają odpowiedników znaków typu **char**.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie znaków do przekonwertowania.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków do przekonwertowania.

\ miejsca *docelowego*
Stała wskaźnik do pierwszego znaku typu **char** w zakresie docelowym, który przechowuje przekonwertowany zakres znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja członkowska zwraca natywny znak typu **char** , który odpowiada znakowi parametru typu `CharType default`, jeśli nie określono odpowiednika.

Druga funkcja członkowska zwraca wskaźnik do zakresu docelowego znaków natywnych przekonwertowanych ze znaków typu `CharType`.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca [do_narrow](#do_narrow)(`ch`, `default`). Druga funkcja członkowska zwraca [do_narrow](#do_narrow) (`first`, `last`, `default`, `dest`). Tylko podstawowe znaki źródłowe mają mieć zagwarantowany unikatowy `CharType` obrazu w obszarze `narrow`. W przypadku następujących podstawowych znaków źródłowych: `narrow` ( [rozszerzenie](#widen) ( **c** ), 0) = = **c**.

### <a name="example"></a>Przykład

```cpp
// ctype_narrow.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "english" );
   wchar_t *str1 = L"\x0392fhello everyone";
   char str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).narrow
      ( str1, str1 + wcslen(str1), 'X', &str2[0] ) != 0);  // C4996
   str2[wcslen(str1)] = '\0';
   wcout << str1 << endl;
   cout << &str2[0] << endl;
}
```

```Output
Xhello everyone
```

## <a name="scan_is"></a>CType:: scan_is

Lokalizuje pierwszy znak w zakresie, który pasuje do określonej maski.

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal*\
Wartość maski do dopasowania przez znak.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie, który ma być skanowany.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie, który ma być skanowany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego znaku w zakresie, który jest zgodny z określoną maską. Jeśli taka wartość nie istnieje, funkcja zwraca wartość *Last*.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_scan_is](#do_scan_is)(`maskVal`, `first`, `last`).

### <a name="example"></a>Przykład

```cpp
// ctype_scan_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_is
      ( ctype_base::punct, string, string + strlen(string) );
   cout << "The first punctuation is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
The first punctuation is "," at position: 5
```

## <a name="scan_not"></a>CType:: scan_not

Lokalizuje pierwszy znak w zakresie, który nie pasuje do określonej maski.

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal*\
Wartość maski nie powinna być dopasowana przez znak.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie, który ma być skanowany.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie, który ma być skanowany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego znaku w zakresie, który nie pasuje do określonej maski. Jeśli taka wartość nie istnieje, funkcja zwraca wartość *Last*.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_scan_not](#do_scan_not)(`maskVal`, `first`, `last`).

### <a name="example"></a>Przykład

```cpp
// ctype_scan_not.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_not
      ( ctype_base::alpha, string, string + strlen(string) );
   cout << "First nonalpha character is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
First nonalpha character is "," at position: 5
```

## <a name="tolower"></a>CType:: ToLower

Konwertuje znak lub zakres znaków na małe litery.

```cpp
CharType tolower(CharType ch) const;

const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch*\
Znak do przekonwertowania na małe litery.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie znaków, którego przypadki mają być konwertowane.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków, którego przypadki mają być konwertowane.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja członkowska zwraca małą formę parametru *ch*. Jeśli nie istnieje małe litery, zwraca wartość *ch*.

Druga funkcja członkowska zwraca wartość *Last*.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca [do_tolower](#do_tolower)(`ch`). Druga funkcja członkowska zwraca [do_tolower](#do_tolower)(`first`, `last`).

### <a name="example"></a>Przykład

```cpp
// ctype_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "HELLO, MY NAME IS JOHN";

   use_facet<ctype<char> > ( loc1 ).tolower
      ( string, string + strlen(string) );
   cout << "The lowercase string is: " << string << endl;
}
```

```Output
The lowercase string is: hello, my name is john
```

## <a name="toupper"></a>CType:: ToUpper

Konwertuje znak lub zakres znaków na wielkie litery.

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch*\
Znak do przekonwertowania na wielkie litery.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie znaków, którego przypadki mają być konwertowane.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków, którego przypadki mają być konwertowane.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja członkowska zwraca wielką formę parametru *ch*. Jeśli nie istnieje Wielka litera, zwraca wartość *ch*.

Druga funkcja członkowska zwraca wartość *Last*.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca [do_toupper](#do_toupper)(`ch`). Druga funkcja członkowska zwraca [do_toupper](#do_toupper)(`first`, `last`).

### <a name="example"></a>Przykład

```cpp
// ctype_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "Hello, my name is John";

   use_facet<ctype<char> > ( loc1 ).toupper
      ( string, string + strlen(string) );
   cout << "The uppercase string is: " << string << endl;
}
```

```Output
The uppercase string is: HELLO, MY NAME IS JOHN
```

## <a name="widen"></a>CType:: rozszerzając

Konwertuje znak typu **char** w macierzystym zestawie znaków na odpowiedni znak typu `CharType` używany przez ustawienia regionalne.

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>Parametry

\ *bajtów*
Znak typu char w macierzystym zestawie znaków do przekonwertowania.

*pierwszy*\
Wskaźnik do pierwszego znaku w zakresie znaków do przekonwertowania.

*ostatni*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków do przekonwertowania.

\ miejsca *docelowego*
Wskaźnik do pierwszego znaku typu `CharType` w zakresie docelowym, który przechowuje przekonwertowany zakres znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja członkowska zwraca znak typu `CharType`, który odpowiada znakowi parametru typu natywnego **char**.

Druga funkcja członkowska zwraca wskaźnik do zakresu docelowego znaków typu `CharType` używany przez ustawienia regionalne konwertowane z znaków natywnych typu **char**.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca [do_widen](#do_widen)(`byte`). Druga funkcja członkowska zwraca [do_widen](#do_widen)(`first`, `last`, `dest`).

### <a name="example"></a>Przykład

```cpp
// ctype_widen.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "English" );
   char *str1 = "Hello everyone!";
   wchar_t str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).widen
      ( str1, str1 + strlen(str1), &str2[0] ) != 0);  // C4996
   str2[strlen(str1)] = '\0';
   cout << str1 << endl;
   wcout << &str2[0] << endl;

   ctype<wchar_t>::char_type charT;
   charT = use_facet<ctype<char> > ( loc1 ).widen( 'a' );
}
```

```Output
Hello everyone!
Hello everyone!
```

## <a name="see-also"></a>Zobacz też

[\<ustawienia regionalne >](../standard-library/locale.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
