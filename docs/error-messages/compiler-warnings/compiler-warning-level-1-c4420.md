---
title: Ostrzeżenie kompilatora (poziom 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: 72ab87b34e07717112f5af1727a216b4f786ae0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186793"
---
# <a name="compiler-warning-level-1-c4420"></a>Ostrzeżenie kompilatora (poziom 1) C4420

"operator": operator nie jest dostępny, przy użyciu "operator" zamiast; Sprawdzanie w czasie wykonywania może być naruszone

To ostrzeżenie jest generowane, gdy używasz [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (sprawdzanie nowego/usuwania wektora) i gdy nie zostanie znaleziony żaden formularz wektorowy. W tym przypadku jest używany formularz niebędący wektorem.

Aby/RTCv działał prawidłowo, kompilator powinien zawsze wywołać formę Vector [nowej](../../cpp/new-operator-cpp.md)/[Usuń](../../cpp/delete-operator-cpp.md) , jeśli użyto składni wektorowej.
