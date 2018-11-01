---
title: Ostrzeżenie LNK4254 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4254
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
ms.openlocfilehash: 2c68e49d58b0fd6b28607eb0ba78c092441f6f4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467018"
---
# <a name="linker-tools-warning-lnk4254"></a>Ostrzeżenie LNK4254 narzędzi konsolidatora

w sekcji 'sekcja ' 1 (przesunięciem) została scalona z "Sekcja2" (przesunięcie), z różnymi atrybutami

Zawartość jednej sekcji zostały scalone w innej, ale atrybuty dwie sekcje są różne. Program może dać nieoczekiwane wyniki. Na przykład dane, które ma być odczytywane tylko mogą teraz znajdować się w zapisywalna sekcja.

Aby rozwiązać LNK4254, należy zmodyfikować lub usunąć żądanie scalania.

Podczas określania wartości x86 maszyn i elementy docelowe Windows CE (ARM, MIPS, SH4 i przycisku przewijania) z programem Visual C++. Sekcja CRT jest tylko do odczytu. Jeśli Twój kod jest zależna od poprzedniego zachowania (. Sekcje CRT są odczytu/zapisu), można uzyskać nieoczekiwane zachowanie.

Aby uzyskać więcej informacji, zobacz,

- [/MERGE (Połącz sekcje)](../../build/reference/merge-combine-sections.md)

- [komentarz (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie LNK4254.

```
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```