---
title: "uniform_int_distribution — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::uniform_int_distribution
- random/std::uniform_int_distribution::reset
- random/std::uniform_int_distribution::a
- random/std::uniform_int_distribution::b
- random/std::uniform_int_distribution::param
- random/std::uniform_int_distribution::min
- random/std::uniform_int_distribution::max
- random/std::uniform_int_distribution::operator()
- random/std::uniform_int_distribution::param_type
- random/std::uniform_int_distribution::param_type::a
- random/std::uniform_int_distribution::param_type::b
- random/std::uniform_int_distribution::param_type::operator==
- random/std::uniform_int_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::uniform_int_distribution [C++]
- std::uniform_int_distribution [C++], reset
- std::uniform_int_distribution [C++], a
- std::uniform_int_distribution [C++], b
- std::uniform_int_distribution [C++], param
- std::uniform_int_distribution [C++], min
- std::uniform_int_distribution [C++], max
- std::uniform_int_distribution [C++], param_type
- std::uniform_int_distribution [C++], param_type
ms.assetid: a1867dcd-3bd9-4787-afe3-4b62692c1d04
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f44926c91b0e0ee9d576d62870b5118d1f34e70
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="uniformintdistribution-class"></a>uniform_int_distribution — Klasa
Generuje jednolity (każda wartość jest równie prawdopodobne) dystrybucji całkowitą zakresu danych wyjściowych z wartościami granicznymi włącznie.  
  
## <a name="syntax"></a>Składnia  
```  
template<class IntType = int>
   class uniform_int_distribution {
public:    
   // types 
   typedef IntType result_type;    
   struct param_type;    
   
   // constructors and reset functions 
   explicit uniform_int_distribution(
      result_type a = 0, result_type b = numeric_limits<result_type>::max());
   explicit uniform_int_distribution(const param_type& parm);
   void reset();

   // generating functions 
   template <class URNG>  
      result_type operator()(URNG& gen);
   template <class URNG>  
      result_type operator()(URNG& gen, const param_type& parm);

   // property functions 
   result_type a() const;
   result_type b() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
};  
```  
### <a name="parameters"></a>Parametry  
*IntType*  
Integer — typ wyniku domyślnie `int`. Dla typów możliwych [ \<losowe >](../standard-library/random.md).  
  
## <a name="remarks"></a>Uwagi  
Klasa szablonu opisuje wraz z wartościami granicznymi włącznie dystrybucji tworzącego wartości określonych przez użytkownika typu całkowitego z dystrybucji tak, aby każda wartość jest równie prawdopodobne. Poniższe łącza tabeli do artykułów na temat poszczególnych członków.  
  
||||  
|-|-|-|  
|[uniform_int_distribution](#uniform_int_distribution)|`uniform_int_distribution::a`|`uniform_int_distribution::param`|  
|`uniform_int_distribution::operator()`|`uniform_int_distribution::b`|[param_type](#param_type)|  
  
Element członkowski właściwości `a()` zwraca aktualnie przechowywana minimalna granica dystrybucji, podczas `b()` zwraca aktualnie przechowywana granica maksymalna. Dla tej klasy dystrybucji tych minimalne i maksymalne wartości są takie same jak zwracany przez typowych funkcji właściwości `min()` i `max()`.  
  
Element członkowski właściwości `param()` Ustawia lub zwraca `param_type` dystrybucji składowanych parametr pakietu.  

`min()` i `max()` funkcje Członkowskie zwracają najmniejsza możliwa wynik i największa możliwa wynik, odpowiednio.  
  
`reset()` Funkcji członkowskiej odrzuca wszystkie buforowane wartości, tak aby wynik następne wywołanie `operator()` nie zależy od wartości uzyskane z aparatu przed wywołaniem.  
  
`operator()` Elementu członkowskiego zwracają wartość następnego wygenerowanego oparty na aparacie URNG, z bieżącego pakietu parametrów lub pakiet określony parametr.
  
Aby uzyskać więcej informacji o dystrybucji klasy i ich elementy członkowskie, zobacz [ \<losowe >](../standard-library/random.md).  
  
## <a name="example"></a>Przykład  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const int a, const int b, const int s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1729);  
  
    std::uniform_int_distribution<> distr(a, b);  
  
    std::cout << "lower bound == " << distr.a() << std::endl;  
    std::cout << "upper bound == " << distr.b() << std::endl;  
  
    // generate the distribution as a histogram  
    std::map<int, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    std::cout << "Distribution for " << s << " samples:" << std::endl;  
    for (const auto& elem : histogram) {  
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    int a_dist = 1;  
    int b_dist = 10;  
  
    int samples = 100;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter an integer value for the lower bound of the distribution: ";  
    std::cin >> a_dist;  
    std::cout << "Enter an integer value for the upper bound of the distribution: ";  
    std::cin >> b_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(a_dist, b_dist, samples);  
}  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the lower bound of the distribution: 0
Enter an integer value for the upper bound of the distribution: 12
Enter an integer value for the sample count: 200
lower bound == 0
upper bound == 12
Distribution for 200 samples:
    0 :::::::::::::::
    1 :::::::::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::
    4 :::::::
    5 :::::::::::::::::::::
    6 :::::::::::::
    7 ::::::::::
    8 :::::::::::::::
    9 :::::::::::::
   10 ::::::::::::::::::::::
   11 :::::::::::::
   12 :::::::::::::::::
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<losowe >  
  
 **Namespace:** Standard  
  
##  <a name="uniform_int_distribution"></a>  uniform_int_distribution::uniform_int_distribution  
Tworzy dystrybucji.  
  
```  
explicit uniform_int_distribution(
   result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
explicit uniform_int_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parametry  
*a*  
Dolna granica wartości losowych włącznie.  
  
*b*  
Górna granica wartości losowych włącznie.  
  
*parm*  
`param_type` Struktury użyta do skonstruowania dystrybucji.  
  
### <a name="remarks"></a>Uwagi  
**Warunek wstępny:** `a ≤ b`  
  
Pierwszy Konstruktor konstrukcji obiektu których przechowywane `a` wartość przechowuje wartość *a* i których przechowywane `b` wartość zawiera wartość *b*.  
  
Drugi Konstruktor konstrukcji obiektu, którego parametry przechowywane są inicjowane z *parametr*. Możesz uzyskać i ustawić bieżących parametrów istniejącego dystrybucji przez wywołanie metody `param()` funkcję elementu członkowskiego.  
  
##  <a name="param_type"></a>  uniform_int_distribution::param_type  
 Przechowuje parametry dystrybucji.  
```cpp  
struct param_type {  
   typedef uniform_int_distribution<result_type> distribution_type;  
   param_type(
      result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  

### <a name="parameters"></a>Parametry  
*a*  
Dolna granica wartości losowych włącznie.  
  
*b*  
Górna granica wartości losowych włącznie.  
  
*right*  
`param_type` Obiekt do porównania z tym.  
  
### <a name="remarks"></a>Uwagi  
**Warunek wstępny:** `a ≤ b`  
  
Ta struktura może być przekazany do konstruktora klasy dystrybucji przy tworzeniu wystąpienia, do `param()` funkcji członkowskiej, aby ustawić parametry przechowywane istniejących dystrybucji oraz do `operator()` do użycia zamiast przechowywane parametry.  
  
## <a name="see-also"></a>Zobacz też  
 [\<losowe >](../standard-library/random.md)



