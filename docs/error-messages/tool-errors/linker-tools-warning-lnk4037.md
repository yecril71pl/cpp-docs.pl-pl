---
title: "Ostrzeżenie LNK4037 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4037
dev_langs: C++
helpviewer_keywords: LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c93eab2faf81e4cd743eae4befa2f842c100589
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4037"></a>Ostrzeżenie LNK4037 narzędzi konsolidatora

>"*symbol*" nie istnieje; zignorowano

Nazwa *symbol* nie może zostać określona za pomocą [/kolejność](../../build/reference/order-put-functions-in-order.md) opcja, ponieważ nie odnaleziono w programie. Sprawdź specyfikację *symbol* w pliku odpowiedzi w kolejności. Aby uzyskać więcej informacji, zobacz [/order (Put funkcje w kolejności)](../../build/reference/order-put-functions-in-order.md) — opcja konsolidatora.

> [!NOTE]
> ŁĄCZE nie można uporządkować statyczne funkcje, ponieważ nazwy funkcji statyczne nie są nazw symboli publicznych. Gdy **/kolejność** jest określona, konsolidator, to ostrzeżenie jest generowany dla każdego symbolu w pliku odpowiedzi kolejności statycznych lub nie został odnaleziony.