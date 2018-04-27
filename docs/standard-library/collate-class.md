---
title: COLLATE — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a18745faf6a8fe0e57e57b15c811cc153780a4f7
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="collate-class"></a>collate — Klasa

Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych, aby kontrolować kolejność i grupowanie znaków w ciągu, porównania między nimi i mieszanie ciągów.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>Parametry

`CharType` Typ używany w programie do kodowania znaków.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba jej wartości przechowywanej dostępu są przechowywane w unikatową wartość dodatnią **identyfikator.** W przypadku niektórych języków znaki są grupowane i traktowane jak pojedynczy znak, a w innych, pojedyncze znaki są traktowane tak, jakby były dwoma znakami. Usługi sortowania dostarczane przez klasę collate umożliwiają sortowanie w tych przypadkach.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Sortowanie](#collate)|Konstruktor dla obiektów klasy `collate` służy jako zestaw reguł ustawienia regionalne do obsługi ciąg sortowania Konwencji.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ, który opisuje znaku typu `CharType`.|
|[string_type](#string_type)|Typ, który opisuje ciąg typu `basic_string` zawierające znaki typu `CharType`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[Porównaj](#compare)|Porównuje dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.|
|[do_compare](#do_compare)|Funkcja wirtualna porównująca dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.|
|[do_hash](#do_hash)|Funkcja wirtualna wywoływana w celu określenia wartości mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.|
|[do_transform](#do_transform)|Funkcja wirtualna wywoływana w celu konwersji sekwencji znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.|
|[Wyznaczania wartości skrótu](#hash)|Określa wartość mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.|
|[transform](#transform)|Konwertuje sekwencję znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** Standard

## <a name="char_type"></a>  COLLATE::char_type

Typ, który opisuje znaku typu **CharType**.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType**.

## <a name="collate"></a>  COLLATE::COLLATE

Konstruktor dla obiektów klasy collate służącym jako zestaw reguł ustawienia regionalne do obsługi ciąg sortowania Konwencji.

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

`_Refs` Wartość całkowita używany do określania typu zarządzania pamięci dla obiektu.

`_Locname` Nazwa ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Możliwe wartości `_Refs` i ich znaczenie są:

- 0: okres istnienia obiektu zarządza ustawieniami regionalnymi, które zawierałoby proces.

- 1: okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: te wartości są niezdefiniowane.

Konstruktor inicjuje jego obiektu podstawowego z **locale::**[aspektu](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="compare"></a>  COLLATE::COMPARE

Porównuje dwie sekwencje znaków zgodnie z ich zasadami równości i nierówności specyficznymi dla zestawów reguł.

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametry

`first1` Wskaźnik do pierwszego elementu w pierwszej kolejności ma zostać porównane.

`last1` Wskaźnik do ostatniego elementu w pierwszej kolejności ma zostać porównane.

`first2` Wskaźnik do pierwszego elementu w drugim sekwencji do porównania.

`last2` Wskaźnik do ostatniego elementu w drugim sekwencji do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję elementu członkowskiego:

- -1, jeśli pierwszy sekwencji porównuje mniej niż drugi sekwencji.

- + 1, jeśli drugi sekwencji porównuje mniej niż pierwszy sekwencji.

- 0, jeśli sekwencje są równoważne.

### <a name="remarks"></a>Uwagi

Pierwszy sekwencji porównuje mniejszy, jeśli ma mniejszy element najwcześniejszą pary nierówne w sekwencjach lub, jeśli nie nierówne pary istnieje, ale pierwszym sekwencji jest krótszy.

Funkcja członkowska zwraca [do_compare](#do_compare)( `first1`, `last1`, `first2`, `last2`).

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

`first1` Wskaźnik do pierwszego elementu w pierwszej kolejności ma zostać porównane.

`last1` Wskaźnik do ostatniego elementu w pierwszej kolejności ma zostać porównane.

`first2` Wskaźnik do pierwszego elementu w drugim sekwencji do porównania.

`last2` Wskaźnik do ostatniego elementu w drugim sekwencji do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję elementu członkowskiego:

- -1, jeśli pierwszy sekwencji porównuje mniej niż drugi sekwencji.

- + 1, jeśli drugi sekwencji porównuje mniej niż pierwszy sekwencji.

- 0, jeśli sekwencje są równoważne.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego porównuje sekwencji w [* first1, Nazwisko1) * z sekwencją na *[first2, Nazwisko2*). Porównuje wartości, stosując **operatora <** między parami odpowiednie elementy typu **CharType**. Pierwszy sekwencji porównuje mniejszy, jeśli ma mniejszy element najwcześniejszą pary nierówne w sekwencjach lub nie nierówne pary istnieje, ale pierwszym sekwencji jest krótszy.

### <a name="example"></a>Przykład

Zobacz przykład [collate::compare](#compare), które wywołuje `do_compare`.

## <a name="do_hash"></a>  COLLATE::do_hash

Funkcja wirtualna wywoływana w celu określenia wartości mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

`first` Wskaźnik do pierwszego znaku w sekwencji, których ma wartość zostanie określony.

`last` Wskaźnik do ostatni znak w sekwencji, których ma wartość zostanie określony.

### <a name="return-value"></a>Wartość zwracana

Wartość skrótu typu **długi** w sekwencji.

### <a name="remarks"></a>Uwagi

Wartość skrótu może być przydatne na przykład w dystrybucję sekwencji pseudolosowo tablicy list.

### <a name="example"></a>Przykład

Zobacz przykład [skrótu](#hash), które wywołuje `do_hash`.

## <a name="do_transform"></a>  COLLATE::do_transform

Funkcja wirtualna wywoływana w celu konwersji sekwencji znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

`first` Wskaźnik do pierwszego znaku w sekwencji, który ma zostać przekonwertowany.

`last` Wskaźnik do ostatni znak w sekwencji, który ma zostać przekonwertowany.

### <a name="return-value"></a>Wartość zwracana

Ciąg, który jest sekwencja znaków po przekształceniu.

### <a name="remarks"></a>Uwagi

Funkcja chroniony wirtualny element członkowski zwraca obiekt klasy [string_type](#string_type) których kontrolowanej sekwencji jest kopią sekwencji [ `first`, `last`). Jeśli klasa pochodna od sortowania\< **CharType**> zastępuje [do_compare](#do_compare), również powinny zastępować `do_transform` do dopasowania. Gdy dane są przekazywane do `collate::compare`, dwa ciągi przekształcone powinien uzyskanie takiego samego wyniku, jak z przekazywaniem Nieprzekształcony ciągi do porównania w klasie pochodnej.

### <a name="example"></a>Przykład

Zobacz przykład [przekształcenie](#transform), które wywołuje `do_transform`.

## <a name="hash"></a>  COLLATE::hash

Określa wartość mieszania sekwencji zgodnie z ich zasadami specyficznymi dla zestawów reguł.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

`first` Wskaźnik do pierwszego znaku w sekwencji, których ma wartość zostanie określony.

`last` Wskaźnik do ostatni znak w sekwencji, których ma wartość zostanie określony.

### <a name="return-value"></a>Wartość zwracana

Wartość skrótu typu **długi** w sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_hash](#do_hash)( `first`, `last`).

Wartość skrótu może być przydatne na przykład w dystrybucję sekwencji pseudolosowo tablicy list.

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

Typ, który opisuje ciąg typu `basic_string` zawierające znaki typu **CharType**.

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Uwagi

Typ w tym artykule opisano specjalizacji szablonu klasy [basic_string —](../standard-library/basic-string-class.md) obiektów, których można przechowywać kopie sekwencji źródłowej.

### <a name="example"></a>Przykład

Przykład sposobu deklarowanie i użycie `string_type`, zobacz [przekształcenie](#transform).

## <a name="transform"></a>  COLLATE::Transform

Konwertuje sekwencję znaków z ustawień regionalnych na ciąg znaków, który może być używany w porównaniach leksykograficznych z innymi sekwencjami znaków podobnie przekonwertowanymi z tych samych ustawień regionalnych.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

`first` Wskaźnik do pierwszego znaku w sekwencji, który ma zostać przekonwertowany.

`last` Wskaźnik do ostatni znak w sekwencji, który ma zostać przekonwertowany.

### <a name="return-value"></a>Wartość zwracana

Ciąg, który zawiera sekwencję znaków po przekształceniu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [do_transform](#do_transform)( `first`, `last`).

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
