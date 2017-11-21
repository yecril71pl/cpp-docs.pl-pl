---
title: Klasy magazynu (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- thread_local_cpp
- external_cpp
- static_cpp
dev_langs: C++
helpviewer_keywords: storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3830f91683399eba4784b5348ca252e9caa22d57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="storage-classes-c"></a>Klasy magazynu (C++)  
  
A *Klasa magazynu* w kontekście C++ deklaracje zmiennej to Specyfikator typu określająca lokalizację okres istnienia, powiązania i pamięci obiektów. Dany obiekt może mieć tylko jedną klasę magazynu. Zmienne zdefiniowane w bloku ma automatyczne magazynu, chyba że określono inaczej, za pomocą `extern`, `static`, lub `thread_local` specyfikatory. Automatyczne obiekty i zmienne mają bez powiązania; nie są one widoczne dla kodu poza blokiem.  
  
**Uwagi**  
  
1.  [Modyfikowalną](../cpp/mutable-data-members-cpp.md) — słowo kluczowe może zostać uznany za Specyfikator klasy magazynu. Jednak jest ono dostępne tylko na liście elementów członkowskich definicji klasy.  
  
2.  **Visual C++ 2010 lub nowszy:** `auto` — słowo kluczowe nie jest już specyfikatora klasy magazynu języka C++ i `register` — słowo kluczowe jest przestarzały. **Visual Studio 2017 wersji 15.3 i nowszych:** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): `register` — słowo kluczowe nie jest już klasę magazynu obsługiwane. Słowo kluczowe jest nadal zarezerwowane w standardzie do użytku w przyszłości. 
```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="in-this-section"></a>W tej sekcji:
  
-   [statyczne](#static)  
-   [extern](#extern)  
-   [Element thread_local](#thread_local)

<a name="static"></a>
  
## <a name="static"></a>static  
  
`static` — Słowo kluczowe może służyć do deklarowania zmiennych i funkcji w zakresie globalnym, zakresie przestrzeni nazw i klasy zakres. Zmienne statyczne mogą być deklarowane również w zakresie lokalnym.  
  
Czas trwania statycznych oznacza, że obiektu lub zmienna jest przydzielany przy program uruchamia i jest deallocated, gdy program kończy się. Połączenie zewnętrzne oznacza, że nazwa zmiennej jest widoczny spoza pliku, w którym zmienna została zadeklarowana. Z drugiej strony zewnętrzne oznacza, że nazwa nie jest widoczna poza plikiem, w którym zmienna została zadeklarowana. Domyślnie obiektu lub zmienna, która jest zdefiniowana w globalnej przestrzeni nazw ma czas trwania statyczne i połączenie zewnętrzne. `static` w następujących sytuacjach można używać słowa kluczowego.  
  
1.  Gdy zadeklarować zmiennej lub funkcji w zakresie pliku (globalne i/lub zakresie przestrzeni nazw), `static` — słowo kluczowe Określa, że zmienną lub funkcję ma połączenie zewnętrzne. Deklaracja zmiennej zmienna ma czas trwania statyczne i kompilator inicjuje go na 0, chyba że Określ inną wartość.  
  
2.  Deklaracja zmiennej w przypadku funkcji `static` — słowo kluczowe Określa, że zmienna zachowuje stanu między wywołań tej funkcji.  
  
3.  Element członkowski danych w deklaracji klasy w deklaracji `static` — słowo kluczowe Określa, że jedna kopia elementu członkowskiego jest współużytkowana przez wszystkie wystąpienia klasy. Statycznego elementu członkowskiego danych musi być zdefiniowana w zakresie pliku. Element członkowski danych całkowity, który został zadeklarowany jako `const static` może mieć inicjatora.  
  
4.  Deklaracja funkcji członkowskiej w deklaracji klasy `static` — słowo kluczowe Określa, że funkcja jest współużytkowana przez wszystkie wystąpienia klasy. Statycznej funkcji członkowskiej nie można uzyskać dostępu do elementu członkowskiego wystąpienia, ponieważ funkcja ma niejawne `this` wskaźnika. Aby uzyskać dostęp do elementu członkowskiego wystąpienia, należy zadeklarować funkcji z parametrem, który jest wystąpieniem wskaźnik lub odwołanie.  
  
5.  Nie można zadeklarować elementów członkowskich Unii jako statyczny. Jednak zadeklarowany globalnie anonimowa Unia musi być jawnie zadeklarowana `static`.  
  
W tym przykładzie pokazano, jak zmiennej zadeklarowanej `static` w funkcji zachowuje stanu między wywołań tej funkcji.  
  
```cpp  
// static1.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
void showstat( int curr ) {  
   static int nStatic;    // Value of nStatic is retained  
                          // between each function call  
   nStatic += curr;  
   cout << "nStatic is " << nStatic << endl;  
}  
  
