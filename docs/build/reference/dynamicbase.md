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
ms.openlocfilehash: 13987b4ba9c25db0f5417da562ff86f4230937d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271830"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Określa, czy ma być generowany obraz wykonywalny, który może być losowo przebazowanych w czasie ładowania przy użyciu funkcji randomizacji (ASLR) adres miejsca układu systemu Windows, która została po raz pierwszy dostępny w Windows Vista.

## <a name="syntax"></a>Składnia

> **/ DYNAMICBASE**[**: NO**]

## <a name="remarks"></a>Uwagi

**Opcja/DynamicBase** opcja modyfikuje nagłówek *obrazu pliku wykonywalnego*, pliku .dll lub .exe, aby wskazać, czy aplikacja powinna być losowo przebazowanych w czasie ładowania i umożliwia wirtualnego adresu losowe alokacji, który ma wpływ na lokalizację w pamięci wirtualnej sterty, stosy i alokacjami systemu operacyjnego. **Opcja/DynamicBase** opcja dotyczy zarówno 32-bitowych i 64-bitowych obrazów. Obsługiwany jest ASLR w systemach Windows Vista i nowszych systemach operacyjnych. Opcja jest ignorowana przez starszych systemów operacyjnych.

Domyślnie **opcja/DynamicBase** jest włączona. Aby wyłączyć tę opcję, należy użyć **: No**. **Opcja/DynamicBase** opcja jest wymagana dla [/highentropyva](highentropyva-support-64-bit-aslr.md) opcję, aby mieć wpływ.

## <a name="see-also"></a>Zobacz także

- [Opcje EDITBIN](editbin-options.md)
- [Poziom ochrony oprogramowania niezależnego dostawcy oprogramowania Windows](https://msdn.microsoft.com/library/bb430720.aspx)