---
title: _crtDbgFlag | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d9900d42a5bae3c7a613028a7ae4ffe4bdc0333
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044915"
---
# <a name="crtdbgflag"></a>_crtDbgFlag

**_CrtDbgFlag** flagi składa się z pól bitowych pięć, które kontrolują sposób alokacji pamięci w wersji do debugowania sterty są śledzone, zweryfikowane, zgłaszane i zrzucany. Pola bitowe flagi są ustawiane przy użyciu [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) funkcji. Ta flaga i jego pola bitowe są deklarowane w pliku Crtdbg.h. Ta flaga jest dostępna tylko podczas [_DEBUG](../c-runtime-library/debug.md) Flaga został zdefiniowany w aplikacji.

Aby uzyskać więcej informacji o używaniu tej flagi w połączeniu z innymi funkcjami debugowania, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details).

## <a name="see-also"></a>Zobacz też

[Flagi kontrolne](../c-runtime-library/control-flags.md)