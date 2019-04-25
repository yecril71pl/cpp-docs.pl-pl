---
title: /Fe (Nazwij plik EXE)
ms.date: 11/04/2016
f1_keywords:
- /fe
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
ms.openlocfilehash: 5901ef1997cfea84c97b6d91b30335ff7dbc1d9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292618"
---
# <a name="fe-name-exe-file"></a>/Fe (Nazwij plik EXE)

Określa nazwę i katalog dla pliku .exe lub DLL utworzony przez kompilator.

## <a name="syntax"></a>Składnia

> **/Fe**[_pathname_] **/Fe:** _nazwy ścieżki_

### <a name="arguments"></a>Argumenty

*Nazwa ścieżki*<br/>
Względna lub bezwzględna ścieżka i nazwa pliku podstawowego lub względna lub bezwzględna ścieżka do katalogu lub nazwa pliku podstawowego do użycia dla wygenerowanego pliku wykonywalnego.

## <a name="remarks"></a>Uwagi

**/Fe** opcja umożliwia określenie katalogu wyjściowego, danych wyjściowych, nazwę pliku wykonywalnego lub oba for wygenerowany plik wykonywalny. Jeśli *pathname* kończy się separatorem ścieżki (**&#92;**), zakłada się, aby określić do katalogu wyjściowego. W przeciwnym razie ostatni składnik *pathname* jest używana jako nazwa podstawowa pliku danych wyjściowych, a pozostała część *pathname* Określa katalog danych wyjściowych. Jeśli *pathname* nie ma żadnych separatorów ścieżki, zakłada się, aby określić nazwę pliku wyjściowego w bieżącym katalogu. *Pathname* muszą być ujęte w podwójny cudzysłów (**"**) jeśli zawiera on żadnych znaków, które nie mogą znajdować się w krótkich ścieżkę, taką jak spacje, rozszerzone znaki lub składników ścieżki więcej niż 8 znaków długo.

Gdy **/Fe** nie zostanie podana opcja lub gdy plik podstawowy nie określono nazwy w *pathname*, kompilator nadaje plikowi wyjściowemu domyślną nazwę przy użyciu podstawowej nazwy pierwszego źródła lub obiektu określonego pliku w wierszu polecenia i rozszerzenie .exe lub .dll.

Jeśli określisz [/c (Kompiluj bez konsolidacji)](c-compile-without-linking.md) opcji **/Fe** nie ma wpływu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz **właściwości konfiguracji** > **konsolidatora** > **ogólne** stronę właściwości.

1. Modyfikowanie **plik wyjściowy** właściwości. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="example"></a>Przykład

Następujące polecenie w wierszu kompiluje i łączy wszystkie pliki źródłowe C w bieżącym katalogu. Wynikowy plik wykonywalny nosi nazwę PROCESS.exe i jest tworzony w katalogu "C:\Users\User Name\repos\My Project\bin".

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>Przykład

Następujące polecenie tworzy plik wykonywalny w `C:\BIN` o tej samej nazwie podstawowej jako pierwszego pliku źródłowego w bieżącym katalogu:

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)<br/>
