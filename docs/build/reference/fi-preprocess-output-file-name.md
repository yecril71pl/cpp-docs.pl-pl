---
title: /Fi (Przetwarzaj wstępnie nazwę pliku wyjściowego)
ms.date: 08/12/2020
f1_keywords:
- /Fi
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
ms.openlocfilehash: 82bf09a8f01f656f90ad9971530b05f108fc95a4
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561092"
---
# <a name="fi-preprocess-output-file-name"></a>`/Fi` (Przetwarzaj wstępnie nazwę pliku wyjściowego)

Określa nazwę pliku wyjściowego, do którego opcja kompilatora [ `/P` (preproces do pliku)](p-preprocess-to-a-file.md) zapisuje wstępnie przetworzone dane wyjściowe.

## <a name="syntax"></a>Składnia

> **`/Fi`**_`pathname`_

### <a name="parameters"></a>Parametry

*`pathname`*\
Ścieżka względna lub bezwzględna i nazwa pliku wyjściowego utworzonego przez **`/P`** opcję kompilatora. Lub ścieżka katalogu dla *`.i`* plików wyjściowych, gdy jest określony więcej niż jeden plik wejściowy. Nie umieszczaj spacji między **`/Fi`** opcją i *`pathname`* .

## <a name="remarks"></a>Uwagi

Użyj **`/Fi`** opcji kompilatora w połączeniu z **`/P`** opcją kompilatora. Jeśli **`/P`** nie jest określony, powoduje, że **`/Fi`** Ostrzeżenie wiersza polecenia D9007.

Jeśli określisz tylko ścieżkę katalogu (ścieżkę kończącą się ukośnikiem odwrotnym **`\`** ) dla *`pathname`* parametru, podstawowa nazwa pliku źródłowego jest używana jako nazwa podstawowa wstępnie przetworzonego pliku wyjściowego. *`pathname`* Parametr nie wymaga określonego rozszerzenia nazwy pliku. Jednak rozszerzenie ". i" jest używane, jeśli nie określisz rozszerzenia nazwy pliku.

### <a name="example"></a>Przykład

Następujące wstępnie przetwarzane wiersze polecenia *`PROGRAM.cpp`* , zachowuje komentarze, dodaje [`#line`](../../preprocessor/hash-line-directive-c-cpp.md) dyrektywy i zapisuje wynik do *`MYPROCESS.i`* pliku:

```cmd
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

Ten wiersz polecenia wstępnie przetwarza *`main.cpp`* i *`helper.cpp`* *`main.i`* *`helper.i`* w podkatalogu o nazwie *`preprocessed`* :

```cmd
CL /P /Fi".\\preprocessed\\" main.cpp helper.cpp
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz plik źródłowy lub okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracji preprocesora**C/C++**  >  **Preprocessor** .

1. Ustaw dla **procesu wstępnego właściwość pliku** na **wartość tak**.

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Wprowadź **`/Fi`** opcję kompilatora i *`pathname`* w polu **dodatkowe opcje** . Podczas ustawiania tej właściwości dla projektu należy określić tylko ścieżkę katalogu, a nie nazwę pliku.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[`/P` (Przetwarzaj wstępnie do pliku)](p-preprocess-to-a-file.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)
