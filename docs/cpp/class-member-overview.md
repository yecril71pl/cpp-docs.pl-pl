---
title: "Omówienie elementu członkowskiego klasy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- members [C++], types of class members
- members [C++]
- class members [C++], types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2d9a8d274f162e64dc20c5f257d09c84e9871d0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="class-member-overview"></a>Omówienie elementu członkowskiego klasy
Klasy lub struktury składa się z jego elementów członkowskich. Pracy, który wykonuje klasy jest wykonywane przez funkcje elementu członkowskiego. Stan, który przechowuje jest przechowywany w jego elementów członkowskich danych. Inicjowania elementów członkowskich odbywa się przez konstruktory i oczyszczania pracy, takich jak zwalnianie pamięci i zwolnienie zasobów jest realizowane przez destruktorów. W języku C ++ 11 i nowszych, elementy członkowskie danych można i zazwyczaj powinien być inicjowane w punkcie deklaracji.  
  
## <a name="kinds-of-class-members"></a>Typy elementów członkowskich klasy  
 Pełna lista kategorii elementu członkowskiego jest następujący:  
  
-   [Specjalne funkcje Członkowskie](special-member-functions.md).  
  
-   [Przegląd funkcji Członkowskich](overview-of-member-functions.md).  
  
-   [Elementy członkowskie danych](static-members-cpp.md) tym wbudowane typy i innych użytkowników zdefiniowanych typów.  
  
-   Operatory  
  
-   [Zagnieżdżone deklaracje klas](nested-class-declarations.md) i.)  
  
-   [Unie](unions.md)  
  
-   [Wyliczenia](../cpp/enumerations-cpp.md).  
  
-   [Pola bitowe](../cpp/cpp-bit-fields.md).  
  
-   [Znajomych](../cpp/friend-cpp.md).  
  
-   [Aliasy i definicje typów](../cpp/aliases-and-typedefs-cpp.md).  
  
    > [!NOTE]
    >  Elementy zaprzyjaźnione są ujęte w powyższej liście, ponieważ są zawarte w deklaracji klasy. Jednak nie są one prawdziwymi składowymi klasy, ponieważ nie są one w zakresie tej klasy.  
  
## <a name="example-class-declaration"></a>Przykład deklaracji klasy  
 W poniższym przykładzie przedstawiono deklaracji klasy prosty:  
  
```  
// TestRun.h  
  
class TestRun  
{  
    // Start member list.  
  
    //The class interface accessible to all callers.  
public:  
    // Use compiler-generated default constructor:  
    TestRun() = default;   
    // Don't generate a copy constructor:  
    TestRun(const TestRun&) = delete;    
    TestRun(std::string name);  
    void DoSomething();  
    int Calculate(int a, double d);  
    virtual ~TestRun();  
    enum class State { Active, Suspended };  
  
    // Accessible to this class and derived classes only.  
protected:  
    virtual void Initialize();  
    virtual void Suspend();  
    State GetState();  
  
    // Accessible to this class only.  
private:  
    // Default brace-initialization of instance members:  
    State _state{ State::Suspended };   
    std::string _testName{ "" };   
    int _index{ 0 };  
  
    // Non-const static member:  
    static int _instances;  
    // End member list.  
};  
  
// Define and initialize static member.  
int TestRun::_instances{ 0 };  
```  
  
## <a name="member-accessibility"></a>Dostępność elementu członkowskiego  
 Elementy członkowskie klasy są zadeklarowane na liście elementów członkowskich. Listy elementów członkowskich klasy mogą być podzielone dowolną liczbę `private`, `protected` i **publicznego** sekcje słów kluczowych, znany jako specyfikatory dostępu.  Dwukropek **:** musi występować po specyfikatorze dostępu.  Sekcje nie muszą być ciągłe, to znaczy dowolne z tych słów kluczowych mogą wystąpić kilka razy na liście elementów członkowskich.  Słowo kluczowe wyznacza dostęp do wszystkich elementów członkowskich aż do następnego specyfikatora dostępu lub nawiasu zamykającego. Aby uzyskać więcej informacji, zobacz [kontroli dostępu do elementu członkowskiego (C++)](../cpp/member-access-control-cpp.md).  
  
## <a name="static-members"></a>Statyczne elementy członkowskie  
 Element członkowski danych mogą być deklarowane jako jako statyczne, co oznacza, że wszystkie obiekty klasy mają dostęp do tej samej kopii. Funkcji członkowskiej mogą być zadeklarowane jako statyczne, w takim przypadku go mają dostęp tylko statyczne elementy członkowskie danych klasy (i nie ma *to* wskaźnika). Aby uzyskać więcej informacji, zobacz [statyczne elementy członkowskie danych](../cpp/static-members-cpp.md).  
  
## <a name="special-member-functions"></a>Specjalne funkcje Członkowskie  
 Specjalne funkcje Członkowskie są funkcje, które są automatycznie udostępniane przez kompilator, jeśli nie określisz je w kodzie źródłowym.  
  
1.  Konstruktor domyślny  
  
2.  Konstruktor kopiujący  
  
3.  **(C ++ 11)**  Konstruktor przenoszenia  
  
4.  Operator przypisania kopiowania  
  
5.  **(C ++ 11)**  Operator przypisania przenoszenia  
  
6.  Destruktor  
  
Aby uzyskać więcej informacji, zobacz [specjalne funkcje Członkowskie](../cpp/special-member-functions.md).
  
## <a name="memberwise-initialization"></a>Inicjowanie memberwise  
 W języku C ++ 11 i nowszych deklaratorów niestatycznego elementu członkowskiego może zawierać inicjatory.  
  
```  
  
class CanInit  
{  
public:  
    long num {7};       // OK in C++11  
    int k = 9;          // OK in C++11  
    static int i = 9; // Error: must be defined and initialized  
                      // outside of class declaration.  
  
    // initializes num to 7 and k to 9  
    CanInit(){}  
  
    // overwrites original initialized value of num:  
    CanInit(int val) : num(val) {}  
};  
int main()  
{  
}  
```  
  
 Jeśli element członkowski jest przypisywana wartość w konstruktorze, ta wartość zastępuje wartość, której element członkowski został zainicjowany w punkcie deklaracji.  
  
 Istnieje tylko jedna kopia udostępnionych danych statycznych składowych dla wszystkich obiektów typu danej klasy. Dane statyczne członków muszą być zdefiniowane i mogą być zainicjowane w zakresie pliku. (Aby uzyskać więcej informacji na temat statyczne elementy członkowskie danych, zobacz [statyczne elementy członkowskie danych](../cpp/static-members-cpp.md).) Poniższy przykład pokazuje sposób wykonywania takiego inicjowania:  
  
```  
// class_members2.cpp  
class CanInit2  
{  
public:  
    CanInit2() {} // Initializes num to 7 when new objects of type   
                 //  CanInit are created.  
    long     num {7};  
    static int i;  
    static int j;  
};  
  
// At file scope:  
  
// i is defined at file scope and initialized to 15.  
// The initializer is evaluated in the scope of CanInit.  
int CanInit2::i = 15;  
  
// The right side of the initializer is in the scope   
// of the object being initialized  
int CanInit2::j = i;  
```  
  
> [!NOTE]
>  Nazwa klasy `CanInit2` musi znajdować się przed `i`, aby określić, że definiowany `i` jest składową klasy `CanInit2`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy i struktury](../cpp/classes-and-structs-cpp.md)
