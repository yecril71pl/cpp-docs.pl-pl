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
ms.openlocfilehash: b05b2f6240876540cd9e67d83bcb88242b68827b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>Wyjątki i odwijanie stosu w języku C++
W mechanizmie wyjątków C++, kontrola zostaje przekazana z instrukcji throw do pierwszej instrukcji catch, która może obsłużyć wyrzucony typ. Po osiągnięciu instrukcji catch wszystkie automatyczne zmienne, które znajdują się w zakresie między throw i catch instrukcji zostaną zniszczone w procesie, znany jako *stosu rozwinięcia*. W odwijaniu stosu, wykonanie przebiega w następujący sposób:  
  
1.  Kontrola osiąga instrukcję `try` przez normalne wykonanie sekwencyjne. Wykonywana jest sekcja chroniona w bloku `try`.  
  
2.  Jeśli podczas wykonywania sekcji chronionej nie zostanie zgłoszony żaden wyjątek, klauzule `catch`, które następują po bloku `try` nie zostają wykonane. Wykonywanie jest kontynuowane na instrukcji znajdującej się po ostatniej klauzuli `catch`, która następuje po skojarzonym bloku `try`.  
  
3.  Jeśli wyjątek zostanie zgłoszony podczas wykonywania sekcji chronionej lub w dowolnej procedurze, która wywołuje sekcję chronioną bezpośrednio lub pośrednio, tworzony jest obiekt wyjątku z obiektu tworzonego przez operand `throw`. (Oznacza to, że konstruktor kopii może być zaangażowany.) W tym punkcie, kompilator szuka klauzuli `catch` w wyższym kontekście wykonania, która może obsłużyć wyjątek zgłoszonego typu lub klauzuli obsługi `catch`, która może obsłużyć dowolny typ wyjątku. Klauzule obsługi `catch` są weryfikowane w kolejności ich występowania po bloku `try`. Jeśli nie znaleziono odpowiedniej klauzuli obsługi, weryfikowany jest następny dynamicznie otaczający blok `try`. Proces ten jest kontynuowany aż do zweryfikowania najbardziej oddalonego otoczenia bloku `try`.  
  
4.  Jeśli nadal nie znaleziono pasującej klauzuli obsługi lub jeśli podczas procesu odwijania wystąpi wyjątek, ale zanim klauzula obsługi przejmie kontrolę, wywoływana jest wstępnie zdefiniowana funkcja `terminate`. Jeśli wyjątek wystąpi po wyrzuceniu wyjątku, ale przed rozpoczęciem odwijania, wywoływane jest `terminate`.  
  
5.  Jeśli zostanie znaleziona odpowiadająca klauzula obsługi `catch`, która przechwyci kontrolę przez wartość, jej parametr formalny jest inicjowany przez skopiowanie obiektu wyjątku. Jeżeli przechwyci kontrolę przez odwołanie, inicjowany jest parametr odwołujący się do obiektu wyjątku. Po zainicjowaniu parametru formalnego, rozpocznie się proces odwijania stosu. Wiąże się to ze zniszczeniem wszystkich obiektów automatycznych, które zostały w pełni skonstruowane — ale nie zostały jeszcze zniszczone — między początkiem bloku `try` skojarzonego z klauzulą obsługi `catch`, a lokalizacją throw wyjątku. Destrukcja następuje w odwrotnej kolejności do konstrukcji. Klauzula obsługi `catch` jest wykonywana, a program wznawia wykonanie po ostatniej klauzuli obsługi — to znaczy, w pierwszej instrukcji lub konstrukcji, która nie jest klauzulą obsługi `catch`. Klauzula obsługi `catch` może przejąć kontrolę tylko za pośrednictwem wyrzuconego wyjątku, nigdy poprzez instrukcję `goto` lub etykietę `case` w instrukcji `switch`.  
  
## <a name="stack-unwinding-example"></a>Przykład odwijania stosu  
 W poniższym przykładzie zilustrowano, jak stos jest odwijany, gdy zostaje wyrzucony wyjątek. Wykonanie na wątku przechodzi z instrukcji throw w `C` do instrukcji catch w `main` i rozwija każdą funkcję po drodze. Należy zauważyć kolejność, w której obiekty `Dummy` są tworzone i następnie niszczone, gdy wykraczają poza zakres. Należy również zauważyć, że żadna funkcja nie zostaje zakończona z wyjątkiem `main`, która zawiera instrukcję catch. Funkcja `A` nigdy nie wraca z wywołania `B()`, a `B` nigdy nie wraca z wywołania `C()`. Jeśli usuniesz komentarz definicji wskaźnika `Dummy` i odpowiadającą instrukcję delete, a następnie uruchomisz program, zobaczysz, że wskaźnik nigdy nie jest usuwany. Pokazuje to, co może się zdarzyć, gdy funkcje nie zapewniają gwarancji wyjątku. Aby uzyskać więcej informacji, zobacz: Jak projektować obsługę wyjątków. Jeśli komentarz wystąpi poza instrukcją catch, można zaobserwować, co się dzieje, gdy program zakończy wykonanie z powodu nieobsługiwanego wyjątku.  
  
```  
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