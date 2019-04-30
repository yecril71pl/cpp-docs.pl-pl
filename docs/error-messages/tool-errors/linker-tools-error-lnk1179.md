---
title: Błąd narzędzi konsolidatora LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: 71aba1f20cfaf5b6b9ec33d43ebde594e381921f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391416"
---
# <a name="linker-tools-error-lnk1179"></a>Błąd narzędzi konsolidatora LNK1179

nieprawidłowy lub uszkodzony plik: Zduplikowana sekcja COMDAT "filename"

Moduł obiektu zawiera co najmniej dwóch Comdat o takiej samej nazwie.

Ten błąd może być spowodowany przy użyciu [/h](../../build/reference/h-restrict-length-of-external-names.md), co ogranicza długość nazw zewnętrznych i [/Gy](../../build/reference/gy-enable-function-level-linking.md), który pakuje funkcje w Comdat.

## <a name="example"></a>Przykład

W poniższym kodzie `function1` i `function2` są identyczne w pierwszych osiem znaków. Kompilowanie przy użyciu **/Gy** i **/H8** generuje błąd łącza.

```
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```