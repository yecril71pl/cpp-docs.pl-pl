---
title: Funkcje śródwierszowe (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __forceinline_cpp
- __inline_cpp
- inline_cpp
dev_langs:
- C++
helpviewer_keywords:
- inline functions [C++], class members
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b39a6889dfd8a28d65aebcab04881d4bc28ce1e
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403670"
---
# <a name="inline-functions-c"></a>Funkcje śródwierszowe (C++)
Funkcję zdefiniowaną w treści deklaracji klasy jest funkcją śródwierszową.  
  
## <a name="example"></a>Przykład  
 W poniższej deklaracji klasy `Account` Konstruktor jest funkcją śródwierszową. Funkcje elementów członkowskich `GetBalance`, `Deposit`, i `Withdraw` nie są określone jako **wbudowane** , ale można zaimplementować jako wbudowane funkcje.  
  
```cpp 
// Inline_Member_Functions.cpp  
class Account  
{  
public:  
    Account(double initial_balance) { balance = initial_balance; }  
    double GetBalance();  
    double Deposit( double Amount );  
    double Withdraw( double Amount );  
private:  
    double balance;  
};  
  
inline double Account::GetBalance()  
{  
    return balance;  
}  
  
inline double Account::Deposit( double Amount )  
{  
    return ( balance += Amount );  
}  
  
inline double Account::Withdraw( double Amount )  
{  
    return ( balance -= Amount );  
}  
int main()  
{  
}  
```  
  
> [!NOTE]
>  W deklaracji klasy, funkcje zostały zadeklarowane bez **wbudowane** — słowo kluczowe. **Wbudowane** — słowo kluczowe może być określony w deklaracji klasy; wynik jest taki sam.  
  
 Wbudowane danej funkcji składowej musi być zadeklarowany w taki sam sposób, w każdej jednostki kompilacji. To ograniczenie powoduje, że wbudowane funkcje, aby zachowywać się tak, jakby były one funkcje wystąpień. Ponadto musi być dokładnie jednej definicji wbudowanej funkcji.  
  
 Funkcji składowej klasy wartość domyślna to powiązanie zewnętrzne, chyba że zawiera definicję dla tej funkcji **wbudowane** specyfikator. Powyższy przykład pokazuje, że te funkcje nie musi jawnie zadeklarowane z **wbudowane** specyfikator; przy użyciu **wbudowane** w funkcji definicji powoduje, że do wbudowanej funkcji. Jednak nie jest dozwolone ponownie zadeklarować funkcję jako **wbudowane** po wywołaniu tej funkcji.  
  
## <a name="inline-inline-and-forceinline"></a>W tekście, __inline, i \__forceinline  
 **Wbudowane** i **__inline** specyfikatory poinstruować kompilator, aby wstawić kopię treści funkcji do każdego miejsca, w wywołaniu funkcji.  
  
 Wstawianie (o nazwie wbudowane rozwijanie lub inlining) występuje tylko wtedy, gdy analizy kosztów i korzyści kompilatora wyświetlane jako zysków. Wbudowane rozwijanie pozwala uniknąć wywołania funkcji obciążenie na potencjalnych kosztów większego rozmiaru kodu.  
  
 **__Forceinline** — słowo kluczowe zastępuje analizy kosztów i korzyści i opiera się na ocenie programisty. Należy zachować ostrożność przy użyciu **__forceinline**. Użycie nieograniczonego **__forceinline** może powodować większe kodu za pomocą tylko wzrost wydajności brzegowych lub, w niektórych przypadkach nawet spadek wydajności (z powodu zwiększonej stronicowanie większe pliki wykonywalne, na przykład).  
  
 Za pomocą wbudowanych funkcji można szybciej program ponieważ eliminuje obciążenia związanego z wywołania funkcji. Rozwinięty wbudowanych funkcji jest zależna od optymalizacji kodu nie jest dostępna do normalnej pracy.  
  
 Kompilator traktuje opcje rozszerzenia wbudowane i słów kluczowych jako sugestie. Nie ma żadnej gwarancji, funkcje będą śródwierszowych. Nie można wymusić na kompilatorze wbudowane określonej funkcji, nawet w przypadku **__forceinline** — słowo kluczowe. Podczas kompilowania za pomocą **/CLR**, kompilator będzie niewyrównane funkcji w przypadku atrybutów zabezpieczeń zastosowanych do funkcji.  
  
 **Wbudowane** — słowo kluczowe jest dostępne tylko w języku C++. **__Inline** i **__forceinline** słowa kluczowe są dostępne w C i C++. W celu zgodności z poprzednimi wersjami **_inline** jest synonimem dla **__inline**.  
  
 **Wbudowane** — słowo kluczowe informuje kompilator, że wbudowane rozwijanie jest preferowana. Jednak kompilator może utworzyć osobne wystąpienie funkcji (wystąpienia) i tworzenia standardowych powiązań wywoływania zamiast Wstawianie kod inline. Są dwa przypadki, w których taka sytuacja może wystąpić:  
  
-   Funkcje rekursywne.  
  
-   Funkcje, które są określane za pomocą wskaźnika w innym miejscu w jednostce translacji.  
  
 Z tego powodu może zakłócać wstawienia, zrównoważenia *jak inne osoby mogą*, według uznania kompilatora; użytkownik nie powinien zależeć **wbudowane** specyfikator, aby wywołać funkcję, która ma być śródwierszowa.  
  
 Podobnie jak w przypadku normalnych funkcji ma ma zdefiniowanej kolejności oceny argumenty do wbudowanej funkcji. W rzeczywistości może być inna niż kolejność, w której argumenty są obliczane przy przekazywaniu przy użyciu protokołu wywołanie normalnej funkcji.  
  
 [/Ob](../build/reference/ob-inline-function-expansion.md) opcja optymalizacji kompilatora pomaga ustalić, czy rozwijania funkcji inline rzeczywiście występuje.  
  
 [/ LTCG](../build/reference/ltcg-link-time-code-generation.md) wykonuje optimalizaci Mezi wbudowanie niezależnie od tego, czy zażądano w kodzie źródłowym.  
  
### <a name="example-1"></a>Przykład 1  
  
```cpp 
// inline_keyword1.cpp  
// compile with: /c  
inline int max( int a , int b ) {  
   if( a > b )   
      return a;  
   return b;  
}  
```  
  
 Funkcje składowych klasy mogą być deklarowane przy użyciu wbudowanego **wbudowane** — słowo kluczowe lub umieszczając definicji funkcji w ramach definicji klasy.  
  
### <a name="example-2"></a>Przykład 2  
  
```cpp 
// inline_keyword2.cpp  
// compile with: /EHsc /c  
#include <iostream>  
using namespace std;  
  
class MyClass {  
public:  
   void print() { cout << i << ' '; }   // Implicitly inline  
private:  
   int i;  
};  
```  
  
### <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 **__Inline** — słowo kluczowe jest odpowiednikiem **wbudowane**.  
  
 Nawet w przypadku **__forceinline**, kompilator nie kodu wbudowanego w każdych okolicznościach. Kompilator nie wbudowanych funkcji, jeśli:  
  
-   Funkcja lub jego element wywołujący jest kompilowany za pomocą /Ob0 (opcja domyślna do debugowania kompilacji).  
  
-   Funkcja i element wywołujący używają różnych typów (Obsługa wyjątków języka C++ w jednym, obsługa w innych wyjątków strukturalnych) obsługi wyjątków.  
  
-   Funkcja ma listy zmiennych argumentów.  
  
-   Funkcja używa zestawu wbudowanego, chyba że skompilowany przy użyciu /Og, OX, / O1 lub/O2.  
  
-   Funkcja plików jest cykliczna i nie towarzyszy **#pragma inline_recursion(on)**. Pragma śródwierszowych na domyślne głębokość wywołań 16 są funkcji rekursywnych. Aby zmniejszyć wbudowanie głębi, użyj [inline_depth](../preprocessor/inline-depth.md) pragmy.  
  
-   Funkcja jest wirtualny i nosi nazwę praktycznie. Bezpośrednie wywołania do funkcji wirtualnych może być śródwierszowa.  
  
-   Program przyjmuje adres funkcji i wywołanie za pomocą wskaźnika do funkcji. Bezpośrednie wywołania do funkcji, które były ich zajęty adres może być śródwierszowa.  
  
-   Funkcja również jest oznaczona za pomocą ["naked"](../cpp/naked-cpp.md) [__declspec](../cpp/declspec.md) modyfikator.  
  
 Jeśli kompilator nie wbudowanej funkcji zadeklarowanych za pomocą **__forceinline**, generuje ostrzeżenia poziomu 1, z wyjątkiem sytuacji, gdy:
  
-   Funkcja jest kompilowany przy użyciu /Od lub /Ob0. Nie wbudowanie oczekuje się w tych przypadkach.     
  
-   Funkcja jest zdefiniowana zewnętrznie, biblioteka lub innej jednostce translacji, lub jest cel wywołania wirtualnego cel wywołania pośredniego. Kompilator nie może zidentyfikować-śródwierszowych kod, który nie można znaleźć w bieżącej jednostce tłumaczenia.  
  
 Funkcje rekursywne mogą być wbudowane podstawione o szerokości określonej przez [inline_depth](../preprocessor/inline-depth.md) pragma maksymalnie 16 wywołań. Po tym głębokość wywołania funkcji rekursywnych są traktowane jako wywołania wystąpienie funkcji.  Głębokość do cyklicznego, które funkcje są sprawdzane przez Algorytm heurystyczny tekście nie może przekraczać 16. [Inline_recursion](../preprocessor/inline-recursion.md) pragma kontroluje wbudowane rozwijanie funkcji umieszczono rozszerzenia. Zobacz [rozszerzenie funkcji wbudowanej](../build/reference/ob-inline-function-expansion.md) (/ Ob) opcję kompilatora, aby uzyskać powiązane informacje.  
  
**END specyficzny dla Microsoft**  
 Aby uzyskać więcej informacji na temat korzystania z **wbudowane** specyfikator, zobacz:  
  
-   [Funkcje Członkowskie klasy wewnętrznej](../cpp/inline-functions-cpp.md)  
  
-   [Definiowanie funkcji śródwierszowych języka C++ z dllexport i dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)  
  
## <a name="when-to-use-inline-functions"></a>Kiedy należy używać funkcji śródwierszowych  
 Funkcje śródwierszowe, najlepiej sprawdzają się dla małych funkcji, takich jak uzyskiwanie dostępu do danych prywatnych elementów członkowskich. Głównym celem tych funkcji "metody dostępu" jednego lub dwóch wierszy jest do zwracania informacji o stanie dotyczących obiektów; krótkich funkcji są wrażliwe na obciążenie związane z wywołania funkcji. Dłużej funkcje poświęcać proporcjonalnie w sekwencji wywołania/zwracaniu i mniejszy od korzyści ze śródwierszowaniem.  
  
 Element `Point` klasy można zdefiniować w następujący sposób:  
  
```cpp 
// when_to_use_inline_functions.cpp  
class Point  
{  
public:  
    // Define "accessor" functions as  
    //  reference types.  
    unsigned& x();  
    unsigned& y();  
private:  
    unsigned _x;  
    unsigned _y;  
};  
  
inline unsigned& Point::x()  
{  
    return _x;  
}  
inline unsigned& Point::y()  
{  
    return _y;  
}  
int main()  
{  
}  
```  
  
 Zakładając, manipulowania współrzędnych jest stosunkowo typowych operacji w kliencie klasy takie, określając dwie funkcje metod dostępu (`x` i `y` w powyższym przykładzie) jako **wbudowane** zwykle zapisuje Obciążenie:  
  
-   Wywołania funkcji (w tym przekazywanie parametrów i wprowadzania adresu obiektu na stosie)  
  
-   Zachowanie obiektu wywołującego ramki stosu  
  
-   Konfiguracja nowej ramki stosu  
  
-   Zwracana wartość komunikacji  
  
-   Stary przywracania ramki stosu  
  
-   Wróć  
  
## <a name="inline-functions-vs-macros"></a>Funkcje śródwierszowe a makra  
 Chociaż funkcje wbudowane są podobne do makra (ponieważ jest to kod funkcji jest rozwinięte punkcie rozmowy w czasie kompilacji), wbudowane funkcje są analizowane przez kompilator, a makra rozwijane przez preprocesor. W rezultacie istnieje kilka istotnych różnic:  
  
-   Wbudowane funkcje wykonaj wszystkie protokoły bezpieczeństwa typu wymuszane na normalnej pracy.  
  
-   Wbudowane funkcje są określane za pomocą tej samej składni w innych funkcji, z tą różnicą, że zawierają one **wbudowane** — słowo kluczowe w deklaracji funkcji.  
  
-   Wyrażenia przekazywane jako argumenty do funkcji śródwierszowych są wykonywane tylko raz. W niektórych przypadkach wyrażenia przekazywane jako argumenty do makra mogą być obliczane więcej niż jeden raz.  
  
 Poniższy przykład pokazuje makra, która konwertuje małe litery na wielkie litery:  
  
```cpp 
// inline_functions_macro.c  
#include <stdio.h>  
#include <conio.h>  
  
#define toupper(a) ((a) >= 'a' && ((a) <= 'z') ? ((a)-('a'-'A')):(a))  
  
int main() {  
   char ch;  
   printf_s("Enter a character: ");  
   ch = toupper( getc(stdin) );  
   printf_s( "%c", ch );  
}  
//  Sample Input:  xyz  
// Sample Output:  Z  
```  
  
 Celem wyrażenie `toupper(getc(stdin))` jest, że znak są odczytywane z urządzenia z konsoli (`stdin`) i, jeśli to konieczne, są konwertowane na wielkie litery.  
  
 Ze względu na implementację makra `getc` raz wykonane, aby ustalić, czy znak jest większa niż lub równe "a", a po ustalenie, czy jest mniejsze niż lub równe "z". Jeśli w tym zakresie `getc` jest ponownie wykonywane w celu konwersji znaku na wielkie litery. Oznacza to, że program oczekuje na dwóch lub trzech znaków, gdy w idealnym przypadku należy czekać tylko dla jednego.  
  
 Funkcje śródwierszowe rozwiązać problem opisany wcześniej:  
  
```cpp 
// inline_functions_inline.cpp  
#include <stdio.h>  
#include <conio.h>  
  
inline char toupper( char a ) {  
   return ((a >= 'a' && a <= 'z') ? a-('a'-'A') : a );  
}  
  
int main() {  
   printf_s("Enter a character: ");  
   char ch = toupper( getc(stdin) );  
   printf_s( "%c", ch );  
}  
```  
  
```Output  
Sample Input: a  
Sample Output: A  
```  
  
## <a name="see-also"></a>Zobacz także  
 [noinline](../cpp/noinline.md)   
 [auto_inline](../preprocessor/auto-inline.md)