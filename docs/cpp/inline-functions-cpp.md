---
title: "Funkcje śródwierszowe (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __forceinline_cpp
- __inline_cpp
- inline_cpp
dev_langs: C++
helpviewer_keywords: inline functions [C++], class members
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: de370d8dbff1f1340539adc825f7f5316c59a468
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="inline-functions-c"></a>Funkcje śródwierszowe (C++)
Funkcji zdefiniowanej w treści deklaracji klasy jest wbudowanej funkcji.  
  
## <a name="example"></a>Przykład  
 W deklaracji klasy następujące `Account` Konstruktor jest wbudowanej funkcji. Funkcje Członkowskie `GetBalance`, `Deposit`, i `Withdraw` nie są określone jako **wbudowanego** , ale może być zaimplementowany jako funkcji śródwierszowych.  
  
```  
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
>  W deklaracji klasy funkcje zostały zgłoszone bez **wbudowanego** — słowo kluczowe. **Wbudowanego** — słowo kluczowe może być określony w deklaracji klasy; wynik jest taka sama.  
  
 Funkcji wbudowanej danego elementu członkowskiego musi być zadeklarowana tak samo w każdej jednostki kompilacji. Wbudowane funkcje do zachowują się tak, jakby były wystąpień funkcji powoduje, że to ograniczenie. Ponadto musi być dokładnie jednej definicji wbudowanej funkcji.  
  
 Funkcja członkowska klasy Domyślnie połączenie zewnętrzne o ile nie zawiera definicji dla tej funkcji **wbudowanego** specyfikator. W poprzednim przykładzie pokazano, że funkcje te nie muszą jawnie deklarować z **wbudowanego** specyfikator; przy użyciu **wbudowanego** w funkcji definicji powoduje, że należy wbudowanej funkcji. Jednak nie jest dozwolone ponownie zadeklarować funkcji jako **wbudowanego** po wywołaniu tej funkcji.  
  
## <a name="inline-inline-and-forceinline"></a>W tekście, __inline, i \__forceinline  
 `inline` i `__inline` specyfikatory poinstruować kompilator, aby wstawić kopię treści funkcji do każdego miejsca wywołania funkcji.  
  
 Wstawiania (wywołać rozszerzenie funkcji wbudowanej lub ze śródwierszowaniem) występuje tylko wtedy, gdy analiza kosztów i korzyści kompilatora wyświetleniem być korzystne. Rozszerzenie funkcji wbudowanej wyeliminować wywołania funkcji narzut na potencjalne koszty większego rozmiaru kodu.  
  
 `__forceinline` — Słowo kluczowe zastępuje analizy kosztów i korzyści i zamiast tego opiera się na ocenie programisty. Należy zachować ostrożność przy użyciu `__forceinline`. Niekontrolowane stosowanie `__forceinline` może powodować większe kodu za pomocą tylko wzrost wydajności brzegowego lub, w niektórych przypadkach, nawet spadek wydajności (ze względu na zwiększenie stronicowania większych pliku wykonywalnego, na przykład).  
  
 Przy użyciu funkcji śródwierszowych można szybciej program ponieważ eliminuje obciążenia związanego z wywołania funkcji. Funkcje rozwinięte wbudowanego podlegają optymalizacji kodu nie jest dostępny do normalnej pracy.  
  
 Kompilator traktuje wbudowane opcje rozszerzeń i słowa kluczowe jako sugestie. Nie ma żadnej gwarancji, że funkcje są wbudowane. Nie można wymusić na kompilatorze wbudowanego konkretną funkcję, nawet w przypadku `__forceinline` — słowo kluczowe. Podczas kompilowania za pomocą **/CLR**, kompilator będzie niewyrównane funkcji w przypadku atrybutów zabezpieczeń zastosowanych dla funkcji.  
  
 **Wbudowanego** — słowo kluczowe jest dostępna tylko w języku C++. `__inline` i `__forceinline` słowa kluczowe są dostępne zarówno C i C++. Zgodność z poprzednimi wersjami **_inline** jest synonimem `__inline`.  
  
 **Wbudowanego** — słowo kluczowe informuje kompilator, że rozszerzenie funkcji wbudowanej jest preferowana. Jednak utworzyć oddzielnego wystąpienia funkcji Kompilator (wystąpienia) i tworzenia standardowego powiązań wywoływania zamiast Wstawianie wbudowanego kodu. Przypadków, gdy jest to możliwe są następujące:  
  
-   Funkcje rekursywne.  
  
-   Funkcje, które są określane za pomocą wskaźnika w innym miejscu w jednostce tłumaczenia.  
  
 Z tego względu może zakłócać ze śródwierszowaniem, *jak inne osoby mogą*, według uznania kompilatora; nie należy uwzględniać na **wbudowanego** specyfikator spowodować funkcję, która ma zostać umieszczona w tekście.  
  
 Podobnie jak w przypadku normalnej pracy jest nie zdefiniowanej kolejności obliczania argumentów do wbudowanej funkcji. W rzeczywistości może być inna niż kolejność, w którym argumenty są oceniane po upływie przy użyciu protokołu wywołanie funkcji normalnego.  
  
 [/Ob](../build/reference/ob-inline-function-expansion.md) opcję optymalizacji kompilatora pozwala określić, czy rozszerzenie funkcji wbudowanej funkcji rzeczywiście występowała.  
  
 [/ LTCG](../build/reference/ltcg-link-time-code-generation.md) wykonuje między modułami niezależnie od tego, czy żądano w kodzie źródłowym.  
  
### <a name="example-1"></a>Przykład 1  
  
```  
// inline_keyword1.cpp  
// compile with: /c  
inline int max( int a , int b ) {  
   if( a > b )   
      return a;  
   return b;  
}  
```  
  
 Funkcje elementów członkowskich klasy mogą być deklarowane przy użyciu wbudowanego **wbudowanego** — słowo kluczowe lub umieszczając definicji funkcji w definicji klasy.  
  
### <a name="example-2"></a>Przykład 2  
  
```  
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
 `__inline` — Słowo kluczowe jest odpowiednikiem **wbudowanego**.  
  
 Nawet w przypadku `__forceinline`, kompilator nie kodu wbudowanego we wszystkich okolicznościach. Kompilator nie wbudowanej funkcji, jeśli:  
  
