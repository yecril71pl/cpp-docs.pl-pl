---
title: Ostrzeżenie kompilatora (poziom 1) C4436
ms.date: 11/04/2016
f1_keywords:
- C4436
helpviewer_keywords:
- C4436
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
ms.openlocfilehash: 7772d835e398ade24b452f2b816afeae09659bf7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162390"
---
# <a name="compiler-warning-level-1-c4436"></a>Ostrzeżenie kompilatora (poziom 1) C4436

dynamic_cast z wirtualnej bazy "Class1" do "'klasa" w konstruktorze lub destruktorze może zakończyć się niepowodzeniem z zakompilowaniem częściowo skompilowanego obiektu przy użyciu/VD2 zmieni lub Zdefiniuj "'klasa" z #pragma vtordisp (2) w efekcie

Kompilator napotkał `dynamic_cast` operacji z następującymi charakterystykami.

- Rzutowanie pochodzi ze wskaźnika klasy bazowej do wskaźnika klasy pochodnej.

- Klasa pochodna praktycznie dziedziczy klasę bazową.

- Klasa pochodna nie ma pola `vtordisp` dla bazy wirtualnej.

- Rzutowanie jest dostępne w konstruktorze lub destruktorze klasy pochodnej lub pewnej klasie, która dodatkowo dziedziczy z klasy pochodnej.

Ostrzeżenie wskazuje, że `dynamic_cast` może nie działać prawidłowo, jeśli działa na obiekt częściowo skonstruowany.  Dzieje się tak, jeśli Konstruktor pochodny/destruktor działa na obiekcie podrzędnym innego obiektu pochodnego.  Jeśli klasa pochodna o nazwie w ostrzeżeniu nigdy nie będzie bardziej pochodna, ostrzeżenie można zignorować.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4436 i demonstruje problem z generowaniem kodu, który powstał z brakujących pola `vtordisp`.

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
