---
title: Błąd narzędzi konsolidatora LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: b397ef8e551f8cd6179392541e35183a5850454f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357751"
---
# <a name="linker-tools-error-lnk1561"></a>Błąd narzędzi konsolidatora LNK1561

punkt wejścia musi być zdefiniowany

Konsolidator nie znalazł *punktu wejścia*, początkowej funkcji do wywołania w pliku wykonywalnym. Domyślnie konsolidator `main` wyszukuje lub `wmain` funkcji dla `WinMain` `wWinMain` aplikacji konsoli, lub `DllMain` funkcji dla aplikacji systemu Windows lub biblioteki DLL, która wymaga inicjowania. Inną funkcję można określić za pomocą opcji [/ENTRY.](../../build/reference/entry-entry-point-symbol.md)

Ten błąd może mieć kilka przyczyn:

- Być może nie uwzględniono pliku definiujące punkt wejścia na liście plików do połączenia. Sprawdź, czy plik zawierający funkcję punktu wejścia jest połączony z aplikacją.
- Być może zdefiniowano punkt wejścia przy użyciu niewłaściwego podpisu funkcji; na przykład może mieć błędnie lub używane niewłaściwy przypadek dla nazwy funkcji lub określono typ zwracany lub typy parametrów niepoprawnie.
- Być może nie określono opcji [/DLL](../../build/reference/dll-build-a-dll.md) podczas tworzenia biblioteki DLL.
- Być może nazwa funkcji punktu wejścia została określona niepoprawnie podczas użycia opcji [/ENTRY.](../../build/reference/entry-entry-point-symbol.md)
- Jeśli używasz narzędzia [LIB](../../build/reference/lib-reference.md) do tworzenia biblioteki DLL, być może określono plik def. Jeśli tak, usuń plik def z kompilacji.

Podczas tworzenia aplikacji konsolidator szuka funkcji punktu wejścia do wywołania, aby uruchomić kod. Jest to funkcja, która jest wywoływana po załadowaniu aplikacji i zainicjowane środowisko uruchomieniowe. Musisz podać funkcję punktu wejścia dla aplikacji lub aplikacja nie może działać. Punkt wejścia jest opcjonalny dla biblioteki DLL. Domyślnie konsolidator wyszukuje funkcję punktu wejścia, która ma jedną `int main(int, char**)`z kilku określonych nazw i podpisów, takich jak . Inną nazwę funkcji można określić jako punkt wejścia za pomocą opcji /ENTRY.

## <a name="example"></a>Przykład

Następujący przykład generuje LNK1561:

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
