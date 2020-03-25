---
title: Błąd narzędzi konsolidatora LNK2039
ms.date: 11/04/2016
f1_keywords:
- LNK2039
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
ms.openlocfilehash: 7712747deb865ec62fa007fcd95ad09630d00cea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194502"
---
# <a name="linker-tools-error-lnk2039"></a>Błąd narzędzi konsolidatora LNK2039

Importowanie klasy referencyjnej "\<typ >", która jest zdefiniowana w innym elemencie. obj; powinien zostać zaimportowany lub zdefiniowany, ale nie oba

Klasa referencyjna "<`type`>" została zaimportowana do określonego pliku. obj, ale jest również zdefiniowana w innym pliku. obj. Ten stan może spowodować awarię środowiska uruchomieniowego lub inne nieoczekiwane zachowanie.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź, czy element "`type`" musi być zdefiniowany w innym pliku. obj i sprawdź, czy należy go zaimportować z pliku winmd.

1. Usuń definicję lub import.

## <a name="see-also"></a>Zobacz też

[Błędy i ostrzeżenia narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[Błąd narzędzi konsolidatora LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)
