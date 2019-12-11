---
title: Ostrzeżenie LNK4254 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4254
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
ms.openlocfilehash: 8431bd2d89fd5df5cf076ad006ab04006f552c4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988063"
---
# <a name="linker-tools-warning-lnk4254"></a>Ostrzeżenie LNK4254 narzędzi konsolidatora

sekcja "Section1" (offset) została scalona z elementem "section2" (offset) z różnymi atrybutami

Zawartość jednej sekcji została scalona w innej, ale atrybuty obu sekcji są różne. Program może dać nieoczekiwane wyniki. Na przykład dane, które mają być tylko do odczytu, mogą teraz znajdować się w sekcji możliwej do zapisu.

Aby rozwiązać LNK4254 narzędzi KONSOLIDATORA, zmodyfikuj lub Usuń żądanie scalenia.

W przypadku komputerów z procesorem x86 i elementów docelowych Windows CE (ARM, MIPS, SH4 i kciuk C++) z wizualizacją. Sekcja CRT jest tylko do odczytu. Jeśli kod zależy od poprzedniego zachowania (. Sekcje CRT są do odczytu/zapisu, ale można zobaczyć nieoczekiwane zachowanie.

Aby uzyskać więcej informacji, zobacz,

- [/MERGE (Połącz sekcje)](../../build/reference/merge-combine-sections.md)

- [komentarz (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Przykład

Poniższy przykład generuje LNK4254 narzędzi KONSOLIDATORA.

```cpp
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```
