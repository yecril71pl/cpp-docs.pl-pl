---
title: /MANIFESTUAC (Osadza informacje UAC w manifeście)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
ms.openlocfilehash: ecc30baabdcb60a030418e9643e2fcffe5ba8281
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813269"
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

*fragment*<br/>
Ciąg, który zawiera `level` i `uiAccess` wartości. Aby uzyskać więcej informacji zobacz sekcję Uwagi w dalszej części tego tematu.

*_level*<br/>
Jedną z *asInvoker*, *highestAvailable*, lub *requireAdministrator*. Wartość domyślna to asInvoker. Aby uzyskać więcej informacji zobacz sekcję Uwagi w dalszej części tego tematu.

*_uiAccess*<br/>
**wartość true,** Jeśli chcesz, aby ją, aby pominąć ochronę UI i dysków danych wejściowych do wyższych uprawnień okien na pulpicie; w przeciwnym razie **false**. Wartość domyślna to **false**. Ustaw **true** tylko dla aplikacji ułatwień dostępu interfejsu użytkownika.

## <a name="remarks"></a>Uwagi

Jeśli określisz wiele opcji /MANIFESTUAC w wierszu polecenia, ostatni z nich wprowadzono ma pierwszeństwo.

Dostępne są następujące opcje dla /MANIFESTUAC:level:

- `asInvoker`: Aplikacja zostanie uruchomiona przy użyciu tych samych uprawnień jako proces, który je zainicjował. Aplikacja może być z podwyższonym poziomem uprawnień na wyższy poziom uprawnień, wybierając **Uruchom jako Administrator**.

- highestAvailable: Aplikacja zostanie uruchomiona przy użyciu najwyższy poziom uprawnień, który jest to możliwe. Jeśli użytkownik uruchamia aplikację jest członkiem grupy Administratorzy, ta opcja jest taka sama jak requireAdministrator. Jeśli najwyższy poziom uprawnień dostępne jest wyższy niż poziom procesu otwierania, system wyświetli monit o podanie poświadczeń.

- requireAdministrator: Aplikacja zostanie uruchomiona z uprawnieniami administratora. Użytkownik, który uruchamia aplikację musi być członkiem grupy Administratorzy. Jeśli proces otwierania nie jest uruchomiony z uprawnieniami administracyjnymi, system wyświetli monit o podanie poświadczeń.

Przy użyciu opcji /MANIFESTUAC:fragment, można określić poziom i uiAccess wartości w jednym kroku. Fragment musi mieć następującą formę:

```
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **konsolidatora** węzła.

1. Wybierz **pliku manifestu** stronę właściwości.

1. Modyfikowanie **Włącz (Kontrola konta)**, **poziom wykonywania UAC**, i **ochrona Interfejsu użytkownika obejścia kontroli konta użytkownika** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A>, i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
