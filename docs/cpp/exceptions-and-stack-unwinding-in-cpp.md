---
title: Wyjątki i Odwijanie stosu w języku C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a413179ca2c44d1a66ae1702c690039383d1045
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032214"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>Wyjątki i odwijanie stosu w języku C++

W mechanizmie wyjątków C++, kontrola zostaje przekazana z instrukcji throw do pierwszej instrukcji catch, która może obsłużyć wyrzucony typ. Gdy osiągnięta zostanie instrukcja catch, wszystkie zmienne automatyczne, które znajdują się w zakresie między throw i catch, instrukcje są niszczone w procesie, który jest znany jako *odwijanie stosu*. W odwijaniu stosu, wykonanie przebiega w następujący sposób:

1. Kontrola osiąga **spróbuj** instrukcji przez normalne wykonanie sekwencyjne. Sekcja chroniona w **spróbuj** blok jest wykonywany.

1. Jeśli żaden wyjątek zostanie zgłoszony podczas wykonywania sekcji chronionej **catch** klauzul, które należy wykonać **spróbuj** bloku nie są wykonywane. Wykonywanie jest kontynuowane na instrukcji znajdującej się po ostatniej **catch** klauzula, która następuje po skojarzonym **spróbuj** bloku.

1. Jeśli wyjątek zostanie zgłoszony podczas wykonywania sekcji chronionej lub w dowolnej procedurze, która wywołuje sekcję chronioną bezpośrednio lub pośrednio, tworzony jest obiekt wyjątku z obiektu, który jest tworzony przez **throw** operand. (Oznacza to, że konstruktor kopii może być zaangażowany.) W tym momencie, kompilator szuka **catch** w wyższym kontekście wykonania, która może obsłużyć wyjątek zgłoszonego typu lub dla klauzuli **catch** program obsługi, który może obsłużyć dowolny typ wyjątku. **Catch** obsługi są badane w kolejności ich występowania po **spróbuj** bloku. Jeśli nie odpowiedni program obsługi zostanie znaleziony, następny dynamicznie otaczający **spróbuj** bloku jest sprawdzany pod. Ten proces jest kontynuowany do momentu oddalonego **spróbuj** bloku jest sprawdzany pod.

1. Jeśli nadal nie znaleziono pasującej klauzuli obsługi lub jeśli podczas procesu odwijania wystąpi wyjątek, ale zanim klauzula obsługi przejmie kontrolę, wywoływana jest wstępnie zdefiniowana funkcja `terminate`. Jeśli wyjątek wystąpi po wyrzuceniu wyjątku, ale przed rozpoczęciem odwijania, wywoływane jest `terminate`.

1. Jeśli pasujący obiekt typu **catch** program obsługi zostanie znaleziony i przechwyci kontrolę przez wartość, jej parametr formalny jest inicjowany przez skopiowanie obiektu wyjątku. Jeżeli przechwyci kontrolę przez odwołanie, inicjowany jest parametr odwołujący się do obiektu wyjątku. Po zainicjowaniu parametru formalnego, rozpocznie się proces odwijania stosu. Obejmuje to ze zniszczeniem wszystkich obiektów automatycznych, które zostały w pełni skonstruowane —, ale nie zostały jeszcze zniszczone — między początkiem **spróbuj** blok, który jest skojarzony z **catch** obsługi i throw lokacji wyjątku. Destrukcja następuje w odwrotnej kolejności do konstrukcji. **Catch** program obsługi jest wykonywana, a program wznawia wykonanie po ostatniej klauzuli obsługi — oznacza to, w pierwszej instrukcji lub konstrukcji, która nie jest **catch** programu obsługi. Kontroli można wprowadzić tylko **catch** obsługi za pośrednictwem wyrzuconego wyjątku, nigdy poprzez **goto** instrukcji lub **przypadek** etykiety w **Przełącz** Instrukcja.

## <a name="stack-unwinding-example"></a>Przykład odwijania stosu

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