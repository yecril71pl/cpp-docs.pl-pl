---
title: Kompilator ostrzeżenie (poziom 4) C4435
ms.date: 11/04/2016
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
ms.openlocfilehash: 7db1d483f571289c5b890c223ba1e59ba3d1f41e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572331"
---
# <a name="compiler-warning-level-4-c4435"></a>Kompilator ostrzeżenie (poziom 4) C4435

'klasa1': Układ obiektu pod /vd2 zmieni się ze względu na wirtualną klasę podstawową 'klasa2'

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

W domyślnym skompilować opcji/vd1 i Klasa pochodna nie jest objęta `vtordisp` pole wskazany bazy wirtualnej.  Jeśli/vd2 lub `#pragma vtordisp(2)` – `vtordisp` pola będą obecne, zmieniając układ obiektu.  Może to prowadzić do problemów ze zgodnością binarne, jeśli moduły interakcje są kompilowane z różnymi `vtordisp` ustawienia.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4435.

```cpp
// C4435.cpp
// compile with: /c /W4
#pragma warning(default : 4435)
class A
{
public:
    virtual ~A() {}
};

class B : public virtual A  // C4435
{};
```

## <a name="see-also"></a>Zobacz też

[vtordisp](../../preprocessor/vtordisp.md)<br/>
[/vd (Wyłącz przemieszczanie konstrukcji)](../../build/reference/vd-disable-construction-displacements.md)