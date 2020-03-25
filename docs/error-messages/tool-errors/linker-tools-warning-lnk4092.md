---
title: Ostrzeżenie LNK4092 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4092
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
ms.openlocfilehash: 706ab843f4b079b507033af76a7f407816fce820
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183361"
---
# <a name="linker-tools-warning-lnk4092"></a>Ostrzeżenie LNK4092 narzędzi konsolidatora

udostępniona zapisywalna sekcja "sekcja" zawiera relokacje; obraz może nie działać poprawnie

Konsolidator emituje to ostrzeżenie za każdym razem, gdy istnieje sekcja udostępniona, aby ostrzec o potencjalnie poważnym problemie.

Jednym ze sposobów udostępniania danych między wieloma procesami jest oznaczenie sekcji jako "Shared". Jednak oznaczenie sekcji jako udostępnionej może spowodować problemy. Na przykład masz bibliotekę DLL, która zawiera deklaracje podobne do sekcji danych udostępnionych:

```
int var = 1;
int *pvar = &var;
```

Konsolidator nie może rozpoznać `pvar`, ponieważ jego wartość zależy od lokalizacji, w której Biblioteka DLL jest załadowana w pamięci, więc umieszcza rekord relokacji w bibliotece DLL. Podczas ładowania biblioteki DLL do pamięci, adres `var` można rozpoznać i `pvar` przypisane. Jeśli inny proces ładuje tę samą bibliotekę DLL, ale nie może załadować jej pod tym samym adresem, relokacja dla adresu `var` zostanie zaktualizowana dla drugiego procesu, a przestrzeń adresowa pierwszego procesu wskaże niewłaściwy adres.
