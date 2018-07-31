---
title: funkcjonalności (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/functional>
- cliext::binary_delegate
- cliext::binary_delegate_noreturn
- cliext::binary_negate
- cliext::bind1st
- cliext::bind2nd
- cliext::binder1st
- cliext::binder2nd
- cliext::divides
- cliext::equal_to
- cliext::greater
- cliext::greater_equal
- cliext::less
- cliext::less_equal
- cliext::logical_and
- cliext::logical_not
- cliext::logical_or
- cliext::minus
- cliext::modulus
- cliext::multiplies
- cliext::negate
- cliext::not_equal_to
- cliext::not1
- cliext::not2
- cliext::plus
- cliext::unary_delegate
- cliext::unary_delegate_noreturn
- cliext::unary_negate
dev_langs:
- C++
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
- binary_delegate function [STL/CLR]
- binary_delegate_noreturn function [STL/CLR]
- binary_negate function [STL/CLR]
- bind1st function [STL/CLR]
- bind2nd function [STL/CLR]
- binder1st function [STL/CLR]
- binder2nd function [STL/CLR]
- divides function [STL/CLR]
- equal_to function [STL/CLR]
- greater function [STL/CLR]
- greater_equal function [STL/CLR]
- less function [STL/CLR]
- less_equal function [STL/CLR]
- logical_and function [STL/CLR]
- logical_not function [STL/CLR]
- logical_or function [STL/CLR]
- minus function [STL/CLR]
- modulus function [STL/CLR]
- multiplies function [STL/CLR]
- negate function [STL/CLR]
- not_equal_to function [STL/CLR]
- not1 function [STL/CLR]
- not2 function [STL/CLR]
- plus function [STL/CLR]
- unary_delegate function [STL/CLR]
- unary_delegate_noreturn function [STL/CLR]
- unary_negate function [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 98640997536bc48330beeda793a6067e3da97b5f
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376368"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)
Dołącz nagłówek STL/CLR `<cliext/functional>` zdefiniować liczbę klasy szablonów i delegatów pokrewne szablonu i funkcje.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <functional>  
```  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext — / funkcjonalności >  
  
 **Namespace:** cliext — 

## <a name="declarations"></a>Deklaracje  
  
|Delegate|Opis|  
|--------------|-----------------|  
|[binary_delegate (STL/CLR)](#binary_delegate)|Delegat dwuargumentową.|  
|[binary_delegate_noreturn (STL/CLR)](#binary_delegate_noreturn)|Delegat dwuargumentową, zwracając **void**.|  
|[unary_delegate (STL/CLR)](#unary_delegate)|Delegat jeden argument.|  
|[unary_delegate_noreturn (STL/CLR)](#unary_delegate_noreturn)|One-argument — delegowanego, zwracając **void**.|  
  
|Class|Opis|  
|-----------|-----------------|  
|[binary_negate (STL/CLR)](#binary_negate)|Funktor do zanegowania funktor dwuargumentową.|  
|[binder1st (STL/CLR)](#binder1st)|Funktor, aby powiązać funktor dwóch argumentów pierwszy argument.|  
|[binder2nd (STL/CLR)](#binder2nd)|Funktor, aby powiązać funktor dwuargumentową drugi argument.|  
|[divides (STL/CLR)](#divides)|Podziel funktor.|  
|[equal_to (STL/CLR)](#equal_to)|Porównanie równego funktor.|  
|[greater (STL/CLR)](#greater)|Większa funktor porównania.|  
|[greater_equal (STL/CLR)](#greater_equal)|Większe lub równe porównania funktor.|  
|[less (STL/CLR)](#less)|Mniej funktor porównania.|  
|[less_equal (STL/CLR)](#less_equal)|Porównanie mniejsze lub równe funktor.|  
|[logical_and (STL/CLR)](#logical_and)|Logiczne AND funktor.|  
|[logical_not (STL/CLR)](#logical_not)|Logiczne nie funktor.|  
|[logical_or (STL/CLR)](#logical_or)|Logiczne lub funktor.|  
|[minus (STL/CLR)](#minus)|Odejmij funktor.|  
|[modulus (STL/CLR)](#modulus)|Modulo funktor.|  
|[multiplies (STL/CLR)](#multiplies)|Pomnóż funktor.|  
|[negate (STL/CLR)](#negate)|Funktor do zwrócenia jej argument ujemna.|  
|[not_equal_to (STL/CLR)](#not_equal_to)|Nie równa się porównanie funktor.|  
|[plus (STL/CLR)](#plus)|Dodaj funktor.|  
|[unary_negate (STL/CLR)](#unary_negate)|Funktor do zanegowania funktor jeden argument.|  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[bind1st (STL/CLR)](#bind1st)|Generuje binder1st — argument i funktor.|  
|[bind2nd (STL/CLR)](#bind2nd)|Generuje binder2nd — argument i funktor.|  
|[not1 (STL/CLR)](#not1)|Generuje unary_negate — dla funktorem.|  
|[not2 (STL/CLR)](#not2)|Generuje binary_negate — dla funktorem.|  
   
## <a name="members"></a>Elementy członkowskie

## <a name="binary_delegate"></a> binary_delegate — (STL/CLR)
Klasa genereic opisuje dwuargumentową delegata. Możesz użyć Określ delegata pod względem jego argumentów i typów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
generic<typename Arg1,  
    typename Arg2,  
    typename Result>  
    delegate Result binary_delegate(Arg1, Arg2);  
```  
  
#### <a name="parameters"></a>Parametry  
 *arg1*  
 Typ pierwszego argumentu.  
  
 *argument2*  
 Typ drugiego argumentu.  
  
 *wynik*  
 Typ zwracany.  
  
### <a name="remarks"></a>Uwagi  
 Delegat genereic opisano funkcję dwuargumentową.  
  
 Należy pamiętać, że dla:  
  
 `binary_delegate<int, int, int> Fun1;`  
  
 `binary_delegate<int, int, int> Fun2;`  
  
 typy `Fun1` i `Fun2` są synonimy, podczas gdy dla:  
  
 `delegate int Fun1(int, int);`  
  
 `delegate int Fun2(int, int);`  
  
 nie są tego samego typu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_binary_delegate.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
bool key_compare(wchar_t left, wchar_t right)   
    {   
    return (left < right);   
    }   
  
typedef cliext::binary_delegate<wchar_t, wchar_t, bool> Mydelegate;   
int main()   
    {   
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="binary_delegate_noreturn"></a> binary_delegate_noreturn — (STL/CLR)
Klasa genereic opisuje delegata dwuargumentową, która zwraca **void**. Możesz użyć Określ delegata pod kątem jej argument.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
generic<typename Arg1,  
    typename Arg2>  
    delegate void binary_delegate(Arg1, Arg2);  
```  
  
#### <a name="parameters"></a>Parametry  
 *arg1*  
 Typ pierwszego argumentu.  
  
 *argument2*  
 Typ drugiego argumentu.  
  
### <a name="remarks"></a>Uwagi  
 Delegat genereic w tym artykule opisano funkcję dwuargumentową, która zwraca **void**.  
  
 Należy pamiętać, że dla:  
  
 `binary_delegate_noreturn<int, int> Fun1;`  
  
 `binary_delegate_noreturn<int, int> Fun2;`  
  
 typy `Fun1` i `Fun2` są synonimy, podczas gdy dla:  
  
 `delegate void Fun1(int, int);`  
  
 `delegate void Fun2(int, int);`  
  
 nie są tego samego typu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_binary_delegate_noreturn.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
void key_compare(wchar_t left, wchar_t right)   
    {   
    System::Console::WriteLine("compare({0}, {1}) = {2}",   
        left, right, left < right);   
    }   
  
typedef cliext::binary_delegate_noreturn<wchar_t, wchar_t> Mydelegate;   
int main()   
    {   
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);   
  
    kcomp(L'a', L'a');   
    kcomp(L'a', L'b');   
    kcomp(L'b', L'a');   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
compare(a, a) = False  
compare(a, b) = True  
compare(b, a) = False  
```  

## <a name="binary_negate"></a> binary_negate — (STL/CLR)
Klasa szablonu opisuje funktorem, który po wywołaniu zwraca logiczny nie z jego przechowywanej funktor dwuargumentową. Możesz użyć Określ obiekt funkcyjny pod względem jego przechowywanej funktor.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Fun>  
    ref class binary_negate  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    explicit binary_negate(Fun% functor);  
    binary_negate(binary_negate<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *Zabawa*  
 Typ przechowywanych funktor.  
  
## <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
|stored_function_type|Typ funkcję.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|binary_negate|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|delegate_type^() — operator|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktorem dwuargumentową, który przechowuje inny dwuargumentową funktor. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, zwraca logiczny nie jest przechowywane funkcję o nazwie z dwóch argumentów.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_binary_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::less<int> less_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(),   
        cliext::binary_negate<cliext::less<int> >(less_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::not2(less_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
4 4  
1 0  
1 0  
```  

## <a name="bind1st"></a> bind1st — (STL/CLR)
Generuje `binder1st` argumentu i funktor.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Fun,  
    typename Arg>  
    binder1st<Fun> bind1st(Fun% functor,  
        Arg left);  
```  
  
#### <a name="template-parameters"></a>Parametry szablonu  
 *ARG*  
 Typ argumentu.  
  
 *Zabawa*  
 Typ funkcję.  
  
#### <a name="function-parameters"></a>Parametry funkcji  
 *funktor*  
 Funkcję do opakowania.  
  
 *left*  
 Pierwszy argument do opakowania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu zwraca [binder1st — (STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`. Służy jako wygodny sposób opakować funktor dwuargumentową i jej pierwszy argument w funktorem jeden argument, który ją wywołuje z drugiego argumentu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_bind1st.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        subfrom3);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind1st(sub_op, 3));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
-1 0  
-1 0  
```  

## <a name="bind2nd"></a> bind2nd — (STL/CLR)
Generuje `binder2nd` argumentu i funktor.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Fun,  
    typename Arg>  
    binder2nd<Fun> bind2nd(Fun% functor,  
        Arg right);  
```  
  
#### <a name="template-parameters"></a>Parametry szablonu  
 *ARG*  
 Typ argumentu.  
  
 *Zabawa*  
 Typ funkcję.  
  
#### <a name="function-parameters"></a>Parametry funkcji  
 *funktor*  
 Funkcję do opakowania.  
  
 *right*  
 Drugi argument do opakowania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu zwraca [binder2nd — (STL/CLR)](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`. Służy jako wygodny sposób zabalit funktorem jeden argument, który ją wywołuje, którego pierwszy argument funktor dwuargumentową i drugi argument.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_bind2nd.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        sub4);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind2nd(sub_op, 4));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
0 -1  
0 -1  
```  

## <a name="binder1st"></a> binder1st — (STL/CLR)
Klasa szablonu opisuje funktor one-argument — który, po wywołaniu zwraca jego przechowywanej funktor dwuargumentową volat swój pierwszy argument przechowywanych i dostarczony drugi argument. Możesz użyć Określ obiekt funkcyjny pod względem jego przechowywanej funktor.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Fun>  
    ref class binder1st  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef typename Fun:result_type result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        second_argument_type, result_type>  
        delegate_type;  
  
    binder1st(Fun% functor, first_argument_type left);  
    binder1st(binder1st<Arg>% right);  
  
    result_type operator()(second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *Zabawa*  
 Typ przechowywanych funktor.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
|stored_function_type|Typ funkcję.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|binder1st|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|delegate_type^() — operator|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktorem jeden argument, który przechowuje funktor dwuargumentową i pierwszy argument. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, funkcja zwraca wynik wywołania przechowywanych funktor za pomocą składowanych pierwszy argument i dostarczony drugi argument.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_binder1st.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        subfrom3);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind1st(sub_op, 3));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
-1 0  
-1 0  
```  

## <a name="binder2nd"></a> binder2nd — (STL/CLR)
Klasa szablonu opisuje funktor one-argument — który, po wywołaniu zwraca jego przechowywanej funktor dwuargumentową volat podane pierwszy argument i jego przechowywanej drugi argument. Możesz użyć Określ obiekt funkcyjny pod względem jego przechowywanej funktor.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Fun>  
    ref class binder2nd  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef typename Fun:result_type result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        first_argument_type, result_type>  
        delegate_type;  
  
    binder2nd(Fun% functor, second_argument_type left);  
    binder2nd(binder2nd<Arg>% right);  
  
    result_type operator()(first_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *Zabawa*  
 Typ przechowywanych funktor.  
  
## <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
|stored_function_type|Typ funkcję.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|binder2nd|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|delegate_type^() — operator|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktorem jeden argument, który przechowuje funktor dwuargumentową i drugi argument. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, funkcja zwraca wynik wywołania przechowywanych funktor przy użyciu podanej pierwszy argument i przechowywanych drugi argument.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_binder2nd.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        sub4);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind2nd(sub_op, 4));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
0 -1  
0 -1  
```  
  
## <a name="divides"></a> dzieli (STL/CLR)
Klasa szablonu opisuje funktorem, gdy zostanie wywołana, zwraca wartość pierwszego argumentu podzieloną przez drugi. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class divides  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    divides();  
    divides(divides<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typ argumentów i wartości zwracanej.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|divides|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|delegate_type^() — operator|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor dwuargumentową. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, zwraca wartość pierwszego argumentu podzieloną przez drugi.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_divides.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::divides<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
2 1  
2 3  
```  

## <a name="equal_to"></a> equal_to — (STL/CLR)
Klasa szablonu opisuje funktorem, gdy zostanie wywołana, zwraca wartość true tylko wtedy, gdy jest to pierwszy argument jest równe drugiemu. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class equal_to  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    equal_to();  
    equal_to(equal_to<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typy argumentów.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|equal_to|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|delegate_type^() — operator|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor dwuargumentową. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, zwraca wartość true, tylko jeśli pierwszy argument jest równe drugiemu.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_equal_to.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::equal_to<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
4 4  
1 0  
```  

## <a name="greater"></a> większa (STL/CLR)
Klasa szablonu opisuje funktorem, gdy zostanie wywołana, zwraca wartość true tylko wtedy, gdy jest to pierwszy argument jest większy od drugiego. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class greater  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    greater();  
    greater(greater<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typy argumentów.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|greater|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor dwuargumentową. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, zwraca wartość true, tylko jeśli pierwszy argument jest większy od drugiego.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_greater.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(3);   
    c2.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 3 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::greater<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
3 3  
1 0  
```  

## <a name="greater_equal"></a> greater_equal — (STL/CLR)
Klasa szablonu opisuje funktorem, gdy zostanie wywołana, zwraca wartość true, tylko jeśli pierwszy argument jest większy niż lub równe drugiemu. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class greater_equal  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    greater_equal();  
    greater_equal(greater_equal<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typy argumentów.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|greater_equal|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor dwuargumentową. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, zwraca wartość true, tylko jeśli pierwszy argument jest większy niż lub równe drugiemu.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_greater_equal.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::greater_equal<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
4 4  
1 0  
```  

## <a name="less"></a> mniej (STL/CLR)
Klasa szablonu opisuje funktorem, gdy zostanie wywołana, zwraca wartość true tylko wtedy, gdy jest to pierwszy argument jest mniejszy od drugiego. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class less  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    less();  
    less(less<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typy argumentów.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|less|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor dwuargumentową. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, zwraca wartość true, tylko jeśli pierwszy argument jest mniejszy od drugiego.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_less.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::less<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
4 4  
0 1  
``` 

## <a name="less_equal"></a> less_equal — (STL/CLR)
Klasa szablonu opisuje funktorem, gdy zostanie wywołana, zwraca wartość true, tylko jeśli pierwszy argument jest mniejszy niż lub równe drugiemu. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class less_equal  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    less_equal();  
    less_equal(less_equal<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typy argumentów.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|less_equal|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor dwuargumentową. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, zwraca wartość true, tylko jeśli pierwszy argument jest mniejszy niż lub równe drugiemu.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_less_equal.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(3);   
    c2.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 3 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::less_equal<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
3 3  
0 1  
``` 

## <a name="logical_and"></a> logical_and — (STL/CLR)
Klasa szablonu opisuje funktorem, gdy zostanie wywołana, zwraca wartość true tylko wtedy, gdy jest to pierwszy argument i drugi test jako wartość true. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class logical_and  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    logical_and();  
    logical_and(logical_and<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typy argumentów.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|logical_and|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor dwuargumentową. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, zwraca wartość true, tylko jeśli pierwszy argument i drugi test jako wartość true.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_logical_and.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(2);   
    c1.push_back(0);   
    Myvector c2;   
    c2.push_back(3);   
    c2.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 1 0" and " 1 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::logical_and<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
2 0  
3 0  
1 0  
``` 

## <a name="logical_not"></a> logical_not — (STL/CLR)
Klasa szablonu opisuje funktorem, gdy zostanie wywołana, zwraca wartość true tylko wtedy, gdy albo jej argument testy jako wartość false. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class logical_not  
    { // wrap operator()  
public:  
    typedef Arg argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    logical_not();  
    logical_not(logical_not<Arg> %right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typy argumentów.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|argument_type|Typ argumentu funktor.|  
|delegate_type|Typ delegata ogólnego.|  
|Element result_type|Typ wyniku funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|logical_not|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor jeden argument. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, jego zwraca wartość true, tylko jeśli jej argument testy jako wartość false.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_logical_not.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c3.begin(), cliext::logical_not<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 0  
0 1  
``` 

## <a name="logical_or"></a> logical_or — (STL/CLR)
Klasa szablonu opisuje funktorem, gdy zostanie wywołana, zwraca wartość true tylko wtedy, gdy jest to pierwszy argument lub drugie testów jako wartość true. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class logical_or  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    logical_or();  
    logical_or(logical_or<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typy argumentów.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|logical_or|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor dwuargumentową. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, zwraca wartość true, tylko jeśli pierwszy argument lub drugie testów jako wartość true.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_logical_or.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(2);   
    c1.push_back(0);   
    Myvector c2;   
    c2.push_back(0);   
    c2.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 2 0" and " 0 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::logical_or<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
2 0  
0 0  
1 0  
```      

## <a name="minus"></a> minus (STL/CLR)
Klasa szablonu opisuje funktorem, gdy zostanie wywołana, zwraca wartość pierwszego argumentu, minus sekundę. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class minus  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    minus();  
    minus(minus<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typ argumentów i wartości zwracanej.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|minus|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor dwuargumentową. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, zwraca wartość pierwszego argumentu, minus sekundę.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_minus.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::minus<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
2 1  
2 2  
``` 

## <a name="modulus"></a> modulo (STL/CLR)
Klasa szablonu opisuje funktorem, który po wywołaniu zwraca pierwszy argument modulo drugiego. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class modulus  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    modulus();  
    modulus(modulus<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typ argumentów i wartości zwracanej.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|modulus|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor dwuargumentową. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, funkcja zwraca pierwszy argument modulo drugiego.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_modulus.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(2);   
    Myvector c2;   
    c2.push_back(3);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 2" and " 3 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::modulus<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 2  
3 1  
1 0  
```   

## <a name="multiplies"></a> Mnoży (STL/CLR)
Klasa szablonu opisuje funktorem, który po wywołaniu zwraca pierwszy argument razy drugiego. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class multiplies  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    multiplies();  
    multiplies(multiplies<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typ argumentów i wartości zwracanej.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|multiplies|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor dwuargumentową. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, funkcja zwraca pierwszy argument razy drugiego.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_multiplies.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::multiplies<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
2 1  
8 3  
```  

## <a name="negate"></a> negate — (STL/CLR)
Klasa szablonu opisuje funktorem, który po wywołaniu zwraca jej argument ujemna. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class negate  
    { // wrap operator()  
public:  
    typedef Arg argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    negate();  
    negate(negate<Arg>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typy argumentów.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|argument_type|Typ argumentu funktor.|  
|delegate_type|Typ delegata ogólnego.|  
|Element result_type|Typ wyniku funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|negate|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor jeden argument. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, funkcja zwraca jej argument ujemna.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(-3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 -3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c3.begin(), cliext::negate<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 -3  
-4 3  
``` 

## <a name="not_equal_to"></a> not_equal_to — (STL/CLR)
Klasa szablonu opisuje funktorem, gdy zostanie wywołana, zwraca wartość true tylko wtedy, gdy jest to pierwszy argument nie jest równe drugiemu. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class not_equal_to  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    not_equal_to();  
    not_equal_to(not_equal_to<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typy argumentów.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|not_equal_to|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor dwuargumentową. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, zwraca wartość true, tylko jeśli pierwszy argument nie jest równe drugiemu.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_not_equal_to.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::not_equal_to<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
4 4  
0 1  
```   

## <a name="not1"></a> not1 — (STL/CLR)
Generuje `unary_negate` dla funktorem.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Fun>  
    unary_negate<Fun> not1(Fun% functor);  
```  
  
#### <a name="template-parameters"></a>Parametry szablonu  
 *Zabawa*  
 Typ funkcję.  
  
#### <a name="function-parameters"></a>Parametry funkcji  
 *funktor*  
 Funkcję do opakowania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu zwraca [unary_negate — (STL/CLR)](../dotnet/unary-negate-stl-clr.md)`<Fun>(functor)`. Służy jako wygodny sposób opakować funktor jeden argument w funktorem, który dostarcza jego logiczne NOT.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_not1.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::logical_not<int> not_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::unary_negate<cliext::logical_not<int> >(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::not1(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 0  
1 0  
1 0  
```  

## <a name="not2"></a> not2 — (STL/CLR)
Generuje `binary_negate` dla funktorem.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Fun>  
    binary_negate<Fun> not2(Fun% functor);  
```  
  
#### <a name="template-parameters"></a>Parametry szablonu  
 *Zabawa*  
 Typ funkcję.  
  
#### <a name="function-parameters"></a>Parametry funkcji  
 *funktor*  
 Funkcję do opakowania.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu zwraca [binary_negate — (STL/CLR)](../dotnet/binary-negate-stl-clr.md)`<Fun>(functor)`. Służy jako wygodny sposób zabalit funktor dwuargumentową funktorem, który dostarcza jego logiczne NOT.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_not2.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::less<int> less_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(),   
        cliext::binary_negate<cliext::less<int> >(less_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::not2(less_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
4 4  
1 0  
1 0  
```  

## <a name="plus"></a> plus (STL/CLR)
Klasa szablonu opisuje funktorem, gdy zostanie wywołana, funkcja zwraca pierwszy argument, a także drugi. Możesz użyć Określ obiekt funkcyjny pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Arg>  
    ref class plus  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    plus();  
    plus(plus<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typ argumentów i wartości zwracanej.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|delegate_type|Typ delegata ogólnego.|  
|first_argument_type|Typ pierwszego argumentu funktor.|  
|Element result_type|Typ wyniku funktor.|  
|second_argument_type|Typ drugiego argumentu funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|plus|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|Operator delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktor dwuargumentową. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, zwraca pierwszy argument, a także drugi.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_plus.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::plus<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 3  
2 1  
6 4  
```  

## <a name="unary_delegate"></a> unary_delegate — (STL/CLR)
Klasa genereic opisuje delegata jeden argument. Możesz użyć Określ delegata pod względem jego argumentów i typów.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
generic<typename Arg,  
    typename Result>  
    delegate Result unary_delegate(Arg);  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typ argumentu.  
  
 *wynik*  
 Typ zwracany.  
  
### <a name="remarks"></a>Uwagi  
 Delegat genereic opisano funkcję jeden argument.  
  
 Należy pamiętać, że dla:  
  
 `unary_delegare<int, int> Fun1;`  
  
 `unary_delegare<int, int> Fun2;`  
  
 typy `Fun1` i `Fun2` są synonimy, podczas gdy dla:  
  
 `delegate int Fun1(int);`  
  
 `delegate int Fun2(int);`  
  
 nie są tego samego typu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_unary_delegate.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
int hash_val(wchar_t val)   
    {   
    return ((val * 17 + 31) % 67);   
    }   
  
typedef cliext::unary_delegate<wchar_t, int> Mydelegate;   
int main()   
    {   
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
```  
  
```Output  
hash(L'a') = 5  
hash(L'b') = 22  
```  

## <a name="unary_delegate_noreturn"></a> unary_delegate_noreturn — (STL/CLR)
Klasa genereic opisuje delegat jeden argument, który zwraca **void**. Możesz użyć Określ delegata pod względem jego typ argumentu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
generic<typename Arg>  
    delegate void unary_delegate_noreturn(Arg);  
```  
  
#### <a name="parameters"></a>Parametry  
 *ARG*  
 Typ argumentu.  
  
### <a name="remarks"></a>Uwagi  
 Delegat genereic zawiera opis funkcji jednym argumentem, która zwraca **void**.  
  
 Należy pamiętać, że dla:  
  
 `unary_delegare_noreturn<int> Fun1;`  
  
 `unary_delegare_noreturn<int> Fun2;`  
  
 typy `Fun1` i `Fun2` są synonimy, podczas gdy dla:  
  
 `delegate void Fun1(int);`  
  
 `delegate void Fun2(int);`  
  
 nie są tego samego typu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_unary_delegate_noreturn.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
void hash_val(wchar_t val)   
    {   
    System::Console::WriteLine("hash({0}) = {1}",   
       val, (val * 17 + 31) % 67);   
    }   
  
typedef cliext::unary_delegate_noreturn<wchar_t> Mydelegate;   
int main()   
    {   
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);   
  
    myhash(L'a');   
    myhash(L'b');   
    return (0);   
    }  
```  
  
```Output  
hash(a) = 5  
hash(b) = 22  
```  

## <a name="unary_negate"></a> unary_negate — (STL/CLR)
Klasa szablonu opisuje funktorem, który po wywołaniu zwraca logiczny nie z jego przechowywanej funktor jeden argument. Możesz użyć Określ obiekt funkcyjny pod względem jego przechowywanej funktor.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Fun>  
    ref class unary_negate  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::argument_type argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    unary_negate(Fun% functor);  
    unary_negate(unary_negate<Fun>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 *Zabawa*  
 Typ przechowywanych funktor.  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|argument_type|Typ argumentu funktor.|  
|delegate_type|Typ delegata ogólnego.|  
|Element result_type|Typ wyniku funktor.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|unary_negate|Tworzy funkcję.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|delegate_type ^|Rzutuje funktor do delegata.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje funktorem jeden argument, który przechowuje inny funktor jeden argument. Definiuje operator składowy `operator()` tak, że gdy obiekt jest wywoływana jako funkcja, zwraca logiczny nie jest przechowywane funktor wywołane z argumentem.  
  
 Możesz też przekazać obiekt jako argumentu funkcji, którego typem jest `delegate_type^` i zostanie przekonwertowany odpowiednio.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// cliext_unary_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::logical_not<int> not_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::unary_negate<cliext::logical_not<int> >(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::not1(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
4 0  
1 0  
1 0  
```  