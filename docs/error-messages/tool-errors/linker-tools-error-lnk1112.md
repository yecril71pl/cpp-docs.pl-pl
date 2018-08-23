---
title: Błąd narzędzi konsolidatora LNK1112 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1112
dev_langs:
- C++
helpviewer_keywords:
- LNK1112
ms.assetid: 425793d8-37e6-4072-9b6e-c3d4e9c12562
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e08e8dae82675d9503575d543edfcaa2c96275e9
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464982"
---
# <a name="linker-tools-error-lnk1112"></a>Błąd narzędzi konsolidatora LNK1112

> Typ maszyny modułu "*type1*"powoduje konflikt z typem maszyny docelowej"*type2*"

## <a name="remarks"></a>Uwagi

Pliki obiektów, określony jako dane wejściowe zostały skompilowane dla typów na innym komputerze.

Na przykład, Jeśli spróbujesz połączyć skompilowany plik obiektu przy użyciu **/CLR** i plik obiektu kompilowany przy użyciu **/CLR: pure** (typ CEE maszyny), konsolidator wygeneruje błąd LNK1112. **/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Podobnie w przypadku utworzenia jeden moduł x64 kompilatora i inny moduł przy użyciu x86 kompilatora i spróbuj połączyć je, konsolidator wygeneruje LNK1112.

Możliwa przyczyna tego błędu jest Jeśli tworzysz aplikację 64-bitową, ale nie jest zainstalowany jeden z programów kompilujących w języku Visual C++ 64-bitowych. W tym przypadku nie będzie dostępne konfiguracje 64-bitowych. Aby rozwiązać ten problem, uruchom Instalatora programu Visual Studio, a następnie zainstalowanie brakujących składników języka C++.

Ten błąd może również wystąpić, jeśli zmienisz **Konfiguracja rozwiązania aktywnego** w **programu Configuration Manager** , a następnie spróbuj skompilować projekt, przed usunięciem plików pośrednich projektu. Aby rozwiązać ten problem, wybierz pozycję **Kompiluj rozwiązanie** z **kompilacji** menu. Możesz również wybrać **czyste rozwiązanie** z **kompilacji** menu i przeprowadź kompilację rozwiązania.

## <a name="see-also"></a>Zobacz także

- [Błędy i ostrzeżenia narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