-   Funkcja lub swojego obiektu wywołującego jest skompilowana przy użyciu /Ob0 (domyślną opcją debugowania kompilacji).  
  
-   Funkcja i wywołującego używają różnych typów (C++, obsługa wyjątków w jednej, obsługi w innych wyjątków strukturalnych) obsługi wyjątków.  
  
-   Funkcja ma listy zmiennych argumentów.  
  
-   Funkcja używa zestawu wbudowanego, chyba że kompilowane /Og, OX, / O1 lub/O2.  
  
-   Funkcja jest rekursywny i nie towarzyszy **#pragma inline_recursion(on)**. Z pragma funkcje rekurencyjne są wbudowane do domyślnego głębokości wywołań 16. Aby zmniejszyć ze śródwierszowaniem głębokość, użyj [inline_depth](../preprocessor/inline-depth.md) pragma.  
  
-   Funkcja jest wirtualna i nosi nazwę wirtualną. Bezpośrednie wywołania funkcji wirtualnych mogą być wbudowane.  
  
-   Program pobiera adres funkcji i wywołanie za pomocą wskaźnika do funkcji. Bezpośrednie wywołania funkcji, które miały adresu pobranego mogą być wbudowane.  
  
-   Funkcja jest również oznaczona atrybutem [naked](../cpp/naked-cpp.md) [__declspec](../cpp/declspec.md) modyfikator.  
  
 Jeśli kompilator nie wbudowanego funkcja zadeklarowana ze `__forceinline`, generuje ostrzeżenia poziomu 1, chyba że:
  
-   Funkcja jest skompilowana przy użyciu /Od lub /Ob0. Nie ze śródwierszowaniem jest oczekiwany w tych przypadkach.     
  
