---
title: Wyjątki i odwijanie stosu w języku C++
ms.date: 11/19/2019
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
ms.openlocfilehash: 11657206e86dbc81eb62c1e11b49fd87777f11d8
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246566"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>Wyjątki i odwijanie stosu w języku C++

W mechanizmie wyjątków C++, kontrola zostaje przekazana z instrukcji throw do pierwszej instrukcji catch, która może obsłużyć wyrzucony typ. Po osiągnięciu instrukcji catch wszystkie zmienne automatyczne, które są w zakresie między instrukcjami throw i catch, są niszczone w procesie, który jest znany jako odwracanie *stosu*. W odwijaniu stosu, wykonanie przebiega w następujący sposób:

1. Kontrolka osiąga instrukcję **try** przez normalne wykonywanie sekwencyjne. Sekcja chroniona w bloku **try** jest wykonywana.

1. Jeśli podczas wykonywania sekcji chronionej nie wystąpi wyjątek, klauzule **catch** wykonujące blok **try** nie są wykonywane. Wykonywanie jest kontynuowane w instrukcji po ostatniej klauzuli **catch** , która następuje po skojarzonym bloku **try** .

1. Jeśli wyjątek jest zgłaszany podczas wykonywania sekcji chronionej lub w każdej procedurze, którą Sekcja chroniona wywołuje bezpośrednio lub pośrednio, obiekt wyjątku jest tworzony na podstawie obiektu utworzonego przez operand operacji **throw** . (Oznacza to, że może być używany Konstruktor kopiujący). W tym momencie kompilator szuka klauzuli **catch** w wyższym kontekście wykonywania, który może obsłużyć wyjątek zgłoszonego typu lub dla procedury obsługi **catch** , która może obsługiwać dowolny typ wyjątku. Programy obsługi **catch** są badane w kolejności ich występowania po bloku **try** . Jeśli nie zostanie znaleziona odpowiednia procedura obsługi, zostanie sprawdzona Następna dynamicznie otaczający blok **try** . Ten proces jest kontynuowany, dopóki nie zostanie sprawdzony zewnętrzny otaczający blok **try** .

1. Jeśli nadal nie znaleziono pasującej klauzuli obsługi lub jeśli podczas procesu odwijania wystąpi wyjątek, ale zanim klauzula obsługi przejmie kontrolę, wywoływana jest wstępnie zdefiniowana funkcja `terminate`. Jeśli wyjątek wystąpi po wyrzuceniu wyjątku, ale przed rozpoczęciem odwijania, wywoływane jest `terminate`.

1. Jeśli zostanie znaleziony pasujący program obsługi **catch** i przechwytuje on wartość, jego parametr formalny jest inicjowany przez skopiowanie obiektu Exception. Jeżeli przechwyci kontrolę przez odwołanie, inicjowany jest parametr odwołujący się do obiektu wyjątku. Po zainicjowaniu parametru formalnego, rozpocznie się proces odwijania stosu. Dotyczy to niszczenia wszystkich obiektów automatycznych, które zostały w pełni skonstruowane — ale nie zostały jeszcze zadestruktorne — między początkiem bloku **try** , który jest skojarzony z obsługą **catch** i witryną throw wyjątku. Destrukcja następuje w odwrotnej kolejności do konstrukcji. Procedura obsługi **catch** jest wykonywana, a program wznawia wykonywanie po ostatniej obsłudze — to znaczy, na pierwszej instrukcji lub konstrukcji, która nie jest obsługą **catch** . Kontrolka może wprowadzać tylko procedurę obsługi **catch** poprzez zgłoszony wyjątek, nigdy za pomocą instrukcji **goto** lub etykiety **Case** w instrukcji **Switch** .

## <a name="stack-unwinding-example"></a>Przykład odwinięcia stosu

W poniższym przykładzie zilustrowano, jak stos jest odwijany, gdy zostaje wyrzucony wyjątek. Wykonanie na wątku przechodzi z instrukcji throw w `C` do instrukcji catch w `main` i rozwija każdą funkcję po drodze. Należy zauważyć kolejność, w której obiekty `Dummy` są tworzone i następnie niszczone, gdy wykraczają poza zakres. Należy również zauważyć, że żadna funkcja nie zostaje zakończona z wyjątkiem `main`, która zawiera instrukcję catch. Funkcja `A` nigdy nie wraca z wywołania `B()`, a `B` nigdy nie wraca z wywołania `C()`. Jeśli usuniesz komentarz definicji wskaźnika `Dummy` i odpowiadającą instrukcję delete, a następnie uruchomisz program, zobaczysz, że wskaźnik nigdy nie jest usuwany. Pokazuje to, co może się zdarzyć, gdy funkcje nie zapewniają gwarancji wyjątku. Aby uzyskać więcej informacji, zobacz: Jak projektować obsługę wyjątków. Jeśli komentarz wystąpi poza instrukcją catch, można zaobserwować, co się dzieje, gdy program zakończy wykonanie z powodu nieobsługiwanego wyjątku.

```cpp
#include <string>
#include <iostream>
using namespace std;

class MyException{};
class Dummy
{
    public:
    Dummy(string s) : MyName(s) { PrintMsg("Created Dummy:"); }
    Dummy(const Dummy& other) : MyName(other.MyName){ PrintMsg("Copy created Dummy:"); }
    ~Dummy(){ PrintMsg("Destroyed Dummy:"); }
    void PrintMsg(string s) { cout << s  << MyName <<  endl; }
    string MyName;
    int level;
};

void C(Dummy d, int i)
{
    cout << "Entering FunctionC" << endl;
    d.MyName = " C";
    throw MyException();

    cout << "Exiting FunctionC" << endl;
}

void B(Dummy d, int i)
{
    cout << "Entering FunctionB" << endl;
    d.MyName = "B";
    C(d, i + 1);
    cout << "Exiting FunctionB" << endl;
}

void A(Dummy d, int i)
{
    cout << "Entering FunctionA" << endl;
    d.MyName = " A" ;
  //  Dummy* pd = new Dummy("new Dummy"); //Not exception safe!!!
    B(d, i + 1);
 //   delete pd;
    cout << "Exiting FunctionA" << endl;
}

int main()
{
    cout << "Entering main" << endl;
    try
    {
        Dummy d(" M");
        A(d,1);
    }
    catch (MyException& e)
    {
        cout << "Caught an exception of type: " << typeid(e).name() << endl;
    }

    cout << "Exiting main." << endl;
    char c;
    cin >> c;
}

/* Output:
    Entering main
    Created Dummy: M
    Copy created Dummy: M
    Entering FunctionA
    Copy created Dummy: A
    Entering FunctionB
    Copy created Dummy: B
    Entering FunctionC
    Destroyed Dummy: C
    Destroyed Dummy: B
    Destroyed Dummy: A
    Destroyed Dummy: M
    Caught an exception of type: class MyException
    Exiting main.

*/
```
