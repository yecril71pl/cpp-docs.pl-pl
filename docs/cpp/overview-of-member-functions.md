---
title: "Przegląd funkcji Członkowskich | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions [C++]
- inline functions [C++], treating member functions as
- member functions [C++], definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cfc355a58ae87bcb32d7abd72f1ff5cb6e980a6d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="overview-of-member-functions"></a>Przegląd funkcji członkowskich
Funkcje składowe są statyczne lub niestatyczne. Zachowanie statycznych funkcji Członkowskich różni się od innych funkcji elementów członkowskich, ponieważ statycznych funkcji Członkowskich ma niejawne nie **to** argumentu. Niestatyczne funkcje Członkowskie ma **to** wskaźnika. Funkcje członkowskie, zarówno statyczne, jak i niestatyczne, można zdefiniować w obrębie lub poza deklaracją klasy.  
  
 Jeśli funkcję członkowską zdefiniowano w obrębie deklaracji klasy, jest ona traktowana jak funkcja śródwierszowa i nie ma potrzeby kwalifikowania nazwy funkcji za pomocą nazwy klasy. Chociaż funkcje zdefiniowane wewnątrz deklaracji klasy już są traktowane jako funkcji śródwierszowych, możesz użyć **wbudowanego** — słowo kluczowe do kodu dokumentu.  
  
 Przykład deklarowania funkcji w obrębie deklaracji klasy:  
  
```  
// overview_of_member_functions1.cpp  
class Account  
{  
public:  
    // Declare the member function Deposit within the declaration  
    //  of class Account.  
    double Deposit( double HowMuch )  
    {  
        balance += HowMuch;  
        return balance;  
    }  
private:  
    double balance;  
};  
  
int main()  
{  
}  
```  
  
 Jeśli definicji funkcji członkowskiej poza deklaracji klasy, jest traktowany jako funkcja wbudowana tylko wtedy, gdy jest jawnie zadeklarowana jako **wbudowanego**. Ponadto, nazwa funkcji w definicji musi być kwalifikowana odpowiednią nazwą klasy za pomocą operatora rozpoznawania zakresu (`::`).  
  
 Poniższy przykład jest identyczny z poprzednią deklaracją klasy `Account`, z wyjątkiem tego, że funkcja `Deposit` jest zdefiniowana poza deklaracją klasy:  
  
```  
// overview_of_member_functions2.cpp  
class Account  
{  
public:  
    // Declare the member function Deposit but do not define it.  
    double Deposit( double HowMuch );  
private:  
    double balance;  
};  
  
inline double Account::Deposit( double HowMuch )  
{  
    balance += HowMuch;  
    return balance;  
}  
  
int main()  
{  
}  
```  
  
> [!NOTE]
>  Funkcje członkowskie można zdefiniować w obrębie deklaracji klasy lub oddzielnie, funkcji członkowskich nie można dodać do klasy po jej zdefiniowaniu.  
  
 Klasy zawierające funkcje członkowskie mogą mieć wiele deklaracji, ale same funkcje członkowskie mogą mieć tylko jedną definicję w programie. Wiele definicji powoduje wyświetlenie komunikatu o błędzie w czasie połączenia. Jeśli klasa zawiera definicje funkcji śródwierszowej, definicje funkcji muszą być identyczne, aby przestrzegać zasady „jednej definicji”.  
  
