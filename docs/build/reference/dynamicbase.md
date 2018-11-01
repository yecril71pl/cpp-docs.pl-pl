---
title: /DYNAMICBASE
ms.date: 06/12/2018
f1_keywords:
- /dynamicbase
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
ms.openlocfilehash: fb8bfd4f4b11d14dbbc605f4366cf1cd5446a319
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430799"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Określa, czy ma być generowany obraz wykonywalny, który może być losowo przebazowanych w czasie ładowania przy użyciu funkcji randomizacji (ASLR) adres miejsca układu systemu Windows, która została po raz pierwszy dostępny w Windows Vista.

## <a name="syntax"></a>Składnia

> **/ DYNAMICBASE**[**: NO**]

## <a name="remarks"></a>Uwagi

**Opcja/DynamicBase** opcja modyfikuje nagłówek *obrazu pliku wykonywalnego*, pliku .dll lub .exe, aby wskazać, czy aplikacja powinna być losowo przebazowanych w czasie ładowania i umożliwia wirtualnego adresu losowe alokacji, który ma wpływ na lokalizację w pamięci wirtualnej sterty, stosy i alokacjami systemu operacyjnego. **Opcja/DynamicBase** opcja dotyczy zarówno 32-bitowych i 64-bitowych obrazów. Obsługiwany jest ASLR w systemach Windows Vista i nowszych systemach operacyjnych. Opcja jest ignorowana przez starszych systemów operacyjnych.

Domyślnie **opcja/DynamicBase** jest włączona. Aby wyłączyć tę opcję, należy użyć **: No**. **Opcja/DynamicBase** opcja jest wymagana dla [/highentropyva](highentropyva-support-64-bit-aslr.md) opcję, aby mieć wpływ.

## <a name="see-also"></a>Zobacz także

- [Opcje EDITBIN](../../build/reference/editbin-options.md)
- [Poziom ochrony oprogramowania niezależnego dostawcy oprogramowania Windows](https://msdn.microsoft.com/library/bb430720.aspx)