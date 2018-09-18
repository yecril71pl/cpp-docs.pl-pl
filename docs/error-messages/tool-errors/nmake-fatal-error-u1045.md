---
title: Błąd krytyczny NMAKE U1045 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1045
dev_langs:
- C++
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2b9be4f7440d9e79d603e917c1886aebe7c44af
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056888"
---
# <a name="nmake-fatal-error-u1045"></a>Błąd krytyczny NMAKE U1045

zduplikowanie nie powiodło się: komunikat

Polecenie wywoływane przez NMAKE lub program nie powiodło się z powodu danego. Kiedy NMAKE wywołuje inny program — na przykład, kompilator lub konsolidator — wywołanie może zakończyć się niepowodzeniem i błędem mogą być zwrócone przez program o nazwie. Ten komunikat jest używana do zgłaszania błędu.

Aby rozwiązać ten problem, należy najpierw określić przyczynę błędu. Można użyć poleceń zgłoszone przez NMAKE [/N](../../build/nmake-options.md) opcję, aby sprawdzić ustawienia środowiska i powtórz czynności wykonywane przez NMAKE w wierszu polecenia.