---
title: Ostrzeżenie narzędzi konsolidatora LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: d0205ba065f6e410383c38a0f1c2eaa0da55fe93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173871"
---
# <a name="linker-tools-warning-lnk4286"></a>Ostrzeżenie narzędzi konsolidatora LNK4286

> Symbol "*symbol*" zdefiniowany w elemencie "*filename_1. obj*" został zaimportowany przez element "*filename_2. obj*"

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) została określona dla *symbolu* , chociaż symbol jest zdefiniowany w pliku obiektu *filename_1. obj* w tym samym obrazie. Usuń modyfikator `__declspec(dllimport)`, aby usunąć to ostrzeżenie.

## <a name="remarks"></a>Uwagi

Ostrzeżenie LNK4286 to bardziej ogólna wersja [narzędzi konsolidatora LNK4217 narzędzi konsolidatora](linker-tools-warning-lnk4217.md). Konsolidator generuje ostrzeżenie LNK4286, gdy może rozpoznać plik obiektu, do którego odwołuje się symbol, ale nie funkcję.

Aby rozwiązać LNK4286, Usuń modyfikator deklaracji `__declspec(dllimport)` z deklaracji do przodu *symboli* , do której odwołuje się element *filename_2. obj*.

Mimo że ostatni wygenerowany kod działa prawidłowo, kod wygenerowany do wywołania zaimportowanej funkcji jest mniej wydajny niż bezpośrednie wywoływanie funkcji. To ostrzeżenie nie pojawia się podczas kompilowania przy użyciu opcji [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) .

Aby uzyskać więcej informacji na temat importowania i eksportowania deklaracji danych, zobacz [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="see-also"></a>Zobacz też

[Ostrzeżenie narzędzi konsolidatora lnk4049 narzędzi konsolidatora](linker-tools-warning-lnk4049.md) \
[Ostrzeżenie narzędzi konsolidatora lnk4217 narzędzi konsolidatora](linker-tools-warning-lnk4217.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
