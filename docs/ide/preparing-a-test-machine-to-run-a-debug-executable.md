---
title: Przygotowanie maszyny testowej do uruchomienia debugowania pliku wykonywalnego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31369f6aad04a0bd7077e9718e0b85776ca39556
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377815"
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>Przygotowanie maszyny testowej do uruchomienia debugowania pliku wykonywalnego

Aby przygotować komputer, aby sprawdzić wersję debugowania aplikacji, która powstała przy użyciu języka Visual C++, należy wdrażać wersje do debugowania biblioteki Visual C++ bibliotek DLL, która zależy od aplikacji. Aby zidentyfikować, które biblioteki DLL mają zostać wdrożone, wykonaj kroki opisane w [poznanie zależności aplikacji Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Zazwyczaj mają nazwy, które kończą się na "d"; w wersji debugowania bibliotek DLL biblioteki Visual C++ na przykład pliku msvcr100.dll wersję debugowania nosi nazwę msvcr100d.dll.

> [!NOTE]
>  Wersje do debugowania aplikacji nie są do dystrybucji i wersji debugowania bibliotek DLL biblioteki Visual C++ nie są do dystrybucji. Wersje do debugowania aplikacji i bibliotek DLL Visual C++ mogą wdrażać tylko na innych komputerach, wyłącznie w celu debugowania i testowania aplikacji na komputerze, na którym nie ma zainstalowanego programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md).

Istnieją trzy sposoby wdrażania wersji debugowania bibliotek DLL biblioteki Visual C++, wraz z wersji debugowania aplikacji.

- Aby zainstalować wersję debugowania określonej biblioteki DLL Visual C++ w katalogu %windir%\system32\ przy użyciu projektu instalacji, który obejmuje moduły scalania dla odpowiedniej biblioteki wersji i architektury aplikacji, używają centralnego wdrożenia. Moduły scalania znajdują się w Program Files lub katalogu Program Files (x86) \Common modułów\\. Wersja do debugowania modułu scalania generuje debugowania, w tym przykładzie namefor Microsoft_VC110_DebugCRT_x86.msm. Przykładem tego wdrożenia można znaleźć w [wskazówki: Wdrażanie Visual C++ Application By Using projektu Instalatora](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

- Użyj lokalnego wdrażania, aby zainstalować wersję debugowania określonej biblioteki DLL Visual C++ w katalogu instalacyjnym aplikacji przy użyciu plików, które znajdują się w katalogu Program Files (x86) w \Microsoft Visual Studio lub Program Files \<wersja > \VC\redist\Debug_NonRedist\\.

    > [!NOTE]
    >  Zdalne debugowanie aplikacji skompilowanych przy użyciu Visual C++ 2005 lub Visual C++ 2008 na innym komputerze, trzeba wdrażać wersje do debugowania biblioteki Visual C++ bibliotek DLL jako współużytkowanych zestawów side-by-side. Aby zainstalować odpowiednie moduły scalania, można użyć projektu instalacji lub Instalatora Windows.

- Użyj the_**Wdróż** opcji **programu Configuration Manager** okno dialogowe w programie Visual Studio, aby skopiować dane wyjściowe projektu i inne pliki do komputera zdalnego.

Po zainstalowaniu bibliotek DLL Visual C++, można uruchomić zdalnego debugera w udziale sieciowym. Aby uzyskać więcej informacji na temat debugowania zdalnego, zobacz [zdalne debugowanie](/visualstudio/debugger/remote-debugging.md).

## <a name="see-also"></a>Zobacz też

[Wdrażanie w Visual C++](../ide/deployment-in-visual-cpp.md)<br>
[Opcje wiersza polecenia Instalatora Windows](/windows/desktop/Msi/command-line-options)<br>
[Przykłady wdrożeń](../ide/deployment-examples.md)<br>
[Debugowanie zdalne](/visualstudio/debugger/remote-debugging.md)