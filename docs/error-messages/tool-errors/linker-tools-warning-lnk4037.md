---
title: Ostrzeżenie LNK4037 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/04/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4037
dev_langs:
- C++
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b87f0a415d6ae7d282e29c2ca67fda043c2a901
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4037"></a>Ostrzeżenie LNK4037 narzędzi konsolidatora

>"*symbol*" nie istnieje; zignorowano

Nazwa *symbol* nie może zostać określona za pomocą [/kolejność](../../build/reference/order-put-functions-in-order.md) opcja, ponieważ nie odnaleziono w programie. Sprawdź specyfikację *symbol* w pliku odpowiedzi w kolejności. Aby uzyskać więcej informacji, zobacz [/order (Put funkcje w kolejności)](../../build/reference/order-put-functions-in-order.md) — opcja konsolidatora.

> [!NOTE]
> ŁĄCZE nie można uporządkować statyczne funkcje, ponieważ nazwy funkcji statyczne nie są nazw symboli publicznych. Gdy **/kolejność** jest określona, konsolidator, to ostrzeżenie jest generowany dla każdego symbolu w pliku odpowiedzi kolejności statycznych lub nie został odnaleziony.