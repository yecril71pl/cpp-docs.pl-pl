---
title: /DISASM
ms.date: 01/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: fb394b2266470e77c50ce5398aea961c37ac34fb
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927724"
---
# <a name="disasm"></a>/DISASM

Wydrukuj demontaż sekcji kodu w danych wyjściowych polecenia DUMPBIN.

## <a name="syntax"></a>Składnia

> **/DISASM**{ **:** \[**BYTES**|**NOBYTES**]}

### <a name="arguments"></a>Argumenty

**BYTES**<br/>
Zawiera instrukcje bajty wraz ze interpretowanymi opcode i argumentami w danych wyjściowych demontażu. Jest to opcja domyślna.

**NOBYTES**<br/>
Nie zawiera instrukcji w bajtach w danych wyjściowych deasemblera.

## <a name="remarks"></a>Uwagi

Opcja **opcja/DISASM** wyświetla odzbiór sekcji kodu w pliku. Używa symboli debugowania, jeśli znajdują się w pliku.

**Opcja/DISASM** należy używać tylko w natywnych, niezarządzanych obrazach. Odpowiednikiem narzędzia dla kodu zarządzanego jest [Ildasm](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Tylko opcja [/Headers](headers.md) polecenia DUMPBIN jest dostępna do użytku dla plików tworzonych przez opcję kompilatora [/GL (Optymalizacja całego programu)](gl-whole-program-optimization.md) .

## <a name="see-also"></a>Zobacz także

[Opcje DUMPBIN](dumpbin-options.md)
