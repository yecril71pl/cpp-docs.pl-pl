---
title: Kompilator ostrzeżenie (poziom 4) C4437 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 11d234f7f264f051042ae99900875b8e570fa66a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118651"
---
# <a name="compiler-warning-level-4-c4437"></a>Kompilator ostrzeżenie (poziom 4) C4437

dynamic_cast z podstawowej wirtualnej 'klasa1' na 'klasa2' może zakończyć się niepowodzeniem w niektórych kontekstach kompilacji z opcją/vd2 lub zdefiniować 'klasa2' przy użyciu #pragma vtordisp(2) w efekcie

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Kompilator napotkał `dynamic_cast` operację, podając następujące właściwości.

- Rzutowanie jest ze wskaźnika do klasy bazowej na wskaźnik klasy pochodnej.

- Klasa pochodna dziedziczy praktycznie klasy bazowej.

- Klasa pochodna nie ma `vtordisp` pole bazy wirtualnej.

- Rzutowanie nie zostanie znaleziony w Konstruktor lub destruktor klasy pochodnej lub niektóre klasy, która dalsze dziedziczy z klasy pochodnej (ostrzeżenie w przeciwnym razie, kompilatora, który pojawi się C4436).

To ostrzeżenie wskazuje, że `dynamic_cast` nie może działać prawidłowo, jeśli jest zasilany z częściowo skonstruowanym obiektem.  Ta sytuacja występuje, gdy otaczającej funkcja jest wywoływana z konstruktora lub destruktora klasy, która dziedziczy z klasy pochodnej, która nosi nazwę ostrzeżenie.  Jeśli klasa pochodna, która nosi nazwę ostrzeżenie nigdy nie jest dalsze pochodzi, lub funkcji otaczającej nie jest wywoływany podczas obiektu utworzenia lub zniszczenia, można zignorować to ostrzeżenie.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4437 i demonstruje problem dotyczący generowania kodu, która wynika z brakujący `vtordisp` pola.

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

[Operator dynamic_cast](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[Ostrzeżenie kompilatora (poziom 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)