int main() {  
   for ( int i = 0; i < 5; i++ )  
      showstat( i );  
}  
```  
  
```Output  
nStatic is 0  
nStatic is 1  
nStatic is 3  
nStatic is 6  
nStatic is 10  
```  
  
W tym przykładzie pokazano sposób użycia `static` w klasie.  
  
```cpp  
// static2.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class CMyClass {  
public:  
   static int m_i;  
};  
  
int CMyClass::m_i = 0;  
CMyClass myObject1;  
CMyClass myObject2;  
  
int main() {  
   cout << myObject1.m_i << endl;  
   cout << myObject2.m_i << endl;  
  
   myObject1.m_i = 1;  
   cout << myObject1.m_i << endl;  
   cout << myObject2.m_i << endl;  
  
   myObject2.m_i = 2;  
   cout << myObject1.m_i << endl;  
   cout << myObject2.m_i << endl;  
  
   CMyClass::m_i = 3;  
   cout << myObject1.m_i << endl;  
   cout << myObject2.m_i << endl;  
}  
```  
  
```Output  
0  
0  
1  
1  
2  
2  
3  
3  
```  
  
W tym przykładzie pokazano zmienna lokalna zadeklarowana `static` w funkcji członkowskiej. Zmienna statyczna jest dostępny dla całego programu; wszystkie wystąpienia typu współużytkują tę samą kopię zmienna statyczna.  
  
```cpp  
// static3.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
struct C {  
   void Test(int value) {  
      static int var = 0;  
      if (var == value)   
         cout << "var == value" << endl;  
      else  
         cout << "var != value" << endl;  
  
      var = value;  
   }  
};   
  
int main() {  
   C c1;  
   C c2;  
   c1.Test(100);  
   c2.Test(100);  
}  
```  
  
```Output  
var != value  
var == value  
```  
  
Począwszy od języka C ++ 11 Inicjowanie statyczne zmiennej lokalnej jest gwarancji wątkowo. Ta funkcja jest czasem nazywany *Magiczna statystykach*. Jednak w aplikacji wielowątkowych wszystkie kolejne przypisania musi być synchronizowany. Funkcja Inicjowanie statyczne wątkowo można wyłączyć za pomocą [/Zc:threadSafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) flagę w celu uniknięcia przyjmowanie zależności CRT.  
  
<a name="extern"></a>  
  
## <a name="extern"></a>extern  
  
Obiekty i zmiennych zadeklarowanych jako `extern` zadeklarować obiektu, który jest zdefiniowany w innej jednostce tłumaczenia lub w otaczającym zakresie jako mający połączenie zewnętrzne.  
  
Deklaracja `const` zmiennych o `extern` Klasa magazynu wymusza zmienna ma połączenie zewnętrzne. Inicjowanie `extern const` zmiennej jest dozwolone w jednostce tłumaczenia definiującego. Inicjowanie w jednostce tłumaczenia innych niż definiowanie jednostce tłumaczenia dać niezdefiniowane wyniki. Aby uzyskać więcej informacji, zobacz [użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)  
  
Poniższy kod przedstawia dwa `extern` deklaracje, `DefinedElsewhere` (które odwołuje się do nazwy zdefiniowany w jednostce tłumaczenia różnych) i `DefinedHere` (które odwołuje się do nazwy zdefiniowanej w otaczającym zakresie):  
  
```cpp  
// external.cpp  
// DefinedElsewhere is defined in another translation unit  
extern int DefinedElsewhere;     
int main() {  
   int DefinedHere;   
   {  
      // refers to DefinedHere in the enclosing scope  
      extern int DefinedHere;  
   }  
}  
```  
  
<a name="thread_local"></a>  
  
## <a name="threadlocal-c11"></a>Element thread_local (C ++ 11)  
  
Zmienna zadeklarowana ze `thread_local` specyfikator jest dostępna tylko w wątku, w którym została utworzona. Zmienna jest tworzony podczas wątek nie zostanie utworzona i zniszczona, gdy wątek zostanie zniszczony. Każdy wątek ma własną kopię zmiennej. W systemie Windows `thread_local` jest funkcjonalnym odpowiednikiem specyficzne dla firmy Microsoft [__declspec (wątek)](../cpp/thread.md) atrybutu.  
  
```cpp  
thread_local float f = 42.0; // Global namespace. Not implicitly static.
  
struct S // cannot be applied to type definition  
{  
    thread_local int i; // Illegal. The member must be static.  
    thread_local static char buf[10]; // OK 
};  
  
