---
title: Kompilatora (poziom 1) ostrzeżenie C4436 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1da06a329a9c0bdfcff6877ce69c8e3672619bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4436"></a>Kompilator C4436 ostrzegawcze (poziom 1)
dynamic_cast z wirtualnej podstawowej "class1" do "class2" w konstruktorze lub destruktorze może zakończyć się niepowodzeniem z częściowo skonstruowanym obiektem kompilacji z opcją/vd2 lub zdefiniować "class2" z #pragma vtordisp(2) w celu  
  
 Kompilator napotkał `dynamic_cast` operacji o następującej charakterystyce.  
  
-   Rzutowanie jest ze wskaźnika klasy podstawowej na wskaźnik klasy pochodnej.  
  
-   Klasa pochodna dziedziczy praktycznie klasy podstawowej.  
  
-   Klasa pochodna nie ma `vtordisp` dla wirtualnej podstawy pole.  
  
-   Rzutowanie znajduje się w konstruktorze lub destruktorze klasy pochodnej lub niektóre klasy, która dalsze dziedziczy z klasy pochodnej.  
  
 Ostrzeżenie wskazuje `dynamic_cast` nie może działać prawidłowo, jeśli działa na częściowo skonstruowanym obiektem.  Ma to miejsce, jeśli działa pochodnej konstruktora/destruktora dla obiektu podrzędnego niektóre dodatkowe pochodnej obiektu.  Jeśli klasa pochodna o nazwie w ostrzeżeniu nigdy nie jest dalsze pochodnych, to ostrzeżenie można zignorować.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4436 i prezentuje problem generowania kodu, który wynika z brakujący `vtordisp` pola.  
  
```cpp  
// C4436.cpp  
// To see the warning and runtime assert, compile with: /W1  
// To eliminate the warning and assert, compile with: /W1 /vd2  
//       or compile with: /W1 /DFIX  
#include <cassert>  
  
struct A  
{  
public:  
    virtual ~A() {}  
};  
  
#if defined(FIX)  
#pragma vtordisp(push, 2)  
#endif  
struct B : virtual A  
{  
    B()  
    {  
        A* a = static_cast<A*>(this);  
        B* b = dynamic_cast<B*>(a);     // C4436  
        assert(this == b);              // assert unless compiled with /vd2  
    }  
};  
#if defined(FIX)  
#pragma vtordisp(pop)  
#endif  
  
struct C : B  
{  
    int i;  
};  
  
int main()  
{  
    C c;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operator dynamic_cast](../../cpp/dynamic-cast-operator.md)   
 [vtordisp](../../preprocessor/vtordisp.md)   
 [Ostrzeżenie kompilatora (poziom 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)