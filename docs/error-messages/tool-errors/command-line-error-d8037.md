---
title: Błąd D8037 wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D8037
helpviewer_keywords:
- D8037
ms.assetid: acddaaa0-bd84-426f-a37b-8f680b379c9d
ms.openlocfilehash: e1c43b2ee7bf065207fb858117a9a78384b3974e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657174"
---
# <a name="command-line-error-d8037"></a>Błąd D8037 wiersza polecenia

Nie można utworzyć pliku tymczasowego il; wyczyścić katalog temp starych plików il

Nie jest wystarczająco dużo miejsca, aby utworzyć tymczasowy kompilatora pliki pośrednie. Aby rozwiązać ten błąd, należy usunąć stare pliki MSIL w katalogu określonym przez **TMP** zmiennej środowiskowej. Te pliki zostaną z _CL_hhhhhhhh.ss formularza, gdzie h reprezentuje losowe cyfra szesnastkowa, a ss reprezentuje typ pliku IL. Ponadto upewnij się zaktualizować komputer przy użyciu najnowszych poprawek systemu operacyjnego.

## <a name="see-also"></a>Zobacz też

[Błędy wiersza polecenia od D8000 do D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)