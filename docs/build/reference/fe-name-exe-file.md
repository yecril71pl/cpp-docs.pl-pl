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
ms.openlocfilehash: f0bd8f3a96555cc29d06f74fb44a73bbed32889b
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825581"
---
# <a name="fe-name-exe-file"></a>/Fe (Nazwij plik EXE)

Określa nazwę i katalog dla pliku exe lub DLL utworzonego przez kompilator.

## <a name="syntax"></a>Składnia

> **/Fe**[_nazwa_ścieżki_] \
> **/Fe:** _Nazwa ścieżki_

### <a name="arguments"></a>Argumenty

*ścieżki*<br/>
Ścieżka względna lub bezwzględna i podstawowa nazwa pliku albo względna lub bezwzględna ścieżka do katalogu lub podstawowa nazwa pliku do użycia dla wygenerowanego pliku wykonywalnego.

## <a name="remarks"></a>Uwagi

Opcja **/Fe** umożliwia określenie katalogu wyjściowego, wyjściowej nazwy pliku wykonywalnego lub obu — dla wygenerowanego pliku wykonywalnego. Jeśli *Nazwa ścieżki* zostanie zakończona w separatorze ścieżki (**&#92;**), zakłada się, że jest określony tylko katalog wyjściowy. W przeciwnym razie ostatni składnik nazwy *ścieżki* jest używany jako nazwa podstawowa pliku wyjściowego, a reszta *ścieżki* określa katalog wyjściowy. Jeśli nazwa *ścieżki* nie ma żadnych separatorów ścieżki, zakłada się, że nazwa pliku wyjściowego jest określona w bieżącym katalogu. *Nazwa ścieżki* musi być ujęta w podwójne cudzysłowy (**"**), jeśli zawiera znaki, które nie mogą znajdować się w krótkiej ścieżce, takie jak spacje, znaki rozszerzone lub składniki ścieżki więcej niż osiem znaków.

Jeśli opcja **/Fe** nie została określona lub gdy nazwa podstawowa pliku nie została określona w nazwie *ścieżki*, kompilator nadaje plikowi wyjściowemu nazwę domyślną przy użyciu podstawowej nazwy pierwszego pliku źródłowego lub obiektu określonego w wierszu polecenia i rozszerzenie. exe lub. dll.

W przypadku określenia opcji [/c (Kompiluj bez konsolidacji)](c-compile-without-linking.md) **/Fe** nie ma żadnego wpływu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz stronę właściwości**Ogólne**  > **konsolidatora** >  **Właściwości konfiguracji**.

1. Zmodyfikuj właściwość **pliku wyjściowego** . Wybierz **przycisk OK** , aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="example"></a>Przykład

Poniższy wiersz polecenia kompiluje i łączy wszystkie pliki źródłowe C w bieżącym katalogu. Powstały plik wykonywalny nosi nazwę PROCESS. exe i został utworzony w katalogu "C:\Users\User Name\repos\My Project\bin".

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>Przykład

Poniższy wiersz polecenia tworzy plik wykonywalny w programie `C:\BIN` z tą samą nazwą bazową jak pierwszy plik źródłowy w bieżącym katalogu:

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Określanie nazwy ścieżki](specifying-the-pathname.md)<br/>
