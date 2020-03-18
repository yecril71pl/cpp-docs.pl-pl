---
title: /FD (Minimalna ponowna kompilacja IDE)
ms.date: 04/08/2019
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: 896adcb97a259e6714cf23241424841456371491
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439805"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Minimalna ponowna kompilacja IDE)

**/FD** jest dostępna tylko dla użytkowników na stronie właściwości [wiersza polecenia](command-line-property-pages.md) okna dialogowego C++ **strony właściwości** projektu. Jest ona dostępna, jeśli i tylko wtedy, gdy opcja nie jest zaznaczona i wyłączona [(Włącz minimalną](gm-enable-minimal-rebuild.md) ponowną kompilację). **/FD** nie jest efektem innym niż środowisko programistyczne. **/FD** nie jest ujawniane w danych wyjściowych `cl /?`.

Jeśli nie włączysz opcji **/GM** przestarzałe w środowisku deweloperskim, zostanie użyta wartość **/FD** . **/FD** gwarantuje, że plik. IDB ma wystarczające informacje o zależnościach. **/FD** jest używana tylko przez środowisko programistyczne i nie należy go używać z wiersza polecenia ani skryptu kompilacji.

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
