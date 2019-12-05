---
title: Ostrzeżenie kompilatora (poziom 4) C4435
ms.date: 11/04/2016
f1_keywords:
- C4435
helpviewer_keywords:
- C4435
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
ms.openlocfilehash: 0ff545d3de3ef173cdbfd99d7714890e8631ce7a
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810661"
---
# <a name="compiler-warning-level-4-c4435"></a>Ostrzeżenie kompilatora (poziom 4) C4435

'klasa1': Układ obiektu pod /vd2 zmieni się ze względu na wirtualną klasę podstawową 'klasa2'

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

W obszarze domyślna opcja kompilacji elementu/vd1 Klasa pochodna nie ma pola `vtordisp` dla wskazanej bazy wirtualnej.  Jeśli/VD2 zmieni lub `#pragma vtordisp(2)` obowiązuje, `vtordisp` pole będzie obecne, zmieniając układ obiektu.  Może to prowadzić do problemów ze zgodnością binarną, jeśli korzystanie z modułów jest kompilowane z różnymi ustawieniami `vtordisp`.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4435.

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