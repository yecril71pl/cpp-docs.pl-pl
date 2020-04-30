---
title: Przygotowanie maszyny testowej do uruchomienia debugowania pliku wykonywalnego
ms.date: 07/02/2019
helpviewer_keywords:
- debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
ms.openlocfilehash: 26a92d5efc4bf9f0332a0e81fa2f9c8b2c2a958f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359922"
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>Przygotowanie maszyny testowej do uruchomienia debugowania pliku wykonywalnego

Aby przygotować komputer do testowania wersji aplikacji skompilowanej za pomocą Visual C++, należy wdrożyć wersje debugowania bibliotek DLL biblioteki Visual C++, od których zależy aplikacja. Aby określić, które biblioteki DLL muszą zostać wdrożone, wykonaj kroki opisane w temacie [Informacje o zależnościach aplikacji Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md). Zwykle wersje bibliotek DLL biblioteki Visual C++ bibliotek mają nazwy kończące się na "d"; na przykład wersja debugowana pliku msvcr100. dll ma nazwę msvcr100d. dll.

> [!NOTE]
> Wersje debugowe aplikacji nie są redystrybucyjne i wersje bibliotek DLL biblioteki Visual C++ nie są redystrybuowane. W celu debugowania i testowania aplikacji na komputerze, na którym nie zainstalowano programu Visual Studio, można wdrożyć wersje debugowania aplikacji i biblioteki DLL Visual C++ tylko na innych komputerach. Aby uzyskać więcej informacji, zobacz [Redystrybuowanie plików Visual C++](redistributing-visual-cpp-files.md).

Istnieją trzy sposoby wdrażania wersji debugowania bibliotek DLL bibliotek Visual C++, a także do debugowania wersji aplikacji.

- Wdrożenie centralne służy do instalowania wersji debugowania określonej Visual C++ DLL w katalogu%windir%\system32\ przy użyciu projektu Instalatora zawierającego moduły scalania dla właściwej wersji biblioteki i architektury aplikacji. Moduły scalania są dostępne w katalogu Program Files lub Program Files (x86) w modułach\\\Common Files\Merge. Wersja debugowania modułu scalania ma debugowanie w przykładzie namefor, Microsoft_VC110_DebugCRT_x86. MSM. Przykład tego wdrożenia można znaleźć w [przewodniku: wdrażanie aplikacji Visual C++ przy użyciu projektu Instalatora](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

- Wdrożenie lokalne służy do instalowania wersji debugowania określonej Visual C++ DLL w katalogu instalacyjnym aplikacji przy użyciu plików dostarczonych w katalogu Program Files lub Program Files (x86) w wersji \Microsoft Visual Studio \<> \vc\redist\ Debug_NonRedist.\\

    > [!NOTE]
    >  Do zdalnego debugowania aplikacji skompilowanej za pomocą programu Visual Studio 2005 lub Visual Studio 2008 na innym komputerze należy wdrożyć wersje debugowania bibliotek DLL bibliotek Visual C++ jako współużytkowane zestawy równoległe. Aby zainstalować odpowiednie moduły scalania, można użyć projektu Instalatora lub Instalator Windows.

- Użyj opcji the_**Deploy** w oknie dialogowym **Configuration Manager** w programie Visual Studio, aby skopiować dane wyjściowe projektu i inne pliki na komputer zdalny.

Po zainstalowaniu bibliotek DLL Visual C++ można uruchomić zdalny debuger w udziale sieciowym. Aby uzyskać więcej informacji na temat debugowania zdalnego, zobacz [zdalne debugowanie](/visualstudio/debugger/remote-debugging).

## <a name="see-also"></a>Zobacz także

[Wdrożenie w Visual C++](deployment-in-visual-cpp.md)<br>
[Opcje wiersza polecenia Instalator Windows](/windows/win32/Msi/command-line-options)<br>
[Przykłady wdrożeń](deployment-examples.md)<br>
[Debugowanie zdalne](/visualstudio/debugger/remote-debugging)
