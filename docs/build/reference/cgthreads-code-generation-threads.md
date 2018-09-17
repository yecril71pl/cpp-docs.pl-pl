---
title: -cgthreads (wątki generowania kodu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /cgthreads
dev_langs:
- C++
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb6849a4b30e903d05b5ac3d37fce558074110a5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719631"
---
# <a name="cgthreads-code-generation-threads"></a>/cgthreads (wątki generowania kodu)

Ustawia liczbę wątków cl.exe na potrzeby generowania optymalizacji i kodu.

## <a name="syntax"></a>Składnia

```
/cgthreads[1-8]
```

## <a name="arguments"></a>Argumenty

*Numer*<br/>
Maksymalna liczba wątków dla cl.exe, aby korzystać z zakresu od 1 do 8.

## <a name="remarks"></a>Uwagi

**/Cgthreads** opcja określa maksymalną liczbę wątków cl.exe używa równolegle do optymalizacji i kodu generowania fazy kompilacji. Należy zauważyć, że może istnieć bez spacji między **/cgthreads** i `number` argumentu. Domyślnie program cl.exe używa cztery wątki tak, jakby **/cgthreads4** zostały określone. Jeśli więcej rdzeni procesora są dostępne, większego `number` wartość może skrócić czas kompilacji. Ta opcja jest szczególnie przydatne w połączeniu z [/GL (Optymalizacja Całoprogramowa)](../../build/reference/gl-whole-program-optimization.md).

Można określić wiele poziomów równoległości dla kompilacji. Przełącznik msbuild.exe **/maxcpucount** określa liczbę procesów programu MSBuild, które mogą być uruchamiane równolegle. [/MP (kompilacja z wieloma procesami)](../../build/reference/mp-build-with-multiple-processes.md) flagi kompilatora określa liczbę procesów cl.exe, jednocześnie kompilowane do plików źródłowych. **/Cgthreads** opcja określa liczbę wątków używanych przez każdy proces cl.exe. Ponieważ procesor można uruchamiać tylko tyle wątków w tym samym czasie, są rdzenie procesora, nie jest to przydatne do określenia większe wartości dla wszystkich tych opcji, w tym samym czasie i mogą być unikają szkodliwych dla produkcji. Aby uzyskać więcej informacji na temat sposobu tworzenia projektów wykonywane równolegle, zobacz [tworzenie wielu projektów w sposób równoległy](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji**, **C/C++** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/cgthreads**`N`, gdzie `N` jest wartością z zakresu od 1 do 8, a następnie wybierz **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)