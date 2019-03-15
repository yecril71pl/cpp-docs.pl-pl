---
title: /STACK (Twórz stos z alokacji)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.StackReserveSize
- VC.Project.VCLinkerTool.StackCommitSize
- /stack
helpviewer_keywords:
- STACK linker option
- -STACK linker option
- memory allocation, stack
- /STACK linker option
- stack, setting size
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
ms.openlocfilehash: 27de554e1933b2753f641be358461c8d7ff4fffa
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813802"
---
# <a name="stack-stack-allocations"></a>/STACK (Twórz stos z alokacji)

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Uwagi

Opcja /STACK ustawia rozmiar stosu w bajtach. Użyj tej opcji tylko wtedy, gdy tworzysz pliku .exe.

`reserve` Wartość określa Alokacja całkowita stosu w pamięci wirtualnej. Dla ARM x86 i x64 maszyn, domyślny rozmiar stosu to 1 MB.

`commit` podlega interpretacji przez system operacyjny. W Windows wypchnie określa ilość pamięci fizycznej do przydzielenia w danym momencie. Zadeklarowanej pamięci wirtualnej powoduje, że miejsce, które mają zostać zarezerwowane w pliku stronicowania. Uzyskanie lepszej `commit` wartość pozwala zaoszczędzić czas, gdy potrzeba więcej miejsca na stosie aplikacji, ale zwiększa wymagania dotyczące pamięci i ewentualnie czas uruchamiania. Dla ARM maszyn x86 i x64 zatwierdzenia wartość domyślna to 4 KB.

Określ `reserve` i `commit` wartości dziesiętnych lub notacji języka C.

Innym sposobem Ustaw rozmiar stosu jest [STACKSIZE](stacksize.md) instrukcja w pliku definicji modułu (.def). **STACKSIZE** zastępuje twórz stos z alokacji (/ STACK) opcję, jeśli są określone oba. Rozmiar stosu można zmienić po utworzeniu pliku .exe przy użyciu [EDITBIN](editbin-reference.md) narzędzia.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **systemu** stronę właściwości.

1. Zmodyfikuj jedną z następujących właściwości:

   - **Zaalokowany rozmiar stosu**

   - **Zarezerwowany rozmiar stosu**

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A> właściwości.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
