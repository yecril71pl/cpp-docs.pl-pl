---
title: Błąd wiersza polecenia D8037 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8037
dev_langs:
- C++
helpviewer_keywords:
- D8037
ms.assetid: acddaaa0-bd84-426f-a37b-8f680b379c9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38bbb8e85f0bb11af3846435f31cfc4223a39f16
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086320"
---
# <a name="command-line-error-d8037"></a>Błąd D8037 wiersza polecenia

Nie można utworzyć pliku tymczasowego il; wyczyścić katalog temp starych plików il

Nie jest wystarczająco dużo miejsca, aby utworzyć tymczasowy kompilatora pliki pośrednie. Aby rozwiązać ten błąd, należy usunąć stare pliki MSIL w katalogu określonym przez **TMP** zmiennej środowiskowej. Te pliki zostaną z _CL_hhhhhhhh.ss formularza, gdzie h reprezentuje losowe cyfra szesnastkowa, a ss reprezentuje typ pliku IL. Ponadto upewnij się zaktualizować komputer przy użyciu najnowszych poprawek systemu operacyjnego.

## <a name="see-also"></a>Zobacz też

[Błędy wiersza polecenia od D8000 do D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)