---
title: Błąd narzędzi konsolidatora LNK2039 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2039
dev_langs:
- C++
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac4fdde90911427a1a193bfb6f3a950a7bdcf180
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081796"
---
# <a name="linker-tools-error-lnk2039"></a>Błąd narzędzi konsolidatora LNK2039

Importowanie klasy referencyjnej\<typu > "zdefiniowanego w another.obj, powinna to być albo importowanych albo zdefiniowana, ale nie oba

Klasa ref "<`type`>" są importowane w pliku .obj określony, ale również jest zdefiniowany w innym pliku .obj. Ten stan może spowodować błąd czasu wykonywania lub inne nieoczekiwane zachowania.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź, czy "`type`" musi być zdefiniowana w pliku .obj i sprawdź, czy należy zaimportować z pliku winmd.

1. Usuń definicję lub importu.

## <a name="see-also"></a>Zobacz też

[Błędy i ostrzeżenia narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[Błąd narzędzi konsolidatora LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)