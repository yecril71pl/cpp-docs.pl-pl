---
title: Wyliczenia (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/01/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- enum_cpp
dev_langs:
- C++
helpviewer_keywords:
- declarations, enumerations
- enumerators, declaring
- enum keyword [C++]
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: 081829db-5dca-411e-a53c-bffef315bcb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00a1b940ad6c792abbb13ec91b7376b73b2be16b
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43130953"
---
# <a name="enumerations-c"></a>Wyliczenia (C++)
Wyliczenie to typ zdefiniowany przez użytkownika, który składa się z szeregu nazwanych stałych liczbach całkowitych, które są znane jako moduły wyliczające.  
  
> [!NOTE]
>  Ten artykuł omawia język ISO Standard C++ **wyliczenia** typu i o określonym zakresie (lub silnie typizowane) **klasa wyliczeniowa** typu, który został wprowadzony w C ++ 11. Uzyskać informacji na temat **klasy publicznym typie wyliczeniowym** lub **klasa wyliczeniowa prywatnej** typów w języku C + +/ CLI i C + +/ CX, zobacz [klasa wyliczeniowa](../windows/enum-class-cpp-component-extensions.md).  
  
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
  
```cpp 
// Forward declaration of enumerations  (C++11):  
enum A : int; // non-scoped enum must have type specified
enum class B; // scoped enum defaults to int but ...
enum class C : short;  // ... may have any integral underlying type
```  
  
## <a name="parameters"></a>Parametry  
 *Identyfikator*  
 Nazwa typu nadana enumeracji.  
  
 *Typ*  
 Podstawowy typ enumeratorów; wszystkie moduły wyliczające mają ten sam typ podstawowy. Może być dowolnego typu całkowitoliczbowego.  
  
 *Lista wyliczenia*  
 Rozdzielana przecinkami lista modułów wyliczających w wyliczeniu. Każdy moduł wyliczający lub nazwa zmiennej w zakresie musi być unikatowa. Jednakże wartości mogą być zduplikowane. W przypadku wyliczenia niewystępującego w zakresie zakresem jest otaczający zakres; w wyliczeniowym w zakresie zakresem jest *listy wyliczenia* sam.  W wyliczeniowym w zakresie listy może być puste w praktyce definiujący nowy typ całkowity.
  
 *class*  
 Za pomocą słowa kluczowego w zgłoszeniu, należy określić, ma zakres wyliczenia, a *identyfikator* musi zostać podana. Można również użyć **struktury** słowa kluczowego zamiast **klasy**, jak są semantycznie równoważne w tym kontekście.  
  
## <a name="enumerator-scope"></a>Zakres modułu wyliczającego  
 Wyliczenie tworzy kontekst do opisania zakresu wartości, które są reprezentowane jako nazwane stałe i są również nazywane modułami wyliczającymi. W oryginalnym C i C++ typów wyliczenia niekwalifikowane moduły wyliczające są widoczne w całym zakresie, w którym deklarowane jest wyliczenie. W typach wyliczeniowych Nazwa modułu wyliczającego musi być kwalifikowana przez nazwę typu wyliczenia. Poniższy przykład pokazuje tę podstawową różnicę między dwoma rodzajami wyliczeń:  
  
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
  
 Każda nazwa wyliczenia przydzielono wartość całkowita, która odpowiada jej miejscu w kolejności wartości w wyliczeniu. Domyślnie pierwszej wartości jest przypisane 0, następnej jest przypisany 1 i tak dalej, ale można jawnie ustawić wartość modułu wyliczającego, jak pokazano poniżej:  
  
```cpp  
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };  
```  
  
 Moduł wyliczający `Diamonds` jest przypisywana wartość `1`. Kolejne enumeratory, jeśli nie posiadają wartości jawnej, otrzymują wartość poprzedniego enumeratora plus jeden. W poprzednim przykładzie `Hearts` miałby wartość 2, `Clubs` mogłoby być 3 i tak dalej.  
  
 Każdy moduł wyliczający jest traktowany jako stała i musi mieć unikatową nazwę w zakresie gdzie **wyliczenia** zdefiniowano (dla wyliczeń poza zakresem) lub w ramach **wyliczenia** sam (dla wyliczeń objętych zakresem). Wartości nadane nazwom nie muszą być unikatowe. Na przykład jeśli deklaracja wyliczenia niewystępującego w zakresie `Suit` to:  
  
```cpp  
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };  
```  
  
 Następnie wartości `Diamonds`, `Hearts`, `Clubs`, i `Spades` to 5, 6, 4 i 5, odpowiednio. Należy zauważyć, że 5 zastosowano więcej niż raz; jest to dozwolone, mimo że nie może być korzystne. Te zasady są takie same dla wyliczeń objętych zakresem.  
  
 ## <a name="casting-rules"></a>Reguły rzutowania  
  
 Stałe wyliczeń nieobjętych zakresem można niejawnie przekonwertować **int**, ale **int** nigdy nie jest niejawnie konwertowany na wartość wyliczenia. W poniższym przykładzie pokazano, co się stanie, jeśli użytkownik próbuje przypisać `hand` wartość, która nie jest `Suit`:  
  
```cpp  
int account_num = 135692;  
Suit hand;  
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'  
```  
  
 Obsada jest wymagana do konwertowania **int** do zakresem lub bez zakresu modułu wyliczającego. Możesz jednak podwyższyć poziom modułu wyliczającego nieobjętego zakresem do wartości będącej liczbą całkowitą bez rzutowania.  
  
```cpp  
int account_num = Hearts; //OK if Hearts is in a unscoped enum  
```  
  
 Korzystanie z niejawnych konwersji w ten sposób może prowadzić do niezamierzonych skutków ubocznych. Aby wyeliminować błędy programowania związane z wyliczeniami nieobjętymi zakresem, wartości wyliczeń w zakresie są silnie typizowane. Moduły wyliczające w zakresie musi być kwalifikowana przez nazwę typu wyliczenia (identyfikator) i nie można niejawnie przekonwertować, jak pokazano w poniższym przykładzie:  
  
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
  
 Należy zauważyć, że wiersz `hand = account_num;` nadal powoduje błąd występujący z wyliczeniami nieobjętymi zakresem, jak pokazano wcześniej. Jest ona dozwolona z jawnym rzutowaniem. Jednakże przy typach wyliczeniowych w zakresie próba konwersji w następnej instrukcji `account_num = Suit::Hearts;`, nie jest już dozwolona bez jawnego rzutowania. 

## <a name="no_enumerators"></a> Typy wyliczeniowe atrybutem nie modułów wyliczających

**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): definiując wyliczenia (regularnych lub zakresie) za pomocą jawnego typu podstawowego i nie wyliczenia, możesz obowiązuje wprowadzić nową typu całkowitego nie ma niejawnej konwersji do żadnego innego typu. Przy użyciu tego typu, a nie jej wbudowany typ podstawowy, można wyeliminować ryzyko drobne błędy spowodowane przypadkowego niejawne konwersje.  


```cpp
enum class byte : unsigned char { };
```

Nowy typ jest dokładna kopia typu podstawowego i dlatego ma tą samą konwencję wywołania, co oznacza, że może służyć przez interfejsy ABI bez żadnych spadek wydajności. Brak rzutowania jest wymagany, gdy zmienne typu są inicjowane za pomocą bezpośrednich listy inicjowania. Poniższy przykład pokazuje, jak zainicjować Typy wyliczeniowe atrybutem nie modułów wyliczających w różnych kontekstach:

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
  
## <a name="see-also"></a>Zobacz także  
 [Deklaracje modułów Wyliczających języka C](../c-language/c-enumeration-declarations.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)