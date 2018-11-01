---
title: /FD (Minimalna ponowna kompilacja IDE)
ms.date: 11/04/2016
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: a902096bf13105e6a6a66b7bd3ccc56b8f7cf624
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433596"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Minimalna ponowna kompilacja IDE)

**/FD** nie jest widoczne dla użytkowników z wyjątkiem w [wiersza polecenia](../../ide/command-line-property-pages.md) strony właściwości projektu C++ **stron właściwości** okno dialogowe, w przypadku i tylko wtedy, gdy [/Gm (Włącz minimalną ponowną kompilację)](../../build/reference/gm-enable-minimal-rebuild.md) również nie jest zaznaczone. **/FD** nie obowiązuje, innego niż ze środowiska projektowego. **/FD** nie jest widoczny w danych wyjściowych **cl /?**.

Jeśli nie włączysz **/Gm** w środowisku programistycznym **/FD** będą używane. **/FD** gwarantuje, że plik .idb ma wystarczające informacje o zależnościach. **/FD** jest używana tylko przez środowisko programistyczne i nie powinny być używane z wiersza polecenia lub skryptu kompilacji.

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/F), opcje](../../build/reference/output-file-f-options.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)