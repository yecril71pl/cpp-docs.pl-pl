---
title: -CLRTHREADATTRIBUTE (ustaw atrybut wątku CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
dev_langs:
- C++
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bea5b75c9f0691ef74c35ed405d64fc3389c4fcd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705799"
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE (Ustaw atrybut wątku CTR)

Określ jawnie atrybut wątkowości dla punktu wejścia programu CLR.

## <a name="syntax"></a>Składnia

```
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}
```

#### <a name="parameters"></a>Parametry

**MTA**<br/>
Stosuje atrybut MTAThreadAttribute do punktu wejścia programu.

**BRAK**<br/>
Taka sama jak /CLRTHREADATTRIBUTE nie został podany.  Umożliwia języka wspólnego środowiska uruchomieniowego (CLR) Ustaw domyślnego atrybutu wątkowości.

**STA.**<br/>
Stosuje atrybut STAThreadAttribute do punktu wejścia programu.

## <a name="remarks"></a>Uwagi

Ustawienie atrybutu wątku jest prawidłowy tylko podczas kompilowania .exe, jak ma to wpływ na punkt wejścia w wątku głównym.

Jeśli używasz domyślnego punktu wejścia (main lub wmain, na przykład) Określ model wątkowości, za pomocą /CLRTHREADATTRIBUTE lub przez umieszczenie wątkowości atrybutu (STAThreadAttribute lub MTAThreadAttribute) na domyślnej funkcji wpis.

Korzystając z punktem wejścia innych niż domyślne, określ model wątkowy przy użyciu /CLRTHREADATTRIBUTE lub umieszczając wątkowości atrybutu na funkcji wejścia innych niż domyślne, a następnie określ punkt wejścia innych niż domyślne, za pomocą [/Entry](../../build/reference/entry-entry-point-symbol.md) .

Jeśli model wątkowy określona w kodzie źródłowym nie zgadza się z modelu wątkowości określony za pomocą /CLRTHREADATTRIBUTE, konsolidator zignoruje /CLRTHREADATTRIBUTE i zastosowanie modelu wątkowości, określona w kodzie źródłowym.

Będzie trzeba użyć pojedynczego wątków na przykład CLR program udostępnia obiekt COM, który korzysta z wątków w jednym.  Jeśli Twoje CLR program używa wielowątkowości, nie można go hosta obiektu COM, który korzysta z wątków w jednym.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **konsolidatora** węzła.

1. Wybierz **zaawansowane** stronę właściwości.

1. Modyfikowanie **atrybut wątku CLR** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)