void DoSomething()  
{  
    // Apply thread_local to a local variable.
    // Implicitly "thread_local static S my_struct".
    thread_local S my_struct;  
}  
```  
  
Rzeczy do uwzględnienia o `thread_local` specyfikator:  
  
-  `thread_local` Specyfikator mogą być łączone z `static` lub `extern`.  
  
-  Możesz zastosować `thread_local` tylko do danych deklaracje i definicje; `thread_local` nie można użyć w deklaracji lub definicji funkcji.  
  
-  Korzystanie z `thread_local` może zakłócać [opóźnienia ładowania](../build/reference/linker-support-for-delay-loaded-dlls.md) biblioteki DLL importuje. 
  
-  W systemie XP `thread_local` nie może działać prawidłowo, jeśli korzysta z biblioteki DLL `thread_local` danych i jej załadowaniu dynamicznie za pośrednictwem `LoadLibrary`.  
  
-  Można określić `thread_local` tylko dla elementów danych ze statycznym okresem magazynu. Obejmuje to obiekty danych globalnych (zarówno `static` i `extern`), lokalnego obiektu statycznego i danymi statycznymi członkami klas. Wszelkie zmienna lokalna zadeklarowana `thread_local` jest niejawnie statyczny, jeśli podano inną klasę magazynu; innymi słowy, w zakresie bloku `thread_local` jest odpowiednikiem `thread_local static`. 
  
-  Należy określić `thread_local` dla deklaracji i definicji obiektu lokalnego wątku czy deklaracji i definicji występować w tym samym pliku lub oddzielnych plików.  
  
W systemie Windows `thread_local` jest funkcjonalnym odpowiednikiem [__declspec(thread)](../cpp/thread.md) z tą różnicą, że `__declspec(thread)` może odnosić się do definicji typu i jest prawidłowy w kodzie C. Jeśli to możliwe, użyj `thread_local` ponieważ jest częścią standardowej C++ i dlatego jest bardziej przenośne.  
  
##  <a name="register"></a>Rejestr  
**Visual Studio 2017 wersji 15.3 i nowszych** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): `register` — słowo kluczowe nie jest już klasę magazynu obsługiwane. Słowo kluczowe jest nadal zarezerwowane w standardzie do użytku w przyszłości. 

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Przykład: automatyczne i Inicjowanie statyczne  
  
Lokalnego automatyczne obiektu lub zmienna jest zainicjowana za każdym razem, gdy przepływu sterowania osiągnie jego definicji. Lokalnego obiektu statycznego lub zmiennej został zainicjowany po raz pierwszy przepływu sterowania osiągnie jego definicji.  
  
Poniższy przykład, który definiuje klasę, która rejestruje inicjowania i niszczenie obiektów, a następnie definiuje trzy obiekty, rozważ `I1`, `I2`, i `I3`:  
  
```cpp  
// initialization_of_objects.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string.h>  
using namespace std;  
  
// Define a class that logs initializations and destructions.  
class InitDemo {  
public:  
    InitDemo( const char *szWhat );  
    ~InitDemo();  
  
private:  
    char *szObjName;  
    size_t sizeofObjName;  
};  
  
// Constructor for class InitDemo  
InitDemo::InitDemo( const char *szWhat ) :  
    szObjName(NULL), sizeofObjName(0) {  
    if ( szWhat != 0 && strlen( szWhat ) > 0 ) {  
        // Allocate storage for szObjName, then copy  
        // initializer szWhat into szObjName, using  
        // secured CRT functions.  
        sizeofObjName = strlen( szWhat ) + 1;  
  
        szObjName = new char[ sizeofObjName ];  
        strcpy_s( szObjName, sizeofObjName, szWhat );  
  
        cout << "Initializing: " << szObjName << "\n";  
    }  
    else {  
        szObjName = 0;  
    }
}  
  
// Destructor for InitDemo  
InitDemo::~InitDemo() {  
    if( szObjName != 0 ) {  
        cout << "Destroying: " << szObjName << "\n";  
        delete szObjName;  
    }  
}  
  
// Enter main function  
int main() {  
    InitDemo I1( "Auto I1" ); {  
        cout << "In block.\n";  
        InitDemo I2( "Auto I2" );  
        static InitDemo I3( "Static I3" );  
    }  
    cout << "Exited block.\n";  
}  
```  
  
```Output  
Initializing: Auto I1  
In block.  
Initializing: Auto I2  
Initializing: Static I3  
Destroying: Auto I2  
Exited block.  
Destroying: Auto I1  
Destroying: Static I3  
```  
  
W tym przykładzie pokazano, jak i kiedy obiekty `I1`, `I2`, i `I3` są inicjowane i kiedy zostaną zniszczone.  
  
Istnieje kilka punktów, należy pamiętać o programie:  
  
- Najpierw `I1` i `I2` zostaną zniszczone automatycznie, gdy przepływu sterowania opuszcza blok, w którym są zdefiniowane.  
  
- Po drugie w języku C++ go nie jest konieczne deklarować obiektów lub zmienne na początku bloku. Ponadto te obiekty są inicjowane tylko wtedy, gdy przepływu sterowania osiągnie ich definicje. (`I2` i `I3` przedstawiono przykłady takich definicji.) Przedstawia dane wyjściowe dokładnie, gdy są one inicjowane.  
  
- Na koniec statycznych zmiennych lokalnych, takich jak `I3` zachowują swoje wartości w czasie trwania programu, ale są zniszczona, ponieważ program zakończy.  
  
## <a name="see-also"></a>Zobacz też  
  
 [Deklaracje i definicje](../cpp/declarations-and-definitions-cpp.md)
