---
title: Ostrzeżenie narzędzi konsolidatora LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 43fae7d0f19f96998d2e1a1739bc3e596bbd9ea9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194203"
---
# <a name="linker-tools-warning-lnk4037"></a>Ostrzeżenie narzędzi konsolidatora LNK4037

>"*symbol*" nie istnieje; Ignoruj

Nie można zamówić *symbolicznej* nazwy przy użyciu opcji [/Order](../../build/reference/order-put-functions-in-order.md) , ponieważ nie można jej znaleźć w programie. Sprawdź specyfikację *symbolu* w pliku odpowiedzi porządkowania. Aby uzyskać więcej informacji, zobacz [/Order (Put Functions in order)](../../build/reference/order-put-functions-in-order.md) — opcja konsolidatora.

> [!NOTE]
> LINK nie może zamówić funkcji statycznych, ponieważ nazwy funkcji statycznych nie są nazwami symboli publicznych. Gdy **/Order** jest określony, to ostrzeżenie konsolidatora jest generowane dla każdego symbolu w pliku odpowiedzi zamówienia, który jest statyczny lub nie został znaleziony.