-   Funkcja została zdefiniowana w zewnętrznie, biblioteki dołączony lub w innej jednostce tłumaczenia, lub jest docelowy wywołania wirtualnych lub celu pośrednie wywołania. Kompilator nie może zidentyfikować-wbudowanego kodu, który nie może odnaleźć w bieżącej jednostce tłumaczenia.  
  
 Funkcje rekursywne może być wbudowany podstawione o szerokości określonej przez [inline_depth](../preprocessor/inline-depth.md) pragma maksymalnie 16 wywołań. Po tym głębokość wywołania funkcji rekursywnych są traktowane jako połączenia z wystąpieniem funkcji.  Głębokość do cyklicznego, które funkcje są sprawdzane przez Algorytm heurystyczny wbudowanego nie może przekraczać 16. [Inline_recursion](../preprocessor/inline-recursion.md) pragma steruje rozszerzenie funkcji wbudowanej funkcji aktualnie w ramach rozszerzenia. Zobacz [rozszerzenie funkcji wbudowanej](../build/reference/ob-inline-function-expansion.md) (/ Ob) — opcja kompilatora powiązane informacje.  
  
**KOŃCOWY określonych firmy Microsoft**  
 Aby uzyskać więcej informacji na temat używania **wbudowanego** specyfikator, zobacz:  
  
-   [Wbudowane funkcje elementu członkowskiego klasy](../cpp/inline-functions-cpp.md)  
  
-   [Definiowanie funkcji śródwierszowych języka C++ z dllexport i dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)  
  
## <a name="when-to-use-inline-functions"></a>Kiedy należy używać funkcji śródwierszowych  
 Wbudowane funkcje najlepiej są używane dla małych funkcji, takich jak uzyskiwanie dostępu do danych prywatnych elementów członkowskich. Głównym celem tych funkcji "metody dostępu" jednego lub dwóch wiersza jest do zwracania informacji o stanie dotyczących obiektów; krótkich funkcji są wrażliwe na obciążenie związane z wywołania funkcji. Funkcje dłużej poświęcają proporcjonalnie mniej czasu w wywołaniu/zwracanie sekwencji i korzystać od ze śródwierszowaniem.  
  
 A `Point` klasy mogą być zdefiniowane w następujący sposób:  
  
```  
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
  
 Przy założeniu manipulowania współrzędnych jest stosunkowo typowych operacji w kliencie takie klasy, określając dwie funkcje dostępu (`x` i `y` w poprzednim przykładzie) jako **wbudowanego** zwykle zapisuje Obciążenie:  
  
-   Wywołania funkcji (w tym przekazywanie parametru i wprowadzania adresu obiektu na stosie)  
  
-   Zachowanie obiektu wywołującego ramki stosu  
  
-   Nowe ustawienia ramki stosu  
  
-   Wartość zwracaną komunikacji  
  
-   Stary przywracania ramki stosu  
  
-   Zwraca  
  
## <a name="inline-functions-vs-macros"></a>Funkcje śródwierszowe a makra  
 Mimo że wbudowane funkcje są podobne do makra (ponieważ kod funkcji jest rozwinięta w punkcie połączenia w czasie kompilacji), funkcji śródwierszowych są analizowane przez kompilator, makra są rozszerzony przez preprocesora. W związku z tym istnieje kilka istotnych różnic:  
  
-   Wbudowane funkcje wykonaj wszystkie protokoły bezpieczeństwa typu wymuszane na normalnej pracy.  
  
-   Wbudowane funkcje są określane przy użyciu takiej samej składni innych funkcji, z wyjątkiem tego, że zawierają one **wbudowanego** — słowo kluczowe w deklaracji funkcji.  
  
-   Wyrażenia przekazywane jako argumenty do funkcji śródwierszowych są oceniane raz. W niektórych przypadkach wyrażenia przekazywane jako argumenty do makra może przyjąć więcej niż raz.  
  
 W poniższym przykładzie przedstawiono makra, który konwertuje małych liter na wielkie litery:  
  
```  
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
  
 Celem wyrażenie `toupper(getc(stdin))` jest, że znak są odczytywane z urządzenia konsoli (`stdin`) i, jeśli to konieczne, przekonwertowany na wielkie litery.  
  
 Z powodu wykonania makra `getc` raz wykonane, aby określić, czy znak jest większa niż lub równe "a", a po ustalenie, czy jest mniejsza niż lub równa "z". Jeśli w tym zakresie `getc` jest wykonywane ponownie przekonwertować znak na wielkie litery. Oznacza to, że program oczekuje na dwóch lub trzech znaków, gdy najlepszym rozwiązaniem, wymaga tylko jednego.  
  
 Funkcje śródwierszowe rozwiązać problem opisany powyżej:  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [noinline](../cpp/noinline.md)   
 [auto_inline](../preprocessor/auto-inline.md)