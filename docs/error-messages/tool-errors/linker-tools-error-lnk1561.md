---
title: Błąd narzędzi konsolidatora LNK1561 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1561
dev_langs:
- C++
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac24ed0c4aff4cbd7f0ea95ff71d0b8c4b3be09c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050765"
---
# <a name="linker-tools-error-lnk1561"></a>Błąd narzędzi konsolidatora LNK1561

punkt wejścia musi być zdefiniowany.

Konsolidator nie znalazł *punktu wejścia*, początkowej funkcja do wywołania w plik wykonywalny. Domyślnie konsolidator szuka `main` lub `wmain` dla aplikacji konsoli, funkcja `WinMain` lub `wWinMain` dla aplikacji Windows, funkcja lub `DllMain` dla biblioteki DLL, która wymaga inicjowania. Należy określić inną funkcję za pomocą [/Entry](../../build/reference/entry-entry-point-symbol.md) — opcja konsolidatora.

Ten błąd może mieć kilka przyczyn:
- Może nie dołączono plik który definiuje punktem wejścia na liście plików w celu połączenia. Upewnij się, że plik, który zawiera funkcję punktu wejścia jest połączony z Twoją aplikacją.
- Definicja punktu wejścia przy użyciu sygnatury funkcji problem; na przykład możesz mieć błędnie napisana lub używany nieprawidłowy przypadek dla nazwy funkcji lub niepoprawnie określony zwracany typ lub typy parametrów.
- Nie określono [/dll](../../build/reference/dll-build-a-dll.md) opcję podczas kompilowania biblioteki DLL.
- Być może określono nazwę funkcji punktu wejścia niepoprawnie użycia [/Entry](../../build/reference/entry-entry-point-symbol.md) — opcja konsolidatora.
- Jeśli używasz [LIB](../../build/reference/lib-reference.md) narzędzie do tworzenia biblioteki DLL, określony plik .def. Jeśli tak, usuń plik .def z kompilacji.

Podczas kompilowania aplikacji, konsolidator szuka funkcję punktu wejścia do wywołania, aby uruchomić kod. Jest to funkcja, która jest wywoływana po załadowaniu aplikacji i środowiska uruchomieniowego jest zainicjowany. Należy podać funkcję punktu wejścia dla aplikacji lub nie można uruchomić aplikacji. Punkt wejścia jest opcjonalne dla biblioteki DLL. Domyślnie konsolidator szuka funkcji punktu wejścia, który ma jeden z kilku konkretne nazwy i podpisy, takie jak `int main(int, char**)`. Można określić inną nazwę funkcji jako wpis punktu, przy użyciu opcji konsolidatora/Entry.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie LNK1561:

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```