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
ms.openlocfilehash: 89b0784ff10e7d9521351e01d8907c963c9304fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="disasm"></a>/DISASM

Drukowanie dezasemblacji sekcji kodu w danych wyjściowych polecenia DUMPBIN.

## <a name="syntax"></a>Składnia

> **/DISASM**{**:**\[**BYTES**|**NOBYTES**]}  

### <a name="arguments"></a>Argumenty

**BYTES**  
Obejmuje bajtów instrukcji wraz z opcodes interpretowany i argumenty w danych wyjściowych dezasemblacji. Jest to opcja domyślna.

**NOBYTES**  
Nie ma instrukcji bajtów w danych wyjściowych dezasemblacji.

## <a name="remarks"></a>Uwagi

**/DISASM** opcja powoduje wyświetlenie dezasemblacji sekcji kodu w pliku. Jeśli są obecne w pliku używa symboli debugowania.

**/ DISASM** powinien być używany tylko w macierzystym, nie jest zarządzany, obrazy. Odpowiednik narzędzie dla kodu zarządzanego nie jest [narzędzia ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Tylko [/HEADERS](../../build/reference/headers.md) — opcja polecenia DUMPBIN jest dostępny do użytku na pliki tworzone przez [/GL (optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora.

## <a name="see-also"></a>Zobacz także

[Opcje DUMPBIN](../../build/reference/dumpbin-options.md)  
