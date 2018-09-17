---
title: -NOLOGO (Pomijaj transparent startowy) (konsolidator) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
dev_langs:
- C++
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 405cfd08b681d8b48343bae5055f5be9cf23dadb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707580"
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO (Pomiń transparent początkowy) (Konsolidator)

```
/NOLOGO
```

## <a name="remarks"></a>Uwagi

Opcja/nologo uniemożliwia wyświetlanie liczby o prawach autorskich komunikat i wersji.

Ta opcja powoduje również pominięcie wyświetlania pliku polecenia. Aby uzyskać więcej informacji, zobacz [pliki poleceń LINK](../../build/reference/link-command-files.md).

Domyślnie te informacje są wysyłane przez konsolidator, aby w oknie danych wyjściowych. W wierszu polecenia jest wysyłane do wyjścia standardowego i mogą zostać przekierowane do pliku.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Ta opcja powinna być używana tylko z poziomu wiersza polecenia.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Nie można zmienić tę opcję konsolidatora w programowo.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)