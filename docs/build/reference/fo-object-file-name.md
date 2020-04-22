---
title: /Fo (Nazwa pliku obiektu)
description: Przewodnik po opcji kompilatora microsoft C++ /Fo (nazwa pliku obiektu) w programie Visual Studio.
ms.date: 04/20/2020
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: cd22ba745128fe1df67853d98c1495491b9ca840
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748977"
---
# <a name="fo-object-file-name"></a>/Fo (Nazwa pliku obiektu)

Określa nazwę pliku*`.obj`* lub katalogu obiektu ( ), który ma być używany zamiast domyślnego.

## <a name="syntax"></a>Składnia

> **`/Fo`**_Nazwa_ścieżki_

## <a name="remarks"></a>Uwagi

Za pomocą **`/Fo`** opcji kompilatora można ustawić katalog wyjściowy dla wszystkich plików obiektów generowanych przez polecenie kompilatora CL. Można go też użyć do zmiany nazwy pliku pojedynczego obiektu.

Domyślnie pliki obiektów wygenerowane przez kompilator są umieszczane w bieżącym katalogu. Otrzymują podstawową nazwę pliku źródłowego i *`.obj`* rozszerzenie.

Aby użyć **`/Fo`** opcji zmiany nazwy pliku obiektu, należy określić wyjściową nazwę pliku jako argument *nazwy ścieżki.* Po zmianie nazwy pliku obiektu można użyć dowolnej nazwy i rozszerzenia, ale *`.obj`* zalecana konwencja jest używana . Kompilator generuje błąd wiersza polecenia D8036, jeśli **`/Fo`** określisz nazwę pliku, gdy określono więcej niż jeden plik źródłowy do skompilowania.

Aby użyć **`/Fo`** opcji ustawiania katalogu wyjściowego dla wszystkich plików obiektów utworzonych przez polecenie CL, należy określić katalog jako argument *nazwy ścieżki.* Katalog jest wskazywany przez ukośnik końcowy w argumie *pathname.* Określony katalog musi istnieć; nie jest tworzony automatycznie.

## <a name="example"></a>Przykład

Poniższy wiersz polecenia tworzy plik obiektu o nazwie *sample.obj* w istniejącym * \\katalogu, pośrednim*, na dysku D.

```cmd
CL /Fo"D:\intermediate\" /EHsc /c sample.cpp
```

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Ustawianie opcji w programie Visual Studio lub programowo

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Wybierz stronę **właściwości Właściwości** > konfiguracji**C/C++** > **Pliki wyjściowe.**

1. Zmodyfikuj właściwość **Nazwa pliku obiektu,** aby ustawić katalog wyjściowy. W IDE plik obiektu musi mieć *`.obj`* rozszerzenie .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)
