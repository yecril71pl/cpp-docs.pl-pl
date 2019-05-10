---
title: Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia
ms.custom: conceptual
ms.date: 05/06/2019
helpviewer_keywords:
- environment variables [C++]
- VCVARS32.bat file
- cl.exe compiler [C++], environment variables
- LINK tool [C++], environment variables
- PATH reserved word
- INCLUDE reserved word
- LINK tool [C++], path
- LIB environment variable
- compiling source code [C++], from command line
- environment variables [C++], CL compiler
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
ms.openlocfilehash: 30dadf365186ae74144a3225889c08eedfb89b47
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217602"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia

Microsoft C++ narzędzia wiersza polecenia kompilacji (MSVC) wymaga kilku zmiennych środowiskowych, które są dostosowane dla danej konfiguracji instalacji i kompilacji. Obciążenie języka C++ jest instalowany przez Instalatora programu Visual Studio, tworzy się pliki niestandardowe polecenie lub pliki wsadowe, które ustawić zmienne środowiskowe wymagane. Instalator używa następnie te pliki poleceń do tworzenia skrótów menu Windows Start, aby otworzyć okno wiersza polecenia dla deweloperów. Skróty, skonfiguruj zmienne środowiskowe dla określonej kompilacji konfiguracji. W przypadku korzystania z narzędzi wiersza polecenia można uruchomić jeden z tych skrótów lub można otworzyć okno wiersza polecenia zwykły, a następnie uruchom jeden z plików polecenie niestandardowe można samodzielnie ustawić środowisko konfiguracji kompilacji. Aby uzyskać więcej informacji, zobacz [możesz używać zestawu narzędzi MSVC z wiersza polecenia](building-on-the-command-line.md).

Narzędzia wiersza polecenia MSVC używać zmiennych środowiskowych PATH, TMP, INCLUDE, LIB i LIBPATH i również używać innych zmiennych środowiskowych specyficzne dla Twojego zainstalowanych narzędzi, platform i zestawów SDK. Nawet prostą instalację programu Visual Studio mogą ustawiać 20 lub więcej zmiennych środowiskowych. Ponieważ wartości tych zmiennych środowiskowych specyficznych dla instalacji programu i wybraną konfigurację kompilacji i może zostać zmieniona przez uaktualnienia i aktualizacje produktu, zdecydowanie zalecamy użycie skrót do wiersza polecenia dla deweloperów lub jedna z pliki poleceń dostosowane ustawienia, zamiast ustawiać ich w środowisku Windows samodzielnie.

Aby zobaczyć, które zmienne środowiskowe są ustawiane przez skrót do wiersza polecenia dla deweloperów, można użyć polecenia SET. Otwórz okno wiersza polecenia zwykły i przechwycenie danych wyjściowych polecenia SET dla linii bazowej. Otwórz okno wiersza polecenia dla deweloperów i przechwycenie danych wyjściowych polecenia SET dla porównania. Narzędzia porównującego, takiego jak wbudowana w środowisku IDE programu Visual Studio może być przydatne do porównywania zmiennych środowiskowych i zobacz, co jest ustawiana przez wiersz polecenia dla deweloperów. Aby uzyskać informacji na temat określonych zmiennych środowiskowych używane przez kompilatora i konsolidatora, zobacz [zmienne środowiskowe CL](reference/cl-environment-variables.md).

> [!NOTE]
>  Kilka narzędzi wiersza polecenia i opcje narzędzia może wymagać uprawnień administratora. Jeśli masz problemy z uprawnieniami, podczas korzystania z nich, firma Microsoft zaleca Otwórz okno wiersza polecenia dla deweloperów przy użyciu **Uruchom jako Administrator** opcji. W systemie Windows 10, kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla okna wiersza polecenia, a następnie wybierz **więcej**, **Uruchom jako administrator**.

## <a name="see-also"></a>Zobacz także

[Używanie zestawu narzędzi MSVC z poziomu wiersza polecenia](building-on-the-command-line.md)<br/>
[Dokumentacja konsolidatora MSVC](reference/linking.md)<br/>
[Opcje konsolidatora MSVC](reference/linker-options.md)<br/>
[Dokumentacja kompilatora MSVC](reference/compiling-a-c-cpp-program.md)<br/>
[Opcje kompilatora MSVC](reference/compiler-options.md)
