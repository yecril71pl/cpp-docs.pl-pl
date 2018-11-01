---
title: 'Porady: debugowanie kompilacji wydania'
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
ms.openlocfilehash: 4ee99bb76d3af4339e065a3ed4d4809acfe23507
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649257"
---
# <a name="how-to-debug-a-release-build"></a>Porady: debugowanie kompilacji wydania

Umożliwia debugowanie kompilacji wydania aplikacji.

### <a name="to-debug-a-release-build"></a>Debugowanie kompilacji wydania

1. Otwórz **stron właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** węzła. Ustaw **formatu informacji debugowania** do [zgodne z C7 (/ Z7)](../../build/reference/z7-zi-zi-debug-information-format.md) lub **bazy danych programu (/Zi)**.

1. Rozwiń **konsolidatora** i kliknij przycisk **ogólne** węzła. Ustaw **Włącz konsolidację przyrostową** do [nr (/ INCREMENTAL: NO)](../../build/reference/incremental-link-incrementally.md).

1. Wybierz **debugowanie** węzła. Ustaw **generowanie informacji o debugowaniu** do [tak (/ DEBUG)](../../build/reference/debug-generate-debug-info.md).

1. Wybierz **optymalizacji** węzła. Ustaw **odwołania** do [/OPT: REF](../../build/reference/opt-optimizations.md) i **umożliwić składanie COMDAT** do [/OPT: ICF](../../build/reference/opt-optimizations.md).

1. Można teraz debugować aplikację kompilacji wydania. Aby odnaleźć problem, przejrzyj kod (lub użyj Just-In-Time debugging), aż znajdziesz, gdzie występuje błąd, a następnie sprawdzić niepoprawne parametry lub kodu.

   Jeśli aplikacja działa w kompilacji debugowania, ale zakończy się niepowodzeniem w kompilacji wydania, jeden optymalizacje kompilatora może udostępnianie wadę w kodzie źródłowym. Aby ustalić przyczynę problemu, należy wyłączyć optymalizacje wybrane dla każdego pliku kodu źródłowego do momentu zlokalizowania pliku i Optymalizacja, który jest przyczyną problemu. (Aby przyspieszyć proces, należy można podzielić pliki na dwie grupy, wyłącz optymalizację na jedną grupę i po znalezieniu problem w grupie, nadal dzielenia aż izolowania pliku problem.)

   Możesz użyć [usunęliśmy](../../build/reference/rtc-run-time-error-checks.md) próby umożliwiającymi takie błędy w swoich kompilacjach debugowania.

   Aby uzyskać więcej informacji, zobacz [optymalizacji kodu](../../build/reference/optimizing-your-code.md).

## <a name="see-also"></a>Zobacz też

[Naprawianie problemów kompilacji wydania](../../build/reference/fixing-release-build-problems.md)