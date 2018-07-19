---
title: New — Operator (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b01a7f2ca1af2ef114347d7355fbd1be973b8af
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37948260"
---
# <a name="new-operator-c"></a>new — Operator (C++)
Przydziela pamięć dla obiektu lub tablicy obiektów *nazwy typu* z wolnego magazynu i zwraca wskaźnik odpowiednio wpisany, różniącego wartość różną od zera do obiektu.  
  
> [!NOTE]
>  Rozszerzenia składnik C++ firmy Microsoft zapewnia obsługę **nowe** — słowo kluczowe, aby dodać wpisy szczeliny vtable. Aby uzyskać więcej informacji, zobacz [new (nowe gniazdo w vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
## <a name="syntax"></a>Składnia  
  
```  
[::] new [placement] new-type-name [new-initializer]  
[::] new [placement] ( type-name ) [new-initializer]  
```  
  
## <a name="remarks"></a>Uwagi  
 W przypadku niepowodzenia **nowe** zwraca wartość zero lub zgłasza wyjątek; zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md) Aby uzyskać więcej informacji. Można zmienić to zachowanie domyślne, tworząc niestandardowe procedury obsługi wyjątków i wywoływania [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) funkcji biblioteki wykonawczej z nazwą Twojej funkcji jako argumentem.  
  
 Aby uzyskać informacje na temat tworzenia obiektu w zarządzanym stosie, zobacz [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md).  
  
 Gdy **nowe** jest używany, można przydzielić pamięci dla obiektu klasy C++, Konstruktor obiektu jest wywoływana po alokowaniu pamięci.  
  
 Użyj [Usuń](../cpp/delete-operator-cpp.md) operator, aby dealokować pamięć alokowaną z **nowe** operatora.  
  
 Poniższy przykład przydziela i następnie zwalnia dwuwymiarową tablicę znaków o rozmiarze `dim` przez 10. Przy alokowaniu wielowymiarowej tablicy, wszystkie wymiary, z wyjątkiem pierwszej muszą być wyrażeniami stałymi, które obliczają do wartości dodatnich; wymiar tablicy skrajnie po lewej stronie może być dowolne wyrażenie, którego wynikiem jest wartość dodatnią. Alokując tablicę przy użyciu **nowe** operatora, pierwszy wymiar może być zerem — **nowe** operator zwraca unikalny wskaźnik.  
  
```cpp 
char (*pchar)[10] = new char[dim][10];  
delete [] pchar;  
```  
  
 *Nazwy typu* nie może zawierać **const**, **volatile**, deklaracji klasy lub deklaracji enumeracji. W związku z tym poniższe wyrażenie jest niedozwolone:  
  
```cpp 
volatile char *vch = new volatile char[20];  
```  
  
 **Nowe** operator nie przydziela typów odwołań, ponieważ nie są obiektami.  
  
 **Nowe** operator nie może służyć do przydzielania funkcji, ale może służyć do przydzielania wskaźników do funkcji. Poniższy przykład przydziela i następnie zwalnia tablicę siedmiu wskaźników do funkcji, które zwracają liczby całkowite.  
  
```cpp 
int (**p) () = new (int (*[7]) ());  
delete *p;  
```  
  
 Jeśli korzystasz z operatora **nowe** bez żadnych dodatkowych argumentów i kompilujesz z [/GX](../build/reference/gx-enable-exception-handling.md), [/eha](../build/reference/eh-exception-handling-model.md), lub [/EHS](../build/reference/eh-exception-handling-model.md) opcja, kompilator będzie Generuj kod aby wywołać operator **Usuń** Jeśli Konstruktor zgłasza wyjątek.  
  
 Na poniższej liście opisano elementy gramatyki **nowe**:  
  
 *placement*  
 Zapewnia możliwość przekazywania dodatkowych argumentów, jeśli przeładujesz **nowe**.  
  
 *Nazwa typu*  
 Określa typ ma zostać przydzielony; może być typ wbudowany lub zdefiniowany przez użytkownika. Jeśli specyfikacja typu jest skomplikowana, może być otoczona nawiasami, aby wymusić kolejność wiązania.  
  
 *initializer*  
 Oferuje wartości dla zainicjowanego obiektu. Nie można określić inicjatorów dla tablic. **Nowe** operator spowoduje utworzenie tablic obiektów tylko wtedy, gdy klasa ma domyślnego konstruktora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przydziela tablicy znaków i obiekt klasy `CName` i następnie zwalnia je.  
  
```cpp 
// expre_new_Operator.cpp  
// compile with: /EHsc  
#include <string.h>  
  
class CName {  
public:  
   enum {  
      sizeOfBuffer = 256  
   };  
  
   char m_szFirst[sizeOfBuffer];  
   char m_szLast[sizeOfBuffer];  
  
public:  
   void SetName(char* pszFirst, char* pszLast) {  
     strcpy_s(m_szFirst, sizeOfBuffer, pszFirst);  
     strcpy_s(m_szLast, sizeOfBuffer, pszLast);  
   }  
  
};  
  
int main() {  
   // Allocate memory for the array  
   char* pCharArray = new char[CName::sizeOfBuffer];  
   strcpy_s(pCharArray, CName::sizeOfBuffer, "Array of characters");  
  
   // Deallocate memory for the array  
   delete [] pCharArray;             
   pCharArray = NULL;  
  
   // Allocate memory for the object  
   CName* pName = new CName;  
   pName->SetName("Firstname", "Lastname");  
  
   // Deallocate memory for the object  
   delete pName;  
   pName = NULL;  
}  
```  
  
## <a name="example"></a>Przykład  
 Jeśli korzystasz z formularza nowego położenia z **nowe** operatora, formularza z argumentami prócz rozmiaru alokacji, kompilator nie obsługuje formularza położenia **Usuń** operator Jeśli Konstruktor zgłasza wyjątek. Na przykład:  
  
```cpp 
// expre_new_Operator2.cpp  
// C2660 expected  
class A {  
public:  
   A(int) { throw "Fail!"; }  
};  
void F(void) {  
   try {  
      // heap memory pointed to by pa1 will be deallocated  
      // by calling ::operator delete(void*).  
      A* pa1 = new A(10);  
   } catch (...) {  
   }  
   try {  
      // This will call ::operator new(size_t, char*, int).  
      // When A::A(int) does a throw, we should call  
      // ::operator delete(void*, char*, int) to deallocate  
      // the memory pointed to by pa2.  Since  
      // ::operator delete(void*, char*, int) has not been implemented,  
      // memory will be leaked when the deallocation cannot occur.  
  
      A* pa2 = new(__FILE__, __LINE__) A(20);  
   } catch (...) {  
   }  
}  
  
int main() {  
   A a;  
}  
```  
  
## <a name="initializing-object-allocated-with-new"></a>Inicjowanie obiektów przydzielonych za pomocą nowego  
 Opcjonalny *inicjatora* pole jest uwzględniane w gramatyce dla **nowe** operatora. Dzięki temu nowe obiekty mogą zostać zainicjowane z konstruktorów zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji dotyczących sposobu inicjalizacji, zobacz [inicjatory](../cpp/initializers.md). Poniższy przykład ilustruje sposób użycia wyrażenia inicjowania **nowe** operator:  
  
```cpp 
// expre_Initializing_Objects_Allocated_with_new.cpp  
class Acct  
{  
public:  
    // Define default constructor and a constructor that accepts  
    //  an initial balance.  
    Acct() { balance = 0.0; }  
    Acct( double init_balance ) { balance = init_balance; }  
private:  
    double balance;  
};  
  
int main()  
{  
    Acct *CheckingAcct = new Acct;  
    Acct *SavingsAcct = new Acct ( 34.98 );  
    double *HowMuch = new double ( 43.0 );  
    // ...  
}  
```  
  
 W tym przykładzie obiekt `CheckingAcct` jest przydzielany za pomocą **nowe** operatora, ale nie domyślna Inicjalizacja jest określony. W związku z tym, wywoływany jest domyślny konstruktor dla klasy `Acct()`. Następnie obiekt `SavingsAcct` jest przydzielany ten sam sposób, chyba że wyraźnie jest zainicjowany na 34.98. Ponieważ 34.98 jest typu **double**, Konstruktor, który przyjmuje argument typu jest wywoływana w celu zainicjowania obsługi. Wreszcie, typ nonclass `HowMuch` jest zainicjowany na 43.0.  
  
 Jeśli obiekt jest typu klasy i klasa ma konstruktory (tak jak w poprzednim przykładzie), obiekty mogą być zainicjowane przez **nowe** operatora tylko wtedy, gdy jest spełniony jeden z następujących warunków:  
  
-   Argumenty dostarczone w inicjatorze zgadzają się z tymi z konstruktora.  
  
-   Klasa ma domyślny konstruktor (konstruktor, który można wywołać bez argumentów).  
  
 Inicjowanie elementu jawnego nie może odbywać się podczas przydzielania tablic przy użyciu **nowe** operator; tylko Konstruktor domyślny, jeśli jest obecny, jest wywoływana. Zobacz [argumenty domyślne](../cpp/default-arguments.md) Aby uzyskać więcej informacji.  
  
 Jeśli alokacja pamięci nie powiedzie się (**nowy operator** zwraca wartość 0), inicjowanie nie jest wykonywane. Chroni to przed próbami inicjalizacji danych, które nie istnieją.  
  
 Podobnie jak w przypadku wywołań funkcji, kolejność oceny inicjowanych wyrażeń nie jest zdefiniowana. Ponadto, nie należy zakładać, że te wyrażenia zostaną całkowicie ocenione przed wykonaniem alokacji pamięci. Jeśli alokacja pamięci nie powiedzie się i **nowe** operator zwraca zero, niektóre wyrażenia w inicjatorze mogą nie zostać całkowicie ocenione.  
  
## <a name="lifetime-of-objects-allocated-with-new"></a>Okres istnienia obiektów przydzielonych za pomocą nowego  
 Obiekty przydzielone za pomocą **nowe** operator nie są niszczone, gdy zostanie zakończone zakresu, w której są zdefiniowane. Ponieważ **nowe** operator zwraca wskaźnik do obiektów, przydziela, program musi definiować wskaźnik przy użyciu odpowiedniego zakresu dostępu do tych obiektów. Na przykład:  
  
```cpp 
// expre_Lifetime_of_Objects_Allocated_with_new.cpp  
// C2541 expected  
int main()  
{  
    // Use new operator to allocate an array of 20 characters.  
    char *AnArray = new char[20];  
  
    for( int i = 0; i < 20; ++i )  
    {  
        // On the first iteration of the loop, allocate  
        //  another array of 20 characters.  
        if( i == 0 )  
        {  
            char *AnotherArray = new char[20];  
        }  
    }  
  
    delete [] AnotherArray; // Error: pointer out of scope.  
    delete [] AnArray;      // OK: pointer still in scope.  
}  
```  
  
 Gdy wskaźnik myszy `AnotherArray` zbliża się poza zakresem, w tym przykładzie obiekt już nie może zostać usunięty.  
  
## <a name="how-new-works"></a>Działa jak nowe  
 *Wyrażenie alokacji* — wyrażenie zawierające **nowe** operator — wykonuje trzy rzeczy:  
  
-   Lokalizuje i rezerwuje pamięć dla obiektu lub obiektów, które mają zostać przydzielone. Po ukończeniu tego etapu, poprawna ilość pamięci jest przydzielana, ale nie jest jeszcze obiektem.  
  
-   Inicjalizuje obiekt(y). Po zakończeniu inicjalizacji, wystarczająca ilość informacji jest obecna dla przydzielenia pamięci, która ma być obiektem.  
  
-   Zwraca wskaźnik do obiektu(ów) typu wskaźnika pochodną *nową nazwę typu* lub *nazwy typu*. Program używa tego wskaźnika do dostępu do nowo przydzielonego obiektu.  
  
 **Nowe** operator wywołuje funkcję **nowy operator**. Dla tablic dowolnego typu i obiektów, które nie są **klasy**, **struktury**, lub **Unii** typów, funkcja globalna **:: nowy operator**, jest wywołuje się, aby przydzielić magazyn. Obiekty typu klasy mogą definiować własne **nowy operator** funkcja statycznej składowej na podstawie klasy.  
  
 Gdy kompilator napotka **nowe** operator można przydzielić obiektu typu **typu**, emituje wywołanie `type` **:: nowy operator (sizeof (** `type` **))** lub, jeśli nie zdefiniowana przez użytkownika **nowy operator** jest zdefiniowany, **:: nowy operator (sizeof (** `type` **))**. W związku z tym **nowe** — operator może alokować poprawną ilość pamięci dla obiektu.  
  
> [!NOTE]
>  Argument **nowy operator** typu `size_t`. Ten typ jest zdefiniowany w \<direct.h >, \<malloc.h >, \<memory.h >, \<search.h >, \<stddef.h >, \<stdio.h >, \<stdlib.h >, \<string.h >, a \<time.h >.  
  
 Opcja w gramatyce umożliwia specyfikację *umieszczania* (zobacz gramatyka dla [operatora new](../cpp/new-operator-cpp.md)). *Umieszczania* parametru należy używać tylko w przypadku implementacji użytkownika **nowy operator**; umożliwia dodatkowe informacje, które zostaną przekazane do **nowy operator**. Wyrażenia z *umieszczania* pola, takie jak `T *TObject = new ( 0x0040 ) T;` jest tłumaczona na `T *TObject = T::operator new( sizeof( T ), 0x0040 );` Jeśli klasa T ma operator składowy new, w przeciwnym razie do `T *TObject = ::operator new( sizeof( T ), 0x0040 );`.  
  
 Oryginalny zamiar *umieszczania* pole było dopuszcza się użycia obiektów zależnych od sprzętu do przydzielenia w określonym przez użytkownika.  
  
> [!NOTE]
>  Mimo że w poprzednim przykładzie pokazano tylko jeden argument w *umieszczania* pola, nie ma żadnych ograniczeń, o ile dodatkowych argumentów może być przekazywany do **nowy operator** w ten sposób.  
  
 Nawet wtedy, gdy **nowy operator** został zdefiniowany dla typu klasy, globalny operator może służyć za pomocą formularza, w tym przykładzie:  
  
```cpp 
T *TObject =::new TObject;  
```  
  
 Operator rozpoznawania zakresu (`::`) wymusza użycie globalnego **nowe** operatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [nowe i delete — operatory](../cpp/new-and-delete-operators.md)