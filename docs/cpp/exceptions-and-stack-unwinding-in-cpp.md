---
title: Wyjątki i odwijanie stosu w języku C++
ms.date: 11/19/2019
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
ms.openlocfilehash: e0dadc90f85caeea359fca4ed0b45868ea77177e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221565"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>Wyjątki i odwijanie stosu w języku C++

W mechanizmie wyjątków C++, kontrola zostaje przekazana z instrukcji throw do pierwszej instrukcji catch, która może obsłużyć wyrzucony typ. Po osiągnięciu instrukcji catch wszystkie zmienne automatyczne, które są w zakresie między instrukcjami throw i catch, są niszczone w procesie, który jest znany jako odwracanie *stosu*. W odwijaniu stosu, wykonanie przebiega w następujący sposób:

1. Formant osiąga **`try`** instrukcję przez normalne wykonywanie sekwencyjne. Sekcja chroniona w **`try`** bloku jest wykonywana.

1. Jeśli podczas wykonywania sekcji chronionej nie wystąpi wyjątek, **`catch`** klauzule znajdujące się po **`try`** bloku nie są wykonywane. Wykonywanie jest kontynuowane w instrukcji po ostatniej **`catch`** klauzuli, która następuje po elemencie skojarzonym **`try`** bloku.

1. Jeśli wyjątek jest zgłaszany podczas wykonywania sekcji chronionej lub procedury, którą Sekcja chroniona wywołuje bezpośrednio lub pośrednio, obiekt wyjątku jest tworzony na podstawie obiektu utworzonego przez **`throw`** operand. (Oznacza to, że może być używany Konstruktor kopiujący). W tym momencie kompilator szuka **`catch`** klauzuli w wyższym kontekście wykonywania, który może obsłużyć wyjątek zgłoszonego typu lub dla **`catch`** programu obsługi, który może obsługiwać dowolny typ wyjątku. **`catch`** Programy obsługi są badane w kolejności ich występowania po **`try`** bloku. Jeśli nie zostanie znaleziona odpowiednia procedura obsługi, **`try`** zostanie zbadany następny dynamicznie otaczający blok. Ten proces jest kontynuowany do momentu zbadania najbardziej zewnętrznego otaczającego **`try`** bloku.

1. Jeśli nadal nie znaleziono pasującej klauzuli obsługi lub jeśli podczas procesu odwijania wystąpi wyjątek, ale zanim klauzula obsługi przejmie kontrolę, wywoływana jest wstępnie zdefiniowana funkcja `terminate`. Jeśli wyjątek wystąpi po wyrzuceniu wyjątku, ale przed rozpoczęciem odwijania, wywoływane jest `terminate`.

1. W przypadku znalezienia zgodnego **`catch`** programu obsługi i przechwycenia przez wartość jego parametr formalny jest inicjowany przez skopiowanie obiektu Exception. Jeżeli przechwyci kontrolę przez odwołanie, inicjowany jest parametr odwołujący się do obiektu wyjątku. Po zainicjowaniu parametru formalnego, rozpocznie się proces odwijania stosu. Dotyczy to niszczenia wszystkich obiektów automatycznych, które zostały w pełni skonstruowane — ale nie zostały jeszcze zadestruktorne — między początkiem **`try`** bloku, który jest skojarzony z **`catch`** programem obsługi, a lokacją throw wyjątku. Destrukcja następuje w odwrotnej kolejności do konstrukcji. **`catch`** Procedura obsługi jest wykonywana, a program wznawia wykonywanie po ostatniej obsłudze — to znaczy, na pierwszej instrukcji lub konstrukcji, która nie jest **`catch`** programem obsługi. Kontrolka może wprowadzać tylko **`catch`** procedurę obsługi poprzez zgłoszony wyjątek, nigdy za pomocą **`goto`** instrukcji lub **`case`** etykiety w **`switch`** instrukcji.

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
