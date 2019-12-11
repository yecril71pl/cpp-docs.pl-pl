---
title: Ostrzeżenie LNK4253 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4253
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
ms.openlocfilehash: c3f45880571e5c06f76d5f063ff993e2f6b2be9b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988083"
---
# <a name="linker-tools-warning-lnk4253"></a>Ostrzeżenie LNK4253 narzędzi konsolidatora

sekcja "Section1" nie została scalona z "section2"; scalono już do "section3"

Konsolidator wykrył wiele, powodujących konflikt żądań scalania. Konsolidator zignoruje jeden z żądań.

Napotkano opcję/dyrektywę metody **/merge** , a sekcja `from` została już scalona z inną sekcją ze względu na poprzednią opcję lub dyrektywę **/merge** (lub z powodu niejawnego scalania z konsolidatora).

Aby rozwiązać LNK4253 narzędzi KONSOLIDATORA, Usuń jedno z żądań scalenia.

W przypadku komputerów z procesorem x86 i elementów docelowych Windows CE (ARM, MIPS, SH4 i kciuk C++) z wizualizacją. Sekcja CRT jest teraz tylko do odczytu. Jeśli kod zależy od poprzedniego zachowania (. Sekcje CRT są do odczytu/zapisu, ale można zobaczyć nieoczekiwane zachowanie.

Aby uzyskać więcej informacji, zobacz,

- [/MERGE (Połącz sekcje)](../../build/reference/merge-combine-sections.md)

- [komentarz (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Przykład

W poniższym przykładzie konsolidator jest polecany do scalania części `.rdata`, ale w różnych sekcjach. Poniższy przykład generuje LNK4253 narzędzi KONSOLIDATORA.

```cpp
// LNK4253.cpp
// compile with: /W1 /link /merge:.rdata=text2
// LNK4253 expected
#pragma comment(linker, "/merge:.rdata=.text")
int main() {}
```
