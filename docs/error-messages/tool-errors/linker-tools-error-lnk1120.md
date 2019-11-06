---
title: Błąd narzędzi konsolidatora LNK1120
description: Opisuje błąd konsolidatora LNK1120, który raportuje liczbę nierozwiązanych błędów symboli zewnętrznych w łączu.
ms.date: 10/31/2019
f1_keywords:
- LNK1120
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
ms.openlocfilehash: 21a1ede07a69cdc065dd897715e243115529600d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626581"
---
# <a name="linker-tools-error-lnk1120"></a>Błąd narzędzi konsolidatora LNK1120

> *Liczba* nierozpoznanych elementów zewnętrznych

LNK1120 błędów zgłasza liczbę [nierozwiązanych błędów symboli zewnętrznych](linker-tools-error-lnk2001.md#what-is-an-unresolved-external-symbol) w bieżącym łączu.

Każdy nierozpoznany symbol zewnętrzny najpierw jest raportowany przez błąd [LNK2001](linker-tools-error-lnk2001.md) lub [LNK2019](linker-tools-error-lnk2019.md) . Komunikat LNK1120 jest ostatni i zawiera nierozpoznaną liczbę błędów symboli.

> [!IMPORTANT]
> **Nie musisz naprawić tego błędu.** Ten błąd znajduje się w przypadku skorygowania wszystkich błędów konsolidatora LNK2001 i LNK2019 przed nim w danych wyjściowych kompilacji. Zawsze usuwaj problemy, zaczynając od pierwszego zgłoszonego błędu. Późniejsze błędy mogą wynikać z wcześniejszych wersji i przejść po usunięciu wcześniejszych błędów.
