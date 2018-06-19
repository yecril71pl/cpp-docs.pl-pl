---
title: C2666 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2666
dev_langs:
- C++
helpviewer_keywords:
- C2666
ms.assetid: 78364d15-c6eb-439a-9088-e04a0176692b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 773744baa1ff7f709a471c7324b7f60c3686a7c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235649"
---
# <a name="compiler-error-c2666"></a>C2666 błąd kompilatora
'Identyfikator': liczba przeciążenia mają podobne konwersje  
  
 Przeciążonej funkcji lub operator jest niejednoznaczna.   Listy parametrów formalnych może być zbyt podobne dla kompilatora w celu rozwiązania niejednoznaczności.  Aby rozwiązać ten problem, jawnie rzutować co najmniej jeden z parametrów rzeczywistych.  
  
 Poniższy przykład generuje C2666:  
  
```  
// C2666.cpp  
struct complex {  
   complex(double);  
};  
  
void h(int,complex);  
void h(double, double);  
  
int main() {  
   h(3,4);   // C2666  
}  
```  
  
 Ten błąd może być również generowany w wyniku pracy zgodność kompilatora, która została wykonana dla programu Visual Studio .NET 2003:  
  
-   operatory binarne i zdefiniowanych przez użytkownika konwersje na typy wskaźnika  
  
-   Konwersja kwalifikacji nie jest taka sama jak tożsamość konwersji  
  
 Dla operatorów binarnych \<, >, \<=, a > =, przekazany parametr teraz jest niejawnie przekonwertowana na typ operandu w przypadku typ parametru definiuje operator konwersji zdefiniowany przez użytkownika można przekonwertować na typ argumentu. Istnieje teraz możliwość niejednoznaczności.  
  
 Kod, który jest prawidłowy w Visual Studio .NET 2003 i wersji programu Visual Studio .NET programu Visual C++ należy wywołać operatora klasy jawnie przy użyciu składni funkcji.  
  
## <a name="example"></a>Przykład  
  
```  
// C2666b.cpp  
#include <string.h>  
#include <stdio.h>  
  
struct T   
{  
    T( const T& copy )   
    {  
        m_str = copy.m_str;  
    }  
  
    T( const char* str )   
    {  
        int iSize = (strlen( str )+ 1);  
        m_str = new char[ iSize ];  
        if (m_str)  
            strcpy_s( m_str, iSize, str );  
    }  
  
    bool operator<( const T& RHS )   
    {  
        return m_str < RHS.m_str;  
    }  
  
    operator char*() const   
    {  
        return m_str;  
    }  
  
    char* m_str;  
};  
  
int main()   
{  
    T str1( "ABCD" );  
    const char* str2 = "DEFG";  
  
    // Error - Ambiguous call to operator<()  
    // Trying to convert str1 to char* and then call   
    // operator<( const char*, const char* )?  
    //  OR  
    // trying to convert str2 to T and then call  
    // T::operator<( const T& )?  
  
    if( str1 < str2 )   // C2666  
  
    if ( str1.operator < ( str2 ) )   // Treat str2 as type T  
        printf_s("str1.operator < ( str2 )\n");  
  
    if ( str1.operator char*() < str2 )   // Treat str1 as type char*  
        printf_s("str1.operator char*() < str2\n");  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2666  
  
```  
// C2666c.cpp  
// compile with: /c  
  
enum E   
{  
    E_A,   E_B  
};  
  
class A   
{  
    int h(const E e) const {return 0; }  
    int h(const int i) { return 1; }  
    // Uncomment the following line to resolve.  
    // int h(const E e) { return 0; }  
  
    void Test()   
    {  
        h(E_A);   // C2666  
        h((const int) E_A);  
        h((int) E_A);  
    }  
};  
```