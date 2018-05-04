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
ms.openlocfilehash: 365beedce529e29be73c02caa57e5c6236565b9c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="new-operator-c"></a>new — Operator (C++)
Przydziela pamięć dla obiekt lub tablicę obiektów *nazwy typu* z bezpłatną magazynu i zwraca wskaźnik typizowany odpowiednio, różną od zera do obiektu.  
  
> [!NOTE]
>  Rozszerzenia składnika C++ firmy Microsoft zapewnia obsługę `new` — słowo kluczowe, aby dodać wpisy gniazda vtable. Aby uzyskać więcej informacji, zobacz [new (nowe gniazdo w vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
## <a name="syntax"></a>Składnia  
  
```  
[::] new [placement] new-type-name [new-initializer]  
[::] new [placement] ( type-name ) [new-initializer]  
```  
  
## <a name="remarks"></a>Uwagi  
 W przypadku niepowodzenia **nowe** zwraca zero lub zgłasza wyjątek; zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md) Aby uzyskać więcej informacji. To zachowanie domyślne można zmienić, tworząc niestandardowe procedury obsługi wyjątków i wywoływania [_set_new_handler —](../c-runtime-library/reference/set-new-handler.md) funkcja biblioteki wykonawczej nazwą funkcji jako jej argument.  
  
 Aby uzyskać informacje dotyczące sposobu tworzenia obiektów na stercie zarządzanej, zobacz [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md).  
  
 Gdy **nowe** jest używana, można przydzielić pamięci dla obiekt klasy C++, konstruktora obiektu jest wywoływana po jest przydzielana pamięć.  
  
 Użyj [usunąć](../cpp/delete-operator-cpp.md) operatora, aby zwolnić pamięć przydzielona z **nowe** operatora.  
  
 W poniższym przykładzie przydziela i następnie zwalnia jest tablicą dwuwymiarową znaków rozmiar `dim` przez 10. Podczas przydzielania tablicy wielowymiarowej, wszystkie wymiary oprócz pierwszego muszą być stałych wyrażeń określających wartości dodatnie. wymiar tablicy po lewej stronie może być dowolne wyrażenie, którego wynikiem jest wartość dodatnia. Podczas przydzielania tablicy przy użyciu **nowe** operatora, pierwszy wymiar może być równa zero — **nowe** operator zwraca wskaźnik unikatowy.  
  
```  
char (*pchar)[10] = new char[dim][10];  
delete [] pchar;  
```  
  
 *Nazwy typu* nie może zawierać **const**, `volatile`, deklaracji klasy lub deklaracji wyliczenia. W związku z tym następujące wyrażenie jest niedozwolone:  
  
```  
volatile char *vch = new volatile char[20];  
```  
  
 **Nowe** operator nie przydzielić typy odwołań, ponieważ nie są obiektami.  
  
 **Nowe** przydzielić funkcji nie można używać operatora, ale może służyć do przydzielenia wskaźniki do funkcji. Poniższy przykład przydziela i następnie zwalnia tablicę siedmiu wskaźniki do funkcji zwracających liczb całkowitych.  
  
```  
int (**p) () = new (int (*[7]) ());  
delete *p;  
```  
  
 Jeśli używasz operator **nowe** bez żadnych dodatkowych argumentów i skompiluj z [/GX](../build/reference/gx-enable-exception-handling.md), [/eha](../build/reference/eh-exception-handling-model.md), lub [/EHS](../build/reference/eh-exception-handling-model.md) opcja, kompilator będzie Generuj kod wywoła operator **usunąć** Jeśli w Konstruktorze zgłasza wyjątek.  
  
 Na poniższej liście opisano elementy gramatyki **nowe**:  
  
 *placement*  
 Umożliwia przekazywanie dodatkowe argumenty, jeśli można przeciążać **nowe**.  
  
 *Nazwa typu*  
 Określa typ do przydzielenia; może być typu wbudowanego lub zdefiniowanej przez użytkownika. Jeśli specyfikacja typu jest skomplikowane, może być ujęte w nawiasy, aby wymusić kolejności wiązania.  
  
 *initializer*  
 Zawiera wartość dla obiekt zainicjowane. Nie można określić Inicjatory dla tablic. **Nowe** operator utworzy tablice obiektów tylko wtedy, gdy klasa ma konstruktora domyślnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przydziela tablicy znaków i obiekt klasy `CName` , a następnie pozwala im.  
  
```  
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
 Jeśli używasz nowego formularza umieszczania z **nowe** operatora formularza z argumentami oprócz rozmiar alokacji kompilator nie obsługuje formularza umieszczania **usunąć** — operator Jeśli Konstruktor zgłasza wyjątek. Na przykład:  
  
```  
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
  
## <a name="initializing-object-allocated-with-new"></a>Inicjowanie obiektów przydzielonych za pomocą instrukcji new  
 Opcjonalny *inicjatora* pole jest uwzględniane w gramatyce dla **nowe** operatora. Dzięki temu nowe obiekty mogą zostać zainicjowane z konstruktorów zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji dotyczących sposobu inicjowania jest wykonywane, zobacz [inicjatory](../cpp/initializers.md). Poniższy przykład przedstawia sposób użycia wyrażenia inicjowania z **nowe** operator:  
  
```  
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
  
 W tym przykładzie obiekt `CheckingAcct` jest przydzielany przy użyciu **nowe** określono operatora, ale nie inicjowanie domyślnych. W związku z tym, wywoływany jest domyślny konstruktor dla klasy `Acct()`. Następnie obiekt `SavingsAcct` jest przydzielany ten sam sposób, chyba że wyraźnie jest zainicjowany na 34.98. Ponieważ typ jest 34.98 **podwójne**, Konstruktor, który przyjmuje argument typu jest wywoływana w celu inicjowania obsługi. Wreszcie, typ nonclass `HowMuch` jest zainicjowany na 43.0.  
  
 Jeśli obiekt jest typu klasy, a klasy ma konstruktorów (tak jak w poprzednim przykładzie), można zainicjować obiektu przez **nowe** operator tylko wtedy, gdy jest spełniony jeden z następujących warunków:  
  
-   Argumenty dostarczone w inicjatorze zgadzają się z tymi z konstruktora.  
  
-   Klasa ma domyślny konstruktor (konstruktor, który można wywołać bez argumentów).  
  
 Nie inicjowania elementu jawne może odbywać się podczas przydzielania stałych przy użyciu **nowe** operator; tylko Konstruktor domyślny, jeśli istnieje, jest nazywany. Zobacz [argumenty domyślne](../cpp/default-arguments.md) Aby uzyskać więcej informacji.  
  
 Jeśli alokacja pamięci nie powiedzie się (`operator new` zwraca wartość 0), inicjowanie nie jest wykonywane. Chroni to przed próbami inicjalizacji danych, które nie istnieją.  
  
 Podobnie jak w przypadku wywołań funkcji, kolejność oceny inicjowanych wyrażeń nie jest zdefiniowana. Ponadto, nie należy zakładać, że te wyrażenia zostaną całkowicie ocenione przed wykonaniem alokacji pamięci. Jeśli alokacja pamięci nie powiedzie się i **nowe** operator zwraca zero, niektóre inicjatora może nie być całkowicie obliczone wyrażenia.  
  
## <a name="lifetime-of-objects-allocated-with-new"></a>Okres istnienia obiektów przydzielonych za pomocą instrukcji new  
 Obiektów przydzielonych za pomocą **nowe** operator nie zostaną zniszczone, gdy zakres, w którym są definiowane jest zakończony. Ponieważ **nowe** operator zwraca wskaźnik do przydzielania obiektów, program musi definiować wskaźnika z odpowiedniego zakresu dostępu do tych obiektów. Na przykład:  
  
```  
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
  
 Raz wskaźnik `AnotherArray` zbliża się poza zakresem w przykładzie obiekt już nie mogą zostać usunięte.  
  
## <a name="how-new-works"></a>Jak nowe działania  
 *Wyrażenie alokacji* — wyrażenia zawierającego **nowe** operator — trzy elementy:  
  
-   Lokalizuje i rezerwuje pamięć dla obiektu lub obiektów, które mają zostać przydzielone. Po ukończeniu tego etapu, poprawna ilość pamięci jest przydzielana, ale nie jest jeszcze obiektem.  
  
-   Inicjalizuje obiekt(y). Po zakończeniu inicjalizacji, wystarczająca ilość informacji jest obecna dla przydzielenia pamięci, która ma być obiektem.  
  
-   Zwraca wskaźnik do obiektów typu wskaźnika pochodną *nową nazwę typu* lub *nazwy typu*. Program używa tego wskaźnika do dostępu do nowo przydzielonego obiektu.  
  
 **Nowe** operator wywołuje funkcję `operator new`. Dla tablic dowolnego typu, a dla obiektów, które nie mają **klasy**, `struct`, lub **Unii** typów, funkcją globalną **:: nowy operator**, jest wywoływana, aby przydzielić magazyn. Obiekty typu klasy mogą definiować własne statyczne funkcje składowe `operator new` na podstawie klasy.  
  
 Gdy wystąpi kompilator **nowe** operator można przydzielić obiektu typu `type`, wystawia wywołanie `type` **:: nowy operator (sizeof (** `type` **))**  lub, jeśli nie, zdefiniowane przez użytkownika `operator new` jest zdefiniowany, **:: nowy operator (sizeof (** `type` **))**. W związku z tym **nowe** operator może Przydziel poprawną ilość pamięci dla obiektu.  
  
> [!NOTE]
>  Argument `operator new` jest typu **size_t**. Ten typ jest zdefiniowany w \<direct.h >, \<malloc.h >, \<memory.h >, \<search.h >, \<stddef.h >, \<stdio.h >, \<stdlib.h >, \<string.h >, a \<time.h >.  
  
 Opcja w gramatyce umożliwia określenie *umieszczania* (zobacz gramatyki dla [operatora new](../cpp/new-operator-cpp.md)). *Umieszczania* parametr może zostać użyty tylko w przypadku wdrożeń użytkownika `operator new`; umożliwia dodatkowe informacje, które mają być przekazane do `operator new`. Wyrażenia z *umieszczania* pola, takie jak `T *TObject = new ( 0x0040 ) T;` jest translacji `T *TObject = T::operator new( sizeof( T ), 0x0040 );` Jeśli klasa T operator członkowski nowe, w przeciwnym razie `T *TObject = ::operator new( sizeof( T ), 0x0040 );`.  
  
 Oryginalny zamiar *umieszczania* pole było umożliwiające obiektów zależnych od sprzętu można przydzielić na adresy określone przez użytkownika.  
  
> [!NOTE]
>  Mimo że w poprzednim przykładzie pokazano tylko jeden argument w *umieszczania* pola nie podlega ograniczeniom, na ile dodatkowe argumenty mogą zostać przekazane do `operator new` w ten sposób.  
  
 Nawet jeśli `operator new` został zdefiniowany dla typu klasy, globalny operator może być używany za pomocą formy w tym przykładzie:  
  
```  
T *TObject =::new TObject;  
```  
  
 Operator rozpoznawanie zakresów (`::`) wymusza stosowanie globalnej **nowe** operatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [nowe i delete — operatory](../cpp/new-and-delete-operators.md)