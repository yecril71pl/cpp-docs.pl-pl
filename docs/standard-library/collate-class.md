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
ms.openlocfilehash: f05c2e9482f8a0bada3868fdc946d4d26a0e0e1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371926"
---
# <a name="collate-class"></a>collate — Klasa

Szablon klasy, który opisuje obiekt, który może służyć jako aspekt ustawień regionalnych do kontrolowania kolejności i grupowania znaków w ciągu, porównania między nimi i mieszania ciągów.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ używany w programie do kodowania znaków.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba uzyskania dostępu do przechowywanej wartości `id`przechowuje unikatową wartość dodatnią w programie . W przypadku niektórych języków znaki są grupowane i traktowane jak pojedynczy znak, a w innych, pojedyncze znaki są traktowane tak, jakby były dwoma znakami. Usługi sortowania dostarczane przez klasę collate umożliwiają sortowanie w tych przypadkach.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Collate](#collate)|Konstruktor dla obiektów `collate` klasy, który służy jako aspekt ustawień regionalnych do obsługi konwencji sortowania ciągów.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ opisujący znak typu `CharType`.|
|[string_type](#string_type)|Typ opisujący ciąg typu `basic_string` zawierający znaki `CharType`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Porównać](#compare)|Porównuje dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.|
|[do_compare](#do_compare)|Funkcja wirtualna porównująca dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.|
|[do_hash](#do_hash)|Funkcja wirtualna wywoływana w celu określenia wartości mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.|
|[do_transform](#do_transform)|Funkcja wirtualna wywoływana w celu konwersji sekwencji znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.|
|[Mieszania](#hash)|Określa wartość mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.|
|[Przekształcić](#transform)|Konwertuje sekwencję znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ustawień regionalnych

**Przestrzeń nazw:** std

## <a name="collatechar_type"></a><a name="char_type"></a>sortować::char_type

Typ opisujący znak typu `CharType`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `CharType`szablonu .

## <a name="collatecollate"></a><a name="collate"></a>sortowanie::sortowanie

Konstruktor dla obiektów klasy sortowania, który służy jako aspekt ustawień regionalnych do obsługi konwencji sortowania ciągów.

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

*_refs*\
Wartość całkowita używana do określania typu zarządzania pamięcią dla obiektu.

*_Locname*\
Nazwa ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* i ich znaczenie to:

- 0: Okres istnienia obiektu jest zarządzany przez ustawienia regionalne, które go zawierają.

- 1: Okres istnienia obiektu musi być zarządzany ręcznie.

- \>1: Te wartości nie są zdefiniowane.

Konstruktor inicjuje swój obiekt bazowy`_Refs`za pomocą **ustawień regionalnych::**[aspekt](../standard-library/locale-class.md#facet_class)( ).

## <a name="collatecompare"></a><a name="compare"></a>sortowanie::porównanie

Porównuje dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametry

*po pierwsze1*\
Wskaźnik do pierwszego elementu w pierwszej sekwencji do porównania.

*ostatni1*\
Wskaźnik do ostatniego elementu w pierwszej sekwencji do porównania.

*pierwszy2*\
Wskaźnik do pierwszego elementu w drugiej sekwencji do porównania.

*ostatni2*\
Wskaźnik do ostatniego elementu w drugiej sekwencji do porównania.

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca:

- -1, jeśli pierwsza sekwencja porównuje mniej niż druga sekwencja.

- +1, jeśli druga sekwencja porównuje mniej niż pierwsza sekwencja.

- 0, jeśli sekwencje są równoważne.

### <a name="remarks"></a>Uwagi

Pierwsza sekwencja porównuje mniej, jeśli ma mniejszy element w najwcześniejszej pary nierównej w sekwencjach lub, jeśli nie istnieją nierówne pary, ale pierwsza sekwencja jest krótsza.

Funkcja elementu [do_compare](#do_compare)członkowskiego zwraca `first1`do_compare `last1` `first2`( `last2`, , , ).

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

## <a name="collatedo_compare"></a><a name="do_compare"></a>sortować::do_compare

Funkcja wirtualna porównująca dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametry

*po pierwsze1*\
Wskaźnik do pierwszego elementu w pierwszej sekwencji do porównania.

*ostatni1*\
Wskaźnik do ostatniego elementu w pierwszej sekwencji do porównania.

*pierwszy2*\
Wskaźnik do pierwszego elementu w drugiej sekwencji do porównania.

*ostatni2*\
Wskaźnik do ostatniego elementu w drugiej sekwencji do porównania.

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca:

- -1, jeśli pierwsza sekwencja porównuje mniej niż druga sekwencja.

- +1, jeśli druga sekwencja porównuje mniej niż pierwsza sekwencja.

- 0, jeśli sekwencje są równoważne.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualnego elementu członkowskiego porównuje sekwencję w [ * first1, Last1)* z sekwencją w *[ first2, last2*). Porównuje wartości, `operator<` stosując między parami odpowiednich elementów typu `CharType`. Pierwsza sekwencja porównuje mniej, jeśli ma mniejszy element w najwcześniejszej pary nierównej w sekwencjach lub jeśli nie istnieją żadne nierówne pary, ale pierwsza sekwencja jest krótsza.

### <a name="example"></a>Przykład

Zobacz przykład [zestawienia::porównaj](#compare), `do_compare`który wywołuje .

## <a name="collatedo_hash"></a><a name="do_hash"></a>sortować::do_hash

Funkcja wirtualna wywoływana w celu określenia wartości mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Wskaźnik do pierwszego znaku w sekwencji, którego ma wartość ma być określona.

*Ostatnio*\
Wskaźnik do ostatniego znaku w sekwencji, którego ma wartość ma być określona.

### <a name="return-value"></a>Wartość zwracana

Wartość mieszania typu **long** dla sekwencji.

### <a name="remarks"></a>Uwagi

Wartość mieszania może być przydatna, na przykład w dystrybucji sekwencji pseudolosowo w tablicy list.

### <a name="example"></a>Przykład

Zobacz przykład [skrótu](#hash), `do_hash`który wywołuje .

## <a name="collatedo_transform"></a><a name="do_transform"></a>sortate::do_transform

Funkcja wirtualna wywoływana w celu konwersji sekwencji znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Wskaźnik do pierwszego znaku w sekwencji, która ma zostać przekonwertowana.

*Ostatnio*\
Wskaźnik do ostatniego znaku w sekwencji do konwersji.

### <a name="return-value"></a>Wartość zwracana

Ciąg, który jest przekształconą sekwencją znaków.

### <a name="remarks"></a>Uwagi

Funkcja chronionego wirtualnego elementu członkowskiego zwraca obiekt klasy [string_type](#string_type) której kontrolowana `first` `last`sekwencja jest kopią sekwencji [ , ). Jeśli klasa pochodząca z\< sortowania **CharType**> zastępuje [do_compare](#do_compare), należy również `do_transform` zastąpić dopasowywać. Po przekazaniu do `collate::compare`, dwa przekształcone ciągi powinny przynieść taki sam wynik, który można uzyskać od przekazywania nietransformowanych ciągów do porównania w klasie pochodnej.

### <a name="example"></a>Przykład

Zobacz przykład [przekształcania](#transform), `do_transform`który wywołuje .

## <a name="collatehash"></a><a name="hash"></a>sortowanie::hash

Określa wartość mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Wskaźnik do pierwszego znaku w sekwencji, którego ma wartość ma być określona.

*Ostatnio*\
Wskaźnik do ostatniego znaku w sekwencji, którego ma wartość ma być określona.

### <a name="return-value"></a>Wartość zwracana

Wartość mieszania typu **long** dla sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja elementu [do_hash](#do_hash)członkowskiego zwraca do_hash `first` `last`( , ).

Wartość mieszania może być przydatna, na przykład w dystrybucji sekwencji pseudolosowo w tablicy list.

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

## <a name="collatestring_type"></a><a name="string_type"></a>sortować::string_type

Typ opisujący ciąg typu `basic_string` zawierający znaki `CharType`typu .

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizację szablonu klasy [basic_string](../standard-library/basic-string-class.md) którego obiekty mogą przechowywać kopie sekwencji źródłowej.

### <a name="example"></a>Przykład

Na przykład jak zadeklarować `string_type`i używać , zobacz [transform .](#transform)

## <a name="collatetransform"></a><a name="transform"></a>sortowanie::przekształcanie

Konwertuje sekwencję znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Wskaźnik do pierwszego znaku w sekwencji, która ma zostać przekonwertowana.

*Ostatnio*\
Wskaźnik do ostatniego znaku w sekwencji do konwersji.

### <a name="return-value"></a>Wartość zwracana

Ciąg, który zawiera sekwencję przekształconych znaków.

### <a name="remarks"></a>Uwagi

Funkcja elementu [do_transform](#do_transform)członkowskiego zwraca do_transform`first` `last`( , ).

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

## <a name="see-also"></a>Zobacz też

[\<>ustawień regionalnych](../standard-library/locale.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
