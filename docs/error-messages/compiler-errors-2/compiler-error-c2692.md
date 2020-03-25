---
title: Błąd kompilatora C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: 7ce57cd50e9ec83cf80ec64e14f49eb9714f9208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177095"
---
# <a name="compiler-error-c2692"></a>Błąd kompilatora C2692

"function_name": funkcje w pełni prototypowe wymagane w kompilatorze języka C z opcją "/CLR"

Podczas kompilowania kodu zarządzanego .NET kompilator języka C wymaga deklaracji funkcji ANSI. Ponadto, jeśli funkcja nie przyjmuje żadnych parametrów, musi jawnie zadeklarować `void` jako typ parametru.
