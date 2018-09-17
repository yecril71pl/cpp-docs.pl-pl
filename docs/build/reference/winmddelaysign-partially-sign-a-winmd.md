---
title: -WINMDDELAYSIGN (Podpisz częściowo winmd) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
dev_langs:
- C++
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b31f6ae5baf9aadbb40b4b45f532b344b6b2e037
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723856"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN (podpisz częściowo winmd)

Umożliwia częściowe podpisywanie pliku metadanych środowiska wykonawczego Windows (.winmd) poprzez umieszczenie klucza publicznego w pliku.

```
/WINMDDELAYSIGN[:NO]
```

## <a name="remarks"></a>Uwagi

Przypomina [/DelaySign](../../build/reference/delaysign-partially-sign-an-assembly.md) opcji konsolidatora, która jest stosowana do pliku winmd. Użyj **opcji/winmddelaysign** Jeśli chcesz umieścić klucz publiczny w pliku winmd. Domyślnie konsolidator działa tak, jakby **/winmddelaysign: No** zostały określone; oznacza to, że nie podpisuje plik winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **metadanych Windows** stronę właściwości.

1. W **Windows metadanych opóźnione podpisywanie** listy rozwijanej wybierz odpowiednią opcję.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)