---
title: Literały zdefiniowane przez użytkownika (C++)
description: Opisuje przeznaczenie i użycie literałów zdefiniowanych przez użytkownika w standardowym C++.
ms.date: 02/10/2020
ms.assetid: ff4a5bec-f795-4705-a2c0-53788fd57609
ms.openlocfilehash: a6636be414fa4dc199ce10fca1b33f092492575f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2020
ms.locfileid: "79090570"
---
# <a name="user-defined-literals"></a>Literały definiowane przez użytkownika

Istnieje sześć głównych kategorii literałów w C++: Integer, Character, zmiennoprzecinkowy, String, Boolean i wskaźnik. Począwszy od C++ 11, można definiować własne literały oparte na tych kategoriach, aby zapewnić skróty składniowe dla typowych idiomy i zwiększyć bezpieczeństwo typu. Załóżmy na przykład, że masz klasę `Distance`. Można zdefiniować literał dla kilometrów i drugi dla kilometrów i zachęcić użytkownika jako jawnego o jednostkach miary, pisząc: `auto d = 42.0_km` lub `auto d = 42.0_mi`. Nie ma żadnej oceny wydajności ani niekorzystnej dla literałów zdefiniowanych przez użytkownika; są one głównie dla wygody lub do odejmowania typu w czasie kompilacji. Biblioteka standardowa ma literały zdefiniowane przez użytkownika dla `std::string`, dla `std::complex`i dla jednostek w czasie i czasie trwania w \<Chrono >:

```cpp
Distance d = 36.0_mi + 42.0_km;         // Custom UDL (see below)
std::string str = "hello"s + "World"s;  // Standard Library <string> UDL
complex<double> num =
   (2.0 + 3.01i) * (5.0 + 4.3i);        // Standard Library <complex> UDL
auto duration = 15ms + 42h;             // Standard Library <chrono> UDLs
```

## <a name="user-defined-literal-operator-signatures"></a>Sygnatury operatora literału zdefiniowanego przez użytkownika

Należy zaimplementować zdefiniowany przez użytkownika literał przez zdefiniowanie **operatora ""** w zakresie przestrzeni nazw z jedną z następujących form:

```cpp
ReturnType operator "" _a(unsigned long long int);   // Literal operator for user-defined INTEGRAL literal
ReturnType operator "" _b(long double);              // Literal operator for user-defined FLOATING literal
ReturnType operator "" _c(char);                     // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _d(wchar_t);                  // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _e(char16_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _f(char32_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _g(const char*, size_t);      // Literal operator for user-defined STRING literal
ReturnType operator "" _h(const wchar_t*, size_t);   // Literal operator for user-defined STRING literal
ReturnType operator "" _i(const char16_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _g(const char32_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Nazwy operatorów w poprzednim przykładzie są symbolami zastępczymi dla każdej podania nazwy; jednak wymagany jest znak podkreślenia wiodącego. (Tylko Biblioteka standardowa może definiować literały bez znaku podkreślenia). Typ zwracany to miejsce, w którym można dostosować konwersję lub inne operacje wykonywane przez literał. Ponadto dowolny z tych operatorów można zdefiniować jako `constexpr`.

## <a name="cooked-literals"></a>Literały gotowane

W kodzie źródłowym, dowolny literał, czy zdefiniowany przez użytkownika, jest zasadniczo sekwencją znaków alfanumerycznych, takich jak `101`, lub `54.7`lub `"hello"` lub `true`. Kompilator interpretuje sekwencję jako liczbę całkowitą, wartość zmiennoprzecinkową, ciąg znaków const\* i tak dalej. Literał zdefiniowany przez użytkownika, który akceptuje jako dane wejściowe dowolnego typu kompilator przypisany do wartości literału, jest nieformalnie znany jako jako *literał gotowane*. Wszystkie operatory powyżej oprócz `_r` i `_t` są literałami gotowane. Na przykład literał `42.0_km` byłby powiązany z operatorem o nazwie _km, który ma sygnaturę podobną do _b, a literał `42_km` zostałby powiązany z operatorem o sygnaturze podobnej do _a.

W poniższym przykładzie przedstawiono sposób, w jaki literały zdefiniowane przez użytkownika mogą zachęcić wywołujących do jawnej informacji o ich danych wejściowych. Aby skonstruować `Distance`, użytkownik musi jawnie określić kilometry lub mile przy użyciu odpowiedniego literału zdefiniowanego przez użytkownika. Można osiągnąć ten sam wynik w inny sposób, ale literały zdefiniowane przez użytkownika są mniej pełne niż alternatywy.

```cpp
// UDL_Distance.cpp

#include <iostream>
#include <string>

struct Distance
{
private:
    explicit Distance(long double val) : kilometers(val)
    {}

    friend Distance operator"" _km(long double val);
    friend Distance operator"" _mi(long double val);

    long double kilometers{ 0 };
public:
    const static long double km_per_mile;
    long double get_kilometers() { return kilometers; }

    Distance operator+(Distance other)
    {
        return Distance(get_kilometers() + other.get_kilometers());
    }
};

const long double Distance::km_per_mile = 1.609344L;

Distance operator"" _km(long double val)
{
    return Distance(val);
}

Distance operator"" _mi(long double val)
{
    return Distance(val * Distance::km_per_mile);
}

