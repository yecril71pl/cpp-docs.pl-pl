---
title: static_cast Operator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- static_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3913937d9099304c478404c4c55a09fa54392785
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="staticcast-operator"></a>Operator static_cast
Konwertuje *wyrażenie* do typu *identyfikator typu* oparte tylko na typy, które znajdują się w wyrażeniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
static_cast <type-id> ( expression )   
```  
  
## <a name="remarks"></a>Uwagi  
 W standardowym C++ nie jest wykonywane żadne sprawdzenie typu w czasie wykonywania, aby pomóc w zapewnieniu bezpieczeństwa konwersji. W C++/CX, wykonywane są sprawdzenia czasu kompilacji i czasu wykonywania. Aby uzyskać więcej informacji, zobacz [rzutowanie](casting.md).  
  
 `static_cast` Operator może służyć do operacji, takich jak konwersja wskaźnika do klasy podstawowej na wskaźnik do klasy pochodnej. Takie konwersje nie zawsze są bezpieczne.  
  
 Ogólnie rzecz biorąc użyj `static_cast` niektórych typów danych umożliwia konwertowanie typów danych liczbowych, takich jak typy wyliczeniowe wskazówki lub wskazówki elementów przestawnych, i są zaangażowane w konwersji. `static_cast`Konwersje nie są bezpieczne, jak i `dynamic_cast` konwersji, ponieważ `static_cast` sprawdza nie typu run-time, podczas gdy `dynamic_cast` jest. A `dynamic_cast` do wskaźnika niejednoznaczne zakończy się niepowodzeniem, gdy `static_cast` zwraca tak, jakby nie był nieprawidłowy; może to być niebezpieczne. Mimo że `dynamic_cast` konwersje są bezpieczniejsze, `dynamic_cast` tylko do działania na wskaźniki lub odniesienia i wyboru typu run-time jest zmniejszenie. Aby uzyskać więcej informacji, zobacz [dynamic_cast Operator](../cpp/dynamic-cast-operator.md).  
  
 W następującym przykładzie, wiersz `D* pd2 = static_cast<D*>(pb);` nie jest bezpieczne ponieważ `D` mogą mieć pól i metod, które nie znajdują się w `B`. Jednak wiersza `B* pb2 = static_cast<B*>(pd);` jest bezpieczne konwersji, ponieważ `D` zawsze zawiera wszystkie `B`.  
  
```  
// static_cast_Operator.cpp  
// compile with: /LD  
class B {};  
  
class D : public B {};  
  
void f(B* pb, D* pd) {  
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields  
                                   // and methods that are not in B.  
  
   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always  
                                   // contains all of B.  
}  
```  
  
 Contrast do [dynamic_cast](../cpp/dynamic-cast-operator.md), bez sprawdzania czasu wykonywania jest podejmowana `static_cast` konwersja `pb`. Obiekt wskazywany przez `pb` nie może być obiektem typu `D`, w którym to przypadku użycia `*pd2` może być Fatalne. Na przykład wywołanie funkcji, które jest członkiem `D` klasy, ale nie `B` klasy, może spowodować naruszenie zasad dostępu.  
  
 `dynamic_cast` i `static_cast` operatory wskaźnika w całej hierarchii klas. Jednak `static_cast` wyłącznie zależy od informacji dostępnych w instrukcji rzutowania i dlatego może być niebezpieczne. Na przykład:  
  
```  
// static_cast_Operator_2.cpp  
// compile with: /LD /GR  
class B {  
public:  
   virtual void Test(){}  
};  
class D : public B {};  
  
void f(B* pb) {  
   D* pd1 = dynamic_cast<D*>(pb);  
   D* pd2 = static_cast<D*>(pb);  
}  
```  
  
 Jeśli `pb` naprawdę wskazuje na obiekt typu `D`, następnie `pd1` i `pd2` pobierze tę samą wartość. Zostanie również otrzymują tę samą wartość Jeśli `pb == 0`.  
  
 Jeśli `pb` wskazuje na obiekt typu `B` , a nie do pełnej `D` klasy, następnie `dynamic_cast` wiedzą, aby zwracać zera. Jednak `static_cast` zależy od programisty potwierdzenia które `pb` wskazuje na obiekt typu `D` i po prostu zwraca wskaźnik do którego powinien `D` obiektu.  
  
 W rezultacie `static_cast` możliwość odwrotność niejawne konwersje, w którym to przypadku wyniki są niezdefiniowane. Zostanie pozostawiony dla programisty do sprawdzenia, czy wyniki `static_cast` konwersji są bezpieczne.  
  
 To działanie dotyczy także innych typów niż typy klas. Na przykład `static_cast` może służyć do przekonwertowania z int do `char`. Jednak powstałe w ten sposób `char` może nie mieć wystarczającej liczby bitów, aby pomieścić całą `int` wartość. Ponownie, jest pozostawiany bez dla programisty do sprawdzenia, czy wyniki `static_cast` konwersji są bezpieczne.  
  
 `static_cast` Operator można również wykonać niejawnej konwersji, w tym konwersje standardowe i konwersje zdefiniowane przez użytkownika. Na przykład:  
  
```  
// static_cast_Operator_3.cpp  
// compile with: /LD /GR  
typedef unsigned char BYTE;  
  
void f() {  
   char ch;  
   int i = 65;  
   float f = 2.5;  
   double dbl;  
  
   ch = static_cast<char>(i);   // int to char  
   dbl = static_cast<double>(f);   // float to double  
   i = static_cast<BYTE>(ch);  
}  
```  
  
 `static_cast` Operator można jawnie przekonwertować na typ wyliczeniowy wartością całkowitą. Jeśli wartość typu całkowitego nie wchodzi w zakres wartości wyliczenia, wynikowa wartość wyliczenia jest niezdefiniowana.  
  
 `static_cast` Operator konwertuje wartość wskaźnika o wartości null na wartość pustego wskaźnika typu docelowego.  
  
 Dowolne wyrażenie można jawnie przekonwertować na typ void przez `static_cast` operatora. Docelowy typ void można opcjonalnie dołączyć `const`, `volatile`, lub `__unaligned` atrybutu.  
  
 `static_cast` Operatora nie można rzutować optymalizacji `const`, `volatile`, lub `__unaligned` atrybutów. Zobacz [const_cast Operator](../cpp/const-cast-operator.md) informacji o usuwaniu te atrybuty.  
  
 Z powodu ryzyka wykonania niezaznaczone rzutowania na górze przemieszczenie moduł GC, korzystanie z `static_cast` tylko należy w kodu wrażliwego na wydajność, gdy będzie działać prawidłowo. Jeśli musisz użyć `static_cast` w trybie wersji zastąpić go z [safe_cast](../windows/safe-cast-cpp-component-extensions.md) w kompilacjach debugowania, aby zapewnić powodzenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory rzutowania](../cpp/casting-operators.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)