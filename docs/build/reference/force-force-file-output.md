---
title: /FORCE (Wymuszaj produkt wyjściowy pliku)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: 28b1c21382832c8775ffe0406038a482e74076c5
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299720"
---
# <a name="force-force-file-output"></a>/FORCE (Wymuszaj produkt wyjściowy pliku)

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>Uwagi

Opcja/FORCE nakazuje konsolidatorowi utworzenie prawidłowego pliku. exe lub DLL, nawet jeśli istnieje odwołanie do symbolu, ale nie zdefiniowano go lub jest on wielokrotnie zdefiniowany.

Opcja/FORCE może przyjmować opcjonalny argument:

- Użyj/FORCE: MULTIPLE, aby utworzyć plik wyjściowy, niezależnie od tego, czy LINK znajduje więcej niż jedną definicję symbolu.

- Użyj/FORCE: unrozwiązało, aby utworzyć plik wyjściowy niezależnie od tego, czy LINK odnajdzie niezdefiniowany symbol. /FORCE: nierozpoznany jest ignorowany, jeśli symbol punktu wejścia nie został rozpoznany.

/FORCE bez argumentów oznacza zarówno wielokrotne, jak i nierozwiązane.

Plik utworzony przy użyciu tej opcji może nie działać zgodnie z oczekiwaniami. Konsolidator nie będzie łączyć przyrostowo, gdy zostanie określona opcja/FORCE.

Jeśli moduł jest kompilowany z **/CLR**, **/Force** nie utworzy obrazu.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. 

1. Kliknij folder **konsolidator** .

1. Kliknij stronę właściwości **wiersza polecenia** .

1. Wpisz opcję w polu **dodatkowe opcje** .

Aby uzyskać więcej informacji, [Zobacz C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