int main()
{
    // Must have a decimal point to bind to the operator we defined!
    Distance d{ 402.0_km }; // construct using kilometers
    std::cout << "Kilometers in d: " << d.get_kilometers() << std::endl; // 402

    Distance d2{ 402.0_mi }; // construct using miles
    std::cout << "Kilometers in d2: " << d2.get_kilometers() << std::endl;  //646.956

    // add distances constructed with different units
    Distance d3 = 36.0_mi + 42.0_km;
    std::cout << "d3 value = " << d3.get_kilometers() << std::endl; // 99.9364

    // Distance d4(90.0); // error constructor not accessible

    std::string s;
    std::getline(std::cin, s);
    return 0;
}
```

Numer literału musi mieć wartość dziesiętną. W przeciwnym razie liczba będzie interpretowana jako liczba całkowita, a typ nie będzie zgodny z operatorem. W przypadku danych wejściowych zmiennoprzecinkowych typ musi być **dłuższy niż Double**, a dla typów całkowitych musi być **długi**Long.

## <a name="raw-literals"></a>Surowe literały

W przypadku nieprzetworzonego literału zdefiniowanego przez użytkownika, zdefiniowany operator akceptuje literał jako sekwencję wartości char. Można interpretować tę sekwencję jako liczbę lub ciąg lub inny typ. Na liście operatorów przedstawionych wcześniej na tej stronie `_r` i `_t` mogą służyć do definiowania literałów nieprzetworzonych:

```cpp
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Można użyć literałów nieprzetworzonych, aby zapewnić niestandardową interpretację sekwencji wejściowej, która jest inna niż normalne zachowanie kompilatora. Można na przykład zdefiniować literał, który konwertuje `4.75987` sekwencji na niestandardowy typ dziesiętny zamiast typu zmiennoprzecinkowego IEEE 754. Niesformatowane literały, takie jak gotowane literały, mogą również służyć do sprawdzania poprawności sekwencji wejściowych w czasie kompilacji.

### <a name="example-limitations-of-raw-literals"></a>Przykład: ograniczenia dotyczące literałów nieprzetworzonych

Operator nieprzetworzonego literału i szablon operatora literału działają tylko dla całkowitych i zmiennoprzecinkowych literałów zdefiniowanych przez użytkownika, jak pokazano w następującym przykładzie:

```cpp
#include <cstddef>
#include <cstdio>

// Literal operator for user-defined INTEGRAL literal
void operator "" _dump(unsigned long long int lit)
{
    printf("operator \"\" _dump(unsigned long long int) : ===>%llu<===\n", lit);
};

// Literal operator for user-defined FLOATING literal
void operator "" _dump(long double lit)
{
    printf("operator \"\" _dump(long double)            : ===>%Lf<===\n",  lit);
};

// Literal operator for user-defined CHARACTER literal
void operator "" _dump(char lit)
{
    printf("operator \"\" _dump(char)                   : ===>%c<===\n",   lit);
};

void operator "" _dump(wchar_t lit)
{
    printf("operator \"\" _dump(wchar_t)                : ===>%d<===\n",   lit);
};

void operator "" _dump(char16_t lit)
{
    printf("operator \"\" _dump(char16_t)               : ===>%d<===\n",   lit);
};

void operator "" _dump(char32_t lit)
{
    printf("operator \"\" _dump(char32_t)               : ===>%d<===\n",   lit);
};

// Literal operator for user-defined STRING literal
void operator "" _dump(const     char* lit, size_t)
{
    printf("operator \"\" _dump(const     char*, size_t): ===>%s<===\n",   lit);
};

void operator "" _dump(const  wchar_t* lit, size_t)
{
    printf("operator \"\" _dump(const  wchar_t*, size_t): ===>%ls<===\n",  lit);
};

void operator "" _dump(const char16_t* lit, size_t)
{
    printf("operator \"\" _dump(const char16_t*, size_t):\n"                  );
};

void operator "" _dump(const char32_t* lit, size_t)
{
    printf("operator \"\" _dump(const char32_t*, size_t):\n"                  );
};

// Raw literal operator
void operator "" _dump_raw(const char* lit)
{
    printf("operator \"\" _dump_raw(const char*)        : ===>%s<===\n",   lit);
};

template<char...> void operator "" _dump_template();       // Literal operator template

int main(int argc, const char* argv[])
{
    42_dump;
    3.1415926_dump;
    3.14e+25_dump;
     'A'_dump;
    L'B'_dump;
    u'C'_dump;
    U'D'_dump;
      "Hello World"_dump;
     L"Wide String"_dump;
    u8"UTF-8 String"_dump;
     u"UTF-16 String"_dump;
     U"UTF-32 String"_dump;
    42_dump_raw;
    3.1415926_dump_raw;
    3.14e+25_dump_raw;

    // There is no raw literal operator or literal operator template support on these types:
    //  'A'_dump_raw;
    // L'B'_dump_raw;
    // u'C'_dump_raw;
    // U'D'_dump_raw;
    //   "Hello World"_dump_raw;
    //  L"Wide String"_dump_raw;
    // u8"UTF-8 String"_dump_raw;
    //  u"UTF-16 String"_dump_raw;
    //  U"UTF-32 String"_dump_raw;
}
```

```Output
operator "" _dump(unsigned long long int) : ===>42<===
operator "" _dump(long double)            : ===>3.141593<===
operator "" _dump(long double)            : ===>31399999999999998506827776.000000<===
operator "" _dump(char)                   : ===>A<===
operator "" _dump(wchar_t)                : ===>66<===
operator "" _dump(char16_t)               : ===>67<===
operator "" _dump(char32_t)               : ===>68<===
operator "" _dump(const     char*, size_t): ===>Hello World<===
operator "" _dump(const  wchar_t*, size_t): ===>Wide String<===
operator "" _dump(const     char*, size_t): ===>UTF-8 String<===
operator "" _dump(const char16_t*, size_t):
operator "" _dump(const char32_t*, size_t):
operator "" _dump_raw(const char*)        : ===>42<===
operator "" _dump_raw(const char*)        : ===>3.1415926<===
operator "" _dump_raw(const char*)        : ===>3.14e+25<===
```
