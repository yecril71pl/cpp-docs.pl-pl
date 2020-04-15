---
title: Ustawianie zmiennych ścieżki i środowiska dla kompilacji wiersza polecenia
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
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Ustawianie zmiennych ścieżki i środowiska dla kompilacji wiersza polecenia

Narzędzia do tworzenia wiersza polecenia Microsoft C++ (MSVC) wymagają kilku zmiennych środowiskowych dostosowanych do konfiguracji instalacji i kompilacji. Gdy obciążenie języka C++ jest instalowane przez instalator programu Visual Studio, tworzy dostosowane pliki poleceń lub pliki wsadowe, które ustawiają wymagane zmienne środowiskowe. Instalator następnie używa tych plików poleceń do tworzenia skrótów do menu Start systemu Windows, aby otworzyć okno wiersza polecenia dewelopera. Te skróty skonfigurować zmienne środowiskowe dla określonej konfiguracji kompilacji. Aby użyć narzędzi wiersza polecenia, można uruchomić jeden z tych skrótów lub otworzyć okno wiersza polecenia, a następnie uruchomić jeden z niestandardowych plików poleceń, aby samodzielnie ustawić środowisko konfiguracji kompilacji. Aby uzyskać więcej informacji, zobacz [Używanie zestawu narzędzi MSVC z wiersza polecenia](building-on-the-command-line.md). Aby użyć plików poleceń z prostym wierszem polecenia, zobacz sekcję zatytułowaną [Lokalizacje plików poleceń dewelopera](building-on-the-command-line.md#developer_command_file_locations).

Narzędzia wiersza polecenia MSVC używają zmiennych środowiskowych PATH, TMP, INCLUDE, LIB i LIBPATH, a także używają innych zmiennych środowiskowych specyficznych dla zainstalowanych narzędzi, platform i zestawów SDK. Nawet prosta instalacja programu Visual Studio może ustawić dwadzieścia lub więcej zmiennych środowiskowych. Ponieważ wartości tych zmiennych środowiskowych są specyficzne dla instalacji i wybranej konfiguracji kompilacji i mogą być zmieniane przez aktualizacje lub uaktualnienia produktu, zdecydowanie zaleca się użycie skrótu wiersza polecenia dewelopera lub jednego z niestandardowych plików poleceń, aby je ustawić, zamiast samodzielnie ustawiać je w środowisku systemu Windows.

Aby zobaczyć, które zmienne środowiskowe są ustawiane przez skrót wiersza polecenia dewelopera, można użyć polecenia SET. Otwórz okno wiersza polecenia i przechwyć dane wyjściowe polecenia SET dla linii bazowej. Otwórz okno wiersza polecenia dewelopera i przechwyć dane wyjściowe polecenia SET w celu porównania. Narzędzie różnicowe, takie jak wbudowane w ide programu Visual Studio może być przydatne do porównania zmiennych środowiskowych i zobacz, co jest ustawione przez wiersz polecenia dewelopera. Aby uzyskać informacje na temat określonych zmiennych środowiskowych używanych przez kompilator i konsolidator, zobacz [Zmienne środowiskowe CL](reference/cl-environment-variables.md).

> [!NOTE]
> Kilka narzędzi wiersza polecenia lub opcji narzędzia może wymagać uprawnień administratora. Jeśli masz problemy z uprawnieniami podczas korzystania z nich, zaleca się otwarcie okna wiersza polecenia dewelopera przy użyciu opcji **Uruchom jako administrator.** W systemie Windows 10 kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów dla okna wiersza polecenia, a następnie wybierz pozycję **Więcej**, **Uruchom jako administrator**.

## <a name="see-also"></a>Zobacz też

[Używanie zestawu narzędzi MSVC z poziomu wiersza polecenia](building-on-the-command-line.md)<br/>
[Dokumentacja konsolidatora MSVC](reference/linking.md)<br/>
[Opcje konsolidatora MSVC](reference/linker-options.md)<br/>
[Dokumentacja kompilatora MSVC](reference/compiling-a-c-cpp-program.md)<br/>
[Opcje kompilatora MSVC](reference/compiler-options.md)
