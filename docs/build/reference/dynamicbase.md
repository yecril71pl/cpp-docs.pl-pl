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
ms.openlocfilehash: ab7682c8344d6fc36ded03e7ef885c83d2f19ab7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169048"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Określa, czy generować obraz wykonywalny, który może być losowo zmieniany w czasie ładowania przy użyciu funkcji losowego układu przestrzeni adresowej (ASLR) systemu Windows, która była początkowo dostępna w systemie Windows Vista.

## <a name="syntax"></a>Składnia

> **/DYNAMICBASE**[ **: No**]

## <a name="remarks"></a>Uwagi

Opcja **/DYNAMICBASE** modyfikuje nagłówek *obrazu wykonywalnego*, pliku DLL lub exe, aby wskazać, czy aplikacja powinna być losowo zmieniana w czasie ładowania, i umożliwia losowe generowanie alokacji adresów wirtualnych, co ma wpływ na lokalizację pamięci wirtualnej sterty, stosy i inne alokacje systemu operacyjnego. Opcja **/DYNAMICBASE** dotyczy zarówno obrazów 32-bitowych, jak i 64-bitowych. ASLR jest obsługiwana w systemach operacyjnych Windows Vista i nowszych. Ta opcja jest ignorowana przez wcześniejsze systemy operacyjne.

Domyślnie **/DYNAMICBASE** jest włączona. Aby wyłączyć tę opcję, użyj **/DYNAMICBASE: No**. Opcja **/DYNAMICBASE** jest wymagana, aby opcja [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) miała efekt.

## <a name="see-also"></a>Zobacz też

- [Opcje EDITBIN](editbin-options.md)
- [Ochrona przed oprogramowaniem ISV systemu Windows](https://msdn.microsoft.com/library/bb430720.aspx)
