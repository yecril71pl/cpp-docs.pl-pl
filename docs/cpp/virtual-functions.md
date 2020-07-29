---
title: Funkcje wirtualne
ms.date: 09/10/2019
helpviewer_keywords:
- functions [C++], virtual functions
- derived classes [C++], virtual functions
- virtual functions
ms.assetid: b3e1ed88-2a90-4af8-960a-16f47deb3452
ms.openlocfilehash: 4296d66af8f8bb9aed4946d6dc57871f447108d2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231042"
---
# <a name="virtual-functions"></a>Funkcje wirtualne

Funkcja wirtualna jest funkcją składową, która powinna zostać ponownie zdefiniowana w klasach pochodnych. Przy odwoływaniu się do obiektu klasy pochodnej za pomocą wskaźnika lub odwołania do klasy bazowej, można wywołać funkcję wirtualną dla tego obiektu i wykonać wersję klasy pochodnej tej funkcji.

Funkcje wirtualne zapewniają wywołanie poprawnej funkcji dla obiektu, bez względu na wyrażenie użyte do wywołania funkcji.

Załóżmy, że klasa bazowa zawiera funkcję zadeklarowaną jako [wirtualną](../cpp/virtual-cpp.md) , a Klasa pochodna definiuje tę samą funkcję. Funkcja z klasy pochodnej jest wywoływana dla obiektów klasy pochodnej, nawet jeśli jest wywoływana przy użyciu wskaźnika lub odwołania do klasy bazowej. W poniższym przykładzie przedstawiono klasę bazową, która dostarcza implementację funkcji `PrintBalance` i dwie klasy pochodne

```cpp
// deriv_VirtualFunctions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Account {
public:
   Account( double d ) { _balance = d; }
   virtual ~Account() {}
   virtual double GetBalance() { return _balance; }
   virtual void PrintBalance() { cerr << "Error. Balance not available for base type." << endl; }
private:
    double _balance;
};

class CheckingAccount : public Account {
public:
   CheckingAccount(double d) : Account(d) {}
   void PrintBalance() { cout << "Checking account balance: " << GetBalance() << endl; }
};

class SavingsAccount : public Account {
public:
   SavingsAccount(double d) : Account(d) {}
   void PrintBalance() { cout << "Savings account balance: " << GetBalance(); }
};

int main() {
   // Create objects of type CheckingAccount and SavingsAccount.
   CheckingAccount checking( 100.00 );
   SavingsAccount  savings( 1000.00 );

   // Call PrintBalance using a pointer to Account.
   Account *pAccount = &checking;
   pAccount->PrintBalance();

   // Call PrintBalance using a pointer to Account.
   pAccount = &savings;
   pAccount->PrintBalance();
}
```

W powyższym kodzie, wywołania `PrintBalance` są identyczne, z wyjątkiem tego, na co wskazuje obiekt `pAccount`. Ponieważ `PrintBalance` jest wirtualna, wywoływana jest wersja funkcji zdefiniowana dla każdego obiektu. Funkcja `PrintBalance` w klasach pochodnych `CheckingAccount` i `SavingsAccount` „zastępuje” funkcję w klasie bazowej `Account`.

Jeśli zadeklarowano klasę, która nie dostarcza zastąpionej implementacji funkcji `PrintBalance`, używana jest domyślna implementacja z klasy bazowej `Account`.

Funkcje w klasach pochodnych zastępują funkcje wirtualne w klasach bazowych tylko wtedy, gdy ich typ jest taki sam. Funkcja w klasie pochodnej nie może różnić się od funkcji wirtualnej w klasie bazowej tylko pod względem zwracanego typu; lista argumentów również musi się różnić.

Podczas wywoływania funkcji za pomocą wskaźników lub odwołań, obowiązują następujące zasady:

- Wywołanie funkcji wirtualnej jest rozwiązywane zgodnie z podstawowym typem obiektu, dla którego jest wywoływane.

- Wywołanie funkcji niewirtualnej jest rozwiązywane zgodnie z typem wskaźnika lub odwołania.

W poniższym przykładzie pokazano sposób, w jaki wirtualne i niewirtualne funkcje zachowują się po wywołaniu przez wskaźniki:

```cpp
// deriv_VirtualFunctions2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Base {
public:
   virtual void NameOf();   // Virtual function.
   void InvokingClass();   // Nonvirtual function.
};

// Implement the two functions.
void Base::NameOf() {
   cout << "Base::NameOf\n";
}

void Base::InvokingClass() {
   cout << "Invoked by Base\n";
}

class Derived : public Base {
public:
   void NameOf();   // Virtual function.
   void InvokingClass();   // Nonvirtual function.
};

// Implement the two functions.
void Derived::NameOf() {
   cout << "Derived::NameOf\n";
}

void Derived::InvokingClass() {
   cout << "Invoked by Derived\n";
}

int main() {
   // Declare an object of type Derived.
   Derived aDerived;

   // Declare two pointers, one of type Derived * and the other
   //  of type Base *, and initialize them to point to aDerived.
   Derived *pDerived = &aDerived;
   Base    *pBase    = &aDerived;

   // Call the functions.
   pBase->NameOf();           // Call virtual function.
   pBase->InvokingClass();    // Call nonvirtual function.
   pDerived->NameOf();        // Call virtual function.
   pDerived->InvokingClass(); // Call nonvirtual function.
}
```

```Output
Derived::NameOf
Invoked by Base
Derived::NameOf
Invoked by Derived
```

Należy zauważyć, że bez względu na to, czy funkcja `NameOf` jest wywoływana za pomocą wskaźnika do `Base`, czy wskaźnika do `Derived`, wywołuje funkcję dla `Derived`. Wywołuje funkcję dla `Derived`, ponieważ `NameOf` jest funkcją wirtualną i zarówno `pBase`, jak i `pDerived` wskazują obiekt typu `Derived`.

Ponieważ funkcje wirtualne są wywoływane tylko dla obiektów typu klasy, nie można zadeklarować funkcji globalnych lub statycznych jako **`virtual`** .

**`virtual`** Słowo kluczowe może być używane podczas deklarowania funkcji przesłaniania w klasie pochodnej, ale nie jest to konieczne; zastąpienia funkcji wirtualnych są zawsze wirtualne.

Funkcje wirtualne w klasie bazowej muszą być zdefiniowane, chyba że są deklarowane przy użyciu *czystego specyfikatora*. (Aby uzyskać więcej informacji na temat czystych funkcji wirtualnych, zobacz [klasy abstrakcyjne](../cpp/abstract-classes-cpp.md)).

Mechanizm wywołania funkcji wirtualnych można pominąć przez jawną kwalifikację nazwy funkcji za pomocą operatora rozpoznawania zakresu (`::`). Rozważmy wcześniejszy przykład obejmujący klasę `Account`. Aby wywołać `PrintBalance` w klasie bazowej, należy użyć następującego kodu:

```cpp
CheckingAccount *pChecking = new CheckingAccount( 100.00 );

pChecking->Account::PrintBalance();  //  Explicit qualification.

Account *pAccount = pChecking;  // Call Account::PrintBalance

pAccount->Account::PrintBalance();   //  Explicit qualification.
```

Oba wywołania `PrintBalance` w poprzednim przykładzie pomijają mechanizm wywołania funkcji wirtualnej.
