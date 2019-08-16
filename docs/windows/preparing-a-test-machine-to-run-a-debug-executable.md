---
title: Przygotowanie maszyny testowej do uruchomienia debugowania pliku wykonywalnego
ms.date: 07/02/2019
helpviewer_keywords:
- debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
ms.openlocfilehash: ae751b1632473fa316c7965bc751e91b782a89ea
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513670"
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>Przygotowanie maszyny testowej do uruchomienia debugowania pliku wykonywalnego

Aby przygotować komputer do testowania wersji aplikacji skompilowanej za pomocą wizualizacji C++, należy wdrożyć wersje debugowania bibliotek DLL biblioteki wizualnej C++ , od których zależy aplikacja. Aby określić, które biblioteki DLL muszą zostać wdrożone, wykonaj kroki opisane w temacie [Informacje o zależnościach aplikacji C++ wizualnej](understanding-the-dependencies-of-a-visual-cpp-application.md). Zwykle wersje bibliotek DLL bibliotek wizualnych C++ mają nazwy kończące się na "d"; na przykład wersja debugowana pliku msvcr100. dll ma nazwę msvcr100d. dll.

> [!NOTE]
>  Wersje debugowe aplikacji nie są redystrybucyjne i nie można redystrybuowania wersji C++ debugowania bibliotek DLL biblioteki wizualnej. W celu debugowania i testowania aplikacji na komputerze, C++ na którym nie zainstalowano programu Visual Studio, można wdrożyć wersje debugowania aplikacji i bibliotek DLL. Aby uzyskać więcej informacji, zobacz Redystrybuowanie [plików C++ wizualnych](redistributing-visual-cpp-files.md).

Istnieją trzy sposoby wdrażania wersji debugowania bibliotek DLL biblioteki graficznej C++ wraz z wersją debugowania aplikacji.

- Wdrożenie centralne służy do instalowania wersji debugowania określonej wizualizacji C++ dll w katalogu%windir%\system32\ przy użyciu projektu Instalatora zawierającego moduły scalania dla właściwej wersji biblioteki i architektury aplikacji. Moduły scalania są dostępne w katalogu Program Files lub Program Files (x86) w modułach\\\Common Files\Merge. Wersja debugowania modułu scalania ma debugowanie w namefor przykładzie Microsoft_VC110_DebugCRT_x86. MSM. Przykład tego wdrożenia można znaleźć w [przewodniku: Wdrażanie aplikacji wizualnej C++ przy użyciu projektu](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)Instalatora.

- Wdrożenie lokalne służy do instalowania wersji debugowania określonej wizualnej C++ biblioteki DLL w katalogu instalacyjnym aplikacji przy użyciu plików udostępnianych w katalogu Program Files lub Program Files (x86) w \Microsoft Visual Studio \< wersja > \VC\redist\Debug_NonRedist\\.

    > [!NOTE]
    >  Do zdalnego debugowania aplikacji skompilowanej za pomocą programu Visual Studio 2005 lub Visual Studio 2008 na innym komputerze należy wdrożyć wersje debugowania bibliotek DLL biblioteki wizualnej C++ jako współużytkowane zestawy równoległe. Aby zainstalować odpowiednie moduły scalania, można użyć projektu Instalatora lub Instalator Windows.

- Użyj opcji the_**Deploy** w oknie dialogowym **Configuration Manager** w programie Visual Studio, aby skopiować dane wyjściowe projektu i inne pliki na komputer zdalny.

Po zainstalowaniu C++ bibliotek DLL można uruchomić zdalny debuger w udziale sieciowym. Aby uzyskać więcej informacji na temat debugowania zdalnego, zobacz [zdalne debugowanie](/visualstudio/debugger/remote-debugging).

## <a name="see-also"></a>Zobacz także

[Wdrażanie w Visual C++](deployment-in-visual-cpp.md)<br>
[Opcje wiersza polecenia Instalator Windows](/windows/win32/Msi/command-line-options)<br>
[Przykłady wdrożeń](deployment-examples.md)<br>
[Debugowanie zdalne](/visualstudio/debugger/remote-debugging)
