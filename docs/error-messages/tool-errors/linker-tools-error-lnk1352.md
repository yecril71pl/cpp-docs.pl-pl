---
title: LNK1352 błędu narzędzi konsolidatora
description: Błąd narzędzi konsolidatora LNK1352 występuje, gdy podjęta zostanie próba nieobsługiwanego scalania sekcji.
ms.date: 09/10/2019
f1_keywords:
- LNK1352
helpviewer_keywords:
- LNK1352
ms.openlocfilehash: 38f773bfd669529dfb1ada9c7bb59e6f0962c9c7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908383"
---
# <a name="linker-tools-error-lnk1352"></a>LNK1352 błędu narzędzi konsolidatora

> nie można scalić "*section_name_1*" i "*section_name_2*" w różnych sekcjach

## <a name="remarks"></a>Uwagi

Konsolidator wykrył, że Scalanie sekcji nie jest dozwolone, ponieważ *section_name_1* i *section_name_2* muszą zostać scalone w tej samej sekcji. Na przykład ten błąd występuje, gdy konsolidator wykryje próbę scalenia `.stls` sekcji `.tls` i sekcji w różnych sekcjach.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

Sprawdź opcję [/merge](../../build/reference/merge-combine-sections.md) w wierszu polecenia konsolidatora tego problemu.

## <a name="see-also"></a>Zobacz także

[Błędy i ostrzeżenia narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
