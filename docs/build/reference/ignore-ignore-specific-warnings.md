---
title: /IGNORE (ignorowanie określonych ostrzeżeń)
ms.date: 11/04/2016
f1_keywords:
- /OVERWRITE
helpviewer_keywords:
- /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
ms.openlocfilehash: 4ed87a1a12bea189f56545cf5256351a29977643
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040265"
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (ignorowanie określonych ostrzeżeń)

```
/IGNORE:warning[,warning]
```

## <a name="parameters"></a>Parametry

*wyświetlania*<br/>
Numer ostrzeżenia konsolidatora do pomijania w zakresie od 4000 do 4999.

## <a name="remarks"></a>Uwagi

Domyślnie łącze raportuje wszystkie ostrzeżenia. Określ **/Ignore:** `warning` , aby określić, że konsolidator ma pominąć określony numer ostrzegawczy. Aby zignorować wiele ostrzeżeń, rozdziel je przecinkami.

Konsolidator nie zezwala na ignorowanie niektórych ostrzeżeń. Ta tabela zawiera listę ostrzeżeń, które nie są pomijane przez **/Ignore**:

| Ostrzeżenie konsolidatora | Wiadomość |
|--------------------|-|
|LNK4017|`keyword` Instrukcja nie jest obsługiwana dla platformy docelowej; Ignoruj|
|[LNK4044 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|Nierozpoznana opcja " `option` "; zignorowano|
|LNK4062|element " `option` " jest niezgodny z `architecture` maszyną docelową ""; opcja została zignorowana|
|[LNK4075 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|ignorowanie `option1` specyfikacji "" ze względu na " `option2` "|
|[LNK4086 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|punkt wejścia " `function` " nie jest __stdcall z " `number` " bajtami argumentów; uruchomienie obrazu może nie być możliwe|
|LNK4088|obraz generowany z powodu opcji/FORCE; nie można uruchomić obrazu|
|[LNK4105 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|nie określono argumentu z opcją " `option` "; ignorowanie przełącznika|
|LNK4203|Wystąpił błąd podczas odczytywania bazy danych programu " `filename` "; obiekt zostanie skonsolidowany bez informacji debugowania|
|[LNK4204 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|element " `filename` " nie ma informacji debugowania dla przywołującego modułu; obiekt zostanie skonsolidowany bez informacji debugowania|
|[LNK4205 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|element " `filename` " nie ma bieżących informacji debugowania dla odwołującego modułu; obiekt zostanie skonsolidowany bez informacji debugowania|
|[LNK4206 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|nie znaleziono wstępnie skompilowanych informacji o typie; element " `filename` " nie jest połączony ani nadpisany; obiekt zostanie skonsolidowany bez informacji debugowania|
|LNK4207|" `filename` skompilowano/YC/Yu/Z7; nie można utworzyć pliku PDB; Skompiluj ponownie za pomocą/Zi; obiekt zostanie skonsolidowany bez informacji debugowania|
|LNK4208|niezgodny format PDB w elemencie " `filename` "; Usuń i Skompiluj ponownie; obiekt zostanie skonsolidowany bez informacji debugowania|
|LNK4209|uszkodzone informacje debugowania; Skompiluj ponownie moduł; Łączenie obiektu bez informacji debugowania|
|[LNK4224 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option` nie jest już obsługiwane; Ignoruj|
|LNK4228|element " `option` " jest nieprawidłowy dla biblioteki DLL; zignorowano|
|[LNK4229 narzędzi KONSOLIDATORA](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|Nieprawidłowa dyrektywa/ `directive` znaleziono; zignorowano|

Ogólnie rzecz biorąc, ostrzeżenia konsolidatora, których nie można zignorować, reprezentują błędy kompilacji, błędy wiersza polecenia lub błędy konfiguracji, które należy naprawić.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. W folderze **konsolidatora** wybierz stronę właściwości **wiersza polecenia** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.
