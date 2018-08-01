---
title: Różnice w obsłudze wyjątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9c17c0abbd8286d05423ac52abc2e2109253f6d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404626"
---
# <a name="exception-handling-differences"></a>Różnice w obsłudze wyjątków
Główna różnica pomiędzy obsługą wyjątków strukturalnych i obsługa wyjątków języka C++ jest, że model operuje na różnych typach obsługi wyjątków C++, podczas C strukturalny model obsługi wyjątków zajmuje się wyjątkami jednego typu — w szczególności  **unsigned int**. Oznacza to, że wyjątki C są identyfikowane przez nieoznaczoną wartość całkowitą, natomiast wyjątki C++ są identyfikowane przez typ danych. Gdy tworzony jest wyjątek w C, każdy możliwy program obsługi wykonuje filtr, który sprawdza kontekst wyjątków C i określa, czy należy zaakceptować wyjątek, przekazać go do innego programu obsługi lub zignorować. Gdy wyjątek jest zgłaszany w języku C++, może być dowolnego typu.  
  
 Druga różnica polega na tym, że model obsługi wyjątków strukturalnych C jest określony, jako „asynchroniczny” ponieważ wyjątki występują pobocznie do normalnego przepływu sterowania. Mechanizm obsługi wyjątków C++ jest całkowicie „synchroniczny”, co oznacza, że wyjątki występują tylko wtedy kiedy są zgłaszane.  
  
 Jeśli wyjątek C jest inicjowany w programie C++, mogą być obsługiwane przez program obsługi wyjątków strukturalnych z skojarzonym filtrem lub przez C++ **catch** obsługi, która kwota jest dynamicznie bliżej kontekstu wyjątku. Na przykład, poniższy program w języku C++ zgłasza wyjątek C wewnątrz C++ **spróbuj** kontekstu:  
  
## <a name="example"></a>Przykład  
  
```cpp 
// exceptions_Exception_Handling_Differences.cpp  
// compile with: /EHa  
#include <iostream>  
  
using namespace std;  
void SEHFunc( void );  
  
int main() {  
   try {  
      SEHFunc();  
   }  
   catch( ... ) {  
      cout << "Caught a C exception."<< endl;  
   }  
}  
  
void SEHFunc() {  
   __try {  
      int x, y = 0;  
      x = 5 / y;  
   }  
   __finally {  
      cout << "In finally." << endl;  
   }  
}  
```  
  
```Output  
In finally.  
Caught a C exception.  
```  
  
##  <a name="_core_c_exception_wrapper_class"></a> Klasa otoki dla wyjątków C  
 W prostym przykładzie jak wyżej, wyjątek C może zostać przechwycony tylko wielokropkiem (**...** ) **catch** programu obsługi. Brak informacji na temat typu lub rodzaju wyjątku jest przekazywany do modułu obsługi. Chociaż ta metoda zadziała, to w niektórych przypadkach, może być konieczne zdefiniowanie transformacji między dwoma modelami obsługi wyjątków tak, aby każdy wyjątek C był skojarzony z konkretną klasą. W tym celu, można zdefiniować klasy „otoki” wyjątku w języku C, które mogą być używane lub dziedziczone w celu przypisania atrybutu typu określonej klasy do wyjątku języka C. W ten sposób każdy wyjątek C może być obsługiwany przez C++ **catch** obsługi bardziej niezależnie niż w poprzednim przykładzie.  
  
 Klasa otoki może mieć interfejs składający się z niektórych funkcji składowych, które określają wartość wyjątku i dostęp do rozszerzonych informacji kontekstu wyjątku dostarczonych przez model wyjątków C. Można także zdefiniować domyślny konstruktor i Konstruktor, który akceptuje **unsigned int** argument (zapewnienie podstawowej reprezentacji wyjątku C) i bitowy Konstruktor kopiujący. Oto możliwa implementacja klasy otoki wyjątku C:  
  
```cpp 
// exceptions_Exception_Handling_Differences2.cpp  
// compile with: /c  
class SE_Exception {  
private:  
   SE_Exception() {}  
   SE_Exception( SE_Exception& ) {}  
   unsigned int nSE;  
public:  
   SE_Exception( unsigned int n ) : nSE( n ) {}  
   ~SE_Exception() {}  
   unsigned int getSeNumber() {  
      return nSE;  
   }  
};  
```  
  
 Aby użyć tej klasy, należy zainstalować funkcję tłumaczenia niestandardowych wyjątków C, która jest wywoływana przez mechanizm obsługi wyjątków, każdorazowo, kiedy zgłaszany jest wyjątek w języku C. W ramach funkcji tłumaczenia, możliwe jest zgłoszenie wyjątku dowolnego typu (być może `SE_Exception` wpisać lub typ klasy pochodnej z `SE_Exception`), może zostać przechwycony przez odpowiednie języka C++ **catch** programu obsługi. Funkcja tłumaczenia może po prostu może nic nie zwracać, co oznacza, że nie obsłużyła wyjątku. Jeżeli sama funkcja tłumaczenia zgłasza wyjątek C, [zakończyć](../c-runtime-library/reference/terminate-crt.md) jest wywoływana.  
  
 Aby określić niestandardową funkcję tłumaczenia, należy wywołać [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) funkcji o nazwie funkcji tłumaczenia, jako pojedynczy argument. Napisana funkcja tłumaczenia jest wywoływana jeden raz dla każdego wywołania funkcji na stosie, które ma **spróbuj** bloków. Nie ma domyślnego tłumaczenia funkcji; Jeśli nie określisz jedna poprzez wywołanie `_set_se_translator`, wyjątek C można zastosować wyłącznie z wielokropkiem modelu **catch** programu obsługi.  
  
## <a name="example"></a>Przykład  
 Na przykład, poniższy kod instaluje niestandardową funkcję tłumaczenia i następnie zgłasza wyjątek C, który jest otoczony przez klasę `SE_Exception`:  
  
```cpp 
// exceptions_Exception_Handling_Differences3.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <eh.h>  
#include <windows.h>  
  
class SE_Exception {  
private:  
   SE_Exception() {}  
   unsigned int nSE;  
  
public:  
   SE_Exception( SE_Exception& e) : nSE(e.nSE) {}  
   SE_Exception(unsigned int n) : nSE(n) {}  
   ~SE_Exception() {}  
   unsigned int getSeNumber() { return nSE; }  
};  
  
void SEFunc() {  
   __try {  
      int x, y = 0;  
      x = 5 / y;  
    }  
    __finally {  
      printf_s( "In finally\n" );  
   }  
}  
  
void trans_func( unsigned int u, _EXCEPTION_POINTERS* pExp ) {  
   printf_s( "In trans_func.\n" );  
   throw SE_Exception( u );  
}  
  
int main() {  
   _set_se_translator( trans_func );  
    try {  
      SEFunc();  
    }  
    catch( SE_Exception e ) {  
      printf_s( "Caught a __try exception with SE_Exception.\n" );  
      printf_s( "nSE = 0x%x\n", e.getSeNumber() );  
    }  
}  
```  
  
```Output  
In trans_func.  
In finally  
Caught a __try exception with SE_Exception.  
nSE = 0xc0000094  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Połączenie wyjątków języka C (strukturalnych) i C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)