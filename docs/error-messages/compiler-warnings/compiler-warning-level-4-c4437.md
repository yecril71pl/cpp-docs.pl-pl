---
title: Kompilatora (poziom 4) ostrzeżenie C4437 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 748ba39d9c22a4071307b8df075eab233f3cfbb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298330"
---
# <a name="compiler-warning-level-4-c4437"></a>Kompilator C4437 ostrzegawcze (poziom 4)
dynamic_cast z wirtualnej podstawowej "class1" do "class2" może zakończyć się niepowodzeniem w niektórych kontekstach kompilacji z opcją/vd2 lub zdefiniować "class2" z #pragma vtordisp(2) w celu  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Kompilator napotkał `dynamic_cast` operacji o następującej charakterystyce.  
  
-   Rzutowanie jest ze wskaźnika klasy podstawowej na wskaźnik klasy pochodnej.  
  
-   Klasa pochodna dziedziczy praktycznie klasy podstawowej.  
  
-   Klasa pochodna nie ma `vtordisp` dla wirtualnej podstawy pole.  
  
-   Rzutowanie nie znaleziono konstruktora lub destruktora klasy pochodnej lub niektóre klasy, która dalsze dziedziczy z klasy pochodnej (ostrzeżenie w przeciwnym razie kompilatora, które zostaną wystawione C4436).  
  
 Ostrzeżenie wskazuje, że `dynamic_cast` nie może działać prawidłowo, jeśli działa na częściowo skonstruowanym obiektem.  Ta sytuacja występuje, gdy funkcji otaczającej jest wywoływana z konstruktora lub destruktora klasy, która dziedziczy z klasy pochodnej, która jest nazywane ostrzeżenia.  Jeśli klasa pochodna, która jest nazywane ostrzeżenia nigdy nie jest dalsze pochodzi, lub funkcji otaczającej nie jest wywoływana podczas konstruowania obiektu lub zniszczenia, można zignorować to ostrzeżenie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4437 i prezentuje problem generowania kodu, który wynika z brakujący `vtordisp` pola.  
  
```cpp  
// C4437.cpp  
// To see the warning and runtime assert, compile with: /W4  
// To eliminate the warning and assert, compile with: /W4 /vd2  
//       or compile with: /W4 /DFIX  
#pragma warning(default : 4437)  
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
        func();  
    }  
  
    void func()  
    {  
        A* a = static_cast<A*>(this);  
        B* b = dynamic_cast<B*>(a);     // C4437  
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
 [Ostrzeżenie kompilatora (poziom 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)