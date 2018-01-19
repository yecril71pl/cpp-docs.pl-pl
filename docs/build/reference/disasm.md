---
title: /DISASM | Microsoft Docs
ms.date: 1/17/2018
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /disasm
dev_langs: C++
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d448b92c3436f3d2875bd8d9b8e0af6a7149e065
ms.sourcegitcommit: ff9bf140b6874bc08718674c07312ecb5f996463
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
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
