---
title: collate — Klasa
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate
- locale/std::collate::char_type
- locale/std::collate::string_type
- locale/std::collate::compare
- locale/std::collate::do_compare
- locale/std::collate::do_hash
- locale/std::collate::do_transform
- locale/std::collate::hash
- locale/std::collate::transform
helpviewer_keywords:
- std::collate [C++]
- std::collate [C++], char_type
- std::collate [C++], string_type
- std::collate [C++], compare
- std::collate [C++], do_compare
- std::collate [C++], do_hash
- std::collate [C++], do_transform
- std::collate [C++], hash
- std::collate [C++], transform
ms.assetid: 92168798-9628-4a2e-be6e-fa62dcd4d6a6
ms.openlocfilehash: 88b04ad4f14faf4d152c0ce2b9c3477928263c52
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689812"
---
# <a name="collate-class"></a>collate — Klasa

Szablon klasy, który opisuje obiekt, który może stanowić zestaw reguł ustawień regionalnych w celu sterowania kolejnością i grupowaniem znaków w ciągu, porównania między nimi a mieszaniem ciągów.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>Parametry

@No__t_1 *CharType*
Typ używany w programie do kodowania znaków.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości przechowuje unikatową wartość dodatnią w `id`. W przypadku niektórych języków znaki są grupowane i traktowane jak pojedynczy znak, a w innych, pojedyncze znaki są traktowane tak, jakby były dwoma znakami. Usługi sortowania dostarczane przez klasę collate umożliwiają sortowanie w tych przypadkach.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[sortowan](#collate)|Konstruktor dla obiektów klasy `collate`, który służy jako zestaw reguł ustawień regionalnych do obsługi Konwencji sortowania ciągów.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ, który opisuje znak typu `CharType`.|
|[string_type](#string_type)|Typ, który opisuje ciąg typu `basic_string` zawierający znaki typu `CharType`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[porównaniu](#compare)|Porównuje dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.|
|[do_compare](#do_compare)|Funkcja wirtualna porównująca dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.|
|[do_hash](#do_hash)|Funkcja wirtualna wywoływana w celu określenia wartości mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.|
|[do_transform](#do_transform)|Funkcja wirtualna wywoływana w celu konwersji sekwencji znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.|
|[skrótu](#hash)|Określa wartość mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.|
|[przekształcania](#transform)|Konwertuje sekwencję znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<locale >

**Przestrzeń nazw:** std

## <a name="char_type"></a>COLLATE:: char_type

Typ, który opisuje znak typu `CharType`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `CharType`.

## <a name="collate"></a>COLLATE:: COLLATE

Konstruktor dla obiektów klasy COLLATE, który służy jako zestaw reguł ustawień regionalnych do obsługi Konwencji sortowania ciągów.

```cpp
public:
    explicit collate(
    size_t _Refs = 0);

protected:
    collate(
const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs* \
Wartość całkowita służąca do określania typu zarządzania pamięcią dla obiektu.

*_Locname* \
Nazwa ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie są następujące:

- 0: okres istnienia obiektu jest zarządzany przez elementy lokalne, które go zawierają.

- 1: okres istnienia obiektu musi być zarządzany ręcznie.

- \> 1: te wartości nie są zdefiniowane.

Konstruktor inicjuje swój obiekt podstawowy przy użyciu **ustawień regionalnych::** [facet](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="compare"></a>COLLATE:: Compare

Porównuje dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametry

*first1* \
Wskaźnik do pierwszego elementu w pierwszej sekwencji, który ma zostać porównany.

*last1* \
Wskaźnik do ostatniego elementu w pierwszej sekwencji, który ma zostać porównany.

*first2* \
Wskaźnik do pierwszego elementu w drugiej sekwencji, który ma zostać porównany.

*last2* \
Wskaźnik do ostatniego elementu w drugiej sekwencji, który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zwraca:

- -1, jeśli pierwsza sekwencja porównuje mniej niż drugą sekwencję.

- \+ 1, jeśli druga sekwencja porównuje mniej niż pierwszą sekwencję.

- 0, jeśli sekwencje są równoważne.

### <a name="remarks"></a>Uwagi

Pierwsza sekwencja porównuje mniej, jeśli ma mniejszego elementu w najwcześniejszym nierównej parze w sekwencjach lub, jeśli nie istnieją pary nierówne, ale pierwsza sekwencja jest krótsza.

Funkcja członkowska zwraca [do_compare](#do_compare)(`first1`, `last1`, `first2`, `last2`).

### <a name="example"></a>Przykład

```cpp
// collate_compare.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare ( s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result2 << endl;
}
```

## <a name="do_compare"></a>COLLATE::d o_compare

Funkcja wirtualna porównująca dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametry

*first1* \
Wskaźnik do pierwszego elementu w pierwszej sekwencji, który ma zostać porównany.

*last1* \
Wskaźnik do ostatniego elementu w pierwszej sekwencji, który ma zostać porównany.

*first2* \
Wskaźnik do pierwszego elementu w drugiej sekwencji, który ma zostać porównany.

*last2* \
Wskaźnik do ostatniego elementu w drugiej sekwencji, który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zwraca:

- -1, jeśli pierwsza sekwencja porównuje mniej niż drugą sekwencję.

- \+ 1, jeśli druga sekwencja porównuje mniej niż pierwszą sekwencję.

- 0, jeśli sekwencje są równoważne.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego porównuje sekwencję z [* FIRST1, Last1) * z sekwencją *[First2, last2*). Porównuje wartości poprzez zastosowanie `operator<` między parami odpowiednich elementów typu `CharType`. Pierwsza sekwencja porównuje mniej, jeśli ma mniejszy element w najwcześniejszym nierównej parze w sekwencjach lub jeśli nie ma żadnej nierównej pary, ale pierwsza sekwencja jest krótsza.

### <a name="example"></a>Przykład

Zobacz przykład dla [instrukcji COLLATE:: Compare](#compare), która wywołuje `do_compare`.

## <a name="do_hash"></a>COLLATE::d o_hash

Funkcja wirtualna wywoływana w celu określenia wartości mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*pierwszy* \
Wskaźnik do pierwszego znaku w sekwencji, którego wartość ma zostać określona.

*ostatni* \
Wskaźnik do ostatniego znaku w sekwencji, którego wartość ma zostać określona.

### <a name="return-value"></a>Wartość zwracana

Wartość skrótu typu **Long** dla sekwencji.

### <a name="remarks"></a>Uwagi

Wartość skrótu może być przydatna na przykład w przypadku dystrybuowania sekwencji pseudo-losowo w tablicy list.

### <a name="example"></a>Przykład

Zobacz przykład dla [skrótu](#hash), który wywołuje `do_hash`.

## <a name="do_transform"></a>COLLATE::d o_transform

Funkcja wirtualna wywoływana w celu konwersji sekwencji znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*pierwszy* \
Wskaźnik do pierwszego znaku w sekwencji do przekonwertowania.

*ostatni* \
Wskaźnik do ostatniego znaku w sekwencji do przekonwertowania.

### <a name="return-value"></a>Wartość zwracana

Ciąg, który jest przekształconą sekwencją znaków.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego zwraca obiekt klasy [string_type](#string_type) , której kontrolowana sekwencja jest kopią sekwencji [`first`, `last`). Jeśli klasa pochodna sortowania \< **chartype**> przesłania [do_compare](#do_compare), należy również przesłonić `do_transform` w celu dopasowania. Po przekazaniu do `collate::compare` dwa przekształcone ciągi powinny zwracać ten sam wynik, który można przekazać nieprzekształcone ciągi do porównania w klasie pochodnej.

### <a name="example"></a>Przykład

Zobacz przykład [transformacji](#transform), która wywołuje `do_transform`.

## <a name="hash"></a>COLLATE:: hash

Określa wartość mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*pierwszy* \
Wskaźnik do pierwszego znaku w sekwencji, którego wartość ma zostać określona.

*ostatni* \
Wskaźnik do ostatniego znaku w sekwencji, którego wartość ma zostać określona.

### <a name="return-value"></a>Wartość zwracana

Wartość skrótu typu **Long** dla sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_hash](#do_hash)(`first`, `last`).

Wartość skrótu może być przydatna na przykład w przypadku dystrybuowania sekwencji pseudo-losowo w tablicy list.

### <a name="example"></a>Przykład

```cpp
// collate_hash.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("\x00dfzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet
   _TCHAR * s2 = _T("zzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet

   long r1 = use_facet< collate<_TCHAR> > ( loc ).
      hash (s1, &s1[_tcslen( s1 )-1 ]);
   long r2 =  use_facet< collate<_TCHAR> > ( loc ).
      hash (s2, &s2[_tcslen( s2 )-1 ] );
   cout << r1 << " " << r2 << endl;
}
```

```Output
541187293 551279837
```

## <a name="string_type"></a>COLLATE:: string_type

Typ, który opisuje ciąg typu `basic_string` zawierający znaki typu `CharType`.

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) , którego obiekty mogą przechowywać kopie sekwencji źródłowej.

### <a name="example"></a>Przykład

Przykład sposobu deklarowania i używania `string_type` można znaleźć w temacie [Transform](#transform).

## <a name="transform"></a>COLLATE:: Transform

Konwertuje sekwencję znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*pierwszy* \
Wskaźnik do pierwszego znaku w sekwencji do przekonwertowania.

*ostatni* \
Wskaźnik do ostatniego znaku w sekwencji do przekonwertowania.

### <a name="return-value"></a>Wartość zwracana

Ciąg, który zawiera przekształconą sekwencję znaków.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_transform](#do_transform)(`first`, `last`).

### <a name="example"></a>Przykład

```cpp
// collate_transform.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   _TCHAR* s1 = _T("\x00dfzz abc.");
   // \x00df is the German sharp-s (looks like beta),
   // it comes before z in the alphabet
   _TCHAR* s2 = _T("zzz abc.");

   collate<_TCHAR>::string_type r1;   // OK for typedef
   r1 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s1, &s1[_tcslen( s1 )-1 ]);

   cout << r1 << endl;

   basic_string<_TCHAR> r2 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s2, &s2[_tcslen( s2 )-1 ]);

   cout << r2 << endl;

   int result1 = use_facet<collate<_TCHAR> > ( loc ).compare
      (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );

   cout << _tcscmp(r1.c_str( ),r2.c_str( )) << result1
      << _tcscmp(s1,s2) <<endl;
}
```

```Output

-1-11
```

## <a name="see-also"></a>Zobacz także

[\<locale >](../standard-library/locale.md) \
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
