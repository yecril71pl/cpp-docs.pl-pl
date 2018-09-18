---
title: Kompilator ostrzeżenie (poziom 4) C4435 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c9a69e0d899e1a79c1d91b7c18c0eacaf66d32a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027300"
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