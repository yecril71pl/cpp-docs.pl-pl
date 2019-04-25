---
title: Ostrzeżenie LNK4092 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4092
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
ms.openlocfilehash: 0b18002135d225a90f7e45adc2ff57a64c0a79f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279323"
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