---
title: /MANIFESTUAC (Osadza informacje UAC w manifeście)
ms.date: 06/12/2020
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
ms.openlocfilehash: 96719c6f6f5359afb03b967524b1f65db6dc664a
ms.sourcegitcommit: 8645408c7929558b8162f781776d0908d790a41c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85334935"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC (Osadza informacje UAC w manifeście)

Określa, czy informacje kontroli konta użytkownika (UAC) są osadzone w manifeście programu.

## <a name="syntax"></a>Składnia

> **`/MANIFESTUAC`**\
> **`/MANIFESTUAC:NO`**\
> **`/MANIFESTUAC:`**_`level`_\
> **`/MANIFESTUAC:`**_`uiAccess`_\
> **`/MANIFESTUAC:`**_`fragment`_

### <a name="parameters"></a>Parametry

**`NO`**<br/>
Konsolidator nie osadza informacji UAC w manifeście programu.

*`level`*<br/>
**`level=`** po którym następuje jedna z **`'asInvoker'`** , **`'highestAvailable'`** lub **`'requireAdministrator'`** . Wartość domyślna to **`'asInvoker'`** . Aby uzyskać więcej informacji, zobacz sekcję [uwagi](#remarks) .

*`uiAccess`*<br/>
**`uiAccess='true'`** Jeśli chcesz, aby aplikacja obejść poziomy ochrony interfejsu użytkownika i dane wejściowe dysku do systemu Windows wyższego poziomu uprawnień na pulpicie; w przeciwnym razie **`uiAccess='false'`** . Wartość domyślna to **`uiAccess='false'`** . Ustaw ten argument **`uiAccess='true'`** tylko dla aplikacji ułatwień dostępu interfejsu użytkownika.

*`fragment`*<br/>
Ciąg, który zawiera *`level`* wartości i *`uiAccess`* . Opcjonalnie może być ujęty w podwójne cudzysłowy. Aby uzyskać więcej informacji, zobacz sekcję [uwagi](#remarks) .

## <a name="remarks"></a>Uwagi

W przypadku określenia wielu **`/MANIFESTUAC`** opcji w wierszu polecenia, Ostatnia wprowadzona wartość ma pierwszeństwo.

Dostępne **`/MANIFESTUAC:`** _`level`_ są następujące opcje:

- **`level='asInvoker'`**: Aplikacja jest uruchamiana na tym samym poziomie uprawnień co proces, który go uruchomił. Można podwyższyć poziom uprawnień aplikacji, wybierając pozycję **Uruchom jako administrator**.

- **`level='highestAvailable'`**: Aplikacja jest uruchamiana na najwyższym poziomie uprawnień, który może. Jeśli użytkownik, który uruchamia aplikację, jest członkiem grupy Administratorzy, ta opcja jest taka sama jak **`level='requireAdministrator'`** . Jeśli najwyższy dostępny poziom uprawnień jest wyższy niż poziom procesu otwierania, system będzie monitował o poświadczenia.

- **`level='requireAdministrator'`**: Aplikacja jest uruchamiana przy użyciu uprawnień administratora. Użytkownik, który uruchamia aplikację, musi być członkiem grupy Administratorzy. Jeśli proces otwierania nie jest uruchomiony z uprawnieniami administracyjnymi, system będzie monitował o poświadczenia.

Można określić zarówno *`level`* wartości, jak i *`uiAccess`* w jednym kroku przy użyciu **`/MANIFESTUAC:`** _`fragment`_ opcji. Fragment musi mieć następującą postać:

> **`/MANIFESTUAC:`** \[ **`"`** ] **`level=`** { **`'asInvoker'`** | **`'highestAvailable'`** | **`'requireAdministrator'`** } **`uiAccess=`** { **`'true'`** | **`'false'`** } \[ **`"`** ]

Przykład:

**`/MANIFESTUAC:"level='highestAvailable' uiAccess='true'"`**

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz pozycję **Właściwości konfiguracji**  >  **Linker**  >  Strona właściwości**pliku manifestu** konsolidatora.

1. Zmodyfikuj właściwości **Włącz kontrolę konta użytkownika**, **poziom wykonywania UAC**i **Ignoruj funkcję ochrony użytkownika** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A> , <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A> .

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[MSVC Opcje konsolidatora](linker-options.md)
