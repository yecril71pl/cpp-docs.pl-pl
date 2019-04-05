---
title: Błąd D8037 wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D8037
helpviewer_keywords:
- D8037
ms.assetid: acddaaa0-bd84-426f-a37b-8f680b379c9d
ms.openlocfilehash: f9f099d1abb8529620c1b3a0bc14705463ca5cd0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59021485"
---
# <a name="command-line-error-d8037"></a>Błąd D8037 wiersza polecenia

Nie można utworzyć pliku tymczasowego il; wyczyścić katalog temp starych plików il

Nie jest wystarczająco dużo miejsca, aby utworzyć tymczasowy kompilatora pliki pośrednie. Aby rozwiązać ten błąd, należy usunąć stare pliki MSIL w katalogu określonym przez **TMP** zmiennej środowiskowej. Te pliki zostaną z _CL_hhhhhhhh.ss formularza, gdzie h reprezentuje losowe cyfra szesnastkowa, a ss reprezentuje typ pliku IL. Ponadto upewnij się zaktualizować komputer przy użyciu najnowszych poprawek systemu operacyjnego.

## <a name="see-also"></a>Zobacz także

[Błędy wiersza polecenia od D8000 do D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Opcje kompilatora MSVC](../../build/reference/compiler-options.md)