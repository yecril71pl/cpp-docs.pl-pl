---
title: Friend (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: friend_cpp
dev_langs: C++
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b30b49825d14e72c06f569c343f96c7cf091a62f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="friend-c"></a>friend (C++)
W niektórych sytuacjach jest wygodniejsze udzielenia dostępu na poziomie elementu członkowskiego do funkcji, które nie należą do klasy, lub do wszystkich elementów członkowskich w osobnej klasy. Tylko implementujący klasy mogą zadeklarować kim są swoich znajomych. Funkcja lub klasy nie można zadeklarować się jako element zaprzyjaźniony dowolnej klasy. W definicji klasy, należy użyć `friend` — słowo kluczowe i nazwę funkcji niebędący elementem członkowskim lub inną klasę, aby przyznać jej dostęp do prywatnych i chronionych elementów członkowskich klasy.         W definicji szablonu parametru typu mogą być deklarowane jako element zaprzyjaźniony.  
  
## <a name="syntax"></a>Składnia  
  
```  
class friend F  
friend F;  
```  
  
## <a name="friend-declarations"></a>Deklaracje funkcji Friend  
 Deklarowanie funkcji zaprzyjaźnionej, który nie został wcześniej zadeklarowany tej funkcji są eksportowane do otaczającego zakresu nonclass.  
  
 Zadeklarowany w deklaracji elementu zaprzyjaźnionego funkcje są traktowane jako ich zadeklarowano przy użyciu `extern` — słowo kluczowe. (Aby uzyskać więcej informacji na temat `extern`, zobacz [specyfikatory statycznych klas magazynu](http://msdn.microsoft.com/en-us/3ba9289a-a412-4a17-b319-ceb2c087df48).)  
  
 Chociaż funkcje z zakresu globalnego mogą być deklarowane jako znajomych przed ich prototypy, funkcje Członkowskie nie można zadeklarować jako znajomych przed pojawieniem się ich deklaracji pełnej klasy. W poniższym kodzie przyczyny niepowodzenia:  
  
```cpp  
class ForwardDeclared;   // Class name is known.  
class HasFriends  
{  
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected  
};  
```  
  
 Powyższy przykład wprowadza nazwę klasy `ForwardDeclared` w zakresie, ale pełną deklarację — w szczególności składnik, który deklaruje funkcję `IsAFriend` — nie jest znany. W związku z tym `friend` deklaracji klasy `HasFriends` generuje błąd.  
  
 Począwszy od języka C ++ 11, istnieją dwie formy deklaracje funkcji friend klasy:  
  
```cpp  
friend class F;  
friend F;  
```  
  
 Pierwszy formularz wprowadza nową klasę F, jeśli żadna z istniejących klas o tej nazwie odnaleziono w najbardziej przestrzeni nazw.  **C ++ 11**: drugi formularz nie wprowadza nową klasę; można używać, gdy klasa została już zadeklarowana i należy go używać przy deklarowaniu parametru typu szablonu lub typedef jako element zaprzyjaźniony.  
  
 Użyj `class friend F` po typu występującego w odwołaniu nie jeszcze została zadeklarowana:  
  
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
  
 Użyj `friend F` Aby zadeklarować parametr szablonu jako element zaprzyjaźniony:  
  
```cpp  
template <typename T>  
class my_class  
{  
    friend T;  
    //...  
};  
```  
  
 Użyj `friend F` Aby zadeklarować typedef jako przyjaciel:  
  
```cpp  
class Foo {};  
typedef Foo F;  
  
class G  
{  
    friend F; // OK  
    friend class F // Error C2371 -- redefinition  
};  
```  
  
 Aby zadeklarować dwóch klas, które są wzajemnie znajomych, należy określić jako element zaprzyjaźniony to pierwsza klasa całej klasy sekundy. Przyczyna to ograniczenie się, że kompilator ma za mało informacji do deklarowania friend poszczególne funkcje tylko w momencie, w którym zadeklarowana jest klasa sekundy.  
  
> [!NOTE]
>  Mimo że całego drugiej klasy musi być przyjazne do pierwszej klasy, możesz wybrać funkcje, które w pierwszej klasie jest znajomych drugiej klasy.  
  
## <a name="friend-functions"></a>friend — funkcje  
 A `friend` funkcja jest funkcją, która nie jest elementem członkowskim klasy, ale ma dostęp do tej klasy prywatnych i chronionych elementów członkowskich. Friend — funkcje nie są traktowane jako elementy członkowskie klasy; są one normalne zewnętrzne funkcje, które są podane uprawnienia dostępu specjalnego. Znajomych nie znajdują się w zakresie tej klasy, a nie są wywoływane przy użyciu operatory wyboru elementu członkowskiego (**.** i -**>**), chyba że są oni członkami innej klasy. A `friend` funkcja zadeklarowana jest klasa, która udziela dostępu. `friend` Deklaracji można umieścić w dowolnym w deklaracji klasy. Nie ma wpływu na słowa kluczowe kontroli dostępu.  
  
 W poniższym przykładzie przedstawiono `Point` klasy i funkcja zaprzyjaźniona `ChangePrivate`. `friend` Funkcji ma dostęp do elementu członkowskiego danych prywatnych `Point` obiekt odbierze jako parametr.  
  
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
  
## <a name="class-members-as-friends"></a>Elementy członkowskie klasy jako znajomych  
 Funkcje elementów członkowskich klasy mogą być deklarowane jako znajomych w innych klasach. Rozważmy następujący przykład:  
  
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
  
 W poprzednim przykładzie, tylko funkcja `A::Func1( B& )` otrzymuje przyjaznego dostępu do klasy `B`. W związku z tym dostęp do prywatnego elementu członkowskiego `_b` jest poprawny w `Func1` klasy `A` , ale nie `Func2`.  
  
 A `friend` klasa jest klasą są wszystkie funkcje elementów członkowskich, których friend — funkcje klasy, oznacza to, którego funkcji Członkowskich mają dostęp do innej klasy prywatnych i chronionych elementów członkowskich. Załóżmy, że `friend` deklaracji klasy `B` był:  
  
```cpp  
friend class A;  
```  
  
 W takim przypadku wszystkie funkcje Członkowskie w klasie `A` czy przyznano przyjaznego dostępu do klasy `B`. Następujący kod jest przykładem klasy przyjazne:  
  
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
  
 Przyjaźni nie jest wzajemne, chyba że jawnie określony sposób. W powyższym przykładzie funkcji Członkowskich `YourClass` nie ma dostępu do członków prywatnych `YourOtherClass`.  
  
 Typ zarządzany nie może mieć żadnych friend — funkcje klasy przyjazne i friend interfejsów.  
  
 Przyjaźni nie jest dziedziczone, co oznacza, że klasy wyprowadzone z `YourOtherClass` nie ma dostępu do `YourClass`przez prywatne elementy członkowskie. Przyjaźni nie jest przechodnie, więc klas, które są znajomych `YourOtherClass` nie ma dostępu do `YourClass`przez prywatne elementy członkowskie.  
  
 Na poniższej ilustracji przedstawiono cztery deklaracje klas: `Base`, `Derived`, `aFriend`, i `anotherFriend`. Tylko klasy `aFriend` ma bezpośredni dostęp do członków prywatnych `Base` (oraz wszystkie elementy członkowskie `Base` mogą być dziedziczone).  
  
 ![Implikacje relacji friend](../cpp/media/vc38v41.gif "vc38V41")  
Efekty friend relacji  
  
## <a name="inline-friend-definitions"></a>Definicje friend wbudowany  
 Friend — funkcje może zostać zdefiniowany w deklaracji klasy. Te funkcje są wbudowane funkcje jak wbudowanego elementu członkowskiego, które funkcje, które zachowują się tak, jakby zostały zdefiniowane natychmiast po wszystkich klas widoczne są elementy członkowskie i przed klasy zakres jest zamknięta (koniec deklaracji klasy).  
  
 Friend — funkcje zdefiniowane wewnątrz deklaracji klasy nie są uważane za w zakresie otaczającą klasę; znajdują się w zakresie pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)