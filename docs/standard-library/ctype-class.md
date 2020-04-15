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
ms.openlocfilehash: dae6f62a0eda9263986a77b82754596d17be94e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373165"
---
# <a name="ctype-class"></a>ctype — Klasa

Klasa zawierająca zestaw reguł, który służy do klasyfikowania znaków, konwersji z wielkich i małych liter i konwersji między macierzystym zestawem znaków i zestawem używanym przez ustawienia regionalne.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ używany w programie do kodowania znaków.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości `id`przechowuje unikatową wartość dodatnią w programie . Do kryteriów klasyfikacji jest dostarczany typ zagnieżdżonej maski bitów w klasie bazowej ctype_base.

Biblioteka standardowa języka C++ definiuje dwie jawne specjalizacje tego szablonu klasy:

- `ctype<char>`, specjalizacja jawna, której różnice są opisane oddzielnie. Aby uzyskać więcej informacji, zobacz [ctype&lt;char&gt; Class](../standard-library/ctype-char-class.md).

- `ctype<wchar_t>`, który traktuje elementy jako szerokie znaki.

Inne specjalizacje `ctype<CharType>`szablonu klasy:

- Konwertuj wartość *typu* *CharType* na wartość **typu** `(char)ch`char z wyrażeniem .

- Konwertuj *bajt* wartości **typu char** na wartość `CharType(byte)`typu *CharType* z wyrażeniem .

