---
title: -FD (minimalna ponowna kompilacja IDE) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FD
dev_langs:
- C++
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74fb35ec25bed808e2165498c00b65723aba5bac
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702445"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Minimalna ponowna kompilacja IDE)

**/FD** nie jest widoczne dla użytkowników z wyjątkiem w [wiersza polecenia](../../ide/command-line-property-pages.md) strony właściwości projektu C++ **stron właściwości** okno dialogowe, w przypadku i tylko wtedy, gdy [/Gm (Włącz minimalną ponowną kompilację)](../../build/reference/gm-enable-minimal-rebuild.md) również nie jest zaznaczone. **/FD** nie obowiązuje, innego niż ze środowiska projektowego. **/FD** nie jest widoczny w danych wyjściowych **cl /?**.

Jeśli nie włączysz **/Gm** w środowisku programistycznym **/FD** będą używane. **/FD** gwarantuje, że plik .idb ma wystarczające informacje o zależnościach. **/FD** jest używana tylko przez środowisko programistyczne i nie powinny być używane z wiersza polecenia lub skryptu kompilacji.

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)
[opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)