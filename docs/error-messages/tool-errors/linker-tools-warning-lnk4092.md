---
title: Ostrzeżenie LNK4092 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4092
dev_langs:
- C++
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9b47b347e11e640425bc7840a0f78a33e9e3b7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113425"
---
# <a name="linker-tools-warning-lnk4092"></a>Ostrzeżenie LNK4092 narzędzi konsolidatora

współużytkowana, zapisywalna sekcja "section" zawiera relokacje; Obraz może nie działać poprawnie

Konsolidator emituje to ostrzeżenie, zawsze wtedy, gdy masz udostępnionej sekcji, aby ostrzec o potencjalnie poważny problem.

Jednym ze sposobów udostępniania danych między wiele procesów jest do oznaczania sekcji jako "udostępnione". Jednakże oznaczanie sekcji jako udostępniony może powodować problemy. Na przykład masz biblioteki DLL, która zawiera deklaracje następująco w sekcji udostępnionych danych:

```
int var = 1;
int *pvar = &var;
```

Nie można rozpoznać konsolidator `pvar` , ponieważ jej wartość zależy od tego, gdzie biblioteki DLL jest ładowany w pamięci, dlatego umieszcza rekord relokacji w bibliotece DLL. Jeśli biblioteka DLL jest ładowany do pamięci, adres `var` może zostać rozpoznany i `pvar` przypisane. Jeśli inny proces ładuje tej samej bibliotece DLL, ale nie można załadować w taki sam adres, relokacja dla adresu `var` zostaną zaktualizowane do drugiego procesu i przestrzeń adresową pierwszy proces wskaże niewłaściwy adres.