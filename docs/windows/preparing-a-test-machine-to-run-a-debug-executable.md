---
title: Przygotowanie maszyny testowej do uruchomienia debugowania pliku wykonywalnego
ms.date: 07/02/2019
helpviewer_keywords:
- debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
ms.openlocfilehash: 87d2bf434aef3a85bf7fa19f5886bec106515809
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552338"
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>Przygotowanie maszyny testowej do uruchomienia debugowania pliku wykonywalnego

Aby przygotować komputer, aby sprawdzić wersję debugowania aplikacji, która powstała przy użyciu języka Visual C++, należy wdrażać wersje do debugowania biblioteki Visual C++ bibliotek DLL, która zależy od aplikacji. Aby zidentyfikować, które biblioteki DLL mają zostać wdrożone, wykonaj kroki opisane w [poznanie zależności aplikacji Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md). Zazwyczaj mają nazwy, które kończą się na "d"; w wersji debugowania bibliotek DLL biblioteki Visual C++ na przykład pliku msvcr100.dll wersję debugowania nosi nazwę msvcr100d.dll.

> [!NOTE]
>  Wersje do debugowania aplikacji nie są do dystrybucji i wersji debugowania bibliotek DLL biblioteki Visual C++ nie są do dystrybucji. Wersje do debugowania aplikacji i bibliotek DLL Visual C++ mogą wdrażać tylko na innych komputerach, wyłącznie w celu debugowania i testowania aplikacji na komputerze, na którym nie ma zainstalowanego programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Redistributing Visual C++ Files](redistributing-visual-cpp-files.md).

Istnieją trzy sposoby wdrażania wersji debugowania bibliotek DLL biblioteki Visual C++, wraz z wersji debugowania aplikacji.

- Używają centralnego wdrożenia, aby zainstalować wersję debugowania konkretnej wizualizacji C++ biblioteki DLL do katalogu %windir%\system32\ przy użyciu projektu instalacji, który obejmuje moduły scalania dla odpowiedniej biblioteki wersji i architektury aplikacji. Moduły scalania znajdują się w Program Files lub katalogu Program Files (x86) \Common modułów\\. Wersja do debugowania modułu scalania generuje debugowania, w tym przykładzie namefor Microsoft_VC110_DebugCRT_x86.msm. Przykładem tego wdrożenia można znaleźć w [instruktażu: Wdrażanie aplikacji Visual C++ przy użyciu projektu instalacji](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

- Użyj lokalnego wdrażania, aby zainstalować wersję debugowania konkretnej wizualizacji C++ biblioteki DLL w katalogu instalacji aplikacji przy użyciu plików, które znajdują się w katalogu Program Files (x86) w \Microsoft Visual Studio lub Program Files \< w wersji > \VC\redist\Debug_NonRedist\\.

    > [!NOTE]
    >  Zdalne debugowanie aplikacji skompilowanych przy użyciu programu Visual Studio 2005 lub Visual Studio 2008 na innym komputerze, należy wdrożyć wersje do debugowania Visual C++ biblioteki DLL jako współużytkowanych zestawów side-by-side. Aby zainstalować odpowiednie moduły scalania, można użyć projektu instalacji lub Instalatora Windows.

- Użyj the_**Wdróż** opcji **programu Configuration Manager** okno dialogowe w programie Visual Studio, aby skopiować dane wyjściowe projektu i inne pliki do komputera zdalnego.

Po zainstalowaniu bibliotek DLL Visual C++, można uruchomić zdalnego debugera w udziale sieciowym. Aby uzyskać więcej informacji na temat debugowania zdalnego, zobacz [zdalne debugowanie](/visualstudio/debugger/remote-debugging).

## <a name="see-also"></a>Zobacz także

[Wdrażanie w Visual C++](deployment-in-visual-cpp.md)<br>
[Opcje wiersza polecenia Instalatora Windows](/windows/desktop/Msi/command-line-options)<br>
[Przykłady wdrożeń](deployment-examples.md)<br>
[Debugowanie zdalne](/visualstudio/debugger/remote-debugging)
