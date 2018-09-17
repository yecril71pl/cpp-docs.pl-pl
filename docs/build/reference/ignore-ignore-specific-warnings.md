---
title: -IGNORE (Ignorowanie określonych ostrzeżeń) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /OVERWRITE
dev_langs:
- C++
helpviewer_keywords:
- /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aee498951c01c332dffe720dbd6e3b77c8121aa5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705864"
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (ignorowanie określonych ostrzeżeń)

```
/IGNORE:warning[,warning]
```

## <a name="parameters"></a>Parametry

*ostrzeżenie*<br/>
Liczba konsolidatora ostrzeżenie do pomijania w zakresie 4000 do 4999.

## <a name="remarks"></a>Uwagi

Domyślnie łącza raportuje wszystkie ostrzeżenia. Określ **/IGNORE:** `warning` stwierdzić, konsolidator, aby pominąć określony numer ostrzeżenia. Aby zignorować wiele ostrzeżeń, numerów ostrzeżeń, które należy oddzielić przecinkami.

Konsolidator nie zezwala na kilka ostrzeżeń, które mają być ignorowane. Poniższa tabela zawiera listę ostrzeżeń, które nie są pomijane przez **/IGNORE**:

|Ostrzeżenia konsolidatora||
|--------------------|-|
|LNK4017|`keyword` Instrukcja nie jest obsługiwana dla platformy docelowej; ignorowane|
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|Nierozpoznana opcja "`option`"; zignorowano|
|LNK4062|"`option`"nie jest zgodna z"`architecture`" maszyna docelowa; opcja została zignorowana|
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|ignorowanie "`option1`" ze względu na"`option2`" Specyfikacja|
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|punkt wejścia "`function`"jest inny niż __stdcall z"`number`" bajtami argumentów; uruchomienie obrazu może nie|
|LNK4088|Obraz jest generowany ze względu opcji/Force; Obraz może nie działać.|
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|Brak argumentu określony za pomocą opcji "`option`"; ignorowanie przełącznika|
|LNK4203|Wystąpił błąd podczas odczytu z bazy danych programu "`filename`"; skonsolidowany obiektu bez informacji debugowania|
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|"`filename`" nie ma informacji debugowania dla przywołującego modułu; skonsolidowany obiektu bez informacji debugowania|
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|"`filename`" nie ma bieżących informacji debugowania dla przywołującego modułu; skonsolidowany obiektu bez informacji debugowania|
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|informacje o wstępnie skompilowanym typie nie znaleziono; "`filename`" nie połączone lub zastąpione; skonsolidowany obiektu bez informacji debugowania|
|LNK4207|"`filename`" skompilowany /Yc /Yu z/z7; nie można utworzyć pliku PDB; Skompiluj ponownie z opcją /Zi; obiekt zostanie skonsolidowany bez informacji debugowania|
|LNK4208|niezgodny format PDB w "`filename`"; Usuń i ponownie skompiluj; skonsolidowany obiektu bez informacji debugowania|
|LNK4209|informacje debugowania uszkodzone; Skompiluj ponownie moduł; skonsolidowany obiektu bez informacji debugowania|
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option` nie jest już obsługiwany; ignorowane|
|LNK4228|"`option`" nieprawidłowe dla biblioteki DLL; zignorowano|
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|nieprawidłową dyrektywę /`directive` znaleziono; zignorowano|

Ogólnie rzecz biorąc ostrzeżenia konsolidatora, które nie mogą zostać pominięte reprezentują błędy kompilacji, błędy wiersza polecenia lub błędy konfiguracji, które powinno rozwiązać.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. W **konsolidatora** folderu, wybierz **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.