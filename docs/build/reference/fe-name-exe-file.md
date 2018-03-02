---
title: -Fe (Nazwij plik EXE) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /fe
dev_langs:
- C++
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d74892ef670ed53e68701730fdb71554989a495c
ms.sourcegitcommit: d24de38f9da844f824acb9d200a3f263077145fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="fe-name-exe-file"></a>/Fe (Nazwij plik EXE)

Określa nazwę i katalog dla pliku .exe lub DLL utworzony przez kompilator.

## <a name="syntax"></a>Składnia

> **/Fe**[_pathname_]  
> **/ Fe:** _nazwy ścieżki_  

### <a name="arguments"></a>Argumenty

*Nazwa ścieżki*<br/>
Względna lub bezwzględna ścieżka i nazwa pliku podstawowego lub względna lub bezwzględna ścieżka do katalogu lub nazwa pliku podstawowego do użycia dla wygenerowanego pliku wykonywalnego.

## <a name="remarks"></a>Uwagi

**/Fe** opcji można określić katalog wyjściowy, nazwa pliku wykonywalnego dla danych wyjściowych lub dla wygenerowanego pliku wykonywalnego. Jeśli *pathname* kończy się separatorem ścieżki (**&#92;**), zakłada się, aby określić do katalogu wyjściowego. W przeciwnym razie ostatni składnik *pathname* jest używana jako Nazwa podstawowego pliku wyjściowego, a pozostałe *pathname* katalog wyjściowy. Jeśli *pathname* nie ma żadnych separatorów ścieżek, zakłada się, aby określić nazwę pliku wyjściowego w bieżącym katalogu. *Pathname* musi być ujęta w cudzysłów (**"**) zawiera znaki, które nie mogą być w krótkiej ścieżki, takie jak spacje, rozszerzony znaków lub składników ścieżki więcej niż osiem znaków długie.

Gdy **/Fe** nie określono opcji lub gdy plik podstawowy nazwa nie jest określona w *pathname*, kompilator zapewnia pliku wyjściowego domyślną nazwę podstawową nazwę pierwszego źródła lub obiektu określonego pliku w wierszu polecenia i rozszerzenie .exe lub dll.

Jeśli określisz [/c (Kompiluj bez konsolidacji)](c-compile-without-linking.md) opcji **/Fe** nie ma wpływu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Otwórz **właściwości konfiguracji** > **konsolidatora** > **ogólne** strony właściwości.

1. Modyfikowanie **pliku wyjściowego** właściwości. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="example"></a>Przykład

Następujące polecenie w wierszu kompiluje i łączy wszystkie pliki źródłowe C w bieżącym katalogu. Wynikowy plik wykonywalny nosi nazwę PROCESS.exe i jest tworzone w katalogu "C:\Users\User Name\repos\My Project\bin".

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>Przykład

Następujące polecenie w wierszu tworzy plik wykonywalny w `C:\BIN` o takiej samej nazwie podstawowej jako pierwszy pliku źródłowego w bieżącym katalogu:

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](../../build/reference/output-file-f-options.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)<br/>
