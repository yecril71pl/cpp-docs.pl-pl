---
title: / DISASM | Dokumentacja firmy Microsoft
ms.date: 1/17/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /disasm
dev_langs:
- C++
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a5a4d930c47d2a3c2808cbd0a343c5c68de4ac9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707190"
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
