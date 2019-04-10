---
title: Linker Tools Warning LNK4286
ms.date: 04/09/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: f4ab9104c68534eaf1278a6cacb91623c24a237b
ms.sourcegitcommit: 0ad3f4517e64900a2702dd3d366586f9e2bce2c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477440"
---
# <a name="linker-tools-warning-lnk4286"></a>Linker Tools Warning LNK4286

> symbol "*symbol*"zdefiniowane w"*filename_1.obj*"zaimportowanych przez"*filename_2.obj*"

[__declspec(DllImport)](../../cpp/dllexport-dllimport.md) określono *symbol* nawet, jeśli symbol jest zdefiniowany w pliku obiektu *filename_1.obj* w ten sam obraz. Usuń `__declspec(dllimport)` modyfikator, aby rozwiązać tego ostrzeżenia.

## <a name="remarks"></a>Uwagi

Ostrzeżenie LNK4286 jest nieco bardziej ogólnych [LNK4217 ostrzeżenie narzędzi konsolidatora](linker-tools-warning-lnk4217.md). Konsolidator wygeneruje ostrzeżenie LNK4286, gdy można stwierdzić, plik, który obiekt odwołanie do symbolu, ale nie funkcji.

Aby rozwiązać LNK4286, Usuń `__declspec(dllimport)` modyfikator deklaracji z deklaracją do przodu o *symbol* zawartymi w *filename_2.obj*.

Chociaż końcowego wygenerowany kod działa poprawnie, kod generowany w celu wywołania funkcji importowanych jest mniej wydajne niż bezpośrednie wywoływanie funkcji. To ostrzeżenie nie jest wyświetlany podczas kompilowania przy użyciu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opcji.

Aby uzyskać więcej informacji na temat Importowanie i eksportowanie danych deklaracji, zobacz [dllexport i dllimport](../../cpp/dllexport-dllimport.md).

## <a name="see-also"></a>Zobacz także

[Linker Tools Warning LNK4049](linker-tools-warning-lnk4049.md) \
[Linker Tools Warning LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)