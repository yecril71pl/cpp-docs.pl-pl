---
title: Błąd krytyczny NMAKE U1045
ms.date: 11/04/2016
f1_keywords:
- U1045
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
ms.openlocfilehash: 0937e83303fefdf1f2aaaa5eea6f43c27159fd57
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808238"
---
# <a name="nmake-fatal-error-u1045"></a>Błąd krytyczny NMAKE U1045

zduplikowanie nie powiodło się: komunikat

Polecenie wywoływane przez NMAKE lub program nie powiodło się z powodu danego. Kiedy NMAKE wywołuje inny program — na przykład, kompilator lub konsolidator — wywołanie może zakończyć się niepowodzeniem i błędem mogą być zwrócone przez program o nazwie. Ten komunikat jest używana do zgłaszania błędu.

Aby rozwiązać ten problem, należy najpierw określić przyczynę błędu. Można użyć poleceń zgłoszone przez NMAKE [/N](../../build/reference/nmake-options.md) opcję, aby sprawdzić ustawienia środowiska i powtórz czynności wykonywane przez NMAKE w wierszu polecenia.