---
title: Debugowanie i listy dla zestawu wbudowanego
ms.date: 08/30/2018
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
ms.openlocfilehash: 3254fb6b750466de0a38230c5e1cfa067c476f5e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169516"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>Debugowanie i listy dla zestawu wbudowanego

**Specyficzne dla firmy Microsoft**

Programy zawierające kod asemblera wbudowanego mogą być debugowane przy użyciu debugera na poziomie źródła, Jeśli kompilujesz za pomocą opcji [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) .

W debugerze można ustawić punkty przerwania w wierszach języka C C++ lub i. W przypadku włączenia zestawu mieszanego i trybu źródłowego można wyświetlić zarówno źródłowy, jak i rozmontowany formularz kodu zestawu.

Należy zauważyć, że umieszczenie wielu instrukcji zestawu lub instrukcji języka źródłowego w jednym wierszu może obsłużyć debugowanie. W trybie źródłowym można użyć debugera, aby ustawić punkty przerwania w pojedynczym wierszu, ale nie w poszczególnych instrukcjach w tym samym wierszu. Ta sama zasada ma zastosowanie do bloku `__asm` zdefiniowanego jako makro C, które rozwija się do pojedynczej linii logicznej.

Jeśli utworzysz Źródło mieszane i listę zestawu przy użyciu opcji kompilatora [/FAS](../../build/reference/fa-fa-listing-file.md) , lista zawiera zarówno formularze źródłowe, jak i zestawy poszczególnych wierszy w języku. Makra nie są rozwinięte na listach, ale są rozwinięte podczas kompilacji.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
