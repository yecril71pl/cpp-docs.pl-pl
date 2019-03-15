---
title: /DISASM
ms.date: 1/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: 10e8187e896b3922438a8cf2dafa0aec4c91f904
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57822538"
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

Tylko [/HEADERS](headers.md) — opcja polecenia DUMPBIN jest dostępny do użytku na pliki tworzone przez [/GL (optymalizacja całego programu)](gl-whole-program-optimization.md) — opcja kompilatora.

## <a name="see-also"></a>Zobacz także

[Opcje DUMPBIN](dumpbin-options.md)
