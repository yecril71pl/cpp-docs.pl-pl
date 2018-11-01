---
title: Ostrzeżenie narzędzi konsolidatora LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 9a8121617e622fc12efe5bd26aac23faf2530f24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607405"
---
# <a name="linker-tools-warning-lnk4037"></a>Ostrzeżenie narzędzi konsolidatora LNK4037

>"*symbol*" nie istnieje; został zignorowany

Również nazwę uzupełnioną *symbol* nie może zostać określona za pomocą [/ORDER](../../build/reference/order-put-functions-in-order.md) opcji, ponieważ nie można go znaleźć w programie. Sprawdź specyfikację *symbol* w pliku odpowiedzi w kolejności. Aby uzyskać więcej informacji, zobacz [/order (Put funkcje w kolejności)](../../build/reference/order-put-functions-in-order.md) — opcja konsolidatora.

> [!NOTE]
> ŁĄCZE nie zamówienia statyczne funkcje, ponieważ nazwy statycznej funkcji nie są nazwy symboli publicznych. Gdy **/ORDER** jest określona, konsolidator, to ostrzeżenie jest generowany dla każdego symbolu w pliku odpowiedzi zamówienia, który jest statycznych lub nie został odnaleziony.