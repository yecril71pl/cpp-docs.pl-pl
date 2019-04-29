---
title: Ostrzeżenie narzędzi konsolidatora LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: 43ed18808ba5ce632dd7dc7095f7bc30e4497ec9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352440"
---
# <a name="linker-tools-warning-lnk4286"></a>Ostrzeżenie narzędzi konsolidatora LNK4286

> symbol "*symbol*"zdefiniowane w"*filename_1.obj*"zaimportowanych przez"*filename_2.obj*"

[__declspec(DllImport)](../../cpp/dllexport-dllimport.md) określono *symbol* nawet, jeśli symbol jest zdefiniowany w pliku obiektu *filename_1.obj* w ten sam obraz. Usuń `__declspec(dllimport)` modyfikator, aby rozwiązać tego ostrzeżenia.

## <a name="remarks"></a>Uwagi

Ostrzeżenie LNK4286 jest nieco bardziej ogólnych [LNK4217 ostrzeżenie narzędzi konsolidatora](linker-tools-warning-lnk4217.md). Konsolidator wygeneruje ostrzeżenie LNK4286, gdy można stwierdzić, plik, który obiekt odwołanie do symbolu, ale nie funkcji.

Aby rozwiązać LNK4286, Usuń `__declspec(dllimport)` modyfikator deklaracji z deklaracją do przodu o *symbol* zawartymi w *filename_2.obj*.

Chociaż końcowego wygenerowany kod działa poprawnie, kod generowany w celu wywołania funkcji importowanych jest mniej wydajne niż bezpośrednie wywoływanie funkcji. To ostrzeżenie nie jest wyświetlany podczas kompilowania przy użyciu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opcji.

Aby uzyskać więcej informacji na temat Importowanie i eksportowanie danych deklaracji, zobacz [dllexport i dllimport](../../cpp/dllexport-dllimport.md).

## <a name="see-also"></a>Zobacz także

[Linker Tools Warning LNK4049](linker-tools-warning-lnk4049.md) \
[Linker Tools Warning LNK4217](linker-tools-warning-lnk4217.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)