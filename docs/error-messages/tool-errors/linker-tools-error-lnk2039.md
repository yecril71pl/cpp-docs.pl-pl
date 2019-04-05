---
title: Błąd narzędzi konsolidatora LNK2039
ms.date: 11/04/2016
f1_keywords:
- LNK2039
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
ms.openlocfilehash: 57d0c101358f84816c8d0cf96eb5137833df0b48
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027571"
---
# <a name="linker-tools-error-lnk2039"></a>Błąd narzędzi konsolidatora LNK2039

Importowanie klasy referencyjnej\<typu > "zdefiniowanego w another.obj, powinna to być albo importowanych albo zdefiniowana, ale nie oba

Klasa ref "<`type`>" są importowane w pliku .obj określony, ale również jest zdefiniowany w innym pliku .obj. Ten stan może spowodować błąd czasu wykonywania lub inne nieoczekiwane zachowania.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź, czy "`type`" musi być zdefiniowana w pliku .obj i sprawdź, czy należy zaimportować z pliku winmd.

1. Usuń definicję lub importu.

## <a name="see-also"></a>Zobacz także

[Błędy i ostrzeżenia narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[Błąd narzędzi konsolidatora LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)