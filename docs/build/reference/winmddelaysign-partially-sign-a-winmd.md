---
title: /WINMDDELAYSIGN (podpisz częściowo winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
ms.openlocfilehash: 5e6eab3fbc40543b634f03da826d3bd3477b9623
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316603"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN (podpisz częściowo winmd)

Umożliwia częściowe podpisywanie pliku metadanych środowiska wykonawczego Windows (.winmd) poprzez umieszczenie klucza publicznego w pliku.

```
/WINMDDELAYSIGN[:NO]
```

## <a name="remarks"></a>Uwagi

Przypomina [/DelaySign](delaysign-partially-sign-an-assembly.md) opcji konsolidatora, która jest stosowana do pliku winmd. Użyj **opcji/winmddelaysign** Jeśli chcesz umieścić klucz publiczny w pliku winmd. Domyślnie konsolidator działa tak, jakby **/winmddelaysign: No** zostały określone; oznacza to, że nie podpisuje plik winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **metadanych Windows** stronę właściwości.

1. W **Windows metadanych opóźnione podpisywanie** listy rozwijanej wybierz odpowiednią opcję.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
