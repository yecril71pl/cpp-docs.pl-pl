---
title: 'Porady: debugowanie kompilacji wydania'
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
ms.openlocfilehash: 6d93fac4e980085c322acb55e6f8758e6cea0a00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188967"
---
# <a name="how-to-debug-a-release-build"></a>Porady: debugowanie kompilacji wydania

Można debugować kompilację wydania aplikacji.

### <a name="to-debug-a-release-build"></a>Aby debugować kompilację wydania

1. Otwórz okno dialogowe **strony właściwości** dla projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](working-with-project-properties.md).

1. Kliknij węzeł **C/C++** . Ustaw **Format informacji debugowania** na wartość [C7 Compatible (/Z7)](reference/z7-zi-zi-debug-information-format.md) lub **Program Database (/ZI)**.

1. Rozwiń węzeł **konsolidator** i kliknij węzeł **Ogólne** . Ustaw **opcję Włącz łączenie przyrostowe** na wartość [nie (/Incremental: No)](reference/incremental-link-incrementally.md).

1. Wybierz węzeł **debugowanie** . Ustaw opcję **Generuj informacje o debugowaniu** na [wartość tak (/Debug)](reference/debug-generate-debug-info.md).

1. Wybierz węzeł **Optymalizacja** . Ustaw **odwołania** do [/OPT: ref](reference/opt-optimizations.md) i **Włącz COMDAT składania** do [/OPT: ICF](reference/opt-optimizations.md).

1. Teraz możesz debugować aplikację do tworzenia wersji. Aby znaleźć problem, Przekrocz kod (lub użyj debugowania just-in-Time) do momentu, w którym wystąpił błąd, a następnie określ nieprawidłowe parametry lub kod.

   Jeśli aplikacja działa w kompilacji debugowania, ale kończy się niepowodzeniem w kompilacji wydania, jedna z optymalizacji kompilatora może ujawnić wady w kodzie źródłowym. Aby wyizolować ten problem, wyłącz wybrane optymalizacje dla każdego pliku kodu źródłowego do momentu zlokalizowania pliku i optymalizacji, która powoduje problem. (Aby przyspieszyć proces, można podzielić pliki na dwie grupy, wyłączyć optymalizację dla jednej grupy, a po znalezieniu problemu w grupie Kontynuuj podział do momentu wyodrębnienia pliku problemu).

   Możesz użyć [/RTC](reference/rtc-run-time-error-checks.md) , aby spróbować uwidocznić takie usterki w kompilacjach debugowania.

   Aby uzyskać więcej informacji, zobacz [Optymalizacja kodu](optimizing-your-code.md).

## <a name="see-also"></a>Zobacz też

[Naprawianie problemów kompilacji wydania](fixing-release-build-problems.md)
