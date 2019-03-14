---
title: /WINMDDELAYSIGN (podpisz częściowo winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
ms.openlocfilehash: 85698362a753e147a28922db19b456d4d649e55d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421471"
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

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)
