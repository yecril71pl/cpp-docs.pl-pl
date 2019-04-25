---
title: num_get — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
ms.openlocfilehash: c0984c15e2bf1682fc902264f47f340d0bd3c859
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223759"
---
# <a name="numget-class"></a>num_get — Klasa

Klasa szablonu opisująca obiekt, który może służyć jako zestaw reguł ustawień regionalnych w celu kontroli konwersji sekwencji typu `CharType` na wartości liczbowe.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ używany w programie do kodowania znaków w ustawieniach regionalnych.

*InputIterator*<br/>
Typ iteratora, z którego liczbowe funkcje get odczytują swoje dane wejściowe.

## <a name="remarks"></a>Uwagi

Podobnie jak w przypadku dowolnego zestawu reguł ustawień regionalnych, identyfikator obiektu statycznego ma początkową przechowywaną wartość zero. Pierwsza próba dostępu do jego przechowywanej wartości przechowuje unikatową wartość dodatnią w **identyfikator.**

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[num_get](#num_get)|Konstruktor dla obiektów typu `num_get` służących do wyodrębniania wartości liczbowych z sekwencji.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ opisujący znak używany przez ustawienie regionalne.|
|[iter_type](#iter_type)|Typ, który opisuje iterator danych wejściowych.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[do_get](#do_get)|Funkcja wirtualna wywoływana w celu wyodrębniania wartości liczbowej lub logicznej z sekwencji znaków.|
|[get](#get)|Wyodrębnia wartość liczbową lub logiczną z sekwencji znaków.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="char_type"></a>  num_get::char_type

Typ opisujący znak używany przez ustawienie regionalne.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu **CharType**.

## <a name="do_get"></a>  num_get::do_get

Funkcja wirtualna wywoływana w celu wyodrębniania wartości liczbowej lub logicznej z sekwencji znaków.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Początek zakresu znaków, z którego można odczytać numeru.

*last*<br/>
Koniec zakresu znaków, z którego można odczytać numeru.

*_Iosbase*<br/>
[Ios_base —](../standard-library/ios-base-class.md) którego flagi są używane przez konwersję.

*_Stanu*<br/>
Stan, do których failbit (zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) jest dodawany w przypadku awarii.

*Val*<br/>
Wartość, która została odczytana.

### <a name="return-value"></a>Wartość zwracana

Iterator po przeczytaniu wartość.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja wirtualna elementu członkowskiego chronionego

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
```

Dopasowuje elementy sekwencyjnych, rozpoczynając od *pierwszy* w sekwencji `[first, last)` dopóki nie został rozpoznany kompletna, niepustych liczby całkowitej danych wejściowych pola. Jeśli operacja się powiedzie, konwertuje to pole na jego równoważną wartość jako typ **długie**i zapisuje wynik w *val*. Zwraca iterator, wyznaczanie pierwszego elementu poza pola danych wejściowych numerycznego. W przeciwnym razie funkcja przechowuje, żadne postanowienie *val* i ustawia `ios_base::failbit` w `state`. Zwraca iterator, wyznaczanie pierwszego elementu poza dowolnego prefiksu, pola wejściowego prawidłową liczbę całkowitą. W obu przypadkach, jeśli wartość zwracana równa `last`, zestawy funkcji `ios_base::eofbit` w `state`.

Pole wejściowe liczba całkowita jest konwertowany przez te same zasady, które są używane przez funkcje skanowania do dopasowania i konwertowania szereg **char** elementów z pliku. (Każdy przykład **char** przyjęto, że element mapowania na równoważne elementu typu `Elem` przez prosty, jeden do jednego, mapowanie.) Specyfikacja konwersji równoważne skanowania jest określany w następujący sposób:

Jeśli `iosbase.` [ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), to specyfikacja konwersji `lo`.

Jeśli `iosbase.flags() & ios_base::basefield == ios_base::` [szesnastkowy](../standard-library/ios-functions.md#hex), to specyfikacja konwersji `lx`.

Jeśli `iosbase.flags() & ios_base::basefield == 0`, to specyfikacja konwersji `li`.

W przeciwnym razie jest specyfikacja konwersji `ld`.

Format wejściowy pola Liczba całkowita jest dalsze ustalana [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class) `fac` zwracany przez wywołanie [use_facet](../standard-library/locale-functions.md#use_facet) `<` [numpunct —](../standard-library/numpunct-class.md) `<Elem>(iosbase.` [ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())`. W szczególności:

`fac.` [numpunct::GROUPING](../standard-library/numpunct-class.md#grouping) `()` określa sposób grupowania cyfr na lewo od każdego znaku dziesiętnego

`fac.` [numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` określa kolejność, która oddziela grup cyfr na lewo od każdego znaku dziesiętnego.

Jeśli nie wystąpienia `fac.thousands_sep()` występują w pola danych wejściowych numerycznego, zostaje nałożone nie ograniczenia grupowania. W przeciwnym razie wszelkie ograniczenia grupowania nałożonych przez `fac.grouping()` są wymuszane i separatory są usuwane, zanim wystąpi konwersji skanowania.

Czwarty chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

zachowuje się taka sama jak pierwsza strona, z tą różnicą, że zastępuje specyfikacja konwersji `ld` z `lu`. Jeśli pomyślne konwertuje pola danych wejściowych numerycznego do wartości typu **unsigned long** i zapisuje wynikową wartość w *val*.

Piąty chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;
```

zachowuje się taka sama jak pierwsza strona, z tą różnicą, że zastępuje specyfikacja konwersji `ld` z `lld`. Jeśli pomyślne konwertuje pola danych wejściowych numerycznego do wartości typu **long long** i zapisuje wynikową wartość w *val*.

Szósty chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;
```

zachowuje się taka sama jak pierwsza strona, z tą różnicą, że zastępuje specyfikacja konwersji `ld` z `llu`. Jeśli pomyślne konwertuje pola danych wejściowych numerycznego do wartości typu **unsigned long long** i zapisuje wynikową wartość w *val*.

Siódmego chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;
```

działa tak samo jako pierwsze, chyba że usiłują dopasowania pełne, niepustych pola wejściowego zmiennoprzecinkowego. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` określa kolejność, która oddziela liczby całkowite od cyfr końcowej. Jest równoważne skanowania specyfikatora konwersji `lf`.

Ósmego chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

działa tak samo jako pierwsze, chyba że usiłują dopasowania pełne, niepustych pola wejściowego zmiennoprzecinkowego. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` określa kolejność, która oddziela liczby całkowite od cyfr końcowej. Jest równoważne skanowania specyfikatora konwersji `lf`.

Dziewiąty chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

zachowuje się taka sama jak ósmego, z tą różnicą, że jest równoważna skanowania specyfikatora konwersji `Lf`.

Dziesiąty chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

działa tak samo, pierwsza strona, z tą różnicą, że jest równoważna skanowania specyfikatora konwersji `p`.

Ostatnie (jedenasta) chronione funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

zachowuje się taka sama jak pierwsza strona, poza tym, że usiłują dopasowania pełne, niepustych logiczna pola wejściowego. Jeśli pomyślne konwertuje wartość logiczna pola wejściowego na wartość typu **bool** i zapisuje wynikową wartość w *val*.

Logiczna pole wejściowe ma jedną z dwóch form. Jeśli `iosbase.flags() & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) ma wartość FAŁSZ, jest taka sama jak liczba całkowita pola wejściowego, z tą różnicą, że wartość przekonwertowanego musi być 0 (false) lub 1 (PRAWDA). W przeciwnym razie sekwencja musi odpowiadać jednej `fac.` [numpunct::falsename](../standard-library/numpunct-class.md#falsename) `()` (w przypadku wartości false), lub `fac.` [numpunct::truename](../standard-library/numpunct-class.md#truename) `()` (w przypadku wartości true).

### <a name="example"></a>Przykład

Zobacz przykład [uzyskać](#get), w którym funkcja wirtualna elementu członkowskiego jest wywoływana przez `do_get`.

## <a name="get"></a>  num_get::Get

Wyodrębnia wartość liczbową lub logiczną z sekwencji znaków.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Początek zakresu znaków, z którego można odczytać numeru.

*last*<br/>
Koniec zakresu znaków, z którego można odczytać numeru.

*_Iosbase*<br/>
[Ios_base —](../standard-library/ios-base-class.md) którego flagi są używane przez konwersję.

*_Stanu*<br/>
Stan, do których failbit (zobacz [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) jest dodawany w przypadku awarii.

*Val*<br/>
Wartość, która została odczytana.

### <a name="return-value"></a>Wartość zwracana

Iterator po przeczytaniu wartość.

### <a name="remarks"></a>Uwagi

Wszystkie funkcje Członkowskie zwracają [do_get —](#do_get)( `first`, `last`, `_Iosbase`, `_State`, `val`).

Pierwsza funkcja wirtualna elementu członkowskiego chronionego próbuje dopasować kolejne elementy od początku sekwencji [ `first`, `last`), dopóki nie został rozpoznany kompletna, niepustych liczby całkowitej danych wejściowych pola. Jeśli operacja się powiedzie, konwertuje to pole na jego równoważną wartość jako typ **długie** i zapisuje wynik w *val*. Zwraca iterator, wyznaczanie pierwszego elementu poza pola danych wejściowych numerycznego. W przeciwnym razie funkcja przechowuje, żadne postanowienie *val* i ustawia `ios_base::failbit` w _ *stanu*. Zwraca iterator, wyznaczanie pierwszego elementu poza dowolnego prefiksu, pola wejściowego prawidłową liczbę całkowitą. W obu przypadkach, jeśli wartość zwracana równa *ostatniego*, zestawy funkcji `ios_base::eofbit` w *_stanu*.

Pole wejściowe liczba całkowita jest konwertowany przez te same zasady, które są używane przez funkcje skanowania do dopasowania i konwertowania szereg **char** elementów z pliku. Każdy przykład **char** przyjęto, że element mapowania na równoważne elementu typu `CharType` przez mapowania proste, jeden do jednego. Specyfikacja konwersji równoważne skanowania jest określany w następujący sposób:

- If `iosbase`. [flagi](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct), to specyfikacja konwersji `lo`.

- Jeśli **iosbase.flags** & **ios_base::basefield** == `ios_base::`[szesnastkowy](../standard-library/ios-functions.md#hex), to specyfikacja konwersji `lx`.

- Jeśli **iosbase.flags** & **ios_base::basefield** == 0, to specyfikacja konwersji `li`.

- W przeciwnym razie jest specyfikacja konwersji `ld`.

Format wejściowy pola Liczba całkowita jest dalsze ustalana [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class)**fac** zwracany przez wywołanie [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct — ](../standard-library/numpunct-class.md) \< **Elem**> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). W szczególności:

- **FAC**. [Grupowanie](../standard-library/numpunct-class.md#grouping) określa sposób grupowania cyfr na lewo od każdego znaku dziesiętnego.

- **FAC**. [thousands_sep —](../standard-library/numpunct-class.md#thousands_sep) określa kolejność, która oddziela grup cyfr na lewo od każdego znaku dziesiętnego.

Jeśli nie wystąpienia **fac**. `thousands_sep` występują w pola danych wejściowych numerycznego, zostaje nałożone nie ograniczenia grupowania. W przeciwnym razie wszelkie ograniczenia grupowania nałożonych przez **fac**. **Grupowanie** są wymuszane i separatory są usuwane, zanim wystąpi konwersji skanowania.

Druga funkcja wirtualna elementu członkowskiego chronionego:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

zachowuje się taka sama jak pierwsza strona, z tą różnicą, że zastępuje specyfikacja konwersji `ld` z `lu`. Jeśli operacja się powiedzie, konwertuje pola danych wejściowych numerycznego do wartości typu **unsigned long** i zapisuje wynikową wartość w *val*.

Trzecia funkcja wirtualna elementu członkowskiego chronionego:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

zachowuje się taka sama jak pierwsza strona, z tą różnicą, że próbuje dopasować pełne, niepustych pola wejściowego zmiennoprzecinkowego. **FAC**. [decimal_point —](../standard-library/numpunct-class.md#decimal_point) określa kolejność, która oddziela liczby całkowite od cyfr końcowej. Jest równoważne skanowania specyfikatora konwersji `lf`.

Czwarty chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

działa tak samo trzeci, z tą różnicą, że jest równoważna skanowania specyfikatora konwersji `Lf`.

Piąty chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

działa tak samo, pierwsza strona, z tą różnicą, że jest równoważna skanowania specyfikatora konwersji `p`.

Szósty chronionych funkcja wirtualna elementu członkowskiego:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

działa tak samo jako pierwsze, poza tym, że próbuje dopasować pełne, niepustych logiczna pola wejściowego. Jeśli pomyślne konwertuje wartość logiczna pola wejściowego na wartość typu **bool** i zapisuje wynikową wartość w *val*.

Logiczna pole wejściowe ma jedną z dwóch form. Jeśli **iosbase**. **flagi** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) jest **false**, jest taka sama jak liczba całkowita pola wejściowego, z tą różnicą, że wartość przekonwertowanego musi być albo 0 (dla **false** ) lub 1 (dla **true**). W przeciwnym razie sekwencja musi odpowiadać jednej **fac**. [falsename —](../standard-library/numpunct-class.md#falsename) (dla **false**), lub **fac**. [truename —](../standard-library/numpunct-class.md#truename) (dla **true**).

### <a name="example"></a>Przykład

```cpp
// num_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   basic_stringstream<char> psz, psz2;
   psz << "-1000,56";

   ios_base::iostate st = 0;
   long double fVal;
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;

   psz.imbue( loc );
   use_facet <num_get <char> >
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter(0), psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get( ) FAILED" << endl;
   else
      cout << "money_get( ) = " << fVal << endl;
}
```

## <a name="iter_type"></a>  num_get::iter_type

Typ, który opisuje iterator danych wejściowych.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `InputIterator`.

## <a name="num_get"></a>  num_get::num_get

Konstruktor dla obiektów typu `num_get` służących do wyodrębniania wartości liczbowych z sekwencji.

```cpp
explicit num_get(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*<br/>
Wartość liczby całkowitej, można określić typ zarządzania pamięci dla obiektu.

### <a name="remarks"></a>Uwagi

Możliwe wartości parametru *_Refs* parametrów i ich znaczenie są:

- 0: Okres istnienia obiektu jest zarządzany przez ustawienia regionalne, zawierających go.

- 1: Okres istnienia obiektu musi być zarządzane ręcznie.

- \> 1: Te wartości nie są zdefiniowane.

Żadnych przykładów bezpośrednie są to tylko możliwe, ponieważ destruktor jest chroniony.

Konstruktor inicjuje jego podstawowego obiektu z **locale::**[aspekt](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="see-also"></a>Zobacz także

[\<locale>](../standard-library/locale.md)<br/>
[facet Class](../standard-library/locale-class.md#facet_class)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
