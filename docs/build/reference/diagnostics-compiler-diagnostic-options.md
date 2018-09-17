---
title: -diagnostics (Opcje diagnostyki kompilatora) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/11/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
dev_langs:
- C++
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97b5e3ef2e5c14ae93d4fcc3b016f4dbc955edbd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709166"
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/ Diagnostics (Opcje diagnostyki kompilatora)

Użyj **/Diagnostics** opcję kompilatora, aby określić wyświetlanie informacji o lokalizacji błędu i ostrzeżenia.

## <a name="syntax"></a>Składnia

```
/diagnostics:{caret|classic|column}
```

## <a name="remarks"></a>Uwagi

Ta opcja jest obsługiwana w programie Visual Studio 2017 i nowszych wersjach.

**/Diagnostics** — opcja kompilatora kontroluje wyświetlanie błędów i ostrzeżeń.

**/Diagnostics:classic** jest opcja domyślna, która zgłasza tylko numer wiersza, gdzie znaleziono problem.

**/Diagnostics:column** opcja obejmuje również kolumny, gdy problem został znaleziony. Może to pomóc w identyfikacji konstrukcji języka lub znak, który jest przyczyną problemu.

**/Diagnostics:caret** opcja powoduje dołączenie kolumn, gdy problem został znaleziony i umieszcza znak daszka (^) znajdujące się w lokalizacji w wierszu kodu, w których wykryto problem.

Należy pamiętać, że w niektórych przypadkach, kompilator nie może wykryć problem, gdzie się pojawił. Na przykład Brak średnika mogą nie zostać wykryte do momentu napotkano innych, nieoczekiwane symboli. Kolumny są zgłaszane i karetkę znajduje się, gdzie kompilator wykrył, że coś było nie tak, który nie jest zawsze gdzie musisz wprowadzić poprawkę.

**/Diagnostics** opcja jest dostępna, począwszy od programu Visual Studio 2017.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz swój projekt **stron właściwości** okno dialogowe.

2. W obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** folder i wybierz polecenie **ogólne** stronę właściwości.

3. Korzystanie z kontrolki listy rozwijanej w **Format diagnostyki** opcja wyświetlania pola, aby wybrać diagnostyki. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)