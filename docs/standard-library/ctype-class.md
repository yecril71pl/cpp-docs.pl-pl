---
title: CType — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a65008b01262ad6252e9942444a4e80602d4292
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208640"
---
# <a name="ctype-class"></a>ctype — Klasa

Klasa zawierająca zestaw reguł, który służy do klasyfikowania znaków, konwersji z wielkich i małych liter i konwersji między macierzystym zestawem znaków i zestawem używanym przez ustawienia regionalne.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>Parametry

*CharType* typ używany w programie do kodowania znaków.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba dostępu do jego przechowywanej wartości przechowuje unikatową wartość dodatnią w `id`. Do kryteriów klasyfikacji jest dostarczany typ zagnieżdżonej maski bitów w klasie bazowej ctype_base.

Standardowa biblioteka C++ definiuje dwie jawne specjalizacje tej klasy szablonu:

- [CType](../standard-library/ctype-char-class.md)< `char`>, jawna specjalizacja, której różnice są opisane osobno.

- **CType**<`wchar_t`>, który traktuje elementy jako znaki dwubajtowe.

Pozostałe specjalizacje szablonu klasy **ctype** \< **CharType**>:

- Konwertowanie wartości ***ch*** typu `CharType` na wartość typu **char** z wyrażeniem (`char`) **ch**.

- Konwertowanie wartości ***bajtów*** typu **char** na wartość typu `CharType` z wyrażeniem **CharType** (**bajtów**).

