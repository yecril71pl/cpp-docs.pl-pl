---
title: Ostrzeżenie kompilatora (poziom 4) C4437
ms.date: 11/04/2016
f1_keywords:
- C4437
helpviewer_keywords:
- C4437
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
ms.openlocfilehash: 949cd208d8c4f86afb1ef0a36db8483de4aac232
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214389"
---
# <a name="compiler-warning-level-4-c4437"></a>Ostrzeżenie kompilatora (poziom 4) C4437

dynamic_cast z wirtualnej bazy "Class1" do "'klasa" może zakończyć się niepowodzeniem w niektórych kontekstach kompilowanych przy użyciu/VD2 zmieni lub Zdefiniuj "'klasa" z #pragma vtordisp (2) w efekcie

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Kompilator napotkał **`dynamic_cast`** operację o następującej charakterystyce.

- Rzutowanie pochodzi ze wskaźnika klasy bazowej do wskaźnika klasy pochodnej.

- Klasa pochodna praktycznie dziedziczy klasę bazową.

- Klasa pochodna nie ma `vtordisp` pola dla bazy wirtualnej.

- Rzutowanie nie znajduje się w konstruktorze lub destruktorze klasy pochodnej lub Klasa, która dodatkowo dziedziczy z klasy pochodnej (w przeciwnym razie zostanie wygenerowane Ostrzeżenie kompilatora C4436).

Ostrzeżenie wskazuje, że **`dynamic_cast`** może nie działać poprawnie, jeśli działa na obiekcie częściowo skonstruowanym.  Ta sytuacja występuje, gdy funkcja otaczająca jest wywoływana z konstruktora lub destruktora klasy, która dziedziczy klasę pochodną o nazwie w ostrzeżeniu.  Jeśli klasa pochodna o nazwie w ostrzeżeniu nigdy nie będzie bardziej pochodna lub otaczająca funkcja nie jest wywoływana podczas konstruowania lub niszczenia obiektu, ostrzeżenie można zignorować.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4437 i demonstruje problem z generowaniem kodu, który wynika z brakujących `vtordisp` pól.

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

## <a name="see-also"></a>Zobacz także

[Operator dynamic_cast](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[Ostrzeżenie kompilatora (poziom 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)
