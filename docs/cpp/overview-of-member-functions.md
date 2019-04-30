---
title: Przegląd funkcji członkowskich
ms.date: 11/04/2016
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions [C++]
- inline functions [C++], treating member functions as
- member functions [C++], definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
ms.openlocfilehash: faa7d016c8f48e9a5ee57c8efa4ce3dfd3f3eb01
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345854"
---
# <a name="overview-of-member-functions"></a>Przegląd funkcji członkowskich

Funkcje składowe są statyczne lub niestatyczne. Zachowanie statycznych funkcji Członkowskich różni się od innych funkcji Członkowskich, ponieważ statyczne funkcje Członkowskie nie mają niejawnego **to** argumentu. Niestatyczne funkcje Członkowskie mają **to** wskaźnika. Funkcje członkowskie, zarówno statyczne, jak i niestatyczne, można zdefiniować w obrębie lub poza deklaracją klasy.

Jeśli funkcję składową zdefiniowano w obrębie deklaracji klasy, jest ona traktowana jak funkcja śródwierszowa i nie ma potrzeby kwalifikowania nazwy funkcji za pomocą nazwy klasy. Chociaż funkcje zdefiniowane w obrębie deklaracji klasy są już traktowane jak funkcje śródwierszowe, można użyć **wbudowane** — słowo kluczowe, aby udokumentować kod.

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

Jeśli definicja funkcji składowej jest poza deklaracją klasy, jest ona traktowana jak funkcja śródwierszowa, tylko wtedy, gdy jest jawnie zadeklarowana jako **wbudowane**. Ponadto, nazwa funkcji w definicji musi być kwalifikowana odpowiednią nazwą klasy za pomocą operatora rozpoznawania zakresu (`::`).

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