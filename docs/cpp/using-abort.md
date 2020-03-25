---
title: Użycie przerywania
ms.date: 11/04/2016
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: db0f6cdcdaf4bca1b74d89a9415c4f7951455d80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187860"
---
# <a name="using-abort"></a>Użycie przerywania

Wywołanie funkcji [Abort](../c-runtime-library/reference/abort.md) powoduje natychmiastowe zakończenie. Pomija proces normalnego niszczenia dla zainicjowanych globalnych obiektów statycznych. Pomija również specjalne przetwarzanie, które zostało określone przy użyciu funkcji `atexit`.

## <a name="see-also"></a>Zobacz też

[Dodatkowe zagadnienia dotyczące kończenia](../cpp/additional-termination-considerations.md)
