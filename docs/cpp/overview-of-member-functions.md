---
title: Przegląd funkcji członkowskich
ms.date: 11/04/2016
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions [C++]
- inline functions [C++], treating member functions as
- member functions [C++], definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
ms.openlocfilehash: d1c3e069325363276e58a617d6ba21cb0b6e4ff0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188470"
---
# <a name="overview-of-member-functions"></a>Przegląd funkcji członkowskich

Funkcje składowe są statyczne lub niestatyczne. Zachowanie statycznych funkcji Członkowskich różni się od innych funkcji Członkowskich, ponieważ statyczne funkcje członkowskie nie mają niejawnego **tego** argumentu. Niestatyczne funkcje składowe mają **ten** wskaźnik. Funkcje członkowskie, zarówno statyczne, jak i niestatyczne, można zdefiniować w obrębie lub poza deklaracją klasy.

Jeśli funkcję składową zdefiniowano w obrębie deklaracji klasy, jest ona traktowana jak funkcja śródwierszowa i nie ma potrzeby kwalifikowania nazwy funkcji za pomocą nazwy klasy. Chociaż funkcje zdefiniowane wewnątrz deklaracji klasy są już traktowane jako funkcje wbudowane, można użyć **wbudowanego** słowa kluczowego, aby dokumentować kod.

Przykład deklarowania funkcji w obrębie deklaracji klasy:

```cpp
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

Jeśli definicja funkcji składowej znajduje się poza deklaracją klasy, jest traktowana jako funkcja wbudowana tylko wtedy, gdy jest jawnie zadeklarowana jako **wbudowana**. Ponadto, nazwa funkcji w definicji musi być kwalifikowana odpowiednią nazwą klasy za pomocą operatora rozpoznawania zakresu (`::`).

Poniższy przykład jest identyczny z poprzednią deklaracją klasy `Account`, z wyjątkiem tego, że funkcja `Deposit` jest zdefiniowana poza deklaracją klasy:

```cpp
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
>  Funkcje składowe można zdefiniować w obrębie deklaracji klasy lub oddzielnie, funkcji składowych nie można dodać do klasy po jej zdefiniowaniu.

Klasy zawierające funkcje składowe mogą mieć wiele deklaracji, ale same funkcje składowe mogą mieć tylko jedną definicję w programie. Wiele definicji powoduje wyświetlenie komunikatu o błędzie w czasie połączenia. Jeśli klasa zawiera definicje funkcji śródwierszowej, definicje funkcji muszą być identyczne, aby przestrzegać zasady „jednej definicji”.
