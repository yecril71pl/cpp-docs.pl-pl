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
ms.openlocfilehash: 21d5825f8d9ea00359f2aa1c87291b831d1f330f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630116"
---
# <a name="collate-class"></a>collate — Klasa

Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych, aby kontrolować kolejność i grupowanie znaków w ciągu, porównania między nimi i mieszanie ciągów.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ używany w programie do kodowania znaków.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba dostępu do jego przechowywanej wartości przechowuje unikatową wartość dodatnią w `id`. W przypadku niektórych języków znaki są grupowane i traktowane jak pojedynczy znak, a w innych, pojedyncze znaki są traktowane tak, jakby były dwoma znakami. Usługi sortowania dostarczane przez klasę collate umożliwiają sortowanie w tych przypadkach.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[COLLATE](#collate)|Konstruktor dla obiektów klasy `collate` służy jako zestaw reguł ustawień regionalnych do obsługi konwencji sortowania ciągów.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ, który opisuje znak typu `CharType`.|
|[string_type](#string_type)|Typ, który opisuje ciąg typu `basic_string` zawierający znaki typu `CharType`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Porównanie](#compare)|Porównuje dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.|
|[do_compare —](#do_compare)|Funkcja wirtualna porównująca dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.|
|[do_hash](#do_hash)|Funkcja wirtualna wywoływana w celu określenia wartości mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.|
|[do_transform](#do_transform)|Funkcja wirtualna wywoływana w celu konwersji sekwencji znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.|
|[Skrót](#hash)|Określa wartość mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.|
|[transform](#transform)|Konwertuje sekwencję znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="char_type"></a>  COLLATE::char_type

Typ, który opisuje znak typu `CharType`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `CharType`.

## <a name="collate"></a>  COLLATE::COLLATE

COLLATE — Konstruktor dla obiektów klasy, która służy jako zestaw reguł ustawień regionalnych do obsługi konwencji sortowania ciągów.

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

*_Refs*<br/>
Wartość liczby całkowitej, można określić typ zarządzania pamięci dla obiektu.

*_Locname*<br/>
Nazwa ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* parametrów i ich znaczenie są:

- 0: okres istnienia obiektu jest zarządzany przez ustawienia regionalne, zawierających go.

- 1: okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: nie zdefiniowano tych wartości.

Konstruktor inicjuje jego podstawowego obiektu z **locale::**[aspekt](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="compare"></a>  COLLATE::COMPARE

Porównuje dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Wskaźnik do pierwszego elementu w pierwszej kolejności mają być porównane.

*Nazwisko1*<br/>
Wskaźnik do ostatniego elementu w pierwszej kolejności mają być porównane.

*first2*<br/>
Wskaźnik do pierwszego elementu w drugiej sekwencji, które mają być porównane.

*Nazwisko2*<br/>
Wskaźnik do ostatniego elementu w drugiej sekwencji, które mają być porównane.

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca:

- -1, jeśli pierwszej sekwencji porównuje mniejsza od drugiej sekwencji.

- + 1, jeśli drugiej sekwencji porównuje mniejszą od pierwszej sekwencji.

- 0, jeśli sekwencji, które są równoważne.

### <a name="remarks"></a>Uwagi

Pierwszej sekwencji porównuje mniej, jeśli ma ona mniejsze elementu w najbliższej pary nierówne w sekwencji lub, jeśli istnieje nie pary nierówne, ale pierwszej sekwencji jest krótszy.

Funkcja elementu członkowskiego zwraca [do_compare —](#do_compare)( `first1`, `last1`, `first2`, `last2`).

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

## <a name="do_compare"></a>  COLLATE::do_compare

Funkcja wirtualna porównująca dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Wskaźnik do pierwszego elementu w pierwszej kolejności mają być porównane.

*Nazwisko1*<br/>
Wskaźnik do ostatniego elementu w pierwszej kolejności mają być porównane.

*first2*<br/>
Wskaźnik do pierwszego elementu w drugiej sekwencji, które mają być porównane.

*Nazwisko2*<br/>
Wskaźnik do ostatniego elementu w drugiej sekwencji, które mają być porównane.

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca:

- -1, jeśli pierwszej sekwencji porównuje mniejsza od drugiej sekwencji.

- + 1, jeśli drugiej sekwencji porównuje mniejszą od pierwszej sekwencji.

- 0, jeśli sekwencji, które są równoważne.

### <a name="remarks"></a>Uwagi

Chronione wirtualna funkcja składowa porównuje sekwencji w [* first1, Nazwisko1) * sekwencji w *[first2, Nazwisko2*). Porównuje wartości, stosując `operator<` między parami odpowiednie elementy typu `CharType`. Pierwszej sekwencji porównuje mniejszy, jeśli ma ona mniejsze elementu w najbliższej pary nierówne w sekwencji, lub jeśli istnieje nie pary nierówne, ale pierwszej sekwencji jest krótszy.

### <a name="example"></a>Przykład

Zobacz przykład [collate::compare](#compare), która wywołuje metodę `do_compare`.

## <a name="do_hash"></a>  COLLATE::do_hash

Funkcja wirtualna wywoływana w celu określenia wartości mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Wskaźnik do pierwszego znaku w sekwencji, w których ma wartość zostanie określony.

*ostatni*<br/>
Wskaźnik do ostatniego znaku w sekwencji, w których ma wartość zostanie określony.

### <a name="return-value"></a>Wartość zwracana

Wartość skrótu typu **długie** w sekwencji.

### <a name="remarks"></a>Uwagi

Wartość skrótu może być przydatne, na przykład dystrybucję sekwencje pseudo-losowo array, list.

### <a name="example"></a>Przykład

Zobacz przykład [skrótu](#hash), która wywołuje metodę `do_hash`.

## <a name="do_transform"></a>  COLLATE::do_transform

Funkcja wirtualna wywoływana w celu konwersji sekwencji znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Wskaźnik do pierwszego znaku w sekwencji, który ma zostać przekonwertowany.

*ostatni*<br/>
Wskaźnik do ostatniego znaku w sekwencji, który ma zostać przekonwertowany.

### <a name="return-value"></a>Wartość zwracana

Ciąg, który jest sekwencją znaków przekształcone.

### <a name="remarks"></a>Uwagi

Funkcja chronionych wirtualna elementu członkowskiego zwraca obiekt klasy [string_type](#string_type) którego kontrolowanej sekwencji jest kopię sekwencji [ `first`, `last`). Jeśli klasa jest pochodną collate\< **CharType**> zastępuje [do_compare —](#do_compare), powinien także Przesłoń `do_transform` do dopasowania. Gdy przekazywane do `collate::compare`, dwa ciągi przekształcone powinien uzyskanie ten sam wynik, jak z przekazywanie Nieprzekształcony ciągów do porównania w klasie pochodnej.

### <a name="example"></a>Przykład

Zobacz przykład [Przekształcanie](#transform), która wywołuje metodę `do_transform`.

## <a name="hash"></a>  COLLATE::hash

Określa wartość mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Wskaźnik do pierwszego znaku w sekwencji, w których ma wartość zostanie określony.

*ostatni*<br/>
Wskaźnik do ostatniego znaku w sekwencji, w których ma wartość zostanie określony.

### <a name="return-value"></a>Wartość zwracana

Wartość skrótu typu **długie** w sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_hash —](#do_hash)( `first`, `last`).

Wartość skrótu może być przydatne, na przykład dystrybucję sekwencje pseudo-losowo array, list.

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

## <a name="string_type"></a>  COLLATE::STRING_TYPE

Typ, który opisuje ciąg typu `basic_string` zawierający znaki typu `CharType`.

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje specjalizacji szablonu klasy [basic_string](../standard-library/basic-string-class.md) których obiekty można przechowywać kopie sekwencji źródłowej.

### <a name="example"></a>Przykład

Na przykład jak deklarować i użyj `string_type`, zobacz [Przekształcanie](#transform).

## <a name="transform"></a>  COLLATE::Transform

Konwertuje sekwencję znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Wskaźnik do pierwszego znaku w sekwencji, który ma zostać przekonwertowany.

*ostatni*<br/>
Wskaźnik do ostatniego znaku w sekwencji, który ma zostać przekonwertowany.

### <a name="return-value"></a>Wartość zwracana

Ciąg, który zawiera sekwencję znaków przekształcone.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [do_transform —](#do_transform)(`first`, `last`).

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

[\<Ustawienia regionalne >](../standard-library/locale.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
