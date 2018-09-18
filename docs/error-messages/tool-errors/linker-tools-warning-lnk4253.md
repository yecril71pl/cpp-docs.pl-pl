---
title: Ostrzeżenie LNK4253 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4253
dev_langs:
- C++
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d26d688825f504cbce8224adc9a5766a555d2fc8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016822"
---
# <a name="linker-tools-warning-lnk4253"></a>Ostrzeżenie LNK4253 narzędzi konsolidatora

sekcja sekcja ' 1' nie została scalona 'Sekcja2'; już scalona "section3"

Konflikt scalania, konsolidator Wykryto wiele żądań. Konsolidator będzie ignorować jedno z żądań.

A **/MERGE** napotkano opcji lub dyrektywie i `from` sekcji został już scalony do różnych sekcji ze względu na poprzednie **/MERGE** opcji lub dyrektywie (lub z powodu niejawne scalania z konsolidator).

Aby rozwiązać LNK4253, należy usunąć jedno z żądań scalania.

Podczas określania wartości x86 maszyn i elementy docelowe Windows CE (ARM, MIPS, SH4 i przycisku przewijania) z programem Visual C++. Sekcja CRT jest teraz tylko do odczytu. Jeśli Twój kod jest zależna od poprzedniego zachowania (. Sekcje CRT są odczytu/zapisu), można uzyskać nieoczekiwane zachowanie.

Aby uzyskać więcej informacji, zobacz,

- [/MERGE (Połącz sekcje)](../../build/reference/merge-combine-sections.md)

- [komentarz (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Przykład

W poniższym przykładzie, konsolidator jest zobowiązany do scalenia `.rdata` sekcji dwa razy, ale w różne sekcje. Poniższy przykład spowoduje wygenerowanie LNK4253.

```
// LNK4253.cpp
// compile with: /W1 /link /merge:.rdata=text2
// LNK4253 expected
#pragma comment(linker, "/merge:.rdata=.text")
int main() {}
```