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
ms.openlocfilehash: 323a0045ab11f23ab996d5179a135d0eb4184f20
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817442"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Minimalna ponowna kompilacja IDE)

**/FD** nie jest widoczne dla użytkowników z wyjątkiem w [wiersza polecenia](command-line-property-pages.md) strony właściwości projektu C++ **stron właściwości** okno dialogowe, w przypadku i tylko wtedy, gdy [/Gm (Włącz minimalną ponowną kompilację)](gm-enable-minimal-rebuild.md) również nie jest zaznaczone. **/FD** nie obowiązuje, innego niż ze środowiska projektowego. **/FD** nie jest widoczny w danych wyjściowych **cl /?**.

Jeśli nie włączysz **/Gm** w środowisku programistycznym **/FD** będą używane. **/FD** gwarantuje, że plik .idb ma wystarczające informacje o zależnościach. **/FD** jest używana tylko przez środowisko programistyczne i nie powinny być używane z wiersza polecenia lub skryptu kompilacji.

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
