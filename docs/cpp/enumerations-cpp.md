---
title: Wyliczenia (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: enum_cpp
dev_langs: C++
helpviewer_keywords:
- declarations, enumerations
- enumerators, declaring
- enum keyword [C++]
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: 081829db-5dca-411e-a53c-bffef315bcb3
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 96b1b29baaa779fda1e1f076daf3d8bd9335403b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="enumerations-c"></a>Wyliczenia (C++)
Wyliczenie jest zdefiniowane przez użytkownika typu, który zawiera zestaw o nazwie stałe całkowite, które są określane jako wyliczenia.  
  
> [!NOTE]
>  W tym artykule omówiono Standard języka C++ ISO `enum` typu i zakresami (lub jednoznacznie) `enum class` typu, który wprowadzono w języku C ++ 11. Aby uzyskać informacje o `public enum class` lub `private enum class` typów w języku C + +/ CLI i C + +/ CX, zobacz [Wylicz klasy](../windows/enum-class-cpp-component-extensions.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
// unscoped enum:  
enum [identifier] [: type]  
{enum-list};   
  
// scoped enum:  
enum [class|struct]   
[identifier] [: type]   
{enum-list};  
```  
  
```  
// Forward declaration of enumerations  (C++11):  
enum A : int; // non-scoped enum must have type specified
enum class B; // scoped enum defaults to int but ...
enum class C : short;  // ... may have any integral underlying type
```  
  
## <a name="parameters"></a>Parametry  
 `identifier`  
 Nazwa typu wyliczenia.  
  
 `type`  
 Podstawowy typ wyliczenia; wszystkie moduły wyliczające mają ten sam typ podstawowy. Mogą być dowolnego typu całkowitego.  
  
 `enum-list`  
 Rozdzielana przecinkami lista wyliczenia w wyliczeniu. Każdy moduł wyliczający lub nazwę zmiennej w zakresie musi być unikatowa. Jednak być zduplikowane wartości. Wyliczenia niewystępującego w zakresie zakres jest otaczającym zasięgu; w zakresie wyliczenia, zakres jest `enum-list` samej siebie.  W zakresie wyliczenia listy może być pusta skutkuje definiujący nowy typ całkowity.
  
 `class`  
 Za pomocą słowa kluczowego w deklaracji, należy określić, ma zakres wyliczenia i `identifier` należy podać. Można również użyć `struct` słowa kluczowego zamiast `class`, ponieważ są one semantycznie równoważne w tym kontekście.  
  
## <a name="enumerator-scope"></a>Zakres modułu wyliczającego  
 Wyliczenie zawiera kontekstu do opisywania zakres wartości, które są reprezentowane jako stałe nazwane i są również nazywane wyliczenia. W oryginalnym C i C++ typów wyliczenia niekwalifikowane moduły wyliczające są widoczne w zakresie, w którym zadeklarowane jest wyliczenie. W zakresie wyliczenia Nazwa modułu wyliczającego musi być kwalifikowana przez nazwę typu wyliczenia. W poniższym przykładzie pokazano to podstawowa różnica między dwa rodzaje wyliczenia:  
  
```cpp  
namespace CardGame_Scoped  
{  
    enum class Suit { Diamonds, Hearts, Clubs, Spades };  
  
    void PlayCard(Suit suit)  
    {  
        if (suit == Suit::Clubs) // Enumerator must be qualified by enum type  
        { /*...*/}  
    }  
}  
  
namespace CardGame_NonScoped  
{  
    enum Suit { Diamonds, Hearts, Clubs, Spades };  
  
    void PlayCard(Suit suit)  
    {  
        if (suit == Clubs) // Enumerator is visible without qualification  
        { /*...*/  
        }  
    }  
}  
```  
  
 Każda nazwa w wyliczeniu przydzielono wartością całkowitą, która odpowiada jego miejsce według wartości w wyliczeniu. Domyślnie pierwszą wartość przypisano 0, kolejny przypisano 1 i tak dalej, ale wartość modułu wyliczającego, można ustawić jawnie, jak pokazano poniżej:  
  
```cpp  
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };  
  
```  
  
 Moduł wyliczający `Diamonds` jest przypisywana wartość `1`. Kolejne wyliczenia, jeśli nie podano wartości jawnej przyjmuje wartość poprzedniej modułu wyliczającego plus jeden. W poprzednim przykładzie `Hearts` będzie mieć wartość 2, `Clubs` będzie mieć 3 i tak dalej.  
  
 Każdy moduł wyliczający jest traktowany jako stała i musi mieć unikatową nazwę w zakresie gdzie `enum` zdefiniowano (dla wyliczenia niewystępującego w zakresie) lub w ramach wyliczenia (dla wyliczeń w zakresie). Podane wartości nazwy nie muszą być unikatowe. Na przykład jeśli w deklaracji wyliczenia niewystępującego w zakresie `Suit` to:  
  
```cpp  
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };  
```  
  
 Następnie wartości `Diamonds`, `Hearts`, `Clubs`, i `Spades` to odpowiednio 5, 6, 4 i 5. Zwróć uwagę, że 5 jest używana więcej niż raz; jest to dozwolone, mimo że nie może być korzystne. Te reguły są takie same dla wyliczenia w zakresie.  
  
 ## <a name="casting-rules"></a>Reguły rzutowania  
  
 Stałe wyliczenia niewystępującego w zakresie można niejawnie przekonwertować `int`, ale `int` nie jest nigdy niejawnie przekonwertować wartości wyliczenia. W poniższym przykładzie pokazano, co się stanie, Jeśli spróbujesz przypisać `hand` wartość, która nie jest `Suit`:  
  
```cpp  
int account_num = 135692;  
Suit hand;  
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'  
  
