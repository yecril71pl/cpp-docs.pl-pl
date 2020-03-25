---
title: /IGNORE (ignorowanie określonych ostrzeżeń)
ms.date: 11/04/2016
f1_keywords:
- /OVERWRITE
helpviewer_keywords:
- /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
ms.openlocfilehash: c1f9374c168e5b21dfd761f8c984f00ceae9f1bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170621"
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (ignorowanie określonych ostrzeżeń)

```
/IGNORE:warning[,warning]
```

## <a name="parameters"></a>Parametry

*ostrzeżenie*<br/>
Numer ostrzeżenia konsolidatora do pomijania w zakresie od 4000 do 4999.

## <a name="remarks"></a>Uwagi

Domyślnie łącze raportuje wszystkie ostrzeżenia. Określ **/Ignore:** `warning`, aby określić, że konsolidator ma pominąć określony numer ostrzegawczy. Aby zignorować wiele ostrzeżeń, rozdziel je przecinkami.

Konsolidator nie zezwala na ignorowanie niektórych ostrzeżeń. Ta tabela zawiera listę ostrzeżeń, które nie są pomijane przez **/Ignore**:

|Ostrzeżenie konsolidatora||
|--------------------|-|
|LNK4017|Instrukcja `keyword` nie jest obsługiwana dla platformy docelowej; Ignoruj|
|[LNK4044 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|Nierozpoznana opcja "`option`"; Ignoruj|
|LNK4062|element "`option`" jest niezgodny z maszyną docelową "`architecture`"; Opcja zignorowana|
|[LNK4075 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|Ignorowanie "`option1`" ze względu na specyfikację "`option2`"|
|[LNK4086 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|punkt wejścia "`function`" nie jest __stdcall za pomocą "`number`" bajtów argumentów; nie można uruchomić obrazu|
|LNK4088|obraz generowany z powodu opcji/FORCE; nie można uruchomić obrazu|
|[LNK4105 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|nie określono argumentu z opcją "`option`"; ignorowanie przełącznika|
|LNK4203|Wystąpił błąd podczas odczytywania bazy danych programu "`filename`"; Łączenie obiektu bez informacji debugowania|
|[LNK4204 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|"`filename`" nie zawiera informacji debugowania dla przywołującego modułu; Łączenie obiektu bez informacji debugowania|
|[LNK4205 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|element "`filename`" nie ma bieżących informacji debugowania dla przywołującego modułu; Łączenie obiektu bez informacji debugowania|
|[LNK4206 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|nie znaleziono wstępnie skompilowanych informacji o typie; "`filename`" nie jest połączony ani nadpisany; Łączenie obiektu bez informacji debugowania|
|LNK4207|"`filename`" skompilowano/YC/Yu/Z7; nie można utworzyć pliku PDB; Kompiluj ponownie z/Zi; Łączenie obiektu bez informacji debugowania|
|LNK4208|niezgodny format PDB w elemencie "`filename`"; Usuń i Skompiluj ponownie; Łączenie obiektu bez informacji debugowania|
|LNK4209|uszkodzone informacje debugowania; Skompiluj ponownie moduł; Łączenie obiektu bez informacji debugowania|
|[LNK4224 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option` nie jest już obsługiwana; Ignoruj|
|LNK4228|element "`option`" jest nieprawidłowy dla biblioteki DLL; Ignoruj|
|[LNK4229 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|Znaleziono nieprawidłową dyrektywę/`directive`; Ignoruj|

Ogólnie rzecz biorąc, ostrzeżenia konsolidatora, których nie można zignorować, reprezentują błędy kompilacji, błędy wiersza polecenia lub błędy konfiguracji, które należy naprawić.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. W folderze **konsolidatora** wybierz stronę właściwości **wiersza polecenia** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.
