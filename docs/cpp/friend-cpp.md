---
title: Friend (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/02/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- friend_cpp
dev_langs:
- C++
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9938e8bb2128def7d5f507acb111de854dfd4977
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942084"
---
# <a name="friend-c"></a>friend (C++)
W niektórych sytuacjach jest bardziej wygodne do udzielania dostępu poziom elementu członkowskiego do funkcji, które nie są elementami członkowskimi klasę lub do wszystkich elementów członkowskich w osobnej klasy. Można zadeklarować tylko implementujący klasy, którzy swoich znajomych. Funkcji lub klasy nie można zadeklarować sam jako zaprzyjaźniona z dowolnej klasy. W definicji klasy, należy użyć **friend** — słowo kluczowe i nazwy funkcji składowej lub innej klasy, aby przyznać jej dostęp do prywatnych i chronionych składowych klasy. W definicji szablonu parametr typu może być zadeklarowana jako zaprzyjaźniona.  
  
## <a name="syntax"></a>Składnia  
  
```  
class friend F  
friend F;  
```  
  
## <a name="friend-declarations"></a>Deklaracje funkcji Friend  
 Jeśli deklarowana jest funkcja zaprzyjaźniona, który nie został wcześniej zadeklarowany, tej funkcji są eksportowane do zasięgu nonclass.  
  
 Funkcje zadeklarowane w deklaracji elementu zaprzyjaźnionego są traktowane tak, jakby one zostały zgłoszone za pomocą **extern** — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [extern](extern-cpp.md).  
  
 Chociaż funkcje z zakresu globalnego mogą być deklarowane jako znajomych przed ich prototypy, elementów członkowskich nie można zadeklarować jako typu Friend przed pojawieniem się jego deklarację pełnej klasy. W poniższym kodzie Dlaczego to się nie powiedzie:  
  
```cpp  
class ForwardDeclared;   // Class name is known.  
class HasFriends  
{  
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected  
};  
```  
  
 Poprzedni przykład wprowadza imię i nazwisko klasy `ForwardDeclared` do zakresu, ale pełną deklarację — w szczególności fragment, który deklaruje funkcję `IsAFriend` — nie jest znany. W związku z tym **friend** deklaracji w klasie `HasFriends` generuje błąd.  
  
 Począwszy od C ++ 11, istnieją dwa rodzaje deklaracje funkcji friend dla klasy:  
  
```cpp  
friend class F;  
friend F;  
```  
  
 Pierwszy formularz wprowadza nową klasę F, jeśli żadna z istniejących klas o tej nazwie został znaleziony w najbardziej przestrzeni nazw.  **C ++ 11**: drugi formularz nie wprowadza nową klasę; można używać, gdy klasa została już zadeklarowana. Ponadto należy użyć podczas deklarowania parametrowi typu szablonu lub typedef jako zaprzyjaźniona.  
  
 Użyj `class friend F` kiedy przywoływany typ nie ma jeszcze zadeklarowana:  
  
```cpp  
namespace NS  
{  
    class M  
    {  
        class friend F;  // Introduces F but doesn't define it  
    };  
}  
```  
  
```cpp  
namespace NS  
{  
    class M  
    {  
        friend F; // error C2433: 'NS::F': 'friend' not permitted on data declarations  
    };  
}  
```  
  
 W poniższym przykładzie `friend F` odwołuje się do `F` klasy, która jest zadeklarowana poza zakresem NS.  
  
```cpp  
class F {};  
namespace NS  
{  
    class M  
    {  
        friend F;  // OK   
    };  
}  
```  
  
 Użyj `friend F` Aby zadeklarować parametr szablonu jako zaprzyjaźniona:  
  
```cpp  
template <typename T>  
class my_class  
{  
    friend T;  
    //...  
};  
```  
  
 Użyj `friend F` do deklarowania typedef jako friend:  
  
```cpp  
class Foo {};  
typedef Foo F;  
  
class G  
{  
    friend F; // OK  
    friend class F // Error C2371 -- redefinition  
};  
```  
  
 Aby zadeklarować dwóch klas, które są wzajemnie znajomych, cała klasa sekundę muszą być określone jako zaprzyjaźniona z pierwszej klasy. Przyczyną tego ograniczenia jest, że kompilator ma za mało informacji do deklarowania friend poszczególnych funkcji tylko w punkcie, w którym zadeklarowana jest klasa sekundę.  
  
> [!NOTE]
>  Mimo że cała klasa sekundę musi być elementem zaprzyjaźnionym pierwszej klasy, możesz wybrać funkcje, które w pierwszej klasie będzie przyjaciół klasy sekundy.  
  
## <a name="friend-functions"></a>friend — funkcje  
 A **friend** funkcja jest funkcją, która nie jest składową klasy, ale ma dostęp do prywatnych i chronionych składowych klasy. Friend — funkcje nie są traktowane jako elementy członkowskie klasy; są one normalnej funkcji zewnętrznych, które są określone uprawnienia dostępu specjalnego. Znajomych nie znajdują się w zakresie klasy i ich nie są wywoływane przy użyciu operatorów wyboru elementów członkowskich (**.** i -**>**), chyba że są oni członkami innej klasy. A **friend** funkcja jest zadeklarowana przez klasę, która udziela praw dostępu. **Friend** deklaracji można umieścić w dowolnym miejscu w deklaracji klasy. Nie występuje według słów kluczowych kontroli dostępu.  
  
 W poniższym przykładzie przedstawiono `Point` klasa i funkcja zaprzyjaźniona `ChangePrivate`. **Friend** funkcji ma dostęp do prywatnych danych elementu członkowskiego `Point` obiekt otrzymuje jako parametr.  
  
```cpp  
// friend_functions.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Point  
{  
    friend void ChangePrivate( Point & );  
public:  
    Point( void ) : m_i(0) {}  
    void PrintPrivate( void ){cout << m_i << endl; }  
  
private:  
    int m_i;  
};  
  
void ChangePrivate ( Point &i ) { i.m_i++; }  
  
int main()  
{  
   Point sPoint;  
   sPoint.PrintPrivate();  
   ChangePrivate(sPoint);  
   sPoint.PrintPrivate();  
// Output: 0  
           1  
}  
```  
  
## <a name="class-members-as-friends"></a>Składowe klasy jako typu Friend  
 Funkcje składowych klasy mogą być deklarowane jako znajomych w innych klas. Rozważmy następujący przykład:  
  
```cpp  
// classes_as_friends1.cpp  
// compile with: /c  
class B;  
  
class A {  
public:  
   int Func1( B& b );  
  
private:  
   int Func2( B& b );  
};  
  
class B {  
private:  
   int _b;  
  
   // A::Func1 is a friend function to class B  
   // so A::Func1 has access to all members of B  
   friend int A::Func1( B& );  
};  
  
int A::Func1( B& b ) { return b._b; }   // OK  
int A::Func2( B& b ) { return b._b; }   // C2248  
```  
  
 W poprzednim przykładzie, tylko funkcja `A::Func1( B& )` otrzymuje przyjazny dostęp do klasy `B`. W związku z tym, dostęp do prywatnego członka `_b` jest poprawny w `Func1` klasy `A` , ale nie `Func2`.  
  
 A `friend` klasa jest klasą są wszystkie funkcje Członkowskie, których zaprzyjaźnionych funkcji w klasie, oznacza to, którego funkcje Członkowskie mają dostęp do prywatnych i chronionych członków innych klas. Załóżmy, że `friend` deklaracji w klasie `B` była:  
  
```cpp  
friend class A;  
```  
  
 W takim przypadku wszystkie funkcje składowych klasy `A` czy przyznano dostęp zaprzyjaźniony do klasy `B`. Poniższy kod jest przykładem klasy zaprzyjaźnionej:  
  
```cpp  
// classes_as_friends2.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class YourClass {  
friend class YourOtherClass;  // Declare a friend class  
public:  
   YourClass() : topSecret(0){}  
   void printMember() { cout << topSecret << endl; }  
private:  
   int topSecret;  
};  
  
class YourOtherClass {  
public:  
   void change( YourClass& yc, int x ){yc.topSecret = x;}  
};  
  
int main() {  
   YourClass yc1;  
   YourOtherClass yoc1;  
   yc1.printMember();  
   yoc1.change( yc1, 5 );  
   yc1.printMember();  
}  
```  
  
 Przyjaźni nie jest wzajemne, chyba że jawnie określone jako takie. W powyższym przykładzie, funkcje składowe `YourClass` nie może uzyskać dostępu do prywatnych składowych z `YourOtherClass`.  
  
 Typ zarządzany nie może mieć żadnych zaprzyjaźnionych funkcji, klasy przyjazne lub friend interfejsów.  
  
 Przyjaźni nie jest dziedziczone, co oznacza, że klasy pochodne klasy `YourOtherClass` nie ma dostępu do `YourClass`firmy prywatnych elementów członkowskich. Przyjaźni nie jest przechodnia, więc klasy, które są znajomych `YourOtherClass` nie ma dostępu do `YourClass`firmy prywatnych elementów członkowskich.  
  
 Na poniższej ilustracji przedstawiono cztery deklaracje klas: `Base`, `Derived`, `aFriend`, i `anotherFriend`. Tylko klasy `aFriend` ma bezpośredni dostęp do prywatnych składowych `Base` (oraz wszystkie elementy członkowskie `Base` może być dziedziczona).  
  
 ![Implikacje relacji friend](../cpp/media/vc38v41.gif "vc38V41")  
Implikacje friend relacji  
  
## <a name="inline-friend-definitions"></a>Definicje friend wbudowane  
 Friend — funkcje mogą być definiowane w obrębie deklaracji klasy. Te funkcje są wbudowane funkcje i podobnie jak wbudowanego elementu członkowskiego, które funkcje, które zachowują się tak, jakby zostały zdefiniowane natychmiast po wszystkich klasy widoczne są członkami ale przed klasy zakres jest zamknięty (koniec deklaracji klasy).  
  
 Friend — funkcje zdefiniowane w obrębie deklaracji klasy nie są uwzględniane w zakresie otaczającej klasy; są one w zakresie pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)