Wszystkie inne operacje są wykonywane na wartości **char** w `ctype<char>`taki sam sposób, jak dla specjalizacji jawne .

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Ctype](#ctype)|Konstruktor dla `ctype` obiektów klasy, które służą jako aspekty ustawień regionalnych dla znaków.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ, który opisuje znak używany przez ustawienie regionalne.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[do_is](#do_is)|Funkcja wirtualna wywoływana w celu sprawdzenia, czy pojedynczy znak ma określony atrybut, lub sklasyfikowania atrybutów każdego znaku w zakresie i przechowywania ich w tablicy.|
|[do_narrow](#do_narrow)|Funkcja wirtualna wywoływana do `CharType` konwersji znaku typu używanego przez ustawienia regionalne na odpowiedni znak **typu char** w natywnym zestawie znaków.|
|[do_scan_is](#do_scan_is)|Wirtualna funkcja wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który pasuje do określonej maski.|
|[do_scan_not](#do_scan_not)|Funkcja wirtualna wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który nie pasuje do określonej maski.|
|[do_tolower](#do_tolower)|Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na ich małe litery.|
|[do_toupper](#do_toupper)|Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na ich wielkie litery.|
|[do_widen](#do_widen)|Funkcja wirtualna wywoływana do konwertowania znaku **typu char** w `CharType` natywnym zestawie znaków na odpowiedni znak typu używanego przez ustawienia regionalne.|
|[is](#is)|Sprawdza, czy pojedynczy znak ma określony atrybut, lub klasyfikuje atrybuty każdego znaku w zakresie i przechowuje je w tablicy.|
|[Wąskie](#narrow)|Konwertuje znak `CharType` typu używanego przez ustawienia regionalne na odpowiedni znak typu char w natywnym zestawie znaków.|
|[scan_is](#scan_is)|Lokalizuje pierwszy znak w zakresie, który pasuje do określonej maski.|
|[scan_not](#scan_not)|Lokalizuje pierwszy znak w zakresie, który nie pasuje do określonej maski.|
|[Tolower](#tolower)|Konwertuje znak lub zakres znaków na małe litery.|
|[Toupper](#toupper)|Konwertuje znak lub zakres znaków na wielkie litery.|
|[Poszerzyć](#widen)|Konwertuje znak **typu char** w natywnym zestawie `CharType` znaków na odpowiedni znak typu używanego przez ustawienia regionalne.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="ctypechar_type"></a><a name="char_type"></a>ctype::char_type

Typ, który opisuje znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu *CharType*.

### <a name="example"></a>Przykład

Zobacz [poszerzyć](#widen) funkcję elementu członkowskiego `char_type` na przykład, który używa jako wartość zwracaną.

## <a name="ctypectype"></a><a name="ctype"></a>ctype::ctype

Konstruktor dla obiektów klasy ctype, które służą jako aspekty ustawień regionalnych dla znaków.

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_refs*\
Wartość całkowita używana do określania typu zarządzania pamięcią dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie to:

- 0: Okres istnienia obiektu jest zarządzany przez ustawienia regionalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: Te wartości nie są zdefiniowane.

Nie są możliwe żadne bezpośrednie przykłady, ponieważ destruktor jest chroniony.

`locale::facet` Konstruktor inicjuje swój obiekt bazowy za pomocą ustawień **regionalnych::**[aspekt](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="ctypedo_is"></a><a name="do_is"></a>ctype::do_is

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
Wartość maski, dla której znak ma być testowany.

*Ch*\
Znak, którego atrybuty mają być testowane.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie, którego atrybuty mają być klasyfikowane.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie, którego atrybuty mają być klasyfikowane.

*Dest*\
Wskaźnik do początku tablicy, w którym mają być przechowywane wartości maski charakteryzujące atrybuty każdego ze znaków.

### <a name="return-value"></a>Wartość zwracana

Funkcja pierwszego elementu członkowskiego zwraca wartość logiczną, która jest **prawdziwa,** jeśli testowany znak ma atrybut opisany przez wartość maski; **false,** jeśli nie ma atrybutu.

Funkcja drugiego elementu członkowskiego zwraca tablicę zawierającą wartości maski charakteryzujące atrybuty każdego ze znaków w zakresie.

### <a name="remarks"></a>Uwagi

Wartości maski klasyfikujące atrybuty znaków są dostarczane przez klasę [ctype_base](../standard-library/ctype-base-class.md), z której pochodzi ctype. Funkcja pierwszego elementu członkowskiego może akceptować wyrażenia dla swojego pierwszego parametru, nazywanego maskami bitowymi i utworzona z kombinacji wartości maski przez logiczne operatory bitowe (&#124; , & ^ , ~).

### <a name="example"></a>Przykład

Zobacz przykład [jest](#is), `do_is`który wywołuje .

## <a name="ctypedo_narrow"></a><a name="do_narrow"></a>ctype::do_narrow

Funkcja wirtualna wywoływana do `CharType` konwersji znaku typu używanego przez ustawienia regionalne na odpowiedni znak **typu char** w natywnym zestawie znaków.

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

*Ch*\
Znak typu `Chartype` używanego przez ustawienia regionalne do konwersji.

*Domyślny*\
Wartość domyślna, która ma być przypisana `CharType` przez funkcję elementu członkowskiego do znaków typu, które nie mają znaków odpowiednika typu **char**.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie znaków do konwersji.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków do konwersji.

*Dest*\
Wskaźnik const do pierwszego znaku typu **char** w zakresie docelowym, który przechowuje przekonwertowany zakres znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja chronionego elementu członkowskiego zwraca znak macierzysty typu char, `CharType` który odpowiada znakowi parametru typu lub *domyślnemu,* jeśli nie zdefiniowano żadnego odpowiednika.

Druga funkcja chronionego elementu członkowskiego zwraca wskaźnik do docelowego zakresu `CharType`znaków natywnych przekonwertowanych ze znaków typu .

### <a name="remarks"></a>Uwagi

Druga funkcja chronionego szablonu `dest` `I`elementu członkowskiego `do_narrow`przechowuje `default`w `I` [ ] wartość `last`  -  `first`( `first` [ `I`], dla w przedziale [0, ).

### <a name="example"></a>Przykład

Zobacz przykład [wąski](#narrow), `do_narrow`który wywołuje .

## <a name="ctypedo_scan_is"></a><a name="do_scan_is"></a>ctype::do_scan_is

Wirtualna funkcja wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który pasuje do określonej maski.

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal*\
Wartość maski, która ma być dopasowana przez znak.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie, który ma być skanowany.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie, który ma być skanowany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego znaku w zakresie, który pasuje do określonej maski. Jeśli taka wartość nie istnieje, funkcja zwraca *ostatni*plik .

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego zwraca `ptr` najmniejszy wskaźnik `first` `last`w zakresie [ , \* `ptr`), dla którego [do_is](#do_is)( , `maskVal`) jest true.

### <a name="example"></a>Przykład

Zobacz przykład [scan_is](#scan_is), który wywołuje `do_scan_is`.

## <a name="ctypedo_scan_not"></a><a name="do_scan_not"></a>ctype::do_scan_not

Funkcja wirtualna wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który nie pasuje do określonej maski.

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal*\
Wartość maski, która nie ma być dopasowywała się do znaku.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie, który ma być skanowany.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie, który ma być skanowany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego znaku w zakresie, który nie pasuje do określonej maski. Jeśli taka wartość nie istnieje, funkcja zwraca *ostatni*plik .

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego zwraca `ptr` najmniejszy wskaźnik `first` `last`w zakresie [ , ), \* `ptr`dla którego [do_is](#do_is)( , `maskVal`) jest false.

### <a name="example"></a>Przykład

Zobacz przykład [scan_not](#scan_not), który wywołuje `do_scan_not`.

## <a name="ctypedo_tolower"></a><a name="do_tolower"></a>ctype::do_tolower

Funkcja wirtualna wywoływana do konwersji znaku lub zakresu znaków na małe litery.

```cpp
virtual CharType do_tolower(CharType ch) const;

virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, który ma zostać przekonwertowany na małe litery.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie znaków, których sprawy mają zostać przekonwertowane.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków, których sprawy mają zostać przekonwertowane.

### <a name="return-value"></a>Wartość zwracana

Pierwsza chroniona funkcja elementów członkowskich zwraca formularz małych liter parametru *ch*. Jeśli formularz małych liter nie istnieje, zwraca on *go*. Druga chroniona funkcja elementu członkowskiego zwraca *ostatni*plik .

### <a name="remarks"></a>Uwagi

Druga chroniona funkcja szablonu elementu `first` `I`członkowskiego `I` zastępuje każdy element [ `last`  -  `first`], `do_tolower` `first` dla `I`w interwale [0, ), z ( [ ]).

### <a name="example"></a>Przykład

Zobacz przykład [tolower](#tolower), `do_tolower`który wywołuje .

## <a name="ctypedo_toupper"></a><a name="do_toupper"></a>ctype::do_toupper

Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na ich wielkie litery.

```cpp
virtual CharType do_toupper(CharType ch) const;

virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, który ma zostać przekonwertowany na wielkie litery.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie znaków, których sprawy mają zostać przekonwertowane.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków, których sprawy mają zostać przekonwertowane.

### <a name="return-value"></a>Wartość zwracana

Pierwsza chroniona funkcja elementu członkowskiego zwraca wielką literę parametru *ch*. Jeśli formularz nie istnieje, zwraca on *ch*. Druga chroniona funkcja elementu członkowskiego zwraca *ostatni*plik .

### <a name="remarks"></a>Uwagi

Druga chroniona funkcja szablonu elementu `first` `I`członkowskiego `I` zastępuje każdy element [ `last`  -  `first`], `do_toupper` `first` dla `I`w interwale [0, ), z ( [ ]).

### <a name="example"></a>Przykład

Zobacz przykład [toupper](#toupper), `do_toupper`który wywołuje .

## <a name="ctypedo_widen"></a><a name="do_widen"></a>ctype::do_widen

Funkcja wirtualna wywoływana do konwertowania znaku **typu char** w `CharType` natywnym zestawie znaków na odpowiedni znak typu używanego przez ustawienia regionalne.

```cpp
virtual CharType do_widen(char byte) const;

virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>Parametry

*Bajtów*\
Znak typu **char** w natywnym zestawie znaków do konwersji.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie znaków do konwersji.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków do konwersji.

*Dest*\
Wskaźnik do pierwszego znaku `CharType` typu w zakresie docelowym, który przechowuje przekonwertowany zakres znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja chronionego elementu członkowskiego `CharType` zwraca znak typu odpowiadający znakowi parametru **znaku**typu macierzystego .

Druga funkcja chronionego elementu członkowskiego zwraca wskaźnik do `CharType` docelowego zakresu znaków typu używanego przez ustawienia regionalne przekonwertowane ze znaków macierzystych typu **char**.

### <a name="remarks"></a>Uwagi

Druga funkcja chronionego szablonu `dest` `I`elementu członkowskiego `do_widen` `first`przechowuje w [ ] wartość ( [ `I`]), dla `I` w interwale [0, `last`  -  `first`).

### <a name="example"></a>Przykład

Zobacz przykład [widen](#widen), `do_widen`który wywołuje .

## <a name="ctypeis"></a><a name="is"></a>ctype::jest

Sprawdza, czy pojedynczy znak ma określony atrybut lub klasyfikuje atrybuty każdego znaku w zakresie i przechowuje je w tablicy.

```cpp
bool is(mask maskVal, CharType ch) const;

const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parametry

*maskVal*\
Wartość maski, dla której znak ma być testowany.

*Ch*\
Znak, którego atrybuty mają być testowane.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie, którego atrybuty mają być klasyfikowane.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie, którego atrybuty mają być klasyfikowane.

*Dest*\
Wskaźnik do początku tablicy, w którym mają być przechowywane wartości maski charakteryzujące atrybuty każdego ze znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca **wartość true,** jeśli testowany znak ma atrybut opisany przez wartość maski; **false,** jeśli nie ma atrybutu.

Funkcja drugiego elementu członkowskiego zwraca wskaźnik do ostatniego znaku w zakresie, którego atrybuty mają zostać sklasyfikowane.

### <a name="remarks"></a>Uwagi

Wartości maski klasyfikujące atrybuty znaków są dostarczane przez klasę [ctype_base Class](../standard-library/ctype-base-class.md), z której pochodzi ctype. Funkcja pierwszego elementu członkowskiego może akceptować wyrażenia dla swojego pierwszego parametru, nazywanego maskami bitowymi i utworzona z kombinacji wartości maski przez logiczne operatory bitowe (&#124; , & ^ , ~).

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

## <a name="ctypenarrow"></a><a name="narrow"></a>ctype::wąski

Konwertuje znaki `CharType` typu używane przez ustawienia regionalne na odpowiednie znaki **typu char** w natywnym zestawie znaków.

```cpp
char narrow(CharType ch, char default = '\0') const;

const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak typu `Chartype` używanego przez ustawienia regionalne do konwersji.

*Domyślny*\
Wartość domyślna, która ma być przypisana `CharType` przez funkcję elementu członkowskiego do znaków typu, które nie mają znaków odpowiednika typu **char**.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie znaków do konwersji.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków do konwersji.

*Dest*\
Wskaźnik const do pierwszego znaku typu **char** w zakresie docelowym, który przechowuje przekonwertowany zakres znaków.

### <a name="return-value"></a>Wartość zwracana

Funkcja pierwszego elementu członkowskiego zwraca znak macierzysty **typu char,** `CharType default` który odpowiada znakowi parametru typu, jeśli nie jest zdefiniowany odpowiednik.

Funkcja drugiego elementu członkowskiego zwraca wskaźnik do docelowego zakresu znaków `CharType`natywnych przekonwertowanych ze znaków typu .

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu [do_narrow](#do_narrow)członkowskiego zwraca`ch`do_narrow `default`( , ). Funkcja drugiego elementu [do_narrow](#do_narrow) członkowskiego zwraca`first`do_narrow `last` `default`( `dest`, , , . Tylko podstawowe znaki źródłowe są gwarantowane, `CharType` `narrow`aby mieć unikalny obraz odwrotny w obszarze . Dla tych podstawowych znaków źródłowych następujące `narrow` niezmienne blokady: ( [widen](#widen) ( **c** ), 0 ) == **c**.

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

## <a name="ctypescan_is"></a><a name="scan_is"></a>ctype::scan_is

Lokalizuje pierwszy znak w zakresie, który pasuje do określonej maski.

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal*\
Wartość maski, która ma być dopasowana przez znak.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie, który ma być skanowany.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie, który ma być skanowany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego znaku w zakresie, który pasuje do określonej maski. Jeśli taka wartość nie istnieje, funkcja zwraca *ostatni*plik .

### <a name="remarks"></a>Uwagi

Funkcja elementu [do_scan_is](#do_scan_is)członkowskiego zwraca`maskVal`do_scan_is `first` `last`( , , ).

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

## <a name="ctypescan_not"></a><a name="scan_not"></a>ctype::scan_not

Lokalizuje pierwszy znak w zakresie, który nie pasuje do określonej maski.

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal*\
Wartość maski, która nie ma być dopasowywała się do znaku.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie, który ma być skanowany.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie, który ma być skanowany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego znaku w zakresie, który nie pasuje do określonej maski. Jeśli taka wartość nie istnieje, funkcja zwraca *ostatni*plik .

### <a name="remarks"></a>Uwagi

Funkcja elementu [do_scan_not](#do_scan_not)członkowskiego zwraca do_scan_not`maskVal` `first`( `last`, , ).

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

## <a name="ctypetolower"></a><a name="tolower"></a>ctype::tolower

Konwertuje znak lub zakres znaków na małe litery.

```cpp
CharType tolower(CharType ch) const;

const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, który ma zostać przekonwertowany na małe litery.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie znaków, których sprawy mają zostać przekonwertowane.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków, których sprawy mają zostać przekonwertowane.

### <a name="return-value"></a>Wartość zwracana

Funkcja pierwszego elementu członkowskiego zwraca formularz małych liter parametru *ch*. Jeśli formularz małych liter nie istnieje, zwraca on *go*.

Druga funkcja elementu członkowskiego zwraca *ostatni*plik .

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu [do_tolower](#do_tolower)członkowskiego zwraca`ch`do_tolower ( ). Funkcja drugiego elementu [do_tolower](#do_tolower)członkowskiego zwraca`first`do_tolower `last`( , ).

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

## <a name="ctypetoupper"></a><a name="toupper"></a>ctype::toupper

Konwertuje znak lub zakres znaków na wielkie litery.

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, który ma zostać przekonwertowany na wielkie litery.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie znaków, których sprawy mają zostać przekonwertowane.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków, których sprawy mają zostać przekonwertowane.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca wielką literę parametru *ch*. Jeśli formularz nie istnieje, zwraca on *ch*.

Druga funkcja elementu członkowskiego zwraca *ostatni*plik .

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu [do_toupper](#do_toupper)członkowskiego zwraca`ch`do_toupper ( ). Funkcja drugiego elementu członkowskiego zwraca `first` `last` [do_toupper](#do_toupper)( , ).

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

## <a name="ctypewiden"></a><a name="widen"></a>ctype::widen

Konwertuje znak **typu char** w natywnym zestawie `CharType` znaków na odpowiedni znak typu używanego przez ustawienia regionalne.

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>Parametry

*Bajtów*\
Znak typu char w natywnym zestawie znaków do konwersji.

*Pierwszym*\
Wskaźnik do pierwszego znaku w zakresie znaków do konwersji.

*Ostatnio*\
Wskaźnik do znaku bezpośrednio po ostatnim znaku w zakresie znaków do konwersji.

*Dest*\
Wskaźnik do pierwszego znaku `CharType` typu w zakresie docelowym, który przechowuje przekonwertowany zakres znaków.

### <a name="return-value"></a>Wartość zwracana

Funkcja pierwszego elementu członkowskiego zwraca `CharType` znak typu odpowiadający znakowi parametru **znaku**typu macierzystego .

Funkcja drugiego elementu członkowskiego zwraca wskaźnik do docelowego zakresu znaków typu `CharType` używanego przez ustawienia regionalne przekonwertowane ze znaków macierzystych typu **char**.

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu [do_widen](#do_widen)członkowskiego zwraca`byte`do_widen ( ). Funkcja drugiego elementu [do_widen](#do_widen)członkowskiego zwraca`first`do_widen `last` `dest`( , , ).

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

[\<>ustawień regionalnych](../standard-library/locale.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
