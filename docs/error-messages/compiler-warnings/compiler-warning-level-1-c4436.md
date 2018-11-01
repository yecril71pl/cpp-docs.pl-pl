---
title: Kompilator ostrzeżenie (poziom 1) C4436
ms.date: 11/04/2016
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
ms.openlocfilehash: b8f62b7556d458f285597b4ae92a4f6e15ee60c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657996"
---
# <a name="compiler-warning-level-1-c4436"></a>Kompilator ostrzeżenie (poziom 1) C4436

dynamic_cast z podstawowej wirtualnej 'klasa1' na 'klasa2' w konstruktorze lub destruktorze może zakończyć się niepowodzeniem z częściowo skonstruowanym obiektem kompilacji z opcją/vd2 lub zdefiniować 'klasa2' przy użyciu #pragma vtordisp(2) w efekcie

Kompilator napotkał `dynamic_cast` operację, podając następujące właściwości.

- Rzutowanie jest ze wskaźnika do klasy bazowej na wskaźnik klasy pochodnej.

- Klasa pochodna dziedziczy praktycznie klasy bazowej.

- Klasa pochodna nie ma `vtordisp` pole bazy wirtualnej.

- Rzutowanie znajduje się w konstruktorze lub destruktor klasy pochodnej lub niektóre klasy, która dalsze dziedziczy z klasy pochodnej.

To ostrzeżenie wskazuje `dynamic_cast` nie może działać poprawnie, jeśli jest zasilany z częściowo skonstruowanym obiektem.  Tak się stanie, jeśli działa pochodnej konstruktora/destruktora w podobiekcie dalsze pochodnego obiektu.  Jeśli klasa pochodna o nazwie ostrzeżenie nigdy nie jest dalsze derived, można je zignorować.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4436 i demonstruje problem dotyczący generowania kodu, która wynika z brakujący `vtordisp` pola.

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

[Operator dynamic_cast](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[Ostrzeżenie kompilatora (poziom 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)