---
title: Błąd D8037 wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D8037
helpviewer_keywords:
- D8037
ms.assetid: acddaaa0-bd84-426f-a37b-8f680b379c9d
ms.openlocfilehash: 3ebca6a21e6e19e0eca144c61e5c529bc6b2d03c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820757"
---
# <a name="command-line-error-d8037"></a>Błąd D8037 wiersza polecenia

Nie można utworzyć pliku tymczasowego il; wyczyścić katalog temp starych plików il

Nie jest wystarczająco dużo miejsca, aby utworzyć tymczasowy kompilatora pliki pośrednie. Aby rozwiązać ten błąd, należy usunąć stare pliki MSIL w katalogu określonym przez **TMP** zmiennej środowiskowej. Te pliki zostaną z _CL_hhhhhhhh.ss formularza, gdzie h reprezentuje losowe cyfra szesnastkowa, a ss reprezentuje typ pliku IL. Ponadto upewnij się zaktualizować komputer przy użyciu najnowszych poprawek systemu operacyjnego.

## <a name="see-also"></a>Zobacz też

[Błędy wiersza polecenia od D8000 do D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[MSVC Compiler Options](../../build/reference/compiler-options.md)