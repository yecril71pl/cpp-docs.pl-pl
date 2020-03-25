---
title: Błąd narzędzi konsolidatora LNK1313
ms.date: 11/04/2016
f1_keywords:
- LNK1313
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
ms.openlocfilehash: a2314f160dc6add45547082c7804ec5e2c8f2349
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194866"
---
# <a name="linker-tools-error-lnk1313"></a>Błąd narzędzi konsolidatora LNK1313

> Wykryto IJW/moduł macierzysty; nie można połączyć z czystymi modułami

## <a name="remarks"></a>Uwagi

Bieżąca wersja programu Visual C++ nie obsługuje łączenia natywnych lub mieszanych plików. obj z atrybutami. obj, które zostały skompilowane z **/CLR: Pure**.

**/CLR: Pure** kompilator Option jest przestarzały w programie visual Studio 2015 i nieobsługiwany w programie visual Studio 2017.

## <a name="example"></a>Przykład

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

## <a name="example"></a>Przykład

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

## <a name="example"></a>Przykład

Poniższy przykład generuje LNK1313.

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```
