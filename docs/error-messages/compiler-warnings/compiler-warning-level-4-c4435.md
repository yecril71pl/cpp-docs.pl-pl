---
title: Kompilator ostrzeżenie (poziom 4) C4435
ms.date: 11/04/2016
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
ms.openlocfilehash: 43c13c484d6e9accee7c4d2c58b72a4539a75c4c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391481"
---
# <a name="compiler-warning-level-4-c4435"></a>Kompilator ostrzeżenie (poziom 4) C4435

'klasa1': Układ obiektu pod/vd2 zmieni się ze względu na wirtualną klasę podstawową 'klasa2'

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

## <a name="see-also"></a>Zobacz także

[vtordisp](../../preprocessor/vtordisp.md)<br/>
[/vd (Wyłącz przemieszczanie konstrukcji)](../../build/reference/vd-disable-construction-displacements.md)