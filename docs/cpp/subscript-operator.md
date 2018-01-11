---
title: 'Operator indeksu dolnego: | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '[]'
dev_langs: C++
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1fbcb3657af276cdfc9aa05d461c090b76f6de0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="subscript-operator"></a>Operator indeksu dolnego:
## <a name="syntax"></a>Składnia  
  
```  
  
postfix-expression [ expression ]  
```  
  
## <a name="remarks"></a>Uwagi  
 Operatory przyrostka wyrażenia (która również może być wyrażenie podstawowego) następuje operator indeksu dolnego **[**, określa indeksowanie tablicy.  
  
 Informacje dotyczące zarządzanych tablic, zobacz [tablice](../windows/arrays-cpp-component-extensions.md).  
  
 Zazwyczaj reprezentowany przez wartość *wyrażenie przyrostek* jest wartość wskaźnika, na przykład identyfikator tablicy i *wyrażenie* jest wartością całkowitą (w tym typy wyliczane). Wszystko jest jednak wymagana Składnia tego jedno z wyrażeń jest typu wskaźnika i innych być typu całkowitego. W związku z tym może być wartością całkowitą w *przyrostek wyrażenie* pozycji i wartości wskaźnika, które mogą być w nawiasach w *wyrażenie* lub pozycji indeksu. Rozważmy następujący fragment kodu:  
  
```  
int nArray[5] = { 0, 1, 2, 3, 4 };  
cout << nArray[2] << endl;            // prints "2"  
cout << 2[nArray] << endl;            // prints "2"  
```  
  
 W powyższym przykładzie wyrażenie `nArray[2]` jest taka sama jak `2[nArray]`. Przyczyną jest to, że wynik wyrażenia indeksu dolnego *e1***[** *e2* **]** jest określany przez:  
  
 **\*((** *e2* **)**  *+*  **(***e1***))**  
  
 Adres przekazanej przez wyrażenie, które nie jest *e2* bajtów z adresu *e1*. Zamiast adresu jest skalowana umożliwiające uzyskanie następny obiekt w tablicy *e2*. Na przykład:  
  
```  
double aDbl[2];  
```  
  
 Adresy `aDb[0]` i `aDb[1]` są od siebie 8 bajtów — rozmiar obiektu typu **podwójne**. Ta skalowania zgodnie z typem obiektu odbywają się automatycznie za pomocą języka C++ i jest zdefiniowany w [operatory dodatku](../cpp/additive-operators-plus-and.md) gdzie omówiono Dodawanie i odejmowanie argumentów operacji typu wskaźnika.  
  
 Wyrażenie indeksu dolnego może mieć wiele indeksów dolnych, jak pokazano poniżej:  
  
 *wyrażenie1* **[***wyrażenie2***] [***expression3***]**...  
  
 Wyrażenia indeksu dolnego są skojarzone od lewej do prawej. Po lewej stronie wyrażenia indeksu *wyrażenie1***[***wyrażenie2***]**, jest szacowana jako pierwsza. Adres, który jest wynikiem Dodawanie *wyrażenie1* i *wyrażenie2* formularzy wyrażenia wskaźnika; następnie *expression3* zostanie dodany do tego wyrażenia wskaźnika do utworzenia nowego wyrażenia wskaźnika, i tak dalej, aż ostatniego wyrażenia indeksu został dodany. Operator pośredni (**\***) są stosowane po ostatnim jako wyrażenie jest obliczane, chyba że wartość wskaźnika końcowe adresy typem tablicy.  
  
 Wyrażenia z wielu indeksów dolnych odwoływać się do elementów tablic wielowymiarowych. Tablica wielowymiarowa jest tablicą, której elementy są tablicami. Na przykład, pierwszy element tablicy trójwymiarowej jest tablicą z dwoma wymiarami. W poniższym przykładzie deklaruje i inicjuje proste tablicą dwuwymiarową znaków:  
  
```  
// expre_Subscript_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
#define MAX_ROWS 2  
#define MAX_COLS 2  
  
int main() {  
   char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };  
   for ( int i = 0; i < MAX_ROWS; i++ )  
      for ( int j = 0; j < MAX_COLS; j++ )  
         cout << c[ i ][ j ] << endl;  
}  
```  
  
## <a name="positive-and-negative-subscripts"></a>Dodatnie i ujemne indeksy dolne  
 Pierwszy element tablicy jest element 0. Zakres tablicy C++ jest z *tablicy*[0] do *tablicy*[*rozmiar* - 1]. Dodatnie i ujemne indeksy dolne obsługuje jednak C++. Ujemne indeksy dolne muszą mieścić się w granicach tablicy; Jeśli nie, wyniki są nieprzewidywalne. Poniższy kod przedstawia tablicy dodatnie i ujemne indeksy dolne:  
  
```  
#include <iostream>  
using namespace std;  
  
int main() {  
    int intArray[1024];  
    for (int i = 0, j = 0; i < 1024; i++)  
    {  
        intArray[i] = j++;  
    }  
  
    cout << intArray[512] << endl;// 512  
  
    int *midArray = &intArray[512];  // pointer to the middle of the array  
  
    cout << midArray[-256] << endl;   // 256  
  
    cout << intArray[-256] << endl; // unpredictable  
}  
```  
  
 Ujemna indeks w wierszu lasta może spowodować błędów czasu wykonywania, ponieważ wskazuje adres niższy 256 bajtów w pamięci, niż pochodzenia tablicy. Wskaźnik `midArray` został zainicjowany w środku `intArray`; w związku z tym jest możliwe użycie obu indeksy tablicy dodatnie i ujemne. Błędy indeks dolny tablicy nie generują błędy kompilacji, ale dają one nieoczekiwane wyniki.  
  
 Operator indeksu dolnego jest przemienne. W związku z tym wyrażenia *tablicy*[*indeksu*] i *tablicy*[*tablicy*] zapewniona jest równoważne tak długo, jak indeks dolny operator nie jest przeciążony (zobacz [przeciążone operatory](../cpp/operator-overloading.md)). Pierwszy formularz jest najbardziej typowych praktyk kodowania, ale albo działa.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia przyrostków](../cpp/postfix-expressions.md)   
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Tablice](../cpp/arrays-cpp.md)   
 [Tablice jednowymiarowe](../c-language/one-dimensional-arrays.md)   
 [Tablice wielowymiarowe](../c-language/multidimensional-arrays-c.md)