Wszystkie inne operacje są wykonywane na **char** wartości w taki sam sposób jak w przypadku jawnej specjalizacji **ctype**<`char`>.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[ctype](#ctype)|Konstruktor dla obiektów klasy `ctype` które służą jako zestawy reguł ustawień regionalnych dla znaków.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ, który opisuje znak używany przez ustawienie regionalne.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[do_is](#do_is)|Funkcja wirtualna wywoływana w celu sprawdzenia, czy pojedynczy znak ma określony atrybut, lub sklasyfikowania atrybutów każdego znaku w zakresie i przechowywania ich w tablicy.|
|[do_narrow](#do_narrow)|Funkcja wirtualna wywoływana w celu konwersji znaku typu `CharType` używany przez ustawienie regionalne do odpowiedniego znaku typu **char** w macierzystym znaków.|
|[do_scan_is](#do_scan_is)|Wirtualna funkcja wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który pasuje do określonej maski.|
|[do_scan_not](#do_scan_not)|Funkcja wirtualna wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który nie pasuje do określonej maski.|
|[do_tolower](#do_tolower)|Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na ich małe litery.|
|[do_toupper](#do_toupper)|Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na ich wielkie litery.|
|[do_widen](#do_widen)|Funkcja wirtualna wywoływana w celu konwertuje znak typu **char** w macierzystym zestawie znaków do odpowiedniego znaku typu `CharType` używany przez ustawienie regionalne.|
|[is](#is)|Sprawdza, czy pojedynczy znak ma określony atrybut, lub klasyfikuje atrybuty każdego znaku w zakresie i przechowuje je w tablicy.|
|[Zawęź](#narrow)|Konwertuje znak typu `CharType` używany przez ustawienie regionalne do odpowiedniego znaku typu char w macierzystym zestawem znaków.|
|[scan_is](#scan_is)|Lokalizuje pierwszy znak w zakresie, który pasuje do określonej maski.|
|[scan_not](#scan_not)|Lokalizuje pierwszy znak w zakresie, który nie pasuje do określonej maski.|
|[tolower](#tolower)|Konwertuje znak lub zakres znaków na małe litery.|
|[toupper](#toupper)|Konwertuje znak lub zakres znaków na wielkie litery.|
|[widen](#widen)|Konwertuje znak typu **char** w macierzystym zestawie znaków do odpowiedniego znaku typu `CharType` używany przez ustawienie regionalne.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="char_type"></a>  CType::char_type

Typ, który opisuje znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *CharType*.

### <a name="example"></a>Przykład

Zobacz opis funkcji elementu członkowskiego [mogą zostać poszerzone](#widen) przykład, który używa `char_type` jako wartości zwracanej.

## <a name="ctype"></a>  CType::CType

Konstruktor dla obiektów klasy ctype, które służą jako zestawy reguł ustawień regionalnych dla znaków.

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs* wartość całkowitą, można określić typ zarządzania pamięci dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* parametrów i ich znaczenie są:

- 0: okres istnienia obiektu jest zarządzany przez ustawienia regionalne, zawierających go.

- 1: okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: nie zdefiniowano tych wartości.

Żadnych przykładów bezpośrednie są to tylko możliwe, ponieważ destruktor jest chroniony.

Konstruktor inicjuje jego `locale::facet` podstawowego obiektu z **locale::**[aspekt](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="do_is"></a>  CType::do_is

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

*maskVal* wartość maski, dla którego ma zostać przetestowana znak.

*ch* znaku, w których atrybuty są badane.

*pierwszy* wskaźnik do pierwszego znaku w zakresie, w których atrybuty, które mają być klasyfikowane.

*ostatni* wskaźnik do znaku zaraz po ostatnim znakiem z zakresu, w których atrybuty, które mają być klasyfikowane.

*dest* wskaźnik do początku tablicy, gdzie mają być przechowywane wartości maski charakteryzujące atrybuty znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca wartość logiczną, która jest **true** Jeśli znak przetestowane ma atrybut, który został opisany przez wartość maski; **false** Jeżeli nie ma atrybutu.

Druga funkcja elementu członkowskiego zwraca tablicę zawierającą wartości maski charakteryzujące atrybuty wszystkich znaków w zakresie.

### <a name="remarks"></a>Uwagi

Wartości maski klasyfikowania atrybutów znaki są dostarczane przez klasy [ctype_base](../standard-library/ctype-base-class.md), z których ctype pochodzi. Pierwsza funkcja elementu członkowskiego może akceptować wyrażenia jako pierwszy parametr określa się jako masek bitowych i tworzony na podstawie kombinacji wartości maski przez operatory logiczne bitowe (&#124; &, ^, ~).

### <a name="example"></a>Przykład

Zobacz przykład [jest](#is), która wywołuje metodę `do_is`.

## <a name="do_narrow"></a>  CType::do_narrow

Funkcja wirtualna wywoływana w celu konwersji znaku typu `CharType` używany przez ustawienie regionalne do odpowiedniego znaku typu **char** w macierzystym znaków.

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

*ch* znaku typu `Chartype` używane przez ustawienia regionalne do skonwertowania.

*domyślne* wartość domyślna ma zostać przypisany przez funkcję elementu członkowskiego, aby znaki typu `CharType` nie mają odpowiednika znaki typu **char**.

*pierwszy* wskaźnik do pierwszego znaku w zakresie znaków ma zostać przekonwertowany.

*ostatni* wskaźnik do znaku zaraz po ostatnim znakiem z zakresu znaków, które ma zostać przekonwertowany.

*dest* wskaźnika elementu const do pierwszego znaku typu **char** w zakresie docelowym, który przechowuje przekonwertowanego zakres znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja chronionego elementu członkowskiego zwraca natywnych znaku typu CHAR, który odpowiada znakowi parametr typu `CharType` lub *domyślne* Jeśli nie zdefiniowano odpowiednika.

Druga funkcja chronionego elementu członkowskiego zwraca wskaźnik do zakresu docelowego, natywne znaków, znaków typu `CharType`.

### <a name="remarks"></a>Uwagi

Drugi chronionego elementu członkowskiego szablonu funkcji sklepów w `dest`[ `I`] wartość `do_narrow`( `first` [ `I`], `default`), aby uzyskać `I` w interwale [0, `last`  -  `first`).

### <a name="example"></a>Przykład

Zobacz przykład [zawęzić](#narrow), która wywołuje metodę `do_narrow`.

## <a name="do_scan_is"></a>  CType::do_scan_is

Wirtualna funkcja wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który pasuje do określonej maski.

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal* wartość maski mają być dopasowywane o znak.

*pierwszy* wskaźnik do pierwszego znaku w zakresie do przeskanowania.

*ostatni* wskaźnik do znaku zaraz po ostatni znak w zakresie do skanowania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego znaku w zakresie, który pasuje do określonej maski. Jeśli takie wartość nie istnieje, funkcja zwraca *ostatniego*.

### <a name="remarks"></a>Uwagi

Chroniona funkcja elementu członkowskiego zwraca najmniejszy wskaźnik `ptr` w zakresie [ `first`, `last`) dla której [do_is —](#do_is)( `maskVal`, \* `ptr`) ma wartość true.

### <a name="example"></a>Przykład

Zobacz przykład [scan_is —](#scan_is), która wywołuje metodę `do_scan_is`.

## <a name="do_scan_not"></a>  CType::do_scan_not

Funkcja wirtualna wywoływana w celu zlokalizowania pierwszego znaku w zakresie, który nie pasuje do określonej maski.

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal* wartość maski nie mają być dopasowywane znak.

*pierwszy* wskaźnik do pierwszego znaku w zakresie do przeskanowania.

*ostatni* wskaźnik do znaku zaraz po ostatni znak w zakresie do skanowania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego znaku w zakresie, który nie pasuje do określonej maski. Jeśli takie wartość nie istnieje, funkcja zwraca *ostatniego*.

### <a name="remarks"></a>Uwagi

Chroniona funkcja elementu członkowskiego zwraca najmniejszy wskaźnik `ptr` w zakresie [ `first`, `last`) dla której [do_is —](#do_is)( `maskVal`, \* `ptr`) ma wartość false.

### <a name="example"></a>Przykład

Zobacz przykład [scan_not —](#scan_not), która wywołuje metodę `do_scan_not`.

## <a name="do_tolower"></a>  CType::do_tolower

Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na małe litery.

```cpp
virtual CharType do_tolower(CharType ch) const;


virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch* znak, który ma zostać przekonwertowany na małe litery.

*pierwszy* wskaźnik do pierwszego znaku w zakresie znaków, w których przypadki są ma zostać przekonwertowany.

*ostatni* wskaźnik do znaku zaraz po ostatnim znakiem z zakresu znaków, w których przypadki są ma zostać przekonwertowany.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja chronionego elementu członkowskiego zwraca małe formularza parametru *ch*. Jeśli żadna z form małe istnieje, zwraca *ch*. Drugi chroniony element członkowski funkcja zwraca *ostatniego*.

### <a name="remarks"></a>Uwagi

Druga funkcja szablonu chroniony element członkowski zastępuje każdy element `first` [ `I`], aby uzyskać `I` w interwale [0, `last`  -  `first`), za pomocą `do_tolower`( `first` [ `I`]).

### <a name="example"></a>Przykład

Zobacz przykład [tolower](#tolower), która wywołuje metodę `do_tolower`.

## <a name="do_toupper"></a>  CType::do_toupper

Funkcja wirtualna wywoływana w celu konwersji znaku lub zakresu znaków na ich wielkie litery.

```cpp
virtual CharType do_toupper(CharType ch) const;


virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch* znak, który ma zostać przekonwertowany na wielkie litery.

*pierwszy* wskaźnik do pierwszego znaku w zakresie znaków, w których przypadki są ma zostać przekonwertowany.

*ostatni* wskaźnik do znaku zaraz po ostatnim znakiem z zakresu znaków, w których przypadki są ma zostać przekonwertowany.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja chronionego elementu członkowskiego zwraca wielkich liter parametru *ch*. Jeśli istnieje nie wielkich liter, zwraca *ch*. Drugi chroniony element członkowski funkcja zwraca *ostatniego*.

### <a name="remarks"></a>Uwagi

Druga funkcja szablonu chroniony element członkowski zastępuje każdy element `first` [ `I`], aby uzyskać `I` w interwale [0, `last`  -  `first`), za pomocą `do_toupper`( `first` [ `I`]).

### <a name="example"></a>Przykład

Zobacz przykład [toupper](#toupper), która wywołuje metodę `do_toupper`.

## <a name="do_widen"></a>  CType::do_widen

Funkcja wirtualna wywoływana w celu konwertuje znak typu **char** w macierzystym zestawie znaków do odpowiedniego znaku typu `CharType` używany przez ustawienie regionalne.

```cpp
virtual CharType do_widen(char byte) const;


virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>Parametry

*Bajt* znaku typu **char** w macierzystym zestawie znaków do skonwertowania.

*pierwszy* wskaźnik do pierwszego znaku w zakresie znaków ma zostać przekonwertowany.

*ostatni* wskaźnik do znaku zaraz po ostatnim znakiem z zakresu znaków, które ma zostać przekonwertowany.

*dest* wskaźnik do pierwszego znaku typu `CharType` w zakresie docelowym, który przechowuje przekonwertowanego zakres znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja chronionego elementu członkowskiego zwraca znak typu `CharType` , który odpowiada znakowi parametr typu natywnego **char**.

Druga funkcja chronionego elementu członkowskiego zwraca wskaźnik do zakresu docelowego znaków typu `CharType` używany przez ustawienie regionalne natywnych znaków typu **char**.

### <a name="remarks"></a>Uwagi

Drugi chronionego elementu członkowskiego szablonu funkcji sklepów w `dest`[ `I`] wartość `do_widen`( `first`[ `I`]), aby uzyskać `I` w interwale [0, `last`  -  `first`).

### <a name="example"></a>Przykład

Zobacz przykład [mogą zostać poszerzone](#widen), która wywołuje metodę `do_widen`.

## <a name="is"></a>  CType::is

Sprawdza, czy pojedynczy znak ma określony atrybut lub klasyfikuje atrybuty każdego znaku w zakresie i przechowuje je w tablicy.

```cpp
bool is(mask maskVal, CharType ch) const;


const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parametry

*maskVal* wartość maski, dla którego ma zostać przetestowana znak.

*ch* znaku, w których atrybuty są badane.

*pierwszy* wskaźnik do pierwszego znaku w zakresie, w których atrybuty, które mają być klasyfikowane.

*ostatni* wskaźnik do znaku zaraz po ostatnim znakiem z zakresu, w których atrybuty, które mają być klasyfikowane.

*dest* wskaźnik do początku tablicy, gdzie mają być przechowywane wartości maski charakteryzujące atrybuty znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca **true** Jeśli znak przetestowane ma atrybut, który został opisany przez wartość maski; **false** Jeżeli nie ma atrybutu.

Druga funkcja elementu członkowskiego zwraca wskaźnik do ostatniego znaku w zakresie, w których atrybuty, które mają być klasyfikowane.

### <a name="remarks"></a>Uwagi

Wartości maski klasyfikowania atrybutów znaki są dostarczane przez klasy [ctype_base — klasa](../standard-library/ctype-base-class.md), z których ctype pochodzi. Pierwsza funkcja elementu członkowskiego może akceptować wyrażenia jako pierwszy parametr określa się jako masek bitowych i tworzony na podstawie kombinacji wartości maski przez operatory logiczne bitowe (&#124; &, ^, ~).

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

## <a name="narrow"></a>  CType::Narrow

Konwertuje znaki typu `CharType` używany przez ustawienie regionalne do odpowiedniego znaki typu **char** w macierzystym znaków.

```cpp
char narrow(CharType ch, char default = '\0') const;


const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parametry

*ch* znaku typu `Chartype` używane przez ustawienia regionalne do skonwertowania.

*domyślne* wartość domyślna ma zostać przypisany przez funkcję elementu członkowskiego, aby znaki typu `CharType` nie mają odpowiednika znaki typu **char**.

*pierwszy* wskaźnik do pierwszego znaku w zakresie znaków ma zostać przekonwertowany.

*ostatni* wskaźnik do znaku zaraz po ostatnim znakiem z zakresu znaków, które ma zostać przekonwertowany.

*dest* wskaźnika elementu const do pierwszego znaku typu **char** w zakresie docelowym, który przechowuje przekonwertowanego zakres znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca znak natywnego typu **char** , który odpowiada znakowi parametr typu `CharType default` Jeśli odpowiednika nie został zdefiniowany.

Druga funkcja elementu członkowskiego zwraca wskaźnik do zakresu docelowego, natywne znaków, znaków typu `CharType`.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca [do_narrow —](#do_narrow)(`ch`, `default`). Druga funkcja elementu członkowskiego zwraca [do_narrow —](#do_narrow) (`first`, `last`, `default`, `dest`). Tylko znaków podstawowego źródła są musi mieć unikatowy obraz odwrotność `CharType` w obszarze `narrow`. Tych znaków podstawowego źródła, zawiera następujące niezmiennej: `narrow` ( [mogą zostać poszerzone](#widen) ( **c** ), 0) == **c**.

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

## <a name="scan_is"></a>  CType::scan_is

Lokalizuje pierwszy znak w zakresie, który pasuje do określonej maski.

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal* wartość maski mają być dopasowywane o znak.

*pierwszy* wskaźnik do pierwszego znaku w zakresie do przeskanowania.

*ostatni* wskaźnik do znaku zaraz po ostatni znak w zakresie do skanowania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego znaku w zakresie, który pasuje do określonej maski. Jeśli takie wartość nie istnieje, funkcja zwraca *ostatniego*.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_scan_is —](#do_scan_is)(`maskVal`, `first`, `last`).

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

## <a name="scan_not"></a>  CType::scan_not

Lokalizuje pierwszy znak w zakresie, który nie pasuje do określonej maski.

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal* wartość maski nie mają być dopasowywane znak.

*pierwszy* wskaźnik do pierwszego znaku w zakresie do przeskanowania.

*ostatni* wskaźnik do znaku zaraz po ostatni znak w zakresie do skanowania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego znaku w zakresie, który nie pasuje do określonej maski. Jeśli takie wartość nie istnieje, funkcja zwraca *ostatniego*.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_scan_not —](#do_scan_not)(`maskVal`, `first`, `last`).

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

## <a name="tolower"></a>  CType::tolower

Konwertuje znak lub zakres znaków na małe litery.

```cpp
CharType tolower(CharType ch) const;


const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch* znak, który ma zostać przekonwertowany na małe litery.

*pierwszy* wskaźnik do pierwszego znaku w zakresie znaków, w których przypadki są ma zostać przekonwertowany.

*ostatni* wskaźnik do znaku zaraz po ostatnim znakiem z zakresu znaków, w których przypadki są ma zostać przekonwertowany.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca małe formularza parametru *ch*. Jeśli żadna z form małe istnieje, zwraca *ch*.

Druga funkcja elementu członkowskiego zwraca *ostatniego*.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca [do_tolower —](#do_tolower)(`ch`). Druga funkcja elementu członkowskiego zwraca [do_tolower —](#do_tolower)(`first`, `last`).

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

## <a name="toupper"></a>  CType::toupper

Konwertuje znak lub zakres znaków na wielkie litery.

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch* znak, który ma zostać przekonwertowany na wielkie litery.

*pierwszy* wskaźnik do pierwszego znaku w zakresie znaków, w których przypadki są ma zostać przekonwertowany.

*ostatni* wskaźnik do znaku zaraz po ostatnim znakiem z zakresu znaków, w których przypadki są ma zostać przekonwertowany.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca wielkich liter parametru *ch*. Jeśli istnieje nie wielkich liter, zwraca *ch*.

Druga funkcja elementu członkowskiego zwraca *ostatniego*.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca [do_toupper —](#do_toupper)(`ch`). Druga funkcja elementu członkowskiego zwraca [do_toupper —](#do_toupper)( `first`, `last`).

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

## <a name="widen"></a>  CType::widen

Konwertuje znak typu **char** w macierzystym zestawie znaków do odpowiedniego znaku typu `CharType` używany przez ustawienie regionalne.

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>Parametry

*Bajt* zestaw znaków typu CHAR w macierzystym znaków ma zostać przekonwertowany.

*pierwszy* wskaźnik do pierwszego znaku w zakresie znaków ma zostać przekonwertowany.

*ostatni* wskaźnik do znaku zaraz po ostatnim znakiem z zakresu znaków, które ma zostać przekonwertowany.

*dest* wskaźnik do pierwszego znaku typu `CharType` w zakresie docelowym, który przechowuje przekonwertowanego zakres znaków.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca znak typu `CharType` , który odpowiada znakowi parametr typu natywnego **char**.

Druga funkcja elementu członkowskiego zwraca wskaźnik do zakresu docelowego znaków typu `CharType` używany przez ustawienie regionalne natywnych znaków typu **char**.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca [do_widen —](#do_widen)(`byte`). Druga funkcja elementu członkowskiego zwraca [do_widen —](#do_widen)(`first`, `last`, `dest`).

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

## <a name="see-also"></a>Zobacz także

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
