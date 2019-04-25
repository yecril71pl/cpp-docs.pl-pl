---
title: /FD (Minimalna ponowna kompilacja IDE)
ms.date: 04/08/2019
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: ac63b021dc0cb9ee5964af7fa2e168f710653979
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292878"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Minimalna ponowna kompilacja IDE)

**/FD** jest dostępne tylko dla użytkowników w [wiersza polecenia](command-line-property-pages.md) stronie właściwości C++ projektu **stron właściwości** okno dialogowe. Dostępne wtedy i tylko wtedy, gdy jest przestarzała i będzie wyłączone domyślnie [/Gm (Włącz minimalną ponowną kompilację)](gm-enable-minimal-rebuild.md) nie została wybrana opcja. **/FD** nie obowiązuje, innego niż ze środowiska projektowego. **/FD** nie jest widoczne w danych wyjściowych `cl /?`.

Jeśli nie włączysz przestarzałego **/Gm** opcja w środowisku deweloperskim **/FD** jest używany. **/FD** zapewnia pliku .idb ma wystarczające informacje o zależnościach. **/FD** jest używana tylko przez środowisko programistyczne i nie powinny być używane z wiersza polecenia lub skryptu kompilacji.

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
