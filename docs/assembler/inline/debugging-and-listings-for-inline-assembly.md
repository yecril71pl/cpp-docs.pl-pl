---
title: Debugowanie i listy dla zestawu wbudowanego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6cca954ae15252b97d883ba8491fdb98e506f68
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689292"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>Debugowanie i listy dla zestawu wbudowanego

**Microsoft Specific**

Programy zawierają wbudowany kod zestawu może być debugowany przy użyciu debugera poziom źródła, jeśli kompilujesz z opcją [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) opcji.

W ramach debugera można ustawić punktów przerwania w wierszach C lub C++ i język asemblera. Jeśli włączysz zestawów mieszanych i tryb źródła, możesz wyświetlić źródłowym i w postaci zdezasemblowany kod zestawu.

Należy pamiętać, że umieszczenie wielu zestawu instrukcji lub instrukcjach języka źródłowego w jednym wierszu mogą utrudniać debugowania. W trybie źródła można użyć debugera można ustawić punktów przerwania w jednym wierszu, ale nie na pojedyncze instrukcje w tym samym wierszu. Ta sama zasada dotyczy `__asm` bloku zdefiniowany jako makra języka C, która rozszerza się na jednym wierszu logicznym.

Jeśli utworzysz mieszane źródła i listę przy użyciu zestawu [/FAS](../../build/reference/fa-fa-listing-file.md) — opcja kompilatora, listę zawiera zarówno źródłowy, jak i zestaw formularze każdego wiersza języka asemblera. Makra nie są rozszerzone na listach zawartości, ale są one rozszerzane podczas kompilacji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>