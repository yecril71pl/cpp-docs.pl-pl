---
title: /DISASM
ms.date: 1/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: 77f6f05029ec4480afb2180eab0bb57838d643a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462949"
---
# <a name="disasm"></a>/DISASM

Drukowanie dezasemblacji sekcji kodu w danych wyjściowych polecenia DUMPBIN.

## <a name="syntax"></a>Składnia

> **/DISASM**{**:**\[**BYTES**|**NOBYTES**]}

### <a name="arguments"></a>Argumenty

**BYTES**<br/>
Obejmuje bajtów instrukcji wraz z interpretowanych rozkazów i argumenty w danych wyjściowych dezasemblacji. Jest to opcja domyślna.

**NOBYTES**<br/>
Nie obejmuje bajtów instrukcji w danych wyjściowych dezasemblacji.

## <a name="remarks"></a>Uwagi

**/DISASM** opcji wyświetla dezasemblację sekcje kodu w pliku. Używa symbole debugowania, jeśli są obecne w pliku.

**/ DISASM** powinien być używany tylko w obrazach macierzystych, nie zarządzany. Jest równoważne narzędzie dla kodu zarządzanego [ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Tylko [/HEADERS](../../build/reference/headers.md) — opcja polecenia DUMPBIN jest dostępny do użytku na pliki tworzone przez [/GL (optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora.

## <a name="see-also"></a>Zobacz także

[Opcje DUMPBIN](../../build/reference/dumpbin-options.md)
