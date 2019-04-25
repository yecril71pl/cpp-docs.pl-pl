---
title: Błąd narzędzi konsolidatora LNK1120
ms.date: 05/17/2017
f1_keywords:
- LNK1120
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
ms.openlocfilehash: b11318dcffb665d3b422fffcbd7e6275f35984dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255108"
---
# <a name="linker-tools-error-lnk1120"></a>Błąd narzędzi konsolidatora LNK1120

> *Liczba* nierozpoznanych elementów zewnętrznych

Błąd LNK1120 liczności (*numer*) błędów nierozpoznany symbol zewnętrzny dla tej operacji łączenia. Większość nierozpoznanych symboli zewnętrznych błędy są zgłaszane indywidualnie przez [błąd narzędzi konsolidatora LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md) i [błąd narzędzi konsolidatora LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md), które poprzedzają ten komunikat o błędzie, jeden raz dla każdego nierozpoznany zewnętrzny symbol błędu.

Aby naprawić ten błąd, należy rozwiązać wszystkie inne nierozwiązane błędy zewnętrznych lub inne błędy konsolidatora, które należy poprzedzić go w danych wyjściowych kompilacji. Ten błąd nie jest zgłaszany, kiedy pozostają żadne nierozwiązane błędy zewnętrznych.
