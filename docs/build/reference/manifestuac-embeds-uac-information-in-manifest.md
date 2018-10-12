---
title: -MANIFESTUAC (osadza informacje UAC w manifeście) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
dev_langs:
- C++
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8c8c3cc219f0cf658dc2669ccc10adf3aba55bd
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163533"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC (Osadza informacje UAC w manifeście)

Określa, czy informacje kontroli konta użytkownika (UAC) są osadzone w manifeście programu.

## <a name="syntax"></a>Składnia

```
/MANIFESTUAC
/MANIFESTUAC:NO
/MANIFESTUAC:fragment
/MANIFESTUAC:level=_level
/MANIFESTUAC:uiAccess=_uiAccess
```

### <a name="parameters"></a>Parametry

*Fragment*<br/>
Ciąg, który zawiera `level` i `uiAccess` wartości. Aby uzyskać więcej informacji zobacz sekcję Uwagi w dalszej części tego tematu.

*_level*<br/>
Jedną z *asInvoker*, *highestAvailable*, lub *requireAdministrator*. Wartość domyślna to asInvoker. Aby uzyskać więcej informacji zobacz sekcję Uwagi w dalszej części tego tematu.

*_uiAccess*<br/>
**wartość true,** Jeśli chcesz, aby ją, aby pominąć ochronę UI i dysków danych wejściowych do wyższych uprawnień okien na pulpicie; w przeciwnym razie **false**. Wartość domyślna to **false**. Ustaw **true** tylko dla aplikacji ułatwień dostępu interfejsu użytkownika.

## <a name="remarks"></a>Uwagi

Jeśli określisz wiele opcji /MANIFESTUAC w wierszu polecenia, ostatni z nich wprowadzono ma pierwszeństwo.

Dostępne są następujące opcje dla /MANIFESTUAC:level:

- `asInvoker`Aplikacja zostanie uruchomiona przy użyciu tych samych uprawnień jako proces, który je zainicjował. Aplikacja może być z podwyższonym poziomem uprawnień na wyższy poziom uprawnień, wybierając **Uruchom jako Administrator**.

- highestAvailable: aplikacja zostanie uruchomiona przy użyciu najwyższy poziom uprawnień, który jest to możliwe. Jeśli użytkownik uruchamia aplikację jest członkiem grupy Administratorzy, ta opcja jest taka sama jak requireAdministrator. Jeśli najwyższy poziom uprawnień dostępne jest wyższy niż poziom procesu otwierania, system wyświetli monit o podanie poświadczeń.

- requireAdministrator: aplikacja będzie uruchamiana z uprawnieniami administratora. Użytkownik, który uruchamia aplikację musi być członkiem grupy Administratorzy. Jeśli proces otwierania nie jest uruchomiony z uprawnieniami administracyjnymi, system wyświetli monit o podanie poświadczeń.

Przy użyciu opcji /MANIFESTUAC:fragment, można określić poziom i uiAccess wartości w jednym kroku. Fragment musi mieć następującą formę:

```
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **konsolidatora** węzła.

1. Wybierz **pliku manifestu** stronę właściwości.

1. Modyfikowanie **Włącz (Kontrola konta)**, **poziom wykonywania UAC**, i **ochrona Interfejsu użytkownika obejścia kontroli konta użytkownika** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A>, i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)