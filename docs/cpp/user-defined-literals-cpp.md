---
title: Zdefiniowane przez użytkownika literałów (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: ff4a5bec-f795-4705-a2c0-53788fd57609
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 835f56498d3bc19f0b31ea9047f2e76d955183f4
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947777"
---
# <a name="user-defined-literals--c"></a>Literały definiowane przez użytkownika (C++)
Istnieje pięć głównych kategorii literałów: liczba całkowita, ciąg znaków, zmiennoprzecinkowych, atrybut typu wartość logiczna i wskaźnika.  Uruchamianie c ++ 11, można zdefiniować własne literały, na podstawie tych kategorii zapewnia składni skróty dla typowych idiomy i poprawia bezpieczeństwo typów. Załóżmy na przykład, że masz klasę odległości. Można zdefiniować literał dla kilometrów i inny dla mil, a zachęcenia użytkowników, aby była niejawna przy korzystaniu jednostki miary, po prostu pisząc: automatyczne d = 42.0_km lub auto d = 42.0_mi. Nie ma żadnych korzyści wydajności ani wadą literały definiowane przez użytkownika; są one przede wszystkim dla wygody lub wnioskowanie typu w czasie kompilacji. Standardowa biblioteka zawiera literały definiowane przez użytkownika std:string, wartość std::complex i jednostek w czas i czas trwania operacji w \<chrono > nagłówka:  
  
```cpp 
Distance d = 36.0_mi + 42.0_km;         // Custom UDL (see below)  
    std::string str = "hello"s + "World"s;  // Standard Library <string> UDL  
    complex<double> num =   
        (2.0 + 3.01i) * (5.0 + 4.3i);       // Standard Library <complex> UDL  
    auto duration = 15ms + 42h;             // Standard Library <chrono> UDLs  
```  
  
## <a name="user-defined-literal-operator-signatures"></a>Podpisy operatora literału zdefiniowanego przez użytkownika  
 Implementowanie literału zdefiniowanego przez użytkownika, definiując `operator""` w zakresie przestrzeni nazw przy użyciu jednego z następujących form:  
  
```cpp 
ReturnType operator "" _a(unsigned long long int);   // Literal operator for user-defined INTEGRAL literal  
ReturnType operator "" _b(long double);              // Literal operator for user-defined FLOATING literal  
ReturnType operator "" _c(char);                     // Literal operator for user-defined CHARACTER literal  
ReturnType operator "" _d(wchar_t);                  // Literal operator for user-defined CHARACTER literal  
ReturnType operator "" _e(char16_t);                 // Literal operator for user-defined CHARACTER literal  
ReturnType operator "" _f(char32_t);                 // Literal operator for user-defined CHARACTER literal  
ReturnType operator "" _g(const     char*, size_t);  // Literal operator for user-defined STRING literal  
ReturnType operator "" _h(const  wchar_t*, size_t);  // Literal operator for user-defined STRING literal  
ReturnType operator "" _i(const char16_t*, size_t);  // Literal operator for user-defined STRING literal  
ReturnType operator "" _g(const char32_t*, size_t);  // Literal operator for user-defined STRING literal  
ReturnType operator "" _r(const char*);              // Raw literal operator  
template<char...> ReturnType operator "" _t();       // Literal operator template  
```  
  
 Nazwy operatora w poprzednim przykładzie są symbolami zastępczymi dowolną nazwę, możesz podać; wymagane jest jednak wiodący znak podkreślenia. (Standardowa biblioteka jest dozwolony do definiowania literałów bez znaku podkreślenia). Typ zwracany to, gdzie możesz dostosować konwersji lub innych operacji, który wykonuje literału. Ponadto dowolne z tych operatorów można zdefiniować jako `constexpr`.  
  
## <a name="cooked-literals"></a>Literały gotowe  
 W źródle kodu wszelkie literał, czy zdefiniowane przez użytkownika nie jest zasadniczo sekwencję znaków alfanumerycznych, takich jak `101`, lub `54.7`, lub `"hello"` lub `true`. Kompilator interpretuje słowa kluczowe, sekwencja jako liczba całkowita, float, const char\* parametry i tak dalej. Literału zdefiniowanego przez użytkownika, który przyjmuje jako dane wejściowe, niezależnie od ich rodzaju kompilatora przypisane do wartości literału jest nazywane nieformalnie *gotowe literał*. Wszystkie operatory powyżej, z wyjątkiem `_r` i `_t` są gotowane literały. Na przykład, literał `42.0_km` będzie powiązać operator o nazwie _km, który ma podpis przypominające _b i literału `42_km` będzie powiązać operatora z podpisem, podobnie jak _a.  
  
 Poniższy przykład pokazuje, jak literały definiowane przez użytkownika może zwiększyć liczbę wywołań, aby była niejawna przy korzystaniu swoje dane wejściowe. Do konstruowania `Distance`, użytkownik musi jawnie określić km lub mil, za pomocą odpowiednich literału zdefiniowanego przez użytkownika. Oczywiście można również osiągnąć ten sam wynik w inny sposób, ale literały definiowane przez użytkownika są mniej szczegółowe informacje, niż alternatyw.  
  
```cpp 
struct Distance  
{  
private:  
    explicit Distance(long double val) : kilometers(val)  
    {}  
  
    friend Distance operator"" _km(long double  val);  
    friend Distance operator"" _mi(long double val);  
    long double kilometers{ 0 };  
public:  
    long double get_kilometers() { return kilometers; }  
    Distance operator+(Distance& other)  
    {  
        return Distance(get_kilometers() + other.get_kilometers());  
    }  
};  
  
Distance operator"" _km(long double  val)  
{  
    return Distance(val);  
}  
  
Distance operator"" _mi(long double val)  
{  
    return Distance(val * 1.6);  
}  
int main(int argc, char* argv[])  
{  
    // Must have a decimal point to bind to the operator we defined!  
    Distance d{ 402.0_km }; // construct using kilometers  
    cout << "Kilometers in d: " << d.get_kilometers() << endl; // 402  
  
    Distance d2{ 402.0_mi }; // construct using miles  
    cout << "Kilometers in d2: " << d2.get_kilometers() << endl;  //643.2  
  
    // add distances constructed with different units  
    Distance d3 = 36.0_mi + 42.0_km;  
    cout << "d3 value = " << d3.get_kilometers() << endl; // 99.6  
  
   // Distance d4(90.0); // error constructor not accessible  
  
    string s;  
    getline(cin, s);  
    return 0;  
}  
```  
  
 Należy zauważyć, że numer literału należy użyć wartości dziesiętnej, w przeciwnym razie liczba może być interpretowany jako liczba całkowita i typ nie jest zgodny z operatorem. Należy również zauważyć, że dla liczb zmiennoprzecinkowych w danych wejściowych, musi być typu **typu long double**, a w przypadku typów całkowitych musi być **long long**.  
  
## <a name="raw-literals"></a>Nieprzetworzone literały  
 W surowego literału zdefiniowanego przez użytkownika operator, który zdefiniujesz akceptuje literału jako sekwencja wartości char i jest maksymalnie do interpretacji tej sekwencji jako liczba lub ciąg lub innego typu. Na liście operatory przedstawiony we wcześniejszej części tej strony `_r` i `_t` może służyć do definiowania literałów raw:  
  
```cpp 
ReturnType operator "" _r(const char*);              // Raw literal operator  
template<char...> ReturnType operator "" _t();       // Literal operator template  
```  
  
 Nieprzetworzone literały służy do zapewnienia niestandardowych interpretacji sekwencji wejściowych, który jest inny niż co kompilator wykona. Na przykład można zdefiniować właściwość literal, która konwertuje sekwencję `4.75987` do niestandardowego typu dziesiętnego zamiast IEEE 754 typu punktu zmiennoprzecinkowego. Nieprzetworzone literały, takich jak gotowane literały, można również przeprowadzić weryfikacji kompilacji sekwencji wejściowych.  
  
### <a name="example"></a>Przykład  
  
### <a name="limitations-of-raw-literals"></a>Ograniczenia nieprzetworzone literały  
 Nieprzetworzonego operatora literału i szablonu operatora literału działać tylko przez całkowite i zmiennoprzecinkowe liczby literały definiowane przez użytkownika, jak pokazano na poniższym przykładzie:  
  
```cpp 
#include <cstddef>  
#include <cstdio>  
  
void operator "" _dump(unsigned long long int lit)  { printf("operator \"\" _dump(unsigned long long int) : ===>%llu<===\n", lit); };  // Literal operator for user-defined INTEGRAL literal  
void operator "" _dump(long double lit)             { printf("operator \"\" _dump(long double)            : ===>%Lf<===\n",  lit); };  // Literal operator for user-defined FLOATING literal  
void operator "" _dump(char lit)                    { printf("operator \"\" _dump(char)                   : ===>%c<===\n",   lit); };  // Literal operator for user-defined CHARACTER literal  
void operator "" _dump(wchar_t lit)                 { printf("operator \"\" _dump(wchar_t)                : ===>%d<===\n",   lit); };  // Literal operator for user-defined CHARACTER literal  
void operator "" _dump(char16_t lit)                { printf("operator \"\" _dump(char16_t)               : ===>%d<===\n",   lit); };  // Literal operator for user-defined CHARACTER literal  
void operator "" _dump(char32_t lit)                { printf("operator \"\" _dump(char32_t)               : ===>%d<===\n",   lit); };  // Literal operator for user-defined CHARACTER literal  
void operator "" _dump(const     char* lit, size_t) { printf("operator \"\" _dump(const     char*, size_t): ===>%s<===\n",   lit); };  // Literal operator for user-defined STRING literal  
void operator "" _dump(const  wchar_t* lit, size_t) { printf("operator \"\" _dump(const  wchar_t*, size_t): ===>%ls<===\n",  lit); };  // Literal operator for user-defined STRING literal  
void operator "" _dump(const char16_t* lit, size_t) { printf("operator \"\" _dump(const char16_t*, size_t):\n"                  ); };  // Literal operator for user-defined STRING literal  
void operator "" _dump(const char32_t* lit, size_t) { printf("operator \"\" _dump(const char32_t*, size_t):\n"                  ); };  // Literal operator for user-defined STRING literal  
void operator "" _dump_raw(const char* lit)         { printf("operator \"\" _dump_raw(const char*)        : ===>%s<===\n",   lit); };  // Raw literal operator  
  
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
    // 'A'_dump_raw;               // There is no raw literal operator or literal operator template support on this type  
    //L'B'_dump_raw;              // There is no raw literal operator or literal operator template support on this type  
    //u'C'_dump_raw;              // There is no raw literal operator or literal operator template support on this type  
    //U'D'_dump_raw;              // There is no raw literal operator or literal operator template support on this type  
    //  "Hello World"_dump_raw;   // There is no raw literal operator or literal operator template support on this type  
    // L"Wide String"_dump_raw;   // There is no raw literal operator or literal operator template support on this type  
    //u8"UTF-8 String"_dump_raw;   // There is no raw literal operator or literal operator template support on this type  
    // u"UTF-16 String"_dump_raw;  // There is no raw literal operator or literal operator template support on this type  
    // U"UTF-32 String"_dump_raw;  // There is no raw literal operator or literal operator template support on this type  
}  
/*****  
Output:  
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
*****/  
  
```