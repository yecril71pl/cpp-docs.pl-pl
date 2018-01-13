---
title: Zakres (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- classes [C++], scope
- scope [C++]
- function prototypes [C++], scope
- class scope
- prototype scope
- functions [C++], scope
- scope, C++ names
ms.assetid: 81fecbb0-338b-4325-8332-49f33e716352
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 55baa4496522336a5a64ee81daa7a8ce484534c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="scope-visual-c"></a>Zakres (Visual C++)
Nazwy C++ mogą być użyte tylko w określonych regionach programu. Ten obszar jest nazywany 'scope' Nazwa. Zakres określa "ważności" nazwę, która nie określa obiektu statycznego obszaru. Zakres określa również widoczność nazwy, wywołanego klasy konstruktory i destruktory i są inicjowane zmiennych lokalnych do zakresu. (Aby uzyskać więcej informacji, zobacz [konstruktorów](../cpp/constructors-cpp.md) i [destruktory](../cpp/destructors-cpp.md).) Istnieje pięć rodzajów zakresu:  
  
-   **Zakres lokalny** nazwę zadeklarowana wewnątrz bloku jest dostępny tylko w obrębie tego bloku i ujęte przez nią i tylko po punkcie deklaracji bloków. Nazwy Argumenty formalne funkcji w zakresie bloku peryferyjnych funkcji ma zakres lokalny tak, jakby ich zadeklarowano wewnątrz bloku treści funkcji otaczającej. Rozważmy następujący fragment kodu:  
  
    ```  
    {  
        int i;  
    }  
    ```  
  
     Ponieważ deklaracja `i` znajduje się w bloku ujęta w nawiasy klamrowe, `i` ma zakres lokalny i nigdy nie jest dostępny, ponieważ żaden kod uzyskuje dostęp do jego przed zamykający nawias klamrowy.  
  
-   **Funkcja zakresu** etykiety są tylko nazwy, które mają zakresem funkcji. Ich można używać w dowolnym miejscu w funkcji, ale nie są dostępne spoza tej funkcji. Argumenty formalne (argumentów określona w definicji funkcji) do funkcji są uważane za w zakresie bloku peryferyjnych treści funkcji.  
  
-   **Zakres pliku** dowolną nazwę zadeklarowana poza wszystkie bloki lub klas, ma zakres pliku. Jest dostępna w dowolnym miejscu w jednostce tłumaczenia po jego deklaracji. Nazw z zakresem pliku, które nie deklaruj statycznych obiektów są często nazywane nazwy globalne.  
  
     W języku C++ pliku zakresu jest nazywana zakresie przestrzeni nazw.  
  
-   **Klasa zakresu** nazwy elementów członkowskich klasy mają zakres klasy. Funkcje elementów członkowskich klasy jest możliwy tylko za pomocą operatory wyboru elementu członkowskiego (**.** lub  **->** ) lub operatory wskaźników do elementów członkowskich (**.\***  lub  **-> \*** ) na obiekt lub wskaźnik do obiektu dla tej klasy; klasa niestatycznego elementu członkowskiego danych jest uznawany za lokalne dla obiekt tej klasy. Należy wziąć pod uwagę następujące deklaracji klasy:  
  
    ```  
    class Point  
    {  
        int x;  
        int y;  
    };  
    ```  
  
     Elementy członkowskie klasy `x` i `y` są uważane za w zakresie klasy `Point`.  
  
-   **Zakres prototypu** nazwy zadeklarowany w prototypu funkcji są widoczne tylko aż do zakończenia prototypu. Następujące prototypu deklaruje trzy nazwy (`strDestination`, `numberOfElements`, i `strSource`); te nazwy się znaleźć poza zakresem na końcu prototypu:  
  
    ```  
    errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );  
    ```  
  
## <a name="hiding-names"></a>Ukrywanie nazw  
 Aby ukryć nazwę, deklarowanie go w zamkniętym bloku. Na poniższej ilustracji `i` jest ponownie zadeklarować w bloku wewnętrznym, a tym samym ukrywanie zmiennej skojarzone z `i` w zakresie bloku zewnętrzne.  
  
 ![Blok &#45; ukrywania nazwa zakresu](../cpp/media/vc38sf1.png "vc38SF1")  
Zakresu bloku i ukrywanie nazwy  
  
 Dane wyjściowe z programu na ilustracji to:  
  
```  
i = 0  
i = 7  
j = 9  
i = 0  
```  
  
> [!NOTE]
>  Argument `szWhat` uważa się w zakresie funkcji. W związku z tym jest traktowana tak, jakby zadeklarowano w najbardziej zewnętrznej bloku funkcji.  
  
## <a name="hiding-class-names"></a>Ukrywanie nazwy klas  
 Deklarowanie funkcji, obiektu lub zmienna lub modułu wyliczającego, w tym samym zakresie można ukryć nazwy klasy. Jednak nazwa klasy nadal będą dostępne, gdy poprzedzona słowem kluczowym **klasy**.  
  
```  
// hiding_class_names.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
// Declare class Account at file scope.  
class Account  
{  
public:  
    Account( double InitialBalance )  
        { balance = InitialBalance; }  
    double GetBalance()  
        { return balance; }  
private:  
    double balance;  
};  
  
double Account = 15.37;            // Hides class name Account  
  
int main()  
{  
    class Account Checking( Account ); // Qualifies Account as   
                                       //  class name  
  
    cout << "Opening account with balance of: "  
         << Checking.GetBalance() << "\n";  
}  
//Output: Opening account with balance of: 15.37  
```  
  
> [!NOTE]
>  Miejsce nazwy klasy (`Account`) jest wywoływana dla klasa — słowo kluczowe musi być używana w odróżnieniu od konta zmiennej o zakresie pliku. Ta zasada nie ma zastosowania w przypadku nazwy klasy po lewej stronie operatora rozpoznawania zakresu (:). Nazwy po lewej stronie operatora rozpoznawanie zakresów zawsze są traktowane jako nazwy klasy.  
  
 W poniższym przykładzie pokazano sposób zadeklarować wskaźnika do obiektu typu `Account` przy użyciu **klasy** — słowo kluczowe:  
  
```  
class Account *Checking = new class Account( Account );  
```  
  
 `Account` w inicjatorze (w nawiasach) w powyższych instrukcji ma zakresie pliku; jest typu **podwójne**.  
  
> [!NOTE]
>  Ponowne użycie nazwy identyfikatora, jak pokazano w poniższym przykładzie jest uważany za niska styl programowania.  
  
 Aby uzyskać więcej informacji na temat wskaźników, zobacz [typów pochodnych](http://msdn.microsoft.com/en-us/aa14183c-02fe-4d81-95fe-beddb0c01c7c). Informacje o deklaracji i inicjowania klasy obiektów, zobacz [klas, struktur i Unii](../cpp/classes-and-structs-cpp.md). Informacji o używaniu **nowe** i **usunąć** magazynu w warstwie bezpłatna operatorów, zobacz [nowy i delete — operatory](new-and-delete-operators.md).  
  
## <a name="hiding-names-with-file-scope"></a>Ukrywanie nazw z zakresem pliku  
 Aby ukryć nazw z zakresem pliku, jawnie Zadeklarowanie tej samej nazwie w zakresie bloku. Jednak nazwy pliku zakresów jest możliwy przy użyciu operatora rozpoznawanie zakresów (`::`).  
  
```  
// file_scopes.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int i = 7;   // i has file scope, outside all blocks  
using namespace std;  
  
int main( int argc, char *argv[] ) {  
   int i = 5;   // i has block scope, hides i at file scope  
   cout << "Block-scoped i has the value: " << i << "\n";  
   cout << "File-scoped i has the value: " << ::i << "\n";  
}  
```  
  
```Output  
Block-scoped i has the value: 5  
File-scoped i has the value: 7  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)