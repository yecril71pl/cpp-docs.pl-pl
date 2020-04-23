---
title: Błąd narzędzi konsolidatora LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: d85693cec11ef53a6bbbb60d8ced716d2a0bb131
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754335"
---
# <a name="linker-tools-error-lnk1179"></a>Błąd narzędzi konsolidatora LNK1179

nieprawidłowy lub uszkodzony plik: zduplikowana "nazwa pliku" COMDAT

Moduł obiektu zawiera co najmniej dwa comdats o tej samej nazwie.

Ten błąd może być spowodowany przy użyciu [/H](../../build/reference/h-restrict-length-of-external-names.md), który ogranicza długość nazw zewnętrznych i [/Gy](../../build/reference/gy-enable-function-level-linking.md), który pakiety funkcji w COMDATs.

## <a name="example"></a>Przykład

W poniższym `function1` kodzie i `function2` są identyczne w pierwszych ośmiu znaków. Kompilacja z **/Gy** i **/H8** powoduje błąd łącza.

```cpp
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```
