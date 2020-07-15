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
ms.openlocfilehash: 54644d9df546299be3b688f9745a121592938df6
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373622"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Określa, czy generować obraz wykonywalny, który może być losowo zmieniany w czasie ładowania przy użyciu funkcji losowego układu przestrzeni adresowej (ASLR) systemu Windows, która była początkowo dostępna w systemie Windows Vista.

## <a name="syntax"></a>Składnia

> **/DYNAMICBASE**[**: No**]

## <a name="remarks"></a>Uwagi

Opcja **/DYNAMICBASE** modyfikuje nagłówek *obrazu wykonywalnego*, pliku DLL lub exe, aby wskazać, czy aplikacja powinna być losowo zmieniana w czasie ładowania, i umożliwia losowe generowanie alokacji adresów wirtualnych, co ma wpływ na lokalizację pamięci wirtualnej sterty, stosy i inne alokacje systemu operacyjnego. Opcja **/DYNAMICBASE** dotyczy zarówno obrazów 32-bitowych, jak i 64-bitowych. ASLR jest obsługiwana w systemach operacyjnych Windows Vista i nowszych. Ta opcja jest ignorowana przez wcześniejsze systemy operacyjne.

Domyślnie **/DYNAMICBASE** jest włączona. Aby wyłączyć tę opcję, użyj **/DYNAMICBASE: No**. Opcja **/DYNAMICBASE** jest wymagana, aby opcja [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) miała efekt.

## <a name="see-also"></a>Zobacz też

- [Opcje polecenia EDITBIN](editbin-options.md)
- [Ochrona przed oprogramowaniem ISV systemu Windows](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
