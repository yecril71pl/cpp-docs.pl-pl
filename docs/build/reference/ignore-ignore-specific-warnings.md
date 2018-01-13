---
title: "-Ignoruj (Ignorowanie określonych ostrzeżeń) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /OVERWRITE
dev_langs: C++
helpviewer_keywords: /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0d8815438ce56629bd120c30b0d0db9fef96916d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (ignorowanie określonych ostrzeżeń)
```  
/IGNORE:warning[,warning]  
```  
  
## <a name="parameters"></a>Parametry  
 `warning`  
 Liczba konsolidator Ostrzeżenie można pominąć w zakresie 4000 do 4999.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie łącze raportuje wszystkie ostrzeżenia. Określ **/Ignoruj:** `warning` mówić konsolidator, aby pominąć na określony numer ostrzeżenia. Aby zignorować wielu ostrzeżeń, numerów ostrzeżeń, które należy oddzielić przecinkami.  
  
 Konsolidator nie zezwalaj na ostrzeżenia mają być ignorowane. Poniższa tabela zawiera ostrzeżenia, które nie są pomijane przez **/Ignoruj**:  
  
|Ostrzeżenia konsolidatora||  
|--------------------|-|  
|LNK4017|`keyword`Instrukcja nie jest obsługiwana dla platformy docelowej; ignorowane|  
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|nierozpoznaną opcję "`option`"; zignorowano|  
|LNK4062|"`option`"nie jest zgodne z"`architecture`" maszyna docelowa; opcja została zignorowana|  
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|ignorowanie "`option1`"z powodu"`option2`" Specyfikacja|  
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|punkt wejścia "`function`"nie jest __stdcall z"`number`" bajtami argumentów; uruchomienie obrazu może nie|  
|LNK4088|Obraz jest generowany ze względu opcji/Force; Obraz może nie działać.|  
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|Brak argumentu określona z opcją "`option`"; zignorował przełącznika|  
|LNK4203|Błąd odczytu bazy danych programu "`filename`"; Konsolidacja obiekt zostanie skonsolidowany bez informacji debugowania|  
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|"`filename`" nie ma informacji debugowania dla przywołującego modułu; Konsolidacja obiekt zostanie skonsolidowany bez informacji debugowania|  
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|"`filename`" nie ma bieżących informacji debugowania dla przywołującego modułu; Konsolidacja obiekt zostanie skonsolidowany bez informacji debugowania|  
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|informacje o wstępnie skompilowanym typie nie można odnaleźć; "`filename`" nie połączone lub zastąpione; Konsolidacja obiekt zostanie skonsolidowany bez informacji debugowania|  
|LNK4207|"`filename`" skompilowany /Yc /Yu/z7; nie można utworzyć pliku PDB; Skompiluj ponownie z opcją /Zi; obiekt zostanie skonsolidowany bez informacji debugowania|  
|LNK4208|niezgodny format PDB w "`filename`"; usunąć i skompiluj ponownie; obiekt zostanie skonsolidowany bez informacji debugowania|  
|LNK4209|informacje debugowania uszkodzone; Skompiluj ponownie moduł; Łączenie obiekt zostanie skonsolidowany bez informacji debugowania|  
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option`nie jest już obsługiwany; ignorowane|  
|LNK4228|"`option`" nieprawidłowy dla biblioteki DLL; zignorowano|  
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|Nieprawidłowa dyrektywa /`directive` znaleziono; zignorowano|  
  
 Ogólnie rzecz biorąc nie można zignorować ostrzeżenia konsolidatora reprezentuje błędy kompilacji, błędy wiersza polecenia lub błędy konfiguracji, które należy naprawić.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  W **konsolidatora** folderu, wybierz opcję **wiersza polecenia** strony właściwości.  
  
3.  Modyfikowanie **dodatkowe opcje** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.