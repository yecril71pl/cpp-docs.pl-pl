---
title: -CGTHREADS (wątki kompilatora) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /CGTHREADS linker option
- -CGTHREADS linker option
- CGTHREADS linker option
ms.assetid: 4b52cfdb-3702-470b-9580-fabeb1417488
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d717ffb3ed135ffe9e6f4ed2c55f925e3f10d86f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720534"
---
# <a name="cgthreads-compiler-threads"></a>/CGTHREADS (wątki kompilatora)

Ustawia liczbę wątków cl.exe na potrzeby generowania optymalizacji i kodu, gdy określono Generowanie łączonych kodów czasowych.

## <a name="syntax"></a>Składnia

```
/CGTHREADS:[1-8]
```

## <a name="arguments"></a>Argumenty

*Numer*<br/>
Maksymalna liczba wątków dla cl.exe, aby korzystać z zakresu od 1 do 8.

## <a name="remarks"></a>Uwagi

**/Cgthreads** opcja określa maksymalną liczbę wątków cl.exe używa równolegle faz optymalizacji i generowania kodu, kompilacji, gdy w czasie konsolidacji generowanie kodu ([opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md)) jest określona. Domyślnie program cl.exe używa cztery wątki tak, jakby **/CGTHREADS:4** zostały określone. Jeśli więcej rdzeni procesora są dostępne, większego `number` wartość może skrócić czas kompilacji.

Można określić wiele poziomów równoległości dla kompilacji. Przełącznik msbuild.exe **/maxcpucount** określa liczbę procesów programu MSBuild, które mogą być uruchamiane równolegle. [/MP (kompilacja z wieloma procesami)](../../build/reference/mp-build-with-multiple-processes.md) flagi kompilatora określa liczbę procesów cl.exe, jednocześnie kompilowane do plików źródłowych. [/Cgthreads](../../build/reference/cgthreads-code-generation-threads.md) — opcja kompilatora określa liczbę wątków używanych przez każdy proces cl.exe. Ponieważ procesor można uruchamiać tylko tyle wątków w tym samym czasie, są rdzenie procesora, nie jest to przydatne do określenia większe wartości dla wszystkich tych opcji, w tym samym czasie i mogą być unikają szkodliwych dla produkcji. Aby uzyskać więcej informacji na temat sposobu tworzenia projektów wykonywane równolegle, zobacz [tworzenie wielu projektów w sposób równoległy](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji**, **konsolidatora** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/cgthreads:**`number`, gdzie `number` jest wartością z zakresu od 1 do 8, a następnie wybierz **OK**.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje konsolidatora](../../build/reference/linker-options.md)<br/>
[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)