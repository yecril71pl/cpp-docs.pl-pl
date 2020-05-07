---
title: Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia
ms.custom: conceptual
ms.date: 07/24/2019
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
ms.openlocfilehash: aeafe806e5d29b89c243586974814aa7cfc16d1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335585"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia

Narzędzia do kompilowania wiersza polecenia w języku Microsoft C++ (MSVC) wymagają kilku zmiennych środowiskowych, które są dostosowane do instalacji i konfiguracji kompilacji. Gdy obciążenie języka C++ jest instalowane przez Instalatora programu Visual Studio, tworzy dostosowane pliki poleceń lub pliki wsadowe, które ustawiają wymagane zmienne środowiskowe. Instalator następnie używa tych plików poleceń do tworzenia skrótów dla menu Start systemu Windows, aby otworzyć okno wiersza polecenia dla deweloperów. Te skróty służą do konfigurowania zmiennych środowiskowych dla określonej konfiguracji kompilacji. Jeśli chcesz użyć narzędzi wiersza polecenia, możesz uruchomić jeden z tych skrótów lub otworzyć zwykłe okno wiersza polecenia, a następnie uruchomić jeden z niestandardowych plików poleceń, aby samodzielnie ustawić środowisko konfiguracji kompilacji. Aby uzyskać więcej informacji, zobacz Korzystanie z zestawu [narzędzi MSVC w wierszu polecenia](building-on-the-command-line.md). Aby użyć plików poleceń z zwykłym wierszem polecenia, zapoznaj się z sekcją zatytułowaną [lokalizacje plików poleceń deweloperskich](building-on-the-command-line.md#developer_command_file_locations).

Narzędzia wiersza polecenia MSVC używają zmiennych środowiskowych PATH, TMP, INCLUDE, LIB i LIBPATH, a także używają innych zmiennych środowiskowych specyficznych dla zainstalowanych narzędzi, platform i zestawów SDK. Nawet prosta instalacja programu Visual Studio może ustawiać dwadzieścia lub więcej zmiennych środowiskowych. Ponieważ wartości tych zmiennych środowiskowych są specyficzne dla danej instalacji i wybranej konfiguracji kompilacji i można je zmienić przy użyciu aktualizacji lub uaktualnień produktu, zdecydowanie zalecamy użycie skrótu wiersza polecenia dla deweloperów lub jednego z niestandardowych plików poleceń, aby je ustawić, zamiast ustawiać je w środowisku systemu Windows.

Aby zobaczyć, które zmienne środowiskowe są ustawiane przez skrót do wiersza polecenia dla deweloperów, można użyć polecenia SET. Otwórz proste okno wiersza polecenia i Przechwyć dane wyjściowe polecenia SET dla linii bazowej. Otwórz okno wiersza polecenia dla deweloperów i Przechwyć dane wyjściowe polecenia SET do porównania. Narzędzie diff, takie jak wbudowane w środowisko IDE programu Visual Studio, może być przydatne do porównania zmiennych środowiskowych i zobacz, co jest ustawione w wierszu polecenia dewelopera. Aby uzyskać informacje o określonych zmiennych środowiskowych używanych przez kompilator i konsolidator, zobacz [zmienne środowiskowe CL](reference/cl-environment-variables.md).

> [!NOTE]
> Kilka narzędzi wiersza polecenia lub opcji narzędzi może wymagać uprawnień administratora. Jeśli masz problemy z uprawnieniami podczas ich używania, zalecamy otwarcie okna wiersza polecenia dla deweloperów za pomocą opcji **Uruchom jako administrator** . W systemie Windows 10 kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla okna wiersza polecenia, a następnie wybierz polecenie **więcej**, **Uruchom jako administrator**.

## <a name="see-also"></a>Zobacz też

[Używanie zestawu narzędzi MSVC z poziomu wiersza polecenia](building-on-the-command-line.md)<br/>
[Dokumentacja konsolidatora MSVC](reference/linking.md)<br/>
[Opcje konsolidatora MSVC](reference/linker-options.md)<br/>
[Dokumentacja kompilatora MSVC](reference/compiling-a-c-cpp-program.md)<br/>
[Opcje kompilatora MSVC](reference/compiler-options.md)
