---
title: _crtDbgFlag
ms.date: 11/04/2016
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
ms.openlocfilehash: a967b436d53acab6d76fa36fdf9b13c7c24d49c3
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746985"
---
# <a name="crtdbgflag"></a>_crtDbgFlag

**_CrtDbgFlag** flagi składa się z pól bitowych pięć, które kontrolują sposób alokacji pamięci w wersji do debugowania sterty są śledzone, zweryfikowane, zgłaszane i zrzucany. Pola bitowe flagi są ustawiane przy użyciu [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) funkcji. Ta flaga i jego pola bitowe są deklarowane w pliku Crtdbg.h. Ta flaga jest dostępna tylko podczas [_DEBUG](../c-runtime-library/debug.md) Flaga został zdefiniowany w aplikacji.

Aby uzyskać więcej informacji o używaniu tej flagi w połączeniu z innymi funkcjami debugowania, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details).

## <a name="see-also"></a>Zobacz także

[Flagi kontrolne](../c-runtime-library/control-flags.md)