```  
  
 Rzutowanie jest wymagany do przekonwertowania `int` na zakresie lub niewystępującego w zakresie modułu wyliczającego. Jednak możesz podwyższyć poziom niewystępującego w zakresie modułu wyliczającego na wartość całkowitą bez rzutowanie.  
  
```cpp  
int account_num = Hearts; //OK if Hearts is in a unscoped enum  
```  
  
 Używanie niejawne konwersje w ten sposób może spowodować niezamierzone skutki uboczne. Aby wyeliminować błędy programowania skojarzony z wyliczenia niewystępującego w zakresie wartości wyliczeniowych zakresami są silnie typizowane. Moduły wyliczające w zakresie musi być kwalifikowana przez nazwę typu wyliczenia (identifier) i nie można niejawnie przekonwertować, jak pokazano w poniższym przykładzie:  
  
```cpp  
namespace ScopedEnumConversions  
{  
    enum class Suit { Diamonds, Hearts, Clubs, Spades };  
  
    void AttemptConversions()  
    {  
        Suit hand;   
        hand = Clubs; // error C2065: 'Clubs' : undeclared identifier  
        hand = Suit::Clubs; //Correct.  
        int account_num = 135692;  
        hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'  
        hand = static_cast<Suit>(account_num); // OK, but probably a bug!!!  
  
        account_num = Suit::Hearts; // error C2440: '=' : cannot convert from 'Suit' to 'int'  
        account_num = static_cast<int>(Suit::Hearts); // OK  
}  
  
```  
  
 Zwróć uwagę, że wiersz `hand = account_num;` nadal powoduje błąd występujący z wyliczenia niewystępującego w zakresie, jak pokazano wcześniej. Może on z jawnego rzutowania. Jednak w przypadku wyliczenia w zakresie, próba konwersji w następnej instrukcji `account_num = Suit::Hearts;`, nie jest dozwolony bez jawnego rzutowania. 

## <a name="enums-with-no-enumerators"></a>Typy wyliczeniowe atrybutem nie moduły wyliczające
**Visual Studio 2017 wersji 15.3 i nowszych** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): przez zdefiniowanie wyliczenia (zwykłe i zakresami) z jawnego typu podstawowego i nie wyliczenia, możesz skutkuje wprowadzić nowy typie całkowitym ma niejawna konwersja do żadnego innego typu. Przy użyciu tego typu zamiast jego typem podstawowym wbudowanych, można wyeliminować potencjalnych subtelnych błędów spowodowanych przez przypadkowej niejawną konwersję.  


```cpp
enum class byte : unsigned char { };
```

Nowy typ jest dokładną kopię typem podstawowym i w związku z tym ma tą samą konwencję wywołania, co oznacza, że może służyć między ABIs bez żadnych spadek wydajności. Rzutowanie nie jest wymagany w przypadku zmiennych typu są inicjowane przy użyciu Inicjalizacja listy bezpośrednio. Poniższy przykład pokazuje, jak zainicjować wyliczenia za pomocą nie moduły wyliczające w różnych kontekstach:

```cpp
enum class byte : unsigned char { };

enum class E : int { };
E e1{ 0 };
E e2 = E{ 0 };

struct X 
{
    E e{ 0 };
    X() : e{ 0 } { }
};

E* p = new E{ 0 }; 

void f(E e) {};

int main()
{
    f(E{ 0 });
    byte i{ 42 };
    byte j = byte{ 42 };

    // unsigned char c = j; // C2440: 'initializing': cannot convert from 'byte' to 'unsigned char'
    return 0;
}
``` 
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje modułów Wyliczających C](../c-language/c-enumeration-declarations.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)